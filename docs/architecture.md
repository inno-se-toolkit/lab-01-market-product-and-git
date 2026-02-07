## Product Choice

- **Product name:** Telegram
- **Website:** https://telegram.org/
- **Short description:** Telegram is a cloud-based messaging platform that supports private chats, groups, and channels with multi-device synchronization. Clients communicate with backend services for authentication, message routing, and media storage.

## Main components

**Component Diagram (C4 — Component level)**

![Telegram Component Diagram](./diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

**PlantUML code:** [Telegram Component Diagram Code](./diagrams/src/telegram/component-diagram/Component%20Diagram.puml)

**Selected components (from the component diagram) and responsibilities**

1. **Client Applications (Mobile/Desktop/Web)**
   Provides the user interface, manages local caching, and calls backend APIs for authentication, messaging, media transfer, and sync.

2. **API Gateway / Edge Service**
   Terminates client connections, applies routing and rate limiting, and forwards validated requests to internal services.

3. **Authentication & Session Service**
   Implements login and session lifecycle, issues/validates session credentials, and ties sessions to users and devices.

4. **Messaging Service**
   Accepts outgoing messages, persists message state/metadata, and routes deliveries to recipient devices using internal fan-out mechanisms.

5. **User & Contacts Service**
   Stores user profiles and settings, resolves identities/usernames, and manages contact/address-book relations and privacy rules.

6. **Media Service / Storage Adapter**
   Handles media upload/download workflows and stores media blobs in object storage, returning references used by messaging.

## Data flow

**Sequence Diagram**

![Telegram Sequence Diagram](./diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

**PlantUML code:** [Telegram Sequence Diagram Code](./diagrams/src/telegram/sequence-diagram/Sequence%20Diagram.puml)

**Chosen action group:** `Send message (cloud chat)`

**What happens in this group**

- The **Client Applications** sends a request to deliver a message, including chat/conversation identifier, session credentials, message text, and (optionally) media references.
- The **API Gateway / Edge Service** validates the request at the boundary (auth/rate limits) and routes it to the **Messaging Service**.
- The **Messaging Service** persists the message state and triggers delivery to recipients; it may query **User & Contacts Service** for membership and permissions.

**Components that communicate and exchanged data**

- **Client Applications → API Gateway / Edge Service:** session/auth data, chat ID, message text, client message ID (idempotency), device metadata.
- **API Gateway / Edge Service → Authentication & Session Service:** token/session validation request; response includes user identity and authorization outcome.
- **API Gateway / Edge Service → Messaging Service:** authenticated send-message command (user ID, chat ID, message body, media handles).
- **Messaging Service → User & Contacts Service:** recipient resolution, chat membership checks, privacy/permission checks.
- If media is present: **Client Applications → API Gateway / Edge Service → Media Service / Storage Adapter:** media bytes + metadata; **Media Service** returns media handle/reference used by **Messaging Service**.

## Deployment

**Deployment Diagram**

![Telegram Deployment Diagram](./diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

**PlantUML code:** [Telegram Deployment Diagram Code](./diagrams/src/telegram/deployment-diagram/Deployment%20Diagram.puml)

**Where components are deployed (high-level)**

- **Client Applications** run on user devices (mobile/desktop) and browsers (web).
- **API Gateway / Edge Service** runs on internet-facing edge nodes behind load balancers/ingress.
- **Authentication & Session Service**, **Messaging Service**, **User & Contacts Service**, and **Media Service** run in backend compute clusters (typically horizontally scaled services).
- Persistent data is stored in backend databases for users/messages and in **object storage** for media.

## Assumptions

1. I assume the **Messaging Service** uses idempotency keys (e.g., client message IDs) to avoid duplicate message creation during retries.
2. I assume the **Media Service / Storage Adapter** supports chunked uploads and may implement deduplication to reduce storage costs.
3. I assume the **API Gateway / Edge Service** enforces rate limits and basic abuse prevention before forwarding requests to core services.

## Open questions

1. How is multi-region routing and failover implemented in production (active-active vs active-passive), and what consistency model is used for message state?
2. What is the exact end-to-end encrypted data flow for secret chats (key exchange, key storage, server involvement boundaries)?
3. What caching layers and invalidation strategies are used for hot data (profiles, chat membership, recent message metadata) under peak load?

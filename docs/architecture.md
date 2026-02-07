## Product Choice

- **Product name**: Telegram
- **Website**: https://telegram.org/
- **Description**: Telegram is a cloud-based instant messaging and voice-over-IP service that emphasizes speed, security, and cross-platform availability. It supports text, media, files, and group chats with up to 200,000 members.

## Main components

![Telegram Component Diagram](../../../docs/diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

[Telegram Component Diagram Code](../../../docs/diagrams/src/telegram/component-diagram.puml)

Selected components:

1. **Client App**  
   The user-facing application (iOS, Android, Web, Desktop) that handles UI rendering, user input, and local caching of messages.

2. **MTProto API Gateway**  
   Entry point for all client requests. Implements Telegram’s custom MTProto protocol for secure communication and routes requests to internal services.

3. **Message Service**  
   Handles message creation, delivery, storage, and retrieval. Ensures messages are delivered in order and supports features like replies and forwards.

4. **User Service**  
   Manages user accounts, profiles, contacts, and privacy settings. Authenticates users and validates session tokens.

5. **Cloud Storage**  
   Stores media files (photos, videos, documents) uploaded by users. Likely uses deduplication to save space on identical files.

## Data flow

![Telegram Sequence Diagram](../../../docs/diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

[Telegram Sequence Diagram Code](../../../docs/diagrams/src/telegram/sequence-diagram.puml)

**Group: "Send Message"**

When a user sends a message:
1. The **Client App** encrypts the message (if not secret chat) and sends it via MTProto to the **MTProto API Gateway**.
2. The gateway forwards it to the **Message Service**, which stores it in the database and retrieves recipient info from the **User Service**.
3. The **Message Service** pushes the message to the recipient’s **Client App** via the gateway.
4. Data exchanged: message content, sender/receiver IDs, timestamps, and metadata (e.g., read receipts).

## Deployment

![Telegram Deployment Diagram](../../../docs/diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

[Telegram Deployment Diagram Code](../../../docs/diagrams/src/telegram/deployment-diagram.puml)

Telegram’s backend services (API Gateway, Message Service, User Service, etc.) are deployed across **distributed data centers** worldwide, likely using virtual machines or containers in private cloud infrastructure. The **Client Apps** run on end-user devices (mobile, desktop). **Cloud Storage** is hosted on scalable object storage systems, possibly with CDN integration for fast media delivery.

## Assumptions

1. Telegram uses **deduplication** in Cloud Storage to avoid storing multiple copies of the same file (e.g., viral memes).
2. The **MTProto API Gateway** performs rate limiting and DDoS protection at the edge layer.

## Open questions

1. How does Telegram ensure **end-to-end encryption** in secret chats while maintaining message ordering and delivery guarantees?
2. What **database technology** does Telegram use for message storage — custom NoSQL, Cassandra, or something else?
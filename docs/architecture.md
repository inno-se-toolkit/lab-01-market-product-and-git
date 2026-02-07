## Product Choice

- **Product name:** Telegram
- **Website:** https://telegram.org/
- **Short description:** Telegram is a messaging platform for private chats, groups, channels, and bots.

## Main components

![Telegram Component Diagram](../docs/diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

[Telegram Component Diagram Code](../docs/diagrams/src/telegram/component-diagram.puml)

Selected components:

1. **Client Apps (iOS/Android/Desktop/Web)**  
   These are user-facing applications where people read chats, send messages, and upload media.  
   They collect user actions and call backend APIs.

2. **Authentication Service**  
   This service verifies user identity, sessions, and tokens.  
   It ensures only authorized users can access protected operations.

3. **Messaging Service**  
   This is the core business service for message sending, editing, and delivery logic.  
   It coordinates persistence and synchronization of chat messages between participants.

4. **Media Service**  
   This service handles file upload/download for photos, videos, and documents.  
   It stores media metadata and provides links/IDs for clients to access files.

5. **Notification Service**  
   This service sends push notifications when new messages or events happen.  
   It helps notify offline users and bring them back to the app.

## Data flow

![Telegram Sequence Diagram](../docs/diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

[Telegram Sequence Diagram Code](../docs/diagrams/src/telegram/sequence-diagram.puml)

### Chosen group: Send Message Flow

In this flow, a user composes a message in the client app and presses **Send**.  
The client sends a request to the API Gateway, which validates the session/token (directly or via Authentication Service) and forwards the request to the Messaging Service.  
The Messaging Service validates business rules, stores the message, and triggers delivery and notification events.  
Finally, recipients receive the new message (real-time update), and offline users get push notifications.

**Components and data exchange:**

- **Client App → API Gateway:** `chat_id`, `sender_id`, message text/media reference, client timestamp, auth token.
- **API Gateway → Authentication Service:** token/session verification request and user/session metadata.
- **API Gateway → Messaging Service:** normalized command to send message with validated user context.
- **Messaging Service → Database/Storage:** message record, chat metadata update, delivery state.
- **Messaging Service → Notification Service:** event with recipient IDs, chat ID, message ID (and short preview for notification).
- **Notification Service → Recipient Devices (via push providers):** push payload containing notification text and deep-link/chat reference.
- **Messaging Service → Recipient Client Apps (real-time channel):** full message payload for immediate display.

## Deployment

![Telegram Deployment Diagram](../docs/diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

[Telegram Deployment Diagram Code](../docs/diagrams/src/telegram/deployment-diagram.puml)

Telegram clients are deployed on user devices (iOS, Android, desktop, web browsers).  
API Gateway and backend services (authentication, messaging, media, notifications) are deployed in distributed cloud/data-center server clusters.  
Databases and media/object storage are deployed in replicated storage infrastructure to provide high availability, durability, and fast access from multiple regions.

## Assumptions

I assume the Messaging Service uses asynchronous event processing (queue/broker) to scale message fan-out for large groups and channels.
I assume media files are stored in object storage, while message/chat metadata is stored separately in databases.

## Open questions

How exactly does Telegram guarantee message ordering and consistency across multiple user devices when network conditions are unstable?

What is the real production architecture for secret chats (key management, routing, and storage boundaries) compared to regular cloud chats?

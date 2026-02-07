## Product Choice

* **Product name:** Telegram
* **Website:** [https://telegram.org/](https://telegram.org/)
* **Description:** Telegram is a cloud-based messaging platform focused on speed, security, and scalability, supporting private chats, group conversations, channels, and media sharing for hundreds of millions of users.

## Main components

### Component diagram

![Telegram Component Diagram](Component-Diagram.svg)

<details><summary>Rendered image (click to open)</summary>

![Telegram Component Diagram](Component%20Diagram.svg)

</details>

* **PlantUML source:** [Telegram Component Diagram Code](component-diagram.puml)

### Selected components

1. **Mobile / Desktop Client**
   The client applications provide the user interface for messaging, media consumption, and account management, and initiate all user-driven requests to the backend.

2. **API Gateway**
   Acts as the main entry point for client requests, handling request routing, authentication, and basic validation before forwarding traffic to internal services.

3. **Authentication Service**
   Responsible for user identity management, login via phone number, session handling, and issuing authorization tokens used by other backend services.

4. **Messaging Service**
   Core service that processes message sending and receiving, manages chat state, and ensures messages are delivered to the correct recipients in the right order.

5. **Media Storage Service**
   Stores large files such as photos, videos, and documents, and provides efficient upload, download, and reuse of media across chats.

6. **Notification Service**
   Sends push notifications to user devices when new messages or events occur, integrating with platform-specific push providers.

## Data flow

### Sequence diagram

![Telegram Sequence Diagram](Sequence%20Diagram.svg)

* **PlantUML source:** [Telegram Sequence Diagram Code](sequence-diagram.puml)

### Chosen flow: Sending a message

In this flow, a user sends a message from a client application to another user or group chat.

1. The **Client** sends a `SendMessage` request to the **API Gateway**, including the message content and metadata (chat ID, sender ID).
2. The **API Gateway** verifies the session with the **Authentication Service** to ensure the user is authorized.
3. After successful validation, the request is forwarded to the **Messaging Service**.
4. The **Messaging Service** persists the message, determines the recipients, and updates the chat state.
5. For recipients who are offline, the **Notification Service** is triggered to send push notifications.
6. When recipients come online, the **Messaging Service** delivers the message to their clients.

Data exchanged includes message text, user and chat identifiers, authorization tokens, and delivery status updates between these components.

## Deployment

### Deployment diagram

![Telegram Deployment Diagram](Deployment%20Diagram.svg)

* **PlantUML source:** [Telegram Deployment Diagram Code](deployment-diagram.puml)

### Deployment description

Client applications run on user devices (mobile and desktop). Backend services such as the API Gateway, Authentication, Messaging, and Notification services are deployed across distributed cloud data centers. Media Storage is deployed on scalable storage clusters optimized for high throughput and global access.

## Assumptions

* I assume the Messaging Service uses data sharding by user or chat ID to scale horizontally across many servers.
* I assume Media Storage supports content deduplication to reduce storage usage for frequently forwarded files.
* I assume the API Gateway performs rate limiting to protect backend services from abuse and traffic spikes.

## Open questions

* How does the data flow differ for end-to-end encrypted secret chats compared to regular cloud chats?
* What consistency guarantees does the Messaging Service provide across geographically distributed data centers?
* How are failover and disaster recovery handled for active chats during a data center outage?

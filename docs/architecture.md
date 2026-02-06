## Product Choice
**Product name:** Telegram
**Website:** [https://telegram.org](https://telegram.org)
**Description:** A cloud-based mobile and desktop messaging app with a focus on security and speed.

## Main components

![Telegram Component Diagram](./diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

[PlantUML code](./diagrams/src/telegram/component-diagram.puml)

1. **MTProto Gateway (DC Entry)**: Acts as the primary entry point for client connections, handling the MTProto protocol and routing requests to internal services.
2. **Auth & Session Service**: Manages user registration, authentication, and maintains active user sessions across multiple devices.
3. **Message Handling Service**: The core service responsible for the logic of sending, delivering, and processing instant messages.
4. **Media & File Service**: Handles the uploading, storage, and distribution of photos, videos, and other documents.
5. **Sharded Chat DB**: A distributed database layer used to store and retrieve chat history efficiently at scale.

## Data flow

![Telegram Sequence Diagram](./diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

[PlantUML code](./diagrams/src/telegram/sequence-diagram.puml)

**Description:**
In the **"User sends message"** flow, the process works as follows:
1. The **Mobile/Desktop App** sends the message data to the **MTProto Gateway**.
2. The **MTProto Gateway** forwards this request to the **Message Handling Service**.
3. The **Message Handling Service** saves the message content into the **Sharded Chat DB**.
4. Simultaneously, it sends a request to the **Notification Service** to inform the recipient about the new message.

## Deployment

![Telegram Deployment Diagram](./diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

[PlantUML code](./diagrams/src/telegram/deployment-diagram.puml)

**Description:**
The system is deployed using a hybrid cloud infrastructure. The **Client Applications** are installed locally on user devices (iOS, Android, Windows, macOS). The **Core Services** and **Data Layer** are deployed in multiple distributed data centers across the globe to ensure low latency and high availability.

## Assumptions
1. I assume the cloud storage system implements deduplication to optimize storage costs for shared media files.
2. I assume that the system uses a Content Delivery Network (CDN) to provide fast access to large media files for users in different geographic regions.

## Open questions
1. How exactly does the data flow look like in secret chats with end-to-end encryption?
2. What specific load-balancing algorithms are used to distribute traffic between different data centers during peak hours?

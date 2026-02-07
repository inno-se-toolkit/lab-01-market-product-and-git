## Product Choice

**Product name:** Telegram

**Link:** [telegram.org](https://telegram.org)

**Description:** Telegram is a cloud-based mobile and desktop messaging app with a focus on security and speed.

## Main Components

![Telegram Component Diagram](./diagrams/out/telegram/component-diagram/Component%20Diagram.svg)
[Telegram Component Diagram Code](./diagrams/src/telegram/component-diagram.puml)

### Description of 5 main components

1. Message Handling Service - Processes incoming and outgoing messages.

2. Auth & Session Service - Authenticates users and manages their sessions, enforces access control.

3. Notification/Updates Service - Delivers real-time updates and notifications to clients. It informs users about new messages, chat changes, and etc.

4. Media & File Service - Handles uploading, storage, and retrieval of media files.

5. Bot API service - Provides an interface for external bots to interact with the system. It allows bots to receive updates and send messages through a dedicated API.

## Data flow

![Telegram Sequence Diagram](./diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)
[Telegram Sequence Diagram Code](./diagrams/src/telegram/sequence-diagram.puml)

### Send Message group

The client sends a message with a reference to an already uploaded file to the backend. The MLProto Gateway authenticates the client, the Messages Serivce saves, updates Database and confirms to the client that the message was successfully accepted.

The Mobile App sends a sendMessage request to the MTProto Gateway. The MTProto Gateway validates the session via the Auth Service, then forwards the message data to the Message Service, which stores message records in the Database and returns a confirmation back through the Gateway to the Mobile App.

## Deployment

![Telegram Deployment Diagram](./diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)
[Telegram Deployment Diagram Code](./diagrams/src/telegram/deployment-diagram.puml)

The MTProto Gateway and BOT API is deployed on edge servers and maintains persistent connections with clients.
Backend services such as Auth Service, Message Service, Push Notification Service, Media Service, and Channel Service run servers inside the data center.
The Database and Media Storage are deployed on separate duplicates storages nodes within the backend infrastructure.

## Assumptions

- I assume the Bot API Service operates on the same messaging backend as regular users but enforces stricter rate limits and permission checks for bots.
- I assume the system uses geographically distributed data centers, and user traffic is routed to the nearest data center to minimize latency.

## Open Questions

1. How are updates actually delivered to clients in production: via persistent connections, long polling, push mechanisms, or a hybrid approach? How does the system handle with slow or offline clients?
2. What does the real data flow look like for secret chats, which components can see the data, where encryption and decryption happen, what is stored on the server, and how this flow differs architecturally from regular cloud chats?

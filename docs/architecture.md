# Telegram Architecture

## Product Choice

**Product Name:** Telegram

**Website:** https://telegram.org

**Description:** Telegram is a cloud-based messaging application that provides instant messaging, voice and video calls, media sharing, and group communication features. It focuses on speed, security, and privacy, supporting both regular chats and end-to-end encrypted secret chats.

## Main components

### Component Diagram

![Telegram Component Diagram](diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

**PlantUML Source:** [Telegram Component Diagram Code](../diagrams/src/telegram/component-diagram.puml)

### Component Descriptions
1. **MTProto Gateway (DC Entry)** - The connection manager that serves as the entry point for all client connections. It handles incoming MTProto protocol requests from mobile apps, desktop apps, and web clients, routing them to the appropriate backend services using internal RPC calls.
2. **Auth & Session Service** - Manages user authentication, session validation, and SMS-based login verification. It validates client sessions before allowing access to other services and integrates with external SMS providers to handle phone number verification during registration.
3. **Message Handling Service** - The core service responsible for processing, storing, and retrieving messages. It persists messages to the database, maintains message sequence numbers (pts), and publishes message events to the event bus for asynchronous propagation to other users.
4. **Media & File Service** - Handles media uploads and downloads including photos, videos, documents, and other files. It manages file chunking, persistence in the distributed file system, and retrieval of media with optimizations like thumbnail generation for efficient delivery.
5. **Notification/Updates Service** - Consumes events from the message broker and is responsible for sending push notifications to offline users via external providers (FCM, APNs). It checks user notification settings and respects mute preferences before sending alerts.
6. **Channel/Broadcast Service** - Manages public and private channels, supergroups, and broadcast operations. It handles channel-specific operations and publishes updates to the event bus so that all channel members receive notifications about new content.

## Data flow

### Sequence Diagram

![Telegram Sequence Diagram](diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

**PlantUML Source:** [Telegram Sequence Diagram Code](../diagrams/src/telegram/sequence-diagram.puml)

### Event Propagation (Fan-out) Flow

The "Event Propagation (Fan-out)" flow (Step 3) demonstrates how messages reach all relevant recipients asynchronously:

1. After the Message Service persists a message to the database and updates the sequence number in cache, it publishes a `NewMessageUpdate` event to the Kafka event bus.
2. The MTProto Gateway consumes this event and synchronizes the update to all online devices of the recipient, updating the UI with the delivery confirmation (double tick).
3. Simultaneously, the Push Notification Service consumes the same event from Kafka, checks the recipient's notification settings and session status in the cache and database.
4. If the recipient is offline or has notifications enabled, the Push Service sends a notification through external providers (APNs for iOS, FCM for Android).

**Components involved:** Message Service → Kafka Event Bus → MTProto Gateway and Push Notification Service. The Message Service publishes the event, while downstream consumers (Gateway and Push Service) handle delivery to online and offline clients respectively, exchanging message metadata and notification status.

## Deployment

### Deployment Diagram

![Telegram Deployment Diagram](diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

**PlantUML Source:** [Telegram Deployment Diagram Code](../diagrams/src/telegram/deployment-diagram.puml)

### Deployment Description

Telegram's infrastructure is organized across multiple tiers:

- **Client Tier:** Users connect via mobile apps (iOS/Android), desktop applications, or web clients.
- **Edge Layer:** The MTProto Gateway and Bot API Frontend handle incoming connections from clients and external bots respectively.
- **Compute Cluster:** Microservices (Auth Service, Message Service, Channel Service, Media Service, Push Notification Service) run in containerized pods and process requests.
- **Middleware & Data Tier:** Kafka event bus provides asynchronous message passing between services. A Redis-based state cache stores session data and sequence numbers for fast access. The sharded chat database stores persistent message and user data, while a distributed file system handles media file storage.
- **External Ecosystem:** External SMS providers handle phone verification, and push services (FCM/APNs) deliver notifications to mobile devices.

## Assumptions
1. **I assume the Message Service uses optimistic locking with sequence numbers (pts) to prevent duplicate message deliveries and maintain message ordering consistency across distributed replicas.**
2. **I assume the MTProto Gateway maintains persistent TCP connections with clients or implements a connection pooling mechanism to efficiently handle millions of concurrent users while minimizing resource overhead.**
3. **I assume the Distributed File System implements content-addressed storage (content deduplication) to optimize storage costs when multiple users share the same media file (e.g., popular stickers or shared documents).**

## Open questions
1. **How does Telegram handle the consistency model when a user is connected to multiple devices? Are all devices guaranteed to receive messages in the same order, or are there potential race conditions?**
2. **What specific database sharding strategy is used for the Sharded Chat DB? Is it sharded by user ID, by chat ID, or by some other key, and how are resharding operations handled during growth?**
3. **How does the system handle secret chat synchronization across devices? Are secret chats accessible from multiple devices of the same user, and if so, how are encryption keys distributed securely?**

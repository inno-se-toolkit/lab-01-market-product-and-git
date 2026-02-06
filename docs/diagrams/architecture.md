## TELEGRAM
**Product name:** Telegram
**Link:** https://telegram.org
**Description:** Secure messaging app with cloud sync, channels, bots, and end-to-end encrypted secret chats.

## MAIN COMPONENTS
![Telegram Component Diagram](./diagrams/out/telegram/component-diagram/Component Diagram.svg)
![Telegram Component Diagram code](./diagrams/src/telegram/component-diagram.puml)
**Components:**
1. **MTProto Gateway** - handles incoming client connections and manages sessions.
2. **Auth & Session Service** - responsible for user authentication and session management.
3. **Message Handling Service** - processes sending, receiving, and routing of messages.
4. **Distributed File System (DFS)** - stores media files and documents in a distributed system.
5. **Sharded Chat DB** - sharded database for storing chat history.

## DATA FLOW
![Telegram Sequence Diagram](./diagrams/out/telegram/sequence-diagram/Sequence Diagram.svg)
![Telegram Component Diagram code](./diagrams/src/telegram/sequence-diagram.puml)

**Action group: "Send Message Flow"**
1. Client encrypts message via MTProto
2. Sends to MTProto Gateway
3. Gateway forwards to Message Handling Service
4. Service saves message to Sharded Chat DB
5. Sends notification to recipient via Notification Service
6. Recipient receives message through their client

**Component interaction:**
- **Client ↔ MTProto Gateway:** encrypted message data
- **Gateway ↔ Message Service:** message metadata and content
- **Message Service ↔ Chat DB:** stored message with metadata

## Deployment
![Telegram Deployment Diagram](./out/docs/diagrams/out/telegram/component-diagram/Component-Diagram.svg)

<img src="docs/diagrams/out/telegram/component-diagram/Component-Diagram.svg">

**Deployment description:**
Telegram services are deployed across multiple data centers worldwide. Each DC contains a full set of services for fault tolerance and low latency.

## Assumptions

1. I assume MTProto Gateway uses load balancing between multiple instances.
2. I assume Distributed File System uses file replication between DCs for fast access.
3. I assume Redis cache is used to store active user sessions.

## Open questions

1. How does the data flow look like in secret chats?
3. How are conflicts handled when messages are edited simultaneously?
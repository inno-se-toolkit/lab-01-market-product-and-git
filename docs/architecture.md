##Product Choice
Product name: Telegram
Link to the product's website: https://telegram.org
Short description of the product: A cloud-based instant messaging app with end-to-end encryption for secret chats, supporting text, media, voice, and group communication across platforms.

##Main components
![Telegram Component Diagram](../docs/diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

PlantUML code: ../../../docs/diagrams/src/telegram/component-diagram/component-diagram.puml

Selected components:
1. MTProto Gateway (DC Entry)
   Acts as the entry point for all client connections, handling MTProto protocol parsing, session management, and load distribution across data centers.

2. Auth & Session Service
   Manages user authentication, session tokens, and device registration; validates credentials before allowing access to core services.

3. Message Handling Service
   Processes message routing, delivery, and persistence—including inbox/outbox logic, sequence numbering, and fan-out to recipients.

4. Media & File Service
   Handles upload, storage, deduplication, and retrieval of media/files; interfaces with DFS and state cache for metadata and thumbnails.

5. Secret Chat Relay
   Orchestrates end-to-end encrypted (E2EE) secret chats using client-side key exchange; bypasses cloud storage and relies on direct peer-to-peer or relayed encrypted payloads.

##Data flow
![Telegram Media Message Flow (Upload & Propagate)](../../docs/diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

PlantUML code: ../../../docs/diagrams/src/telegram/sequence-diagram/media-message-flow.puml

Group selected: “2. Send Message (with File Ref)”
After media is uploaded and stored (Step 1), the client sends a sendMessage RPC with the file ID. The MTProto Gateway validates the session (Auth Service), then the Message Service persists the message (to Inbox/Outbox) and increments sequence numbers. It returns an assigned message ID and triggers asynchronous event publishing via Kafka.

Components involved:
- Client → MTProto Gateway (RPC)
- MTProto Gateway ↔ Auth Service (session validation)
- MTProto Gateway → Message Service (message request)
- Message Service ↔ Shared DB (persist message + seq)
- Message Service → Kafka Event Bus (publish NewMessageUpdate)

Data exchanged: file ID, peer ID, session token, message metadata, sequence number.

##Deployment
![Telegram Deployment Diagram (Physical View)](../../docs/diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

PlantUML code: ../../../docs/diagrams/src/telegram/deployment-diagram/deployment-diagram.puml

Briefly describe where the components are deployed:
Clients (mobile/desktop/web) connect to the Edge / Connection Layer (MTProto Gateway + Bot API Frontend) in Telegram’s global infrastructure (Primary DC). Core services (Auth, Message, Media, Channel, Push) run as pods in the Compute Cluster (App Engine), communicating via RPC (TL-Schema). State Cache (Redis), Sharded Chat DB, and Distributed File System (DFS) reside in dedicated Storage Clusters, with DFS likely spanning multiple regions. Event Bus (Kafka) runs in a separate cluster for async propagation. External integrations (SMS, Push, 3rd-party bots) communicate over HTTPS/Webhooks or SMPP.

##Assumptions
1. Deduplication in Media & File Service: I assume uploaded media files are deduplicated by hash (e.g., SHA-256) across users to save storage—especially for popular stickers, photos, or forwarded content.
2. Kafka for Fan-out: I assume the Event Bus (Kafka) is used for asynchronous fan-out of message updates to online devices, rather than real-time push from Message Service directly.

##Open questions
1. How are secret chats actually routed—do they use the same MTProto Gateway, or a separate hardened relay path?
2. What consistency model is used for the Sharded Chat DB during high-concurrency group messages (e.g., eventual vs. strong consistency)?

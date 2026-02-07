## Product Choice
Telegram
desktop.telegram.org/
Telegram is a cross-platform, cloud-based instant messaging service developed by Telegram Messenger LLP.
## Main components
![Telegram Component Diagram](diagrams/src/telegram/component-diagram.puml)
Auth & Session Service: 
Checking user authorization and session management
Channel/Broadcast Service: 
Managing channels and broadcasts
Message Handling Service: 
Handling messages
Notification/Updates Service: 
Sending notifications and updates
Media & File Service: 
Handling media and files

## Data Flow
![Telegram Sequence Diagram](diagrams/src/telegram/sequence-diagram.puml)
Connection Layer:
- Client connects to the server using MTProto protocol
Media Upload (Encrypted Parts):
- Select Photo & send
- RPC: saveFilePart
- Stream file data
- Write File Chunk
## Deployment
![Telegram Deployment Diagram](diagrams/src/telegram/deployment-diagram.puml)
Based on this deployment diagram, the components are deployed in the following locations:

**1. Client Tier (User Devices)**
- Telegram Mobile App: Deployed on user smartphones (iOS/Android)
- Telegram Desktop App: Deployed on user computers
- Telegram Web Client: Deployed in web browsers as web applications

**2. Telegram Global Infrastructure (Primary Data Center)**
All core services are deployed within Telegram's cloud infrastructure:
- **Edge Layer:** MTProto Gateway, Bot API Frontend (entry points)
- **Compute Cluster:** All microservices (Auth, Message, Channel, Media, Push) in containerized pods
- **Data Layer:** Sharded Chat Database, Distributed File System, Redis Cache cluster
- **Middleware:** Kafka/Event Bus cluster for asynchronous communication

**3. External/Third Party Infrastructure**
- **External Bot Logic:** Deployed on third-party servers outside Telegram
- **SMS Providers:** Deployed in external SMS service infrastructure
- **Push Services:** Deployed in Google (FCM) and Apple (APNs) cloud infrastructure

The architecture follows a centralized cloud deployment model with client applications distributed to end-user devices, while all core business logic and data reside in Telegram's primary data center, connected to external providers for SMS and push notifications.
## Assumptions
1. "I assume Telegram implements eventual consistency with conflict-free replicated data types (CRDTs) for message delivery across user sessions (mobile/desktop/web) to handle synchronization without strict locking mechanisms."

2. "I assume Telegram uses geographically distributed edge proxies for the MTProto Gateways (not shown in this single-DC diagram) to reduce latency by routing users to the nearest entry point while connecting back to the primary data center for stateful operations."
## Open questions
1. "How does Telegram implement cross-data-center replication and failover for stateful services? Are there active-active regions with consensus protocols (like Raft/Paxos) or simply active-passive backups with cold standby?"
2. "How does Telegram handle data migration and schema evolution?

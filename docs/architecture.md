## Product Choice

**Product name:** Telegram  
**Website:** <https://telegram.org/>  
**Description:** Telegram is a cloud-based messaging platform that allows users to exchange messages, media files, and make voice and video calls securely across multiple devices.

---

## Main components

![Telegram Component Diagram](../../../docs/diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

[Telegram Component Diagram Code](../../../docs/diagrams/src/telegram/component-diagram.puml)

### 1. Mobile Client

The Mobile Client provides the user interface and allows users to send messages, upload media, and interact with Telegram services.

### 2. API Gateway

The API Gateway acts as the main entry point for client requests. It routes incoming requests to the appropriate backend services and handles request validation.

### 3. Authentication Service

The Authentication Service manages user login, verification using phone numbers or codes, and session management for secure access.

### 4. Messaging Service

The Messaging Service processes message delivery, synchronization between devices, and message storage logic.

### 5. Media Storage Service

The Media Storage Service stores and retrieves user-uploaded files such as images, videos, and documents, ensuring fast and reliable access.

---

## Data flow

![Telegram Sequence Diagram](../../../docs/diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

[Telegram Sequence Diagram Code](../../../docs/diagrams/src/telegram/component-diagram.puml)

### Example user action: Sending a message

1. The Mobile Client sends a message request to the API Gateway.
2. The API Gateway forwards the request to the Authentication Service to verify the user's session.
3. After successful verification, the request is sent to the Messaging Service.
4. The Messaging Service stores the message in the database and prepares it for delivery to the recipient.
5. If the message contains media, the Media Storage Service stores the file and provides a reference link to the Messaging Service.

**Components interaction:**

- Mobile Client → API Gateway  
- API Gateway → Authentication Service  
- API Gateway → Messaging Service  
- Messaging Service → Media Storage Service  
- Messaging Service → Database  

**Data exchanged:**

- Authentication tokens  
- Message text and metadata  
- Media files and storage references  
- Delivery status information  

---

## Deployment

![Telegram Deployment Diagram](../../../docs/diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

[Telegram Deployment Diagram Code](../../../docs/diagrams/src/telegram/deployment-diagram.puml)

The Mobile Client is deployed on user devices such as smartphones and desktops. Backend services including Messaging, Authentication, and API Gateway are deployed on distributed cloud servers. Databases and media storage systems are hosted on server clusters to ensure high availability, scalability, and fault tolerance.

---

## Assumptions

1. I assume Telegram uses distributed databases to synchronize user messages across multiple devices.
2. I assume the Media Storage Service uses caching and file compression to improve performance and reduce bandwidth usage.

---

## Open questions

1. How does Telegram internally manage encryption keys for secret chats?
2. What load balancing strategies are used to distribute traffic between Telegram servers?

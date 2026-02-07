# Product Architecture Analysis

## Product Choice

* **Product:** Telegram
* **Website:** [https://telegram.org](https://telegram.org)
* **Description:** A cloud-based mobile and desktop messaging app with a focus on security and speed.

## Main components

![Component Diagram](../../docs/diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

[Link to PlantUML Code](../../docs/diagrams/src/telegram/component-diagram.puml)

### Component Descriptions

1. **Client App (Mobile/Desktop):** The user interface that allows users to send messages, manage chats, and view media.
2. **Load Balancer:** Distributes incoming network traffic across multiple servers to ensure no single server bears too much load.
3. **Authentication Service:** Handles user registration, login verification via SMS codes, and session management.
4. **Message Handling Service:** Processes incoming messages, stores them in the database, and routes them to the correct recipient.
5. **Notification Service:** Interacts with Apple (APNs) and Google (FCM) push notification servers to alert users about new messages when the app is closed.

## Data flow

![Sequence Diagram](../../docs/diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

[Link to PlantUML Code](../../docs/diagrams/src/telegram/sequence-diagram.puml)

### Flow Description (Sending a Message)

This group describes the process of a user sending a text message.

1. The **Client App** sends the message data to the **Load Balancer**, which forwards it to the **Message Service**.
2. The **Message Service** saves the message into the **Database**.
3. Once saved, the **Message Service** triggers the **Notification Service**.
4. The **Notification Service** sends a signal to the Recipient's device, notifying them of a new message.

## Deployment

![Deployment Diagram](../../docs/diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

[Link to PlantUML Code](../../docs/diagrams/src/telegram/deployment-diagram.puml)

### Deployment Description

The system is deployed using a hybrid approach. Client applications run on user devices (iOS, Android, Desktop). The backend infrastructure is hosted in distributed Data Centers, likely using container orchestration (like Kubernetes) to manage microservices (Auth, Message, Notification services) ensuring high availability and scalability.

## Assumptions

1. I assume that the **Media Storage System** uses a content delivery network (CDN) or distributed caching to speed up the download of images and videos for users in different regions.
2. I assume that **Secret Chats** bypass the standard message storage database and use end-to-end encryption where keys are only stored on user devices.

## Open questions

1. What specific database technology does Telegram use to handle billions of messages daily with such high speed (is it custom-built or based on Cassandra/Postgres)?
2. How does the system handle data consistency between different data centers when a user moves from one geographical region to another?

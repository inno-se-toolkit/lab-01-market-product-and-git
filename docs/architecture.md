## Product Choice

Name: Telegram

[Link to Telegram site](https://telegram.org/)

Telegram is popular messanger with many features, including ton.

## Main components

![Telegram Component Diagram](./diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

[Telegram Component Diagram code](./diagrams/src/telegram/component-diagram.puml)

1. **Mobile App (Client)**: The user interface running on iOS/Android that handles user input, local caching, and displaying messages.
2. **Load Balancer**: Distributes incoming network traffic across multiple servers to ensure no single server becomes overwhelmed.
3. **Authentication Service**: Manages user login via SMS codes, handles sessions, and ensures secure access to the account.
4. **Message Database**: A distributed storage system that persists chat history, user metadata, and message status.
5. **Push Notification Service**: Interacts with Apple APNs and Google FCM to send alerts to user devices even when the app is closed.

## Data flow

![link](./diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

[link to the PlantUML](C:\software-engineering-toolkit\lab-01-market-product-and-git\docs\diagrams\src\telegram\sequence-diagram.puml)

In the **"Message Delivery"** group (Flow), the following happens:

1. The **Mobile App** sends an encrypted message payload to the **Load Balancer**.
2. The **Load Balancer** forwards the request to the **Messaging Server**.
3. The **Messaging Server** saves the message into the **Message Database** and returns a success confirmation (single checkmark) to the sender.
4. Simultaneously, the **Messaging Server** triggers the **Push Notification Service** to alert the recipient about the new message.

## Assumptions

1. I assume that the **Authentication Service** uses a temporary caching layer (like Redis) to store SMS codes for quick validation and rate limiting.
2. I assume the **Media Storage** system implements deduplication logic, so if a popular meme is forwarded 1000 times, it is stored physically only once to save space.

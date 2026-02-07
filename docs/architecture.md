# Product Architecture Documentation

## Product Choice
**Product name:** Telegram  
**Website:** https://telegram.org  

Telegram is a cloud-based messaging platform that allows users to exchange messages, media, and files with a strong focus on speed, scalability, and security.

---

## Main components

1. **Client Applications (Mobile / Desktop / Web)**  
   Provide the user interface and handle user interactions such as sending messages, uploading media, and displaying chats.

2. **API Gateway**  
   Acts as a single entry point for all client requests, handling authentication, request validation, and routing to backend services.

3. **Messaging Service**  
   Responsible for processing, storing, and delivering messages between users, including message synchronization across devices.

4. **Media Storage Service**  
   Stores and serves media files such as photos, videos, and documents uploaded by users.

5. **User & Authentication Service**  
   Manages user accounts, login sessions, authentication tokens, and access control.

---

## Data flow

**Selected flow: Sending a message**

1. The user sends a message from the Client Application.
2. The request is sent to the API Gateway, which verifies authentication.
3. The Messaging Service processes and stores the message.
4. Media files are uploaded to the Media Storage Service if present.
5. The message is delivered to the recipient’s client application.

---

## Deployment

Telegram client applications run on user devices.  
Backend services (API Gateway, Messaging Service, Authentication Service, Media Storage Service) run on distributed cloud servers behind load balancers for scalability and availability.

---

## Assumptions

- The Messaging Service is horizontally scalable and uses sharding.
- Media files are stored in distributed object storage with replication.

---

## Open questions

- How is end-to-end encryption implemented and managed for secret chats?
- What caching strategies are used to reduce latency for messages and media?

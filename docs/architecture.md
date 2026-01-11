# Product Architecture: ChatGPT

## 1. Product Choice
I chose ChatGPT because it is the most influential AI product today. As a tech specialist, I am fascinated by how a large language model is integrated into a user-friendly interface that handles millions of requests. Understanding how the web interface communicates with complex AI models is crucial for a modern engineer.

## 2. Modules & Data Flow
### Modules:
- **Web/Mobile UI (Client):** The interface where users type prompts and see the AI's response.
- **API Gateway:** The entry point that manages user requests, authentication, and rate limiting.
- **Inference Engine:** The core module where the actual AI model (like GPT-4) runs and generates text.
- **Conversation History Service:** A service that saves and retrieves past chats so users can continue their sessions.
- **Database:** Stores user account data, preferences, and chat logs.
- **Moderation Layer:** An automated system that checks prompts and responses for safety and policy violations.

### Data Flow:
When a user sends a prompt, the Client sends it to the API Gateway. The Gateway authenticates the user and passes the text to the Moderation Layer. If it's safe, the prompt goes to the Inference Engine. The engine generates a response, which is then saved by the Conversation History Service into the Database and streamed back to the Client in real-time.

## 3. Deployment (High Level)
- **Client-side:** Runs in web browsers or as a mobile app on user devices.
- **Server-side:** Complex GPU clusters in the cloud (Azure/OpenAI infrastructure) to run the AI models and backend services.

## 4. Things I am not sure about
1. I am not sure how they manage to stream the text word-by-word so quickly despite the heavy computations of the model.
2. I am curious about the specific load balancing techniques used to distribute requests between thousands of GPUs.
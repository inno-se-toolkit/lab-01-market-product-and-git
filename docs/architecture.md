## Product Choice
Telegram (link: https://web.telegram.org/a/)
> a worldwide cross-platform social network. It allows users to send text messages, images, videos, etc.

## Main components
![Telegram Component Diagram](docs/diagrams/out/telegram/component-diagram/Component%20Diagram.svg)
Link to the PlantUML code for the diagram: ![code](docs/diagrams/src/telegram/component-diagram.puml).

Some components of the app:
1. **Channel/Broadcast Service**. This service is used for managing data from different sources (channels)
2. **Message handling Service**. It is used for processing all the evnts related to the messages sent between users
3. **MTProto Gateway**. The Gateway works as the entry point for all client connections and actions related to the use of MTProto security protocol
4. **Notification/Updates Service**. This service is responsible for sending notifications to the users and provide information about any released updates
5. **Media & File Service**. This component processes various operations on files, such as uploading them, sending in the chats, etc.

## Data flow
![Telegram Sequence Diagram](docs/diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)
Link to the PlantUML code for the diagram: ![code](docs/diagrams/src/telegram/sequence-diagram.puml).

Description of 'Send Message' block:
Firstly, the procedural call of sending a message from user is invoked. It connects to the MTProto Gateway 
to enable further processing. Auth Service validates the session. Then, the Message Service increments the *pts* 
in cache and persists message with the help of Sharded DB. The ID gets assigned to the message, and the  RPC responce 
is sent to the client side. After that, the UI gets updated, so that the user can see the message. 

## Deployment
![Telegram Deployment Diagram](docs/diagrams/out/telegram/deployment-diagram/Deployment Diagram.svg)
Link to the PlantUML code for the diagram: ![code](docs/diagrams/src/telegram/deployment-diagram.puml)

The used protocols: TCP, Native DB Proto, HTTP/2 (APNs/FCM), etc.

## Assumptions
I assume the cloud storage system implements deduplication to optimize storage costs for shared media files.
Also, I assume that MTProto is responsible for data security.

## Open questions
1. How exactly does MTProto Gateway manages all the operations it is used in?
2. In what way was the engine for Sharded Chat DB customized?

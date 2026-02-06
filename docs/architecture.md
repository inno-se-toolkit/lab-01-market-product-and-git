## Product Choice
Telegram 
https://web.telegram.org/
The popular app to communicate with others.

## Main components

![Telegram Component Diagram](diagrams/out/telegram/component-diagram/Component_Diagram.svg)

![Telegram Component Diagram code](diagrams\src\telegram\component-diagram.puml)

Auth & Session Service - working with authetication of users
Notification/Updates Service - notify users new impovements and new message
Media & File Service - store/delete/add files
Bot API Server - the server that compute all requests
SMS Providers - working with storing/sending users' messages

## Data flow

![Telegram Sequence Diagram](diagrams/out/telegram/sequence-diagram/Sequence_Diagram.svg)  

![Telegram Sequence Diagram code](diagrams\src\telegram\sequence-diagram.puml)

Send Message:
1. User send message
2. Check the validation of the request
3. Process the message request to the server
4. Sending message to the user
3. Return the status of the message

They share with CSRF-Token, Auth-token, Message body, other status...

## Deployment

![Telegram Deployment Diagram](diagrams/out/telegram/deployment-diagram/Deployment_Diagram.svg)   

![Telegram Deployment Diagram code](diagrams\src\telegram\deployment-diagram.puml)

On user device stored the App and the cache, on the main server they have main server that compute most of the requests. They also have some other external services with that they communicate and integrate.

## Assumptions
I assume they use cloud storage system to optimaze the storing of users' data and media files.
I assume they use microservices to separate the load of all requests.

## Open questions
How do they optimize searching free logins when user create new account?
How did they separate the databases and optimize it?
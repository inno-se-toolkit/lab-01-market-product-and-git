## Product Choice
Telegram
https://web.telegram.org/
Telegram is a fast, secure, cloud-based messaging app.


## Main components
![Telegram Component Diagram](docs/diagrams/out/telegram/component-diagram/Component%20Diagram.svg)
docs/diagrams/src/telegram
/component-diagram.puml

-Mobile App (iOS/Android)
-Desktop App
-Web Client (K/Z)
Fronted components for different devices.

-Distributed File System (DFS)
Backend component for storage.

-Notification/Updates Service
Backend  component for real time monitoring and updates.


## Data flow
![Telegram Component Diagram](docs/diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)
docs/diagrams/src/telegram/sequence-diagram.puml
Media Upload (Encrypted Parts)
Photo gets transfered from Client to Data & Middleware

Mobile App sends file to
MTProto Gateway sends stream file data to media service sends:
  Write file chunk to Distributed DFS
  Save file metadata to Sharded DB


## Deployment
![Telegram Component Diagram](docs/diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)
https://github.com/ivan84201/lab-01-market-product-and-git/blob/main/docs/diagrams/src/telegram/deployment-diagram.puml
Backend components are deployed in Telegram Global Infrastructure (Primary DC), frontend components are deployed on client devices, External Bot Logic is deployed on Third-Party servers.


## Assumptions
life is meaningless
gambling is awesome


## Open questions
where should i exist

## Product choice

Telegram
<https://web.telegram.org/>
Telegram (also known as Telegram Messenger) is a cloud-based, cross-platform social media and instant messaging (IM) service. It launched for iOS on 14 August 2013 and Android on 20 October 2013. It allows users to exchange messages, share media and files, and hold private and group voice or video calls as well as public livestreams

![Telegram Component Diagram](./diagrams/out/telegram/component-diagram/Component%20Diagram.svg)
[Telegram Component Diagram code](./diagrams/src/telegram/component-diagram.puml)

### Bot API server

Server which hosts API for telegram bots

### Desktop App

The component responsible for desktop version of the telegram

### Mobile App

The component responsible for mobile version of the telegram

### Web client

The component responsible for web version of the telegram

### Notification/Updates Service

The component responsible for notifications

## Data flow

![Telegram Sequence Diagram](./diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)
[Telegram Sequence Diagram code](./diagrams/src/telegram/deployment-diagram.puml)

Bot API server communicates with different versions of telegram using connections layer

## Deployment

![Telegram Component Diagram](./diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)
[Telegram Component Diagram code](./diagrams/src/telegram/deployment-diagram.puml)

## Assumptions

I assume the cloud storage system implements deduplication to optimize storage costs for shared media files
I assume that sms providers are external ecosystems because it is easier to provide sms messages in different countries

## Open questions

How does the data flow look like in secret chats?
How does telegram can store so many messages?

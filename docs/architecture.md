Product's name: Telegram
Product's Website: https://telegram.org/
Product's Description: A new era in messaging. Private communication and a user-friendly interface.

![Telegram Component Diagram](../../../docs/diagrams/out/telegram/component-diagram/Component%20Diagram.svg)
![Telegram Component Diagram Code](../../../docs/diagrams/src/telegram/component-diagram.puml)

Components:
Desktop App - This is the program users install on their computer to chat in Telegram.
Bot API Server - This is the server that lets developers create and control Telegram bots.
Secret Chat Relay — This is the system that sends secret messages safely between users.
Auth & Session Service — This service checks who you are and keeps you logged in.
Media & File Service — This service stores and sends photos, videos, and files.

![Telegram Sequence Diagram](../../../docs/diagrams/out/telegram/component-diagram/sequence-diagram.svg)
![Telegram Sequence Diagram Code](../../../docs/diagrams/src/telegram/sequence-diagram.puml)


group #F9F9F9 1. Media Upload (Encrypted Parts)
    note right of App: Media is uploaded via 'saveFilePart'\nbefore the message is sent.

    Alice -> App: Select Photo & Send
    App -> Gateway: RPC: saveFilePart (bytes, file_id_A)
    activate Gateway
    
    Gateway -> MediaSvc: Stream File Data
    activate MediaSvc
    
    MediaSvc -> DFS: Write File Chunk
    DFS -->> MediaSvc: Checksum OK
    
    MediaSvc -> DB: Save File Metadata (Owner: Alice)
    MediaSvc -->> Gateway: Part Saved
    deactivate MediaSvc
    
    Gateway -->> App: ACK (Part Saved)
    deactivate Gateway
    
    note right of App: App repeats until file is fully uploaded.
end

In that block:
- Alice chooses a photo and presses send.
- The app starts sending the photo in small parts.
- Each part is sent to the server.
- The server passes it further so it can be stored.
- The system saves the data and checks that it was saved correctly.
- The system also remembers who sent the photo.
- The server sends back a message that this part was saved.
- The app gets the confirmation.
- The app repeats this until the whole photo is sent.

![Telegram Deployment Diagram](../../../docs/diagrams/out/telegram/component-diagram/deployment-diagram.svg)
![Telegram Deployment Diagram Code](../../../docs/diagrams/src/telegram/deployment-diagram.puml)

Components:
The apps are on user devices: on a phone, on a computer, and in a web browser.
External services are outside the system on other servers.
All main services are in the cloud data center.
Inside the data center there are servers for logic, storage, and messaging, and they work together.

Assumptions:
- I assume all main services run in the same primary cloud data center.
- I assume user apps (mobile, desktop, web) only connect to the system through gateway servers, not directly to internal services.
- I assume media files are stored separately from chat data in a dedicated storage system.
- I assume external services (SMS and push notifications) are outside of Telegram’s infrastructure and are accessed over the internet.

Open questions:
- How exactly are messages encrypted and decrypted inside the system?
- How is data replicated between different data centers?
- What internal rules are used to scale services when the load increases?

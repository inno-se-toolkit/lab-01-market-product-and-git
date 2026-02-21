# Product Architecture: Telegram

## Product Choice
* **Product name:** Telegram
* **Website:** https://telegram.org
* **Description:** A cross-platform, cloud-based instant messaging service that provides end-to-end encrypted video calling, VoIP, file sharing, and other features.

## Main components
![Telegram Component Diagram](../docs/diagrams/out/telegram/component-diagram/Component%20Diagram.svg)
[Link to PlantUML source](../docs/diagrams/src/telegram/component-diagram.puml)

### Description of Components:
*Задание требует описать 5 компонентов. Глядя на диаграмму (она лежит в папке `docs/diagrams/out/telegram/`), опиши своими словами:*
1. **API Gateway:** Точка входа для всех запросов клиентов.
2. **Auth Service:** Отвечает за проверку кодов из СМС и паролей.
3. **Chat Service:** Логика отправки и получения сообщений.
4. **Media Storage:** Хранилище для твоих фото и видео.
5. **Push Notification Service:** Отправляет уведомления на твой MateBook или телефон.

## Data flow
![Telegram Sequence Diagram](../docs/diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

## Deployment
![Telegram Deployment Diagram](../docs/diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

## Assumptions
* I assume that Telegram uses a distributed database system to handle global traffic.
* I assume that the CDN is used to speed up media delivery for users worldwide.
## Product Choice

- Yandex go
- <https://go.yandex>
- Mobile app for order a taxi, a food and other options from Yandex company.

## Main components

![Yandex Go Component Diagram](../docs/diagrams/out/yandex-go/architecture-component/Component%20Diagram.svg)

[Telegram Component Diagram Code](../docs/diagrams/src/yandex-go/architecture-component.puml)

1. Mobile App
This is the application on a phone. You use it to order taxi or food.

2. Web App
This is the website version. You can use it on your computer to order services.

3. User Service
This service keeps your information - name, phone number, and order history.

4. Payment Service
This service processes your payments when you order something.

5. Maps & Routing Service
This service finds the best way. It shows drivers where to go and calculates travel time.

## Data flow

![Yandex Go Sequence Diagram](../docs/diagrams/out/yandex-go/architecture-sequence/Sequence%20Diagram.svg)

[Telegram Component Diagram Code](../docs/diagrams/src/yandex-go/architecture-sequence.puml)

Booking & Async Dispatch

What happens in this group: User do the order in the mobile app. App sends booking request to the API Gateway, system starts looking for a driver - dispatch service searches for available drivers nearby. Booking is confirmed asynchronously - user sees "Looking for driver" message.

Components that talk to each other:
Mobile App and API Gateway. Data exchanged: Ride details, payment method, user preferences

API Gateway and Dispatch Service. Data exchanged: Ride request with location and requirements

## Deployment

![Yandex Go Sequence Diagram](../docs/diagrams/out/yandex-go/architecture-deployment/Deployment%20Diagram.svg)

[Telegram Component Diagram Code](../docs/diagrams/src/yandex-go/architecture-deployment.puml)

1. User Devices deplied in user smarthone.
2. Yandex go Web app - in user web brauser.
3. API Gateway in Yandex Cloud. It includes kubernetes cluster.

## Assumptions

I assume the pricing service handles surge pricing calculations based on demand and supply in real-time.

I assume the Dispatch Service uses real-time geolocation and machine learning

## Open questions

How does the actual load balancing mechanism work between the microservices in production?

How does the system prioritize between different types of requests?

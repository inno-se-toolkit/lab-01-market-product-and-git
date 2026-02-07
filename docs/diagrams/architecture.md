## Product Choice

- Yandex Go

- https://go.yandex/ru_ru/

- This service allow users to call a taxi, or deliver something from one point to another

  
## Main components

![Yandex Go Component Diagram](out/yandex-go/architecture-component/ComponentDiagram.svg)

[Link to PlantUML source code](src/yandex-go/architectureComponent.puml)

- API Gateway – Acts as the single entry point for the mobile application, routing incoming requests to the appropriate microservices while handling authentication and rate limiting.

- Pricing Engine – Calculates trip fares in real-time by analyzing dynamic factors such as current demand (surge), traffic congestion, weather conditions, and driver availability.

- Matching Service – Responsible for instantly identifying and assigning the most suitable nearby driver to a customer's request to minimize wait times.

- Notification Service – Manages the delivery of push notifications and SMS alerts to both users and drivers regarding order status, car arrival, or in-app messages.

- Payment Service – Handles secure credit card integration and transaction management, including initial fund authorization (holds) and final payment processing.

## Deployments

![Deployment diagram](out\yandex-go\architecture-deployment\DeploymentDiagram.svg)
[Link to plantUML source code](src\yandex-go\architecture-deployment.puml)

The backend microservices of Yandex Go are primarily deployed in Docker containers orchestrated by Kubernetes (K8s) clusters. These clusters reside within Yandex Cloud infrastructure and internal private data centers to ensure high availability and geographic redundancy. The client-side logic is deployed natively on iOS and Android devices, while static asssets (like map tiles and UI icons) are distributed through a Content Delivery Network (CDN) to minimize latency for users across different regions.

## Assumptions
Real-time Geofencing: I assume the Geo/Routing Service utilizes high-precision geofencing to trigger specific pricing rules or service availability notifications as soon as a user enters or leaves defined city zones.

Predictive Matching: I assume the Matching Service incorporates machine learning models to predict where demand will be highest in the next 15–30 minutes, proactively suggesting "hot zones" to drivers to reduce pickup times.

## Open questions
Cold Storage & Compliance: How does Yandex Go manage the long-term storage and encryption of GPS traces and user data to comply with local data sovereignty laws while maintaining system performance?

Failover Orchestration: In the event of a total regional data center outage, what is the specific automated failover RTO (Recovery Time Objective) for shifting millions of active "in-ride" sessions to a backup region without losing real-time tracking?
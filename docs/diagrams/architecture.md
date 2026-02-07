## Product Choice
1. Yandex Go
2. https://go.yandex/
3. Yandex's mobile app for transportation and delivery
## Main components
1. ![Yandex Go Component Diagram](https://github.com/Erusiaaa/lab-01-market-product-and-git/tree/main/docs/diagrams/out/yandex-go/architecture-component/Component%20Diagram.svg)
2. https://github.com/Erusiaaa/lab-01-market-product-and-git/blob/main/docs/diagrams/src/yandex-go/architecture-component.puml
3. Mobile App
The mobile app is the program people use on their phones to order rides and see information. It sends requests to the server and shows results to the user.

API Gateway
The API Gateway is the main entry point for all requests from apps. It receives requests and sends them to the correct internal service.

User Service
The User Service stores and manages user accounts, profiles, and settings. It helps the system know who is using the app.

Dispatch Service
The Dispatch Service finds the best driver for a ride request. It connects passengers with available drivers nearby.

Payment Service
The Payment Service processes payments for rides and other services. It works with external payment systems to complete transactions.
## Data flow
1. ![Yandex Go Sequence Diagram](https://github.com/Erusiaaa/lab-01-market-product-and-git/tree/main/docs/diagrams/out/yandex-go/architecture-sequence/Sequence%20Diagram.svg)
2. https://github.com/Erusiaaa/lab-01-market-product-and-git/blob/main/docs/diagrams/src/yandex-go/architecture-sequence.puml
3. Geospatial Search (Drivers)
4. Maps & Pricing Service (or a dedicated Pricing Service) receives the ride request details: pickup location, destination, time, and selected class.
The service checks real-time demand data in the requested zone.
If demand is high, a surge multiplier is applied to the base fare.
The adjusted price is passed back as part of the ride options.
## Deployment
1. ![Yandex Go Deployment Diagram](https://github.com/Erusiaaa/lab-01-market-product-and-git/tree/main/docs/diagrams/out/yandex-go/architecture-deployment/Deployment%20Diagram.svg)
2. https://github.com/Erusiaaa/lab-01-market-product-and-git/blob/main/docs/diagrams/src/yandex-go/architecture-deployment.puml
This is the physical deployment diagram of Yandex Go. Users connect via mobile app or browser. The backend runs on Kubernetes, split into two clusters: one for the core application services (like dispatch and payments) and another for data services (like Redis, Kafka, and databases). They communicate via gRPC and HTTPS.
## Assumptions
I assume the pricing service handles surge pricing calculations based on demand and supply in real-time.
Yandex Go integrates external mapping and traffic data providers to ensure accurate ETAs and navigation.
## Open questions
How does the actual load balancing mechanism work between the microservices in production?
How does Yandex Go synchronize real-time location updates across distributed services without causing latency or data inconsistency?


## Product Choice
- **Product name**: Yandex Go
- **Link**: https://go.yandex/
- **Description**: Yandex Go is a multi-service platform offering ride-hailing, food delivery, and courier services. It connects users with drivers, restaurants, and couriers through a mobile and web application.

## Main components

![Yandex Go Component Diagram](./diagrams/out/yandex-go/architecture-component/Component%20Diagram.svg)

[Yandex Go Component Diagram Code](./diagrams/src/yandex-go/architecture-component.puml)

Selected components:

1. **API Gateway**  
   Acts as a single entry point for all client requests, routing them to appropriate internal services using gRPC and handling protocol translation.

2. **Dispatch Service**  
   Manages driver-rider matching by performing geospatial searches for available drivers and running matching algorithms in real-time.

3. **Pricing Service**  
   Calculates ride costs based on route data, traffic conditions, tariff rules, and dynamic surge pricing during high demand.

4. **Payment Service**  
   Handles payment processing, validates payment methods, initiates transactions, and integrates with external payment systems like Yandex Pay.

5. **Maps & Routing Service**  
   Provides geospatial functionality including route calculation, traffic data, and integration with Yandex Maps API for navigation and ETAs.

## Data flow

![Yandex Go Sequence Diagram](./diagrams/out/yandex-go/architecture-sequence/Sequence%20Diagram.svg)

[Yandex Go Sequence Diagram Code](./diagrams/src/yandex-go/architecture-sequence.puml)

**Selected group**: "Booking & Async Dispatch" (steps 17-30)

**Description**:  
This flow begins when a user confirms a ride booking. The API Gateway receives the `createOrder` request and forwards it to core services. The Payment Service validates the payment method, then the Dispatch Service persists the order with status "SEARCHING" and performs a geospatial search for nearby drivers. Once a driver is matched, the order status updates to "ASSIGNED" and a `RideAssigned` event is published to Kafka. The Notification Service consumes this event and sends a push notification to the user's device while the app updates the map to show the assigned driver.

**Component interactions**:
- Mobile App → API Gateway: Sends `createOrder` with ride class and payment ID
- API Gateway → Payment Service: Validates payment method
- Dispatch Service → Operational DB: Persists order and updates status
- Dispatch Service → Kafka: Publishes `RideAssigned` event
- Notification Service → Push Service: Sends "Driver Found" notification

## Deployment

![Yandex Go Deployment Diagram](./diagrams/out/yandex-go/architecture-deployment/Deployment%20Diagram.svg)

[Yandex Go Deployment Diagram Code](./diagrams/src/yandex-go/architecture-deployment.puml)

**Deployment description**:  
The system is deployed across multiple environments. User-facing mobile apps run on iOS/Android devices, while the web app runs in browsers. The backend services are containerized and orchestrated within a Kubernetes cluster in the application tier. Core microservices (User, Dispatch, Pricing, Payment, etc.) run as pods within this cluster. Supporting infrastructure includes a Redis Cluster for caching, a Kafka Message Broker Cluster for event streaming, and a Data Storage Cluster with ClickHouse for analytics and YDB for operational data. External services like Yandex Pay and Yandex Maps APIs are hosted in separate Kubernetes clusters.

## Assumptions

1. **Surge pricing algorithm**: I assume the Pricing Service uses real-time demand-supply ratios, historical patterns, and traffic conditions to calculate dynamic pricing multipliers.

2. **Driver matching logic**: I assume the Dispatch Service uses a combination of proximity, driver rating, ride history, and current driver workload to optimize matching.

3. **Event-driven architecture**: I assume Kafka is used not only for notifications but also for maintaining eventual consistency between services and enabling real-time analytics.

4. **Geospatial indexing**: I assume YDB or a specialized geospatial database is used to efficiently query nearby drivers using spatial indexes.

## Open questions

1. **Load balancing strategy**: How does the API Gateway distribute traffic between multiple instances of the same microservice? Is it round-robin, least connections, or based on health checks?

2. **Data consistency approach**: How are distributed transactions handled between services like Payment and Dispatch when a booking fails after payment authorization?

3. **Monitoring and observability**: What specific tools (Prometheus, Grafana, Jaeger) are used for monitoring service health, tracing requests across services, and logging?

4. **Multi-tenancy handling**: How does the system isolate data and traffic between different service types (ride-hailing vs food delivery) within the same infrastructure?

5. **Disaster recovery**: What is the RPO/RTO for critical services, and how is data replicated across geographical regions?
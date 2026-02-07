## Components and roles
- Mobile app
  - Mobile engineer (iOS/Android)
  - QA
  - ...
- Payment service
  - Back-end engineer
  - DevOps
  - QA
- ...
## Roles and responsibilities
Mobile App & Web App

Mobile Engineer (iOS/Android): Developing the client-side logic and interface.

Frontend Engineer: Building and maintaining the Web version of the service.

UI/UX Designer: Designing user journeys, maps integration visuals, and layouts.

QA Automation Engineer (Mobile): Writing automated tests for different device types and OS versions.

API Gateway (API Layer)

Backend Engineer: Managing request routing, authentication, and rate limiting.

Security Engineer: Ensuring secure communication between clients and the internal network (SSL/TLS, OAuth).

System Architect: Defining the REST API contracts and overall system entry points.

Core Services (Notification, User, Dispatch, Pricing, Payment, Maps & Routing)

Backend Engineer (Go/C++/Java): Implementing the core business logic and gRPC interfaces.

Data Scientist / ML Engineer: Crucial for Pricing (surge pricing algorithms) and Dispatch (matching logic).

QA Engineer: Performing integration testing to ensure services communicate correctly via gRPC.

SRE (Site Reliability Engineer): Managing service uptime, horizontal scaling, and performance bottlenecks.

Data Layer (ClickHouse, Redis, YDB)

Database Administrator (DBA): Tuning performance for YDB and ClickHouse clusters.

Data Engineer: Designing schemas and ETL pipelines for the Analytics DB.

Backend Engineer: Implementing caching strategies using Redis to reduce latency.

Message Broker (Kafka/Logbroker)

Infrastructure Engineer: Maintaining the high-throughput message bus and ensuring data persistence.

DevOps Engineer: Managing the deployment and monitoring of the streaming infrastructure.

External Services (Yandex Pay, Yandex Maps)

Integration Engineer: Managing the connectivity and handling failures/timeouts from external dependencies.

Backend Engineer: Implementing the "Maps API" and "Payment Processing" abstractions to interface with external systems

## Common skills across roles

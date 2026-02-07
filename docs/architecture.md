## Product Choice

**Product name**: Yandex Go
**Website**: go.yandex
**description**: Yandex Go is a comprehensive urban mobility super-app based on Yandex.Taxi, integrating ride-hailing, food/grocery delivery, car-sharing, scooters, and city services for millions of users. It provides real-time pricing, tracking, and quick access via smart feeds.

## Main components

![Product Component Diagram](./diagrams/out/yandex-go/architecture-component/Component%20Diagram.svg)

![Product Component Diagram Code](./diagrams/src/yandex-go/architecture-component.puml)

- **Client App**: Handles user interactions like ride requests, real-time tracking on maps, payments, and service discovery via smart feeds across iOS/Android/web.
- **Matching Service**: Pairs riders with nearby drivers using algorithms considering location, vehicle type, ETA, and ratings for optimal assignments.
- **Pricing Service**: Calculates dynamic fares including base price, distance, time, and surge multipliers based on real-time supply-demand data.
- **Geolocation Service**: Tracks GPS positions of users/drivers in real-time, powering maps, ETAs, and route optimization.
- **Payment Service**: Processes transactions via cards/wallets, handles splits, refunds, and integrates with banks for secure, fast settlements.
- **Notification Service**: Sends push alerts for ride status, promotions, ETAs, and chat messages between users/drivers.

## Data flow

![Product Deployment Diagram](./diagrams/out/yandex-go/architecture-deployment/Deployment%20Diagram.svg)

![Product Deployment Diagram Code](./diagrams/src/yandex-go/architecture-deployment.puml)

In the "Ride Request Flow" group, the Client App sends ride details (pickup/dropoff locations, preferences) to the Matching Service; Matching Service queries Geolocation Service (exchanges lat/long coords, driver availability lists) and Pricing Service (receives fare quote), then responds with matched driver ID and price to Client

## Deployment

![Product Sequence Diagram](./diagrams/out/yandex-go/architecture-sequence/Sequence%20Diagram.svg)

![Product Sequence Diagram Code](./diagrams/src/yandex-go/architecture-sequence.puml)

Components deploy on Yandex Cloud Kubernetes clusters across multiple Russian data centers for low-latency; databases (e.g., PostgreSQL for users/trips) are replicated; edge CDNs cache maps/static assets; mobile apps run on user devices.

## Assumptions

- I assume the pricing service handles surge pricing calculations based on demand and supply in real-time, adjusting multipliers dynamically during peaks.
- I assume the matching service uses machine learning models trained on historical data to predict ETAs and optimize pairings beyond simple distance.
- I assume geolocation integrates with third-party maps (e.g., Yandex Maps) for traffic-aware routing.

## Open questions

- How does the actual load balancing mechanism work between the microservices in production, especially during city-wide events?
- What specific caching strategies (e.g., Redis setups) are used for high-traffic components like matching during peak hours?
- How does data flow integrate with external partners for food delivery or car-sharing expansions?

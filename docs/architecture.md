Yandex Go
https://go.yandex/

Quick taxi order, food order by Yandex Go.This is popular for Russia and use everyone.

![Yandex Go Component diagram](./diagrams/out/yandex-go/architecture-component/Component%20Diagram.svg)

![Yandex Go Deployment diagram](./diagrams/out/yandex-go/architecture-deployment/Deployment%20Diagram.svg)

Mobile App / Web App
These are the user-facing applications that allow customers to book rides, track drivers, and manage their trips from smartphones or browsers.

API Gateway
It acts as the single entry point for client requests, routing them to the appropriate core services while handling authentication, rate limiting, and request aggregation.

Dispatch Service
This service likely matches ride requests with available drivers, optimizing for factors like proximity, estimated arrival time, and driver ratings.

Pricing Service
It calculates ride fares dynamically based on factors such as distance, time, demand (surge pricing), and route conditions.

Yandex Maps
Provides mapping, geocoding, and real-time routing data essential for driver navigation, ETAs, and location-based features in the app.
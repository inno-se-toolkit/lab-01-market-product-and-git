## Product Choice
    Product name: Yandex Go  
    Link to the product's website: https://go.yandex.com
    Short description of the product: Yandex Go is a mobility platform offering ride-hailing, delivery, and car-sharing services. It connects users with drivers and couriers via a mobile/web app, using real-time geolocation, dynamic pricing, and automated dispatch.
## Main components
    ![Yandex Go Component Diagram](./diagrams/out/yandex-go/component-diagram/Component Diagram.svg)
    ![Yandex Go Component Diagram code](./diagrams/src/yandex-go/component-diagram/component-diagram.puml)
    User Service: Manages user authentication, profiles, session validation, and preferences; 
    Maps & Pricing Service: Computes routes, estimates travel time/traffic, applies tariff rules, and calculates dynamic prices (including surge); integrates with external map APIs.
## Data flow
    ![Yandex Go Ride Booking Flow](./diagrams/out/yandex-go/sequence-diagram/Sequence Diagram.svg)
    ![Yandex Go Sequence Diagram code](./diagrams/src/yandex-go/sequence-diagram/sequence-diagram.puml)
    Box: “Booking & Async Dispatch”
    The user confirms a ride → the Mobile App sends createOrder to API Gateway → Core Services initialize the order (status SEARCHING), validate payment, and persist it → Dispatch Service performs geospatial search for nearby drivers → a matching driver is assigned → the order status updates to ASSIGNED, and a RideAssigned event is published to Kafka → Push Service consumes the event and sends a push notification to the user → the app updates the map to show the driver’s location.
    Mobile App ↔ API Gateway: createOrder(class, payment_id) request; ACK (Searching UI) response.
    API Gateway ↔ User Service: validateSession(token), lookupProfile.
    API Gateway ↔ Maps & Pricing: estimateRide(coords_A, coords_B) → receives route, traffic, tariff options.
    API Gateway ↔ Dispatch Service: initializeRide(order_id), geospatialSearch(radius, coords) → receives candidate drivers.
    Dispatch Service ↔ Operational DB (YDB): persists order state (SEARCHING → ASSIGNED).
    Dispatch Service ↔ Kafka: publishes RideAssigned(order_id, driver_id, eta).
    Push Service ↔ Kafka: consumes RideAssigned; sends push via FCM/APNs.
    Push Service ↔ Mobile App: delivers push notification payload (driver ID, ETA, car info).
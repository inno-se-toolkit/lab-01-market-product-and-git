# Project Architecture

## Product Choice

**Product name:** Yandex Go
**Link:** [https://go.yandex/](https://go.yandex/)

**Description:** A super-app ecosystem that provides taxi rides, food delivery, and logistics services in one place.

## Main components

![Yandex Go Component Diagram](./diagrams/out/yandex-go/architecture-component/Component%20Diagram.svg)
[Link to PlantUML code](./diagrams/src/yandex-go/architecture-component.puml)

* **API Gateway:** A system that receives all requests from apps and sends them to the right internal services.
* **Dispatch Service:** A service that finds the best driver for a user's request in real-time.
* **Pricing Service:** Calculates the price of a trip based on distance, traffic, and current demand.
* **Notification Service:** Sends push notifications to keep users updated on their order status.
* **Operational DB (YDB):** A database used to store and manage information about active orders.

## Data flow

![Yandex Go Sequence Diagram](./diagrams/out/yandex-go/architecture-sequence/Sequence%20Diagram.svg)
[Link to PlantUML code](./diagrams/src/yandex-go/architecture-sequence.puml)

* **Ride Booking Flow:** This group of actions shows how a user books a ride.
* **Step 1:** The **API Gateway** validates the user session and asks the **Maps & Pricing** service for trip options.
* **Step 2:** Once the user chooses a price, the **Dispatch Service** searches for available drivers near the user's location.
* **Step 3:** When a driver is found, the **Push Service** (Notification) sends a message to the user's phone to show the driver is coming.

## Deployment

![Yandex Go Deployment Diagram](./diagrams/out/yandex-go/architecture-deployment/Deployment%20Diagram.svg)
[Link to PlantUML code](./diagrams/src/yandex-go/architecture-deployment.puml)

The system is hosted in the Yandex Cloud Infrastructure. The core services run inside a Kubernetes Cluster, where they are organized into "Pods" for better reliability. Databases like ClickHouse** and YDB are kept in a separate storage cluster to handle large amounts of data.

## Assumptions

* I assume the Pricing Service uses real-time traffic data from Yandex Maps to calculate the final cost.
* I assume the Message Broker (Kafka) is used to make sure no data is lost if one of the services temporarily fails.

## Open questions

* How does the system protect user payment data during a transaction with external banks?
* What happens to the "Dispatch Service" logic if the GPS signal of a driver is lost for a few minutes?

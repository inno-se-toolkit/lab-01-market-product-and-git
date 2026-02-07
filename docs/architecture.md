## Product Choice

Wildberries

https://www.wildberries.ru/

It is a russian marketplace with a wide range of goods.

## Main components

![Wildberries Component Diagram](.\diagrams\out\wildberries\architecture-component\Component Diagram.svg)

![Wildberries Component Diagram code](.\diagrams\src\wildberries\architecture-component.puml)

Customer Mobile App: It provides the mobile app of wildberries

Partner/Seller Gateway: It provides an API for partner or seller.

Auth & ID Service: It provides authorization and ID services for user.

Catalog & Search service: It provides a searching service and catalog for needed goods.

Fintech & Payment Service: It provides a payment service for ordering.

## Data flow

![Wildberries Sequence Diagram](.\diagrams\out\wildberries\architecture-sequence\Sequence Diagram.svg)

![Wildberries Sequence Diagram code](.\diagrams\src\wildberries\architecture-sequence.puml)

box "Logistics & External":
This is the part where the warehouse gets the order after payment is confirmed. The system tells the warehouse which items to pick and pack from the shelves. Then it updates the order status and lets the customer know their package is being prepared.

## Deployment

![Wildberries Deployment Diagram](.\diagrams\out\wildberries\architecture-deployment\Deployment Diagram.svg)

![Wildberries Deployment Diagram code](.\diagrams\src\wildberries\architecture-deployment.puml)

The core application services are deployed inside Wildberries' private Kubernetes cloud infrastructure. The user-facing apps run on customer devices, while databases, caches, and message brokers run as managed clusters within the same data center, connecting to external payment and logistics providers over the internet.

## Assumptions

I assumed the system successfully reserves items before payment so they aren’t sold twice.

I assumed the warehouse system won’t prepare the same order twice, even if it gets the same message more than once.

## Open questions

 How does the system recover if the payment succeeds but the "OrderPaid" event fails to be published to Kafka?

 What happens during a major database outage? Does the Cart Service have a fallback mode to allow users to keep adding items to their cart?

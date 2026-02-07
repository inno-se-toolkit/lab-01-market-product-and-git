# Product Choice
Wildberries.ru
https://www.wildberries.ru

Wildberries is a leading Russian online marketplace offering a vast selection of fashion, electronics, home goods, and more. It operates with a direct shipment model where sellers send products to Wildberries' logistics centers, which then handle storage, packaging, and delivery to customers across the country and beyond.

## Main components
![Wildberries Component Diagram](../diagrams/out/wildberries/architecture-component/Component%20Diagram.svg)

[Wildberries Component Diagram Code](../diagrams/src/wildberries/architecture-component.puml)

### Cart & Checkout Service
Handles the shopping cart state, checkout flow, and order submission initiation from the client side.

### Catalog & Search Service
Provides product catalog browsing and search functionality, including filtering and retrieving product details.

### Order Management (OMS)
Manages order lifecycle after checkout: creation, status updates, cancellations/returns, and coordination with fulfillment.

### Fintech & Payment Service
Processes payment initiation and confirmation, integrates with external payment providers, and handles payment-related validations.

### Warehouse Management (WMS)
Controls warehouse operations such as inventory updates, picking/packing workflows, and preparing orders for shipment.

## Data Flow
![Wildberries Data Flow Diagram](../diagrams/out/wildberries/architecture-sequence/Sequence%20Diagram.svg)

[Wildberries Data Flow Diagram Code](../diagrams/src/wildberries/architecture-sequence.puml)

### Checkout to order fulfillment flow

When a user adds items to the cart, the mobile application sends a request through the Storefront Gateway to the Cart Service. The Cart Service updates the session cart data and stores it in the cache with a temporary expiration time, then returns updated cart totals to the client.

During checkout, the client sends an order creation request. The Order Management Service initializes the order and requests the Inventory Service to reserve stock. The Inventory Service updates available stock in the database and returns a reservation confirmation. The Payment Service then creates a payment transaction and redirects the user to the external bank or payment provider for authentication and payment confirmation.

After successful payment, the bank sends a callback notification. The Order Management Service updates the order status to paid and publishes an order event to the Kafka Event Bus. Warehouse Management Systems consume this event, determine the optimal warehouse location, and generate a pick list for order assembly.

Once the warehouse prepares the order, the system updates order status and sends a shipment notification to the user through the client application.

## Deployement
![Wildberries Deployment Diagram](../diagrams/out/wildberries/architecture-deployment/Deployment%20Diagram.svg)

[Wildberries Deployment Diagram Code](../diagrams/src/wildberries/architecture-deployment.puml)


Wildberries client applications, including customer mobile apps, partner seller apps, customer web browsers, and enterprise warehouse or pickup-point hardware, are deployed on user and partner devices. These clients connect to Wildberries infrastructure via HTTPS, GraphQL, or SSR web protocols.

Edge and ingress components such as the Storefront Gateway, Partner Gateway, and Internal/Ops Gateway are deployed within Wildberries global cloud infrastructure and act as secure entry points for different types of traffic including public customers, business partners, and internal staff systems.

Core business services are deployed as containerized microservices within compute clusters. These include e-commerce services such as cart management, authentication, catalog search, and payment processing, as well as logistics and operational services such as order management, warehouse management, routing optimization, and pickup-point management. Supporting services like notification delivery and media/CDN services are deployed alongside business services.

Data and middleware components including caching clusters, search indexing clusters, distributed event bus infrastructure, relational databases, analytics engines, and object storage systems are deployed in specialized storage and database clusters to ensure scalability, reliability, and high performance.

Wildberries integrates with external financial, logistics, and notification ecosystems through secure APIs to process payments, coordinate third-party shipping, and deliver SMS or push notifications to users.

## Assumptions

- I assume the Inventory Service uses distributed reservation and locking mechanisms to prevent overselling during peak traffic and large sales campaigns.

- I assume the Logistics & Routing service dynamically selects warehouses and delivery partners based on geographic location, delivery cost, and current warehouse load.

## Open questions

- How does Wildberries maintain real-time consistency between warehouse inventory systems and customer-visible stock availability?

- What strategies does Wildberries use to handle traffic spikes and maintain system performance during large promotional events?
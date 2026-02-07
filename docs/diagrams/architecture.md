# Wildberries Architecture

## Product Choice

**Product name:** Wildberries  
**Website:** https://www.wildberries.ru  
**Short description:** Wildberries is the largest e-commerce marketplace in Russia and Eastern Europe, connecting millions of buyers and sellers with a wide range of consumer goods, logistics, and payment services.

---

## Main components

![Wildberries Component Diagram](diagrams/out/wildberries/component-diagram/Component%20Diagram.svg)

Rendered image (click to open)

[Wildberries Component Diagram Code](diagrams/src/wildberries/component-diagram/component-diagram.puml)

### Selected components

1. **Web & Mobile Frontend**  
   Provides user interfaces for browsing products, managing carts, placing orders, and tracking deliveries across web and mobile apps.

2. **API Gateway**  
   Acts as a single entry point for client requests, handling routing, authentication, rate limiting, and request aggregation for backend services.

3. **Product Catalog Service**  
   Manages product listings, categories, pricing, availability, and search metadata used across the platform.

4. **Order Management Service**  
   Handles order creation, status transitions, returns, and coordination between payment, inventory, and logistics services.

5. **Payment Service**  
   Processes customer payments, refunds, and interactions with external payment providers while ensuring transactional integrity.

6. **Logistics & Fulfillment Service**  
   Coordinates warehouse operations, shipment creation, delivery routing, and status tracking.

---

## Data flow

![Wildberries Sequence Diagram](../../../docs/diagrams/out/wildberries/sequence-diagram/Sequence%20Diagram.svg)

[Wildberries Sequence Diagram Code](../../../docs/diagrams/src/wildberries/sequence-diagram/sequence-diagram.puml)

### Order placement flow

In the **order placement** flow, the user submits an order from the frontend, which sends a request to the **API Gateway**.  
The API Gateway forwards the request to the **Order Management Service**, which validates product availability via the **Product Catalog Service** and initiates payment through the **Payment Service**.  
After successful payment confirmation, the **Order Management Service** notifies the **Logistics & Fulfillment Service** to reserve inventory and create a delivery task.  
Order status updates are then returned back to the frontend.

---

## Deployment

![Wildberries Deployment Diagram](../../../docs/diagrams/out/wildberries/deployment-diagram/Deployment%20Diagram.svg)

[Wildberries Deployment Diagram Code](../../../docs/diagrams/src/wildberries/deployment-diagram/deployment-diagram.puml)

The frontend applications are deployed on CDN-backed edge servers to minimize latency.  
Backend services are deployed as containerized microservices in cloud or private data centers, behind load balancers.  
Databases and message brokers are deployed in dedicated clusters with replication for high availability.

---

## Assumptions

- I assume the **Logistics & Fulfillment Service** integrates with both Wildberries-owned warehouses and third-party delivery providers.
- I assume the **Product Catalog Service** uses aggressive caching to handle extremely high read traffic during sales events.
- I assume asynchronous messaging is used between Order Management and Logistics services to improve resilience.

---

## Open questions

- How does Wildberries handle database sharding and data consistency across regions at peak load?
- What exact mechanisms are used to prevent overselling during flash sales?
- How is real-time inventory synchronized between warehouses and the platform?

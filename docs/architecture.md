## Product Choice

Product Name: Wildberries  
Website: [https://www.wildberries.ru](https://www.wildberries.ru)  
Short Description: Wildberries is the largest online retailer in Russia, selling clothing, electronics, cosmetics, and more, providing delivery across the country.

## Main components

![Wildberries Component Diagram](./diagrams/out/wildberries/component-diagram/Component%20Diagram.svg)
[Wildberries Component Diagram Code](./diagrams/src/wildberries/component-diagram/Component%20Diagram.puml)
- Catalog Service – manages the product catalog, categories, and descriptions.  
- Order Service – handles order creation, payment processing, and tracking.  
- User Service – manages user registration, authentication, and profiles.  
- Payment Service – processes transactions and integrates with banking systems.  
- Logistics & Routing – plans delivery routes and coordinates with partners and couriers.

## Data flow

![Wildberries Sequence Diagram](./diagrams/out/wildberries/sequence-diagram/Sequence%20Diagram.svg)
[Wildberries Sequence Diagram Code](./diagrams/src/wildberries/sequence-diagram/Sequence%20Diagram.puml)
Example flow: a user places an order:  
- User Service sends the customer data to Order Service.  
- Order Service checks product availability through Catalog Service and requests payment via Payment Service.  
- Once payment succeeds, Logistics & Routing receives order details to plan delivery.

## Deployment

![Wildberries Deployment Diagram](./diagrams/out/wildberries/deployment-diagram/Deployment%20Diagram.svg)
[Wildberries Deployment Diagram Code](./diagrams/src/wildberries/deployment-diagram/Deployment%20Diagram.puml)
- Catalog Service, Order Service, and User Service are deployed on cloud servers.  
- Payment Service interacts with external banking systems.  
- Logistics & Routing runs on dedicated servers to manage delivery operations.

## Assumptions

- I assume the Logistics & Routing service integrates with multiple delivery partners to optimize shipping costs and delivery times.  
- I assume the Payment Service handles retries and error management for failed transactions.

## Open questions

- How is inventory synchronized across warehouses and online catalog in real time?  
- What caching strategies are used to handle high traffic during sales events?

## Product Choice
Wildberries (https://www.wildberries.ru) — largest Russian marketplace with product delivery, seller support, and millions of daily orders.

## Main components
![Wildberries Component Diagram](../../../docs/diagrams/out/wildberries/component-diagram/Component%20Diagram.svg)
[Wildberries Component Diagram Code](https://github.com/MarikSH/lab-01-market-product-and-git/blob/main/docs/diagrams/src/wildberries/component-diagram.puml)

1. **Frontend Web/Mobile**: UI for catalog, cart, and payments; dynamically renders products.
2. **Catalog Service**: Manages product database, search, and ML-based recommendations.
3. **Order Management**: Handles order creation/cancellation, payment integration.
4. **Logistics & Routing**: Calculates delivery routes, integrates with partners (CDEK, etc.).
5. **Payment Gateway**: Processes transactions, refunds; supports cards/e-wallets.
6. **User Auth Service**: Authentication, seller/buyer profiles with JWT.

## Data flow
![Wildberries Sequence Diagram](../../../docs/diagrams/out/wildberries/sequence-diagram/Sequence%20Diagram.svg)
[Wildberries Sequence Diagram Code](https://github.com/MarikSH/lab-01-market-product-and-git/blob/main/docs/diagrams/src/wildberries/sequence-diagram.puml)

In "Place Order" group: Frontend sends request to Order Management with user_id/cart_items; service checks stock in Catalog, generates invoice for Payment Gateway (data: amount, items), then notifies Logistics (address, tracking_id).

## Deployment
![Wildberries Deployment Diagram](../../../docs/diagrams/out/wildberries/deployment-diagram/Deployment%20Diagram.svg)
[Wildberries Deployment Diagram Code](https://github.com/MarikSH/lab-01-market-product-and-git/blob/main/docs/diagrams/src/wildberries/deployment-diagram.puml)

Components deployed as microservices in cloud (Yandex Cloud/AWS); frontend on CDN, backend in Kubernetes with databases (PostgreSQL for orders, Redis for cache), logistics uses edge computing for regions.

## Assumptions
- Catalog Service uses Elasticsearch for search considering popularity/prices.
- Logistics integrates with external APIs for real-time tracking.

## Open questions
- How are peak loads handled during sales events (Black Friday)?
- What ML models are used for recommendations and how are they trained?

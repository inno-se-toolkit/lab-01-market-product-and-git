## Product Choice

Wildberries
<https://www.wildberries.ru/>
Internet-marketplace.

## Main components

    Embed the product's Component Diagram.svg.

![Wildberries Component Diagram](./diagrams/out/wildberries/architecture-component/Component%20Diagram.svg)

[Wildberries Component Diagram code](./diagrams/src/wildberries/architecture-component.puml)

1. Storefront Gateway
Likely acts as the main entry point for customer traffic, routing requests from the app and website to the appropriate backend services.

2. Auth & ID Service
Probably handles user registration and login processes, issuing security tokens to ensure only authorized users access their accounts.

3. Catalog & Search Service
Seemingly manages the massive list of available products and powers the search engine so users can find items quickly.

4. Order Management (OMS)
I assume this orchestrates the entire lifecycle of an order, tracking it from the moment a customer clicks "buy" until it is ready for delivery.

5. Product/Order DB (Sharded)
This appears to be the primary storage for transactional data, likely split into multiple parts (shards) to handle the huge volume of orders and items.

## Data flow

![Wildberries Sequence Diagram](./diagrams/out/wildberries/architecture-sequence/Sequence%20Diagram.svg)
[Wildberries Sequence Diagram code](./diagrams/src/wildberries/architecture-sequence.puml)

    Group: 3. Payment Callback & Finalization

    Description:
    This flow appears to handle the asynchronous confirmation of a purchase. It starts when an external payment provider sends a Webhook containing a Transaction ID (TxID) to the internal system to confirm success.

    Interactions & Data:
    The Payment/Order Service processes this callback by connecting to the Database to execute an UPDATE query setting the status to 'PAID'. Simultaneously, it publishes an OrderPaid event to a Message Broker (to notify the warehouse) before returning an HTTP 200 OK to the provider to acknowledge the receipt.

## Deployment

![Wildberries deployment Diagram](./diagrams/out/wildberries/architecture-deployment/Sequence%20Diagram.svg)
[Wildberries deployment Diagram code](./diagrams/src/wildberries/architecture-deployment.puml)
    Based on the diagram, the deployment is split into two main physical areas:

1. Client Side (End-User Devices)

    Customer & Partner Apps: Deployed on personal Smartphones (iOS/Android) and User Computers (Web Browsers).
    Internal Operations: Specialized software runs on WB Enterprise Hardware, specifically barcode scanners/terminals in warehouses and PCs at Pickup Points (PVZ).

2. Server Side (Wildberries Global Infrastructure)
The backend is hosted in a Primary Data Center (likely using Kubernetes), organized into several clusters:

    Edge / Ingress Layer: Hosts the API gateways to handle incoming traffic.
    Compute Cluster: Runs the various microservices (E-Commerce, Logistics, Support) inside containers/pods.
    Data & Storage Layers: Dedicated clusters for specific data needs, including In-Memory (Redis), Search (Elasticsearch), Event Bus (Kafka), and persistent Storage (PostgreSQL, S3, Clickhouse).

## Assumptions

    Payment Security: I assume the "Fintech & Payment Service" does not store raw credit card data but relies entirely on tokenization provided by external "Payment Providers" to maintain PCI-DSS compliance.
    Data Consistency: I assume the "Warehouse Management (WMS)" and "Order Management (OMS)" services use eventual consistency models rather than strict ACID transactions to prevent system-wide locks during high-volume periods.

## Open questions

    Search Synchronization: What specific mechanism is used to synchronize data between the "Main RDBMS" and the "Search Index (Elasticsearch)" (e.g., is it CDC using Debezium, dual-writes, or batch indexing), and what is the replication lag?
    Disaster Recovery: Does the "Wildberries Global Infrastructure" operate in an Active-Active configuration across multiple data centers to handle regional outages, or is there a cold/warm standby failover process?

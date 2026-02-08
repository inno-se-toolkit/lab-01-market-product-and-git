## Product Choice
**1. Product name:** Wildberries.ru  
**2. Link to the product's website:** https://www.wildberries.ru/  
**3. Short description of the product:** Wildberries.ru is the largest international marketplace offering a wide range of products with convenient delivery through an extensive network of pickup points. It combines a convenient online shopping platform with effective business management and sales analytics tools.  
## Main Components
![Wildberries Component Diagram](../../docs/diagrams/out/wildberries/architecture-component/Component%20Diagram.svg)  

[Wildberries Component Diagram Code](../../docs/diagrams/src/wildberries/architecture-component.puml)  

### Five Components of the product: 
**1. Auth & ID Service:** it manages authentication and authorization for all users and internal services. It also ensures secure access to the system.  
**2. Catalog & Search Service:** it is responsible for displaying products in the marketplace to users. It helps users find the products they need by processing queries and applied filters.  
**3. Fintech & Payment Service:** it facilitates the acceptance of payments from customers using various methods. It is also responsible for processing transactions, such as refunds and other payouts.  
**4. Order Management (OMS):** it tracks orders from the moment they're placed to the moment they're received. It also integrates other processes, such as inventory management.  
**5. User Profile & Loyalty:** it manages customers' personal data. Furthermore, it tracks purchase histories, points accrual, and so on.

## Data flow
![Wildberries Sequence Diagram](../../docs/diagrams/out/wildberries/architecture-sequence/Sequence%20Diagram.svg)

[Wildberries Sequence Diagram Code](../../docs/diagrams/src/wildberries/architecture-sequence.puml)

### Description of the group Preparation (Search & Cart)
This group of sets describes the process of seraching for products (User browses catalog and selects items) and adding them to the cart (function Add to Cart).  

**Sequence of steps:**
1. User browses catalog andselects items.
2. Click "Add to Cart".
3. RPC: addToCart(sku_id, qty).
4. Update Session Cart
5. HSET cart:{user_id} (TTL 7 days).
6. OK.
7. Cart Update (Total Price).
8. UI Update (Badge Counter)

**Components, which talk to each other:**
* **User:** searches for products and adds them to the cart
* **Cart Service:** manages the state of the shopping cart, receives information about products
* **Storefront Gateway:** it processes requests from the application.
* **Redis (Hot Data):** temporarily stores shopping cart data.  

## Deployment

![Wildberries Deployment Diagram](../../docs/diagrams/out/wildberries/architecture-deployment/Deployment%20Diagram.svg)

[Wildberries Deployment Diagram Code](../../docs/diagrams/src/wildberries/architecture-deployment.puml)

**The components are deployed in a Physical View that includes several logical areas:**
* **"device"**, which consists of Customer Smartphone, Partner Smartphone, User Computer, Web Browser, WB Enterprise Hardware
* **Wildberries Global Infastructure (Primary DC / K8s)**, which consists of Edge / Ingress Layer, Computer Cluster / Microservices (E-Commerce Pods, Logistic & Ops Pods, Support Pods), In-Memory Cluster, Search Cluster, Event Bus Cluster, Storage & Database Cluster
* **Financial & Logistics Ecosystems**
* **External Notifications**

## Assumptions

1. I assume that all user applications (web and mobile) connect to the system through a single central component called the API Gateway, which helps control all incoming traffic and protect internal services.
2. I assume that different databases (for the cart, for orders) are physically separated and located on different servers, so that a high load on one type of data does not slow down the operation of other parts of the system.

## Open questions

1. How exactly does the system decide which specific internal server should process a user's request after it passes through the main gateway (API Gateway)?
2. How exactly is the enormous volume of order data distributed among different physical database machines?
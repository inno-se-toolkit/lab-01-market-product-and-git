## Product Choice
Product name: Wildberries.
Link: https://www.wildberries.ru
Short description: Wildberries is a Russian marketplace. It was founded in 2004 by Tatiana Kim and Vladislav Bakalchuk.

## Main components
docs/diagrams/out/wildberries/architecture-component/Component Diagram.svg

1. Catalog & Search Service
This component manages and serves all product information—including titles, descriptions, prices, and categories—and powers the search functionality with filtering, sorting, and ranking to help customers discover items quickly.

2. Logistics & Routing Service
It calculates delivery options, chooses optimal shipping routes, assigns orders to warehouses or pickup points (PVZ), and coordinates with third-party logistics (3PL) partners to ensure efficient fulfillment and tracking.

3. Fintech & Payment Service
Handles the entire payment flow: validating payment methods, securing transactions, communicating with external payment gateways and acquiring banks, and reconciling financial records for both customers and sellers.

4. Order Management (OMS)
Orchestrates the lifecycle of an order from confirmation to delivery—tracking status, managing inventory deductions, coordinating between cart, payment, and logistics services, and updating sellers and customers.

5. Notification Service
Sends automated alerts and updates via multiple channels (SMS, push, email) for events like order confirmations, shipment tracking, payment receipts, and promotional campaigns, ensuring users stay informed in real time.

## Data Flow

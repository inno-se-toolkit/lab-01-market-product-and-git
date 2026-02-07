## Product choice
Yandex
https://yandex.ru/
Yandex is a search engine provided by a Russian corporation

## Main components
![Yandex Component Diagram](docs\diagrams\out\yandex-go\architecture-component\Component Diagram.svg)

![Yandex Component Diagram Code](docs\diagrams\src\yandex-go\architecture-component.puml)

Mobile App (User communication level for smartphones)
Web App (User communication level for browsers)
API Gateway (processes and redirects input data)
Payment Service (redirects payment operation requests)
Maps & Routig Service (redirects maps and routing operation requests)

## Data flow
![Yandex Sequence Diagram](docs\diagrams\out\yandex-go\architecture-component\Sequence Diagram.svg)

![Yandex Component Diagram Code](docs\diagrams\src\yandex-go\architecture-sequence.puml)

App Initialization & Auth process:
1)User opens the app
2)App validates session token and goes to the connection layer
3)API Gateway sends authenticate token to the User Service
4)User Service looks up for the session/profile in service's State Cahce and gets confirmation
5)User Service return user profile data to API Gateway
6)API Gateway returns authorisation succes information to user's app

## Deployment

![Yandex Deployment Diagram](docs\diagrams\out\yandex-go\architecture-component\Deployment Diagram.svg)

![Yandex Deployment Diagram Code](docs\diagrams\src\yandex-go\architecture-deployment.puml)

Components are deployed into Yandex Cloud Infrastructure.

## Assumptions
"I assume the pricing service handles surge pricing calculations based on demand and supply in real-time."
"I assume the payment service handles banking operations in all Yendex services"

## Open questions
"How does the actual load balancing mechanism work between the microservices in production?"
"How exactly user validation token is being validated?"



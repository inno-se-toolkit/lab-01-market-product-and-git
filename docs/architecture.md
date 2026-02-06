## Product Choice

* Yandex Go

* <https://go.yandex>
* Yandex Go is a mobile application of "Yandex" for transportation and delivery. Its design is based on Yandex Taxi.
* ![Yandex Go Component Diagram](./diagrams/out/yandex-go/architecture-component/Component%20Diagram.svg)
* ![Yandex Go Component Diagram code](./diagrams/src/yandex-go/architecture-component.puml)
* Yandex Pay is an external service to make online payments connected to other Yandex services.
* Notification service is designed to efficiently deliver necessary information to users.
* Pricing service is designed to evaluate business of traffic to offer the best work conditions to users.
* Maps and Routing service is designed to navigate users and evaluate distances between them.
* Mobile app is designed for users to have access to Yandex Go services via their smartphones.

## Data flow

* ![Yandex Go Sequence Diagram](./diagrams/out/yandex-go/architecture-sequence/Sequence%20Diagram.svg)
* ![Yandex Go Sequence Diagram Code](./diagrams/src/yandex-go/architecture-sequence.puml)
* The first group of steps describes app initalization and authentication. The appliaction checks authentication session validity and after that loads the information about user.

## Deployment

* ![Yandex Go Deployment Diagram](./diagrams/out/yandex-go/architecture-deployment/Deployment%20Diagram.svg)
* ![Yandex Go Deployment Diagram Code](./diagrams/src/yandex-go/architecture-deployment.puml)
* The part of components is deployed on user smartphone, computer (in web browser), but the majority is deployed on Yandex cloud infrastructure.

## Assumptions

* I assume that pricing service is designed to evaluate business of traffic to offer the best work conditions to users.
* I assume that the majority of components is deployed on Yandex cloud infrastructure.

## Open questions

* What are approaches to optimize resource consumptions for maintaining the whole system?
* How the application collects user data for smart advertisements?

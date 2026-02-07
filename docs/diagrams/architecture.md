Product Name:
    Yandex Go

Product Link:
    <https://go.yandex/>

# 1

![YandexArch](out/yandex-go/architecture-component/Component%20Diagram.svg)

![YandexArchPuml](src/yandex-go/architecture-component.puml)

1. - Notification Service
        This service sends notifications to users.

2. - Pricing Service
        This service calculates the prices based on different factors, such as weather and daytime.

3. - Payment Service
        This service manages user transactions, checking correctness and providing information for banks and user service.

4. - Maps & Routing Service
        This service tracks situtation on the road, marking traffic jams and finding the best routes for taxis.

5. - User Service
        This service stores users information database, manages their information.

# 2

![YandexFlow](out/yandex-go/architecture-sequence/Sequence%20Diagram.svg)
![YandexFlowPuml](src/yandex-go/architecture-sequence.puml)
App installation and Auth. stage

    User opens his application and sends a session validation request.

    The request to user database is made, checking the validity of a user. 

    If valid, the user data is sent back to him.

    If data is recieved, the user is logged in.

![YandexDeploy](out/yandex-go/architecture-deployment/Deployment%20Diagram.svg)
![YandexDeployPuml](src/yandex-go/architecture-deployment.puml)

On a user device local app is stored, which makes https requests to Yandex Cloud Infrastructure.
The API gateway manages requests, sending them to the required service on Kubernetes Cluster.
The services adress their requests to Redis, Message Broker, Data Storage, or Kubernetes Cluster.

# 3

I assume that Yandex Go interconnects notifications and user database, in order to provide proper messages.

Also I assume that traffic jams info from maps is used in pricing.

# 4

Which exact information is stored my maps and routing?

How many users at maximum can be stored in a Yandex Go database?

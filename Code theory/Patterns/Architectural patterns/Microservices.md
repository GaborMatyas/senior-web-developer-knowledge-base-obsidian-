# Microservices


There are multiple services. Each service is a business activity. Mostly separate teams develop and run the services. 

There is NO logic-heavy enterprise service bus like in Service oriented architecture, where almost all logic is included in one service that serves multiple applications. 

It uses automated tests, deployment, and monitoring. 
![[microservices.png]]

The individual services call each other directly, mostly via HTTP requests. To make the deployment smooth the services are running in containers (e.g.: Docker). 

## Pros
- The services are loosely coupled and easily scalable 
- It gives more agility
- If it is implemented correctly, it is designed to handle failures. 

## Cons
- It is difficult the define the boundaries of the concrete services sometimes.
- The boundaries can change in time -> it is hard to refactor multiple microservices together.
- The separate services are understandable and clear in most cases, but the communication can become quite complex during the development. 

## Main parts
### Data Service
This means not only a database but a whole layer that produces data for different entities. For example a product service, that has no logic or information about product online orders, only about the products themself. 

### Business service
They built on data services. For example an order service...when you want to place an online order in your platform, you need customer data from the customer data service, and product data from the product data service. 

### Translation service
WIP

### Edge service
An edge service is responsible for serving data to users and external services. These services can be used to provide a web view, a service that delivers that content, and other services that deliver to mobile devices. Often, we use edge services to slim down our payloads to make them more mobile friendly, or provide modified payloads that meet the need of a third party contract. While edge services aren't always used, they can be a powerful layer in a complete microservices architecture.


## Platform
This is the runtime for your all service, bare metal servers, Virtual Machines, the whole service network you have. 
Note: use containers when you connect to multiple data centers and you have a quite complex structure, Kubernetes is a good candidate. (https://kubernetes.io/)
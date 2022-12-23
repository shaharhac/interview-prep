### Monolithic applications - WIP

Monolithic application - all the functionalities of a project exists in a single codebase.

Pros:

* Simple to develop relative to microservices
* Easier to deploy, a single service is being deployed
* Easier to develop
* Network latency is less an issue in comparison to microservices architecture

Cons:

* It becomes too large in size with time and hence, diffucult to manage.
* Redeploy the whole application even for a small change
* As the size of the applicatio n increases, its start-up and deployment time also increases
* Hard time for new developers
* Difficult to adopt new technology which is well suited for a particular functionality.
* A single bug in any module can bring down the whole application

### Microservices

The application is made up of smaller services communicating with each other directly using HTTP

![microservices](https://media.geeksforgeeks.org/wp-content/uploads/20200322182733/microservices.jpg)

Instead of sharing a single database with other microservices, each microservice has its own database.
It often result in duplication of some data but having a database per microservice is essential if you want to benefit from this architecture as it ensures loose coupling.

Principles of microservices:
* Single Responsibility - Each microservice must be responsible for a specific feature or a functionality


Pros:

* If there's any update in one of the microservices, then we need to redeploy only that microservice
* New developer only need to understand a particular microservice
* If the microservice is facing a large load of users, we can scale out that microservice only
* Each microservice can use different technology based on the business requirements.
* If a paticular microservice gows down due to some bug, then it doesn't affect other microservices and the whole system remains intact.

Cons:

* Application's complexity increases with the increase in number of microservices
* Microservices are costly in terms of netword usage as they need to interact with each other which result into network latency
* Less secure relative to monolithic application due to the inter-services communication over the network
* Debugging is difficult as the control flows over many microservices

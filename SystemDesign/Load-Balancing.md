# Load Balancer

<details>
<summary>Questions</summary>

<details>
<summary>Question 1</summary>

State 3 advanteges of load balancers

<details>
<summary>Answer</summary>

1. Users experience faster uninterrupted service.
2. System will experience less failed ot stressed components.
3. Efficiently manage failures
4. Prevents any one application server from becoming a single point of failure
5. Handling peak performance


</details>
</details>
<details>
<summary>Question 2</summary>

What is Health Check in refer to load balancer?

<details>
<summary>Answer</summary>

Health checking allows you to determine if a particular server or service is running or has failed. When a service fails health checks, the algorithm will stop sending clients to that server until the service passes health checks again.

</details>
</details>

<details>
<summary>Question 3</summary>

State 3 load balancer algorithms 

<details>
<summary>Answer</summary>

1. Round-Robin
2. Weighted Round-Robin
3. Least Connection
4. Least Bandwidth
5. Least Response Time
6. IP Hash

</details>
</details>

</details>

## Definition

The load balancer (LB) takes "load", which are requests from users using our service, and it routes that traffic to different backend servers.
The goal is to evenly distribute traffic between your backend servers. It also takes care of routing traffic geographically between the servers.

Typically a load balancer sits between the client and the server accepting incoming network and application traffic and disributing the traffic across multip[le backend servers using
various algorithms.

A load balancer reduces individual server load and prevents any one application server from becoming a single point of failure, thus improving overall application availability and responsiveness.

## Different Types of Load Balancers

To utilize full scalability and redundancy, we can balance the load at different layers of the system:

* between the user and the web server
* between web servers and an internal platform layer, like application servers or cache servers.
* between internal platform layer and database


## Health Checks
The load balancer will need to know which machines are abailable to take the user's requests and also which machines are healthy and not overloaded.
This is usually done with so called "health checks", meaning the load balancer makes ping requests to the servers and those reply with their state (healthy/unhealthy).
The health checks will also measure things like latency, where are the servers placed geographically.
The load balancers will keep this data in it's memory, and then as soon as request comes in, it will know which service is running on which server, which of those is healthy
and which of those is ready to serve the customers

## Load Balancing Algorithms

### Round-Robin
The load balancer will send requests in turn to all the servers which are available to serve that request.
pros:
* useful when the servers are of equal specification and there are not many persistent connections

cons:
* won't consider server's load

### Weighted Round-Robin
Each server is assigned a weight (integer value that indicates the proccessing capacity). Servers with higher weights receive new connections before those with less weights.

### Least Connections
The load balancer will check how many open connections every server has, and forward the request to server with the lowest number of connections.

pros:
* useful wen there are a larfe number of persistent client connections which are unevenly disributed between the servers.

cons:


### Least Response Time Method
The load balancer will direct traffic to the server with the fewest active connections and the lowest average response time.

### Least Bandwidth Method
The load balancer will direct traffic to the server that is currently serving the least amount of traffic (measured in Mbps)

### IP Hash
A hash of the IP address of the client is being calculted, and being to the application server accordingly

## Redundancy

Even though the load balancer can prevent from one application server to be a single point of failure, the load balancer itself can be a single of failure.
to overcome this, a second load balancer can be connected to the first to form a cluster. Each load balancer monitors the health of the other and, since both of them are equally capable
of serving traffic and failure detection, in the event the main balancer fails, the second load balancer takes over.



# Horizontal vs. Vertical Scaling

a System cab be scaled one of two ways.
*** Vertical Scaling *** means increasing the resources of a specific node, For example, you might add additional memory to a server to improve its abillty to habndle load changes.
*** Horizonyal Scaling ***means increasing the number of nodes. For example, you might add additional servers, thus decreasing the load on any one server.

Vertical scaling is generally easier than horizontal scaling, but it's limited. you can only add so much memory or disk space.

## Scalability

Let's say you developed a service and uploaded it to your server on the cloud. Couple of months came by, and your service got pretty popular. It means that your service get more
and more requests. The ability to handle more request, called scalability.
We have two ways to handle our problem:
1. Buy bigger machine (vertical scaling)
2. Buy more machines (horizontal scaling)

## A Comparison

| Horizontal Scaling    | Vertical Scaling |
| ------------- | ------------- |
| A lot of small servers  | Big server  |
| Load balancing required  | No need of load balancing  |
| Resilient  | Single point of failure  |
| Network calls between servers (slow)  | Inter process communication (fast)   |
| Data inconsistency  | Consistent   |
| Scales well  | Hardware limit   |

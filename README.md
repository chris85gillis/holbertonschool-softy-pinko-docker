High-level Design
In this design, there is a single server that acts as the entry point for your application. That server acts as a reverse proxy server, which routes traffic to either the API servers or the front-end static-content server; it also acts as a load balancer to balance traffic between the two API servers. When traffic comes in, the server will determine which service it needs to go to (either the front-end static-content server or the API server) and:

If the request is to be routed to the front-end static-content server, it will do so and any static content that is returned from the front-end static-content server to the proxy server will then be sent to the client. The client isn’t directly communicating with the front-end static-content server.

If the request is to be routed to the API server, then it will first go through a load-balancing algorithm to determine which API server to send the request to. We will be using the basic Round Robin load-balancing algorithm for our site. Once the request is routed to an API server and the response is sent back to the proxy server, it will then be sent to the client. The client isn’t directly communicating with either of the API servers.

What is Round Robin load balancing? Round Robin load balancing is a method of distributing traffic across multiple servers or nodes in a network. In this approach, the load balancer assigns requests to each server in a rotating manner, meaning that each server takes turns serving the requests. For example, if there are three servers A, B, and C, the first request will be sent to server A, the second to server B, the third to server C, the fourth to A, the fifth to B, and so on, while the cycle repeats. This ensures that each server receives an equal share of the traffic, and can prevent any one server from becoming overwhelmed with requests. Round Robin load balancing is a simple and effective way to distribute traffic, but it may not be suitable for all applications, particularly those with varying workload patterns or resource requirements. For our learning purposes in this project, it is a sufficient algorithm to implement for our load-balancing needs.
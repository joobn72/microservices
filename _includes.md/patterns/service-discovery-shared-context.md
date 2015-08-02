---
---
## Context

Services typically need to call one another.
In a monolithic application, services invoke one another through language-level method or procedure calls.
In a traditional distributed system deployment, services run at fixed, well known locations (hosts and ports) and so can easily call one another using HTTP/REST or some RPC mechanism.
However, a modern [microservice-based](microservices.html) application typically runs in a virtualized or containerized environments where the number of instances of a service and their locations changes dynamically.

<img class="img-responsive" src="/i/servicediscovery/discovery-problem.jpg">


Consequently, you must implement a mechanism for that enables the clients of service to make requests to a dynamically changing set of ephemeral service instances.

## Problem

How does the client of a service - the API gateway or another service - discover the location of a service instance?

## Forces

* Each instance of a service exposes a remote API such as HTTP/REST, or Thrift etc. at a particular location (host and port)
* The number of services instances and their locations changes dynamically.
* Virtual machines and containers are usually assigned dynamic IP addresses.
* The number of services instances might vary dynamically. For example, an EC2 Autoscaling Group adjusts the number of instances based on load.

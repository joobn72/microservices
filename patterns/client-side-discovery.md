---
layout: pattern
title: Client-side service discovery pattern
---

# Pattern: Client-side service discovery

{% include patterns/service-discovery-shared-context.html %}

## Solution

When making a request to a service, the client obtains the location of a service instance by querying a [Service Registry](service-registry.html), which knows the locations of all service instances.

## Examples

[Netflix OSS](http://netflix.github.io/) provides a good example of client-side discovery:

* [Eureka](https://github.com/Netflix/eureka/wiki/Eureka-at-a-glance) is a [Service Registry](service-registry.html)
* [Ribbon Client](https://github.com/Netflix/ribbon) is an HTTP client that queries Eureka to route HTTP requests to an available service instance

## Resulting context

Client-side discovery has the following benefits:

* Fewer moving parts and network hops compared to [Server-side Discovery](server-side-discovery.html)

Client-side discovery also has the following drawbacks:

* This pattern couples the client to the [Service Registry](service-registry.html) 
* You need to implement client-side service discovery logic for each programming language/framework used by your application, e.g Java/Scala, JavaScript/NodeJS. 
For example, [Netflix Prana](https://github.com/Netflix/Prana) provides an HTTP proxy-based approach to service discovery for non-JVM clients.

## Related patterns

* [Service Registry](service-registry.html)
* [Server Side Discovery](server-side-discovery.html) is an alternative solution to this problem.



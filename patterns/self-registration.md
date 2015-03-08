---
layout: pattern
title: Self Registration pattern
---

# Pattern: Self Registration

{% include patterns/registration-shared-intro.html %}

## Solution

A service instance is responsible for registering itself with the service registry.
On startup the service instance registers itself (host and IP address) with the service registry and makes itself available for discovery.
The client must typically periodically renew it's registration so that the registry knows it is still alive.
On shutdown, the service instance unregisters itself from the service registry.

## Examples

[Netflix Eureka](https://github.com/Netflix/eureka/wiki/Understanding-eureka-client-server-communication) is an example of a service registry. 
It provides a registration API and a client library that service instances use to (un)register themselves.

When using [Apache Zookeeper](http://zookeeper.apache.org) as a service registry, each service corresponds to a particular Zookeeper znode.
On startup, each service instance creates an ephemeral child znode of the service znode.
The ephemeral znode contains the instance's location.
Clients of the service simply retrieve the children of the service znode in order to determine the available instances.
If the client terminates without removing the ephemeral node, Zookeeper will timeout the client and remove the znode.

## Resulting context

The benefits of the Self Registration pattern include the following:

* A service instance knows it's own state so can implement a state model that's more complex than UP/DOWN, e.g. STARTING, AVAILABLE, ...

There are also some drawbacks:

* Couples the service to the Service Registry
* You must implement service registration logic in each programming language/framework that you use to write your services, e.g. NodeJS/JavaScript, Java/Scala, etc.
* A service instance that is running yet unable to handle requests will often lack the self-awareness to unregister itself from the service registry

## Related patterns

* [Service Registry](service-registry.html)
* [Client Side Discovery](client-side-discovery.html)
* [Server Side Discovery](server-side-discovery.html)
* [3rd Party Registration](3rd-party-registration.html) is an alternative solution




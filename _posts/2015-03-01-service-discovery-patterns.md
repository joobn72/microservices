---
layout: misc
title:  "Service discovery patterns"
date:   2015-03-01 16:00:00
categories: microservices news
---

I've added the following service discovery patterns:

* [Client-side discovery](/patterns/client-side-discovery.html) - client-side logic picks the service instance to send a request to
* [Server-side discovery](/patterns/server-side-discovery.html) - client sends a request to a router that picks the service instance to which to forward the request
* [Service registry](/patterns/service-registry.html) - maintain a database of available service instances and their locations (host/port)
* [Self registration](/patterns/self-registration.html) - service instance (un)registers itself with the service registry
* [3rd party registration](/patterns/3rd-party-registration.html) - a 3rd party (un)registers the service instance with the service registry


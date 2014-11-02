---
layout: pattern
title: Microservices Architecture pattern
---
# Pattern: Microservices Architecture

## Context

{% include patterns/shared-context.html %}

## Problem

What's the application's deployment architecture?

## Forces

{% include patterns/shared-forces.html %}

## Solution

Architect the application by applying the [Scale Cube](/articles/scalecube.html) (specifically y-axis scaling) and functionally decompose the application into a set of collaborating services.
Each service implements a set of narrowly, related functions.
For example, an application might consist of services such as the order management service, the customer management service etc.

Service communicate using either synchronous protocols such as HTTP/REST or asynchronous protocols such as AMQP.

Services are developed and deployed independently of one another.

Each service has its own database in order to be decoupled from other services.
When necessary, consistency is between databases is maintained using either database replication mechanisms or application-level events.

## Example

Let’s imagine that you are building an e-commerce application that takes orders from customers, verifies inventory and available credit, and ships them.
The application consists of several components including the StoreFrontUI, which implements the user interface, along with some backend services for checking credit,
maintaining inventory and shipping orders.

The application is deployed as a set of services.

<img class="img-responsive" src="/i/DecomposingApplications.027.jpg"></img>

## Resulting context

This solution has a number of benefits:

 * Each microservice is relatively small
   * Easier for a developer to understand
   * The IDE is faster making developers more productive
   * The web container starts faster, which makes developers more productive, and speeds up deployments

 * Each service can be deployed independently of other services - easier to deploy new versions of services frequently

 * Easier to scale development.
   It enables you to organize the development effort around multiple teams.
   Each (two pizza) team is responsible a single service.
   Each team can develop, deploy and scale their service independently of all of the other teams.


 * Improved fault isolation. For example, if there is a memory leak in one service then only that service will be affected.
  The other services will continue to handle requests.
  In comparison, one misbehaving component of a monolithic architecture can bring down the entire system.

 * Each service can be developed and deployed independently

 * Eliminates any long-term commitment to a technology stack

This solution has a number of drawbacks:

 * Developers must deal with the additional complexity of creating a distributed system.
   * Developer tools/IDEs are oriented on building monolithic applications and don't provide explicit support for developing distributed applications.
   * Testing is more difficult
   * Developers must implement the inter-service communication mechanism.
   * Implementing use cases that span multiple services without using distributed transactions is difficult
   * Implementing use cases that span multiple services requires careful coordination between the teams

 * Deployment complexity
   In production, there is also the operational complexity of deploying and managing a system comprised of many different service types.

 * Increased memory consumption
   The microservices architecture replaces N monolithic application instances with NxM services instances.
   If each service runs in its own JVM (or equivalent), which is usually necessary to isolate the instances, then there is the overhead of M times as many JVM runtimes.
   Moreover, if each service runs on its own VM (e.g. EC2 instance), as is the case at Netflix, the overhead is even higher.

One challenge with using this approach is deciding when it makes sense to use it.
When developing the first version of an application, you often do not have the problems that this approach solves.
Moreover, using an elaborate, distributed architecture will slow down development.
This can be a major problem for startups whose biggest challenge is often how to rapidly evolve the business model and accompanying application.
Using Y-axis is splits might make it much more difficult to iterate rapidly.
Later on, however, when the challenge is how to scale and you need to use functional decomposition then tangled dependencies might make it difficult to decompose your monolithic application into a set of services.

Another challenge is deciding how to partition the system into microservices.
This is very much an art but there are number of strategies that can help.
One approach is to partition services by verb or use case.
For example, later on you will see that the partitioned e-commerce application has a Shipping service that’s responsible for shipping complete orders.
Another common example of partitioning by verb is a login service that implements the login use case.

Another partitioning approach is to partition the system by nouns or resources.
This kind of service is responsible for all operations that operate on entities/resources of a given type.
For example, later on you will see how it makes sense for the e-commerce system to have an Inventory service that keeps tracks whether products are in stock.

Ideally, each service should have only a small set of responsibilities.
(Uncle) Bob Martin talks about designing classes using the [Single Responsible Principle (SRP)](http://www.objectmentor.com/resources/articles/srp.pdf).
The SRP defines a responsibility of class as a reason to change, and that a class should only have one reason to change.
It make sense to apply the SRP to service design as well.

Another analogy that helps with service design is the design of Unix utilities.
Unix provides a large number of utilities such as grep, cat and find.
Each utility does exactly one thing, often exceptionally well, and can be combined with other utilities using a shell script to perform complex tasks.

## Related patterns

The [Monolithic architecture](monolithic.html) is an alternative pattern.
The [API Gateway pattern](apigateway.html) defines how clients access the services.

## Known uses

Most large scale web sites including [Netflix](http://techblog.netflix.com/), [Amazon](http://highscalability.com/blog/2007/9/18/amazon-architecture.html)
and [eBay](http://www.addsimplicity.com/downloads/eBaySDForum2006-11-29.pdf) have evolved from a monolithic architecture to a microservices architecture.

Netflix , which is a very popular video streaming service that’s responsible for up to 30% of internet traffic, has a large scale, service-oriented architecture.
They handle over a billion calls per day to their video streaming API from over 800 different kinds of devices.
Each API call  fans out to an average of six calls to backend services.

Amazon.com  originally had a two-tier architecture.
In order to scale they migrated to a service-oriented architecture consisting of hundreds of backend services.
Several applications call these services including the applications that implement the Amazon.com website and the web service API.
The Amazon.com website application calls 100-150 services to get the data that used to build a web page.

The auction site ebay.com  also evolved from a monolithic architecture to a service-oriented architecture.
The application tier consists of multiple independent applications.
Each application implements the business logic for a specific function area such as buying or selling.
Each application uses X-axis splits and some applications such as search use Z-axis splits.
Ebay.com also applies a combination of X-, Y- and Z-style scaling to the database tier.

## Variations






---
layout: pattern
title: Multiple service instances per host pattern
---

# Pattern: Multiple service instances per host

{% include patterns/deployment-shared-intro.html %}

## Solution

Run multiple instances of different services on a host (Physical or Virtual machine).

There are various ways of deploying a service instance on a shared host including:

* Deploy each service instance as a JVM process. For example, a Tomcat or Jetty instances per service instance.
* Deploy multiple service instances in the same JVM. For example, as web applications or OSGI bundles.

## Examples

## Resulting context

The benefits of this pattern include:

* More efficient resource utilization than the [Service Instance per host pattern](single-service-per-host.html)

The drawbacks of this approach include:

* Risk of conflicting resource requirements
* Risk of conflicting dependency versions
* Difficult to limit the resources consumed by a service instance
* If multiple services instances are deployed in the same process then its difficult to monitor the resource consumption of each service instance.
Its also impossible to isolate each instance

## Related patterns

* The [Single Service Instance per Host pattern](single-service-per-host.html) is an alternative solution.

---
layout: pattern
title: Single Service Instance per Host pattern
---

# Pattern: Single Service Instance per Host

{% include patterns/deployment-shared-intro.html %}

## Solution

Deploy each single service instance on it's own host

## Examples

## Resulting context

The benefits of this approach include:

* Services instances are isolated from one another
* There is no possibility of conflicting resouce requirements or dependency versions
* A service instance can only consume at most the resources of a single host
* Its straightforward to monitor, manage, and redeploy each service instance

The drawbacks of this approach include:

* Potentially less efficient resource utilization compared to [Multiple Services per Host](multiple-services-per-host.html) because there are more hosts

## Related patterns

* The [Multiple Service Instances per Host pattern](multiple-services-per-host.html) is an alternative solution
* The [Service Instance per VM pattern](service-per-vm.html) is a refinement of this pattern
* The [Service Instance per Container pattern](service-per-container.html) is a refinement of this pattern

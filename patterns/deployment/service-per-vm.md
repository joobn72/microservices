---
layout: pattern
title: Service Instance per VM pattern
---

# Pattern: Service Instance per VM

{% include patterns/deployment-shared-intro.html %}

## Solution

Package the service as a virtual machine image and deploy each service instance as a separate VM

## Examples

* Netflix packages each service as an EC2 AMI and deploys each service instance as a EC2 instance.

## Resulting context

The benefits of this approach include:

* Its straightforward to scale the service by increasing the number of instances. Amazon Autoscaling Groups can even do this automatically based on load.
* The VM encapsulates the details of the technology used to build the service. All services are, for example, started and stopped in exactly the same way.
* Each service instance is isolated
* A VM imposes limits on the CPU and memory consumed by a service instance
* IaaS solutions such as AWS provide a mature and feature rich infrastructure for deploying and managing virtual machines. For example,
  * Elastic Load Balancer - 
  * Autoscaling groups
  * ...

The drawbacks of this approach include:

* Building a VM image is slow and time consuming


## Related patterns

* This pattern is a refinement of the [Single Service per Host pattern](single-service-per-host.html)
* The [Service Instance per Container pattern](service-per-container.html) is an alternative solution


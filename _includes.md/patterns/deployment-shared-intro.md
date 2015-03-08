---
---

## Context

You have applied the [Microservices pattern](microservices.md) and architected your system as a set of services.
Each service is deployed as a set of service instances for throughput and availability.

## Problem

How are service instances packaged and deployed?

## Forces

* Services are written using a variety of languages, frameworks, and framework versions
* Each service consists of multiple service instances for throughput and availability
* Service must be independently deployable and scalable
* Service instances need to be isolated from one another
* You need to be able to quickly build and deploy a service
* You need to be able to constrain the resources (CPU and memory) consumed by a service
* You need to monitor the behavior of each service instance
* You must deploy the application as cost-effectively as possible



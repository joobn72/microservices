---
---

## Context

You have applied either the [Client-side Service Discovery pattern](client-side-discovery.html) or the [Server-side Service Discovery pattern](server-side-discovery.html).
Service instances must be registered with the [service registry](service-registry.html) on startup so that they can be discovered and unregistered on shutdown.

## Problem

How are service instances registered with and unregistered from the service registry?

## Forces

* Service instances must be registered with the service registry on startup and unregistered on shutdown
* Service instances that crash must be unregistered from the service registry
* Service instances that are running but incapable of handling requests must be unregistered from the service registry

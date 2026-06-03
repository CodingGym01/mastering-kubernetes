# Cloud Controller Manager

## Introduction

Cloud Controller Manager enables Kubernetes to interact with cloud providers.

It separates cloud-specific logic from core Kubernetes components.

---

## Why is it Needed?

Without Cloud Controller Manager:

Kubernetes would need built-in code for:

- AWS
- Azure
- Google Cloud
- OpenStack

This would make Kubernetes complex.

---

## Responsibilities

### Node Management

Obtains node information from cloud providers.

---

### Load Balancer Management

Creates cloud load balancers automatically.

---

### Route Management

Configures networking routes.

---

### Volume Management

Manages cloud storage resources.

---

## Example

When a Service of type LoadBalancer is created:

```yaml
type: LoadBalancer
```

Cloud Controller Manager communicates with the cloud provider and provisions a load balancer.

---

## Cloud Provider Examples

- Amazon EKS
- Azure AKS
- Google GKE

---

## Real-Life Analogy

Think of Kubernetes as a hotel.

Cloud Controller Manager acts as the hotel's external service coordinator.

Whenever external resources are needed, it contacts the appropriate provider.

---

## Summary

Cloud Controller Manager integrates Kubernetes with cloud providers and manages cloud-specific resources such as load balancers, routes, nodes, and storage.

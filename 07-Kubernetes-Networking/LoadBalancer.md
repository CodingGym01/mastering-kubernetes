# LoadBalancer Service

## Introduction

LoadBalancer is the most common Service type used in cloud environments.

It exposes applications to external users using a cloud provider's load balancer.

---

## What is LoadBalancer?

A LoadBalancer Service automatically provisions an external load balancer.

```text
Internet
    |
Load Balancer
    |
Service
    |
Pods
```

---

## Cloud Providers

Examples:

- Amazon EKS
- Azure AKS
- Google GKE

---

## Example

```yaml
apiVersion: v1
kind: Service

metadata:
  name: nginx-service

spec:
  type: LoadBalancer

  selector:
    app: nginx

  ports:
  - port: 80
    targetPort: 80
```

---

## Traffic Flow

```text
Internet
    |
Load Balancer
    |
Service
    |
-------------------
|                 |
Pod 1          Pod 2
```

---

## Benefits

### Public Access

Applications become accessible from the internet.

---

### High Availability

Traffic distributed across nodes.

---

### Automatic Provisioning

Cloud provider creates and manages the load balancer.

---

## Verify

```bash
kubectl get svc
```

Example:

```text
NAME            TYPE           EXTERNAL-IP
nginx-service   LoadBalancer   34.120.10.5
```

---

## Real-Life Analogy

Think of a call center.

Customers call one public number.

Calls are automatically distributed to available agents.

---

## Summary

LoadBalancer Services expose applications to the internet using cloud provider load balancers.

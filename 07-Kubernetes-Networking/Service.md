# Kubernetes Service

## Introduction

Pods are ephemeral in nature.

This means Pods can be:

- Created
- Deleted
- Recreated

at any time.

Whenever a Pod is recreated, its IP address may change.

This creates a problem because applications need a stable way to communicate.

Kubernetes solves this problem using Services.

---

## What is a Service?

A Service is an abstraction that provides a stable network endpoint for a group of Pods.

Instead of connecting directly to Pods, applications connect to a Service.

```text
Client
   |
Service
   |
-----------------
|       |       |
Pod1   Pod2   Pod3
```

---

## Why Do We Need Services?

Without Services:

```text
Frontend
    |
Pod IP
```

If Pod restarts:

```text
Old IP -> Gone
New IP -> Assigned
```

Application communication breaks.

---

## Solution

Service provides:

```text
Stable IP
Stable DNS Name
```

regardless of Pod changes.

---

## How Service Works

A Service uses Labels and Selectors.

Example:

Pods:

```yaml
labels:
  app: nginx
```

Service:

```yaml
selector:
  app: nginx
```

The Service automatically finds matching Pods.

---

## Types of Services

Kubernetes supports:

- ClusterIP
- NodePort
- LoadBalancer
- ExternalName

---

## Example Service

```yaml
apiVersion: v1
kind: Service

metadata:
  name: nginx-service

spec:
  selector:
    app: nginx

  ports:
  - port: 80
    targetPort: 80
```

---

## Useful Commands

List Services:

```bash
kubectl get svc
```

Describe Service:

```bash
kubectl describe svc nginx-service
```

Delete Service:

```bash
kubectl delete svc nginx-service
```

---

## Real-Life Analogy

Think of a customer support number.

Customers do not call individual employees.

They call a common support number.

The support system routes the request to available employees.

Similarly, Services route traffic to available Pods.

---

## Summary

A Service provides a stable network identity and load balancing for a group of Pods.

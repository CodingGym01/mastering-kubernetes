# ClusterIP Service

## Introduction

ClusterIP is the default Service type in Kubernetes.

It allows communication between applications inside the cluster.

---

## What is ClusterIP?

ClusterIP exposes a Service internally within the Kubernetes cluster.

Only resources inside the cluster can access it.

```text
Cluster
   |
ClusterIP Service
   |
Pods
```

External users cannot access it.

---

## Use Cases

Examples:

- Frontend → Backend
- Backend → Database
- Application → Redis
- Internal APIs

---

## Example

```yaml
apiVersion: v1
kind: Service

metadata:
  name: backend-service

spec:
  type: ClusterIP

  selector:
    app: backend

  ports:
  - port: 80
    targetPort: 8080
```

---

## Traffic Flow

```text
Frontend Pod
      |
backend-service
      |
-------------------
|                 |
Backend Pod 1   Backend Pod 2
```

---

## Important Characteristics

### Internal Access Only

Accessible only from inside the cluster.

---

### Stable Endpoint

Provides a permanent virtual IP.

---

### Built-in Load Balancing

Distributes traffic across Pods.

---

## Verify

```bash
kubectl get svc
```

Output:

```text
NAME              TYPE        CLUSTER-IP
backend-service   ClusterIP   10.96.0.10
```

---

## Real-Life Analogy

Think of an internal office extension number.

Employees can call it internally.

People outside the company cannot access it.

---

## Summary

ClusterIP is the default Service type used for internal communication between applications inside a Kubernetes cluster.

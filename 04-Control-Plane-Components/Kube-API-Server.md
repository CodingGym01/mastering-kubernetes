# Kube API Server

## Introduction

The kube-apiserver is the most important component in Kubernetes.

It acts as the central communication hub of the entire cluster.

Every operation performed in Kubernetes passes through the API Server.

Without the API Server, Kubernetes cannot function.

---

## What is Kube API Server?

The kube-apiserver is the front-end of the Kubernetes Control Plane.

It exposes Kubernetes APIs and processes all requests coming from:

- kubectl
- Kubelet
- Scheduler
- Controller Manager
- External Applications

---

## Why is API Server Needed?

Imagine a cluster with hundreds of nodes and components.

If every component communicated directly with every other component:

```text
Component A <----> Component B
Component A <----> Component C
Component B <----> Component C
...
```

Communication would become extremely complex.

Instead, Kubernetes uses a central communication point.

```text
All Components
       |
       v
API Server
```

---

## Responsibilities

### Authentication

Verifies the identity of users and services.

Example:

```bash
kubectl get pods
```

The API Server verifies who is making the request.

---

### Authorization

Checks whether the user has permission.

Example:

```text
User A → Allowed
User B → Denied
```

---

### Validation

Validates incoming requests.

Example:

```yaml
replicas: -5
```

Invalid configuration is rejected.

---

### State Management

Stores and retrieves cluster state from ETCD.

---

### Communication Hub

Acts as the communication layer between all Kubernetes components.

---

## Request Flow Example

```bash
kubectl get pods
```

Flow:

```text
kubectl
   |
API Server
   |
ETCD
   |
Response
```

---

## Internal Communication

The following components communicate through the API Server:

```text
Scheduler
Controller Manager
Kubelet
kubectl
```

None of them directly modify ETCD.

Only the API Server interacts with ETCD.

---

## Real-Life Analogy

Think of a bank.

Customer → API Server

Vault → ETCD

The customer never accesses the vault directly.

Everything goes through the bank counter.

Similarly, ETCD is never accessed directly by users.

---

## Summary

The kube-apiserver is the central entry point of Kubernetes.

It handles:

- Authentication
- Authorization
- Validation
- API Requests
- Cluster Communication
- ETCD Interactions

Every Kubernetes operation passes through the API Server.

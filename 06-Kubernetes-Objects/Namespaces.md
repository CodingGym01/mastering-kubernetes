# Namespaces

## Introduction

Namespaces provide logical isolation within a Kubernetes cluster.

They help organize and separate resources.

---

## Why Namespaces?

Imagine:

```text
Development Team
Testing Team
Production Team
```

all using the same cluster.

Without namespaces:

```text
Resource conflicts
Naming conflicts
Management complexity
```

---

## Solution

Namespaces create logical boundaries.

```text
Cluster
 |
 -------------------------
 |           |           |
Dev       Test       Prod
```

---

## Default Namespaces

### default

Default namespace for user-created resources.

---

### kube-system

Contains Kubernetes system components.

Examples:

```text
CoreDNS
Kube Proxy
ETCD
```

---

### kube-public

Publicly accessible resources.

---

### kube-node-lease

Stores node heartbeat information.

---

## Create Namespace

```bash
kubectl create namespace dev
```

---

## List Namespaces

```bash
kubectl get namespaces
```

---

## Create Resource in Namespace

```yaml
metadata:
  name: nginx-pod
  namespace: dev
```

---

## View Resources

```bash
kubectl get pods -n dev
```

---

## Real-Life Analogy

Think of namespaces as separate departments inside a company.

Each department has its own resources while sharing the same building.

---

## Summary

Namespaces provide logical isolation and help organize resources inside a Kubernetes cluster.

# ETCD

## Introduction

ETCD is one of the most critical components of Kubernetes.

It acts as the cluster's database.

Everything Kubernetes knows about the cluster is stored inside ETCD.

---

## What is ETCD?

ETCD is a distributed key-value database.

It stores:

- Cluster state
- Configuration data
- Secrets
- Node information
- Pod information
- Service information

---

## Why ETCD is Important?

Imagine ETCD suddenly disappears.

Kubernetes would lose information about:

```text
Pods
Nodes
Deployments
Services
Secrets
ConfigMaps
```

The cluster would no longer know its desired state.

---

## What Does ETCD Store?

Examples:

### Pod Information

```text
nginx-pod
Running
Worker-1
```

---

### Deployment Information

```text
Deployment Name: nginx
Replicas: 3
```

---

### Node Information

```text
Worker Node 1
Ready
```

---

### Secrets

```text
Database Password
API Keys
```

---

## ETCD Architecture

```text
API Server
     |
     v
   ETCD
```

Only the API Server interacts directly with ETCD.

---

## Key-Value Example

Example:

```text
Key:
deployment/nginx

Value:
replicas=3
```

ETCD stores data in key-value format.

---

## Distributed Nature

ETCD can run as a cluster.

Example:

```text
ETCD Node 1
ETCD Node 2
ETCD Node 3
```

Data is replicated between nodes.

This provides high availability.

---

## Real-Life Analogy

Think of ETCD as a hospital database.

Doctors = Kubernetes Components

Database = ETCD

Doctors access patient records through applications.

They do not directly manipulate database files.

---

## Backup Importance

ETCD backup is one of the most important Kubernetes administrative tasks.

Without ETCD backup:

Cluster recovery becomes extremely difficult.

---

## Summary

ETCD is the source of truth for Kubernetes.

It stores all cluster-related information and maintains the current and desired state of the cluster.

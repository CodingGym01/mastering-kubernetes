# Pod

## Introduction

A Pod is the smallest deployable unit in Kubernetes.

Whenever we run an application in Kubernetes, it runs inside a Pod.

Pods are the fundamental building blocks of Kubernetes workloads.

---

## What is a Pod?

A Pod is a wrapper around one or more containers.

Instead of running containers directly, Kubernetes runs Pods.

```text
Pod
 |
 └── Container
```

Most commonly:

```text
1 Pod = 1 Container
```

Although a Pod can contain multiple containers.

---

## Why Do We Need Pods?

Kubernetes was designed to manage distributed applications.

Pods provide:

- Shared Network
- Shared Storage
- Shared Lifecycle

for containers running together.

---

## Pod Characteristics

### Shared Network

All containers inside a Pod share the same IP address.

```text
Pod IP: 10.1.1.10

Container A
Container B
```

Both containers use the same network namespace.

---

### Shared Storage

Containers can share volumes.

```text
Pod
 |
 Volume
 |
 ----------------
 |              |
ContainerA   ContainerB
```

---

### Shared Lifecycle

Containers inside a Pod are created and terminated together.

---

## Single Container Pod

Most common scenario:

```text
Pod
 |
 Nginx Container
```

---

## Multi-Container Pod

Example:

```text
Pod
 |
 --------------------
 |                  |
App Container   Log Agent
```

Both containers work together.

---

## Creating a Pod

Example YAML:

```yaml
apiVersion: v1
kind: Pod

metadata:
  name: nginx-pod

spec:
  containers:
  - name: nginx
    image: nginx:latest
```

Create:

```bash
kubectl apply -f pod.yaml
```

---

## Useful Commands

Create Pod:

```bash
kubectl apply -f pod.yaml
```

List Pods:

```bash
kubectl get pods
```

Describe Pod:

```bash
kubectl describe pod nginx-pod
```

Delete Pod:

```bash
kubectl delete pod nginx-pod
```

---

## Pod Lifecycle

```text
Pending
   |
Running
   |
Succeeded / Failed
```

---

## Important Limitation

Pods are temporary.

If a Pod is deleted:

```text
Pod Deleted
     |
Data Lost
```

unless persistent storage is configured.

---

## Real-Life Analogy

Think of a Pod as an apartment.

Containers are people living inside.

They share:

- Same address
- Same utilities
- Same building

---

## Summary

Pods are the smallest deployable unit in Kubernetes and serve as the execution environment for containers.

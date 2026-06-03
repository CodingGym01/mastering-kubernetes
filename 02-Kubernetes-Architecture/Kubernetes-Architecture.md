# Kubernetes Architecture

## Introduction

Understanding Kubernetes architecture is one of the most important topics for every DevOps engineer.

Every request in Kubernetes passes through multiple components before an application starts running.

Understanding how these components communicate helps in troubleshooting and cluster administration.

---

## High-Level Architecture

```text
                        User
                          |
                          |
                    kubectl CLI
                          |
                          |
                +------------------+
                |  API Server      |
                +------------------+
                          |
      -----------------------------------------
      |                |               |
      |                |               |
   Scheduler         ETCD      Controller Manager
      |
      |
----------------------------------------------------
|                      Cluster                      |
----------------------------------------------------
      |                               |
      |                               |
+-------------+                +-------------+
| Worker-1    |                | Worker-2    |
|             |                |             |
| Kubelet     |                | Kubelet     |
| Kube Proxy  |                | Kube Proxy  |
| Containerd  |                | Containerd  |
| Pods        |                | Pods        |
+-------------+                +-------------+
```

---

## Request Flow

Let's understand what happens when a user deploys an application.

Example:

```bash
kubectl apply -f nginx.yaml
```

---

### Step 1

User sends request using kubectl.

```text
User
  |
kubectl
```

---

### Step 2

Request reaches API Server.

```text
kubectl
    |
API Server
```

The API Server acts as the entry point of Kubernetes.

Every request passes through it.

---

### Step 3

API Server stores desired state inside ETCD.

```text
API Server
      |
     ETCD
```

ETCD stores cluster information.

---

### Step 4

Scheduler identifies a suitable Worker Node.

```text
Scheduler
     |
Worker Node
```

---

### Step 5

Kubelet receives instructions.

```text
API Server
      |
   Kubelet
```

---

### Step 6

Kubelet asks Container Runtime to create containers.

```text
Kubelet
    |
Containerd
```

---

### Step 7

Container starts running inside a Pod.

```text
Pod
 |
Container
```

Application becomes available.

---

## Desired State Concept

One of Kubernetes' most powerful concepts is Desired State.

Example:

User wants:

```text
3 Nginx Pods
```

Current State:

```text
2 Running Pods
```

Kubernetes automatically creates one more Pod.

This process continues continuously.

---

## Self-Healing Example

Desired State:

```text
3 Pods
```

Current State:

```text
2 Pods
```

If one Pod crashes:

```text
Pod Crash
      ↓
Kubernetes Detects Failure
      ↓
New Pod Created
```

This is called Self-Healing.

---

## Summary

The basic request flow is:

```text
kubectl
    ↓
API Server
    ↓
ETCD
    ↓
Scheduler
    ↓
Kubelet
    ↓
Container Runtime
    ↓
Pod
```

Understanding this flow is essential for learning Kubernetes.

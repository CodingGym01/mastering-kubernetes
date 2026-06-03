# Kubernetes Runtime Workflow

## Introduction

One of the most common questions is:

How does Kubernetes actually start a container?

This document explains the complete workflow.

---

## Step 1: User Creates Deployment

Example:

```bash
kubectl apply -f nginx.yaml
```

User submits a deployment request.

---

## Step 2: API Server Receives Request

```text
kubectl
    |
API Server
```

The API Server validates and accepts the request.

---

## Step 3: Desired State Stored in ETCD

```text
API Server
     |
    ETCD
```

The cluster state is stored.

---

## Step 4: Scheduler Selects Worker Node

```text
Scheduler
     |
 Worker Node
```

The scheduler determines the most suitable node.

---

## Step 5: Kubelet Receives Instructions

```text
API Server
      |
   Kubelet
```

The kubelet notices that a new Pod should be created.

---

## Step 6: Kubelet Uses CRI

```text
Kubelet
    |
   CRI
```

Kubelet communicates with the runtime through CRI.

---

## Step 7: Containerd Pulls Image

```text
Containerd
      |
 Docker Registry
```

The required image is downloaded.

Example:

```text
nginx:latest
```

---

## Step 8: Containerd Uses runc

```text
Containerd
      |
     runc
```

runc creates the container.

---

## Step 9: Container Starts

```text
Pod
 |
Container
```

Application becomes available.

---

## Complete Flow

```text
kubectl
   |
API Server
   |
ETCD
   |
Scheduler
   |
Kubelet
   |
CRI
   |
Containerd
   |
runc
   |
Container
```

---

## Important Interview Point

Remember:

```text
Kubernetes does NOT run containers.
```

Kubernetes manages containers.

Container runtimes actually run containers.

Examples:

- containerd
- CRI-O

---

## Summary

The complete container startup workflow is:

1. User submits request.
2. API Server accepts request.
3. ETCD stores state.
4. Scheduler selects node.
5. Kubelet receives instructions.
6. CRI communicates with runtime.
7. Containerd manages lifecycle.
8. runc creates container.
9. Application starts.

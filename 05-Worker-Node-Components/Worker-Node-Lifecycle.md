# Worker Node Lifecycle

## Introduction

Understanding how a Worker Node processes workloads helps in understanding the complete Kubernetes workflow.

This document explains what happens from Pod creation to application execution.

---

## Step 1: User Creates Deployment

Example:

```bash
kubectl apply -f nginx.yaml
```

A request is sent to Kubernetes.

---

## Step 2: API Server Receives Request

```text
User
  |
API Server
```

The request is validated and stored.

---

## Step 3: ETCD Stores Desired State

```text
API Server
    |
   ETCD
```

Cluster state is updated.

---

## Step 4: Scheduler Selects Worker Node

Example:

```text
Worker-1
Worker-2
Worker-3
```

Scheduler chooses the most suitable node.

---

## Step 5: Pod Assignment

The selected Worker Node receives the Pod assignment.

---

## Step 6: Kubelet Detects Assignment

```text
API Server
    |
Kubelet
```

Kubelet notices a new Pod should be created.

---

## Step 7: Kubelet Contacts Runtime

```text
Kubelet
    |
Container Runtime
```

Instructions are sent through CRI.

---

## Step 8: Image Pull

The runtime downloads the required image.

Example:

```text
nginx:latest
```

---

## Step 9: Container Creation

```text
Container Runtime
      |
      runc
      |
 Container Created
```

---

## Step 10: Pod Running

```text
Pod
 |
Running
```

The application becomes available.

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
Worker Node
   |
Kubelet
   |
CRI
   |
Container Runtime
   |
runc
   |
Container
   |
Pod Running
```

---

## Failure Scenario

Suppose:

```text
Pod Crash
```

Kubelet detects the issue.

The Controller Manager compares:

```text
Desired State
Current State
```

A replacement Pod is created automatically.

This is known as Self-Healing.

---

## Summary

Worker Nodes are responsible for executing workloads.

The workflow involves:

1. Receiving Pod assignments.
2. Creating containers.
3. Running applications.
4. Monitoring health.
5. Reporting status back to the Control Plane.

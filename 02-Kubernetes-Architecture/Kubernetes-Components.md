# Kubernetes Components Overview

## Introduction

Kubernetes consists of multiple components.

Each component has a specific responsibility.

Together they ensure applications are deployed and managed efficiently.

---

# Control Plane Components

The Control Plane contains the following components:

---

## kube-apiserver

The API Server is the central communication hub of Kubernetes.

Responsibilities:

- Accept requests
- Validate requests
- Authenticate users
- Authorize users
- Update cluster state

Every component communicates through the API Server.

---

## ETCD

ETCD is a distributed key-value database.

Responsibilities:

- Store cluster configuration
- Store cluster state
- Store secrets
- Store object information

If ETCD is lost, cluster information is lost.

---

## kube-scheduler

The Scheduler decides where Pods should run.

Responsibilities:

- Select worker nodes
- Evaluate resource availability
- Apply scheduling policies

The scheduler does not create Pods.

It only selects the best node.

---

## kube-controller-manager

The Controller Manager maintains the desired state of the cluster.

Responsibilities:

- Monitor resources
- Detect failures
- Create replacement Pods
- Maintain desired replicas

This component enables Kubernetes self-healing.

---

# Worker Node Components

Worker Nodes contain the following components.

---

## kubelet

Kubelet is an agent running on every Worker Node.

Responsibilities:

- Communicate with API Server
- Create Pods
- Monitor Pod health
- Report node status

---

## kube-proxy

Kube Proxy manages networking.

Responsibilities:

- Service networking
- Traffic forwarding
- Load balancing

It ensures users can access applications running inside Pods.

---

## Container Runtime

Container Runtime runs containers.

Examples:

- containerd
- CRI-O

Responsibilities:

- Pull images
- Create containers
- Start containers
- Stop containers

---

## Pods

Pods are the smallest deployable unit in Kubernetes.

Applications run inside Pods.

A Pod may contain:

- One container
- Multiple containers

Most commonly:

```text
1 Pod = 1 Container
```

---

## Complete Architecture

```text
Control Plane

├── API Server
├── ETCD
├── Scheduler
└── Controller Manager

Worker Node

├── Kubelet
├── Kube Proxy
├── Container Runtime
└── Pods
```

---

## Summary

Control Plane components make decisions.

Worker Node components execute those decisions.

Together they form a complete Kubernetes cluster.

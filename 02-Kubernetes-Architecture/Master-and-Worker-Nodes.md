# Master Node and Worker Node

## Introduction

A Kubernetes cluster consists of multiple machines called nodes.

These nodes are divided into two major categories:

1. Control Plane (Master Node)
2. Worker Node

Together, they form a Kubernetes cluster.

---

## Kubernetes Cluster Overview

```text
+--------------------------------------+
|          Control Plane               |
+--------------------------------------+
                |
                |
        -----------------
        |               |
        |               |
+---------------+ +---------------+
| Worker Node 1 | | Worker Node 2 |
+---------------+ +---------------+
```

The Control Plane manages the cluster.

The Worker Nodes run applications.

---

## What is a Control Plane?

The Control Plane is the brain of Kubernetes.

It is responsible for:

- Managing the cluster
- Making scheduling decisions
- Monitoring cluster state
- Maintaining desired state
- Handling API requests

Without the Control Plane, Kubernetes cannot function.

---

## Components of the Control Plane

The Control Plane contains:

- kube-apiserver
- etcd
- kube-scheduler
- kube-controller-manager

These components work together to manage the cluster.

---

## What is a Worker Node?

A Worker Node is a machine where actual applications run.

Applications are deployed inside Pods, and Pods run on Worker Nodes.

---

## Components of a Worker Node

Every Worker Node contains:

- kubelet
- kube-proxy
- Container Runtime
- Pods

These components ensure applications run properly.

---

## Responsibilities of Worker Nodes

Worker Nodes are responsible for:

- Running application containers
- Executing workloads
- Communicating with the Control Plane
- Maintaining Pod health
- Handling networking

---

## Example

Suppose we deploy an Nginx application.

```text
kubectl apply -f nginx.yaml
```

Control Plane decides:

- Where to run the Pod

Worker Node performs:

- Pod creation
- Container execution
- Health monitoring

---

## Real-Life Analogy

Consider a company.

CEO Office = Control Plane

Employees = Worker Nodes

The CEO decides:

- What work should be done
- Who should perform it

Employees execute the actual work.

Similarly:

Control Plane makes decisions.

Worker Nodes execute workloads.

---

## Summary

A Kubernetes cluster consists of:

- Control Plane (decision maker)
- Worker Nodes (work executors)

The Control Plane manages the cluster while Worker Nodes run applications.

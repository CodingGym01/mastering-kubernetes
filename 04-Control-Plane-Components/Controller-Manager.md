# Kube Controller Manager

## Introduction

The Controller Manager is responsible for maintaining the desired state of the cluster.

It continuously watches Kubernetes resources and takes corrective actions whenever the current state differs from the desired state.

---

## Desired State Concept

Example:

Desired State:

```text
3 Nginx Pods
```

Current State:

```text
2 Running Pods
```

Controller Manager detects the difference and creates a new Pod.

---

## Responsibilities

### Self-Healing

Recreates failed Pods.

---

### Maintaining Replicas

Ensures the required number of Pods are running.

---

### Monitoring Resources

Continuously monitors Kubernetes objects.

---

### Corrective Actions

Takes actions when the cluster state changes unexpectedly.

---

## Common Controllers

### Deployment Controller

Maintains desired Pod replicas.

---

### ReplicaSet Controller

Ensures specified replicas remain running.

---

### Node Controller

Monitors node health.

---

### Service Account Controller

Manages service accounts.

---

### Job Controller

Manages batch jobs.

---

## Example

Desired:

```text
3 Pods
```

Current:

```text
2 Pods
```

Action:

```text
Controller Manager
        |
Create New Pod
```

---

## Real-Life Analogy

Imagine a hotel manager.

Required:

```text
10 Employees
```

Available:

```text
8 Employees
```

Manager hires 2 more employees.

The Controller Manager works similarly.

---

## Summary

The Controller Manager continuously watches the cluster and ensures the actual state matches the desired state.

# Kube Scheduler

## Introduction

The Scheduler is responsible for deciding where Pods should run.

It does not create Pods.

It only selects the most suitable Worker Node.

---

## Why Scheduler is Needed?

Imagine a cluster:

```text
Worker-1
Worker-2
Worker-3
Worker-4
```

When a new Pod is created:

```text
nginx-pod
```

Which node should run it?

This decision is made by the Scheduler.

---

## Responsibilities

### Node Selection

Chooses the best node for a Pod.

---

### Resource Evaluation

Checks:

- CPU
- Memory
- Storage

availability.

---

### Policy Enforcement

Considers:

- Node Affinity
- Taints
- Tolerations
- Constraints

---

## Scheduling Process

Step 1:

Pod created.

```text
Pod
 |
Pending
```

---

Step 2:

Scheduler identifies eligible nodes.

---

Step 3:

Scheduler scores nodes.

---

Step 4:

Best node selected.

---

Step 5:

Pod assigned.

```text
Pending
    |
Assigned
```

---

## Example

Cluster:

```text
Worker-1 → 90% CPU
Worker-2 → 30% CPU
Worker-3 → 20% CPU
```

Scheduler will likely choose:

```text
Worker-3
```

because it has more available resources.

---

## Real-Life Analogy

Imagine assigning tasks to employees.

Manager receives a task.

The manager chooses the employee with:

- Availability
- Required skills
- Capacity

Similarly, the Scheduler assigns Pods to nodes.

---

## Summary

The Scheduler decides where Pods should run.

It evaluates cluster resources and policies to select the most suitable Worker Node.

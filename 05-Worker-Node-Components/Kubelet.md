# Kubelet

## Introduction

Kubelet is one of the most important components running on every Kubernetes Worker Node.

It acts as an agent between the Kubernetes Control Plane and the Worker Node.

Without kubelet, a Worker Node cannot join or function within a Kubernetes cluster.

---

## What is Kubelet?

Kubelet is a node agent that runs on every Worker Node.

Its primary responsibility is to ensure that containers described in Pod specifications are running correctly.

In simple terms:

```text
Control Plane
      |
      v
   Kubelet
      |
      v
Containers
```

Kubelet receives instructions from the Control Plane and ensures they are executed on the Worker Node.

---

## Responsibilities of Kubelet

### Pod Management

Creates and manages Pods assigned to the node.

---

### Container Monitoring

Continuously monitors running containers.

---

### Node Status Reporting

Sends node health information to the API Server.

---

### Health Checks

Performs liveness and readiness checks.

---

### Runtime Communication

Communicates with the container runtime through CRI.

---

## Kubelet Workflow

When a Pod is assigned:

```text
Scheduler
    |
Assign Pod
    |
API Server
    |
Kubelet
    |
Container Runtime
    |
Container Starts
```

---

## Example

User creates:

```bash
kubectl apply -f nginx.yaml
```

The Scheduler assigns the Pod to Worker Node-1.

Kubelet on Worker Node-1 notices the assignment and starts the Pod.

---

## What Happens if a Container Crashes?

Example:

```text
Nginx Container
      |
   Crash
```

Kubelet detects the failure and reports it to the Control Plane.

The Controller Manager then ensures the desired state is restored.

---

## Real-Life Analogy

Think of a factory.

Factory Owner = Control Plane

Supervisor = Kubelet

Workers = Containers

The owner gives instructions.

The supervisor ensures the workers are actually doing their jobs.

---

## Important Points

- Runs on every Worker Node.
- Communicates with the API Server.
- Creates and manages Pods.
- Monitors container health.
- Reports node status.

---

## Summary

Kubelet is the node agent responsible for ensuring that Pods assigned to a Worker Node are running as expected.

It acts as the bridge between Kubernetes and the container runtime.

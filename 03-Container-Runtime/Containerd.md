# Containerd

## Introduction

Containerd is one of the most widely used container runtimes in Kubernetes environments.

It is responsible for managing the complete lifecycle of containers.

---

## What is Containerd?

Containerd is a high-performance container runtime that manages:

- Image pulling
- Image storage
- Container creation
- Container execution
- Container monitoring

It acts as the runtime responsible for running containers on Kubernetes worker nodes.

---

## History

Originally, Docker included many components:

```text
Docker CLI
Docker API
Container Management
Image Management
Runtime
```

Over time, Docker extracted the container runtime functionality into a separate project called Containerd.

Today:

```text
Docker
    |
Containerd
```

Even Docker itself uses Containerd internally.

---

## Why Kubernetes Uses Containerd

Earlier Kubernetes used Docker directly.

```text
Kubernetes
     |
   Docker
```

However, Docker was not designed specifically for Kubernetes.

After CRI was introduced:

```text
Kubernetes
     |
    CRI
     |
Containerd
```

This architecture became simpler and more efficient.

---

## Responsibilities of Containerd

### Image Management

Pull images from registries.

Example:

```bash
docker pull nginx
```

Equivalent actions happen through Containerd.

---

### Container Lifecycle

Manages:

- Create
- Start
- Stop
- Delete

operations.

---

### Storage Management

Handles image layers and snapshots.

---

### Runtime Integration

Works with OCI-compliant runtimes like runc.

---

## Architecture

```text
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

## What is runc?

runc is the low-level OCI runtime that actually creates and starts containers.

Containerd manages containers.

runc executes containers.

---

## Real-Life Analogy

Think of a restaurant.

Customer = Kubernetes

Manager = Containerd

Chef = runc

Food = Container

Customer places an order.

Manager coordinates everything.

Chef prepares the food.

---

## Benefits of Containerd

- Lightweight
- Fast
- Stable
- OCI Compliant
- CRI Compatible
- Production Ready

---

## Summary

Containerd is a container runtime used by Kubernetes to manage container lifecycles.

It works with CRI and OCI standards and uses runc to actually execute containers.

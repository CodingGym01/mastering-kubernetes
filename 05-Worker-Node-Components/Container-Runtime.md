# Container Runtime

## Introduction

Containers do not run by themselves.

A component is required to create, start, stop, and manage containers.

This component is known as a Container Runtime.

---

## What is a Container Runtime?

A Container Runtime is software responsible for running containers on a Worker Node.

Kubernetes uses container runtimes through the Container Runtime Interface (CRI).

---

## Responsibilities

### Pull Images

Downloads container images from registries.

Example:

```text
nginx:latest
```

---

### Create Containers

Creates containers using downloaded images.

---

### Start Containers

Launches application processes.

---

### Stop Containers

Stops running containers when required.

---

### Delete Containers

Removes containers when they are no longer needed.

---

## Popular Container Runtimes

### Containerd

Most widely used runtime in Kubernetes.

---

### CRI-O

Lightweight runtime specifically designed for Kubernetes.

---

## Runtime Architecture

```text
Kubelet
   |
  CRI
   |
Container Runtime
   |
  runc
   |
Container
```

---

## Container Startup Process

```text
Kubelet
    |
Container Runtime
    |
Pull Image
    |
Create Container
    |
Start Container
```

---

## Real-Life Analogy

Imagine building construction.

Architect = Kubernetes

Site Manager = Container Runtime

Workers = Containers

The architect creates plans.

The site manager executes those plans.

---

## Important Points

- Runs on every Worker Node.
- Creates and manages containers.
- Works through CRI.
- Uses OCI-compliant runtimes.

---

## Summary

The Container Runtime is responsible for the complete lifecycle of containers, including image management, container creation, execution, and deletion.

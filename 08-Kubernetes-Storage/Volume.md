# Volumes in Kubernetes

## Introduction

Containers are ephemeral by nature.

This means data stored inside a container may be lost when the container stops or is recreated.

To solve this problem, Kubernetes provides Volumes.

---

## Why Do We Need Volumes?

Imagine an application running inside a Pod.

```text
Pod
 |
Container
 |
Application Data
```

If the Pod crashes:

```text
Pod Deleted
     |
Container Deleted
     |
Data Lost
```

This is unacceptable for databases and production applications.

---

## What is a Volume?

A Volume is a storage mechanism that allows data to persist beyond the lifecycle of a container.

Volumes are attached to Pods and can be shared by containers within the same Pod.

---

## Benefits of Volumes

### Data Persistence

Data survives container restarts.

### Shared Storage

Multiple containers can access the same data.

### Decoupled Storage

Storage exists independently from containers.

---

## Example

```yaml
apiVersion: v1
kind: Pod

metadata:
  name: nginx-pod

spec:
  containers:
  - name: nginx
    image: nginx

    volumeMounts:
    - mountPath: /data
      name: app-storage

  volumes:
  - name: app-storage
    emptyDir: {}
```

---

## Common Volume Types

### emptyDir

Temporary storage.

Deleted when Pod is removed.

---

### hostPath

Uses storage from the Worker Node.

---

### Persistent Volumes

Long-term storage managed by Kubernetes.

---

## Real-Life Analogy

Think of a laptop.

Applications are installed software.

The hard disk is the volume.

Even if the application closes, data remains on disk.

---

## Summary

Volumes provide storage for containers and help preserve data beyond container restarts.

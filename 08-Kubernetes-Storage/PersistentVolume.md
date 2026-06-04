# Persistent Volume (PV)

## Introduction

Volumes solve storage issues inside Pods.

However, managing storage manually for every Pod becomes difficult.

Kubernetes introduces Persistent Volumes (PV) to provide cluster-wide storage resources.

---

## What is a Persistent Volume?

A Persistent Volume (PV) is a storage resource in the Kubernetes cluster.

It is created and managed independently of Pods.

---

## Key Idea

Pods come and go.

Storage should remain.

```text
Pod Deleted
      |
Persistent Volume Exists
```

---

## PV Lifecycle

```text
Admin Creates PV
       |
Pod Uses PV
       |
Pod Deleted
       |
PV Remains
```

---

## Example

```yaml
apiVersion: v1
kind: PersistentVolume

metadata:
  name: nginx-pv

spec:
  capacity:
    storage: 5Gi

  accessModes:
    - ReadWriteOnce

  hostPath:
    path: /data/nginx
```

---

## Important Fields

### Capacity

Storage size.

```yaml
storage: 5Gi
```

---

### Access Modes

Defines how storage can be mounted.

Examples:

```text
ReadWriteOnce (RWO)
ReadOnlyMany (ROX)
ReadWriteMany (RWX)
```

---

## Benefits

- Persistent storage
- Independent lifecycle
- Reusable storage
- Better resource management

---

## Real-Life Analogy

Think of a rented warehouse.

Applications may come and go, but the warehouse remains available.

---

## Summary

Persistent Volumes provide long-term storage resources that exist independently of Pods.

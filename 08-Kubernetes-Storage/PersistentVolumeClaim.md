# Persistent Volume Claim (PVC)

## Introduction

Applications should not directly interact with Persistent Volumes.

Instead, they request storage through Persistent Volume Claims.

---

## What is a PVC?

A Persistent Volume Claim (PVC) is a request for storage by a Pod.

Think of it as a storage request form.

---

## Relationship

```text
Pod
 |
PVC
 |
PV
 |
Storage
```

---

## Why PVC?

Without PVC:

```text
Application
      |
Direct Storage Management
```

This becomes difficult and inflexible.

PVC abstracts storage consumption.

---

## Example PVC

```yaml
apiVersion: v1
kind: PersistentVolumeClaim

metadata:
  name: nginx-pvc

spec:
  accessModes:
    - ReadWriteOnce

  resources:
    requests:
      storage: 2Gi
```

---

## Binding Process

Step 1:

PV Available

```text
5Gi PV
```

Step 2:

PVC Request

```text
2Gi PVC
```

Step 3:

Kubernetes Binds PVC to PV

---

## Pod Using PVC

```yaml
volumes:
- name: app-storage

  persistentVolumeClaim:
    claimName: nginx-pvc
```

---

## Real-Life Analogy

Imagine booking a hotel room.

Hotel = PV

Booking Request = PVC

Guest = Pod

The guest never manages the entire hotel.

The guest only requests a room.

---

## Summary

PVCs provide an abstraction layer between applications and storage resources.

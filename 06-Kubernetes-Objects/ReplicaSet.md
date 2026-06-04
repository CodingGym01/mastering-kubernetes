# ReplicaSet

## Introduction

ReplicaSet ensures that a specified number of Pod replicas are always running.

It provides self-healing and high availability.

---

## Problem Without ReplicaSet

Suppose:

```text
1 Nginx Pod
```

If it crashes:

```text
Application Down
```

---

## Solution

ReplicaSet continuously monitors Pods.

Desired:

```text
3 Pods
```

Current:

```text
2 Pods
```

ReplicaSet creates a new Pod automatically.

---

## Example YAML

```yaml
apiVersion: apps/v1
kind: ReplicaSet

metadata:
  name: nginx-rs

spec:
  replicas: 3

  selector:
    matchLabels:
      app: nginx

  template:
    metadata:
      labels:
        app: nginx

    spec:
      containers:
      - name: nginx
        image: nginx
```

---

## Create ReplicaSet

```bash
kubectl apply -f replicaset.yaml
```

---

## Verify

```bash
kubectl get rs
```

---

## Scaling

Increase replicas:

```yaml
replicas: 5
```

Apply again:

```bash
kubectl apply -f replicaset.yaml
```

---

## Limitation

ReplicaSets only manage Pods.

They do not provide:

- Rolling Updates
- Rollbacks

Deployments solve these limitations.

---

## Summary

ReplicaSet ensures the desired number of Pod replicas are always running.

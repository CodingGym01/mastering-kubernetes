# Deployment

## Introduction

Deployment is one of the most commonly used Kubernetes resources.

It provides a higher-level abstraction over ReplicaSets.

---

## Why Deployments?

ReplicaSets can maintain Pod replicas.

However, they cannot perform:

- Rolling Updates
- Rollbacks
- Version Management

Deployments solve these problems.

---

## Deployment Architecture

```text
Deployment
     |
ReplicaSet
     |
Pods
```

---

## Example Deployment

```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: nginx-deployment

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
        image: nginx:latest
```

---

## Create Deployment

```bash
kubectl apply -f deployment.yaml
```

---

## Verify Deployment

```bash
kubectl get deployments
```

---

## View ReplicaSets

```bash
kubectl get rs
```

---

## View Pods

```bash
kubectl get pods
```

---

## Scaling

Scale replicas:

```yaml
replicas: 5
```

Apply again:

```bash
kubectl apply -f deployment.yaml
```

---

## Rolling Update

Update image:

```yaml
image: nginx:1.27
```

Deployment gradually replaces old Pods.

```text
Old Pod
    |
New Pod
```

No downtime occurs.

---

## Rollback

View history:

```bash
kubectl rollout history deployment nginx-deployment
```

Rollback:

```bash
kubectl rollout undo deployment nginx-deployment
```

---

## Why Deployments Are Preferred

Deployments provide:

- Self-Healing
- Scaling
- Rolling Updates
- Rollbacks
- Version Control

---

## Summary

Deployments are the recommended way to run stateless applications in Kubernetes and are built on top of ReplicaSets.

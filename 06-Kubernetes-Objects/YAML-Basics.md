# YAML Basics

## Introduction

YAML is the language used to define Kubernetes resources.

Almost every Kubernetes object is created using YAML files.

Examples:

- Pods
- Deployments
- Services
- ConfigMaps
- Secrets

---

## What is YAML?

YAML stands for:

```text
YAML Ain't Markup Language
```

It is a human-readable data serialization format.

---

## Why YAML?

YAML is:

- Easy to read
- Easy to write
- Human-friendly
- Widely used in DevOps tools

---

## Basic Structure

Example:

```yaml
name: nginx
version: 1.0
environment: production
```

---

## Indentation Rules

YAML uses spaces.

Correct:

```yaml
spec:
  containers:
    - name: nginx
```

Wrong:

```yaml
spec:
containers:
- name: nginx
```

---

## Kubernetes YAML Structure

Every Kubernetes manifest follows:

```yaml
apiVersion:
kind:
metadata:
spec:
```

---

## apiVersion

Defines Kubernetes API version.

Example:

```yaml
apiVersion: v1
```

---

## kind

Defines object type.

Example:

```yaml
kind: Pod
```

---

## metadata

Contains object information.

Example:

```yaml
metadata:
  name: nginx-pod
```

---

## spec

Contains desired configuration.

Example:

```yaml
spec:
  containers:
  - name: nginx
    image: nginx
```

---

## Complete Example

```yaml
apiVersion: v1
kind: Pod

metadata:
  name: nginx-pod

spec:
  containers:
  - name: nginx
    image: nginx
```

---

## Applying YAML

```bash
kubectl apply -f pod.yaml
```

---

## Viewing YAML

```bash
kubectl get pod nginx-pod -o yaml
```

---

## Summary

YAML is the declarative language used by Kubernetes to define infrastructure and application resources.

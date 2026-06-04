# Labels and Selectors

## Introduction

Labels and Selectors are used to organize and identify Kubernetes resources.

They are one of the most important concepts in Kubernetes.

---

## What are Labels?

Labels are key-value pairs attached to Kubernetes objects.

Example:

```yaml
labels:
  app: nginx
  env: production
  team: devops
```

---

## Why Labels?

Imagine:

```text
100 Pods
```

Without labels, identifying specific Pods would be difficult.

Labels help categorize resources.

---

## Example

```yaml
metadata:
  labels:
    app: nginx
    env: production
```

---

## Common Labels

```yaml
app: nginx
env: production
team: devops
version: v1
```

---

## What are Selectors?

Selectors are used to find resources matching labels.

Example:

```yaml
selector:
  app: nginx
```

This matches all resources with:

```yaml
app: nginx
```

---

## Example

Pods:

```text
Pod1 → app=nginx
Pod2 → app=nginx
Pod3 → app=apache
```

Selector:

```yaml
app: nginx
```

Matches:

```text
Pod1
Pod2
```

---

## Command Example

List Pods by label:

```bash
kubectl get pods -l app=nginx
```

---

## Real-Life Analogy

Think of labels as tags on books.

Examples:

```text
Science
History
Programming
```

Selectors are used to search books with specific tags.

---

## Summary

Labels organize resources.

Selectors find resources based on labels.

Many Kubernetes components rely on labels and selectors.

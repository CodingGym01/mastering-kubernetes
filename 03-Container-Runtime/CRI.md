# Container Runtime Interface (CRI)

## Introduction

Kubernetes does not run containers directly.

Instead, Kubernetes communicates with a Container Runtime, and the Container Runtime is responsible for creating and managing containers.

To ensure Kubernetes can work with different container runtimes, Kubernetes introduced the Container Runtime Interface (CRI).

---

## What is CRI?

CRI (Container Runtime Interface) is a standard interface defined by Kubernetes that allows kubelet to communicate with different container runtimes.

Think of CRI as a common language between Kubernetes and container runtimes.

---

## Why Was CRI Created?

Initially, Kubernetes was tightly coupled with Docker.

```text
Kubernetes
    |
 Docker
```

This approach had limitations:

- Kubernetes became dependent on Docker.
- Supporting new runtimes became difficult.
- Runtime innovation was restricted.

To solve this problem, Kubernetes introduced CRI.

---

## How CRI Works

Instead of talking directly to Docker, kubelet communicates through CRI.

```text
Kubelet
   |
  CRI
   |
Container Runtime
```

As long as a runtime supports CRI, Kubernetes can use it.

---

## Supported CRI Runtimes

Examples:

- containerd
- CRI-O

These runtimes implement the CRI specification and can communicate directly with Kubernetes.

---

## Real-Life Analogy

Imagine people from different countries.

Instead of learning every language, everyone agrees to use English.

```text
Person A
    |
 English
    |
Person B
```

Similarly:

```text
Kubelet
    |
   CRI
    |
Runtime
```

CRI acts as the common language.

---

## Benefits of CRI

### Runtime Independence

Kubernetes can work with multiple runtimes.

### Flexibility

Organizations can choose the runtime they prefer.

### Standardization

All runtimes follow the same communication model.

### Future-Proof Design

New runtimes can be added without changing Kubernetes.

---

## Example Workflow

```text
kubectl apply -f nginx.yaml
           |
           v
       API Server
           |
           v
        Kubelet
           |
           v
          CRI
           |
           v
      Containerd
           |
           v
       Container
```

---

## Summary

CRI is a standard interface that enables Kubernetes to communicate with container runtimes.

It allows Kubernetes to remain runtime-agnostic and support multiple container runtimes efficiently.

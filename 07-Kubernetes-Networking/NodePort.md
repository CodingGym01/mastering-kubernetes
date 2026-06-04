# NodePort Service

## Introduction

Sometimes applications need to be accessible from outside the cluster.

NodePort is one way to achieve this.

---

## What is NodePort?

NodePort exposes a Service on a static port of every Worker Node.

```text
User
   |
Node IP:30080
   |
Service
   |
Pods
```

---

## How It Works

Kubernetes opens a port on every node.

Default NodePort range:

```text
30000 - 32767
```

---

## Example

```yaml
apiVersion: v1
kind: Service

metadata:
  name: nginx-service

spec:
  type: NodePort

  selector:
    app: nginx

  ports:
  - port: 80
    targetPort: 80
    nodePort: 30080
```

---

## Access Application

```text
http://NODE-IP:30080
```

Example:

```text
http://192.168.1.100:30080
```

---

## Traffic Flow

```text
User
  |
Node IP:30080
  |
Service
  |
Pods
```

---

## Advantages

- Easy to configure
- Good for testing
- No cloud provider required

---

## Disadvantages

- Requires node IP
- Limited port range
- Not ideal for production

---

## Real-Life Analogy

Imagine a building with multiple entrances.

No matter which entrance you use, security guides you to the correct office.

NodePort works similarly.

---

## Summary

NodePort exposes applications outside the cluster using a port on every Worker Node.

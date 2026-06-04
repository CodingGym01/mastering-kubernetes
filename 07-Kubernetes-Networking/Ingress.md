# Ingress

## Introduction

Managing multiple LoadBalancer Services becomes expensive and difficult.

Ingress provides a smarter way to expose applications.

---

## What is Ingress?

Ingress is a Kubernetes resource that manages external HTTP and HTTPS traffic.

It acts like a reverse proxy.

---

## Problem Without Ingress

```text
Frontend -> LoadBalancer
Backend  -> LoadBalancer
API      -> LoadBalancer
```

Multiple load balancers increase cost.

---

## Solution

```text
Internet
    |
Ingress Controller
    |
--------------------------
|            |           |
Frontend    API      Backend
```

Single entry point.

---

## What is an Ingress Controller?

Ingress resource itself does nothing.

An Ingress Controller implements Ingress rules.

Popular controllers:

- NGINX Ingress Controller
- HAProxy Ingress
- Traefik

---

## Path-Based Routing

Example:

```text
example.com/app
example.com/api
```

Routes:

```text
/app -> Frontend
/api -> Backend
```

---

## Host-Based Routing

Example:

```text
api.example.com
app.example.com
```

Different applications behind same Ingress.

---

## Example

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress

metadata:
  name: app-ingress

spec:
  rules:
  - host: app.example.com

    http:
      paths:
      - path: /
        pathType: Prefix

        backend:
          service:
            name: app-service
            port:
              number: 80
```

---

## Benefits

- Cost Effective
- SSL/TLS Support
- Centralized Routing
- Cleaner Architecture

---

## Real-Life Analogy

Think of a hotel receptionist.

Visitors arrive at one desk.

The receptionist directs them to the correct department.

---

## Summary

Ingress provides centralized HTTP/HTTPS routing and is the preferred way to expose multiple applications in Kubernetes.

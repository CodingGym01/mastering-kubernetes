# DNS in Kubernetes

## Introduction

Kubernetes includes a built-in DNS system that allows applications to discover and communicate with each other using names instead of IP addresses.

---

## Why DNS is Needed?

Pod IPs can change.

Example:

```text
Pod Restart
      |
New IP Assigned
```

Applications cannot reliably use Pod IPs.

---

## Solution

DNS names remain stable.

Applications communicate using Service names.

---

## Example

Service:

```text
backend-service
```

Application connects to:

```text
http://backend-service
```

instead of:

```text
http://10.96.0.20
```

---

## CoreDNS

Kubernetes uses CoreDNS as the default DNS server.

CoreDNS runs inside the cluster.

---

## DNS Flow

```text
Application
     |
DNS Query
     |
CoreDNS
     |
Service IP
```

---

## Fully Qualified Domain Name (FQDN)

Format:

```text
service-name.namespace.svc.cluster.local
```

Example:

```text
backend-service.default.svc.cluster.local
```

---

## Useful Commands

Check DNS Pods:

```bash
kubectl get pods -n kube-system
```

Check Services:

```bash
kubectl get svc
```

---

## Real-Life Analogy

Think of DNS as your phone contacts.

Instead of remembering phone numbers, you remember names.

Similarly, applications use Service names instead of IP addresses.

---

## Summary

DNS in Kubernetes provides service discovery and enables applications to communicate using stable names rather than changing IP addresses.

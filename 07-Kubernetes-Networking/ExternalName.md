# ExternalName Service

## Introduction

Sometimes applications inside Kubernetes need to access external services.

Instead of hardcoding external URLs, Kubernetes provides ExternalName Services.

---

## What is ExternalName?

ExternalName maps a Kubernetes Service to an external DNS name.

---

## Example

External Database:

```text
database.company.com
```

Create Service:

```yaml
apiVersion: v1
kind: Service

metadata:
  name: external-db

spec:
  type: ExternalName
  externalName: database.company.com
```

---

## Traffic Flow

```text
Application
      |
external-db
      |
database.company.com
```

---

## Benefits

- Centralized configuration
- Easier management
- DNS abstraction

---

## Use Cases

- External Databases
- Third-party APIs
- Legacy Systems

---

## Summary

ExternalName provides a DNS alias for external services, making external integrations easier to manage.

# Secret

## Introduction

Applications often require sensitive information.

Examples:

- Passwords
- API Keys
- Tokens
- Certificates

Storing such data directly inside YAML files or source code is a security risk.

---

## What is a Secret?

A Secret is a Kubernetes object used to store sensitive information securely.

---

## Why Not Use ConfigMaps?

ConfigMaps are designed for non-sensitive data.

Secrets are specifically intended for confidential information.

---

## Example Secret

```yaml
apiVersion: v1
kind: Secret

metadata:
  name: db-secret

type: Opaque

data:
  username: YWRtaW4=
  password: cGFzc3dvcmQ=
```

---

## Important Note

Secret values are Base64 encoded.

Example:

```text
admin
```

Encoded:

```text
YWRtaW4=
```

Base64 encoding is NOT encryption.

Additional security controls should be used in production environments.

---

## Using Secret in a Pod

```yaml
env:
- name: DB_PASSWORD

  valueFrom:
    secretKeyRef:
      name: db-secret
      key: password
```

---

## Benefits

- Centralized secret management
- Better security practices
- Reduced exposure of sensitive information
- Integration with external secret managers

---

## ConfigMap vs Secret

| ConfigMap | Secret |
|------------|------------|
| Non-sensitive data | Sensitive data |
| Configuration | Credentials |
| Plain text | Base64 encoded |

---

## Real-Life Analogy

Think of ConfigMap as a public notice board.

Think of Secret as a locked locker.

Both store information, but one requires protection.

---

## Summary

Secrets provide a secure mechanism for storing and managing sensitive application data in Kubernetes.

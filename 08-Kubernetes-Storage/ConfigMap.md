# ConfigMap

## Introduction

Applications often require configuration values.

Examples:

- Database URLs
- Environment Names
- API Endpoints
- Feature Flags

Hardcoding these values inside application code is a bad practice.

---

## What is a ConfigMap?

A ConfigMap stores non-sensitive configuration data in key-value format.

---

## Example

Instead of:

```text
DATABASE_URL=prod-db.company.com
```

inside application code,

store it in a ConfigMap.

---

## ConfigMap Example

```yaml
apiVersion: v1
kind: ConfigMap

metadata:
  name: app-config

data:
  APP_ENV: production
  APP_NAME: nginx-app
```

---

## Using ConfigMap as Environment Variables

```yaml
env:
- name: APP_ENV
  valueFrom:
    configMapKeyRef:
      name: app-config
      key: APP_ENV
```

---

## Benefits

- Centralized configuration
- Easier updates
- Environment-specific configuration
- Better application portability

---

## What Should NOT Be Stored?

Sensitive data such as:

- Passwords
- Tokens
- API Keys

For those, use Secrets.

---

## Real-Life Analogy

Think of ConfigMap as a settings file.

You can change settings without modifying the application itself.

---

## Summary

ConfigMaps store non-sensitive configuration data and help separate configuration from application code.

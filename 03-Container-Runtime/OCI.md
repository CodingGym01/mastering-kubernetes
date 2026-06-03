# Open Container Initiative (OCI)

## Introduction

Before OCI existed, different container technologies followed different standards.

This created compatibility issues.

To solve this problem, industry leaders created the Open Container Initiative (OCI).

---

## What is OCI?

OCI (Open Container Initiative) is an open standard that defines how container images should be built and how containers should run.

It ensures interoperability between different container technologies.

---

## Why Was OCI Created?

Without OCI:

```text
Tool A → Own Image Format
Tool B → Own Image Format
Tool C → Own Runtime Format
```

Containers created by one tool might not work with another.

OCI solved this by defining common standards.

---

## OCI Specifications

OCI mainly defines two standards:

### Image Specification

Defines how container images should be structured.

Examples:

- Layers
- Metadata
- Configuration

---

### Runtime Specification

Defines how containers should be executed.

Examples:

- Process execution
- Namespaces
- Cgroups
- Filesystem behavior

---

## OCI Architecture

```text
Container Image
        |
        v
 OCI Image Spec
        |
        v
 Container Runtime
        |
        v
 OCI Runtime Spec
```

---

## Popular OCI-Compliant Tools

Examples include:

- Docker
- containerd
- CRI-O
- runc
- Podman

---

## Real-Life Analogy

Think of electrical appliances.

Every company follows common standards:

```text
Voltage
Plug Design
Safety Standards
```

Because of these standards, devices work everywhere.

Similarly, OCI provides common standards for containers.

---

## Benefits of OCI

### Standardization

Common industry standards.

### Portability

Containers work across platforms.

### Interoperability

Different tools can work together.

### Vendor Neutrality

No dependency on a specific vendor.

---

## Summary

OCI defines industry standards for container images and container runtimes.

It ensures containers remain portable, compatible, and interoperable across different platforms and tools.

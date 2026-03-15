# UCML Specification
## Unified Collider Modeling Language

UCML (Unified Collider Modeling Language) is a structured language used within Q-Collider to describe particle theories in a compact and machine-readable format.

The goal of UCML is to allow theoretical particle models to be translated directly into collider-relevant representations.

UCML definitions can be parsed into database records representing particles, signatures, and collider predictions.

---

## Design Goals

UCML is designed to satisfy several requirements:

- human readable
- easy to parse programmatically
- compact representation of particle theories
- compatible with collider simulation workflows
- extensible for future model parameters

---

## Core Syntax

A UCML model begins with a model declaration.

Example:

# UCML Extraction Rules
## Formal Specification for Translating Scientific Papers into UCML

## 1. Purpose

This document defines the rules used by Q-Collider to translate uploaded scientific papers into **UCML (Unified Collider Modeling Language)**.

The purpose of these rules is to create a consistent, reviewable, and machine-actionable pathway from:

**paper text → structured theory extraction → draft UCML**

This specification is intended to ensure that paper-to-UCML conversion is:

- systematic
- transparent
- reproducible
- reviewable by researchers

UCML extraction is therefore defined as an **AI-assisted structured interpretation step**, not as an infallible replacement for human scientific judgment.

---

## 2. Scope

The extraction rules apply to uploaded papers in formats such as:

- PDF
- DOCX
- plain text
- LaTeX source

The current extraction scope is limited to collider-relevant theory elements that can be represented in UCML version 1.

These include:

- model name
- framework classification
- particle definitions
- masses
- spins
- charges
- dominant decay channels
- collider signature types

The following may be captured only as notes or optional fields unless explicitly supported:

- coupling constants
- gauge groups
- symmetry-breaking structure
- detailed interaction vertices
- full Lagrangians
- loop corrections
- renormalization prescriptions

---

## 3. Extraction Pipeline

The paper-to-UCML process is divided into five stages.

### Stage 1 — Paper ingestion

The uploaded document is registered and converted into machine-readable text.

### Stage 2 — Scientific structure extraction

The system identifies theory-relevant content and organizes it into a structured intermediate representation.

### Stage 3 — Entity normalization

Names, units, symbols, and channels are normalized into UCML-compatible forms.

### Stage 4 — UCML generation

The structured intermediate representation is converted into draft UCML.

### Stage 5 — Researcher review

The generated UCML is reviewed, edited if needed, and approved before publication into the Theory Lab or Discovery Map.

---

## 4. Intermediate Representation

Before UCML is generated, every paper is translated into an intermediate structured representation.

The extraction engine must populate the following conceptual fields whenever possible:

- `model_name`
- `framework`
- `particles[]`
- `decays[]`
- `signatures[]`
- `notes[]`
- `confidence_score`

### 4.1 Model object

A paper should first produce a model object of the form:

```text
model_name
framework
source_paper_title
source_authors
abstract_summary

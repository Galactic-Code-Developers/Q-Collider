docs/ucml-specification.md
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


MODEL DLSFH_X
FRAMEWORK Valamontes Corpus


This establishes the model identifier and theoretical framework.

---

## Particle Definition

Particles are defined using the PARTICLE keyword.

Example:


PARTICLE X
MASS 450
SPIN 1
CHARGE 0


Typical particle attributes include:

- mass
- spin
- charge
- lifetime
- couplings

Only mass and spin are required in the minimal specification.

---

## Decay Definitions

Decay channels describe how particles transform into observable final states.

Example:


DECAY q qbar


Allowed values include:

- q qbar
- gamma gamma
- e+ e-
- mu+ mu-
- invisible
- custom

Decay channels determine collider signatures and feature encodings.

---

## Signature Definitions

Signatures represent the collider-level experimental observables associated with a theory.

Example:


SIGNATURE dijet


Common signatures include:

- dijet
- diphoton
- dilepton
- missing_energy
- multijet
- custom

Signatures are used to predict detector responses and analysis outcomes.

---

## Example UCML Model


MODEL DarkPhoton_X
FRAMEWORK Benchmark

PARTICLE A'
MASS 20
SPIN 1
CHARGE 0

DECAY e+ e-
SIGNATURE dilepton


This model defines a hypothetical dark photon candidate.

---

## Parsing Behavior

When UCML is parsed inside Q-Collider:

1. a TheoryModels record is created
2. ModelParticles entries are generated
3. ModelSignatures entries are generated
4. optional CorpusModels links are established
5. embeddings are generated for the Discovery Map

This process allows models to move directly into the exploration pipeline.

---

## Versioning

UCML models should support version tracking to ensure reproducibility.

Recommended metadata fields include:

- model version
- author
- creation date
- framework classification

Future versions of UCML may support explicit coupling constants and interaction definitions.

---

## Future Extensions

Planned UCML extensions may include:

interaction definitions  
coupling constants  
gauge group declarations  
symmetry properties  
detector-level observables

The language is intentionally minimal at the current stage to allow rapid theory entry and experimentation.

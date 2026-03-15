# Collider Discovery Map Methodology
## Mapping Particle Theories into Discovery Space

The Collider Discovery Map is the central visualization interface in Q-Collider. It provides a structured representation of theoretical particle models within a multidimensional feature space derived from collider-relevant properties.

The purpose of the map is to allow researchers to compare theoretical models, identify clusters of related predictions, and prioritize promising candidates for further study.

---

## Concept of Discovery Space

In collider physics, theoretical models can often be characterized by a set of observable predictions, including:

- particle masses
- decay channels
- collider signatures
- production cross-sections
- detector-level observables

These properties can be encoded numerically and used to place models within a geometric feature space.

The Discovery Map represents a two-dimensional projection of this higher-dimensional theory space.

---

## Feature Extraction

Each theory model is converted into a feature vector using the **Theory Embedding Engine**.

Typical extracted features include:

particle mass  
particle spin  
particle charge  
dominant decay channel  
collider signature type  
framework classification  
corpus classification  
coupling estimates

These values are encoded numerically for embedding.

---

## Feature Encoding

Example encoding scheme:

Decay channel codes:

| Channel | Code |
|-------|------|
| q qbar | 1 |
| gamma gamma | 2 |
| e+ e- | 3 |
| mu+ mu- | 4 |
| invisible | 5 |
| other | 9 |

Signature codes:

| Signature | Code |
|---------|------|
| dijet | 1 |
| diphoton | 2 |
| dilepton | 3 |
| missing_energy | 4 |
| other | 9 |

Framework codes:

| Framework | Code |
|----------|------|
| Standard Model | 1 |
| Benchmark | 2 |
| Valamontes Corpus | 3 |
| Markoulakis–Valamontes Corpus | 4 |
| Auto Generated | 5 |

Corpus codes:

| Corpus | Code |
|-------|------|
| none | 0 |
| DLSFH | 1 |
| SGCV | 2 |
| Markoulakis–Valamontes | 3 |
| other | 9 |

---

## Coordinate Generation

Embedding coordinates are computed using a simple deterministic rule for initial visualization.

Example coordinate mapping:


x = mass_value
y = (spin_value × 100) + (signature_code × 10) + framework_code
z = corpus_code


This mapping is not intended to represent a final physical embedding. It serves as an interpretable coordinate system for early exploration.

Future versions may incorporate dimensionality reduction techniques such as PCA or UMAP.

---

## Visual Encoding

The Discovery Map uses several visual encodings.

Position  
derived from embedding coordinates.

Point color  
represents discovery probability.

Point size  
represents signal strength.

Point shape  
represents theoretical framework.

These encodings allow researchers to visually identify clusters and promising candidates.

---

## Discovery Probability

Discovery probability is a heuristic score derived from several indicators:

- predicted signal strength
- anomaly score
- resonance score
- missing-energy indicators
- validation metrics

The score is normalized between 0 and 1.

It is intended as a prioritization indicator rather than a statistical discovery claim.

---

## Signal Strength

Signal strength represents the expected relative prominence of the predicted collider signature.

Typical inputs include:

- predicted cross-section
- branching ratios
- analysis significance estimates

Signal strength affects the visual size of the model point on the map.

---

## Validation Score

The validation score measures how well a model agrees with available datasets.

This score may be derived from:

- chi-squared comparisons
- likelihood estimates
- confidence levels

Models with higher validation scores are more consistent with observed data.

---

## Cluster Identification

Clusters of models in the Discovery Map may indicate:

- related theoretical frameworks
- similar collider signatures
- overlapping mass predictions

The platform includes tools for detecting clusters and identifying sparse regions of theory space.

Sparse regions may represent unexplored parameter domains worth investigating.

---

## Scientific Role

The Discovery Map is intended as an exploratory tool rather than a replacement for detailed statistical analysis.

Its primary function is to:

- organize theoretical models
- visualize discovery potential
- guide simulation priorities
- reveal structural patterns in theory space

By presenting theory space in a navigable visual form, the map helps researchers quickly identify promising research directions.

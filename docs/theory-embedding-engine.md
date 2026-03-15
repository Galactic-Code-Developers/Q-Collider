# Theory Embedding Engine
## Mathematical Mapping of Particle Models into Discovery Space

The Theory Embedding Engine is a core component of Q-Collider.  
Its purpose is to convert particle theory models into structured numeric representations that can be analyzed, compared, and visualized within the Collider Discovery Map.

The embedding process transforms theoretical model descriptions into a **feature vector representation** in a structured discovery space.

---

# Motivation

Particle theories are traditionally expressed in symbolic form:

- Lagrangians
- particle multiplets
- coupling constants
- decay channels
- symmetry groups

While these symbolic forms are useful for theoretical derivations, they are difficult to compare across large model sets.

The embedding engine introduces a mapping:


T → Φ(T) ∈ ℝⁿ


where:

- **T** is a theory model
- **Φ(T)** is the numeric feature vector representation

This transformation allows theory models to be placed within a **geometric discovery space** where clustering, ranking, and anomaly detection become possible.

---

# Theory Feature Vector

Each theory model is represented by a vector:


Φ(T) = (m, s, q, d, σ, f, c, g)


where:

| Symbol | Meaning |
|------|--------|
| m | particle mass parameter |
| s | particle spin |
| q | particle charge |
| d | decay channel encoding |
| σ | collider signature encoding |
| f | theoretical framework |
| c | corpus classification |
| g | effective coupling parameter |

These components are extracted automatically from the model registry.

---

# Particle Feature Extraction

For a theory model containing particles:


P = {p₁, p₂, … , pₖ}


each particle contributes parameters:


pᵢ = (mᵢ, sᵢ, qᵢ)


The embedding engine aggregates these values using summary statistics.

Typical aggregation rules:

Mass feature


m = max(mᵢ)


Spin feature


s = mean(sᵢ)


Charge feature


q = mean(|qᵢ|)


These summary values capture the dominant collider scale of the theory.

---

# Decay Channel Encoding

Decay channels are encoded into discrete numeric categories.

Example mapping:

| Decay channel | Code |
|---------------|------|
| q q̄ | 1 |
| γ γ | 2 |
| e⁺ e⁻ | 3 |
| μ⁺ μ⁻ | 4 |
| invisible | 5 |
| other | 9 |

Thus


d ∈ {1,2,3,4,5,9}


This encoding allows decay behavior to influence theory-space geometry.

---

# Collider Signature Encoding

Collider signatures represent experimentally observable event topologies.

Typical encodings include:

| Signature | Code |
|----------|------|
| dijet | 1 |
| diphoton | 2 |
| dilepton | 3 |
| missing energy | 4 |
| multijet | 5 |
| other | 9 |

Thus


σ ∈ {1,2,3,4,5,9}


---

# Framework Encoding

Framework classification identifies the theoretical origin of a model.


f ∈ {1,…,5}


Example mapping:

| Framework | Code |
|----------|------|
| Standard Model | 1 |
| Benchmark | 2 |
| Valamontes Corpus | 3 |
| Markoulakis–Valamontes Corpus | 4 |
| Auto-generated | 5 |

This dimension allows theories to cluster by origin.

---

# Corpus Encoding

Corpus labels identify research families or theoretical lineages.


c ∈ {0,…,9}


Example:

| Corpus | Code |
|------|------|
| none | 0 |
| DLSFH | 1 |
| SGCV | 2 |
| Markoulakis–Valamontes | 3 |
| other | 9 |

This dimension captures conceptual relationships between models.

---

# Coupling Parameter

The parameter


g


represents an effective coupling scale or interaction strength.

If explicit couplings are provided in the model definition, the engine uses them directly.

Otherwise a default value is assigned:


g = 0.5


Future implementations may derive this value from model Lagrangians.

---

# Discovery Space Embedding

The feature vector is mapped into a discovery-space coordinate system.

Let


Φ(T) = (m, s, q, d, σ, f, c, g)


Initial coordinates are defined as:


x = m

y = (100 s) + (10 σ) + f

z = c


This mapping produces an interpretable geometric representation.

Interpretation:

- **x-axis** corresponds to energy scale
- **y-axis** encodes spin and signature structure
- **z-axis** encodes theoretical lineage

The Discovery Map typically displays the projection:


(x, y)


while retaining z for clustering.

---

# Discovery Probability

Each model receives a heuristic discovery probability:


P_d(T)


computed from collider metrics:


P_d = w₁ S + w₂ A + w₃ R + w₄ V


where:

| Term | Meaning |
|------|--------|
| S | signal strength |
| A | anomaly score |
| R | resonance score |
| V | validation score |

and


w₁ + w₂ + w₃ + w₄ = 1


This score is normalized to:


0 ≤ P_d ≤ 1


The score does not represent a statistical discovery claim but a **prioritization heuristic**.

---

# Clustering in Theory Space

Once embedded, models form clusters in discovery space.

Clusters may represent:

- related particle spectra
- similar collider signatures
- shared theoretical frameworks

Clustering algorithms such as:

- k-means
- DBSCAN
- hierarchical clustering

can be applied to detect structure within theory space.

Sparse regions of the embedding may indicate unexplored parameter domains.

---

# Embedding Evolution

The embedding is designed to evolve as new models are introduced.

Updates may include:

- additional features
- improved coupling extraction
- dimensionality reduction techniques
- machine learning embeddings

Future implementations may replace deterministic rules with learned embeddings.

---

# Relationship to Collider Phenomenology

The embedding engine does not replace full theoretical analysis.

Instead it provides a geometric tool for organizing and exploring large theory collections.

By mapping theories into discovery space, the platform allows:

- rapid comparison between models
- visualization of theory families
- identification of promising candidates

This transforms theory exploration into a structured computational workflow.

---

# Summary

The Theory Embedding Engine defines a mathematical transformation:


T → Φ(T) → (x,y,z)


that converts particle theories into coordinates within a discovery space.

This allows Q-Collider to function as a **theory exploration engine** where models can be compared, ranked, and prioritized visually and computationally.

The embedding approach therefore bridges symbolic particle theory and collider-oriented computational analysis.

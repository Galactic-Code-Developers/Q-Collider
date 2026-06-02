# How-To Guide: Theory & Modeling

> Practical step-by-step instructions for all Theory & Modeling modules in Q-Collider.

---

## Table of Contents

1. [How to Create a New Theory Model](#1-how-to-create-a-new-theory-model)
2. [How to Add Particles to a Model](#2-how-to-add-particles-to-a-model)
3. [How to Add Collider Signatures to a Model](#3-how-to-add-collider-signatures-to-a-model)
4. [How to Run a Collision Simulation from Theory Lab](#4-how-to-run-a-collision-simulation-from-theory-lab)
5. [How to Write and Parse UCML Code](#5-how-to-write-and-parse-ucml-code)
6. [How to Search the Corpus Explorer](#6-how-to-search-the-corpus-explorer)
7. [How to Link a Corpus Entry to a Model](#7-how-to-link-a-corpus-entry-to-a-model)
8. [How to Start a Theory Exploration Campaign](#8-how-to-start-a-theory-exploration-campaign)
9. [How to Review Exploration Candidates](#9-how-to-review-exploration-candidates)
10. [How to Design a Parameter Space](#10-how-to-design-a-parameter-space)

---

## 1. How to Create a New Theory Model

**Route:** `/TheoryLab`

1. Navigate to **Theory Lab** from the sidebar.
2. Click the **New Model** button (top-right).
3. Fill in the form:
   - **Model Name** — a unique, descriptive name
   - **Framework** — select from Standard Model, Supersymmetry, Dark Sector, Extra Dimensions, etc.
   - **Model Type** — Custom, Valamontes Corpus, Auto-Generated, etc.
   - **UCML Code** — optional; paste or type your UCML definition
4. Click **Save** — the model appears in the Model List with status `draft`.
5. To edit an existing model, click the **Edit** (pencil) icon on its row.

---

## 2. How to Add Particles to a Model

**Route:** `/TheoryLab` → Model Edit Form

1. Open a model in the **Theory Lab** edit form.
2. Scroll to the **Particles** section.
3. Click **Add Particle**.
4. Fill in:
   - **Particle Name** (e.g. χ₁⁰, Z', H)
   - **Mass (GeV)**
   - **Spin** (0, 0.5, 1, 1.5, 2)
   - **Charge** (electric charge)
   - **Lifetime (s)** — leave blank for stable particles
5. Click **Add** to attach the particle to the model.
6. Repeat for each particle in the model's spectrum.
7. Click **Save Model** to persist changes.

---

## 3. How to Add Collider Signatures to a Model

**Route:** `/TheoryLab` → Model Edit Form

1. Open the model in edit mode.
2. Scroll to the **Signatures** section.
3. Click **Add Signature**.
4. Configure:
   - **Signature Type** — resonance, missing energy, displaced vertex, multi-lepton, dijet, diphoton, mono-jet
   - **Dominant Channel** — e.g. `Z' → l⁺l⁻`
   - **Mass Peak (GeV)** — expected resonance mass
   - **Missing Energy Flag** — toggle if the signature involves invisible particles
   - **Predicted Strength** — estimated signal cross-section multiplier
5. Click **Add** to attach the signature.
6. Save the model.

---

## 4. How to Run a Collision Simulation from Theory Lab

**Route:** `/TheoryLab` → Collision Simulator tab

1. In **Theory Lab**, click the **Simulator** tab at the top.
2. Select the theory model you want to simulate from the dropdown.
3. Adjust the **beam parameters** in the control panel:
   - Beam Energy (TeV)
   - Luminosity
   - Magnetic Field (T)
   - Focus Parameter (β*)
4. Click **Start Simulation** — the 3D particle track rendering begins.
5. Watch live metrics update on the right: luminosity, event rate, signal probability.
6. Adjust parameters in real time to see how they affect signal detection.
7. Click **Reset** to stop and return to default parameters.

---

## 5. How to Write and Parse UCML Code

**Route:** `/UCMLTheoryLab`

1. Navigate to **UCML Theory Lab**.
2. Select an existing model from the dropdown, or start from scratch with the **Empty Template**.
3. The **UCML Editor** opens with syntax highlighting.
4. Write or paste your UCML definition. Example structure:
   ```
   MODEL MyModel
     FRAMEWORK: Supersymmetry
     PARTICLE neutralino MASS=150 SPIN=0.5 CHARGE=0
     SIGNATURE resonance CHANNEL="chi -> gamma gamma" PEAK=150
   END
   ```
5. Click **Parse** to validate the syntax and extract model data.
6. The **Output Panel** shows:
   - Parsed particles list
   - Detected signatures
   - Any syntax errors (with line numbers)
7. Fix any errors highlighted in red.
8. Click **Save to Theory Lab** to persist the model.

---

## 6. How to Search the Corpus Explorer

**Route:** `/CorpusExplorer`

1. Navigate to **Corpus Explorer**.
2. Type a search term in the **search bar** at the top (e.g. author name, paper title, particle name).
3. Results appear in the list below in real time.
4. Use the **Filters** sidebar to narrow by:
   - **Corpus Family** — Valamontes, Markoulakis-Valamontes, Standard Model, etc.
   - **Model Status** — has linked model / no linked model
5. Click any result to open the full **Corpus Entry** panel with:
   - Paper reference / citation
   - Corpus family classification
   - Notes
   - Linked theory models
6. Use the **Export Citation** button to copy the citation in standard format.

---

## 7. How to Link a Corpus Entry to a Model

**Route:** `/CorpusExplorer` → Corpus Entry detail

1. Open a **Corpus Entry** by clicking its row.
2. In the detail panel, click **Link to Model**.
3. A search popup opens — type the model name or ID.
4. Select the model from the results.
5. Confirm the link — the corpus entry now shows the linked model.
6. The model's Theory Lab entry will also show the corpus reference.

**Alternative path:** From the Theory Lab model edit form, scroll to **Corpus Entry** and click **Select Corpus Record**.

---

## 8. How to Start a Theory Exploration Campaign

**Route:** `/GlobalTheoryExploration`

1. Navigate to **Theory Exploration**.
2. Click **New Campaign**.
3. Fill in:
   - **Campaign Name**
   - **Scan Strategy** — Grid, Random, or Bayesian
   - **Parameter Space** — select a saved parameter space from the dropdown
   - **Target Model Count** — how many candidates to evaluate
4. Click **Start Campaign** — the platform dispatches evaluation jobs automatically.
5. The campaign appears in the **Campaign List** with status `running`.
6. Progress updates in real time via the progress bar.

---

## 9. How to Review Exploration Candidates

**Route:** `/GlobalTheoryExploration` → Campaign Detail

1. In the **Campaign List**, click a campaign row to open its detail view.
2. The **Candidate Leaderboard** shows all evaluated candidates ranked by discovery score.
3. Click any candidate row to see:
   - Parameter values
   - Discovery score breakdown
   - Comparison to best known models
4. To trigger a deeper evaluation on a specific candidate, click **Evaluate**.
5. Use the **Annotation Panel** to add notes or flag a candidate for follow-up.
6. Use the **Export** button to download the full candidate list as CSV.

---

## 10. How to Design a Parameter Space

**Route:** `/ParameterSpaceDesigner`

1. Navigate to **Parameter Space Designer**.
2. Click **New Parameter Space**.
3. Give it a **name** (e.g. "SUSY Neutralino Mass Scan").
4. Add parameter **dimensions** one at a time:
   - **Name** — e.g. `mass_GeV`
   - **Min / Max** — numeric bounds
   - **Step** — granularity of the scan
   - **Type** — continuous or discrete
5. The **Coverage Visualisation** panel updates to show the space as a 2D/3D scatter.
6. Click **Save** — the parameter space is now available in the Theory Exploration campaign creator.
7. To reuse an existing space, click **Clone** on any saved configuration.
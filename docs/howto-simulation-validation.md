# How-To Guide: Simulation & Validation

> Practical step-by-step instructions for all Simulation & Validation modules in Q-Collider.

---

## Table of Contents

1. [How to Launch an Emulation Run](#1-how-to-launch-an-emulation-run)
2. [How to Read Emulation Scores](#2-how-to-read-emulation-scores)
3. [How to Validate a Model Against a Dataset](#3-how-to-validate-a-model-against-a-dataset)
4. [How to Interpret Validation Results](#4-how-to-interpret-validation-results)
5. [How to Launch a Full Monte Carlo Pipeline](#5-how-to-launch-a-full-monte-carlo-pipeline)
6. [How to Monitor Pipeline Stage Progress](#6-how-to-monitor-pipeline-stage-progress)
7. [How to Submit a Benchmark Challenge Result](#7-how-to-submit-a-benchmark-challenge-result)
8. [How to Run a Predictive Simulation](#8-how-to-run-a-predictive-simulation)
9. [How to Run a Quantum Decoherence Simulation](#9-how-to-run-a-quantum-decoherence-simulation)
10. [How to Analyse Noise Spectra](#10-how-to-analyse-noise-spectra)
11. [How to Generate a Decoherence Forecast](#11-how-to-generate-a-decoherence-forecast)

---

## 1. How to Launch an Emulation Run

**Route:** `/EmulationDashboard`

1. Navigate to **Emulation Dashboard**.
2. In the **Run Launcher** panel (top-left):
   - Select a **Theory Model** from the first dropdown.
   - Select an **Accelerator Config** from the second dropdown.
3. Click **Run Emulation**.
4. A toast notification confirms the job was queued.
5. The new run appears immediately in the **Run History Table** with status `pending`.
6. Status updates automatically: `pending → running → completed`.

**Tip:** Ensure the theory model has at least one particle and one signature defined, otherwise emulation scores may be zero.

---

## 2. How to Read Emulation Scores

**Route:** `/EmulationDashboard` → Run History Table

After a run completes, click its row to expand the score detail panel:

| Score | Meaning | Good Range |
|---|---|---|
| **Anomaly Score** | Deviation from SM background | > 0.7 signals strong anomaly |
| **Resonance Score** | Likelihood of a resonance peak | > 0.6 for peak structures |
| **Missing Energy Score** | Invisible particle contribution | > 0.5 for DM candidates |
| **Discovery Probability** | Overall discovery likelihood | > 0.8 = high priority |

- The **Anomaly Time Series** chart shows how scores evolved during the run.
- Runs with anomaly score above the threshold are automatically added to **Flagged Candidates**.

---

## 3. How to Validate a Model Against a Dataset

**Route:** `/ValidationDashboard`

1. Navigate to **Validation Dashboard**.
2. Select the **Theory Model** to validate from the model dropdown.
3. Select the **Validation Dataset** from the dataset dropdown.
4. Click **Run Validation**.
5. The job is dispatched; status shows `running` until complete.
6. Results appear in the **Results Panel** when finished.

---

## 4. How to Interpret Validation Results

**Route:** `/ValidationDashboard` → Results Panel

| Metric | Meaning |
|---|---|
| **χ² (chi-squared)** | Goodness-of-fit. Lower = better agreement with data. |
| **Confidence Level** | Statistical confidence (0–1). Values > 0.95 are strong. |
| **Ranking** | Model's rank among all validated models for this dataset. |

- A **low χ²** with **high confidence** means the model is compatible with the reference data.
- A very low χ² (< 0.5) may indicate over-fitting or incorrect background normalisation.
- Click **Compare Rankings** to see how the model stacks up against the full leaderboard.

---

## 5. How to Launch a Full Monte Carlo Pipeline

**Route:** `/SimulationControlRoom`

1. Navigate to **Simulation Control Room**.
2. In the **Pipeline Launcher** panel:
   - Select a **Theory Model**.
   - Optionally select a specific **Accelerator Config** (defaults to the model's linked config).
3. Click **Launch Pipeline**.
4. The pipeline is dispatched through 4 stages:
   - **MadGraph** → generates hard-scatter events (LHE files)
   - **Pythia** → hadronisation and showering (HepMC files)
   - **Delphes** → detector simulation (ROOT files)
   - **Analysis** → physics analysis and result extraction (JSON)
5. Monitor progress in the **Stage Tracker** section below.

---

## 6. How to Monitor Pipeline Stage Progress

**Route:** `/SimulationControlRoom` → Pipeline Run Cards

1. Each pipeline run appears as a **Run Card** in the main list.
2. Click a card to expand its **Stage Progress** detail.
3. Each stage shows one of: `queued | running | completed | failed`.
4. Click a stage badge to view its **file paths** (input card, LHE, HepMC, ROOT, JSON).
5. If a stage fails:
   - The error message appears beneath the stage badge.
   - Click **Retry Stage** to re-queue that specific stage.
   - Click **Abort Pipeline** to stop the run entirely.
6. Completed pipelines show a link to **View Analysis Results**.

---

## 7. How to Submit a Benchmark Challenge Result

**Route:** `/GlobalBenchmarkChallengeProgram`

1. Navigate to **Benchmark Challenges**.
2. Browse open challenges in the **Challenges** tab.
3. Click a challenge to read its description and **task definitions**.
4. Prepare your result file in the required format (JSON, as defined per task).
5. Click **Submit** on the task card.
6. Upload your result file in the upload dialog.
7. The system runs automated scoring — a toast confirms submission.
8. Check the **Leaderboard** tab to see your rank after scoring completes.

**Tip:** Each challenge page includes an **Example Submission** template — download it to ensure your format matches.

---

## 8. How to Run a Predictive Simulation

**Route:** `/PredictiveSimulation`

1. Navigate to **Predictive Simulation**.
2. Click **New Prediction**.
3. Configure:
   - **Theory Model** — the model to forecast
   - **Collider Program** — the experimental program context
   - **Prediction Horizon** — number of future emulation steps to project
4. Click **Run Prediction**.
5. Results appear in the **Results Dashboard** once the job completes:
   - Projected discovery probability curve
   - Significance forecast
   - Signal-to-background ratio trend
6. Use the **Comparison View** to overlay predictions from multiple models.

---

## 9. How to Run a Quantum Decoherence Simulation

**Route:** `/QuantumDecoherenceSimulator`

1. Navigate to **Quantum Decoherence Simulator**.
2. Go to the **Simulation** tab.
3. Configure:
   - **Qubit Count** — number of qubits in the circuit
   - **Circuit Depth** — number of gate layers
   - **Noise Model** — depolarising, thermal, amplitude damping, etc.
   - **Temperature (mK)** — operating temperature of the quantum hardware
4. Click **Run Simulation** — the job is dispatched to the compute grid.
5. Once complete, switch to the **Bloch Sphere** tab to visualise the final qubit states.
6. Switch to **Noise Spectrum** to see the frequency-domain noise profile.
7. Go to **Results** tab to view T1/T2 relaxation times and fidelity metrics.

---

## 10. How to Analyse Noise Spectra

**Route:** `/QuantumDecoherenceSimulator` → Noise Spectrum tab

1. Complete a simulation run (see above).
2. Open the **Noise Spectrum** tab.
3. The chart shows noise power spectral density vs frequency.
4. Key features to look for:
   - **1/f noise** hump at low frequencies → charge noise dominant
   - **Resonance spikes** → coupling to TLS (two-level systems)
   - **White noise floor** → measurement noise baseline
5. Use the **Frequency Range** sliders to zoom into specific bands.
6. Click **Export Data** to download the spectrum as CSV.
7. To test a noise-reduction algorithm against this spectrum, click **Run Algorithm** in the Algorithm Testing panel.

---

## 11. How to Generate a Decoherence Forecast

**Route:** `/DecoherenceForecasting`

1. Navigate to **Decoherence Forecasting**.
2. Select a completed **Simulation Run** from the dropdown as your baseline.
3. Set the **Forecast Horizon**:
   - Number of time steps
   - Time unit (μs, ms, s)
4. Click **Generate Forecast**.
5. The forecast chart renders projected T1 and T2 decay curves.
6. The shaded band shows the 95% confidence interval of the projection.
7. Hover over the chart to read projected T1/T2 values at any future time point.
8. Click **Export CSV** to download the forecast data for external analysis.
# Q-Collider Platform — User Guide

> **Version:** 1.0 · **Platform:** Q-Collider Quantum Research Platform  
> This guide covers every module available in the platform. Use the table of contents to jump to the service you need.

---

## Table of Contents

1. [Getting Started](#1-getting-started)
2. [Discovery & Analysis](#2-discovery--analysis)
   - [Discovery Map](#21-discovery-map)
   - [Collider Discovery Map](#22-collider-discovery-map)
   - [Live Global Collider Map](#23-live-global-collider-map)
   - [Geographic Map](#24-geographic-map)
   - [Analysis Workspace](#25-analysis-workspace)
   - [Detector Event Display](#26-detector-event-display)
3. [Theory & Modeling](#3-theory--modeling)
   - [Theory Lab](#31-theory-lab)
   - [UCML Theory Lab](#32-ucml-theory-lab)
   - [Corpus Explorer](#33-corpus-explorer)
   - [Global Theory Exploration](#34-global-theory-exploration)
   - [Parameter Space Designer](#35-parameter-space-designer)
4. [Simulation & Validation](#4-simulation--validation)
   - [Emulation Dashboard](#41-emulation-dashboard)
   - [Validation Dashboard](#42-validation-dashboard)
   - [Simulation Control Room](#43-simulation-control-room)
   - [Benchmark Challenges](#44-benchmark-challenges)
   - [Predictive Simulation](#45-predictive-simulation)
   - [Quantum Decoherence Simulator](#46-quantum-decoherence-simulator)
   - [Decoherence Forecasting](#47-decoherence-forecasting)
5. [Infrastructure & Computing](#5-infrastructure--computing)
   - [Jetson Cluster Manager](#51-jetson-cluster-manager)
   - [Global Research Grid](#52-global-research-grid)
   - [Embedding Engine](#53-embedding-engine)
   - [Physics Pipeline Control Room](#54-physics-pipeline-control-room)
   - [Autonomous Discovery Engine](#55-autonomous-discovery-engine)
   - [Quantum Optimization Lab](#56-quantum-optimization-lab)
6. [Collaboration & Publishing](#6-collaboration--publishing)
   - [Scientific Publications](#61-scientific-publications)
   - [Scientific Report Builder](#62-scientific-report-builder)
   - [Global Collaboration & Authorship](#63-global-collaboration--authorship)
   - [Physics Knowledge Graph Explorer](#64-physics-knowledge-graph-explorer)
   - [Research Notebook](#65-research-notebook)
   - [Discovery Provenance Tracker](#66-discovery-provenance-tracker)
7. [Site & Campaign Management](#7-site--campaign-management)
   - [Site Onboarding Wizard](#71-site-onboarding-wizard)
   - [Site Trust Dashboard](#72-site-trust-dashboard)
   - [Campaign Management](#73-campaign-management)
   - [Collider Program Comparison](#74-collider-program-comparison)
   - [Correlation Analytics](#75-correlation-analytics)
   - [Statistical Limits](#76-statistical-limits)
8. [Contributions & Recognition](#8-contributions--recognition)
   - [Scientific Contribution Ledger](#81-scientific-contribution-ledger)
   - [Site Contribution Rankings](#82-site-contribution-rankings)
   - [Sponsor & Partnership Dashboard](#83-sponsor--partnership-dashboard)
   - [Global Physics Program Roadmap](#84-global-physics-program-roadmap)
   - [Dataset Browser](#85-dataset-browser)
9. [Settings & Access](#9-settings--access)
   - [Access & Membership](#91-access--membership)
   - [Institutional Dashboard](#92-institutional-dashboard)
10. [Access Control & Roles](#10-access-control--roles)
11. [Glossary](#11-glossary)

---

## 1. Getting Started

### Account Types

| Type | Description |
|---|---|
| **Subscriber** | Full access to Discovery, Analysis, Theory, and Collaboration modules |
| **Sponsor** | All subscriber features + Campaign management and sponsorship tools |
| **Institutional** | Organisation-level access with team management and org analytics |
| **Institutional Sponsor** | Institutional + sponsorship capabilities |
| **Admin** | Full platform access including all admin-gated modules |

### First Login

1. You will be redirected to the **User Dashboard** after authentication.
2. The dashboard shows your **active simulations**, **pending validations**, **contributions**, and **collaborators** at a glance.
3. Use the **sidebar** (left) to navigate between modules, or click any card on the dashboard.
4. The sidebar can be **collapsed** by clicking the arrow button at the top-right of the sidebar panel.

### Navigation

- Modules are grouped into categories in both the sidebar and the dashboard.
- Items marked **Admin** require admin role.
- Items marked **Live** display real-time data.
- Items marked **New** are recently released features.

---

## 2. Discovery & Analysis

### 2.1 Discovery Map

**Route:** `/DiscoveryMap` · **Access:** Admin / Subscriber

The Discovery Map is the central hub for visualising theoretical physics models in a high-dimensional embedding space.

#### Key Features
- **Scatter plot view** — each point represents a theory model, coloured by discovery probability or cluster.
- **Filter panel** — filter by framework, model type, mass range, signature type, and more.
- **Model detail sidebar** — click any point to open a full detail panel including particle properties, emulation results, validation scores, and collider signatures.
- **Cluster live monitor** — view real-time clustering activity across the embedding space.
- **Anomaly signal overlay** — overlay detected anomaly scores directly on the map.
- **Saved views** — save your current filter configuration for later recall.
- **Help modal** — click the (?) icon for an in-app guided tour of the interface.

#### How to Use
1. Navigate to **Discovery Map** from the sidebar or dashboard.
2. Use the **Filters** panel on the left to narrow the visible model set.
3. Click any **dot** on the scatter plot to open the **Model Detail** panel on the right.
4. From the detail panel you can trigger **Emulation**, **Validation**, or **QUBO Optimization** for that model.
5. Switch tabs at the top to access **Live Monitor** or **Anomaly Detection** views.

---

### 2.2 Collider Discovery Map

**Route:** `/ColliderDiscoveryMap` · **Access:** Admin / Subscriber

A 3D interactive canvas for visualising collision topologies, theory space clusters, and decay trees.

#### Key Features
- **Theory Space Canvas** — a 3D rendering of the full model embedding space.
- **Map controls** — zoom, pan, rotate, filter by cluster label or framework.
- **Decay tree panel** — view particle decay trees graphically for any selected model.
- **Model detail sidebar** — collapsible panel with full model stats and action buttons.
- **Map legend** — colour and size encoding explained.

#### How to Use
1. Open the page; the 3D canvas loads automatically with all embedded models.
2. Use **Map Controls** (top-right) to adjust rendering options.
3. Click a node to select a model and open its **Model Detail Sidebar**.
4. Use the **Decay Tree** tab in the sidebar to view the particle decay hierarchy.

---

### 2.3 Live Global Collider Map

**Route:** `/LiveGlobalColliderMap` · **Access:** Admin / Subscriber · **Live**

Real-time feed of global experiment and site activity overlaid on a geographic map.

#### Key Features
- Live event count feeds per site.
- Activity timeline showing recent job completions, site heartbeats, and anomaly triggers.
- Site detail pop-up with current load, node status, and last heartbeat.
- Global summary bar with network-wide aggregates.

#### How to Use
1. The map loads and auto-refreshes every 30 seconds.
2. Click any **site pin** to view a detailed panel for that site.
3. Use the **Filter Panel** to show only sites matching a given status or region.
4. The **Discovery Detail Panel** at the bottom shows recent discovery events from across the network.

---

### 2.4 Geographic Map

**Route:** `/DiscoveryGeographicMap` · **Access:** All users

An interactive geographic map showing all registered research sites and affiliated institutions worldwide.

#### Key Features
- Site location pins colour-coded by status (online / offline / maintenance).
- Hover tooltip showing site name, country, and current node count.
- Filter by organisation type, country, or membership status.

#### How to Use
1. The map loads with all active sites visible.
2. Click a pin to view the site's name, location, and a link to its **Site Detail** page.
3. Use the top filter bar to narrow by region or site status.

---

### 2.5 Analysis Workspace

**Route:** `/AnalysisWorkspace` · **Access:** All users

An integrated scientific data analysis environment for exploring datasets, running custom cuts, and visualising results.

#### Key Features
- **Model & run selector** — choose a theory model and emulation run to load context.
- **Workspace sidebar** — dataset, variable, and event selectors.
- **Main panel** — histogram, scatter plot, and mass spectrum visualisations.
- **Analysis panel** — cut-flow tables, exclusion curves, and significance estimates.
- **Bottom sync row** — syncs the workspace state across all sub-panels.
- **Save & load workspace** — persist your analysis configuration.

#### How to Use
1. Select a **Theory Model** from the top dropdown.
2. Choose an **Emulation Run** to load its associated datasets.
3. Use the **Variable Table** to choose which observables to plot.
4. Apply **expression filters** to select event subsets.
5. View cut-flow results in the **Cut Flow** tab at the bottom.
6. Export results or generate a **Statistical Limit** from the Actions menu.

---

### 2.6 Detector Event Display

**Route:** `/DetectorEventDisplay` · **Access:** All users

A 3D visualisation of individual particle collision events at the detector level.

#### Key Features
- **Detector canvas** — 3D rendering of detector geometry with tracks, hits, and calorimeter deposits.
- **Event filters** — filter by event type, energy range, and particle multiplicity.
- **Mass spectrum panel** — invariant mass distributions from the loaded event sample.
- **Event list** — browse and select individual events from the loaded dataset.
- **Event summary** — per-event kinematics and object counts.
- **Event generator** — generate synthetic events from a chosen model configuration.

#### How to Use
1. Load an **Event Dataset** using the dataset selector at the top.
2. Browse events in the **Event List** panel on the left.
3. Click an event to render its **3D track display**.
4. Use the **Filter** controls to narrow the event sample.
5. Switch to the **Mass Spectrum** tab to view invariant mass distributions.

---

## 3. Theory & Modeling

### 3.1 Theory Lab

**Route:** `/TheoryLab` · **Access:** All users

The primary interface for creating, editing, and testing theoretical physics models using the Q-Collider UCML schema.

#### Key Features
- **Model list** — view all your theory models with status, framework, and type.
- **Model form** — create or edit models with full property control (framework, UCML code, particles, signatures).
- **Collision simulator** — run an interactive 3D simulation using any model's accelerator configuration.
- **Status tracking** — models progress through: `draft → compiled → emulated → validated → archived`.

#### How to Use
1. Click **New Model** to open the creation form.
2. Fill in the model name, select a **framework** (e.g. Standard Model, Supersymmetry, Dark Sector), and optionally enter **UCML code**.
3. Save the model; it appears in the **Model List** with `draft` status.
4. Click **Simulate** to open the **Collision Simulator** for that model.
5. After emulation, the status updates automatically.

---

### 3.2 UCML Theory Lab

**Route:** `/UCMLTheoryLab` · **Access:** All users · **New**

A machine-learning-augmented theory editor for writing, parsing, and analysing Unified Collider Markup Language (UCML) theory files.

#### Key Features
- **UCML Editor** — syntax-highlighted text editor for UCML theory code.
- **Parser engine** — parse UCML to extract model structure, particles, and signatures automatically.
- **ML auto-completion** — AI-assisted suggestions for incomplete UCML blocks.
- **Output panel** — displays parsed model structure and any validation errors.

#### How to Use
1. Select an existing model from the dropdown or start with an empty template.
2. Edit the UCML code in the **Editor** panel.
3. Click **Parse** to validate syntax and extract model data.
4. Review the **Output** panel for parsed particles and signatures.
5. Click **Save to Theory Lab** to persist the model.

---

### 3.3 Corpus Explorer

**Route:** `/CorpusExplorer` · **Access:** All users

A searchable database of the research literature corpus, including papers, model references, and corpus family classifications.

#### Key Features
- Full-text search across paper titles, authors, and abstracts.
- Filter by corpus family (Valamontes Corpus, Markoulakis-Valamontes Corpus, Standard Model, etc.).
- View linked theory models for any corpus entry.
- Citation export and reference linking.

#### How to Use
1. Enter a search term in the search bar at the top.
2. Use the **Filters** sidebar to narrow by corpus family or publication year.
3. Click any result to view the full **Corpus Entry**, including linked models and notes.
4. Use the **Link to Model** button to associate a corpus entry with a theory model.

---

### 3.4 Global Theory Exploration

**Route:** `/GlobalTheoryExploration` · **Access:** All users

A parameter sweep engine for systematic hypothesis generation and multi-dimensional theory space exploration.

#### Key Features
- **Campaign creation** — define scan strategy (grid, random, Bayesian), parameter ranges, and target models.
- **Candidate leaderboard** — ranked list of exploration candidates by discovery score.
- **Job dispatch** — send evaluation jobs to the compute grid.
- **Progress tracking** — live progress bars per campaign.
- **Annotation panel** — add notes and flags to specific candidates.

#### How to Use
1. Click **New Campaign** and fill in the campaign name, scan strategy, and parameter space ID.
2. Click **Start Campaign** to begin dispatching exploration jobs.
3. Monitor progress in the **Campaign List**.
4. Click any campaign to open the **Detail View** with a candidate leaderboard.
5. Use the **Evaluate** button to dispatch further jobs on selected candidates.

---

### 3.5 Parameter Space Designer

**Route:** `/ParameterSpaceDesigner` · **Access:** All users

A visual tool for defining and configuring the parameter spaces used in theory exploration campaigns and emulation runs.

#### Key Features
- Define parameter dimensions (mass ranges, coupling constants, quantum numbers).
- Visualise parameter space coverage as a 2D/3D scatter.
- Save named parameter space configurations.
- Link directly to exploration campaigns or accelerator configs.

#### How to Use
1. Click **New Parameter Space** and give it a name.
2. Add parameter **dimensions** using the form (name, min, max, step, type).
3. Preview the space coverage in the visualisation panel.
4. Click **Save** to persist the configuration for use in campaigns.

---

## 4. Simulation & Validation

### 4.1 Emulation Dashboard

**Route:** `/EmulationDashboard` · **Access:** All users · **Live**

Hardware-in-loop quantum circuit emulation dashboard for running and monitoring emulation jobs against accelerator configurations.

#### Key Features
- **Run launcher** — select a theory model and accelerator config to launch an emulation run.
- **Anomaly time series** — live chart of anomaly scores over time.
- **Flagged candidates** — automatically flagged runs with anomaly scores above threshold.
- **Run history table** — all emulation runs with scores and status.
- **Results panel** — detailed scores: anomaly, resonance, missing energy, discovery probability.

#### How to Use
1. Select a **Theory Model** from the dropdown.
2. Select an **Accelerator Config** to define beam parameters.
3. Click **Run Emulation** — the job is dispatched and appears in the history table.
4. Monitor the **Anomaly Time Series** chart while the run executes.
5. Once complete, click the run to inspect detailed scores.

---

### 4.2 Validation Dashboard

**Route:** `/ValidationDashboard` · **Access:** All users

Validate emulation results against benchmark reference datasets using chi-squared statistics and confidence scoring.

#### Key Features
- Select model and dataset for validation.
- Chi-squared computation with confidence intervals.
- Model ranking against the full validation leaderboard.
- Status tracking per validation run.

#### How to Use
1. Select the **Theory Model** and **Dataset** you want to validate against.
2. Click **Run Validation**.
3. View the **chi-squared** value, **confidence level**, and **ranking** in the results panel.
4. Compare results across models using the **Ranking Table**.

---

### 4.3 Simulation Control Room

**Route:** `/SimulationControlRoom` · **Access:** All users

Orchestrate and monitor full Monte Carlo simulation pipelines (MadGraph → Pythia → Delphes → Analysis).

#### Key Features
- **Pipeline launcher** — select a model and trigger the full 4-stage pipeline.
- **Stage tracker** — visual progress bars per stage (MadGraph, Pythia, Delphes, Analysis).
- **Job status summary** — counts of active, queued, completed, and failed jobs.
- **Job history table** — filterable table of all simulation jobs.
- **Log viewer** — per-job log output for debugging.

#### How to Use
1. Select a **Theory Model** from the model selector.
2. Click **Launch Pipeline** to start the full simulation chain.
3. Watch the **Stage Tracker** update as each stage completes.
4. Click any job in the **History Table** to view its logs and output paths.
5. Failed jobs show an error message; click **Retry** to requeue.

---

### 4.4 Benchmark Challenges

**Route:** `/GlobalBenchmarkChallengeProgram` · **Access:** All users

Community benchmarking program with standardised tasks, leaderboards, and challenge submissions.

#### Key Features
- **Challenge list** — browse open and past challenges by category.
- **Task definitions** — each challenge has one or more tasks with defined inputs and scoring.
- **Submission portal** — upload results and trigger automated scoring.
- **Leaderboard** — ranked table of top performers per challenge.

#### How to Use
1. Browse open challenges from the **Challenges** tab.
2. Click a challenge to view its **Tasks** and scoring criteria.
3. Prepare your result payload (JSON format defined per task).
4. Click **Submit** and upload your results file.
5. Results appear on the **Leaderboard** after automated scoring completes.

---

### 4.5 Predictive Simulation

**Route:** `/PredictiveSimulation` · **Access:** All users

Forward-model predictions for experiment outcomes using ML-based surrogate models trained on historical emulation data.

#### Key Features
- **Prediction config form** — select model, collider program, and prediction horizon.
- **Prediction results dashboard** — discovery probability forecasts, significance estimates, signal/background ratios.
- **Runs list** — history of prediction runs with timestamps and status.

#### How to Use
1. Open **Predictive Simulation** and click **New Prediction**.
2. Select the **Theory Model** and **Collider Program**.
3. Configure the **Prediction Horizon** (number of emulation steps to project forward).
4. Click **Run Prediction** — results appear in the dashboard once the job completes.
5. Compare predictions across models using the **Results Dashboard** comparison view.

---

### 4.6 Quantum Decoherence Simulator

**Route:** `/QuantumDecoherenceSimulator` · **Access:** All users · **New**

Multi-qubit quantum circuit decoherence simulation with 3D detector integration and noise spectrum analysis.

#### Key Features
- **Simulation configurator** — set qubit count, circuit depth, noise model, and temperature.
- **Bloch sphere visualiser** — real-time 3D rendering of qubit state evolution.
- **Detector geometry editor** — configure the detector model used for qubit readout simulation.
- **Noise spectrum chart** — frequency-domain noise profile for the configured system.
- **Algorithm testing** — test noise-reduction algorithms against your simulation.
- **Forecasting tab** — links to the Decoherence Forecasting module.

#### Tabs Overview
| Tab | Purpose |
|---|---|
| Simulation | Configure and launch a new simulation run |
| Detector | Edit detector geometry for readout modelling |
| Bloch Sphere | Visualise qubit state evolution in real time |
| Noise Spectrum | Inspect frequency-domain noise |
| Forecasting | Jump to forward decoherence projections |
| Results | Review completed simulation outputs |

#### How to Use
1. Go to the **Simulation** tab and configure qubit count, noise model, and circuit depth.
2. Click **Run Simulation** — the job is queued and executed on the compute grid.
3. Once complete, switch to **Bloch Sphere** to inspect the final state.
4. Use **Noise Spectrum** to identify dominant noise sources.
5. Run an algorithm from the **Algorithm Testing** panel to compare noise reduction strategies.

---

### 4.7 Decoherence Forecasting

**Route:** `/DecoherenceForecasting` · **Access:** All users

Predictive modelling of qubit decoherence trends over time using time-series forecasting.

#### Key Features
- Select a completed simulation run as the input baseline.
- Configure forecast horizon (steps / time).
- View projected T1/T2 decay curves.
- Download forecast data as CSV.

#### How to Use
1. Select a **Simulation Run** from the dropdown.
2. Set the **Forecast Horizon**.
3. Click **Generate Forecast** — results display as a time-series chart.
4. Click **Export CSV** to download the projected data.

---

## 5. Infrastructure & Computing

### 5.1 Jetson Cluster Manager

**Route:** `/JetsonClusterManager` · **Access:** All users · **Live**

Manage, monitor, and orchestrate the distributed Jetson edge compute cluster.

#### Key Features
- **Cluster overview** — total nodes, active jobs, queue depth, aggregate GPU utilisation.
- **Jetson topology** — visual diagram of nodes and their interconnections.
- **Node cards** — per-node status, hardware specs, current load, and last heartbeat.
- **Job queue table** — all queued and running jobs across the cluster.
- **Metrics monitor** — live time-series charts of GPU, CPU, RAM, and temperature per node.

#### How to Use
1. The **Overview** tab shows the cluster health at a glance.
2. Click any **Node Card** to expand metrics and see assigned jobs.
3. Use the **Job Queue** tab to view, reprioritise, or cancel pending jobs.
4. Use **Metrics Monitor** to watch real-time utilisation charts.
5. Nodes that go offline are highlighted in red; use **Maintenance Mode** to pause them.

---

### 5.2 Global Research Grid

**Route:** `/GlobalResearchGrid` · **Access:** All users

Distributed multi-site compute grid for large-scale physics jobs with geographic load balancing.

#### Key Features
- **Grid summary cards** — total sites, active jobs, total throughput.
- **Site table** — all registered sites with status, region, and job capacity.
- **Site detail panel** — click any site to view its nodes, running jobs, and trust profile.
- **Site edit modal** — update site configuration (admin only).
- **Campaigns panel** — active global campaigns with progress and site participation.

#### How to Use
1. Browse registered sites in the **Site Table**.
2. Click a site row to open the **Site Detail Panel** on the right.
3. Use the **Campaigns Panel** tab to see which sites are participating in active campaigns.
4. Admin users can click **Edit** on any site to modify its configuration.

---

### 5.3 Embedding Engine

**Route:** `/EmbeddingMonitor` · **Access:** All users

Manages vector embedding generation and monitoring for theory models and research documents.

#### Key Features
- Trigger embedding computation for all unembedded models.
- View embedding status per model (pending / complete / error).
- Monitor embedding pipeline health and throughput.
- Inspect per-model feature vectors and cluster assignments.

#### How to Use
1. The page shows a table of all models with their embedding status.
2. Click **Generate Embeddings** to queue all pending models.
3. Monitor progress via the status column — it updates in real time.
4. Click any model row to inspect its **Feature Vector** values.

---

### 5.4 Physics Pipeline Control Room

**Route:** `/PhysicsPipelineControlRoom` · **Access:** All users

Orchestrate multi-stage data processing pipelines with full stage visibility and control.

#### Key Features
- **Pipeline run cards** — each card shows a pipeline's current stage, progress, and status.
- **Stage progress tracker** — visual bar through MadGraph → Pythia → Delphes → Analysis.
- **File path inspector** — view input/output file paths at each stage.
- **Pipeline actions** — advance, retry, or abort individual stages.

#### How to Use
1. View all pipeline runs in the main list.
2. Click a run card to expand **Stage Progress** details.
3. Use the **Action** buttons to advance a stuck stage or trigger a retry.
4. Completed pipelines show a link to their **Analysis Results**.

---

### 5.5 Autonomous Discovery Engine

**Route:** `/AutonomousDiscoveryEngine` · **Access:** All users

Automated signal detection engine that continuously scans datasets for anomalous physics signatures without manual intervention.

#### Key Features
- **Autonomous mode control** — enable/disable autonomous scanning.
- **Discovery cycle log** — log of each scan cycle with models checked and anomalies found.
- **QUBO formulator** — formulate optimisation problems for signal extraction.
- **Jetson annealer** — run GPU-accelerated quantum annealing on the Jetson cluster.
- **Optimisation dashboard** — view QUBO matrix, annealing results, and solution quality.

#### How to Use
1. Enable **Autonomous Mode** with the toggle at the top.
2. The engine runs **Discovery Cycles** automatically at a configured interval.
3. Review the **Cycle Log** for new anomaly detections.
4. For manual optimisation, use the **QUBO Formulator** to define a problem and click **Anneal**.
5. Results appear in the **Optimisation Dashboard**.

---

### 5.6 Quantum Optimization Lab

**Route:** `/QuantumOptimizationLab` · **Access:** All users

Solve combinatorial optimisation problems using QUBO (Quadratic Unconstrained Binary Optimization) and quantum annealing methods.

#### Key Features
- Build custom QUBO matrices from physics problem definitions.
- Dispatch annealing jobs to the Jetson GPU cluster.
- View solution quality metrics (energy, gap, degeneracy).
- Compare classical vs. quantum annealing results.

#### How to Use
1. Define your optimisation problem in the **Problem Setup** panel.
2. Click **Generate QUBO Matrix** — the matrix is computed and displayed.
3. Click **Run Annealing** to dispatch the job to the cluster.
4. Once complete, review the **Solution** and **Energy Landscape** charts.

---

## 6. Collaboration & Publishing

### 6.1 Scientific Publications

**Route:** `/ScientificPublications` · **Access:** All users

Manage the full lifecycle of scientific publications from draft to submission.

#### Key Features
- **Publication list** — all publications with status, authors, and linked models.
- **Publication card** — summary view with abstract, author list, and asset links.
- **Detail panel** — full publication metadata, citation list, and asset downloads.
- **AI generation** — auto-generate a draft publication from emulation and analysis results.
- **Citation manager** — add, edit, and export citations in standard formats.

#### How to Use
1. Click **New Publication** to create a new record.
2. Fill in the title, abstract, and author list.
3. Link relevant **Theory Models** and **Emulation Runs**.
4. Click **Generate Draft** to use AI to populate the manuscript structure.
5. Upload final assets (PDF, data files) via the **Assets** tab.
6. Change status to **submitted** when ready.

---

### 6.2 Scientific Report Builder

**Route:** `/ScientificReportBuilder` · **Access:** All users

Generate formatted scientific reports automatically from your analysis data, figures, and model results.

#### Key Features
- Select data sources (models, runs, analyses, publications).
- Configure report sections (abstract, methods, results, figures, references).
- AI-assisted text generation per section.
- Export to PDF or Markdown.

#### How to Use
1. Click **New Report** and provide a title.
2. Select the **data sources** to include (models, runs, datasets).
3. Choose which **sections** to generate.
4. Click **Generate Report** — the AI drafts each section from the linked data.
5. Edit the output in the text editor, then click **Export PDF**.

---

### 6.3 Global Collaboration & Authorship

**Route:** `/GlobalCollaborationAuthorship` · **Access:** All users

Manage research teams, collaboration invitations, shared workspaces, and authorship proposals.

#### Key Features
- **Collaboration list** — all active and invited collaborations.
- **Member management** — invite members by email, assign roles (view / edit / admin).
- **Campaign linking** — link a collaboration to a specific research campaign.
- **Authorship proposals** — propose and negotiate authorship order for publications.
- **Authorship entries** — finalised author list with affiliations and contribution notes.

#### How to Use
1. Click **New Collaboration** and give it a name and description.
2. Use **Invite Member** to add collaborators by email.
3. Assign each member a **role** (view, edit, or admin).
4. Use the **Authorship** tab to propose a publication author list.
5. Once agreed, click **Finalise Authorship** to lock the order.

---

### 6.4 Physics Knowledge Graph Explorer

**Route:** `/PhysicsKnowledgeGraphExplorer` · **Access:** All users

Interactive graph visualisation of concept nodes, citation links, and model relationships across the research corpus.

#### Key Features
- **Graph canvas** — force-directed graph of knowledge nodes and edges.
- **Node detail** — click any node to view its type, links, and associated publications.
- **Register node** — add a new concept or entity to the knowledge graph.
- **Link nodes** — create semantic edges between any two nodes.
- **Metrics panel** — centrality, degree, and cluster coefficients per node.

#### How to Use
1. The graph loads all registered knowledge nodes automatically.
2. Click any **node** to open its detail panel on the right.
3. Use **Register Node** to add a new concept (theory, experiment, particle, etc.).
4. Use **Link Nodes** to draw a relationship between two existing nodes.
5. Filter the graph by node type using the top filter bar.

---

### 6.5 Research Notebook

**Route:** `/ResearchNotebook` · **Access:** All users

A persistent lab notebook with rich text editing, version history, tagging, and annotation support.

#### Key Features
- **Notebook list** — all your notebooks with last-edited timestamps.
- **Rich text editor** — full markdown / WYSIWYG editor with equation support.
- **Tag filter** — organise and filter notebooks by tags.
- **Version history** — every save creates a version snapshot.
- **Annotations** — attach annotations to specific paragraphs or figures.

#### How to Use
1. Click **New Notebook** and give it a title and tags.
2. Write in the **Editor** — all changes auto-save.
3. Use the **Tag Filter** panel to find notebooks by topic.
4. Click **History** to browse and restore earlier versions.
5. Highlight text and click **Annotate** to attach a note.

---

### 6.6 Discovery Provenance Tracker

**Route:** `/DiscoveryProvenanceTracker` · **Access:** All users

Tracks the full data lineage and result reproducibility chain from raw event data through to published conclusions.

#### Key Features
- **Provenance timeline** — visual chain from dataset → simulation → analysis → result → publication.
- **Node inspection** — click any step to view input parameters, outputs, and timestamps.
- **Reproducibility check** — verify that a result can be recreated from stored inputs.
- **Export provenance** — generate a provenance graph in JSON or DOT format.

#### How to Use
1. Select a **Publication** or **Analysis Result** from the dropdown.
2. The **Provenance Timeline** renders the full chain below.
3. Click any timeline node to inspect its parameters and outputs.
4. Click **Verify Reproducibility** to re-run the chain and compare outputs.
5. Click **Export** to download the provenance graph.

---

## 7. Site & Campaign Management

### 7.1 Site Onboarding Wizard

**Route:** `/SiteOnboardingWizard` · **Access:** Admin

Step-by-step wizard for registering and configuring a new research compute site on the global grid.

#### Steps
| Step | Description |
|---|---|
| 1. Site Info | Organisation name, type, location, website |
| 2. Hardware | Node hardware type, GPU/CPU/RAM specs |
| 3. Network | IP address, public endpoint, scheduler region |
| 4. Policy | Acceptable job types, trust tier, max jobs |
| 5. Validation | Automated connectivity and benchmark checks |
| 6. Confirm | Review and submit for approval |

#### How to Use
1. Navigate to **Onboard Site**.
2. Complete each step of the wizard in order.
3. Step 5 runs automated **Site Validation** — this may take a few minutes.
4. Click **Submit** on the final step to register the site.
5. Site status starts as `pending` and moves to `active` after admin approval.

---

### 7.2 Site Trust Dashboard

**Route:** `/SiteTrustDashboard` · **Access:** Admin

Manage trust levels, certification records, and reliability scores for all registered sites.

#### Key Features
- **Trust overview cards** — summary of sites by trust tier.
- **Trust table** — all sites with their current trust tier, reliability score, and certification status.
- **Certification records panel** — full history of certification runs per site.
- **Node reliability panel** — per-node reliability metrics and trend charts.
- **Run auto-certification** — trigger a certification job for any site.

#### Trust Tiers
| Tier | Description |
|---|---|
| `experimental` | New or untested sites |
| `standard` | Basic validation passed |
| `trusted` | Consistent performance history |
| `certified` | Full certification passed |
| `benchmark` | Reference benchmark site |

#### How to Use
1. Browse the **Trust Table** to see all sites and their current tier.
2. Click a site row to open its **Certification Records**.
3. Click **Run Auto-Certification** to trigger a new certification cycle.
4. Promote or demote a site's trust tier using the **Edit Trust** action.

---

### 7.3 Campaign Management

**Route:** `/CampaignManagement` · **Access:** Sponsor / Institutional / Admin

Create and manage global data collection campaigns with multi-site participation tracking.

#### Key Features
- **Campaign list** — all campaigns segmented by status (active, planned, paused, completed).
- **Progress bars** — visual completion percentage per campaign.
- **Site participation breakdown** — which sites are contributing and their job counts.
- **Campaign creation** — define campaign name, target job count, and participating sites.

#### How to Use
1. Click **New Campaign** and fill in name, description, and target parameters.
2. Assign **Participating Sites** from the registered site list.
3. Click **Schedule Jobs** to distribute jobs across participating sites.
4. Monitor progress in the **Active Campaigns** section.
5. Expand any campaign to view **Site Participation** details.

---

### 7.4 Collider Program Comparison

**Route:** `/ColliderProgramComparison` · **Access:** All users

Side-by-side comparison of multiple collider programs across discovery probability, significance, cross-section, and more.

#### Key Features
- **Program selector** — choose 2–4 programs to compare.
- **Comparison table** — tabular view of key metrics per program.
- **Comparison charts** — bar and radar charts for visual comparison.
- **Recommendation panel** — AI-generated recommendation on best program for a given model.
- **Run buttons** — trigger new emulation runs for any program directly.

#### How to Use
1. Use **Model Selector** to pick the theory model to evaluate.
2. Select the **Programs** to compare from the multi-select dropdown.
3. Click **Run Comparison** — results populate in the table and charts.
4. Read the **Recommendation Panel** for a summary verdict.

---

### 7.5 Correlation Analytics

**Route:** `/CorrelationAnalytics` · **Access:** All users

Find and visualise correlations between variables across multiple datasets and experimental results.

#### Key Features
- Select two or more variables from any dataset.
- Generate a **Correlation Matrix** heatmap.
- Scatter plot view for pairwise correlations.
- Export correlation data as CSV.

#### How to Use
1. Select a **Dataset** from the dropdown.
2. Choose the **variables** to include in the correlation analysis.
3. Click **Compute Correlations** to generate the heatmap.
4. Click any cell in the matrix to open a pairwise scatter plot.

---

### 7.6 Statistical Limits

**Route:** `/StatisticalLimits` · **Access:** All users

Compute exclusion limits and confidence intervals for new physics signals using CLs and frequentist methods.

#### Key Features
- **Limit generator** — configure signal model, background estimate, and observed counts.
- **Exclusion curve plot** — 95% CL exclusion curves in the mass–coupling plane.
- **CLs calculator** — compute CLs values at specified parameter points.
- **Export** — download exclusion data as CSV or JSON.

#### How to Use
1. Select the **Theory Model** and **Dataset** for limit computation.
2. Configure the **Background** and **Observed** counts.
3. Click **Generate Limit** — the exclusion curve renders automatically.
4. Hover over the curve to read out exclusion values at each mass point.
5. Click **Export** to save the results.

---

## 8. Contributions & Recognition

### 8.1 Scientific Contribution Ledger

**Route:** `/ScientificContributionLedger` · **Access:** All users

A full audit log of all scientific contributions made by members across the network.

#### Key Features
- **Ledger table** — all contributions with type, member, timestamp, and points.
- **Type filter** — filter by contribution type (simulation, validation, publication, dataset, etc.).
- **Member filter** — view contributions by a specific user.
- **Export** — download the ledger as CSV.
- **Contribution type icons** — visual icons for quick scanning.

#### How to Use
1. The full ledger loads on page open.
2. Use the **Filters** bar to narrow by member, type, or date range.
3. Click any row to view contribution details.
4. Click **Export CSV** to download the filtered view.

---

### 8.2 Site Contribution Rankings

**Route:** `/SiteContributionRankings` · **Access:** All users

Leaderboard ranking all sites and contributors across the global network by contribution volume and quality.

#### Key Features
- Top-N rankings by total contribution score.
- Breakdown by contribution type (compute, data, publications).
- Time-filtered views (last 7 days, 30 days, all time).
- Refresh button to recompute rankings from the latest ledger data.

#### How to Use
1. Select a **Time Period** from the filter at the top.
2. Browse the **Rankings Table** to see top sites and members.
3. Click any row to see a breakdown of that site's or member's contributions.
4. Click **Refresh Rankings** to trigger a live recomputation.

---

### 8.3 Sponsor & Partnership Dashboard

**Route:** `/SponsorPartnershipDashboard` · **Access:** Sponsor / Institutional / Admin

Central dashboard for sponsor organisations and institutional partners to track their network impact and contribution metrics.

#### Key Features
- **Network stats** — total sites, jobs completed, publications, and active campaigns.
- **Growth charts** — historical trend of network activity.
- **Institutional participation** — which institutions are most active.
- **Sponsor list** — all sponsors with tier, contact info, and contribution score.
- **Recent publications** — latest publications from the network.

#### Access Note
> This page is restricted to users with `sponsor`, `institutional`, `institutional_sponsor`, or `admin` account types. Other users see a membership upgrade prompt.

---

### 8.4 Global Physics Program Roadmap

**Route:** `/GlobalPhysicsProgramRoadmap` · **Access:** All users

View the planned development roadmap for the Q-Collider physics program, including milestones, upcoming features, and program proposals.

#### Key Features
- **Timeline view** — chronological list of milestones.
- **Program proposals** — community-submitted proposals for new collider programs.
- **Proposal voting** — vote on open proposals (requires `can_vote_on_programs` permission).
- **Approved programs** — list of formally approved programs with configuration links.
- **Discussions** — per-proposal comment threads.

#### How to Use
1. Browse the **Timeline** for upcoming milestones.
2. Click any **Program Proposal** to read its details and supporting discussion.
3. If you have voting permission, click **Vote** to cast your vote.
4. Submit a new proposal using the **New Proposal** button.

---

### 8.5 Dataset Browser

**Route:** `/DatasetBrowser` · **Access:** All users

Browse, filter, and download community-contributed physics event datasets.

#### Key Features
- **Dataset list** — all datasets with type, event count, collision energy, and stage.
- **Filter** — filter by dataset type (signal, background, benchmark, validation), energy, and stage.
- **Dataset detail** — click any dataset for full metadata (process code, cross-section, description).
- **Download link** — direct link to the storage path.
- **Variable browser** — list all variables available in the dataset.

#### How to Use
1. Browse the dataset list, using filters to narrow by type or energy.
2. Click any dataset row to open the **Detail Panel**.
3. Click **Browse Variables** to see all available columns.
4. Click **Download** to retrieve the dataset file from storage.

---

## 9. Settings & Access

### 9.1 Access & Membership

**Route:** `/AccessAndMembership` · **Access:** Admin (full management); All users (self-service view)

Control and manage user roles, account types, and membership tier upgrades.

#### Key Features
- **My Membership** — view your current account type, status, and permissions.
- **Membership tiers** — feature comparison across all account types.
- **Upgrade path** — request an upgrade to Sponsor or Institutional tier.
- **Permission flags** — see exactly which capabilities your account includes.
- **Admin panel** — list and edit all user access profiles (admin only).

#### Upgrade Process
1. Click **Upgrade** on the desired membership tier card.
2. A confirmation dialog summarises the new permissions.
3. Confirm to submit the upgrade request.
4. An admin approves the request and your status changes to `active` for the new tier.

---

### 9.2 Institutional Dashboard

**Route:** `/InstitutionalDashboard` · **Access:** Admin / Institutional

Organisation-level analytics, member management, and billing overview for institutional accounts.

#### Key Features
- **Org overview** — member count, active sites, job volume, and publication count.
- **Member list** — all users associated with this institution.
- **Site portfolio** — all sites registered under the institution.
- **Contribution metrics** — org-level contribution score and ledger summary.
- **Billing & usage** — compute credits used and remaining (if applicable).

#### How to Use
1. On first visit, ensure your **Organisation** record exists (or create one via the admin panel).
2. View org-level stats on the **Overview** cards.
3. Use the **Members** tab to manage who belongs to your institutional account.
4. Use the **Sites** tab to see all sites associated with your organisation.

---

## 10. Access Control & Roles

### User Roles

| Role | Description |
|---|---|
| `user` | Standard authenticated user |
| `admin` | Full platform access, including all admin-gated modules |

### Account Types (Access Profiles)

| Account Type | Can Manage Team | Can Manage Site | Can Vote | Can Submit Publications | Can Sponsor Campaigns |
|---|---|---|---|---|---|
| subscriber | ✗ | ✗ | ✗ | ✓ | ✗ |
| sponsor | ✗ | ✗ | ✓ | ✓ | ✓ |
| institutional | ✓ | ✓ | ✓ | ✓ | ✗ |
| institutional_sponsor | ✓ | ✓ | ✓ | ✓ | ✓ |
| admin | ✓ | ✓ | ✓ | ✓ | ✓ |

### Module Access Summary

| Module | Min Access |
|---|---|
| Discovery Map | Admin or Subscriber |
| Collider Map | Admin or Subscriber |
| Live Global Map | Admin or Subscriber |
| All other analysis/theory/simulation modules | Any authenticated user |
| Site Onboarding Wizard | Admin |
| Site Trust Dashboard | Admin |
| Access & Membership | Any user (admin for full management) |
| Institutional Dashboard | Admin or Institutional |
| Campaign Management | Sponsor / Institutional / Admin |
| Sponsor & Partnership Dashboard | Sponsor / Institutional / Admin |

---

## 11. Glossary

| Term | Definition |
|---|---|
| **UCML** | Unified Collider Markup Language — the platform's DSL for defining theory models |
| **Emulation Run** | A hardware-in-loop execution of a theory model against an accelerator configuration |
| **Discovery Probability** | ML-estimated probability that a given model is discoverable at a collider |
| **Anomaly Score** | Statistical measure of deviation from background expectations |
| **QUBO** | Quadratic Unconstrained Binary Optimization — a formulation for quantum annealing |
| **Embedding** | A vector representation of a model in a high-dimensional feature space |
| **Cluster** | A group of models with similar embedding coordinates |
| **Significance** | Statistical significance of a signal above background (in units of σ) |
| **CLs** | Modified frequentist confidence level statistic used for exclusion limits |
| **Pipeline** | The 4-stage simulation chain: MadGraph → Pythia → Delphes → Analysis |
| **Trust Tier** | Certification level of a compute site (experimental → benchmark) |
| **Corpus** | The curated collection of physics research papers and model references |
| **Provenance** | The full traceable chain of data transformations from raw input to result |
| **Feature Vector** | The numeric representation of a model used for embedding and ML scoring |
| **T1 / T2** | Qubit relaxation time (T1) and dephasing time (T2) in quantum systems |

---

*Q-Collider User Guide — maintained by the SDQC Lab team. For technical issues, consult `docs/DEVELOPER.md`.*
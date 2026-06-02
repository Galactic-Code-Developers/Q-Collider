# How-To Guide: Infrastructure & Computing

> Practical step-by-step instructions for all Infrastructure & Computing modules in Q-Collider.

---

## Table of Contents

1. [How to View Jetson Cluster Health](#1-how-to-view-jetson-cluster-health)
2. [How to Manage the Job Queue](#2-how-to-manage-the-job-queue)
3. [How to Put a Node into Maintenance Mode](#3-how-to-put-a-node-into-maintenance-mode)
4. [How to Browse the Global Research Grid](#4-how-to-browse-the-global-research-grid)
5. [How to View a Specific Site's Detail](#5-how-to-view-a-specific-sites-detail)
6. [How to Generate Embeddings for Unembedded Models](#6-how-to-generate-embeddings-for-unembedded-models)
7. [How to Inspect a Model's Feature Vector](#7-how-to-inspect-a-models-feature-vector)
8. [How to Manage a Physics Pipeline](#8-how-to-manage-a-physics-pipeline)
9. [How to Enable Autonomous Discovery Mode](#9-how-to-enable-autonomous-discovery-mode)
10. [How to Run a QUBO Optimisation](#10-how-to-run-a-qubo-optimisation)

---

## 1. How to View Jetson Cluster Health

**Route:** `/JetsonClusterManager`

1. Navigate to **Jetson Cluster Manager**.
2. The **Cluster Overview** panel at the top shows:
   - Total nodes registered
   - Nodes currently online / busy / offline
   - Aggregate GPU utilisation %
   - Total jobs running and queued
3. Below the overview, **Node Cards** display each node individually.
4. Each card shows: hardware type, IP address, current load, GPU %, and status badge.
5. Click any node card to expand its **live metrics** (CPU, GPU, RAM, temperature).
6. The **Metrics Monitor** tab shows time-series charts for the last hour.

**Status colours:**
- 🟢 Green = online and idle
- 🟡 Amber = busy (jobs running)
- 🔴 Red = offline or error
- ⚪ Grey = maintenance

---

## 2. How to Manage the Job Queue

**Route:** `/JetsonClusterManager` → Job Queue tab

1. Click the **Job Queue** tab.
2. The table lists all queued and running jobs across the cluster.
3. Each row shows: job ID, type, model, assigned node, priority, and status.
4. To **reprioritise** a job:
   - Click the job row.
   - Use the **Priority** spinner to change from 1 (highest) to 10 (lowest).
   - Click **Update**.
5. To **cancel** a queued job, click the **✕** button on the job row.
6. To **reassign** a job to a different node, click **Reassign** and select the target node.

---

## 3. How to Put a Node into Maintenance Mode

**Route:** `/JetsonClusterManager` → Node Cards

1. Locate the node in the **Node Cards** list.
2. Click the node card to expand its detail view.
3. Click the **Set Maintenance** button.
4. Confirm the dialog — the node status changes to `maintenance`.
5. Running jobs on that node are **not cancelled** but no new jobs are assigned.
6. Once maintenance is complete, click **Set Online** to return the node to active status.

**Note:** Only admin users and users with `can_manage_site` permission can change node status.

---

## 4. How to Browse the Global Research Grid

**Route:** `/GlobalResearchGrid`

1. Navigate to **Global Research Grid**.
2. The **Grid Summary Cards** at the top show total sites, active jobs, and throughput.
3. The **Site Table** lists all registered sites with:
   - Name and organisation
   - Country and region
   - Status (online / offline / maintenance)
   - Node count and active job count
4. Click a column header to **sort** by that field.
5. Use the **search bar** above the table to filter by site name.
6. Use the **Status Filter** dropdown to show only sites in a specific state.

---

## 5. How to View a Specific Site's Detail

**Route:** `/GlobalResearchGrid` → Site Detail Panel

1. Click any row in the **Site Table**.
2. The **Site Detail Panel** opens on the right:
   - Site metadata (org, type, country, website)
   - Active nodes with their current load
   - Running and queued jobs at this site
   - Trust tier and certification status
3. Click **View Full Site Page** to navigate to the dedicated `/SiteDetail/:siteId` page.
4. From the full site page, you can also view the site's **contribution history** and **validation records**.

---

## 6. How to Generate Embeddings for Unembedded Models

**Route:** `/EmbeddingMonitor`

1. Navigate to **Embedding Engine**.
2. The table shows all theory models with a **Status** column:
   - `complete` — embedding exists
   - `pending` — no embedding yet
   - `error` — previous attempt failed
3. Click **Generate Embeddings** (top-right) to queue all `pending` models.
4. A progress bar appears while jobs are dispatched.
5. Status updates in real time as embeddings complete.
6. To regenerate a specific model's embedding, click its row and select **Re-generate**.

**Note:** Embedding generation requires at least one particle and one signature on the model.

---

## 7. How to Inspect a Model's Feature Vector

**Route:** `/EmbeddingMonitor` → Model Row

1. In the **Embedding Engine**, click any model with `complete` status.
2. The **Feature Vector** panel opens on the right, showing:
   - Mass, spin, charge, decay code
   - Signature code, framework code, corpus code
   - Embedding coordinates (x, y, z)
   - Discovery score and cluster ID
3. These values feed directly into the **Discovery Map** scatter plot coordinates.
4. Click **View on Discovery Map** to jump to that model's position on the map.

---

## 8. How to Manage a Physics Pipeline

**Route:** `/PhysicsPipelineControlRoom`

1. Navigate to **Pipeline Control Room**.
2. All pipeline runs are listed as expandable **Run Cards**.
3. Click a card to see the 4-stage progress tracker.
4. Use the **Action** buttons per stage:
   - **Advance Stage** — manually advance to the next stage (if the current is complete)
   - **Retry** — re-queue a failed stage
   - **Abort** — cancel the entire pipeline
5. Click the **File Paths** icon on any completed stage to view its input and output paths.
6. When all 4 stages complete, the pipeline shows a link to the **Analysis Results** JSON.

---

## 9. How to Enable Autonomous Discovery Mode

**Route:** `/AutonomousDiscoveryEngine`

1. Navigate to **Autonomous Discovery Engine**.
2. At the top of the page, find the **Autonomous Mode** toggle.
3. Toggle it **ON** — a confirmation dialog appears.
4. Confirm to start autonomous scanning.
5. The engine will:
   - Run a **Discovery Cycle** at the configured interval
   - Check all active datasets for anomalous signals
   - Flag candidates above the anomaly threshold
6. Monitor cycles in the **Cycle Log** table, which updates after each run.
7. Toggle **OFF** at any time to pause autonomous scanning.

**Note:** Autonomous mode requires at least one online compute node and one active dataset.

---

## 10. How to Run a QUBO Optimisation

**Route:** `/AutonomousDiscoveryEngine` → QUBO Panel  
or `/QuantumOptimizationLab`

1. Navigate to **Quantum Optimization Lab** (or the QUBO panel in the Discovery Engine).
2. Define your optimisation problem:
   - **Problem Type** — signal extraction, model selection, parameter optimisation
   - **Model** — theory model to optimise
   - **Config** — accelerator config to use as context
3. Click **Generate QUBO Matrix** — the matrix is computed and displayed as a heatmap.
4. Review the matrix for non-zero off-diagonal coupling terms.
5. Click **Run Annealing** to dispatch the job to the Jetson GPU cluster.
6. Monitor status in the job queue (job type = `qubo`).
7. Once complete, view:
   - **Solution vector** — binary assignment for each variable
   - **Energy** — objective function value (lower = better)
   - **Gap** — energy gap to next-best solution
8. Compare results with **Classical Solver** using the toggle at the top.
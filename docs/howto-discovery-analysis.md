# How-To Guide: Discovery & Analysis

> Practical step-by-step instructions for all Discovery & Analysis modules in Q-Collider.

---

## Table of Contents

1. [How to Explore Models on the Discovery Map](#1-how-to-explore-models-on-the-discovery-map)
2. [How to Filter the Discovery Map](#2-how-to-filter-the-discovery-map)
3. [How to Trigger Emulation from the Discovery Map](#3-how-to-trigger-emulation-from-the-discovery-map)
4. [How to Use the Collider Discovery Map (3D)](#4-how-to-use-the-collider-discovery-map-3d)
5. [How to Monitor Live Global Experiment Activity](#5-how-to-monitor-live-global-experiment-activity)
6. [How to Find a Site on the Geographic Map](#6-how-to-find-a-site-on-the-geographic-map)
7. [How to Run a Custom Analysis in the Analysis Workspace](#7-how-to-run-a-custom-analysis-in-the-analysis-workspace)
8. [How to Apply Cut-Flow Filters](#8-how-to-apply-cut-flow-filters)
9. [How to View a 3D Collision Event](#9-how-to-view-a-3d-collision-event)
10. [How to Generate Synthetic Events](#10-how-to-generate-synthetic-events)

---

## 1. How to Explore Models on the Discovery Map

**Route:** `/DiscoveryMap`

1. Navigate to **Discovery Map** from the sidebar.
2. The scatter plot loads all embedded theory models. Each dot represents one model.
3. **Colour** encodes discovery probability (blue = low, red = high by default).
4. **Size** encodes signal strength.
5. Hover over any dot to see the model name and key scores in a tooltip.
6. Click a dot to open the **Model Detail Sidebar** on the right.
7. Use the sidebar to inspect particles, signatures, emulation results, and run actions.

**Tips:**
- Use the **Reset View** button if the plot becomes cluttered.
- Switch to the **Cluster View** tab to colour by cluster label instead of score.

---

## 2. How to Filter the Discovery Map

**Route:** `/DiscoveryMap` → Filters panel (left)

1. Open the **Filters** panel on the left side of the Discovery Map.
2. Set any combination of the following:
   - **Framework** — e.g. Supersymmetry, Dark Sector, Standard Model
   - **Model Type** — Custom, Valamontes Corpus, Auto-Generated, etc.
   - **Mass Range** — drag the slider to set min/max GeV
   - **Discovery Probability** — minimum threshold (0–100%)
   - **Signature Type** — resonance, missing energy, displaced vertex, etc.
3. The scatter plot updates instantly as you change filters.
4. To save a filter configuration, click **Save View** and give it a name.
5. Recall saved views from the **Saved Views** dropdown.

---

## 3. How to Trigger Emulation from the Discovery Map

**Route:** `/DiscoveryMap` → Model Detail Sidebar

1. Click any model dot on the scatter plot to open its detail sidebar.
2. Scroll to the **Actions** section at the bottom of the sidebar.
3. Click **Run Emulator** — this dispatches a new emulation run for the selected model.
4. A toast notification confirms the job was queued.
5. Navigate to `/EmulationDashboard` to monitor progress.
6. You can also click **Run Validation** or **QUBO Optimization** from the same panel.

---

## 4. How to Use the Collider Discovery Map (3D)

**Route:** `/ColliderDiscoveryMap`

1. The 3D Theory Space Canvas loads automatically.
2. **Rotate** — click and drag on the canvas.
3. **Zoom** — scroll wheel or pinch gesture.
4. **Pan** — right-click drag.
5. Use **Map Controls** (top-right) to:
   - Toggle cluster colouring
   - Filter by framework
   - Adjust node size scaling
6. Click any node to select a model and open the **Model Detail Sidebar**.
7. In the sidebar, open the **Decay Tree** tab to visualise the particle decay hierarchy.
8. Use the **Collapse** button on the sidebar to free up canvas space.

---

## 5. How to Monitor Live Global Experiment Activity

**Route:** `/LiveGlobalColliderMap`

1. The map auto-loads all registered sites with live status pins.
2. **Green pins** = online, **amber** = busy, **grey** = offline, **red** = maintenance.
3. The map refreshes every 30 seconds automatically.
4. Click any site pin to open a **Site Detail Panel** showing:
   - Current node count and load
   - Jobs running / queued
   - Last heartbeat timestamp
5. Use the **Filter Panel** (top) to show only sites in a specific region or status.
6. The **Activity Feed** panel (bottom-right) shows the last 20 network events in real time.
7. The **Global Summary Bar** at the top shows total jobs running across all sites.

---

## 6. How to Find a Site on the Geographic Map

**Route:** `/DiscoveryGeographicMap`

1. Navigate to **Geographic Map**.
2. All registered sites appear as map pins.
3. Use the **Filter Bar** at the top to search by:
   - Country or city name
   - Organisation type (university, national lab, etc.)
   - Membership status (active, pending, inactive)
4. Click any pin to open a tooltip with the site name and a link to its **Site Detail** page.
5. Zoom into a region by scrolling, or use the **+/−** zoom controls.

---

## 7. How to Run a Custom Analysis in the Analysis Workspace

**Route:** `/AnalysisWorkspace`

1. Navigate to **Analysis Workspace**.
2. Select a **Theory Model** from the top-left dropdown.
3. Select an **Emulation Run** from the run dropdown — this loads the associated datasets.
4. In the **Workspace Sidebar**, choose the dataset you want to analyse.
5. In the **Variable Table**, tick the variables you want to include.
6. Choose a **Plot Type** (histogram, scatter, mass spectrum) from the main panel.
7. Click **Generate Plot** — the visualisation appears in the main panel.
8. To save the workspace state, click **Save Workspace**.

---

## 8. How to Apply Cut-Flow Filters

**Route:** `/AnalysisWorkspace` → Cut Flow tab

1. With a dataset loaded in the Analysis Workspace, scroll to the **bottom panel**.
2. Click the **Cut Flow** tab.
3. Click **Add Cut** and define your expression (e.g. `pt > 30`, `eta < 2.5`).
4. Each cut appears as a step in the cut-flow table with event count and efficiency.
5. Click **Run Cut Flow** to execute all cuts in sequence.
6. View the **Cut Flow Visualisation** chart showing events remaining after each step.
7. Export the results using **Export CSV** at the top of the table.

---

## 9. How to View a 3D Collision Event

**Route:** `/DetectorEventDisplay`

1. Navigate to **Detector Event Display**.
2. Select an **Event Dataset** from the top dropdown.
3. The **Event List** on the left loads individual events from the dataset.
4. Click any event in the list to render it in the **3D Detector Canvas**.
5. In the canvas:
   - **Rotate** — click and drag
   - **Zoom** — scroll wheel
   - **Toggle layers** — use the checkboxes (tracks, calorimeter, muon system)
6. The **Event Summary** panel (right) shows per-event kinematics and object counts.
7. Use **Filter Events** at the top to narrow the event list by energy or particle type.

---

## 10. How to Generate Synthetic Events

**Route:** `/DetectorEventDisplay` → Event Generator

1. Open the **Detector Event Display**.
2. Click the **Generate Events** button in the toolbar.
3. Select the **Theory Model** and **Accelerator Config** to use.
4. Set the **number of events** to generate.
5. Click **Generate** — the job is dispatched and events appear in the Event List when complete.
6. Generated events are saved as a new **Event Dataset** accessible in the Dataset Browser.
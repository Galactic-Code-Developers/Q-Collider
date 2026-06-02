# How-To Guide: Site & Campaign Management

> Practical step-by-step instructions for all Site & Campaign Management modules in Q-Collider.

---

## Table of Contents

1. [How to Onboard a New Research Site](#1-how-to-onboard-a-new-research-site)
2. [How to Complete Site Validation During Onboarding](#2-how-to-complete-site-validation-during-onboarding)
3. [How to Manage Site Trust Tiers](#3-how-to-manage-site-trust-tiers)
4. [How to Run Site Auto-Certification](#4-how-to-run-site-auto-certification)
5. [How to Create a Campaign](#5-how-to-create-a-campaign)
6. [How to Schedule Campaign Jobs Across Sites](#6-how-to-schedule-campaign-jobs-across-sites)
7. [How to Monitor Campaign Progress](#7-how-to-monitor-campaign-progress)
8. [How to Compare Collider Programs](#8-how-to-compare-collider-programs)
9. [How to Run Correlation Analytics](#9-how-to-run-correlation-analytics)
10. [How to Compute Statistical Limits](#10-how-to-compute-statistical-limits)

---

## 1. How to Onboard a New Research Site

**Route:** `/SiteOnboardingWizard` · **Requires:** Admin

The onboarding wizard walks you through 6 steps. All steps must be completed in order.

### Step 1 — Site Information
1. Navigate to **Onboard Site**.
2. Enter:
   - Organisation name
   - Organisation type (university, national lab, industry, etc.)
   - Country and city
   - Website URL
3. Click **Next**.

### Step 2 — Hardware Specification
1. Select the **Hardware Type** (e.g. Jetson AGX Orin, workstation, cloud VM).
2. Enter:
   - GPU memory (GB)
   - CPU core count
   - RAM (GB)
   - Max parallel jobs
3. Click **Next**.

### Step 3 — Network Configuration
1. Enter the node's **IP address**.
2. Enter the **Public Endpoint** URL or hostname (used for job dispatch).
3. Select a **Scheduler Region** (EU, US, APAC, Global).
4. Select the **Node Role** (worker, scheduler, analysis, simulation, hybrid).
5. Click **Next**.

### Step 4 — Site Policy
1. Select acceptable **Job Types** (emulator, qubo, validation, theory_scan).
2. Set the **Trust Tier** to start with (recommend `experimental` for new sites).
3. Set the **Routing Mode** (local, regional, global).
4. Click **Next**.

### Step 5 — Validation (Automated)
1. The platform runs automated connectivity and benchmark checks.
2. This may take 1–5 minutes.
3. All checks must pass (green) before you can proceed.
4. If a check fails, fix the issue indicated and click **Re-run Checks**.

### Step 6 — Confirm & Submit
1. Review all entered information.
2. Click **Submit** to register the site.
3. Site status is set to `pending` — an admin approves it to make it `active`.

---

## 2. How to Complete Site Validation During Onboarding

**Route:** `/SiteOnboardingWizard` → Step 5

The automated validation runs the following checks:

| Check | What it Tests |
|---|---|
| Connectivity | Can the platform reach the node's public endpoint? |
| Heartbeat | Does the node respond to a heartbeat ping? |
| Hardware Spec | Are the reported specs within acceptable bounds? |
| Benchmark | Can the node complete a benchmark job within time limits? |
| Policy | Are the configured job types compatible with site policy? |

**If a check fails:**
1. Read the error message next to the failed check.
2. Common fixes:
   - **Connectivity fail** — check firewall rules; ensure port 443 or the configured port is open.
   - **Heartbeat fail** — ensure the node agent is running (`./q-collider-agent start`).
   - **Benchmark fail** — node may be overloaded; free up resources and retry.
3. Click **Re-run Checks** after fixing each issue.

---

## 3. How to Manage Site Trust Tiers

**Route:** `/SiteTrustDashboard` · **Requires:** Admin

1. Navigate to **Site Trust Dashboard**.
2. The **Trust Table** lists all sites with their current tier.
3. To change a site's trust tier:
   - Click the site row to open its detail.
   - Click **Edit Trust**.
   - Select the new tier from the dropdown.
   - Add an optional **reason note**.
   - Click **Save**.
4. Trust tier changes are logged in the **Certification Records** panel.

**Trust Tier Requirements:**

| Tier | Requirements |
|---|---|
| `experimental` | Newly registered, no history required |
| `standard` | Passed basic connectivity and benchmark checks |
| `trusted` | ≥ 30 days consistent uptime, < 5% job failure rate |
| `certified` | Passed full auto-certification suite |
| `benchmark` | Used as reference site for benchmark calibration |

---

## 4. How to Run Site Auto-Certification

**Route:** `/SiteTrustDashboard`

1. Open the **Site Trust Dashboard**.
2. Click the site you want to certify.
3. Click **Run Auto-Certification**.
4. A job is dispatched to run the full certification suite:
   - Connectivity test
   - Benchmark performance test
   - Reliability history check
   - Node reliability metrics review
5. Results appear in the **Certification Records Panel** when complete.
6. If all checks pass, the site is eligible for promotion to `certified` tier.
7. Click **Promote Trust Tier** to finalise the upgrade.

---

## 5. How to Create a Campaign

**Route:** `/CampaignManagement` · **Requires:** Sponsor / Institutional / Admin

1. Navigate to **Campaign Management**.
2. Click **New Campaign**.
3. Fill in:
   - **Campaign Name**
   - **Description** — goals and expected output
   - **Target Job Count** — total jobs to distribute
   - **Job Type** — emulator, qubo, validation, or theory_scan
   - **Start Date** and **End Date** (optional)
4. Select **Participating Sites** from the registered site list.
5. Click **Create Campaign** — status starts as `planned`.
6. To activate the campaign, click **Activate** on the campaign card.

---

## 6. How to Schedule Campaign Jobs Across Sites

**Route:** `/CampaignManagement` → Campaign Detail

1. Open an active campaign from the campaign list.
2. Click **Schedule Jobs**.
3. The platform distributes jobs across participating sites proportionally by capacity.
4. Review the **Site Allocation Preview** — it shows how many jobs each site will receive.
5. Adjust allocations manually if needed (click any site row and edit the count).
6. Click **Confirm and Dispatch** — jobs are queued on each site.
7. Monitor progress using the **Site Participation Breakdown** section below.

---

## 7. How to Monitor Campaign Progress

**Route:** `/CampaignManagement`

1. Active campaigns display a **Progress Bar** showing completed / total jobs.
2. Click an active campaign to expand **Site Participation**:
   - Each participating site shows its completed, active, and queued job counts.
3. The **Overall Status** badge updates automatically:
   - `planned` → `running` → `completed` (or `partial` if some sites fail)
4. To **pause** a campaign, click **Pause** — no new jobs are dispatched but running jobs finish.
5. To **resume**, click **Activate** again.
6. Completed campaigns are moved to the **Completed** tab.

---

## 8. How to Compare Collider Programs

**Route:** `/ColliderProgramComparison`

1. Navigate to **Program Comparison**.
2. Select a **Theory Model** from the model dropdown at the top.
3. Select **2 to 4 programs** to compare from the multi-select.
4. Click **Run Comparison** — new emulation runs are dispatched for each selected program.
5. Once results arrive, the **Comparison Table** populates:
   - Discovery probability per program
   - Expected cross-section (pb)
   - Signal event count
   - Background event count
   - Estimated significance (σ)
   - Mass reach estimate (GeV)
6. The **Comparison Charts** tab shows bar and radar visualisations.
7. The **Recommendation Panel** at the bottom summarises which program offers the best discovery potential.

---

## 9. How to Run Correlation Analytics

**Route:** `/CorrelationAnalytics`

1. Navigate to **Correlation Analytics**.
2. Select a **Dataset** from the dropdown.
3. Choose 2 or more **Variables** to include in the correlation matrix.
4. Click **Compute Correlations**.
5. The **Correlation Matrix** heatmap renders:
   - Deep blue = strong negative correlation (−1)
   - White = no correlation (0)
   - Deep red = strong positive correlation (+1)
6. Click any cell in the matrix to open a **Pairwise Scatter Plot** for those two variables.
7. Hover over the scatter to see individual data point values.
8. Click **Export CSV** to download the correlation coefficients.

---

## 10. How to Compute Statistical Limits

**Route:** `/StatisticalLimits`

1. Navigate to **Statistical Limits**.
2. Select the **Theory Model** and **Dataset** to use.
3. Enter the analysis inputs:
   - **Observed Events** — count observed in data
   - **Expected Background** — SM background estimate
   - **Signal Efficiency** — fraction of signal events passing selection
4. Click **Generate Limit**.
5. The **Exclusion Curve Plot** renders a 95% CL exclusion curve in the mass–coupling plane.
6. The **CLs Table** shows the CLs statistic at each mass hypothesis point.
7. Hover over the curve to read out the excluded coupling value at any mass.
8. Click **Export** to download the exclusion data as CSV or JSON.

**Interpreting the curve:**
- The **solid line** is the observed limit.
- The **dashed line** is the expected limit (median of background-only pseudo-experiments).
- The **green band** = ±1σ expected; the **yellow band** = ±2σ expected.
- Points **above** the curve are excluded at 95% CL.
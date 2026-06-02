# How-To Guide: Contributions & Recognition

> Practical step-by-step instructions for all Contribution & Recognition modules in Q-Collider.

---

## Table of Contents

1. [How to View Your Contributions](#1-how-to-view-your-contributions)
2. [How to Filter the Contribution Ledger](#2-how-to-filter-the-contribution-ledger)
3. [How to Export Contribution Records](#3-how-to-export-contribution-records)
4. [How to Check Site Contribution Rankings](#4-how-to-check-site-contribution-rankings)
5. [How to Refresh Rankings](#5-how-to-refresh-rankings)
6. [How to View the Sponsor Dashboard](#6-how-to-view-the-sponsor-dashboard)
7. [How to View the Program Roadmap](#7-how-to-view-the-program-roadmap)
8. [How to Submit a Program Proposal](#8-how-to-submit-a-program-proposal)
9. [How to Vote on a Program Proposal](#9-how-to-vote-on-a-program-proposal)
10. [How to Browse and Download Datasets](#10-how-to-browse-and-download-datasets)

---

## 1. How to View Your Contributions

**Route:** `/ScientificContributionLedger`

1. Navigate to **Contribution Ledger**.
2. The full ledger table loads showing all contributions across the network.
3. To see only your own contributions:
   - Click the **Member** filter.
   - Type your name or select yourself from the dropdown.
4. Each row shows:
   - Contribution type icon
   - Description
   - Points awarded
   - Timestamp
   - Related entity (model, site, publication, etc.)
5. The total at the bottom of the filtered view shows your cumulative contribution score.

---

## 2. How to Filter the Contribution Ledger

**Route:** `/ScientificContributionLedger`

Use the **Filters Bar** at the top:

| Filter | How to Use |
|---|---|
| **Member** | Select a user to see only their contributions |
| **Type** | Choose a contribution type (simulation, validation, publication, dataset, etc.) |
| **Date Range** | Click the calendar icon and set start and end dates |
| **Site** | Filter to contributions from a specific compute site |

- Filters stack — you can apply multiple at once.
- Click **Clear Filters** to reset to the full ledger.

**Contribution Types:**
- `simulation` — completed a simulation pipeline run
- `validation` — ran a model validation
- `publication` — authored or co-authored a paper
- `dataset` — uploaded or generated a dataset
- `campaign` — participated in a research campaign
- `benchmark` — submitted a benchmark challenge result
- `site_management` — registered or maintained a compute site

---

## 3. How to Export Contribution Records

**Route:** `/ScientificContributionLedger`

1. Apply any filters you want to export (or leave unfiltered for the full ledger).
2. Click **Export CSV** in the top-right corner.
3. A CSV file downloads with all visible rows including: member, type, description, points, timestamp, and related entity ID.

---

## 4. How to Check Site Contribution Rankings

**Route:** `/SiteContributionRankings`

1. Navigate to **Contribution Rankings**.
2. The leaderboard loads with sites ranked by total contribution score.
3. Each row shows:
   - Rank position
   - Site name and organisation
   - Total contribution score
   - Breakdown by type (compute jobs, publications, datasets, etc.)
4. Click any row to expand the **contribution breakdown** for that site.
5. Use the **Time Period** filter at the top to view rankings for:
   - Last 7 days
   - Last 30 days
   - Last 90 days
   - All time

---

## 5. How to Refresh Rankings

**Route:** `/SiteContributionRankings`

Rankings are computed from the contribution ledger and cached for performance.

1. Click **Refresh Rankings** at the top of the page.
2. A job is dispatched to recompute all site contribution scores from the latest ledger data.
3. A toast notification confirms the refresh completed.
4. The table reloads with updated scores.

**Note:** Rankings refresh automatically every 24 hours. Manual refresh is available for real-time updates.

---

## 6. How to View the Sponsor Dashboard

**Route:** `/SponsorPartnershipDashboard` · **Requires:** Sponsor / Institutional / Admin

1. Navigate to **Sponsors & Partners**.
2. If you do not have the required account type, you will see an upgrade prompt — see [Access & Membership](#access-membership).
3. The dashboard displays:
   - **Network Stats** — total sites, jobs, publications, active campaigns
   - **Growth Charts** — historical activity trend over the last 6 months
   - **Institutional Participation** — which institutions are most active
   - **Sponsor List** — all sponsors with tier, name, and contribution score
   - **Recent Publications** — latest papers published from the network
4. Use the **Navigation Tabs** to switch between stats, institutional view, and sponsor details.

---

## 7. How to View the Program Roadmap

**Route:** `/GlobalPhysicsProgramRoadmap`

1. Navigate to **Program Roadmap**.
2. The **Timeline** tab shows planned milestones in chronological order.
3. Each milestone shows:
   - Target date
   - Description
   - Status (planned / in progress / completed)
4. The **Proposals** tab lists community-submitted program proposals.
5. Click any proposal to read its full description and the associated discussion thread.
6. The **Approved Programs** tab shows formally approved collider programs with their configurations.

---

## 8. How to Submit a Program Proposal

**Route:** `/GlobalPhysicsProgramRoadmap` → Proposals tab

1. Click the **Proposals** tab.
2. Click **New Proposal**.
3. Fill in:
   - **Title** — clear, concise program name
   - **Description** — scientific motivation and expected impact
   - **Collider Type** — type of machine proposed (e.g. pp, e⁺e⁻, μμ)
   - **Beam Energy (TeV)** — target centre-of-mass energy
   - **Luminosity Target** — integrated luminosity goal
4. Click **Submit Proposal** — the proposal is published to the community.
5. Other members can comment and vote (if they have voting permission).

---

## 9. How to Vote on a Program Proposal

**Route:** `/GlobalPhysicsProgramRoadmap` → Proposals tab

**Requires:** `can_vote_on_programs` permission (sponsor, institutional, or admin account types).

1. Open a proposal from the **Proposals** tab.
2. Read the full description and discussion thread.
3. Click **Vote**.
4. Select your position: **Support** or **Oppose**.
5. Add an optional **comment** explaining your vote.
6. Click **Submit Vote** — your vote is recorded and the proposal's vote tally updates.
7. Voting closes when the proposal enters the **Review** phase (admin-controlled).

---

## 10. How to Browse and Download Datasets

**Route:** `/DatasetBrowser`

1. Navigate to **Dataset Browser**.
2. The dataset list loads showing all community-contributed datasets.
3. Use the **Filters** at the top to narrow by:
   - **Type** — signal, background, benchmark, validation
   - **Stage** — madgraph, pythia, delphes, analysis
   - **Collision Energy** — enter a GeV value range
4. Click any dataset row to open the **Detail Panel**:
   - Full metadata (process code, cross-section, event count, description)
   - Storage path and creation date
5. Click **Browse Variables** to see all available columns/observables in the dataset.
6. Click **Download** to retrieve the dataset file from its storage path.
7. Click **Load in Analysis Workspace** to open the dataset directly in the Analysis Workspace.
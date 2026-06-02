# How-To Guide: Collaboration & Publishing

> Practical step-by-step instructions for all Collaboration & Publishing modules in Q-Collider.

---

## Table of Contents

1. [How to Create a Scientific Publication](#1-how-to-create-a-scientific-publication)
2. [How to Auto-Generate a Publication Draft](#2-how-to-auto-generate-a-publication-draft)
3. [How to Manage Publication Authors and Citations](#3-how-to-manage-publication-authors-and-citations)
4. [How to Generate a Scientific Report](#4-how-to-generate-a-scientific-report)
5. [How to Start a New Collaboration](#5-how-to-start-a-new-collaboration)
6. [How to Invite a Collaborator](#6-how-to-invite-a-collaborator)
7. [How to Propose and Finalise Authorship Order](#7-how-to-propose-and-finalise-authorship-order)
8. [How to Explore the Knowledge Graph](#8-how-to-explore-the-knowledge-graph)
9. [How to Register a Knowledge Node](#9-how-to-register-a-knowledge-node)
10. [How to Use the Research Notebook](#10-how-to-use-the-research-notebook)
11. [How to Track Discovery Provenance](#11-how-to-track-discovery-provenance)

---

## 1. How to Create a Scientific Publication

**Route:** `/ScientificPublications`

1. Navigate to **Scientific Publications**.
2. Click **New Publication**.
3. Fill in the required fields:
   - **Title** — full publication title
   - **Abstract** — summary of the work
   - **Authors** — add authors from the team (see section 3)
   - **Status** — set to `draft` initially
4. Optionally link:
   - **Theory Models** — models described in the paper
   - **Emulation Runs** — runs whose results are reported
   - **Datasets** — event datasets used as input
5. Click **Save** — the publication appears in the publications list.
6. When ready to submit, change status to `submitted`.

---

## 2. How to Auto-Generate a Publication Draft

**Route:** `/ScientificPublications` → Publication Detail

1. Open an existing publication or create a new one.
2. Ensure at least one **Theory Model** and one **Emulation Run** are linked.
3. Click the **Generate Draft** button.
4. The AI drafts the following sections automatically:
   - Introduction (from model framework and motivation)
   - Methods (from emulation config and pipeline details)
   - Results (from emulation and validation scores)
   - Conclusion
5. The draft appears in the **Editor** panel — review and edit freely.
6. Click **Save Draft** to persist the content.

---

## 3. How to Manage Publication Authors and Citations

**Route:** `/ScientificPublications` → Publication Detail → Authors / Citations tabs

**Authors:**
1. Open the publication and click the **Authors** tab.
2. Click **Add Author** and enter name, affiliation, and ORCID (optional).
3. Drag rows to reorder the author list.
4. Toggle **Corresponding Author** for the primary contact.

**Citations:**
1. Click the **Citations** tab.
2. Click **Add Citation** and fill in title, authors, journal, and DOI.
3. Alternatively, click **Generate Citation** — paste in a DOI and the system fetches metadata automatically.
4. Click **Export Citations** to download in BibTeX or APA format.

---

## 4. How to Generate a Scientific Report

**Route:** `/ScientificReportBuilder`

1. Navigate to **Report Builder**.
2. Click **New Report** and enter a title.
3. Select **Data Sources** to include:
   - Theory models
   - Emulation runs
   - Analysis results
   - Validation scores
   - Publications
4. Choose **Report Sections** to generate (toggle each on/off):
   - Abstract, Introduction, Methods, Results, Discussion, References, Figures
5. Click **Generate Report** — the AI drafts each section from the linked data.
6. Review and edit in the text editor below.
7. Click **Export PDF** to download the formatted report.
8. Click **Export Markdown** for a plain-text version.

---

## 5. How to Start a New Collaboration

**Route:** `/GlobalCollaborationAuthorship`

1. Navigate to **Collaborations**.
2. Click **New Collaboration**.
3. Fill in:
   - **Name** — descriptive name (e.g. "Dark Matter Search — ATLAS Group")
   - **Description** — goals and scope
   - **Campaign** (optional) — link to a specific research campaign
4. Click **Create** — you are automatically added as the collaboration admin.
5. The collaboration appears in the **Collaboration List** with status `active`.

---

## 6. How to Invite a Collaborator

**Route:** `/GlobalCollaborationAuthorship` → Collaboration Detail

1. Open a collaboration from the list.
2. Click the **Members** tab.
3. Click **Invite Member**.
4. Enter the collaborator's **email address**.
5. Assign an **Access Level**:
   - `view` — can see all content but cannot edit
   - `edit` — can edit shared content
   - `admin` — can manage members and settings
6. Click **Send Invitation** — the collaborator receives an email invite.
7. Status shows `pending` until they accept; then changes to `accepted`.

---

## 7. How to Propose and Finalise Authorship Order

**Route:** `/GlobalCollaborationAuthorship` → Authorship tab

**Propose:**
1. Open a collaboration and click the **Authorship** tab.
2. Click **New Authorship Proposal**.
3. Select the **Publication** this proposal is for.
4. Add **Authorship Entries** — for each author specify:
   - Name and affiliation
   - Contribution statement
   - Position in the author list
5. Click **Submit Proposal** — all collaboration members can review it.

**Finalise:**
1. Once all members agree, click **Finalise Authorship**.
2. Confirm the dialog — the author list is locked and cannot be changed.
3. The finalised list is pushed to the linked publication's author record.

---

## 8. How to Explore the Knowledge Graph

**Route:** `/PhysicsKnowledgeGraphExplorer`

1. Navigate to **Knowledge Graph Explorer**.
2. The force-directed graph renders all registered nodes automatically.
3. **Node types** are colour-coded:
   - Blue = theory/model
   - Green = experiment/result
   - Orange = concept/particle
   - Purple = publication
4. Click any node to open the **Node Detail Panel** showing:
   - Node type and description
   - All connected edges and their relationship types
   - Linked publications and models
5. Use the **Type Filter** at the top to show/hide node categories.
6. Use the **Search** bar to locate a specific concept by name.
7. The **Metrics Panel** shows centrality score, degree, and cluster coefficient for the selected node.

---

## 9. How to Register a Knowledge Node

**Route:** `/PhysicsKnowledgeGraphExplorer` → Register Node

1. Click **Register Node** (top-right).
2. Fill in:
   - **Node Type** — theory, experiment, particle, concept, publication
   - **Label** — short display name
   - **Description** — detailed description
   - **Properties** — any key-value properties relevant to the node
3. Click **Save** — the node appears in the graph immediately.
4. To connect it to an existing node:
   - Click **Link Nodes**.
   - Select the source and target nodes.
   - Choose the **relationship type** (cites, extends, contradicts, supports, etc.).
   - Click **Create Link**.

---

## 10. How to Use the Research Notebook

**Route:** `/ResearchNotebook`

1. Navigate to **Research Notebook**.
2. Click **New Notebook** and give it a title and tags.
3. The rich text **Editor** opens — supports markdown, equations (LaTeX), and images.
4. Write your notes; changes **auto-save** every 30 seconds.
5. **Tag** your notebooks for organisation — click **Tags** at the top and add comma-separated tags.
6. To search notebooks, use the **Tag Filter** panel on the left.
7. To view edit history, click the **History** icon (clock) — a list of versions appears.
8. Click any version to **preview** it; click **Restore** to revert to that version.
9. To annotate a specific paragraph, highlight the text and click the **Annotate** button that appears.

---

## 11. How to Track Discovery Provenance

**Route:** `/DiscoveryProvenanceTracker`

1. Navigate to **Provenance Tracker**.
2. Select a **Publication** or **Analysis Result** from the dropdown at the top.
3. The **Provenance Timeline** renders the full data lineage chain:
   ```
   Event Dataset → Simulation Pipeline → Analysis Run → Result → Publication
   ```
4. Click any node in the timeline to see:
   - Input parameters and configuration
   - Output file paths
   - Timestamps and user who triggered the step
5. Click **Verify Reproducibility** to re-execute the chain from stored inputs and compare outputs.
6. A green checkmark = outputs match; a red warning = outputs differ (possible non-determinism or config change).
7. Click **Export Provenance** to download the graph in JSON or DOT format for external tools.
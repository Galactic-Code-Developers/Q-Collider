# Q-Collider Developer Update Guide

**SDQC Lab · Quantum Research Platform · v2.2**  
Last reviewed: June 2026

> This document tracks what areas of the platform need updates, improvements, or attention, with a clear completion status for each. Use this as the living checklist for development sprints and onboarding new contributors.

---

## Status Key

| Symbol | Meaning |
|---|---|
| ✅ Complete | Fully implemented, tested, stable |
| 🟡 Partial | Implemented but incomplete, missing edge cases, or needs polish |
| 🔴 Broken / Bug | Known bug actively causing issues |
| 🔵 Planned | Scoped and agreed but not yet started |
| ⚪ Not Started | Identified need, no work done yet |

---

## Table of Contents

1. [Navigation & Routing](#1-navigation--routing)
2. [Authentication & Access Control](#2-authentication--access-control)
3. [Frontend Pages](#3-frontend-pages)
4. [Backend Functions](#4-backend-functions)
5. [Data Entities](#5-data-entities)
6. [Design System & CSS](#6-design-system--css)
7. [Infrastructure & Compute](#7-infrastructure--compute)
8. [Collaboration & Publishing](#8-collaboration--publishing)
9. [Documentation](#9-documentation)
10. [Known Bugs Tracker](#10-known-bugs-tracker)
11. [Priority Action List](#11-priority-action-list)

---

## 1. Navigation & Routing

### 1.1 Route Definitions (`App.jsx`)
| Status | Item |
|---|---|
| ✅ | All 50+ pages have defined routes inside `AuthenticatedApp` |
| ✅ | `RootRedirect` correctly routes authenticated → `/UserDashboard`, unauthenticated → `/Landing` |
| ✅ | `Landing` is public (no auth guard) |
| 🔴 | **BUG** — Nav defined in 3 separate files (`App.jsx`, `Sidebar.jsx`, `UserDashboard.jsx`). Adding a page to only one or two causes silent omissions. See §10.2. |
| 🔵 | Planned: Extract shared `src/lib/navigationConfig.js` used by both Sidebar and Dashboard. `App.jsx` routes still need manual updates but icon/category drift would be eliminated. |

### 1.2 Sidebar (`components/layout/Sidebar.jsx`)
| Status | Item |
|---|---|
| ✅ | Collapsible sidebar with icon-only mode (64px) |
| ✅ | Category-grouped collapsible nav sections |
| ✅ | Role/account-type gating via `canSeeItem()` |
| ✅ | Active link styling |
| ✅ | `openCategories` auto-opens correct category on route change — fixed 2026-06-03 (§10.1) |
| ⚪ | No keyboard navigation / accessibility (ARIA) support |

### 1.3 User Dashboard (`pages/UserDashboard.jsx`)
| Status | Item |
|---|---|
| ✅ | All navigation categories rendered as card grids |
| ✅ | Role/account-type gating via `canSeeItem()` |
| ✅ | Stats bar (active simulations, pending validations, contributions, collaborators) |
| ✅ | PayPal donate button (opens in new tab) |
| 🟡 | Stats are fetched as separate queries — no loading state shown if data is slow |
| ⚪ | No quick-action shortcuts (e.g. "New Model", "New Campaign") from dashboard |

---

## 2. Authentication & Access Control

### 2.1 User Registration Flow
| Status | Item |
|---|---|
| ✅ | `onNewUserRegistration` function creates `AccessProfiles` record on self-registration |
| ✅ | `AccessAndMembership.jsx` fallback creates profile on first visit for invited users |
| 🔴 | **BUG** — `onNewUserRegistration` does NOT fire for admin-invited users. Invited users arrive without an `AccessProfiles` record. See §10.3. |
| 🔵 | Planned: Add invitation webhook or post-login hook to ensure profile creation regardless of registration method. |

### 2.2 Role & Permission System
| Status | Item |
|---|---|
| ✅ | `admin` / `user` roles defined and enforced |
| ✅ | `AccessProfiles.account_type` values: `subscriber`, `sponsor`, `institutional`, `institutional_sponsor`, `admin` |
| ✅ | `account_status` lifecycle: `pending` → `active` → `paused` / `revoked` |
| ✅ | `canSeeItem()` checks role AND account_type in both Sidebar and Dashboard |
| 🟡 | Backend functions inconsistently apply admin guards — some functions lack `user.role !== 'admin'` checks where they should have them |
| ⚪ | No granular permission flags enforced in backend (e.g. `can_vote_on_programs` is stored but not checked server-side) |

### 2.3 Auth Context (`lib/AuthContext.jsx`)
| Status | Item |
|---|---|
| ✅ | `useAuth()` hook provides `user`, `isLoadingAuth`, `authError` |
| ✅ | `user_not_registered` error surfaces `UserNotRegisteredError` component |
| ✅ | Loading screen shown during auth resolution |
| 🟡 | No refresh/retry on transient auth errors |

---

## 3. Frontend Pages

### 3.1 Discovery & Analysis
| Status | Page | Notes |
|---|---|---|
| ✅ | `DiscoveryMap` | Scatter plot, filters, model detail, live monitor, anomaly detection |
| ✅ | `ColliderDiscoveryMap` | 3D theory space canvas, decay tree, map controls |
| ✅ | `LiveGlobalColliderMap` | Real-time geographic feed, 30s refresh, site pins |
| ✅ | `DiscoveryGeographicMap` | Leaflet map with site pins and status colours |
| 🟡 | `AnalysisWorkspace` | Multi-pane workspace exists; workspace **save/load** may not persist correctly across sessions |
| 🟡 | `DetectorEventDisplay` | 3D canvas works; **event generator** button wires to `generateDetectorEvents` but no loading feedback |

### 3.2 Theory & Modeling
| Status | Page | Notes |
|---|---|---|
| ✅ | `TheoryLab` | CRUD model lifecycle, collision simulator tab |
| 🟡 | `UCMLTheoryLab` | Editor and parser exist; **ML auto-completion** is stubbed (no live AI call wired) |
| ✅ | `CorpusExplorer` | Search, corpus family filter, model linking |
| 🟡 | `GlobalTheoryExploration` | Campaign creation and dispatch work; **Bayesian scan strategy** is listed in UI but not implemented in backend |
| 🟡 | `ParameterSpaceDesigner` | Parameter form and save work; **3D preview** of parameter coverage not yet implemented |

### 3.3 Simulation & Validation
| Status | Page | Notes |
|---|---|---|
| ✅ | `EmulationDashboard` | Run launcher, anomaly time series, flagged candidates, history |
| ✅ | `ValidationDashboard` | Chi-squared scoring, confidence, ranking table |
| ✅ | `SimulationControlRoom` | Full 4-stage pipeline, stage tracker, job table |
| 🟡 | `GlobalBenchmarkChallengeProgram` | Challenge list and submission work; **automated scoring** (`submitChallengeResult`) does basic scoring only — no domain-specific scoring logic |
| 🟡 | `PredictiveSimulation` | Config form and run history work; **comparison view** across models is incomplete (no side-by-side chart) |
| ✅ | `QuantumDecoherenceSimulator` | All 9 tabs implemented: Configuration, 3D Detector Editor, Bloch Sphere, Heatmap, Forecasting, Results, Analysis, Algorithm Testing, Export Config |
| ✅ | `DecoherenceForecasting` | Forecast horizon, T1/T2 decay curves, CSV export |

### 3.4 Infrastructure & Computing
| Status | Page | Notes |
|---|---|---|
| ✅ | `JetsonClusterManager` | Node grid, topology, job queue, metrics — all tabs working |
| ✅ | `GlobalResearchGrid` | Site table, campaigns panel, site detail, edit modal |
| 🟡 | `EmbeddingMonitor` | Embedding trigger and status table work; **per-model feature vector inspector** shows raw numbers but no visualisation |
| ✅ | `PhysicsPipelineControlRoom` | Pipeline run cards, stage progress, file paths, pipeline actions |
| ✅ | `AutonomousDiscoveryEngine` | Autonomous mode control, discovery cycle log, QUBO formulator, Jetson annealer |
| 🟡 | `QuantumOptimizationLab` | QUBO matrix generation and annealing dispatch work; **classical vs quantum comparison** chart is placeholder |

### 3.5 Collaboration & Publishing
| Status | Page | Notes |
|---|---|---|
| ✅ | `ScientificPublications` | Full lifecycle: draft, assets, authors, citations, AI generation |
| 🟡 | `ScientificReportBuilder` | Report generation works; **PDF export** uses jsPDF but complex tables may overflow — not tested for large reports |
| ✅ | `GlobalCollaborationAuthorship` | Team management, invitations, roles, authorship proposals, finalisation |
| ✅ | `PhysicsKnowledgeGraphExplorer` | Graph canvas, node/edge registration, metrics panel |
| ✅ | `ResearchNotebook` | Rich text editor, tags, version history, annotations |
| 🟡 | `DiscoveryProvenanceTracker` | Provenance timeline renders; **reproducibility check** (re-run chain and compare) is not implemented — button exists but calls no function |

### 3.6 Site & Campaign Management
| Status | Page | Notes |
|---|---|---|
| ✅ | `SiteOnboardingWizard` | 6-step wizard, automated validation, session persistence |
| ✅ | `SiteTrustDashboard` | Trust table, certification records, node reliability, auto-certification |
| 🟡 | `CampaignManagement` | Campaign creation, site assignment, job scheduling work; **pause/resume campaign** button exists but `scheduleCampaignJobs` does not handle paused state |
| ✅ | `ColliderProgramComparison` | Program selector, comparison charts, recommendation panel, run buttons |
| 🟡 | `CorrelationAnalytics` | Correlation matrix heatmap works; **pairwise scatter plot on cell click** is not implemented |
| 🟡 | `StatisticalLimits` | Exclusion curve and CLs generation work; **hover readout** on curve is not wired |

### 3.7 Analytics & Intelligence
| Status | Page | Notes |
|---|---|---|
| 🟡 | `PredictiveAnalytics` | Discovery probability trend charts exist; framework performance scoring is client-side only — no ML inference called |

### 3.8 Contributions & Recognition
| Status | Page | Notes |
|---|---|---|
| ✅ | `ScientificContributionLedger` | Full ledger, filters, export CSV |
| ✅ | `SiteContributionRankings` | Rankings table, time filter, live recompute |
| ✅ | `SponsorPartnershipDashboard` | Network stats, growth charts, institutional participation, sponsor list |
| 🟡 | `GlobalPhysicsProgramRoadmap` | Timeline and proposals work; **proposal voting** is gated by `can_vote_on_programs` but this flag is not checked server-side in `castProposalVote` |
| ✅ | `DatasetBrowser` | Dataset list, type/energy/stage filters, variable browser, download link |

### 3.9 Settings & Access
| Status | Page | Notes |
|---|---|---|
| ✅ | `AccessAndMembership` | Self-service membership view, upgrade flow, admin panel |
| 🟡 | `InstitutionalDashboard` | Org overview, member list, sites tab work; **billing & usage** section shows placeholder — no real credit tracking connected |

---

## 4. Backend Functions

### 4.1 Core Theory & Emulation
| Status | Function | Notes |
|---|---|---|
| ✅ | `computeTheoryEmbedding` | Feature vector + discovery map coordinate generation |
| ✅ | `theoryEmbeddingEngine` | Bulk embedding orchestrator |
| ✅ | `populateEmbeddings` | Bulk populate for all models |
| ✅ | `ucmlParser` | UCML syntax validation and parse |
| ✅ | `computeEmulationMetrics` | Emulation scoring for model + config |
| ✅ | `syncEmulationRunProgram` | Sync emulation run ↔ collider program |

### 4.2 Simulation Pipeline
| Status | Function | Notes |
|---|---|---|
| ✅ | `launchSimulationPipeline` | Trigger MadGraph → Pythia → Delphes pipeline |
| ✅ | `advancePipelineStage` | Move pipeline to next stage |
| ✅ | `completeSimulationStage` | Mark stage complete |
| ✅ | `startFullPipeline` | Complete pipeline from scratch |
| ✅ | `pipelineAction` | Generic pipeline control |
| ✅ | `jetsonPipeline` | Jetson-specific pipeline execution |

### 4.3 Cluster Management
| Status | Function | Notes |
|---|---|---|
| ✅ | `clusterManager` | Node health, job assignment, cluster ops |
| ✅ | `scheduleJob` | Add job to queue |
| ✅ | `scheduleCampaignJobs` | Bulk schedule for a campaign |
| ✅ | `nodeHealthMonitor` | Heartbeat and health check |
| ✅ | `registerSiteHeartbeat` | Update site last-seen |
| ✅ | `updateNodeReliability` | Recalculate node reliability score |
| 🟡 | `clusterManager → assignQueuedJobs` | Does not respect `required_trust_tier` field on `ComputeJobs` when selecting nodes |

### 4.4 Site Lifecycle
| Status | Function | Notes |
|---|---|---|
| ✅ | `runSiteValidation` | Site certification validation |
| ✅ | `runAutoCertification` | Automated node certification |
| ✅ | `startSiteOnboarding` | Begin site registration |
| ✅ | `saveOnboardingStep` | Save onboarding progress |
| ✅ | `validateOnboardingSession` | Validate onboarding session |
| ✅ | `completeSiteOnboarding` | Finalise site registration |
| ✅ | `seedExampleOnboarding` | Seed demo data |

### 4.5 Discovery & Exploration
| Status | Function | Notes |
|---|---|---|
| ✅ | `generateTheoryCandidates` | Generate BSM candidate models |
| ✅ | `exploreTheorySpace` | Theory parameter space exploration |
| ✅ | `startExplorationCampaign` | Launch exploration campaign |
| ✅ | `dispatchExplorationJobs` | Dispatch exploration jobs |
| ✅ | `finalizeExplorationResult` | Finalise and score results |
| ✅ | `detectDiscoveryClusters` | Cluster models on discovery map |
| ✅ | `runDiscoveryCycle` | Single autonomous discovery scan |
| ✅ | `autonomousDiscoveryEngine` | Full autonomous discovery loop |
| ✅ | `dispatchColliderSimulation` | Dispatch collider simulation job |
| ✅ | `runProgramComparison` | Compare metrics across programs |

### 4.6 Analysis & Statistics
| Status | Function | Notes |
|---|---|---|
| ✅ | `generateExclusionCurve` | Exclusion curve from emulation |
| ✅ | `generateStatisticalLimit` | CLs/frequentist limits |
| ✅ | `generateMassSpectra` | Mass spectrum histograms |
| ✅ | `generateHistogram` | Generic histogram |
| ✅ | `generateScatterPlot` | Generic scatter plot |
| ✅ | `generateDetectorEvents` | Synthetic detector event data |
| ✅ | `generateCutflowFromPipeline` | Cut-flow from pipeline output |
| ✅ | `seedBenchmarkCutflows` | Seed benchmark cut-flow data |
| ✅ | `generateQUBOMatrix` | QUBO problem matrix |
| ✅ | `runGPUAnnealing` | GPU-accelerated QUBO annealing |
| ✅ | `syncAnalysisWorkspace` | Sync analysis workspace state |

### 4.7 Quantum
| Status | Function | Notes |
|---|---|---|
| ✅ | `runQuantumDecoherenceSimulation` | Multi-qubit decoherence simulation |
| ✅ | `predictDecoherence` | Decoherence forecasting |
| ✅ | `runPredictiveSimulation` | Forward-model prediction pipeline |

### 4.8 Collaboration & Publishing
| Status | Function | Notes |
|---|---|---|
| ✅ | `generatePublication` | Auto-generate publication draft |
| ✅ | `generateScientificReport` | Build formatted report |
| ✅ | `generateImpactSnapshot` | Sponsor/institution impact metrics |
| ✅ | `generateCitation` | Formatted citation generation |
| ✅ | `recordContribution` | Log user contribution |
| ✅ | `refreshSiteContributionSummary` | Recalculate site contribution totals |
| ✅ | `createCollaboration` | Create collaboration record |
| ✅ | `inviteCollaborationMember` | Send collaboration invite |
| ✅ | `proposeAuthorship` | Submit authorship proposal |
| ✅ | `finalizeAuthorshipOrder` | Lock and finalise authorship |
| ✅ | `postThreadMessage` | Post to candidate thread |
| ✅ | `createChallenge` | Create benchmark challenge |
| 🟡 | `submitChallengeResult` | Submits results and scores; domain-specific scoring logic is generic — no physics-aware scoring per task type |
| ✅ | `refreshChallengeLeaderboard` | Recalculate leaderboard |

### 4.9 Knowledge & Proposals
| Status | Function | Notes |
|---|---|---|
| ✅ | `registerKnowledgeNode` | Add node to knowledge graph |
| ✅ | `linkKnowledgeNodes` | Create edge between nodes |
| ✅ | `updateKnowledgeMetrics` | Recalculate graph metrics |
| ✅ | `createProgramProposal` | Submit program proposal |
| ✅ | `startProposalVoting` | Open voting on proposal |
| 🟡 | `castProposalVote` | Accepts votes but does NOT check `can_vote_on_programs` permission server-side |
| ✅ | `finalizeProposalVote` | Close and tally votes |

### 4.10 Dataset
| Status | Function | Notes |
|---|---|---|
| ✅ | `loadDataset` | Load event dataset |
| ✅ | `listDatasetVariables` | List dataset variables |
| ✅ | `queryDatasetEvents` | Query filtered events |

### 4.11 User Registration
| Status | Function | Notes |
|---|---|---|
| 🟡 | `onNewUserRegistration` | Creates `AccessProfiles` on self-registration only; invited users bypass this hook — see §10.3 |

---

## 5. Data Entities

### 5.1 Core Entities — Completion
| Status | Entity | Notes |
|---|---|---|
| ✅ | `TheoryModels` | Complete schema, in use everywhere |
| ✅ | `ModelParticles` | Complete, linked to models |
| ✅ | `ModelSignatures` | Complete, linked to models |
| ✅ | `ModelEmbeddings` | Complete, used in Discovery Map |
| ✅ | `TheoryFeatureVectors` | Complete, full feature set |
| ✅ | `EmulationRuns` | Complete, all score fields present |
| ✅ | `AcceleratorConfigs` | Complete |
| ✅ | `ColliderPrograms` | Complete |
| ✅ | `ComputeNodes` | Complete, includes role/region fields |
| ✅ | `ComputeJobs` | Complete, includes trust tier fields |
| ✅ | `ComputeSites` | Complete |
| ✅ | `NodeMetrics` | Complete |
| ✅ | `SimulationJobs` | Complete |
| ✅ | `PipelineRuns` | Complete, all stage path fields |
| ✅ | `EventDatasets` | Complete |
| ✅ | `AnalysisResults` | Complete |
| ✅ | `ValidationScores` | Complete |
| ✅ | `AccessProfiles` | Complete, all permission flags present |
| ✅ | `Organizations` | Complete |
| ✅ | `GlobalJobCampaigns` | Complete |
| ✅ | `ContributionLedger` | Complete |
| ✅ | `CorpusModels` | Complete |
| ✅ | `QUBOOptimizations` | Complete |
| ✅ | `QuantumDecoherenceSimulations` | Complete |
| ✅ | `SiteTrustProfiles` | Complete |
| ✅ | `ResearchNotebook` | Complete |
| ✅ | `ScientificPublications` | Complete |
| ✅ | `CollaborationMembers` | Complete |

### 5.2 Sort Key Consistency Issue
| Status | Issue |
|---|---|
| 🟡 | Some entities define their own `created_at` field (e.g. `ContributionLedger`, `SimulationJobs`) while others rely on the platform auto-field `created_date`. Queries that sort by `-created_at` silently return unsorted results on entities that lack it. **Rule: always use `-created_date` unless the entity schema explicitly defines `created_at`.** |

---

## 6. Design System & CSS

| Status | Item | Notes |
|---|---|---|
| ✅ | `globals.css` — active dark space theme token values | All theme changes MUST go here |
| 🔴 | **CONFLICT** — `main.jsx` imports `index.css` (default shadcn light tokens). `globals.css` (dark space theme) is not imported anywhere in the current codebase, meaning `index.css` is the active stylesheet. All theme changes should go in `globals.css` and it must be wired up as the CSS entry point — currently it has no effect. |
| ✅ | Tailwind config correctly maps tokens via `hsl(var(...))` |
| 🔴 | **PURGE RISK** — Dynamic class interpolation (e.g. `` `bg-${color}-500` ``) gets purged at build time. Only literal class strings in source survive. See `UserDashboard.jsx`'s `accent` object for the correct pattern. |
| ✅ | Glow utilities (`.glow-cyan`, `.glow-magenta`, `.text-glow-cyan`, `.grid-bg`) defined in `globals.css` |
| 🟡 | Typography uses system sans-serif by default; `DM Sans` is loaded via Google Fonts inline on some pages only — inconsistent across all pages |
| ⚪ | No dark/light mode toggle — dark-only. Light mode tokens in `index.css` exist but are unused. |

---

## 7. Infrastructure & Compute

### 7.1 Cluster & Node Management
| Status | Item |
|---|---|
| ✅ | Node seeding and provisioning via `jetsonPipeline → seedNodes` |
| ✅ | Pipeline execution via `jetsonPipeline → runPipeline` |
| ✅ | Job assignment respects hardware type tiers (AGX Orin → MadGraph/Pythia; Orin NX → Delphes/Analysis) |
| 🟡 | `required_trust_tier` field on `ComputeJobs` is stored but not enforced during job assignment |
| 🟡 | `routing_mode` field (`local` / `regional` / `global`) is stored but not respected in scheduling |
| ⚪ | No real heartbeat mechanism — `last_heartbeat` is updated manually; no automated agent pushes heartbeats |
| ⚪ | No real GPU metrics push — `NodeMetrics` is populated only via the `recordNodeMetrics` action called manually |

### 7.2 Automations
| Status | Item |
|---|---|
| ⚪ | No scheduled automations are set up (e.g. nightly data cleanup, periodic node health check) |
| ⚪ | No entity automations watching for job state transitions to auto-advance pipeline stages |
| ⚪ | No connector automations (no external webhooks connected) |

---

## 8. Collaboration & Publishing

| Status | Item |
|---|---|
| ✅ | Collaboration creation, member invitation, role assignment |
| ✅ | Authorship proposal and finalisation workflow |
| ✅ | Publication draft generation, asset upload, citation management |
| ✅ | Report builder with AI section generation |
| 🟡 | `ContentCollaborations` entity exists (sharing notebooks/publications with specific collaborators) but no UI exists to manage it — the entity is defined but unused |
| 🟡 | `DiscoveryProvenanceTracker` — reproducibility re-run button is a UI placeholder; function call not implemented |
| ⚪ | No email notifications on collaboration invitations — `inviteCollaborationMember` creates a record but sends no email |
| ⚪ | No email notifications on authorship proposal or vote outcomes |

---

## 9. Documentation

All documentation lives under `src/docs/`.

| Status | Document | Notes |
|---|---|---|
| ✅ | `src/docs/DEVELOPER.md` | Comprehensive developer reference — up to date as of June 2026 |
| ✅ | `src/docs/USERGUIDE.md` | Full user-facing guide covering all 50+ pages |
| ✅ | `src/docs/developerguide.md` | This document — update status tracker |
| ✅ | `src/docs/CHANGELOG.md` | Version history of all platform changes |
| ✅ | `src/docs/ONBOARDING.md` | Developer onboarding guide — platform overview, access, codebase structure, patterns, and gotchas |
| ✅ | `src/docs/howto-discovery-analysis.md` | How-to for Discovery & Analysis modules |
| ✅ | `src/docs/howto-theory-modeling.md` | How-to for Theory & Modeling |
| ✅ | `src/docs/howto-simulation-validation.md` | How-to for Simulation & Validation |
| ✅ | `src/docs/howto-infrastructure-computing.md` | How-to for Infrastructure & Computing |
| ✅ | `src/docs/howto-collaboration-publishing.md` | How-to for Collaboration & Publishing |
| ✅ | `src/docs/howto-site-campaign-management.md` | How-to for Site & Campaign Management |
| ✅ | `src/docs/howto-contributions-recognition.md` | How-to for Contributions & Recognition |
| ✅ | `src/docs/howto-settings-access.md` | How-to for Settings & Access |
| ⚪ | No `API.md` — no formal documentation of backend function input/output schemas |

---

## 10. Known Bugs Tracker

### 10.1 ✅ Sidebar category does not auto-open on navigation
- **File:** `components/layout/Sidebar.jsx`
- **Impact:** High — UX broken when navigating to a page whose category is collapsed
- **Root cause:** `openCategories` initialised once on mount — never re-evaluated when `location.pathname` changes
- **Fix applied:** Added `useEffect` watching `location.pathname` to open the matching category; `useEffect` added to React import
- **Status:** ✅ Fixed — 2026-06-03

---

### 10.2 🟡 Navigation defined in three separate files
- **Files:** `App.jsx`, `components/layout/Sidebar.jsx`, `pages/UserDashboard.jsx`
- **Impact:** Medium — new pages silently missing from nav if not added to all three
- **Fix planned:** Shared `src/lib/navigationConfig.js`
- **Status:** 🔵 Planned, not started

---

### 10.3 🟡 AccessProfiles not created for admin-invited users
- **Files:** `functions/onNewUserRegistration.js`, `pages/AccessAndMembership.jsx`
- **Impact:** Medium — invited users cannot see gated pages until they visit `/AccessAndMembership`
- **Current workaround:** `AccessAndMembership.jsx` creates the record on first visit — **do not remove this fallback**
- **Fix planned:** Post-login hook or invitation webhook
- **Status:** 🔵 Planned, not started

---

### 10.4 🟡 `created_at` vs `created_date` sort key inconsistency
- **Files:** Multiple pages and functions
- **Impact:** Low-Medium — some lists render in wrong order
- **Rule:** Use `-created_date` unless entity schema explicitly defines `created_at`
- **Status:** 🟡 Partially addressed — rule documented; old sort keys not yet audited/fixed globally

---

### 10.5 🟡 Tailwind dynamic class purging
- **Files:** Any component using runtime class interpolation
- **Impact:** Medium — styles silently missing at runtime
- **Rule:** Always write full literal class strings in source
- **Status:** ✅ Fixed in `UserDashboard.jsx` `accent` map; ⚪ other components not audited

---

### 10.6 🔴 `globals.css` not imported — `index.css` is the active stylesheet
- **Files:** `src/globals.css`, `src/index.css`, `src/main.jsx`
- **Impact:** High — the dark space theme defined in `globals.css` is not loading at all. `main.jsx` imports only `index.css` (shadcn light tokens). Any theme work done in `globals.css` has no effect until it is imported.
- **Fix:** Replace the `index.css` import in `main.jsx` with `globals.css` (or import `globals.css` after it to ensure the dark theme overrides the defaults)
- **Rule:** All theme changes go in `globals.css` — never `index.css`
- **Status:** ⚪ Not yet fixed

---

### 10.7 🔵 `castProposalVote` does not check `can_vote_on_programs` server-side
- **File:** `functions/castProposalVote.js`
- **Impact:** Medium — any authenticated user can vote even without the permission flag
- **Fix:** Add `profile.can_vote_on_programs` check after fetching the user's `AccessProfiles` record
- **Status:** ⚪ Not yet fixed

---

### 10.8 🔵 `clusterManager → assignQueuedJobs` ignores `required_trust_tier`
- **File:** `functions/clusterManager.js`
- **Impact:** Medium — jobs requiring trusted/certified nodes may be assigned to experimental nodes
- **Fix:** Filter candidate nodes by `SiteTrustProfiles.trust_tier >= job.required_trust_tier`
- **Status:** ⚪ Not yet fixed

---

## 11. Priority Action List

Ordered by impact + effort ratio (highest priority first):

| Priority | Action | Effort | Impact |
|---|---|---|---|
| ✅ 1 | ~~Fix Sidebar `openCategories` bug (§10.1)~~ **DONE** — `useEffect` for `location.pathname` added 2026-06-03 | Low | High |
| 🔥 2 | Fix `globals.css` import — wire it up in `main.jsx` so the dark theme actually loads (§10.6) | Low | High |
| 🔥 3 | Fix `castProposalVote` missing permission check (§10.7) | Low | Medium |
| 🔥 4 | Fix `onNewUserRegistration` for invited users (§10.3) | Medium | Medium |
| 🔶 5 | Implement `DiscoveryProvenanceTracker` reproducibility check | Medium | Medium |
| 🔶 6 | Extract shared `navigationConfig.js` (§10.2) | Medium | Medium |
| 🔶 7 | Add `required_trust_tier` enforcement in `clusterManager` (§10.8) | Low | Medium |
| 🔷 8 | Wire ML auto-completion in `UCMLTheoryLab` | High | Low-Medium |
| 🔷 9 | Implement pairwise scatter plot in `CorrelationAnalytics` | Medium | Low |
| 🔷 10 | Add email notifications for collaboration invitations | Medium | Medium |
| 🔷 11 | Set up scheduled automations (nightly node health, pipeline advancement) | Medium | Medium |
| ⬜ 12 | Build UI for `ContentCollaborations` entity | High | Low |
| ⬜ 13 | Audit all pages for `-created_at` → `-created_date` sort key fixes (§10.4) | Low | Low |
| ⬜ 14 | Audit all components for dynamic Tailwind class interpolation (§10.5) | Medium | Low |
| ✅ 15 | ~~Add `CHANGELOG.md`, `API.md`, `ONBOARDING.md`~~ — `CHANGELOG.md` and `ONBOARDING.md` **DONE**; `API.md` still pending | Low | Medium |

---

*Q-Collider Developer Update Guide · SDQC Lab · v2.2 · June 2026*  
*Maintain this file whenever a bug is fixed, a feature is completed, or a new issue is identified.*

# Q-Collider Changelog

**SDQC Lab · Quantum Research Platform**  
All notable changes to this project are documented here.  
Format: `[vX.Y.Z] — YYYY-MM-DD` · Types: `Added` `Changed` `Fixed` `Removed` `Security`

---

## [v2.2.0] — 2026-06-03

### Added
- `docs/ONBOARDING.md` — new developer onboarding guide covering platform overview, access setup, codebase structure, key concepts, step-by-step guides for pages/functions/entities, common patterns, gotchas, and a "where to find things" reference table

### Fixed
- `components/layout/Sidebar.jsx` — sidebar category now auto-opens when navigating to a page in a collapsed category; added `useEffect` watching `location.pathname` to re-evaluate `openCategories` state on route change (bug §10.1); added `useEffect` to imports

---

## [v2.1.0] — 2026-06-03

### Added
- `docs/developerguide.md` — living update-status tracker covering all pages, functions, entities, bugs, and priority action list
- `docs/CHANGELOG.md` — this file; version history of all platform changes
- PayPal donate button added to `UserDashboard` header (top-right, next to "System Online" indicator), opens in new tab

### Fixed
- PayPal donate button `target` corrected to `_blank` (opens in new window as intended)

### Removed
- Duplicate PayPal donate button removed from `Sidebar` footer

---

## [v2.0.0] — 2026-06-01

### Added
- **Quantum Decoherence Simulator** (`/QuantumDecoherenceSimulator`) — full 6-tab interface: Simulation, Detector, Bloch Sphere, Noise Spectrum, Algorithm Testing, Results
- **Decoherence Forecasting** (`/DecoherenceForecasting`) — T1/T2 decay curve projections with CSV export
- **Predictive Analytics** (`/PredictiveAnalytics`) — discovery probability trend dashboard with framework performance scoring
- **Institutional Dashboard** (`/InstitutionalDashboard`) — org-level analytics, member management, site portfolio, billing overview
- **Access & Membership** (`/AccessAndMembership`) — self-service membership tier view, upgrade flow, admin management panel
- **Live Global Collider Map** (`/LiveGlobalColliderMap`) — real-time geographic feed with 30-second refresh, site pins, activity timeline
- **Sponsor & Partnership Dashboard** (`/SponsorPartnershipDashboard`) — network stats, growth charts, institutional participation
- **Global Physics Program Roadmap** (`/GlobalPhysicsProgramRoadmap`) — timeline view, proposal voting, approved programs
- `functions/runQuantumDecoherenceSimulation` — multi-qubit decoherence simulation backend
- `functions/predictDecoherence` — ML-based decoherence forecasting
- `functions/generateImpactSnapshot` — sponsor/institution impact metric computation
- `functions/onNewUserRegistration` — post-registration hook creating `AccessProfiles` record
- `entities/QuantumDecoherenceSimulations` — decoherence simulation run records
- `entities/NoiseReductionAlgorithms` — algorithm configuration records
- `entities/DecoherenceTestResults` — simulation test output records
- `entities/SponsorPartners` — sponsor organisation records
- `entities/ImpactSnapshots` — periodic impact metric snapshots
- `entities/AccessProfiles` — user membership and permission records
- `entities/Organizations` — institution records
- `components/quantum/BlochSphereVisualizer` — 3D qubit state visualisation
- `components/quantum/DetectorGeometryEditor` — detector model configuration for qubit readout
- `components/quantum/DecoherenceForecaster` — forecasting chart component
- `components/quantum/AlgorithmConfigExporter` — export noise-reduction algorithm configurations
- `components/auth/EnsureSubscriberProfile` — profile existence guard used in `AppLayout`
- User Dashboard stats bar: active simulations, pending validations, total contributions, collaborators
- UCML Theory Lab (`/UCMLTheoryLab`) marked as **New** in navigation badges

### Changed
- `UserDashboard` redesigned — card grid layout with colour-coded module categories, badge system (Live / New / Admin), role/account-type gating
- `Sidebar` updated — collapsible category groups, icon-only collapse mode (64px), `canSeeItem()` gating applied
- `AppLayout` updated to include `EnsureSubscriberProfile` guard
- Navigation categories expanded from 7 to 9 groups (added: Analytics & Intelligence, Settings & Access)
- `AccessProfiles` entity extended with all permission flag fields (`can_manage_team`, `can_manage_site`, `can_join_campaigns`, `can_vote_on_programs`, `can_submit_publications`, `can_sponsor_campaigns`)

### Fixed
- Auth flow: `RootRedirect` now correctly sends authenticated users to `/UserDashboard` and unauthenticated to `/Landing`
- `UserNotRegisteredError` component surfaces properly when `authError.type === 'user_not_registered'`

---

## [v1.5.0] — 2026-05-15

### Added
- **Global Collaboration & Authorship** (`/GlobalCollaborationAuthorship`) — team management, invitations, authorship proposal and finalisation
- **Physics Knowledge Graph Explorer** (`/PhysicsKnowledgeGraphExplorer`) — force-directed graph, node/edge registration, centrality metrics
- **Discovery Provenance Tracker** (`/DiscoveryProvenanceTracker`) — data lineage timeline from dataset → publication
- **Research Notebook** (`/ResearchNotebook`) — rich text editor, version history, tagging, annotations
- **Scientific Report Builder** (`/ScientificReportBuilder`) — AI-assisted section generation, PDF export
- `functions/createCollaboration` — collaboration record creation
- `functions/inviteCollaborationMember` — email-based invitation dispatch
- `functions/proposeAuthorship` — authorship proposal submission
- `functions/finalizeAuthorshipOrder` — lock and finalise author list
- `functions/registerKnowledgeNode` — add concept to knowledge graph
- `functions/linkKnowledgeNodes` — create semantic edges between nodes
- `functions/updateKnowledgeMetrics` — graph centrality recalculation
- `functions/generateScientificReport` — formatted report from linked data sources
- `entities/ResearchCollaborations` — collaboration group records
- `entities/CollaborationMembers` — team member records with roles
- `entities/AuthorshipProposals` — authorship order proposals
- `entities/AuthorshipEntries` — finalised author list entries
- `entities/KnowledgeNodes` — graph node records
- `entities/KnowledgeEdges` — graph edge records
- `entities/KnowledgeMetrics` — centrality and cluster metrics
- `entities/ResearchNotebook` — notebook entry records
- `entities/ContentCollaborations` — content-sharing permissions (entity only; UI pending)
- `components/notebook/NotebookEditor` — WYSIWYG rich text editor
- `components/notebook/NotebookList` — notebook listing with tag filter
- `components/annotations/AnnotationPanel` — paragraph-level annotation UI
- `components/timeline/DiscoveryProvenanceTimeline` — provenance chain visualisation

### Changed
- `ScientificPublications` extended with citation manager and AI draft generation
- `functions/generatePublication` updated to link emulation runs and analysis results

---

## [v1.4.0] — 2026-05-01

### Added
- **Site Onboarding Wizard** (`/SiteOnboardingWizard`) — 6-step wizard for registering new compute sites
- **Site Trust Dashboard** (`/SiteTrustDashboard`) — trust tier management, certification records, node reliability
- **Global Research Grid** (`/GlobalResearchGrid`) — multi-site grid overview, campaign panels, site detail
- **Site Detail** (`/SiteDetail/:siteId`) — per-site drilldown with nodes, jobs, and trust profile
- **Scientific Contribution Ledger** (`/ScientificContributionLedger`) — full audit log with filters and CSV export
- **Site Contribution Rankings** (`/SiteContributionRankings`) — leaderboard with time-filtered views
- `functions/startSiteOnboarding`, `saveOnboardingStep`, `validateOnboardingSession`, `completeSiteOnboarding` — full onboarding workflow
- `functions/runSiteValidation` — automated site connectivity and benchmark checks
- `functions/runAutoCertification` — automated node certification pipeline
- `functions/registerSiteHeartbeat` — site last-seen timestamp update
- `functions/updateNodeReliability` — node reliability score recalculation
- `functions/recordContribution` — scientific contribution logging
- `functions/refreshSiteContributionSummary` — site contribution total recalculation
- `entities/ComputeSites` — physical compute site records
- `entities/SiteOnboardingSessions` — onboarding session state
- `entities/SiteValidationChecks` — validation check results
- `entities/SiteTrustProfiles` — site trust tier and certification status
- `entities/SiteCertificationRecords` — certification run history
- `entities/NodeReliabilityMetrics` — per-node reliability trend data
- `entities/ContributionLedger` — user contribution log
- `entities/SiteContributionSummaries` — aggregated site contribution totals
- `entities/ContributionAwards` — contribution milestone awards
- `entities/GlobalJobCampaigns` — research campaign definitions
- `components/trust/*` — TrustOverviewCards, TrustTable, CertificationRecordsPanel, NodeReliabilityPanel
- `components/grid/*` — GridSummaryCards, SiteTable, SiteDetailPanel, CampaignsPanel, SiteEditModal

### Changed
- `ComputeNodes` schema extended with `node_role`, `public_endpoint`, `scheduler_region` fields
- `ComputeJobs` schema extended with `site_id`, `campaign_id`, `routing_mode`, `trust_level`, `required_trust_tier`, `validation_flag`

---

## [v1.3.0] — 2026-04-15

### Added
- **Campaign Management** (`/CampaignManagement`) — campaign creation, site assignment, job scheduling, progress tracking
- **Collider Program Comparison** (`/ColliderProgramComparison`) — side-by-side program comparison with charts and AI recommendations
- **Correlation Analytics** (`/CorrelationAnalytics`) — correlation matrix heatmap across dataset variables
- **Statistical Limits** (`/StatisticalLimits`) — CLs/frequentist exclusion curve generation
- **Global Theory Exploration** (`/GlobalTheoryExploration`) — parameter sweep campaign engine with candidate leaderboard
- **Parameter Space Designer** (`/ParameterSpaceDesigner`) — visual parameter dimension configuration
- **Global Benchmark Challenge Program** (`/GlobalBenchmarkChallengeProgram`) — community benchmarking with leaderboards
- `functions/scheduleCampaignJobs` — bulk job scheduling for campaigns
- `functions/runProgramComparison` — cross-program metric comparison
- `functions/generateStatisticalLimit` — CLs limit computation
- `functions/generateExclusionCurve` — exclusion curve from emulation results
- `functions/startExplorationCampaign`, `dispatchExplorationJobs`, `finalizeExplorationResult` — exploration campaign workflow
- `functions/exploreTheorySpace` — theory parameter space exploration
- `functions/generateTheoryCandidates` — BSM candidate generation
- `functions/createChallenge`, `submitChallengeResult`, `refreshChallengeLeaderboard` — benchmark challenge workflow
- `entities/TheoryExplorationCampaigns`, `ParameterSpaces`, `ExplorationResults`, `CandidateAnnotations`
- `entities/BenchmarkChallenges`, `ChallengeTasks`, `ChallengeSubmissions`, `ChallengeLeaderboards`
- `entities/StatisticalLimits`, `ExclusionCurvePoints`
- `components/comparison/*` — ComparisonTable, ComparisonCharts, ModelSelector, ProgramComparisonCard, RecommendationPanel, ProgramRunButtons
- `components/exploration/*` — CampaignSummaryCards, CandidateLeaderboard

---

## [v1.2.0] — 2026-04-01

### Added
- **Analysis Workspace** (`/AnalysisWorkspace`) — multi-pane integrated analysis environment
- **Dataset Browser** (`/DatasetBrowser`) — dataset list, filters, variable browser, download
- **Detector Event Display** (`/DetectorEventDisplay`) — 3D particle collision event viewer
- **Predictive Simulation** (`/PredictiveSimulation`) — ML surrogate forward-model prediction
- **Autonomous Discovery Engine** (`/AutonomousDiscoveryEngine`) — continuous automated signal scanning
- **Quantum Optimization Lab** (`/QuantumOptimizationLab`) — QUBO formulation and GPU annealing
- `functions/syncAnalysisWorkspace` — multi-panel workspace state sync
- `functions/loadDataset`, `listDatasetVariables`, `queryDatasetEvents` — dataset access
- `functions/generateMassSpectra`, `generateHistogram`, `generateScatterPlot` — analysis plot generation
- `functions/generateCutflowFromPipeline`, `seedBenchmarkCutflows` — cut-flow generation
- `functions/generateDetectorEvents` — synthetic detector event seeding
- `functions/runPredictiveSimulation` — prediction pipeline execution
- `functions/runDiscoveryCycle`, `autonomousDiscoveryEngine` — autonomous discovery loop
- `functions/generateQUBOMatrix`, `runGPUAnnealing` — QUBO and annealing
- `entities/AnalysisWorkspaces`, `DatasetVariables`, `DatasetEvents`, `EventVariables`
- `entities/CutFlowRuns`, `CutFlowSteps`, `MassSpectra`, `MassSpectrumBins`
- `entities/QUBOOptimizations`
- `components/workspace/*` — full 6-panel workspace UI
- `components/dataset/*` — DatasetList, EventList, EventInspector, VariableTable, ExpressionFilter, QuickPlots, StatsPanel
- `components/detector/*` — DetectorCanvas, DetectorEventFilters, DetectorEventSummary, MassSpectrumPanel, CutFlowTable
- `components/emulation/*` — AnomalyTimeSeries, FlaggedCandidates
- `components/limits/*` — ExclusionCurvePlot
- `components/analytics/*` — CorrelationMatrix

---

## [v1.1.0] — 2026-03-15

### Added
- **Jetson Cluster Manager** (`/JetsonClusterManager`) — node grid, topology view, job queue, metrics
- **Physics Pipeline Control Room** (`/PhysicsPipelineControlRoom`) — pipeline run cards, stage tracking, file paths
- **Simulation Control Room** (`/SimulationControlRoom`) — full MC simulation pipeline launcher and monitor
- **Embedding Monitor** (`/EmbeddingMonitor`) — embedding status table, trigger bulk generation
- **Collider Program Comparison** — initial version (metrics table only)
- `functions/clusterManager` — node lifecycle, job assignment, discovery map integration
- `functions/jetsonPipeline` — Jetson-specific pipeline execution (seedNodes, runPipeline)
- `functions/scheduleJob` — individual job queue entry
- `functions/nodeHealthMonitor` — heartbeat and health check
- `functions/launchSimulationPipeline`, `advancePipelineStage`, `completeSimulationStage`, `startFullPipeline`, `pipelineAction` — simulation pipeline control
- `functions/computeTheoryEmbedding`, `theoryEmbeddingEngine`, `populateEmbeddings` — embedding generation
- `functions/detectDiscoveryClusters` — discovery map clustering
- `entities/ComputeNodes`, `ComputeJobs`, `NodeMetrics`, `ClusterRuns`
- `entities/SimulationJobs`, `PipelineRuns`, `EventDatasets`, `AnalysisResults`
- `entities/ModelEmbeddings`, `TheoryFeatureVectors`
- `components/cluster/*` — ClusterOverview, NodeCard, JobQueueTable, MetricsMonitor, JetsonTopology
- `components/pipeline/*` — PipelineRunCard, StageProgress, FilePaths
- `components/simulation/*` — ColliderSimEngine, SimJobTable

---

## [v1.0.0] — 2026-03-01

### Added
- **Landing page** (`/Landing`) — public marketing/entry page
- **Theory Lab** (`/TheoryLab`) — BSM/SM model creation, UCML code entry, collision simulator
- **UCML Theory Lab** (`/UCMLTheoryLab`) — ML-augmented UCML editor with parser
- **Corpus Explorer** (`/CorpusExplorer`) — searchable research literature corpus
- **Emulation Dashboard** (`/EmulationDashboard`) — hardware-in-loop emulation run launcher
- **Validation Dashboard** (`/ValidationDashboard`) — chi-squared scoring and model ranking
- **Discovery Map** (`/DiscoveryMap`) — high-dimensional embedding scatter plot with filters
- **Collider Discovery Map** (`/ColliderDiscoveryMap`) — 3D theory space canvas with decay tree
- **Discovery Geographic Map** (`/DiscoveryGeographicMap`) — Leaflet map with site pins
- **Scientific Publications** (`/ScientificPublications`) — publication lifecycle management
- `functions/ucmlParser` — UCML syntax validation
- `functions/computeEmulationMetrics` — emulation scoring
- `functions/syncEmulationRunProgram` — emulation run ↔ program sync
- `functions/generatePublication` — AI publication draft generation
- `functions/generateCitation` — citation formatting
- `functions/dispatchColliderSimulation` — collider simulation dispatch
- `functions/postThreadMessage` — candidate thread messaging
- `functions/createProgramProposal`, `startProposalVoting`, `castProposalVote`, `finalizeProposalVote` — program proposal workflow
- `entities/TheoryModels`, `ModelParticles`, `ModelSignatures` — core theory model schema
- `entities/EmulationRuns`, `AcceleratorConfigs`, `ColliderPrograms` — emulation infrastructure
- `entities/ValidationScores`, `BenchmarkProcesses`, `TheoryCandidates`, `DiscoveryMetrics`
- `entities/CorpusModels` — Valamontes/MV corpus classification
- `entities/ScientificPublications`, `PublicationAuthors`, `PublicationAssets`, `PublicationCitations`
- `entities/ProgramProposals`, `ProposalDiscussions`, `ProposalVotes`, `ApprovedPrograms`
- `entities/CandidateThreads`, `ThreadMessages`
- `components/theory/*` — TheoryForm, ModelList, CollisionSimulator, DecayTreeCanvas
- `components/discovery/*` — DiscoveryScatterPlot, ModelDetailPanel, MapFilters, ClusterLiveMonitor, AnomalySignalScatterPlot, AcceleratorSelector, AcceleratorConfigModal, SensitivityCurveGenerator, SavedViews, ParticleSearchFilter
- `components/collider/*` — TheorySpaceCanvas, MapControls, MapLegend, ModelDetailSidebar, DecayTreeVisualization
- `components/shared/*` — PageHeader, StatCard, StatusBadge
- `components/layout/*` — AppLayout, Sidebar
- `lib/AuthContext.jsx` — React auth context and hooks
- `globals.css` — dark space theme design tokens
- Base44 platform integration: entity SDK, backend function SDK, TanStack Query patterns established

---

*Q-Collider Changelog · SDQC Lab · Maintained by the platform team.*  
*Update this file with every release. Follow format: Added / Changed / Fixed / Removed / Security.*

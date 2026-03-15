# Jetson Cluster Architecture
## Distributed Collider Emulation Infrastructure

Q-Collider uses NVIDIA Jetson devices as a distributed compute fabric for executing collider emulation workloads.

The goal is to create a compact GPU-based research cluster capable of running simulation pipelines, theory exploration tasks, and anomaly detection jobs.

---

## Why Jetson

Jetson platforms provide several advantages for distributed scientific workloads.

GPU acceleration  
CUDA-capable architecture allows parallel numerical workloads.

Low power consumption  
Jetson nodes operate efficiently compared to traditional HPC servers.

Compact deployment  
Clusters can be deployed in small laboratories or educational environments.

AI acceleration  
Tensor cores enable anomaly detection and ranking models.

These characteristics make Jetson well suited for experimental collider emulation systems.

---

## Cluster Components

A Q-Collider Jetson cluster typically includes several node types.

Controller Node  
Manages job scheduling and system monitoring.

Compute Nodes  
Execute collider simulation stages and analysis tasks.

Monitoring Node  
Collects telemetry and performance metrics.

Storage Node  
Stores event datasets and analysis outputs.

---

## Node Roles

Controller nodes handle:

- job dispatch
- queue management
- cluster state monitoring

Compute nodes handle:

- emulator workloads
- QUBO optimization jobs
- validation runs
- theory scans

Monitoring nodes collect:

- GPU utilization
- CPU utilization
- temperature
- power consumption

---

## Job Types

The system supports several job categories.

Emulator jobs  
Run collider simulations for selected theory models.

Validation jobs  
Compare predicted signatures against datasets.

QUBO jobs  
Perform optimization tasks to prioritize promising models.

Theory scan jobs  
Explore parameter variations across model space.

Each job type can be routed to nodes with appropriate resources.

---

## Node Monitoring

Jetson nodes report telemetry through NodeMetrics records.

Metrics include:

- GPU utilization
- CPU utilization
- RAM utilization
- temperature
- power draw

These metrics allow cluster health to be visualized in the Jetson Cluster Manager dashboard.

---

## Job Scheduling

The scheduling system assigns queued jobs to available nodes using load balancing rules.

Example logic:

emulator jobs → prefer high compute nodes  
qubo jobs → prefer nodes with higher GPU memory  
validation jobs → may run on any node  
theory scans → distributed evenly across nodes

This ensures efficient use of cluster resources.

---

## Node Status States

Nodes can appear in one of several states.

online  
available for jobs

busy  
currently executing jobs

offline  
not reachable or heartbeat missing

maintenance  
temporarily disabled

---

## Cluster Telemetry

The cluster manager provides several system-level statistics.

total active nodes  
total active jobs  
queued jobs  
completed jobs  
failed jobs  
average cluster load

These metrics allow researchers to monitor ongoing theory exploration campaigns.

---

## Future Cluster Capabilities

Future Jetson cluster upgrades may include:

GPU-aware scheduling  
automatic workload scaling  
distributed parameter scanning  
real-time anomaly detection  
energy efficiency optimization

The cluster architecture is intentionally modular to support these upgrades.

---

## Research Role

The Jetson cluster is not intended to replace large-scale collider computing grids.

Instead, it provides a **compact distributed laboratory** for rapid theory exploration, fast emulation experiments, and discovery-space navigation.

This allows researchers to test ideas quickly before committing to larger simulation campaigns.

# 02 — Environment Setup

This page links to the official installation guides and documents what this project encountered during setup. Read the gotchas before starting — they will save you significant time.

---

## Official Installation Guides

Follow these in order:

| Step | Guide |
|------|-------|
| 1. Isaac Sim (local) | https://docs.isaacsim.omniverse.nvidia.com/latest/index.html |
| 2. Isaac Sim on AWS (cloud) | https://docs.isaacsim.omniverse.nvidia.com/4.5.0/installation/install_advanced_cloud_setup_aws.html |
| 3. ROS 2 with Isaac Sim | https://docs.isaacsim.omniverse.nvidia.com/4.5.0/installation/install_ros.html |
| 4. cuOpt with Isaac Sim | https://docs.isaacsim.omniverse.nvidia.com/4.5.0/digital_twin/warehouse_logistics/logistics_tutorial_cuopt.html |

---

## What This Project Encountered During Setup

### Hardware Blocker
Isaac Sim could not run on the local development laptop — no dedicated NVIDIA GPU available. Required provisioning a cloud GPU instance via RMIT RACE Team AWS. This caused a 2-week delay at the start of the project.

**→ See [GOTCHA-001](./06-gotchas.md) and [GOTCHA-002](./06-gotchas.md)**

### AWS Installation
The Isaac Sim installation on AWS involves more steps than the standard workstation installation. The official AWS guide covers the process but requires following multiple steps carefully. Allow at least one full day for the combined AWS setup and Isaac Sim installation process.

**→ See [GOTCHA-004](./06-gotchas.md)**

### AWS GPU Availability
This project lost AWS access for nearly 3 weeks (Weeks 10–12) due to global GPU chip shortage limiting cloud instance availability. This is worth noting as a risk for any cloud-based Isaac Sim project.

**→ See [GOTCHA-008](./06-gotchas.md)**

### NVIDIA Asset Browser
The NVIDIA Asset Browser is not visible by default in Isaac Sim. It requires manually enabling the `omni.kit.browser_asset` extension before it appears.

**→ See [GOTCHA-003](./06-gotchas.md)**

---

## Confirmed Working Environment (This Project)

- **GPU:** NVIDIA L40S (40 GB VRAM) — AWS via RMIT RACE Team
- **OS:** Ubuntu 22.04
- **Isaac Sim:** Full 5.1.0
- **ROS 2:** Jazzy
- **Workspace path:** `/home/ubuntu/IsaacSim-ros_workspaces/jazzy_ws`

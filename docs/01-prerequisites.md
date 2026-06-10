# 01 — Prerequisites

Before starting, read this page fully. Hardware is the most common blocker — confirm your setup before investing time in installation.

---

## Hardware

Isaac Sim requires a **dedicated NVIDIA GPU**. A standard laptop with integrated graphics will not work — this was a confirmed blocker on this project. See [GOTCHA-001](./08-gotchas.md) and [GOTCHA-002](./08-gotchas.md).

**Confirmed working (this project):**
- GPU: NVIDIA L40S (40 GB VRAM) via AWS cloud
- OS: Ubuntu 22.04

**Minimum recommended:**
- GPU: NVIDIA RTX 3080 (8 GB VRAM)
- RAM: 32 GB
- Storage: 50 GB free SSD
- OS: Ubuntu 20.04 or 22.04

> ⚠️ If you do not have a qualifying GPU locally, set up a cloud GPU instance **before starting development**. See [docs/08-compute-sizing.md](./08-compute-sizing.md) for options. Do this in Week 1 — not later.

---

## Software

| Software | Official Installation Guide |
|----------|---------------------------|
| NVIDIA Isaac Sim | https://docs.isaacsim.omniverse.nvidia.com/latest/index.html |
| Isaac Sim System Requirements | https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/requirements.html |
| Isaac Sim on AWS (cloud) | https://docs.isaacsim.omniverse.nvidia.com/4.2.0/installation/install_advanced_cloud_setup_aws.html |
| ROS 2 Installation (via Isaac Sim) | https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/install_ros.html |
| NVIDIA cuOpt | https://docs.isaacsim.omniverse.nvidia.com/4.2.0/features/warehouse_logistics/logistics_tutorial_cuopt.html |

---

## Prerequisite Training

Complete the NVIDIA training courses **before** starting development. They are free and significantly reduce the confusion of working with this toolchain for the first time.

The full Industrial Digital Twins learning path is available here:
> https://learn.nvidia.com/ — search "Industrial Digital Twins"

### Recommended Course Order

| # | Course | Link | Duration |
|---|--------|------|----------|
| 1 | What is a Digital Twin? (start here) | https://www.nvidia.com/en-us/glossary/digital-twin/ | Article |
| 2 | Fundamentals of Working with OpenUSD | https://learn.nvidia.com/courses/course-detail?course_id=course-v1:DLI+S-OV-02+V1 | 2 hrs — Free |
| 3 | An Introduction to Developing with NVIDIA Omniverse | https://learn.nvidia.com/courses/course-detail?course_id=course-v1:DLI+S-OV-11+V1 | 2 hrs — Free |
| 4 | Assembling Your First Digital Twin with Omniverse and OpenUSD | https://learn.nvidia.com/courses/course-detail?course_id=course-v1:DLI+S-OV-16+V1 | 4 hrs — Free |
| 5 | Learn OpenUSD: Creating Composition Arcs | https://learn.nvidia.com/courses/course-detail?course_id=course-v1:DLI+S-OV-13+V1 | 3 hrs — Free |
| 6 | Learn OpenUSD: Asset Structure Principles and Content Aggregation | https://learn.nvidia.com/courses/course-detail?course_id=course-v1:DLI+S-OV-25+V1 | 3 hrs — Free |
| 7 | Learn OpenUSD: Developing Data Exchange Pipelines | https://learn.nvidia.com/courses/course-detail?course_id=course-v1:DLI+S-OV-49+V1 | 1.5 hrs — Free |
| 8 | Getting Started with Isaac Sim | https://learn.nvidia.com/courses/course-detail?course_id=course-v1:DLI+S-OV-33+V1 | Free |
| 9 | OpenUSD Foundations Learning Path | https://docs.nvidia.com/learn-openusd/latest/index.html#start-learning | 11 hrs — Free |
| 10 | Learn OpenUSD: Asset Modularity and Instancing | https://learn.nvidia.com/courses/course-detail?course_id=course-v1:DLI+S-OV-26+V1 | Coming Soon |

> **Note:** Courses 1–8 were completed as part of this project. The training significantly reduced confusion — do not skip them.

---

## Accounts Required

- **NVIDIA NGC Account** — required to access Isaac Sim and cuOpt container
- **AWS Account** — if using cloud GPU (or institutional access if available)

---

## Before You Start — Honest Advice

- Confirm your GPU meets requirements **before** installing anything
- If using institutional cloud access, request it in Week 1 — approval can take 1–2 weeks
- YouTube tutorials for Isaac Sim warehouse work are very limited — a small number of useful ones exist (see [docs/06-resources.md](./06-resources.md))
- The **NVIDIA Developer Forums** is your most important resource when official docs run out: https://forums.developer.nvidia.com/c/omniverse/isaac-sim/
- Expect to spend significant time learning by doing — the official docs are good for individual components but do not show how to connect everything together

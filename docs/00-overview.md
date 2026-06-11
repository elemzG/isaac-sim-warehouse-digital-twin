# 00 — Project Overview

## What This Project Is

This is a **Technical Feasibility and Integration Study** examining how to build a customisable warehouse digital twin using NVIDIA Isaac Sim, ROS 2 Nav2, and NVIDIA cuOpt.

The project did not build a warehouse from scratch. It built on top of NVIDIA's existing examples and assets — and documented every gap, gotcha, and undocumented behaviour encountered along the way. The primary value of this repository is not the simulation itself but the honest account of what the toolchain requires, where it fails, and what a developer needs to know before starting.

---

## The Core Problem This Project Addresses

NVIDIA provides good component-level documentation for Isaac Sim, the Warehouse Creator, cuOpt, and the ROS 2 bridge. However, documentation on connecting these components into a complete working warehouse simulation is limited. There is limited guidance on:

- How to connect these components into a working warehouse simulation
- What to do when the official examples behave unexpectedly
- How to run Isaac Sim without high-end local hardware
- How to bridge cuOpt route optimisation with ROS 2 Nav2 execution

This project worked through all of these challenges and documented the findings.

---

## What Was Achieved

| Deliverable | Status | Notes |
|-------------|--------|-------|
| Warehouse scene with shelves, boxes, conveyor | ✅ Complete | Built on ROS 2 Nova Carter base scene |
| Scalable warehouse | ✅ Complete | Via Warehouse Creator extension |
| Occupancy map for custom layout | ✅ Complete | Generated from warehouse geometry |
| ROS 2 Nav2 — Nova Carter navigating | ✅ Complete | Navigation and localisation active |
| NVIDIA cuOpt — 2-vehicle routing | ✅ Complete | 91-node graph, solution cost 322.69 |
| cuOpt ↔ Nav2 bridge | ❌ Not completed | No documented integration path — Gap G-05 |
| Full fleet simulation | ❌ Not completed | Dependent on bridge above |
| KPI pipeline | ❌ Not completed | Dependent on fleet simulation |

---

## What Was Not Achieved and Why

The cuOpt ↔ Nav2 bridge is the critical missing piece. cuOpt generates optimal routes and Nav2 navigates robots — but no documented method exists for connecting the two. This is the most significant research finding of the project and is documented in detail in [docs/09-gap-analysis.md](./09-gap-analysis.md).

Two hardware blockers affected the project timeline:
- **Blocker 1 (Weeks 3–5):** Local laptop could not run Isaac Sim — resolved by provisioning RMIT RACE Team AWS cloud instance (NVIDIA L40S, 48 GB VRAM)
- **Blocker 2 (Weeks 10–12):** AWS GPU unavailable due to global chip shortage — all development halted for nearly 3 weeks

---

## Research Questions

| ID | Question |
|----|---------|
| RQ-01 | What is the minimum viable workflow to construct a parameterized, customizable warehouse digital twin in NVIDIA Omniverse using Isaac Sim's Warehouse Logistics utilities, and where does the process fail or require undocumented workarounds? |
| RQ-02 | What are the technical, hardware, and documentation barriers that prevent an independent developer from successfully deploying this workflow, and how can these be mitigated? |

---

## Key Resources

| Resource | Link |
|----------|------|
| Isaac Sim Documentation | https://docs.isaacsim.omniverse.nvidia.com/latest/index.html |
| NVIDIA Developer Forums | https://forums.developer.nvidia.com/c/omniverse/isaac-sim/ |
| OpenUSD Documentation | https://openusd.org/docs/index.html |
| ROS 2 Nav2 | https://docs.nav2.org/ |
| NVIDIA cuOpt | https://docs.nvidia.com/cuopt/index.html |
| All Resources | [docs/05-resources.md](./05-resources.md) |

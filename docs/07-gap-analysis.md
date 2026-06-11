# 07 — Gap Analysis

> This is the primary research output of this project. A **gap** is a point in the workflow where NVIDIA's official documentation is absent, insufficient, or stops short of what a developer actually needs to proceed.

---

## Why This Matters

NVIDIA Omniverse and Isaac Sim are powerful tools. The official documentation covers each component well. However, the documentation is primarily **component-level** — it explains how the Warehouse Creator works, how cuOpt works, how the ROS 2 bridge works. Documentation on how to connect them together, what to do when they behave unexpectedly, or how to run them without high-end local hardware is limited.

This gap analysis documents where that guidance is currently limited — based on 14 weeks of hands-on experience.

---

## Gap Register

| ID | Gap | Stage | Severity | What This Means for You |
|----|-----|-------|----------|------------------------|
| G-01 | Isaac Sim provides limited diagnostic output when it fails due to hardware incompatibility | Environment Setup | 🔴 Critical | Hardware requirements are documented but there is no lightweight alternative for learning or testing. If your hardware does not meet the requirements, a cloud GPU is needed before you can proceed. Directly addresses RQ-02. |
| G-02 | A guided workflow for transitioning from the NVIDIA warehouse blueprint template to a custom, arbitrary factory floor plan is not currently available | Scene Construction | 🔴 Critical | NVIDIA provides the warehouse tools working with their own examples. A workflow for substituting a custom layout is an area where documentation is currently limited. Directly addresses RQ-01. |
| G-03 | Cloud-based deployment documentation for Isaac Sim is limited for developers without access to high-end local hardware | Environment Setup | 🔴 Critical | Cloud deployment guides exist but are not consolidated into a single workflow. The risk of GPU unavailability due to chip shortages is worth noting. This project lost nearly 3 weeks to this. Directly addresses RQ-02. |
| G-04 | Documentation on parameterising layout variants and exposing customisation knobs within a USD warehouse scene is currently limited | Scene Construction | 🟡 Significant | NVIDIA's warehouse assets are not structured for editability. USD VariantSets are the right tool for layout parameterisation but warehouse-specific documentation is limited. Addresses RQ-01. |
| G-05 | An integration path between NVIDIA cuOpt route optimisation output and ROS 2 Nav2 goal execution is not currently documented | Fleet Simulation | 🔴 Critical | cuOpt generates optimal routes and Nav2 navigates robots, but the method for connecting the two requires further documentation. This was the final blocker preventing full fleet simulation in this project. Addresses RQ-01 and RQ-02. |

---

## Additional Findings

These emerged from hands-on development and extend the gap analysis:

### Unorganised USD Prim Hierarchy
All tested NVIDIA warehouse assets have flat USD stage hierarchies where walls, ceiling, floor, and equipment share the same level. This makes targeted editing more challenging. See [GOTCHA-006](./06-gotchas.md).

### Warehouse Scaling
Proportional scaling of warehouse scenes including internal assets requires additional steps beyond scaling the building shell. See [GOTCHA-007](./06-gotchas.md).

### Cloud GPU Availability
Cloud GPU availability for research projects carries inherent risk. This project experienced a 3-week outage due to global chip shortage. See [GOTCHA-008](./06-gotchas.md).

---

## What Developers Need to Know Before Starting

**Documentation is primarily component-level.** Excellent guides exist for each individual tool. Integration guides connecting them together are an area where additional documentation would benefit developers. Expect to spend time in the NVIDIA Developer Forums and through hands-on experimentation.

**Resources outside official docs are limited.** YouTube tutorials exist but are sparse for warehouse simulation work. The NVIDIA Developer Forums is the most valuable external resource.

**The cuOpt ↔ Nav2 bridge is the critical unsolved problem.** If you are building on this work, solving Gap G-05 is the highest-priority next step. The Nav2 Simple Commander Python API is the likely starting point: https://docs.nav2.org/commander_api/index.html

---

## Developer Roadmap

For anyone building on this work:

### Immediate Priority
- Implement the cuOpt ↔ Nav2 bridge (Gap G-05) using `nav2_simple_commander`
- Consolidate the AWS cloud deployment process into a single guide (Gap G-03)

### Medium Term
- Build a parameterised USD scene using VariantSets for layout switching (Gap G-04)
- Develop a KPI capture pipeline from Nav2 telemetry
- Test against the NVIDIA Mega Blueprint as a higher-level framework

### Long Term
- Validate against a real factory floor plan from CAD data
- Multi-robot fleet coordination with task assignment
- Real-time data integration

---

## References

All gaps were validated against:
- NVIDIA Isaac Sim official documentation: https://docs.isaacsim.omniverse.nvidia.com/latest/index.html
- NVIDIA Developer Forums: https://forums.developer.nvidia.com/c/omniverse/isaac-sim/
- OpenUSD Working Group specifications: https://openusd.org/docs/index.html
- Direct hands-on empirical discovery during the 14-week project

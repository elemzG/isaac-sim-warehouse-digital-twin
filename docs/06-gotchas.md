# 08 — Gotchas ⚠️

> **Read this before you start.** Every entry here came from direct hands-on experience during this 14-week project. Each one cost significant time to diagnose. The goal is to save you that time.

---

## Index

| ID | Title | Area | Severity |
|----|-------|------|----------|
| [GOTCHA-001](#gotcha-001) | Isaac Sim fails silently on incompatible GPU | Environment | 🔴 Blocker |
| [GOTCHA-002](#gotcha-002) | Isaac Sim cannot run on standard laptops | Environment | 🔴 Blocker |
| [GOTCHA-003](#gotcha-003) | NVIDIA Asset Browser not visible by default | Environment | 🟡 Time sink |
| [GOTCHA-004](#gotcha-004) | Isaac Sim on AWS is a manual, multi-step process | Environment | 🟡 Time sink |
| [GOTCHA-005](#gotcha-005) | Modular Warehouse Creator requires reading docs first | Scene Construction | 🟡 Time sink |
| [GOTCHA-006](#gotcha-006) | USD prims in NVIDIA warehouse assets are not organised | Scene Construction | 🔴 Blocker |
| [GOTCHA-007](#gotcha-007) | Warehouse scaling does not propagate to internal assets | Scene Construction | 🟡 Time sink |
| [GOTCHA-008](#gotcha-008) | AWS GPU unavailable due to global chip shortage | Infrastructure | 🔴 Blocker |

---

## GOTCHA-001
**Isaac Sim fails silently on incompatible GPU**

- **Discovered:** Week 3
- **Symptom:** Isaac Sim opens but crashes or produces no useful output. No error message indicates the hardware is the cause.
- **Root Cause:** Isaac Sim requires a dedicated NVIDIA RTX GPU with minimum 8 GB VRAM. The installer does not warn you before installing on non-compliant hardware.
- **Fix:** Verify hardware against the official requirements before installing anything. If your hardware does not qualify, see GOTCHA-002.
- **Official Reference:** https://docs.isaacsim.omniverse.nvidia.com/latest/index.html

---

## GOTCHA-002
**Isaac Sim cannot run on standard laptops — cloud deployment required**

- **Discovered:** Week 3–4
- **Symptom:** Isaac Sim installer completes but the application cannot launch on a standard laptop with integrated graphics.
- **Root Cause:** Most laptops do not have a dedicated NVIDIA RTX GPU. NVIDIA's documentation does not prominently highlight this before you invest time in installation.
- **Fix:** Use a cloud GPU instance. Options include NVIDIA Brev, AWS EC2 (g4dn.xlarge or g5.xlarge), or institutional cloud access if available. Set this up in Week 1 — not later. Approval processes take time.
- **Impact on this project:** Caused a 2-week delay at the start.
- **Official Reference:** https://docs.isaacsim.omniverse.nvidia.com/4.5.0/installation/install_advanced_cloud_setup_aws.html

---

## GOTCHA-003
**NVIDIA Asset Browser not visible by default**

- **Discovered:** Week 4
- **Symptom:** The NVIDIA Assets tab referenced in NVIDIA training courses is not visible in the Isaac Sim UI. The course assumes it is already present.
- **Root Cause:** Requires the `omni.kit.browser_asset` extension to be manually enabled. The course only reveals how to find it in a later module after already requiring it.
- **Fix:** Go to `Window > Extensions`, search for `omni.kit.browser_asset`, install and enable it. The tab will then appear at `Window > Browsers > NVIDIA Assets`.

---

## GOTCHA-004
**Isaac Sim on AWS is a manual, multi-step process — allow a full day**

- **Discovered:** Week 5
- **Symptom:** The standard Isaac Sim installation steps do not work directly on an AWS instance.
- **Root Cause:** Cloud deployment documentation is spread across multiple pages. The process is more involved than a standard workstation install.
- **Fix:** Read the complete AWS deployment guide before starting. Do not skip steps. Allow at least one full day for combined AWS setup and Isaac Sim installation.
- **Official Reference:** https://docs.isaacsim.omniverse.nvidia.com/4.5.0/installation/install_advanced_cloud_setup_aws.html

---

## GOTCHA-005
**Modular Warehouse Creator — walls cannot be created without reading documentation first**

- **Discovered:** Week 5 | **Resolved:** Week 6
- **Symptom:** Attempting to use the Modular Warehouse Creator without reading the documentation produces no walls. No error message is shown.
- **Root Cause:** The tool requires a specific workflow to be followed in order. There is no in-app guidance.
- **Fix:** Read the complete Warehouse Creator extension documentation before attempting to use the tool.
- **Official Reference:** https://docs.isaacsim.omniverse.nvidia.com/4.5.0/digital_twin/warehouse_logistics/ext_omni_warehouse_creator.html

---

## GOTCHA-006
**USD prims in all NVIDIA warehouse assets are not organised by category**

- **Discovered:** Week 6
- **Symptom:** Opening any NVIDIA warehouse scene (Simple Warehouse, Isaac Warehouse, or Modular Warehouse Creator output) shows a flat, unorganised USD stage hierarchy. Walls, ceiling, floor, and equipment share the same level with generic names.
- **Root Cause:** NVIDIA warehouse assets are built for visual demonstration, not for editability. The Modular Warehouse Creator generates the same flat structure.
- **Impact:** Very difficult to select and edit specific elements. You cannot easily move all walls or replace the ceiling without hunting through hundreds of unnamed prims.
- **Workaround:** Manually reorganise prims after import, or accept the flat structure and edit by selecting individual prims in the viewport.
- **Official Reference:** https://docs.isaacsim.omniverse.nvidia.com/4.5.0/digital_twin/warehouse_logistics/tutorial_static_assets.html

---

## GOTCHA-007
**Scaling a warehouse building does not automatically scale internal assets**

- **Discovered:** Week 7
- **Symptom:** Scaling the warehouse shell (e.g. 2x or 3x) scales the building correctly but all internal assets remain at their original size.
- **Root Cause:** The building shell and internal assets are independent USD prims with no parent-child scaling relationship.
- **Impact:** Every shelf, box, and piece of equipment must be manually rescaled to match. For large scenes this is very time-consuming.
- **Workaround:** Group all assets under a parent Xform prim before scaling, so they scale together.

---

## GOTCHA-008
**AWS GPU unavailable due to global chip shortage**

- **Discovered:** Week 10
- **Symptom:** AWS cloud instance cannot be connected to. GPU resources unavailable on shared infrastructure.
- **Root Cause:** Global GPU chip shortage (2025–2026) limited cloud GPU availability. RMIT RACE Team AWS instances were at capacity.
- **Impact:** All Isaac Sim development blocked for nearly 3 weeks (Weeks 10–12). ROS 2 integration was only completed in the final weeks of the project as a result.
- **Lesson:** Cloud GPU availability is not guaranteed. This risk is not prominently covered in NVIDIA documentation. Always have a fallback option (personal AWS account or NVIDIA Brev) from the start of the project.

---

*Last updated: Week 14*

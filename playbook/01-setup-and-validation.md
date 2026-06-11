# Playbook Step 1 — Setup & Validation

> **Goal:** A working Isaac Sim + ROS 2 + cuOpt environment ready for scene construction.
> **Honest time estimate:** 1–2 days minimum. If using institutional cloud, add 1–2 weeks for access approval.

---

## Checklist

- [ ] GPU confirmed against official requirements
- [ ] Cloud instance provisioned (if needed)
- [ ] Isaac Sim installed and launches
- [ ] ROS 2 Jazzy installed
- [ ] cuOpt Docker container pulled
- [ ] NVIDIA Asset Browser extension enabled

---

## Official Guides — Follow These

| Step | Official Guide |
|------|---------------|
| Isaac Sim installation | https://docs.isaacsim.omniverse.nvidia.com/latest/index.html |
| Isaac Sim on AWS | https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/install_advanced_cloud_setup_aws.html |
| ROS 2 installation | https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/install_ros.html |
| cuOpt setup | https://docs.isaacsim.omniverse.nvidia.com/5.1.0/features/warehouse_logistics/logistics_tutorial_cuopt.html |

---

## What This Project Found During Setup

- **Hardware blocker is the most common first issue** — verify GPU before installing anything. See [GOTCHA-001](../docs/06-gotchas.md) and [GOTCHA-002](../docs/06-gotchas.md)
- **AWS installation takes a full day** — not a quick process. See [GOTCHA-004](../docs/06-gotchas.md)
- **NVIDIA Asset Browser is not visible by default** — must enable manually. See [GOTCHA-003](../docs/06-gotchas.md)
- **Cloud GPU availability is not guaranteed** — have a backup option. See [GOTCHA-008](../docs/06-gotchas.md)

---

## Next Step

→ [Playbook Step 2 — Scene Construction](./02-usd-scene-construction.md)

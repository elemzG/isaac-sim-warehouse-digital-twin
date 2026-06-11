# Playbook Step 3 — AMR Fleet Configuration

> **Goal:** Nova Carter navigating in the warehouse via ROS 2 Nav2, and cuOpt generating optimal routes.
> **Current status:** Both systems confirmed working independently. The bridge between them is the remaining open problem — see [Gap G-05](../docs/07-gap-analysis.md).

---

## Official Guides — Follow These

| Topic | Official Guide |
|-------|---------------|
| ROS 2 Navigation with Nova Carter | https://docs.isaacsim.omniverse.nvidia.com/latest/ros2_tutorials/tutorial_ros2_navigation.html |
| ROS 2 Bridge Overview | https://docs.isaacsim.omniverse.nvidia.com/5.1.0/ros2_tutorials/ros2_landing_page.html |
| Occupancy Map Generation | https://docs.isaacsim.omniverse.nvidia.com/5.1.0/features/ext_omni_isaac_occupancy_map.html |
| cuOpt with Isaac Sim | https://docs.isaacsim.omniverse.nvidia.com/5.1.0/features/warehouse_logistics/logistics_tutorial_cuopt.html |
| Nav2 Documentation | https://docs.nav2.org/ |

---

## Part A — ROS 2 Nav2 Navigation

### What Was Confirmed Working in This Project

- Occupancy map generated for custom warehouse layout ✅
- ROS 2 workspace sourced and Nav2 stack launched ✅
- RViz2 running with costmap visible ✅
- Nova Carter navigating to Nav2 goals ✅

**ROS 2 workspace path used in this project:**
```
/home/ubuntu/IsaacSim-ros_workspaces/jazzy_ws
```

See demo screenshots:
- `demo/05_rviz2_navigation_active.png`
- `demo/10_rviz2_costmap_nova_carter.png`
- `demo/06_occupancy_map.png`

---

## Part B — cuOpt Route Optimisation

### What Was Confirmed Working in This Project

- cuOpt server running via Docker on port 8000 ✅
- Waypoint graph loaded: **91 nodes, 314 edges** ✅
- Orders loaded: **20 tasks** ✅
- Vehicles loaded: **2 vehicles** ✅
- Solution generated: **cost 322.6962556838989** ✅

See demo screenshots:
- `demo/02_cuopt_problem_setup.png`
- `demo/03_cuopt_waypoint_graph.png`
- `demo/04_cuopt_solution_output.png`

---

## The Missing Bridge — Gap G-05

cuOpt produces an optimal visit sequence. Nav2 navigates the robot. **There is no documented integration between the two.**

This was the final blocker preventing full fleet simulation in this project. A future developer solving this should start with the Nav2 Simple Commander Python API:
> https://docs.nav2.org/commander_api/index.html

The NVIDIA Developer Forums is the best place to search for community attempts at this integration:
> https://forums.developer.nvidia.com/c/omniverse/isaac-sim/

---

## Important Note

ROS 2 was implemented in the **final weeks of this project** — not because it was left last by design, but because nearly 3 weeks of AWS access was lost due to global GPU chip shortage. See [GOTCHA-008](../docs/06-gotchas.md).

# 05 — Fleet Simulation

This page documents the fleet simulation workflow used in this project — what worked, what did not, and what is still missing. It points to official documentation and adds findings not covered there.

---

## Official Documentation

| Topic | Link |
|-------|------|
| ROS 2 Navigation with Nova Carter | https://docs.isaacsim.omniverse.nvidia.com/4.5.0/ros2_tutorials/tutorial_ros2_navigation.html |
| ROS 2 Bridge Overview | https://docs.isaacsim.omniverse.nvidia.com/4.5.0/ros2_tutorials/ros2_landing_page.html |
| cuOpt with Isaac Sim | https://docs.isaacsim.omniverse.nvidia.com/4.5.0/digital_twin/warehouse_logistics/logistics_tutorial_cuopt.html |
| Nav2 Documentation | https://docs.nav2.org/ |

---

## What Was Achieved in This Project

### ROS 2 Nav2 Navigation ✅
Nova Carter was successfully navigating in the warehouse scene using ROS 2 Nav2. This required:

1. Generating a new occupancy map for the custom warehouse layout
2. Sourcing the ROS 2 workspace
3. Launching the Nav2 navigation stack
4. Opening RViz2 to visualise and send navigation goals

**Confirmed working state:**
- Navigation: active
- Localisation: active
- Costmap generated from warehouse geometry
- Nova Carter moving to Nav2 goals

See `demo/05_rviz2_navigation_active.png` and `demo/10_rviz2_costmap_nova_carter.png`.

### NVIDIA cuOpt Routing ✅
cuOpt was successfully deployed via Docker and connected to Isaac Sim. The routing problem was configured with:

- **Waypoint graph:** 91 nodes, 314 edges
- **Orders:** 20 tasks
- **Vehicles:** 2
- **Solution cost:** 322.6962556838989

See `demo/02_cuopt_problem_setup.png`, `demo/03_cuopt_waypoint_graph.png`, and `demo/04_cuopt_solution_output.png`.

---

## What Was NOT Achieved — The Missing Bridge

cuOpt produces an optimal visit sequence. Nav2 navigates a robot to a goal. **There is no documented integration between the two.**

This means:
- cuOpt tells you the optimal order to visit waypoints
- Nav2 can navigate the robot between waypoints
- But connecting cuOpt's output to Nav2's input requires custom code that nobody has published

This is **Gap G-05** — the most significant unresolved finding of this project.

A future developer solving this would need to write a ROS 2 node that reads cuOpt's solution and sends sequential Nav2 goals. The Nav2 Simple Commander Python API would be the starting point:
- https://docs.nav2.org/commander_api/index.html

---

## Occupancy Map

The occupancy map generated in this project is shown in:
- `demo/06_occupancy_map.png` — full warehouse map
- `demo/07_occupancy_map_shelves.png` — shelf pattern view

The occupancy map is generated from the warehouse geometry automatically when using the ROS 2 Nova Carter example. For a custom layout, a new map must be generated.

---

## Important Notes for New Developers

- **ROS 2 was implemented in the final weeks of this project** — due to nearly 3 weeks of lost AWS access, this was the last component to be implemented
- **cuOpt and Nav2 work independently** — do not assume they are connected out of the box
- **The NVIDIA Developer Forums** is the best resource for ROS 2 + Isaac Sim integration issues: https://forums.developer.nvidia.com/c/omniverse/isaac-sim/

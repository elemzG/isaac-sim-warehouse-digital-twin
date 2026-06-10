# 04 — Scene Construction

This page documents how the warehouse scene was built in this project and what was discovered during the process. It does not replace the official documentation — it points to it and adds what the official docs do not cover.

---

## Official Documentation

| Topic | Link |
|-------|------|
| Warehouse Creator Extension | https://docs.isaacsim.omniverse.nvidia.com/4.5.0/digital_twin/warehouse_logistics/ext_omni_warehouse_creator.html |
| Static Assets and SimReady Content | https://docs.isaacsim.omniverse.nvidia.com/4.5.0/digital_twin/warehouse_logistics/tutorial_static_assets.html |
| Nova Carter ROS 2 Navigation | https://docs.isaacsim.omniverse.nvidia.com/4.5.0/ros2_tutorials/tutorial_ros2_navigation.html |

---

## Base Scene Used in This Project

This project used the **ROS 2 Nova Carter navigation example** as the base scene — not the NVIDIA warehouse blueprint. This was chosen because:

- It comes with ROS 2 bridge already configured
- It provides a working occupancy map setup out of the box
- RViz2 integration works without additional configuration

The Nova Carter example is found in Isaac Sim under:
```
Isaac Examples > ROS2 > Navigation > Nova Carter
```

---

## What Was Added on Top

The following NVIDIA assets were added to the base scene:

- **Shelves and boxes** — from the NVIDIA SimReady asset library (`Isaac > Environments > Simple_Warehouse`)
- **Conveyor system** — using the Warehouse Logistics Utilities extension
- **Additional warehouse equipment** — from the NVIDIA Asset Browser

All assets were positioned using USD Xform transforms (translation and rotation) in the Isaac Sim Property panel.

See demo screenshots:
- `demo/01_conveyor_warehouse_scene.png` — final scene with conveyor
- `demo/08_warehouse_with_shelves.png` — warehouse with shelf layout
- `demo/09_nova_carter_conveyor.png` — Nova Carter with conveyor

---

## What This Project Found (Not in Official Docs)

### NVIDIA Assets Use Centimetre Scale
Assets from the NVIDIA Asset Browser use centimetre scale by default while Isaac Sim uses metres. Assets will appear very small if this is not accounted for.

**→ See [GOTCHA-005](./06-gotchas.md)**

### USD Prim Hierarchy Is Unorganised
All tested NVIDIA warehouse assets — Simple Warehouse, Isaac Warehouse, and Modular Warehouse Creator output — have flat, unorganised USD stage hierarchies. Walls, ceiling, floor, and equipment share the same level with no logical grouping. This makes targeted editing very difficult.

**→ See [GOTCHA-006](./06-gotchas.md)**

### Warehouse Scaling Does Not Propagate to Internal Assets
Scaling the warehouse building does not automatically scale internal assets. Every shelf, box, and piece of equipment must be manually rescaled.

**→ See [GOTCHA-007](./06-gotchas.md)**

### Modular Warehouse Creator Requires Reading Documentation First
The Warehouse Creator tool will not work as expected if you attempt to use it without reading the official documentation first. Walls cannot be created without following the specific workflow.

**→ See [GOTCHA-005](./06-gotchas.md)**

---

## Available Warehouse Starting Points

Three options were tested in this project:

| Option | Description | Recommendation |
|--------|-------------|----------------|
| ROS 2 Nova Carter example | Minimal warehouse with ROS 2 already configured | ✅ Best starting point if you need Nav2 |
| Simple Warehouse | Clean empty scene | Good for custom builds |
| Isaac Warehouse | Pre-populated with racks and boxes | Good for visual realism |
| Modular Warehouse Creator | Build from scratch using the extension | Use only after reading official docs |

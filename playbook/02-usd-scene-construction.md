# Playbook Step 2 — Scene Construction

> **Goal:** A warehouse scene with shelves, boxes, conveyor, and Nova Carter placed and positioned.

---

## Official Guides — Follow These

| Topic | Official Guide |
|-------|---------------|
| Static Warehouse Assets | https://docs.isaacsim.omniverse.nvidia.com/4.2.0/features/warehouse_logistics/tutorial_static_assets.html |
| Warehouse Creator Extension | https://docs.isaacsim.omniverse.nvidia.com/4.2.0/features/warehouse_logistics/index.html |
| Nova Carter Assets | https://docs.isaacsim.omniverse.nvidia.com/latest/assets/nova_carter_landing_page.html |

---

## Base Scene Used in This Project

This project used the **ROS 2 Nova Carter navigation example** as the base scene:
```
Isaac Examples > ROS2 > Navigation > Nova Carter
```

This was chosen over the NVIDIA warehouse blueprint because it comes with ROS 2 bridge already configured and occupancy map generation ready to use.

---

## What Was Added on Top

- NVIDIA SimReady shelves and boxes from the Asset Browser (`Isaac > Environments > Simple_Warehouse`)
- Conveyor system using the Warehouse Logistics Utilities extension
- Assets positioned using USD Xform transforms in the Property panel

---

## What This Project Found (Not in Official Docs)

- **NVIDIA Assets are centimetre-scale by default** — assets appear very small if scale is not adjusted
- **USD prim hierarchy is unorganised** in all NVIDIA warehouse assets — makes editing difficult. See [GOTCHA-006](../docs/06-gotchas.md)
- **Warehouse scaling does not propagate to internal assets** — every shelf and box must be rescaled manually. See [GOTCHA-007](../docs/06-gotchas.md)
- **Modular Warehouse Creator requires reading docs first** — will not work as expected without following the specific workflow. See [GOTCHA-005](../docs/06-gotchas.md)

---

## Available Warehouse Starting Points

| Option | Best For |
|--------|---------|
| ROS 2 Nova Carter example | ✅ Best if you need Nav2 and occupancy map |
| Simple Warehouse | Clean empty scene for custom builds |
| Isaac Warehouse | Pre-populated scene for visual realism |
| Modular Warehouse Creator | Custom builds — read official docs first |

---

## Next Step

→ [Playbook Step 3 — AMR Fleet Configuration](./03-amr-fleet-configuration.md)

# 10 — Compute Sizing

> Hardware is the first blocker most developers will hit. This page documents what was used on this project and what options are available.

---

## Official Requirements

Before anything else, check the official Isaac Sim system requirements:
> https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/requirements.html

---

## Confirmed Working Hardware (This Project)

All simulation work was done on **NVIDIA L40S (40 GB VRAM)** via RMIT RACE Team AWS cloud infrastructure.

**Observed resource usage from project screenshots:**

| Scene | GPU VRAM Used | Process Memory | FPS |
|-------|--------------|----------------|-----|
| Conveyor warehouse scene | 3.0 GB | 9.6 GB | 119 |
| Warehouse with waypoint graph | 4.2 GB | 9.8 GB | 118 |
| Large warehouse building | 4.9 GB | 12.2 GB | 59 |
| Dense shelf warehouse | 4.7 GB | 18.6 GB | 59 |

The L40S is more than sufficient for this project. An RTX 4080 or A4500 (16 GB) would be comfortable for everything done here.

---

## GPU Recommendations

| Tier | GPU | VRAM | Notes |
|------|-----|------|-------|
| Minimum | NVIDIA RTX 3080 | 8 GB | Functional for simple scenes |
| Recommended | NVIDIA RTX 4080 / A4500 | 16 GB | Comfortable for all scenes in this project |
| Used in this project | NVIDIA L40S | 40 GB | Cloud via RMIT RACE Team AWS |

---

## Cloud Options

If local hardware is insufficient, these cloud options were evaluated:

| Option | GPU | VRAM | Est. Cost | Notes |
|--------|-----|------|-----------|-------|
| NVIDIA Brev | Various (RTX 4090 / A100 / H100) | 24–80 GB | Pricing varies — login required | Native Omniverse support |
| AWS g4dn.xlarge | NVIDIA T4 | 16 GB | ~$0.526/hr | Budget option — manual setup required |
| AWS g5.xlarge | NVIDIA A10G | 24 GB | ~$1.006/hr | Recommended AWS option |
| Institutional cloud (e.g. RMIT RACE Team) | TBC | TBC | Free | Best option if available — apply early |

---

## ⚠️ Important Warning — Cloud GPU Availability

This project lost nearly **3 weeks of development time** (Weeks 10–12) because the RMIT RACE Team AWS GPU instance was unavailable due to global GPU chip shortage. Cloud GPU availability is **not guaranteed**.

NVIDIA's documentation does not mention this risk. See [GOTCHA-008](./08-gotchas.md).

**Recommendation:** Always have a fallback option. If using institutional cloud, also set up a personal NVIDIA Brev or AWS account as a backup.

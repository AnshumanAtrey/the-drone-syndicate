# Phase 3 — Military Payload Systems

**Goal:** Add mission-specific payloads to the Phase 1/2 drone platform. These are the payload categories that defense contractors (ideaForge, Adani Defence, BEL, General Atomics, Elroy Air) actually sell to armed forces worldwide.

> **LEGAL NOTE:** All variants are **legal for college research prototyping**. Actual military deployment requires DGCA certification + MoD procurement. Chemical, biological, and explosive payloads are strictly prohibited (CWC, Arms Act). These prototypes demonstrate the engineering — sensors, release mechanisms, communication — not live weapons.

## Variants (Military-Focused)

| File | Military Application | Approx Additional Cost | Inspired By |
|------|---------------------|----------------------|-------------|
| [variant-1-isr-sensor-pod.md](variant-1-isr-sensor-pod.md) | Surveillance — EO/IR gimbal + thermal | ~Rs.13K-50K over Phase 1 | ideaForge SWITCH, Elbit Hermes |
| [variant-2-comms-relay-mesh.md](variant-2-comms-relay-mesh.md) | Airborne comms relay for troops | ~Rs.5K-12K over Phase 1 | Military MANET, Rajant mesh |
| [variant-3-counter-drone-interceptor.md](variant-3-counter-drone-interceptor.md) | Intercept & capture enemy drones | ~Rs.15K-30K over Phase 1 | Fortem DroneHunter, DRDO anti-drone |
| [variant-4-military-resupply.md](variant-4-military-resupply.md) | Forward base logistics / ammo resupply | ~Rs.12K-25K over Phase 1 | Elroy Air Chaparral, KARGO UAS |
| [variant-5-battlefield-sar.md](variant-5-battlefield-sar.md) | Find wounded + drop medevac supplies | ~Rs.12K-20K over Phase 1 | DJI Enterprise SAR, NDRF ops |
| [variant-6-ew-decoy-payload.md](variant-6-ew-decoy-payload.md) | Electronic decoy / countermeasure dispenser | ~Rs.15K-25K over Phase 1 | Leonardo BriteCloud, chaff/flare pods |

## Why These Categories
These map directly to what Indian armed forces procure:
- **ISR:** Indian Army's largest drone spend — ideaForge SWITCH 1.0 UAV (Rs.30L/unit) is primarily ISR
- **Comms Relay:** Indian Army uses drones as radio relays in Ladakh/Siachen where ground comms fail
- **Counter-Drone:** DRDO + BEL deployed anti-drone systems at Red Fort, airports, military bases
- **Resupply:** Indian Army trialed drone logistics in Ladakh (2022), Navy uses drones for ship-to-shore
- **Battlefield SAR:** NDRF uses drones for disaster SAR; military application is finding wounded in combat zones
- **EW/Decoy:** Indian Air Force and Navy require EW capabilities; DRDO develops indigenous EW systems

## Prerequisites
- Working Phase 1 drone (Variant 2 Jetson Nano or Variant 4 Orin recommended)
- S500 or larger frame (F450 too small for most payloads)
- 4S 5000mAh+ battery for adequate flight time under load

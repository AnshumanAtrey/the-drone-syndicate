# Variant 5 — Fiber-Optic Tethered Drone (Unjammable)

**Total Approx Cost: Rs. 50,000 - 70,000** (fiber spool is the biggest cost variable)

Inspired by Russian/Ukrainian fiber-optic FPV drones deployed since 2024. Uses a physical fiber-optic cable for video/control instead of RF — **completely immune to EMP jamming and electronic warfare**. Trade-off: limited range to fiber spool length (1-5km). Indian supplier **FlySpark.in** sells drone-grade fiber spools.

> **Ref:** Fiber-optic drones first fielded in Ukraine (Spring 2024). US Navy tested in Silent Swarm 25 exercise. Patent: US10090929B2 (Drone-Based Radio-Over-Fiber System). Indian supplier: [FlySpark.in](https://flyspark.in)

## Components

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | Flight Controller | Pixhawk 2.4.8 PX4 32-Bit | 5,500 - 8,514 | Robocraze |
| 2 | Frame | S500 Carbon Fiber w/ Landing Gear | 3,419 | Robocraze |
| 3 | Motors x4 | A2212 920KV BLDC | 1,600 | Robocraze |
| 4 | ESC x4 | SimonK 30A | 1,288 | Robocraze |
| 5 | GPS Module | NEO M8N with Compass | 1,084 - 1,899 | Robokits |
| 6 | Battery | 4S 5000mAh LiPo | 4,500 | Amazon.in |
| 7 | Companion Computer | Raspberry Pi 4 (4GB) | 9,564 | Robocraze |
| 8 | Camera | Pi Camera Module 3 (12MP) | 3,249 | Robocraze |
| 9 | **Fiber Optic Spool** | G657A2 single-mode 1-2km w/ canister | 6,700 - 25,000 | Alibaba (cheapest kit) / FlySpark.in (Rs.52K+) |
| 10 | **Fiber Media Converter x2** | 10/100M or 1G Ethernet-over-fiber (pair) | 3,000 - 8,000 | IndiaMART / Amazon.in |
| 11 | **SFP Transceiver Module** | 1G SFP SX/LX module | 700 - 2,000 | IndiaMART |
| 12 | Obstacle Sensors | HC-SR04 Ultrasonic x2 | 152 | Robocraze |
| 13 | Power Distribution | PDB-XT60 + 5V UBEC | 665 | Robocraze |
| 14 | Propellers | 1045 Props (3 pairs) | 250 | Robocraze |
| 15 | Custom Spool Mount | 3D printed fiber spool holder | 500 (printing) | Local 3D print |

## How It Works
1. Ground station connects to fiber media converter (Ethernet -> Fiber)
2. Fiber spool mounted under drone, cable pays out as drone flies
3. Drone-side fiber converter receives signal, feeds to RPi via Ethernet
4. RPi runs MAVProxy, relays commands to Pixhawk via MAVLink UART
5. Video from Pi Camera streams back over fiber to ground station
6. **Zero RF emission** = invisible to RF detection, immune to jamming

## Key Features
- **100% jam-proof** — physical cable, no RF to intercept or jam
- **Zero latency** — fiber optic gives <1ms latency (vs 30-80ms on 4G)
- **No signal loss** — connection guaranteed as long as fiber is intact
- **Covert** — no RF signature, harder to detect electronically
- **High bandwidth** — fiber supports HD video + telemetry simultaneously
- **Range:** 1-5km depending on fiber spool (can be extended)

## Limitations
- **Tethered** — range limited to fiber length, cable can snag on obstacles
- Fiber spool adds ~200-500g weight
- Cable management is the main engineering challenge
- Cannot be controlled over internet (local only, by design)
- Best for: perimeter surveillance, fixed-area monitoring, research into jam-proof systems

## College Research Angle
- Compare latency: fiber vs 4G vs 433MHz telemetry vs 2.4GHz RC
- Test jamming resilience: use a 2.4GHz jammer (legal in lab), show fiber drone unaffected
- Publish paper on: "Jam-Resistant UAV Communication Using Fiber-Optic Tethering"

# Variant 1 — ISR Sensor Pod (Intelligence, Surveillance, Reconnaissance)

**Additional Cost Over Phase 1: Rs. 10,000 - 50,000** (depends on thermal camera tier)

The #1 military drone payload worldwide. Every armed force buys ISR drones first. A stabilized camera gimbal with thermal + optical feeds for day/night surveillance, target tracking, and battlefield awareness. This is what ideaForge SWITCH, Elbit Hermes 450, and IAI Heron carry.

> **Ref:** ideaForge SWITCH 1.0 is Indian Army's primary tactical ISR drone (Rs.100+ crore contracts). Carries 25X zoom day camera + 640x480 thermal. Israeli Hermes/Heron carry Rafael TOPLITE EO/IR turret. DRDO TAPAS-BH-201 (Rustom-II) carries 350kg of EO/SAR/ELINT payloads. Adani Drishti-10 Starliner delivered to Indian Navy (450kg payload, 36hr endurance).

## Component Tiers

### Tier 1: Budget Research (~Rs.13,500 added)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | **Servo Pan-Tilt** | 2x MG996R servo bracket | 800 - 1,200 | Robocraze |
| 2 | **Optical Camera** | Pi Camera Module 3 (12MP, autofocus) | 3,249 | Robocraze |
| 3 | **Thermal Camera** | MLX90640 IR Array (32x24, 110deg FOV) | 4,589 - 5,624 | Robocraze |
| 4 | **IR Illuminator** | 850nm IR LED array (covert night vision) | 500 - 800 | Amazon.in |
| 5 | **Video Transmitter** | 5.8GHz 600mW FPV TX | 1,500 - 2,500 | Robocraze |
| 6 | **MicroSD Card** | 128GB Class 10 (recording) | 800 | Amazon.in |

### Tier 2: Mid-Range (~Rs.35-43K added)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | **3-Axis Gimbal + Camera** | **SIYI ZR10** — 2K 4MP, 30X hybrid zoom, 10X optical, 3-axis stabilized, night vision | 43,244 | Robokits.co.in |
| 2 | **OR: Dual-Sensor Pod** | **Skydroid C12** — Thermal + 2K HD, dynamic tracking, 3-axis gimbal | 35,900 | Robokits.co.in |
| 3 | **Thermal Upgrade** | FLIR Lepton 2.5 (80x60 pixels, true LWIR) | 15,000 - 22,000 | Tanotis / MG Super Labs |

### Tier 3: Professional Research (~Rs.2-5 lakh added)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | **SIYI ZT30 Four-Sensor** | 4K zoom + 640x512 thermal + laser rangefinder (1200m) + wide-angle, 30X optical | 5,25,000 | Robokits.co.in |
| 2 | **FLIR Lepton 3.5** | 160x120 radiometric LWIR thermal | 25,000 - 35,000 | GroupGets / DigiKey India |

## ISR Capabilities

### Daytime Surveillance
- 12MP Pi Camera 3 with autofocus — captures faces at 20-30m, vehicles at 100m+
- 2-axis gimbal keeps image stable during flight maneuvers
- AI object detection (YOLOv5 on Jetson) identifies: persons, vehicles, weapons
- GPS-tagged snapshots sent to command via 4G in real-time

### Night Surveillance
- MLX90640 thermal detects heat signatures through darkness
- 850nm IR LEDs illuminate scene (invisible to naked eye)
- Pi NoIR camera captures IR-illuminated footage
- Thermal overlay on optical feed for enhanced situational awareness

### Target Tracking
- Jetson Nano runs real-time object tracking (SORT/DeepSORT algorithm)
- Operator clicks target on screen, drone autonomously keeps camera locked on target
- Gimbal auto-adjusts as drone moves to maintain target in frame
- Track and log: target position, heading, speed via GPS correlation

### Battlefield Awareness
- Fly autonomous grid pattern over area of interest
- AI generates "activity map" — where people/vehicles are concentrated
- Detect changes between successive flights (vehicle moved, new structure)
- All data geo-tagged and timestamped for intelligence analysis

## Software Stack
- **OpenCV + GStreamer** — camera capture, video pipeline
- **YOLOv5-nano** — object detection (TensorRT on Jetson, 30fps)
- **DeepSORT** — multi-object tracking
- **SimpleBGC** — gimbal stabilization controller
- **MQTT/WebSocket** — real-time video + detection alerts to ground via 4G
- **Custom Python** — ISR mission logic, geo-tagging, recording

## Key Features
- **Day/night ISR** — optical + thermal + IR illumination
- **Gimbal stabilized** — steady image even in wind/maneuvers
- **AI-powered** — auto-detect persons, vehicles, suspicious activity
- **Target tracking** — lock-on and follow a moving target
- **Real-time relay** — live feed to command center anywhere via 4G
- **Compact** — entire pod weighs ~200-350g

## Limitations
- MLX90640 is 32x24 pixels — military-grade FLIR is 640x480 (Rs.2-5 lakh)
- Detection range limited by camera resolution (Pi Camera effective to ~100m)
- 2-axis gimbal (pitch + roll) — military uses 3-axis with pan
- No optical zoom on Pi Camera (need varifocal lens for long range)
- Military ISR drones fly at 200-500m altitude; this prototype works best at 30-80m

## College Research Angle
- Build ISR pod, demonstrate day/night surveillance from drone
- Measure: detection range for person/vehicle at different altitudes
- Compare: thermal-only vs optical-only vs fused detection rates
- Implement target tracking, measure tracking accuracy + lock-on time
- Publish: "Low-Cost AI-Powered ISR Payload for Tactical UAV Surveillance"

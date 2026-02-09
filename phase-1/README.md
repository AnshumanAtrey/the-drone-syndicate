# Phase 1 — Autonomous Drone with Onboard AI

**Goal:** Build a drone that flies autonomously, detects anomalies mid-flight, changes direction on its own, and when jammed/disconnected switches to local AI for decision-making. Controllable over the internet from anywhere (<500ms latency).

## Core Capabilities
- GPS waypoint navigation (ArduPilot/PX4 on Pixhawk)
- Obstacle detection + autonomous direction change (LiDAR / Ultrasonic)
- EMP/jamming failsafe — onboard AI takes full control when connection lost
- Internet control via 4G LTE module (30-80ms latency in India)
- Local AI inference for real-time decision making (YOLO / MobileNet)

## Variants

| File | AI Computer | Frame | Approx Cost | Best For |
|------|-------------|-------|-------------|----------|
| [variant-1-budget-orange-pi.md](variant-1-budget-orange-pi.md) | Orange Pi 5 | F450 | ~Rs.32K | Cheapest with AI NPU |
| [variant-2-midrange-jetson-nano.md](variant-2-midrange-jetson-nano.md) | Jetson Nano 4GB | S500 | ~Rs.56K | Best AI performance/price |
| [variant-3-ultra-budget-rpi.md](variant-3-ultra-budget-rpi.md) | Raspberry Pi 4 | F450 | ~Rs.28K | Absolute minimum spend |
| [variant-4-premium-jetson-orin.md](variant-4-premium-jetson-orin.md) | Jetson Orin Nano | S500 | ~Rs.85K | Serious research / local LLM |
| [variant-5-fiber-optic-unjammable.md](variant-5-fiber-optic-unjammable.md) | Raspberry Pi 4 | S500 | ~Rs.55-70K | 100% jam-proof (fiber tether) |
| [variant-6-gps-denied-vio-slam.md](variant-6-gps-denied-vio-slam.md) | Jetson Nano 4GB | S500 | ~Rs.80-95K | Flies without GPS (VIO/SLAM) |

## Software Stack (Common to all variants)
- **Flight Firmware:** ArduPilot (on Pixhawk)
- **Ground Station:** Mission Planner / QGroundControl
- **Companion Software:** DroneKit-Python / MAVSDK on companion computer
- **AI Models:** YOLOv5-nano / MobileNet-SSD (TensorRT on Jetson, RKNN on Orange Pi)
- **Internet Relay:** MQTT / WebSocket server on companion computer via 4G
- **Communication Protocol:** MAVLink (Pixhawk <-> Companion via UART)

## Buy From (Indian Stores)
- [Robocraze](https://robocraze.com) — Largest selection, authorized RPi seller
- [QuartzComponents](https://quartzcomponents.com) — Cheapest frames/ESCs
- [Robokits](https://robokits.co.in) — GPS, Pixhawk combos
- [ThinkRobotics](https://thinkrobotics.com) — Jetson boards
- [Robu.in](https://robu.in) — Telemetry, misc parts

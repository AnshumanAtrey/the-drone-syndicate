# Variant 1 — Budget Build (Orange Pi 5)

**Total Approx Cost: Rs. 32,000 - 35,000**

Cheapest build with dedicated AI hardware. Orange Pi 5 has a 6 TOPS NPU (RK3588S) for running object detection models locally. Trade-off: RKNN software ecosystem is less mature than NVIDIA.

## Components

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | Flight Controller | Pixhawk 2.4.8 PX4 32-Bit | 5,500 - 8,514 | Robocraze / IndiaMART |
| 2 | Frame | F450 Quadcopter Frame w/ PCB | 449 - 699 | QuartzComponents / Robocraze |
| 3 | Motors x4 | A2212 920KV/1000KV BLDC | 1,600 (4x 400) | Robocraze |
| 4 | ESC x4 | SimonK 30A | 1,288 (4x 322) | Robocraze |
| 5 | GPS Module | NEO M8N with Compass | 1,084 - 1,899 | Robokits / Robocraze |
| 6 | Battery | 3S 2200mAh 40C LiPo | 1,503 | Robocraze |
| 7 | RC Transmitter | FlySky FS-i6 + iA6B Receiver | 4,679 | Robocraze |
| 8 | Telemetry Radio | 3DR 433MHz 500mW (pair) | 2,151 | Robocraze |
| 9 | Companion Computer | **Orange Pi 5 (4GB)** | 6,999 | IndiaMART |
| 10 | Camera | Raspberry Pi Camera V2 (8MP) | 1,882 | Robocraze |
| 11 | 4G Module | EC200U 4G LTE GNSS Modem | 1,988 | Robocraze |
| 12 | Obstacle Sensors | HC-SR04 Ultrasonic x2 | 152 (2x 76) | Robocraze |
| 13 | Power Distribution | PDB-XT60 + 5V UBEC | 665 | Robocraze |
| 14 | Propellers | 1045 Props (2 pairs CW+CCW) | 150 - 200 | Robocraze |
| 15 | Wires/Connectors | XT60, servo wires, heatshrink | 300 - 500 | QuartzComponents |

## Key Features
- **AI:** 6 TOPS NPU runs RKNN-optimized YOLO at ~15-20 FPS
- **CPU:** 8-core RK3588S (4x A76 + 4x A55) — fastest CPU of budget options
- **Autonomy:** ArduPilot handles GPS waypoints, Orange Pi runs anomaly detection
- **Failsafe:** When 4G drops, onboard AI on Orange Pi takes over navigation decisions
- **Internet:** EC200U provides 4G LTE with ~30-80ms latency in urban India
- **Flight Time:** ~12-15 min with 2200mAh 3S (F450 is lightweight)
- **Weight:** Orange Pi 5 weighs only 62g (lighter than Jetson Nano at 140g)

## Limitations
- RKNN toolkit less documented than NVIDIA TensorRT
- No CUDA — must use NPU-specific model conversion pipeline
- F450 frame has limited payload capacity for upgrades
- 2200mAh gives short flight time; upgrade to 3S 5200mAh (+Rs.3,500) for ~20 min

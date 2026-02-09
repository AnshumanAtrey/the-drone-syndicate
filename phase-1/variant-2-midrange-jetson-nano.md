# Variant 2 — Mid-Range Build (Jetson Nano)

**Total Approx Cost: Rs. 55,000 - 60,000**

Best AI performance per rupee. Jetson Nano's 128 CUDA cores + TensorRT run YOLOv5 at 30+ FPS. Mature NVIDIA ecosystem with tons of drone AI tutorials. S500 frame supports heavier payload.

## Components

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | Flight Controller | Pixhawk 2.4.8 PX4 32-Bit | 8,514 | Robocraze |
| 2 | Frame | S500 Carbon Fiber w/ Landing Gear | 3,419 | Robocraze |
| 3 | Motors x4 | A2212 920KV BLDC | 1,800 (4x 450) | Robocraze |
| 4 | ESC x4 | SimonK 30A | 1,288 (4x 322) | Robocraze |
| 5 | GPS Module | SmartElex NEO M9N (multi-GNSS) | 2,099 | Robocraze |
| 6 | Battery | 4S 2200mAh 40C LiPo x2 | 3,948 (2x 1,974) | Robocraze |
| 7 | RC Transmitter | FlySky FS-i6X + iA10B 10CH Rx | 5,109 | Robocraze |
| 8 | Telemetry Radio | 3DR 433MHz 500mW (pair) | 2,151 | Robocraze |
| 9 | Companion Computer | **NVIDIA Jetson Nano 4GB B01** | 17,999 | Robocraze |
| 10 | Camera | Raspberry Pi Camera Module 3 (12MP) | 3,249 | Robocraze |
| 11 | 4G Module | EC200U 4G LTE GNSS Modem | 1,988 | Robocraze |
| 12 | LiDAR | TFMini-S (12m range) | 3,259 | Prayog India |
| 13 | Obstacle Sensors | HC-SR04 Ultrasonic x2 | 152 (2x 76) | Robocraze |
| 14 | Power Distribution | PDB-XT60 + 5V 3A UBEC | 665 | Robocraze |
| 15 | Propellers | 1045 Props (3 pairs CW+CCW) | 250 | Robocraze |
| 16 | Wires/Connectors | XT60, servo wires, heatshrink | 500 | QuartzComponents |

## Key Features
- **AI:** 128 CUDA cores, TensorRT-optimized YOLOv5 at **30+ FPS real-time**
- **GPU:** Maxwell architecture — same ecosystem as cloud NVIDIA GPUs
- **LiDAR:** TFMini-S for forward obstacle detection up to 12m — far better than ultrasonic
- **Autonomy:** Pixhawk runs ArduPilot, Jetson runs DroneKit + AI models via MAVLink
- **Failsafe:** On signal loss, Jetson Nano runs full autonomous navigation + obstacle avoidance
- **Internet:** 4G LTE via EC200U, WebSocket/MQTT relay for global control
- **Camera:** 12MP autofocus Pi Camera 3 for better anomaly detection
- **Flight Time:** ~15-18 min with dual 4S 2200mAh (S500 handles the weight)
- **GPS:** M9N multi-constellation (GPS + GLONASS + BeiDou + Galileo) for better accuracy

## Why Jetson Nano is the Sweet Spot
- 25-30x better AI inference than Raspberry Pi 4
- Native CUDA/cuDNN/TensorRT — most AI frameworks work out of the box
- Runs YOLOv5-nano at 30 FPS (enough for real-time obstacle avoidance)
- Tons of community projects: JetBot, DonkeyCar, NVIDIA Isaac — all transferable
- Can run lightweight decision-making models for autonomous behavior
- JetPack SDK includes pre-built OpenCV with CUDA acceleration
- Power draw: 5-10W (manageable with 4S battery + UBEC)

## Limitations
- Jetson Nano is heavier (140g with heatsink) — needs S500 frame, not F450
- 10W power draw reduces flight time vs lighter computers
- Costs almost double the budget Orange Pi variant
- No built-in WiFi (need USB dongle or rely on 4G module)

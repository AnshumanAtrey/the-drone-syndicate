# Variant 3 — Ultra Budget Build (Raspberry Pi 4)

**Total Approx Cost: Rs. 28,000 - 32,000**

Absolute cheapest autonomous drone with internet connectivity. RPi 4 has no AI accelerator — runs lightweight MobileNet-SSD at 2-5 FPS on CPU only. Best if your primary goal is internet control + GPS autonomy, with basic AI as a bonus.

## Components

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | Flight Controller | Pixhawk 2.4.8 PX4 32-Bit | 5,500 | IndiaMART |
| 2 | Frame | F450 Quadcopter Frame w/ PCB | 449 | QuartzComponents |
| 3 | Motors x4 | A2212 1000KV BLDC | 1,580 (4x 395) | Robocraze |
| 4 | ESC x4 | SimonK 30A | 1,120 (4x 280) | QuartzComponents |
| 5 | GPS Module | NEO M8N with Compass | 1,084 | Robokits |
| 6 | Battery | 3S 2200mAh 40C LiPo | 1,503 | Robocraze |
| 7 | RC Transmitter | FlySky FS-i6 + iA6B Receiver | 4,679 | Robocraze |
| 8 | Telemetry Radio | 3DR 433MHz 500mW (pair) | 2,151 | Robocraze |
| 9 | Companion Computer | **Raspberry Pi 4 Model B (4GB)** | 9,564 | Robocraze |
| 10 | Camera | FPV Mini 600TVL 170-degree | 1,249 | Robocraze |
| 11 | 4G Module | EC200U 4G LTE GNSS Modem | 1,988 | Robocraze |
| 12 | Obstacle Sensors | HC-SR04 Ultrasonic x2 | 152 (2x 76) | Robocraze |
| 13 | Power Distribution | PDB-XT60 + 5V UBEC | 665 | Robocraze |
| 14 | Propellers | 1045 Props (2 pairs) | 150 | Robocraze |
| 15 | Wires/Connectors | XT60, servo wires, misc | 300 | QuartzComponents |

## Key Features
- **Cheapest viable build** — everything from Indian IoT stores
- **AI:** MobileNet-SSD on CPU at 2-5 FPS (basic but functional)
- **Built-in WiFi + BT** — can create hotspot, no need for extra WiFi dongle
- **Massive community** — most drone companion computer tutorials are for RPi
- **Internet:** 4G LTE via EC200U for remote control
- **Failsafe:** On signal loss, RPi runs basic obstacle avoidance using ultrasonic sensors
- **Flight Time:** ~12-15 min (F450 + lightweight RPi at 46g)
- **Easy to program** — Python, DroneKit, ROS all work perfectly

## Optional AI Upgrade
Add a **Google Coral USB Accelerator** (~Rs.5,000-8,000 from Amazon.in) to get:
- 4 TOPS of AI inference
- MobileNet-SSD at 70+ FPS
- YOLOv5-nano at ~15 FPS
- Plugs directly into RPi USB 3.0

## Limitations
- **No GPU/NPU** — AI inference is CPU-only (2-5 FPS without Coral)
- Cannot run YOLO models at usable framerates without Coral accelerator
- Not suitable if real-time AI decision making is critical
- Best suited for: GPS waypoint autonomy + internet control + basic sensor-based avoidance

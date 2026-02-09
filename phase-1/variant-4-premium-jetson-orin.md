# Variant 4 — Premium Research Build (Jetson Orin Nano)

**Total Approx Cost: Rs. 85,000 - 95,000**

Maximum onboard AI power. 67 TOPS from Jetson Orin Nano Super can run YOLOv8 at 40+ FPS on 1080p AND small LLMs (LLaVA-7B) locally for human-like decision making. This is the "thinks like a human" variant — can reason about situations, not just detect objects.

## Components

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | Flight Controller | Holybro Pixhawk 6C w/ PM02 | 33,899 | Robocraze |
| 2 | Frame | S500 Carbon Fiber w/ Landing Gear | 3,419 | Robocraze |
| 3 | Motors x4 | A2212 920KV BLDC | 1,800 (4x 450) | Robocraze |
| 4 | ESC x4 | SimonK 30A | 1,288 (4x 322) | Robocraze |
| 5 | GPS Module | SmartElex NEO M9N (multi-GNSS) | 2,099 | Robocraze |
| 6 | Battery | 4S 5000mAh LiPo | 4,500 | Amazon.in |
| 7 | RC Transmitter | FlySky FS-i6X + iA10B 10CH Rx | 5,109 | Robocraze |
| 8 | Telemetry Radio | 3DR 433MHz 500mW (pair) | 2,151 | Robocraze |
| 9 | Companion Computer | **Jetson Orin Nano Super 8GB** | 37,499 | Robocraze |
| 10 | Camera | Raspberry Pi Camera Module 3 Wide | 3,800 | Robocraze |
| 11 | 4G Module | Waveshare SIM7600G-H 4G Dongle | 4,917 | Robocraze |
| 12 | LiDAR | TFMini-S (12m range) | 3,259 | Prayog India |
| 13 | Obstacle Sensors | HC-SR04 Ultrasonic x3 | 228 (3x 76) | Robocraze |
| 14 | Power Distribution | PDB-XT60 + 5V 3A UBEC | 665 | Robocraze |
| 15 | Propellers | 1045 Props (3 pairs) | 250 | Robocraze |
| 16 | Wires/Connectors | XT60, servo wires, heatshrink | 500 | QuartzComponents |

## Key Features
- **AI:** 1024 CUDA cores + 32 Tensor cores = **67 TOPS** inference
- **Real-time Vision:** YOLOv8 at 40+ FPS on 1080p video
- **Local LLM:** Can run LLaVA-7B / Phi-3-mini locally for situational reasoning
- **Decision Making:** Not just "obstacle detected" but "analyze scene, decide best route, assess threat level" — human-like reasoning on the edge
- **Pixhawk 6C:** Latest generation flight controller, better sensor suite, USB-C
- **SIM7600G-H:** Global 4G band support — works in any country
- **Flight Time:** ~18-22 min with 5000mAh 4S battery
- **GPS:** M9N multi-constellation for sub-meter accuracy

## Why This is the "Thinks Like a Human" Variant
The 67 TOPS of AI compute means you can run:
1. **Object Detection** (YOLOv8) — what's around me?
2. **Semantic Segmentation** — understand the scene (buildings, trees, roads, threats)
3. **Path Planning AI** — neural network-based path planning, not just GPS waypoints
4. **Small Language Model** — reason about situations in natural language
5. All of the above **simultaneously** with compute to spare

When EMP/jamming cuts all external communication, this drone doesn't just "return home" — it can analyze the situation, find safe landing zones, plan alternative routes, and make nuanced decisions.

## Limitations
- Most expensive variant — Rs.85K+ budget
- Orin Nano draws 15-25W — needs robust power delivery
- Heavier setup reduces flight time
- Overkill if you only need basic obstacle avoidance
- Best justified for thesis/research requiring edge AI demonstration

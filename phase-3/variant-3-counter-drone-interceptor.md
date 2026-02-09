# Variant 3 — Counter-Drone Interceptor

**Additional Cost Over Phase 1: Rs. 15,000 - 30,000**

An autonomous drone that detects, pursues, and physically captures enemy drones using a net. This is exactly what **Fortem Technologies DroneHunter F700** does (4,500+ captures). India's DRDO + BEL deployed anti-drone systems at Red Fort, Republic Day, and major airports. Counter-UAS is one of the fastest-growing defense markets globally.

> **Ref:** Fortem DroneHunter (fortemtech.com) — AI-driven autonomous interceptor with net capture. DRDO's Anti-Drone System deployed since 2020. DroneShield (droneshield.com) — detection + defeat. India allocated Rs.300+ crore for counter-drone procurement.

## Additional Components (on top of Phase 1 — Jetson Nano variant required)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | **Frame Upgrade** | Racing/fast quad frame (QAV250/Martian II) | 936 - 2,500 | Robocraze |
| 2 | **Racing Motors x4** | 2306 2450KV (high speed/thrust) | 4,000 - 6,000 (4x 1,000-1,500) | Robocraze |
| 3 | **ESC x4** | BLHeli_32 35A (fast response) | 3,200 (4x 800) | Robocraze |
| 4 | **Net Launcher** | Compressed air / spring net gun mechanism | 5,000 - 15,000 | DIY / IndiaMART |
| 5 | **Net** | Lightweight nylon net 2x2m, weighted corners | 500 - 1,000 | Amazon.in / local |
| 6 | **Servo Trigger** | MG996R for net release mechanism | 350 | Robocraze |
| 7 | **AI Camera** | Pi Camera Module 3 Wide (120deg FOV) | 3,800 | Robocraze |
| 8 | **Thermal Camera** | MLX90640 (detect drone motors heat) | 4,589 - 5,624 | Robocraze |
| 9 | **CO2 Cartridge** | 12g CO2 (for pneumatic net launch) | 50 - 100 each | Amazon.in |
| 10 | **Tether/DrogueChute** | Small parachute to drag captured drone down | 1,000 - 2,000 | Amazon.in |

## How It Works (Fortem-Style Intercept)

### Phase 1: Detection
1. RTL-SDR (from Phase 2) detects enemy drone's RF control signal
2. AI camera + thermal scan sky for moving targets
3. Jetson Nano runs **YOLO drone detection model** (trained on drone silhouettes)
4. Target acquired — range, bearing, altitude estimated

### Phase 2: Pursuit
1. Drone switches to high-speed pursuit mode
2. AI maintains visual lock on target (DeepSORT tracker)
3. Predictive flight path calculation — intercept course computed
4. Autonomous approach from above/behind (blind spot of most drones)
5. Racing motors provide speed advantage over typical camera/survey drones

### Phase 3: Capture
1. Close to 5-10m range, AI confirms target identification
2. Servo triggers net launcher — compressed CO2 deploys net
3. Net entangles target drone's propellers
4. Drogue chute deploys — tangled target descends under parachute
5. GPS marks capture location for ground recovery team

### Phase 4: Return
1. Interceptor drone returns to base autonomously (RTL)
2. Captured drone recovered by ground team for intelligence analysis

## Key Features
- **Autonomous pursuit** — AI tracks and intercepts without human piloting
- **Non-destructive capture** — net entanglement preserves drone for intel analysis
- **Reusable** — replace net and CO2 cartridge, fly again
- **Day/night capable** — thermal camera detects drone motors even at night
- **Fast** — racing motors give 80-100+ km/h top speed for pursuit
- **Low cost** — vs Rs.5-50 lakh for commercial counter-drone systems

## Net Launcher Design (DIY Research Prototype)

### Option A: Spring-Loaded
- Compressed spring in tube, held by servo latch
- Servo releases latch, spring launches net bag
- Simple, reliable, no consumables except net
- Range: 3-5m (must get close)

### Option B: CO2 Pneumatic
- 12g CO2 cartridge (paintball/airsoft style)
- Puncture mechanism triggered by servo
- Launches weighted net at 10-15m range
- More range but single-shot (need reload)

### Option C: Gravity Drop
- Simplest — fly above target, drop weighted net
- Net falls and entangles target from above
- Requires precise positioning but no launcher mechanism
- Cheapest option for research prototype

## Limitations
- Net launcher is single-shot (must return to reload)
- Pursuit requires faster drone than target (racing build helps)
- AI drone detection model needs training data (drone silhouettes dataset)
- Cannot intercept high-speed military drones (designed for hobby/commercial targets)
- Net range limited (5-15m) — need precise approach
- CO2 mechanism needs careful engineering for safety

## Indian Military Context
- **BEL IDDIS (Integrated Drone Detection & Interdiction System):** Co-developed with DRDO. Radar + EO/IR + RF detection (5-8km range) + laser-based hard kill. Signed contract with Indian Army Air Defence.
- **Operation Sindoor (2025):** BEL's laser-based anti-drone system **destroyed multiple low-RCS Pakistani drones in combat**. First real-world validation of Indian indigenous counter-drone tech.
- **Rs.596+ crore** in recent BEL counter-drone contracts post-Operation Sindoor.
- **Adani + DRDO** vehicle-mounted counter-drone: high-energy laser + 7.62mm gun + radar + SIGINT + EO + jammers, 10km range.
- BSF deployed anti-drone on Pakistan/Punjab border (J&K weapon-dropping drones).
- Red Fort, Republic Day, G20 summit all used counter-drone systems.
- Defence Secretary announced accelerated procurement + trials for private sector counter-drone innovations post-Sindoor.

## College Research Angle
- Build interceptor prototype, demonstrate autonomous pursuit of target quad
- Train YOLOv5 model on drone detection dataset (DroneDetect, DUT Anti-UAV)
- Measure: pursuit accuracy, net deployment success rate, capture rate
- Compare: spring vs CO2 vs gravity-drop effectiveness
- Publish: "Autonomous Counter-UAS Interceptor Using Vision-Based Tracking and Net Capture"

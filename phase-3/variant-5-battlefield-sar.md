# Variant 5 — Battlefield Search & Rescue (CASEVAC Support)

**Additional Cost Over Phase 1: Rs. 12,000 - 20,000**

Find wounded soldiers on the battlefield using thermal + AI vision, then drop first-aid / medevac supplies to keep them alive until ground rescue arrives. In combat, getting to a wounded soldier quickly is the difference between life and death — a drone can reach a casualty in minutes vs hours for ground medevac under fire.

> **Ref:** NDRF uses drones for SAR in Indian floods/earthquakes. US military uses RQ-11 Raven for battle damage assessment. Israeli ORBITER drones used for battlefield ISR + casualty location. Every NATO army is integrating drone CASEVAC (Casualty Evacuation) support.

## Additional Components (on top of Phase 1 — Jetson Nano variant)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | **Thermal Camera** | MLX90640 IR Array (32x24, 110deg FOV) | 4,589 - 5,624 | Robocraze |
| 2 | **Night Camera** | Pi NoIR Camera V2 (no IR filter) | 2,200 | Robocraze |
| 3 | **IR Illuminator** | 850nm IR LED array (covert) | 500 - 800 | Amazon.in |
| 4 | **Servo Release x2** | MG996R (dual payload drop) | 700 (2x 350) | Robocraze |
| 5 | **Cargo Parachute** | Small drone parachute (1kg class) | 3,000 - 5,000 | XBOOM.in |
| 6 | **Loudspeaker** | 5W weatherproof + PAM8403 amp | 500 - 800 | Amazon.in |
| 7 | **Spotlight** | 10W LED (searchlight for night) | 300 - 500 | Amazon.in |
| 8 | **Emergency Strobe** | High-brightness LED strobe beacon | 200 - 400 | Amazon.in |
| 9 | **Extra Battery** | 4S 5000mAh LiPo | 4,500 | Amazon.in |
| 10 | **Payload Container** | Waterproof ABS box for med supplies | 800 - 1,500 | Amazon.in |

## SAR Mission Profile

### Phase 1: Search Grid
1. Commander marks suspected casualty area on map
2. Drone flies autonomous grid pattern at 30-50m altitude
3. Jetson Nano runs dual detection:
   - **Thermal (MLX90640):** detects 35-40°C heat signatures = human body
   - **Visual (YOLOv5):** person detection on Pi Camera
4. AI filters false positives (vehicles, animals, hot debris)
5. When potential casualty found — drone hovers, marks GPS

### Phase 2: Identification
1. Drone descends to 10-15m for close inspection
2. Higher-resolution image sent to command via 4G
3. Thermal confirms body temperature (alive vs deceased)
4. Loudspeaker: "Medical help is coming. Signal if you can hear this."
5. Command confirms — friendly casualty or threat assessment

### Phase 3: Medevac Supply Drop
1. Drone carries emergency medical kit in payload container
2. Flies to confirmed casualty location
3. Hovers at 10m, loudspeaker announces drop
4. Servo releases payload on parachute
5. Strobe LED activates on package for visibility

### Phase 4: Overwatch + Guide
1. Drone orbits above casualty at 30-50m
2. Provides live video to approaching ground medevac team
3. Loudspeaker guides ground team: "Casualty 20 meters north"
4. Maintains watch for enemy movement around casualty

## Emergency Medical Kit (Dropped Payload)
| Item | Weight | Military Use |
|------|--------|-------------|
| Combat tourniquet (CAT) | 80g | Stop arterial bleeding |
| Hemostatic gauze (QuikClot) | 100g | Pack wounds |
| Israeli bandage | 100g | Pressure dressing |
| Chest seal (x2) | 50g | Treat pneumothorax |
| Nasopharyngeal airway | 30g | Maintain airway |
| Morphine auto-injector | 100g | Pain management |
| Emergency blanket | 50g | Prevent hypothermia |
| Chem light (IR) | 20g | Mark position for ground team |
| Two-way radio (optional) | 150g | Communicate with casualty |
| **Total** | **~680g** | Within S500 payload capacity |

## AI Casualty Detection
- **Thermal:** Human body = 36-38°C hot spot. MLX90640 detects to ~50m altitude.
- **Visual:** YOLOv5 "person" class + pose estimation (lying down = potential casualty)
- **Motion analysis:** Stationary person in open = higher priority than moving person
- **Fusion:** thermal + visual cross-confirmation reduces false positives to <5%

## Key Features
- **Find wounded faster** — drone covers 1km² in 10 min vs hours for ground search
- **Night capable** — thermal + IR illumination works in complete darkness
- **Supply drop** — trauma kit arrives within minutes of detection
- **Overwatch** — protects casualty by monitoring area for threats
- **Voice guidance** — loudspeaker communicates with conscious casualties
- **Real-time feed** — command sees everything, directs ground medevac

## Indian Military Context
- Indian Army operates in Siachen (20,000ft) where ground medevac takes hours
- Kashmir encounters — wounded soldiers in dense forest/mountainous terrain
- Naxal operations — casualties in remote jungle areas
- NDRF disaster SAR — floods, earthquakes, landslides (Uttarakhand, Kerala)
- Indian Navy SAR — man overboard, coastal rescue operations

## College Research Angle
- Build SAR drone, demonstrate thermal person detection + supply drop
- Test: thermal detection range at 10m, 30m, 50m altitude
- Measure: search coverage rate (km²/hour) vs grid altitude and speed
- Evaluate: parachute drop accuracy for medical supplies
- Publish: "UAV-Assisted Battlefield Casualty Detection and Emergency Supply Delivery"

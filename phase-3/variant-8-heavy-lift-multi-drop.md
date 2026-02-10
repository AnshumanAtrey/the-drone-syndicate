# Variant 8 — Heavy-Lift Hexacopter Multi-Drop (6 x 500g Payloads)

**Standalone Total Cost: Rs. 55,000 - 78,000** (depending on source & tier)

Heavy-lift hexacopter that carries and individually releases 6 payloads of 400-500g each (3kg total). Uses 6x servo-actuated pin-pull release mechanisms triggered sequentially via ArduPilot mission commands. No AI, no cameras — pure RC + autopilot control with ArduPilot.

> **Why hexacopter?** A quadcopter with 2212 motors produces ~2,200g thrust — can't even lift 3kg payload + drone weight. Six 3508 380KV motors on 6S produce **11,280g thrust**, giving a 1.70:1 thrust-to-weight ratio at full 3kg load. For higher safety margin (2:1), upgrade to MN4012 400KV motors (14,220g total thrust).

---

## Can It Actually Carry 6 Payloads? — YES

| | Value |
|---|---|
| Total thrust (6× MN3508 380KV on 6S) | **11,280g** |
| Drone dry weight | **3,863g** |
| 6 payloads (6 × 500g) | **3,000g** |
| All-up weight (AUW) | **6,863g** |
| Excess thrust at hover | **4,417g** |
| **Thrust-to-weight ratio** | **1.64:1** |

**Verdict:** The drone produces 4,417g of excess thrust beyond what it needs to hover at full load. It **will fly and complete all 6 drops.**

**Practical limits at 1.64:1 TWR:**
- **Calm weather (< 15 km/h wind):** Flies fine, all 6 sequential drops work as designed
- **Windy conditions:** Struggles at full load — insufficient thrust reserve to fight gusts. Not recommended
- **Progressive improvement:** TWR improves with every drop — after 3 drops (1.5kg released), TWR reaches 2.10:1 (excellent)
- **Single motor failure:** Cannot sustain flight at full load with one motor out (hex needs ~1.5:1 minimum on 5 motors → need 10,295g from 5 motors → only 9,400g available). Fly conservatively

**For confident all-weather operation:** Upgrade to MN4012 400KV motors (+Rs. 6,000-12,000). TWR jumps to **1.98:1** at full load with only +312g weight penalty. Same frame, same ESCs, same everything else.

---

## Component Selection — Verified & Justified

Every component below has been researched against manufacturer datasheets, ArduPilot community builds, and real-world test data. Alternatives were evaluated and rejected with justification.

---

### 1. Frame: ZD850 (850mm Carbon Fiber Folding Hex)

**Why ZD850 over Tarot 680 PRO:**

The original spec listed Tarot 680 PRO (695mm wheelbase). This is **physically impossible** for 15-inch propellers.

**Hexacopter geometry proof:**
- In a regular hex, adjacent motor distance = wheelbase ÷ 2
- Tarot 680: adjacent motors = 695 ÷ 2 = **348mm**
- 15-inch prop diameter = **381mm** → **props OVERLAP by 33mm**
- Tarot 680 max prop = 12-13 inch (confirmed by Tarot specs)

**ZD850 verification:**
- Adjacent motors = 850 ÷ 2 = **425mm**
- 15" prop = 381mm → **44mm total clearance (22mm per tip)** ✓
- ZD850 manufacturer rates it for 15-16" propellers
- ArduPilot forum users confirm 6kg+ payload class with this frame

| Spec | ZD850 | Tarot 680 PRO |
|------|-------|---------------|
| Wheelbase | 850mm | 695mm |
| Arm tubes | 20mm carbon fiber | 16mm carbon fiber |
| Weight | 1,210g (with landing gear) | 780g |
| Max prop | 15-16 inch ✓ | 12-13 inch ✗ |
| Max payload | ~6kg | ~2.5kg |
| Landing gear | Carbon fiber, 50kg+ rated | Retractable, lighter duty |
| Foldable | Yes (umbrella style) | Yes |

**Alternatives rejected:**
- **S550 (550mm):** Max 10" props, 2.4kg MTOW — completely inadequate
- **Tarot T960 (960mm):** Fits 18" props, 8kg load — viable but overkill and heavier. Use only if upgrading to MN4012 motors with 16" props

> **Source:** [ArduPilot Forum - ZD850 Motors](https://discuss.ardupilot.org/t/suitable-motors-for-zd850-frame/110052), [OpenELAB ZD850 Wiki](https://wiki.openelab.io/drone-fpv/zd850-850mm-compact-folding-hexacopter-drone-frame-kit-full-carbon-fiber)

---

### 2. Motors: T-Motor MN3508 380KV (Primary) / MN4012 400KV (Upgrade)

#### Primary: T-Motor MN3508 380KV × 6

**Why this motor:**
- Industry standard for professional multirotor builds
- Japanese EZO bearings (oversized, 2× comparable motors) — 1,000-hour MTBF
- Referenced in academic research papers (ResearchGate published test data)
- Most documented thrust data of any 3508 motor

| Spec | Value |
|------|-------|
| KV | 380 RPM/V |
| Weight (with cables) | 103g |
| Internal resistance | 205 mΩ |
| Max continuous current | 14A (180 seconds) |
| Max continuous power | 310W |
| Efficiency range | 2-7A at >84% |
| Shaft | 4mm |
| LiPo | 3-6S |

**Verified thrust data — 6S (22.2V) with 15×5 CF prop:**

| Throttle | Current/Motor | Thrust/Motor | 6-Motor Total | Power/Motor | Efficiency |
|----------|--------------|-------------|---------------|-------------|------------|
| 50% | 3.6A | 820g | 4,920g | 80W | 10.26 g/W |
| 65% | 6.1A | 1,200g | 7,200g | 135W | 8.86 g/W |
| 75% | 9.5A | 1,500g | 9,000g | 211W | 7.11 g/W |
| 100% | 13.3A | 1,880g | **11,280g** | 295W | 6.37 g/W |

*Source: T-Motor official store + ResearchGate academic test data*

**Motors REJECTED:**

| Motor | Why Rejected |
|-------|-------------|
| **GARTT ML3508 380KV** | **Does not exist.** GARTT only makes 580KV and 700KV variants. The 580KV is rated 4S max, not 6S. No thrust data available. Avoid for safety-critical builds. |
| **BrotherHobby Avenger 3508** | **Does not exist.** BrotherHobby's Avenger line includes 2806.5, 2812, 3008, 3120 — no 3508. Any such listing is counterfeit. |
| **SunnySky V3508 380KV** | Verified 1,840g thrust but runs **115°C after 1 minute** at full throttle (near wire insulation limit). 30-second max current rating (vs T-Motor's 180s). 25% higher internal resistance (257 vs 205 mΩ). Acceptable budget alternative if T-Motor unavailable, but thermal margins are tighter. |

#### Upgrade Option: T-Motor MN4012 400KV × 6

For **industry-standard 2:1 thrust-to-weight ratio**, upgrade to MN4012:

| Spec | MN3508 380KV | MN4012 400KV |
|------|-------------|-------------|
| Max thrust (15×5 CF, 6S) | 1,880g | **2,370g** |
| Max thrust (16×5.4 CF, 6S) | N/A | **3,020g** |
| Weight | 103g | 155g |
| Max current (180s) | 14A | 25A |
| Internal resistance | 205 mΩ | **67 mΩ** |
| 6-motor total (15" props) | 11,280g | **14,220g** |
| TWR at 6.6kg AUW | 1.70:1 | **2.05:1** ✓ |
| Price each | Rs. 4,500 | Rs. 5,500-6,500 |
| Weight penalty (6 motors) | — | +312g |

**Recommendation:** MN4012 if budget allows (+Rs. 6,000-12,000 total). MN3508 acceptable for calm-weather flying with 1.7:1 TWR.

> **Source:** [T-Motor MN3508 Official](https://store.tmotor.com/product/mn3508-motor-navigator-type.html), [T-Motor MN4012 Official](https://store.tmotor.com/product/mn4012-kv400-motor-navigator-type.html)

---

### 3. Flight Controller: Matek H743-WING V3

**Why Matek H743-WING V3 over Pixhawk 2.4.8:**

The original spec listed "Pixhawk 2.4.8." Critical finding: **The Pixhawk 2.4.8 does not exist as a genuine product.** The last official Pixhawk 1 was v2.4.6. All "2.4.8" units are unauthorized Chinese clones with documented issues:
- Firmware compatibility problems (throttle dead zones above v3.2.1)
- Counterfeit ICs and substandard components
- Erratic compass and IMU behavior after firmware updates

| Spec | Matek H743-WING V3 | "Pixhawk 2.4.8" (clone) | Pixhawk 4 |
|------|-------------------|----------------------|-----------|
| Processor | **STM32H743 (480MHz)** | STM32F427 (168MHz) | STM32F765 (216MHz) |
| PWM outputs | **13 (12 usable)** | 14 (8 MAIN + 6 AUX) | 16 (8+8) |
| DShot support | Outputs 1-8 | No (MAIN is PWM only) | AUX only |
| Built-in servo BEC | **5/6/7.2V, 8A continuous** | None (external needed) | None (external needed) |
| IMU | Dual ICM42688P | Single/dual (varies by clone) | Dual redundant |
| Clone risk | **None** (Matek is the OEM) | **HIGH** | Medium |
| ArduCopter support | Full | Full | Full |
| Price (INR) | ~5,850 | ~2,250 | ~9,000-13,500 |

**Key advantage — built-in 8A servo BEC:**
- MG90S servo stall current: ~650-750mA each
- 6 servos worst-case simultaneous stall: 4.5A
- BEC capacity: 8A continuous → **3.5A headroom even at worst case**
- No external BEC needed for servo rail power

**PWM output configuration for 6 motors + 6 servos:**
```
Outputs 1-6:  Motors (DShot protocol) — Group A+B
Outputs 7-12: Servos (PWM protocol) — Group C+D
Output 13:    LED (optional)
```

This works because motors and servos are in **separate output groups** (DShot and PWM cannot mix within the same group).

> **Source:** [ArduPilot - Matek H743-Wing](https://ardupilot.org/copter/docs/common-matekh743-wing.html), [ArduPilot Forum - Pixhawk 2.4.8 Clone Issues](https://discuss.ardupilot.org/t/pixhawk-2-4-8-clone-and-problems-with-copter-firmware-above-3-2-1/13957)

---

### 4. ESCs: BLHeli_32 40A Individual ESCs × 6

**Why 40A is sufficient:**
- MN3508 380KV max current: 13.3A at full throttle
- MN4012 400KV max current: 16.2A at full throttle
- 40A ESC provides **2.4-3× safety margin**
- Total system current (6 motors): ~80-100A peak

**Why NOT T-Motor AIR 40A:**
- Does NOT support DShot protocol (PWM only, max 621Hz)
- DShot is recommended for modern ArduCopter builds (faster response, telemetry)

**Why NOT Hobbywing XRotor 40A 4-in-1:**
- It's a 4-in-1 ESC designed for quads, not individual ESCs for hex
- Some single-ESC XRotor versions are rated 2-5S only, NOT 6S

**Recommended: Individual BLHeli_32 40A ESCs (6 + 2 spares)**

| ESC Option | Voltage | DShot | Weight | BEC | Price/ea |
|-----------|---------|-------|--------|-----|----------|
| **Flycolor Francy 40A** | 3-6S | DShot1200 ✓ | 16.5g | Yes (5V) | ~Rs. 600-800 |
| **Flashhobby ARIA 40A** | 3-6S | DShot1200 ✓ | ~15g | Yes | ~Rs. 550-700 |

**Why individual ESCs over 4-in-1:** No 6-in-1 ESC exists. Individual ESCs are actually preferable for hex builds — single ESC failure doesn't take out all motors, and heat dissipation is distributed across the frame.

---

### 5. GPS: Matek M10Q-5883 (or Holybro M10 Micro)

| Spec | Matek M10Q-5883 | Beitian BN-880 | Holybro M8N |
|------|-----------------|----------------|-------------|
| GNSS chip | **u-blox M10 (newest)** | u-blox M8N (older) | u-blox M8N (older) |
| Concurrent constellations | **4** (GPS+GLONASS+Galileo+BeiDou) | 3 | 3 |
| Compass | QMC5883L | HMC5883L | IST8310 |
| ArduPilot support | Full (4.3+) | Full | Full |
| Price (INR) | ~1,800-2,500 | ~1,350-1,620 | ~1,800-2,100 |

**Why M10 over M8N:** The u-blox M10 chip supports 4 concurrent satellite constellations (vs 3 for M8N), providing better position accuracy and faster fix times.

**CRITICAL for hexacopter:** Mount GPS on a **mast 10-15cm above frame** to minimize compass interference from 6 motor power lines. Use twisted wires between PDB and ESCs. Run ArduPilot `COMPASS_MOT` calibration after assembly.

> **Source:** [ArduPilot - Magnetic Interference](https://ardupilot.org/copter/docs/common-magnetic-interference.html), [ArduPilot - Matek M10Q](https://www.mateksys.com/?portfolio=m10q-5883)

---

### 6. Battery: 2× 6S 5000mAh 50C LiPo (Parallel)

**Why 2× 5000mAh parallel instead of 1× 10000mAh:**

| Factor | 2× 5000mAh 50C Parallel | 1× 10000mAh 25C |
|--------|------------------------|-----------------|
| Effective capacity | 10,000mAh | 10,000mAh |
| Weight | ~1,430g (2× 715g) | ~1,350g |
| Internal resistance | **Halved** (parallel) | Standard |
| Voltage sag at 40A | **Lower (better)** | Higher |
| CG placement | Split fore/aft for balance | One large mass |
| Failure mode | **Partial redundancy** | Single point of failure |
| Max current | 500A (overkill) | 250A (sufficient) |
| Cost (INR) | ~7,200-9,000 | ~8,320-9,000 |

**C-rating verification:**
- Hover current: 6 motors × 6-8A = 36-48A total
- 5000mAh 50C = 250A max per pack, 500A parallel → massive headroom
- Even 25C 10000mAh (250A) is sufficient, but parallel config has better voltage sag

**Flight time estimates:**

| Condition | AUW | Hover Current | Flight Time (80% usable) |
|-----------|-----|--------------|------------------------|
| Full load (3kg payload) | ~6,600g | ~42A | **~11 min** |
| Progressive 6-drop mission | 6,600→3,600g | avg ~33A | **~14-15 min** |
| Empty (post-drop) | ~3,600g | ~18A | **~27 min** |

**Buy locally in India.** LiPo batteries face BIS certification seizure risk at Indian customs. GenX (Robokits) or Orange (Robu.in) are safe Indian options.

---

### 7. Propellers: 15×5.5 (1555) Carbon Fiber

**Clearance verified:** 44mm total gap on ZD850 (22mm per tip) — adequate per industry 10-15mm minimum standard.

**Quality recommendation:** Buy generic CF 1555 props at Rs. 1,000-1,350/pair (vs T-Motor at Rs. 2,500+/pair). Multiple RCGroups users report generic CF quality as "identical side by side" to T-Motor. BUT:
1. **ALWAYS balance with a prop balancer** — unbalanced 15" props cause severe vibration
2. Buy 4-5 pairs (3 flying + 1-2 spares) — budget for duds

---

### 8. Release Servos: MG90S Metal Gear Micro Servo × 6

**Torque verification:**
- Payload weight: 500g = 0.5kg
- Servo arm at 1cm from pivot: torque needed = 0.5 kg·cm
- MG90S torque: 1.8 kg·cm (4.8V) / 2.2 kg·cm (6.0V)
- **Safety factor: 3.6× — more than sufficient**

**Why MG90S over alternatives:**

| Servo | Torque | Weight | Verdict |
|-------|--------|--------|---------|
| SG90 | 1.2 kg·cm | 9g | **NO** — plastic gears strip under vibration |
| **MG90S** | **1.8-2.2 kg·cm** | **14g** | **YES** — best weight/torque ratio |
| MG996R | 9.4-11 kg·cm | 55g | Overkill — 6× = 330g unnecessary weight |
| DS3218 | 20 kg·cm | 60g | Massive overkill — designed for robotic arms |

**Vibration mitigation:** Mount with M2 rubber grommets and thin foam tape. Print brackets in PETG (not PLA — PLA gets brittle). Never command servo to absolute end-of-travel.

**Power:** 6 servos powered from Matek H743's built-in 8A servo BEC. No external BEC needed (worst-case 6-servo stall = 4.5A vs 8A BEC capacity).

---

### 9. Charger: ISDT D2 Mark II (or ToolkitRC M7)

**Why NOT iMAX B6AC:**
- 50W maximum → at 6S (22.2V): only 2.25A charge rate
- **4.4 hours to charge 10000mAh** — completely impractical
- Designed for 3S-4S packs, not heavy-lift 6S

| Charger | Power | 6S Charge Rate | Time (10Ah) | Dual Channel | Price (INR) |
|---------|-------|---------------|-------------|-------------|-------------|
| **ISDT D2 Mk II** | **200W×2** | ~8A per channel | **38 min** (2× 5Ah simultaneous!) | **Yes** | ~7,200-9,000 |
| ToolkitRC M7 | 200W | ~8A | 75 min | No | ~3,150-4,050 + PSU |
| iMAX B6AC | 50W | 2.25A | **4.4 hours** ✗ | No | ~1,800 |

**Recommendation:** ISDT D2 Mk II — charges both 5000mAh packs simultaneously in 38 minutes. Built-in AC (no external PSU). 1.5A balance current (7.5× faster than B6AC).

**Budget alternative:** ToolkitRC M7 at Rs. 3,150 + separate DC PSU at Rs. 1,800.

---

### 10. Transmitter: FlySky FS-i6X + iA10B (with ArduPilot Mission Control)

**Channel limitation discovered:**
- FS-i6X has 10 channels max (with 10ch firmware + iA10B receiver)
- Need: 4 sticks + 1 mode + 6 servo releases = **11 minimum**
- FS-i6X is **1 channel short** for individual servo control

**Solution: ArduPilot DO_SET_SERVO — no extra channels needed**

Instead of controlling each servo from the TX, use ArduPilot mission commands:

```
# In Mission Planner, create waypoint mission:
WP1 → NAV_WAYPOINT (fly to drop zone 1)
CMD → DO_SET_SERVO (servo 7, PWM 1700)   // Release payload 1
CMD → DO_SET_SERVO (servo 7, PWM 1100)   // Reset servo 1
WP2 → NAV_WAYPOINT (fly to drop zone 2)
CMD → DO_SET_SERVO (servo 8, PWM 1700)   // Release payload 2
... repeat for all 6 drops
```

**ArduPilot configuration:**
```
SERVO7_FUNCTION  = 0    (Manual/Script control — Payload 1)
SERVO8_FUNCTION  = 0    (Manual/Script control — Payload 2)
SERVO9_FUNCTION  = 0    (Manual/Script control — Payload 3)
SERVO10_FUNCTION = 0    (Manual/Script control — Payload 4)
SERVO11_FUNCTION = 0    (Manual/Script control — Payload 5)
SERVO12_FUNCTION = 0    (Manual/Script control — Payload 6)
```

Payload drops execute **automatically at GPS waypoints** or via GCS MAVLink command. The TX only needs flight controls + mode switch (7 channels total).

**If manual individual control is required:** Upgrade to RadioMaster TX16S Mark II (16ch, Rs. 13,500-18,000) or RadioLink AT10II (12ch, Rs. 9,000).

---

## Build Cost Summary

### All India (no import, 1-week delivery)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | Frame | ZD850 850mm CF hex | 12,000-14,000 | IndiaMART / Amazon.in |
| 2 | Motors ×6 | T-Motor MN3508 380KV | 27,000 | Robokits (4,500/pc) |
| 3 | ESCs ×6 | BLHeli_32 40A individual | 4,800-6,000 | RCDuniya / Amazon.in |
| 4 | Props ×4 pairs | 15×5.5 CF CW+CCW | 4,000-5,400 | IndiaMART |
| 5 | Flight Controller | Matek H743-WING V3 | 5,850 | IndiaMART / Quadkopters |
| 6 | GPS Module | Matek M10Q-5883 | 2,200-2,500 | IndiaMART / Quadkopters |
| 7 | Battery ×2 | 6S 5000mAh 50C (parallel) | 7,200-9,000 | Robokits (GenX) / Robu.in |
| 8 | RC Transmitter + Rx | FlySky FS-i6X + iA10B | 3,389 | IndiaMART |
| 9 | Release Servos ×6 | MG90S Metal Gear | 1,500 | Robu.in (~250/pc) |
| 10 | Release Mechanism | DIY pin-pull (steel wire + 3D print) ×6 | 600 | DIY |
| 11 | Landing Gear | Included with ZD850 frame | — | — |
| 12 | Wiring | XT90, 12AWG, parallel harness | 1,000 | Robu.in |
| 13 | Charger | ToolkitRC M7 + DC PSU | 4,950 | Amazon.in |
| | **TOTAL (All India)** | | **~74,500 - 83,000** | |

### Mixed Source (India + China imports)

| Component | Price (INR) | Source |
|-----------|-------------|--------|
| ZD850 frame | 10,800 | AliExpress/Banggood ($120) |
| 6× MN3508 380KV (SunnySky) | 18,000 | AliExpress ($33/pc) |
| 6× BLHeli_32 40A ESC | 3,600 | AliExpress ($7/pc) |
| 4 pairs 1555 CF props | 3,600 | AliExpress ($10/pair) |
| Matek H743-WING V3 | 4,500 | AliExpress ($50) |
| Matek M10Q-5883 GPS | 1,800 | AliExpress ($20) |
| 2× 6S 5000mAh 50C (BUY IN INDIA) | 7,200 | Robokits |
| FlySky FS-i6X + iA10B | 3,389 | IndiaMART |
| 6× MG90S servos | 1,080 | AliExpress ($2/pc) |
| Release mechanism (DIY) | 300 | DIY |
| Wiring + connectors | 1,000 | Robu.in |
| ToolkitRC M7 + PSU | 4,950 | Amazon.in |
| **TOTAL (Mixed)** | **~60,220** | |

> **Note:** China import adds ~38-50% customs overhead (BCD + IGST). AliExpress banned in India — use Banggood or freight forwarders. **Buy batteries locally** — BIS certification seizure risk on imported LiPo.

---

## Weight Budget (Verified)

| Item | Weight |
|------|--------|
| ZD850 frame + landing gear | 1,210g |
| 6× MN3508 380KV motors (103g each) | 618g |
| 6× BLHeli_32 40A ESCs (~16g each) | 96g |
| 6× 15×5.5 CF props (~14g each) | 84g |
| Matek H743-WING V3 | 36g |
| Matek M10Q GPS + mast | 50g |
| FlySky iA10B receiver | 15g |
| Wiring, connectors, parallel harness | 150g |
| 6× MG90S servos + mounting hardware | 174g |
| 2× 6S 5000mAh 50C LiPo | 1,430g |
| **Drone Dry Weight** | **~3,863g** |
| **Payload (6 × 500g)** | **3,000g** |
| **All-Up Weight (AUW)** | **~6,863g** |

---

## Thrust-to-Weight Ratios

### With MN3508 380KV (Primary Build)

| Condition | AUW | Thrust | Ratio | Status |
|-----------|-----|--------|-------|--------|
| Full load (6 payloads) | 6,863g | 11,280g | **1.64:1** | Functional, limited margin |
| 5 payloads (1 dropped) | 6,363g | 11,280g | **1.77:1** | Acceptable |
| 3 payloads (3 dropped) | 5,363g | 11,280g | **2.10:1** | Good |
| Empty (all dropped) | 3,863g | 11,280g | **2.92:1** | Excellent |

> **Warning:** 1.64:1 at full load is below the ArduPilot community's recommended 2:1 minimum. Fly only in calm weather (<15 km/h wind) at full load. TWR improves rapidly as payloads are dropped.

### With MN4012 400KV (Upgrade Build)

| Condition | AUW | Thrust | Ratio | Status |
|-----------|-----|--------|-------|--------|
| Full load (6 payloads) | 7,175g (+312g motors) | 14,220g | **1.98:1** | ✓ Near 2:1 target |
| 3 payloads | 5,675g | 14,220g | **2.51:1** | Excellent |
| Empty | 4,175g | 14,220g | **3.41:1** | Outstanding |

---

## Flight Time Estimates

| Battery | Payload | Hover Current | Flight Time |
|---------|---------|--------------|-------------|
| 2× 5000mAh parallel | Full (3kg) | ~42A | **~11 min** |
| 2× 5000mAh parallel | Progressive 6-drop | avg ~33A | **~14-15 min** |
| 2× 5000mAh parallel | Empty (0kg) | ~18A | **~27 min** |

> **Best scenario:** Progressive drop mission — as each 500g payload releases, the drone gets lighter and more efficient. Total mission time ~14-15 min on parallel 5000mAh packs.

---

## Multi-Payload Release Mechanism

### Design: Pin-Pull Servo Release (×6)

```
Each station:
    [Servo MG90S] ──pulls──> [2mm steel locking pin]
                                    │
                              [Payload hook/latch]
                                    │
                              [Payload hangs here]

    ArduPilot DO_SET_SERVO → servo rotates 90° → pin pulls out → payload drops
```

- **Servo:** MG90S metal gear (2.2 kg·cm torque at 6V, 14g weight)
- **Safety factor:** 3.6× for 500g payload
- **Latch:** Bent 2mm steel wire hook OR 3D-printed PETG clip
- **Mount:** Under motor arms with rubber grommets for vibration isolation

### Wiring (Matek H743-WING V3)

```
                    ┌─ Output 7  → Servo 1 (signal)
                    ├─ Output 8  → Servo 2 (signal)
   Matek H743      ├─ Output 9  → Servo 3 (signal)
   Outputs 7-12 ───├─ Output 10 → Servo 4 (signal)
                    ├─ Output 11 → Servo 5 (signal)
                    └─ Output 12 → Servo 6 (signal)

   Built-in 8A Servo BEC ──> Powers all 6 servos (no external BEC needed)
```

### Payload Drop Control (ArduPilot Mission)

```
# Mission Planner waypoint sequence:
WP1 → Fly to drop zone 1
CMD → DO_SET_SERVO(7, 1700)    # Release payload 1
CMD → DELAY(2)                  # 2 sec stabilization
WP2 → Fly to drop zone 2
CMD → DO_SET_SERVO(8, 1700)    # Release payload 2
... repeat for all 6 drops
WP7 → RTL (return to launch)
```

**No extra TX channels needed.** Drops execute automatically at GPS waypoints.

---

## Payload Station Layout (Top View)

```
         Motor 1
          /    \
   Motor 6      Motor 2
    |    [ZD850]    |
   Motor 5      Motor 3
          \    /
         Motor 4

   Payload stations P1-P6 mounted under motor arms:
   P1 (under M1-M2 arm), P2 (under M2-M3 arm), P3 (under M3-M4 arm)
   P4 (under M4-M5 arm), P5 (under M5-M6 arm), P6 (under M6-M1 arm)
```

---

## Where to Buy — Researched & Verified (Feb 2026)

> **Note:** Quadkopters.com has **permanently closed** its online store. EvoBuzz.com does not exist. Quadkart.in is currently not accepting orders. All recommendations below are verified active stores.

### BEST STRATEGY: 2-Store India Build (No Customs, Fast Delivery)

| # | Component | Store | Price (INR) | Link |
|---|-----------|-------|-------------|------|
| 1 | ZD850 850mm CF hex frame | **Robu.in** | ~14,000 | [Robu ZD850](https://robu.in/product/zd850-hexa-rotor-frame-for-drone/) |
| 2 | T-Motor MN3508 380KV ×6 | **Robokits** | 4,500 × 6 = **27,000** | [Robokits MN3508](https://robokits.co.in/multirotor-spare-parts/tiger-motor-esc-and-propeller/t-motor-motor/mn-navigator/t-motor-navigator-mn3508-380kv) |
| 3 | Hobbywing XRotor 40A ESC ×6 | **Robokits** | 1,250 × 6 = **7,500** | [Robokits XRotor 40A](https://robokits.co.in/multirotor-spare-parts/brushless-motor-propeller-esc/esc/hobbywing-xrotor-40a-2-6s-esc) |
| 4 | 1555 CF Propellers ×4 pairs | **Indian Robo Store** | ~1,700 × 4 = **6,800** | [IndianRoboStore 1555](https://indianrobostore.com/product/3k-carbon-fiber-1555-propeller-1555-pair-of-cw-ccw-for-drone) |
| 5 | Matek H743-WING V3 FC | **Indian Robo Store** | **7,295** | [IndianRoboStore H743](https://indianrobostore.com/product/matek-flight-controller-h743-wing-v3-ardupilot-inav-3-8s-for-rc-multirotor-airplane-fixed-wing-drones) |
| 6 | Matek M10-5883 GPS | **RC Mumbai** | **3,811** | [RCMumbai M10-5883](https://rcmumbai.com/mateksys-m10-5883-gnss-compass.html) |
| 7 | 6S 5000mAh 50C LiPo ×2 | **Robokits** (GenX) | 4,074 × 2 = **8,148** | [Robokits GenX 6S](https://robokits.co.in/batteries-chargers/drone-batteries/genx-power-premium-lipo-battery/genxpower-22.2v-lipo-batteries/genx-22.2v-6s-5200mah-40c-80c-premium-lipo-lithium-polymer-battery) |
| 8 | FlySky FS-i6X + iA10B | **Robu.in** | **4,899** | [Robu FlySky](https://robu.in/product/flysky-fs-i6x-2-4ghz-10ch-afhds-2a-rc-transmitter-with-fs-ia10b-2-4ghz-10ch-receiver/) |
| 9 | MG90S Servo ×6 | **Robokits** | 102 × 6 = **612** | [Robokits MG90S](https://robokits.co.in/motors/rc-servo-motor/mg90s-semi-metal-gear-servo-motor-9g-premium) |
| 10 | Release mechanism (DIY) | DIY | ~600 | 3D print + 2mm steel wire |
| 11 | XT90, 12AWG wire, harness | **Robu.in** | ~1,000 | [Robu Wiring](https://robu.in/product-category/batteries/wires-and-cables/silicone-wires/) |
| 12 | ToolkitRC M7 charger + PSU | **Robu.in** | ~4,500-5,500 | [Robu ToolkitRC](https://robu.in/product/toolkitrc-m7-200w-10a-2-6s-dc-smart-charger/) |
| | **TOTAL (All India)** | **3 stores** | **~Rs. 86,000 - 91,000** | |

### Store Breakdown — What to Order Where

| Store | Items | Subtotal | Notes |
|-------|-------|----------|-------|
| **Robokits.co.in** | 6× MN3508 motors, 6× XRotor ESCs, 6× MG90S servos, 2× GenX 6S batteries | ~Rs. 43,260 | Cheapest T-Motor dealer in India. Authorized stock |
| **Robu.in** | ZD850 frame, FlySky FS-i6X, ToolkitRC charger, wiring/connectors | ~Rs. 24,400 | Official FlySky distributor. Free shipping on many items |
| **Indian Robo Store** | Matek H743-WING V3, 1555 CF props ×4 | ~Rs. 14,095 | Cheapest Matek H743 source (31% off MRP) |
| **RC Mumbai** (optional) | Matek M10-5883 GPS | ~Rs. 3,811 | Best source for genuine Matek GPS. Can substitute Robokits M8N GPS at Rs. 1,084 to save |

### Alternative: Single Store (Simplest, Slightly More Expensive)

**Robu.in** covers ~9/11 components in one order. Estimated total: **Rs. 90,000-1,05,000**. Only missing: Matek H743-WING V3 (buy from Indian Robo Store) and the exact Matek M10Q GPS (substitute with Foxeer M10Q-5883 equivalent from Robu).

### Budget Option: India + Banggood Import

| Component | Store | Price (INR) |
|-----------|-------|-------------|
| ZD850 frame | Banggood ($80) | ~6,800 + 40% customs = **9,520** |
| 6× Racerstar 3508 380KV | Banggood ($92 total) | ~7,800 + 40% = **10,920** |
| 6× Generic 40A ESC | Banggood ($60 total) | ~5,100 + 40% = **7,140** |
| Matek H743-WING V3 | Indian Robo Store | **7,295** |
| GPS, props, servos | Banggood (~$35) | ~2,975 + 40% = **4,165** |
| FlySky FS-i6X | Robu.in | **4,899** |
| 2× 6S 5000mAh LiPo | **Robokits (BUY LOCAL)** | **8,148** |
| Charger + wiring | Robu.in | **5,500** |
| **TOTAL (Mixed)** | | **~Rs. 57,587** |

> **Warning:** Banggood import risks: 15-45 day delivery, 1.6/5 customer rating, no warranty, customs seizure possible on electronics without BIS marking. If a motor fails, replacement takes 4-6 weeks. Racerstar motors are unverified for this thrust class. **Recommended only if budget is the absolute priority.**

### Stores Researched & Status

| Store | Status | Good For | Coverage |
|-------|--------|----------|----------|
| **Robokits.co.in** | Active ✓ | T-Motor motors, Hobbywing ESCs, servos, batteries | 7/11 |
| **Robu.in** | Active ✓ | Frames, FlySky TX, chargers, wiring, batteries | 9/11 |
| **Indian Robo Store** | Active ✓ | Matek FC (cheapest), CF props | 7/11 |
| **RC Mumbai** | Active ✓ | Matek FC & GPS (genuine), FPV parts | 5/11 |
| **IndiaMART** | Active ✓ | ZD850 frame (Rs. 13K), bulk pricing | Varies |
| **Amazon.in** | Active ✓ | FlySky TX, chargers, generic parts | 4/11 |
| **RC Hyderabad** | Active ✓ | ZD850 frame, agriculture drone parts | 6/11 |
| Quadkopters.com | **CLOSED** ✗ | — | — |
| EvoBuzz.com | **Does not exist** ✗ | — | — |
| Quadkart.in | **Not accepting orders** ✗ | — | — |
| Robocraze.com | Active | Beginner parts only — no T-Motor/Matek | 3/11 |
| ThinkRobotics.com | Active | Educational kits only — too basic | 2/11 |
| RCDuniya.com | Active | Basic frames/ESCs — limited selection | 3/11 |
| FlyRobo.in | Active | Entry-level hex kits — different specs | 4/11 |

### Combo Kit Alternative (Different Specs)

**Prayog India ZD850 Combo Kit — Rs. 47,999** includes: ZD850 frame, 6× 5010 360KV motors, 6× 40A ESCs, Pixhawk 2.4.8, GPS, telemetry, OSD. **Different from our spec** (uses Pixhawk clone + 5010 motors instead of Matek H743 + MN3508), but functional out-of-box hex for ~Rs. 48K if you want quick assembly over optimized performance.

---

## Assembly Notes

1. **Frame assembly:** ZD850 unfolds umbrella-style — assemble arms, mount motors, route ESC wires through 20mm carbon tubes
2. **Motor rotation:** 3 CW + 3 CCW in alternating pattern (standard hex)
3. **ESC calibration:** Calibrate all 6 ESCs to same throttle range before first flight
4. **GPS mast:** Mount GPS 10-15cm above frame on carbon/aluminum mast. Twist PDB-ESC wires. Run COMPASS_MOT calibration
5. **CG (Center of Gravity):** Split 2× batteries fore/aft of center plate. Distribute 6 payload stations symmetrically
6. **Release mechanism test:** Test each servo release on ground 20+ times before flying
7. **Start light:** First flights with NO payload → 1kg → 2kg → work up to 3kg
8. **Prop balance:** Carbon fiber 15" props MUST be balanced — unbalanced props cause severe vibration at this size
9. **Battery safety:** 6S LiPo is 22.2V — use XT90 connectors, never XT60. Store in fireproof bag. Parallel harness must have anti-spark XT90S
10. **ArduPilot tuning:** Set `MOT_THST_HOVER` after first hover test. Use autotune in calm weather

---

## Comparison with Variant 7 (RC Payload Drop)

| Spec | Variant 7 (Quad) | Variant 8 (Hex) |
|------|-------------------|------------------|
| Frame | F450 (450mm) | ZD850 (850mm) |
| Motors | 4× 2212 920KV | 6× 3508 380KV |
| Total Thrust | 2,200g | 11,280g |
| Max Payload | 500g (single) | 3,000g (6 × 500g) |
| Battery | 3S 4000mAh | 2× 6S 5000mAh parallel |
| Flight Time (loaded) | 8-12 min | ~11-15 min |
| Release Stations | 1 | 6 (sequential via mission) |
| Flight Controller | Basic FC | Matek H743-WING V3 |
| Cost (India) | ~13,000 | ~74,500-83,000 |
| Cost (Mixed) | ~10,200 | ~60,200 |
| Thrust-to-Weight | 1.5:1 | 1.64:1 (MN3508) / 1.98:1 (MN4012) |
| Complexity | Beginner | Intermediate-Advanced |

---

## Upgrade Paths

- **2:1 TWR safety margin:** Swap MN3508 → MN4012 400KV motors (+Rs. 6,000-12,000)
- **GPS-denied flight:** Add optical flow sensor (PMW3901) for indoor/GPS-jammed operation (+Rs. 720)
- **FPV camera:** Add RunCam + 5.8GHz VTX for live payload drop aiming (+Rs. 3,000-5,000)
- **Autonomous drops:** ArduPilot DO_SET_SERVO missions already support this (no extra hardware)
- **Heavier payload:** Upgrade to MN4012 + 2× 6S 8000mAh for 4-5kg total payload (+Rs. 6,000)
- **16CH TX:** RadioMaster TX16S for individual manual control of all 6 drops (+Rs. 13,500-18,000)

---

## Limitations

- ZD850 frame is large (850mm) — not portable, needs vehicle transport
- 15" carbon fiber props are fragile and expensive (Rs. 1,000-1,350/pair) — budget for spares
- MN3508 motors at Rs. 4,500 each — motor failure is expensive
- TWR of 1.64:1 at full load is below the recommended 2:1 — limited wind tolerance
- No motor redundancy: single motor/ESC failure = crash (unlike octocopter)
- 6S charging needs a capable charger — iMAX B6AC is inadequate (50W, 4.4 hours). Use ISDT D2 or ToolkitRC M7
- Parallel battery setup requires proper XT90S anti-spark parallel harness
- ZD850 is heavier than Tarot 680 (1,210g vs 780g) — necessary trade-off for 15" prop clearance

---

## Price Comparison Research — Is Robokits the Cheapest? (Feb 2026)

**Important note on Quadkopters.com:** Based on research, [Quadkopters.com](https://www.quadkopters.com/) has **shut down its online storefront**. The website still exists but is no longer operating as a retail store. Not a viable purchasing option.

**Note on RCDhamaka.com:** RCDhamaka is still operating but does **not** stock the MN3508 380KV in their current T-Motor inventory. Their prices tend to be on the higher side for specialty motors.

---

### 1. T-Motor MN3508 380KV Motor (need 6)

| Store | Price per unit (incl. GST) | Notes |
|-------|---------------------------|-------|
| **Robokits** | ~Rs. 4,500 (base) / Rs. 5,894 (incl. GST) | In stock |
| **Robu.in** | Price not publicly visible; historically ~Rs. 5,500-6,000 | Listing exists |
| **ElectronicsComp.com** | Not displayed; check directly | Listed |
| **UAV Garage** | Rs. 7,100 (excl. GST) = ~Rs. 8,378 incl. GST | Significantly more expensive |
| **Zbotic.in** | Rs. 21,158 + GST (backorder) | Extremely overpriced / likely error |
| **Amazon.in** | Not listed / no India seller found | N/A |
| **RCDhamaka** | Not stocked (MN3508 380KV absent from catalog) | N/A |

**Verdict:** Robokits at Rs. 5,894 appears to be the **cheapest verified Indian source**. Total for 6 units: Rs. 31,860 - Rs. 35,364.

---

### 2. Hobbywing XRotor 40A ESC (need 6)

| Store | Price per unit (incl. GST) | Notes |
|-------|---------------------------|-------|
| **Robokits** | Rs. 1,250 (base) / Rs. 1,343 (incl. GST) | In stock |
| **Robu.in** | Rs. 1,949 (incl. GST) | In stock |
| **Flipkart (KitsGuru)** | Rs. 2,550 | In stock |
| **Amazon.in** | Listed but price not displayed publicly | Listing exists |
| **IndiaMART (dual pack)** | Rs. 5,100 / 2 = Rs. 2,550 each | Wholesale |
| **Indian Hobby Center** | ~Rs. 1,500-1,800 range | Check directly |

**Verdict:** Robokits at Rs. 1,343 is **cheapest**. Total for 6: Rs. 8,058.

---

### 3. MG90S Servo Motor (need 6)

| Store | Price per unit (incl. GST) | Notes |
|-------|---------------------------|-------|
| **Robokits** | Rs. 102 (base) / Rs. 120 (incl. GST) | In stock |
| **Robu.in** | Rs. 119 - Rs. 239 (varies by variant) | Multiple listings |
| **KTRON India** | Rs. 149 (incl. GST) | In stock |
| **Amazon.in** | ~Rs. 150-250 per unit (varies by seller) | Multiple sellers |
| **ElectronicsComp.com** | ~Rs. 150-180 | Free shipping + COD |
| **DNA Technology** | Rs. 165 (incl. GST) | In stock |

**Verdict:** Robokits at Rs. 120 each is **cheapest or tied with Robu.in's Rs. 119 listing**. Total for 6: Rs. 714-720.

---

### 4. 6S 5200mAh LiPo Battery (need 2)

| Store | Price per unit (incl. GST) | Notes |
|-------|---------------------------|-------|
| **Robokits (GenX)** | Rs. 4,074 (base) / Rs. 4,807 (incl. GST) | In stock |
| **Robu.in (Orange brand)** | ~Rs. 4,500-5,500 (price not public) | Listed |
| **Robocraze (Bonka)** | Rs. 7,999 (discounted from Rs. 9,097) | Different brand, 35C |
| **Amazon.in** | Not readily available from India sellers | Limited options |

**Verdict:** Robokits GenX at Rs. 4,074-4,807 is **cheapest**. Total for 2: Rs. 8,148-9,614.

---

### 5. M8N GPS with Compass (need 1)

| Store | Price (incl. GST) | Notes |
|-------|-------------------|-------|
| **Robokits** | Rs. 1,084 (base) / Rs. 1,532 (incl. GST) | In stock |
| **Robu.in** | Rs. 2,131 - Rs. 2,352 (incl. GST) | Was out of stock on one listing |
| **IndiaMART** | Rs. 1,799 - Rs. 1,850 | Various sellers |
| **Robocraze** | Rs. 1,861 (discounted from Rs. 3,299) | In stock |
| **Amazon.in (REES52)** | ~Rs. 1,500-2,000 (price hidden behind cart) | Listed |

**Verdict:** Robokits at Rs. 1,084-1,532 is **cheapest**. Total for 1: Rs. 1,532.

---

### 6. 15x5.5 Carbon Fiber Propellers - CW+CCW pair (need 4 pairs)

| Store | Price per pair (incl. GST) | Notes |
|-------|---------------------------|-------|
| **Robokits** | Rs. 864/pair | Budget variant |
| **Xbotics.in** | Rs. 980/pair | In stock |
| **Indian Robo Store** | Rs. 901 (discounted from Rs. 1,499) | Varies |
| **IndiaMART** | Rs. 1,350 - Rs. 1,700/pair | Multiple sellers |

**Verdict:** Robokits at Rs. 864/pair is **cheapest**. Total for 4 pairs: Rs. 3,456.

---

### 7. FlySky FS-i6S 10CH Transmitter with Receiver (need 1)

| Store | Price (incl. GST) | Notes |
|-------|-------------------|-------|
| **Robokits** | Rs. 5,734 | **SOLD OUT** |
| **Robu.in** | ~Rs. 5,500-6,000 (official FlySky distributor) | Check stock |
| **IndiaMART** | Rs. 5,050 | Multiple sellers in Delhi |
| **Robocraze** | Rs. 6,599 (discounted from Rs. 8,000) | In stock |
| **FlyRobo.in** | ~Rs. 5,000-5,500 | Check stock |
| **Flipkart** | ~Rs. 5,500-6,500 | Listed |

**Verdict:** **IndiaMART at Rs. 5,050 is cheapest**. Among e-commerce stores, FlyRobo.in or Robu.in around Rs. 5,000-5,500 would be best. Total: Rs. 5,050-5,500.

---

### 8. Flight Controller - H743 Based (need 1)

| Store | Price (incl. GST) | Notes |
|-------|-------------------|-------|
| **Robokits (HPXGRC H743)** | Rs. 4,099 | Budget-friendly, STM32H743, ArduPilot compatible |
| **Robu.in (BLITZ Wing H743)** | ~Rs. 8,799 | Higher-end variant |
| **RC Mumbai (Matek H743-Mini)** | Rs. 11,291 | Premium Matek brand |
| **RC Mumbai (Matek H743-WLITE)** | Rs. 10,233 | Premium Matek brand |
| **IndiaMART (BLITZ Wing H743)** | Rs. 8,799 | Same product |

**Verdict:** Robokits HPXGRC H743 at Rs. 4,099 is **significantly cheapest**. Total: Rs. 4,099.

---

### 9. LiPo Charger 200W+ (need 1)

| Store | Price (incl. GST) | Notes |
|-------|-------------------|-------|
| **Robokits (ISDT Q6 Retro 350W)** | Rs. 4,871 / Rs. 5,748 (incl. GST) | 350W, premium |
| **Robokits (ISDT Q6 Nano 200W)** | Rs. 3,999 | 200W, 8A |
| **Robu.in (ISDT Q6 Nano 200W)** | ~Rs. 4,000-4,500 | Check directly |
| **IndiaMART** | Rs. 1,500 (Q6 Nano) | Wholesale / bulk price |

**Verdict:** For the **Q6 Retro (350W)**, Robokits at Rs. 4,871 is the main Indian source. For the **Q6 Nano (200W)**, Robokits offers it at Rs. 3,999.

---

### Summary Comparison Table

| # | Component | Robokits Price (incl. GST) | Cheapest Alternative | Alt. Price | Robokits Cheapest? |
|---|-----------|---------------------------|---------------------|------------|-------------------|
| 1 | T-Motor MN3508 380KV (x6) | Rs. 5,894/ea | No cheaper verified source found | -- | **YES** |
| 2 | Hobbywing XRotor 40A ESC (x6) | Rs. 1,343/ea | No cheaper found | -- | **YES** |
| 3 | MG90S Servo (x6) | Rs. 120/ea | Robu.in (basic variant) | Rs. 119/ea | **TIED** |
| 4 | GenX 6S 5200mAh LiPo (x2) | Rs. 4,807/ea | No cheaper for same brand/spec | -- | **YES** |
| 5 | M8N GPS w/ Compass (x1) | Rs. 1,532 | No cheaper verified | -- | **YES** |
| 6 | 15x5.5 CF Props CW+CCW (x4 pairs) | Rs. 864/pair | Indian Robo Store | Rs. 901/pair | **YES** |
| 7 | FlySky FS-i6S TX+RX (x1) | Rs. 5,734 (SOLD OUT) | IndiaMART seller | Rs. 5,050 | **N/A (out of stock)** |
| 8 | HPXGRC H743 FC (x1) | Rs. 4,099 | No cheaper H743 found | -- | **YES** |
| 9 | ISDT Q6 Retro 350W Charger (x1) | Rs. 5,748 | ISDT Q6 Nano (200W, lower spec) | Rs. 3,999 | **YES for Retro** |

### Overall Conclusion

**Robokits (robokits.co.in) is the cheapest or tied for cheapest on 8 out of 9 items.** It is clearly the best single-source option for this drone build in India.

1. **Robokits dominates on price** for specialty drone components. Pricing consistently beats Robu.in, Flipkart, Amazon.in, and other retailers.
2. **The only problem item is the FlySky FS-i6S** which is sold out at Robokits. Best alternatives: IndiaMART sellers (~Rs. 5,050) or Robu.in (~Rs. 5,500).
3. **RCDhamaka** does not stock many of these specific items.
4. **Quadkopters.com has closed down** — not a viable option.
5. **Amazon.in** has limited availability for specialized drone components.
6. **DigiKey, Mouser** — these sell electronic components (ICs, resistors, capacitors), NOT drone motors/ESCs/frames/LiPo batteries. Wrong store type entirely.

---

## Hexacopter Frame Options in India — Comprehensive Research (Feb 2026)

**Key Requirement:** Must support at least 13-inch propellers (15-inch preferred), wheelbase 850mm or larger preferred.

---

### CATEGORY 1: 850mm Frames (Supports 15-16" Propellers) — MEETS ALL REQUIREMENTS

#### ZD850 (LJI / JMT) — The Most Popular Option

The ZD850 is the de facto standard for budget 850mm hex frames. Full carbon fiber, foldable-arm hexacopter with 20mm CF tube arms, CNC aluminum folding joints, weight ~1210g. Supports **15-16 inch propellers**.

| Seller | Price | Stock |
|--------|-------|-------|
| **Eagletronics (IndiaMART, Sangli, MH)** | **Rs. 8,000** | Available |
| Yuvvraj Global Traders (IndiaMART, Akola) | Rs. 13,000 | Available |
| ElectronicsComp.com | Rs. 15,006 + 18% GST (~Rs. 17,707) | 11 in stock |
| RC Hyderabad | Rs. 15,000 | Out of stock |
| Hi Tech XYZ | Rs. 15,999 | Unknown |
| Raceway Impex (IndiaMART, Hyderabad) | Rs. 17,000 | Available |
| Robosync | Rs. 17,990 (discounted from Rs. 22,000) + 18% GST | 3 in stock |
| Spectracore Technologies (IndiaMART, Delhi) | Rs. 19,500 | Available |
| RCProduct.in | Rs. 20,999 | In stock |
| Amazon.in (JMT ZD850) | Price not displayed (check link) | Listed |
| AliExpress (Direct import) | $109-140 USD (~Rs. 9,200-11,800) + customs | Free shipping |

**ZD850 Specifications:**
- Wheelbase: 850mm diagonal
- Max propeller: 15-16 inches
- Arm tube: 20mm carbon fiber
- Center plates: 3mm bottom, 1.5mm top
- Weight: ~1210g
- Foldable arms with CNC aluminum joints
- Landing gear: 16mm + 10mm CF tubes, 350mm height
- Recommended motors: 3508-380KV class (size 35-40)

**CHEAPEST ZD850 OPTION: Rs. 8,000 from Eagletronics on IndiaMART (Sangli, Maharashtra).** Contact: Vikrant Suryavanshi, +91-8043847017.

#### Tarot 810 Sport (TL810S01) — Premium 810mm Option

- Motor-to-motor distance: 810mm, Frame diameter: 850mm
- 25mm tube arms, Weight: 1020g
- Supports **1555 propellers (15x5.5 inch)**
- Payload: 3kg, Max power: 4000W

| Seller | Price |
|--------|-------|
| GadgetsDeal.in | Rs. 28,000 |
| Indian Robo Store (IndiaMART, Delhi) | Rs. 31,999 |
| Yuvvraj Global Traders (IndiaMART, Akola) | Rs. 40,000 |

Premium frame, significantly more expensive than ZD850.

---

### CATEGORY 2: 680-700mm Frames (Supports 12-13" Propellers) — MEETS MINIMUM REQUIREMENT

#### Tarot 680 PRO (TL68P00) — 680mm, Max 13" Props

| Seller | Price | Stock |
|--------|-------|-------|
| RC Mumbai | Rs. 11,935 | Out of stock |
| IndiaMART (Bengaluru) | Rs. 12,500 | Available |
| IndiaMART (Delhi) | Rs. 13,000 | Available |
| Moglix | Rs. 14,928 | Available |

**NOTE:** 680mm wheelbase limits to 13-inch max. NOT 15-inch compatible.

#### Xbotics 700mm Hexacopter Frame (Made in India)

| Variant | Price | Stock |
|---------|-------|-------|
| Foldable arm | Rs. 11,682 | 10 in stock |
| Fixed arm | Rs. 11,446 | 10 in stock |
| IndiaMART listing | Rs. 9,900 | Available |

Max propeller ~13-14 inches based on 700mm wheelbase.

#### Other 680mm Options

| Frame | Seller | Price |
|-------|--------|-------|
| Tarot FY680 (budget) | IndiaMART Delhi | Rs. 10,000 |
| HMF S680 | GadgetsDeal.in | Rs. 13,900 (backorder) |
| 680mm Generic CF Hex | RC Mumbai | Rs. 8,000 |

---

### CATEGORY 3: 550mm Frames (Max 10" Props) — DOES NOT MEET REQUIREMENT

| Product | Seller | Price |
|---------|--------|-------|
| HF550/HJ550 | Robocraze | Rs. 1,259 |
| F550 Frame Kit | REES52 (Amazon.in) | ~Rs. 1,775 |
| S550 Frame Kit | Amazon.in / Flipkart | Rs. 1,500-2,500 |
| Probots 6-Axis Kit | Probots | Rs. 1,999 |

**Completely unsuitable** for 13-15 inch propellers. Max 10" props only.

---

### CATEGORY 4: Budget / Alternative Options

#### Xbotics 750mm Aluminum Hexacopter Frame (Made in India)

- **Price: Rs. 2,950** (tax included)
- Material: Aluminum tubes + glass fiber plates + 3D printed motor mounts
- Wheelbase: 750mm, Max propeller: ~13-14" (estimated)
- **Cheapest frame that could potentially meet 13-inch minimum requirement**
- Caveat: Uses aluminum tubing and 3D-printed motor mounts — heavier and less rigid than carbon fiber

---

### Frame Summary — Best Options Ranked by Value

| Rank | Frame | Wheelbase | Max Prop | Price | Source |
|------|-------|-----------|----------|-------|--------|
| **1** | **Xbotics 750 Aluminum** | 750mm | ~13-14" (est.) | **Rs. 2,950** | Xbotics.in |
| **2** | **ZD850 (Eagletronics)** | 850mm | **15-16"** | **Rs. 8,000** | IndiaMART (Sangli, MH) |
| 3 | 680mm Generic CF Hex | 680mm | 12-13" | Rs. 8,000 | RC Mumbai |
| 4 | ZD850 (AliExpress import) | 850mm | 15-16" | ~Rs. 9,200-11,800 | AliExpress + customs |
| 5 | Xbotics 700 CF (IndiaMART) | 700mm | ~13-14" (est.) | Rs. 9,900 | IndiaMART |
| 6 | Tarot FY680 (budget) | 680mm | 12-13" | Rs. 10,000 | IndiaMART |
| 7 | Xbotics 700 CF (direct) | 700mm | ~13-14" (est.) | Rs. 11,446-11,682 | Xbotics.in |
| 8 | Tarot 680 PRO | 680mm | 12-13" | Rs. 12,500+ | IndiaMART |
| 9 | ZD850 (various Indian stores) | 850mm | 15-16" | Rs. 15,000-20,999 | Multiple sellers |

### Frame Recommendations

**Best overall value for 15" prop requirement:** ZD850 from Eagletronics on IndiaMART at Rs. 8,000.

**Cheapest frame for 13" props:** Xbotics 750mm Aluminum at Rs. 2,950 (but aluminum, not CF — heavier & less rigid).

**No hex frames under Rs. 5,000 support 13"+ propellers.** Sub-Rs. 5,000 frames (F550, S550) are all 550mm and max out at 10-inch props.

**Should you 3D print the frame? NO.**
- 3D printed PLA/PETG cannot handle motor vibration at hexacopter frequencies
- CF tubes + 3D printed joints = Rs. 5,000-8,000 DIY — barely cheaper than ZD850 at Rs. 8,000
- You lose CNC aluminum folding joints (critical for arm alignment and transport)
- ZD850 at Rs. 8,000 gives full CF arms + CNC aluminum joints + landing gear included

---

## Optimized Build Cost (Feb 2026)

| Source | Item | Cost (INR) |
|--------|------|------------|
| Robokits cart (31 items) | Motors, ESCs, servos, batteries, FC, charger, GPS, props, wiring | Rs. 68,915 |
| IndiaMART (Eagletronics, Sangli) | ZD850 Frame | Rs. 8,000 |
| IndiaMART / Robu.in | FlySky FS-i6S TX+RX | Rs. 5,050-5,500 |
| Robokits shipping | DTDC | Rs. 150 |
| **TOTAL** | | **Rs. 82,115 - 82,565** |

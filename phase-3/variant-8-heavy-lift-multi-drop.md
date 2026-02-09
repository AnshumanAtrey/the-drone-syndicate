# Variant 8 — Heavy-Lift Hexacopter Multi-Drop (6 x 500g Payloads)

**Standalone Total Cost: Rs. 55,000 - 78,000** (depending on source & tier)

Heavy-lift hexacopter that carries and individually releases 6 payloads of 400-500g each (3kg total). Uses 6x servo-actuated pin-pull release mechanisms triggered sequentially via Pixhawk AUX outputs. No AI, no cameras — pure RC + autopilot control with ArduPilot.

> **Why hexacopter?** A quadcopter with 2212 motors produces ~2,200g thrust — can't even lift 3kg payload + drone weight. Six 3508 380KV motors on 6S produce **11,280g thrust**, giving a safe 1.74:1 thrust-to-weight ratio at full 3kg load.

---

## Recommended Build: MN3508 380KV + 6S (Option A)

### Component Breakdown

| # | Component | Spec | Best Price (INR) | Best Source | Alt Price (INR) | Alt Source |
|---|-----------|------|-----------------|-------------|-----------------|------------|
| 1 | Frame | Tarot 680 PRO Hexacopter (680mm, foldable, 3K CF) | 9,360 | AliExpress ($104) | 12,500 | IndiaMART |
| 2 | Motors x6 | MN3508 380KV Brushless (T-Motor/SunnySky) | 21,600 | AliExpress ($40/pc) | 27,000 | Robokits (T-Motor, 4,500/pc) |
| 3 | ESCs x6 | 40A 2-6S BLHeli ESC | 3,558 | RCDuniya (593/pc) | 7,500 | Robokits (Hobbywing XRotor, 1,250/pc) |
| 4 | Props x3 pairs | 15x5.5 Carbon Fiber CW+CCW | 4,050 | IndiaMART (1,350/pair) | 4,995 | AliExpress ($18.50/pair) |
| 5 | Flight Controller | Pixhawk 2.4.8 PX4 (6 AUX outputs for servos) | 2,250 | AliExpress ($25) | 5,500 | IndiaMART |
| 6 | GPS Module | NEO M8N/M9N multi-GNSS | 1,620 | AliExpress (~$18) | 2,099 | Robocraze |
| 7 | Battery | 6S 22.2V 10000mAh 25C LiPo | 8,320 | Robokits (GenX) | 9,000 | AliExpress ($100) |
| 8 | RC Transmitter + Rx | FlySky FS-i6X + iA10B (10CH) | 3,389 | IndiaMART | 3,960 | AliExpress ($44) |
| 9 | Release Servos x6 | MG90S Metal Gear Micro Servo | 1,080 | AliExpress (~$2/pc) | 1,500 | Robu.in (~250/pc) |
| 10 | Release Mechanism | DIY pin-pull latch (steel wire + 3D print) x6 | 300 | DIY | 600 | DIY |
| 11 | Landing Gear | Tall fixed carbon fiber skid (200mm clearance) | 800 | IndiaMART | 4,200 | ElectronicsComp (Tarot retractable) |
| 12 | PDB + BEC + Wiring | Heavy-duty PDB, 5V 5A BEC, XT90, 12AWG wire | 1,000 | Robu.in | 1,200 | Amazon.in |
| 13 | Charger | iMAX B6AC 80W (supports 6S) | 1,801 | Robocraze | 2,790 | AliExpress ($31) |
| 14 | Spare Props | 15x5.5 CF (1 extra pair) | 1,350 | IndiaMART | 1,665 | AliExpress |

---

## Build Cost Summary

### Mixed Source (Cheapest per item — India + AliExpress)

| Component | Price (INR) | Source |
|-----------|-------------|--------|
| Tarot 680 PRO frame | 9,360 | AliExpress |
| 6x MN3508 380KV motors | 21,600 | AliExpress |
| 6x 40A ESC | 3,558 | RCDuniya (India) |
| 3 pairs 15x5.5 CF props | 4,050 | IndiaMART |
| Pixhawk 2.4.8 | 2,250 | AliExpress |
| GPS M9N | 1,620 | AliExpress |
| 6S 10000mAh LiPo | 8,320 | Robokits (India) |
| FlySky FS-i6X + iA10B | 3,389 | IndiaMART |
| 6x MG90S servos | 1,080 | AliExpress |
| Release mechanism (DIY) | 300 | DIY |
| Landing gear (fixed) | 800 | IndiaMART |
| PDB + BEC + wiring | 1,000 | Robu.in |
| iMAX B6AC charger | 1,801 | Robocraze |
| Spare props (1 pair) | 1,350 | IndiaMART |
| **TOTAL** | **~60,478** | |

### All India (no import, 1-week delivery)

| Component | Price (INR) | Source |
|-----------|-------------|--------|
| Tarot 680 PRO frame | 12,500 | IndiaMART |
| 6x MN3508 380KV (T-Motor) | 27,000 | Robokits |
| 6x Hobbywing XRotor 40A ESC | 7,500 | Robokits |
| 3 pairs 15x5.5 CF props | 4,197 | IndiaMART |
| Pixhawk 2.4.8 | 5,500 | IndiaMART |
| GPS M9N | 2,099 | Robocraze |
| 6S 10000mAh LiPo | 8,320 | Robokits |
| FlySky FS-i6X + iA10B | 3,389 | IndiaMART |
| 6x MG90S servos | 1,500 | Robu.in |
| Release mechanism (DIY) | 600 | DIY |
| Landing gear (fixed) | 800 | IndiaMART |
| PDB + BEC + wiring | 1,000 | Robu.in |
| iMAX B6AC charger | 1,801 | Robocraze |
| Spare props (1 pair) | 1,399 | IndiaMART |
| **TOTAL** | **~77,605** | |

> **Savings with China import: ~Rs 17,000 (22%)** — but 3-6 week wait + customs risk.

---

## Thrust & Performance Data

### Motor: MN3508 380KV + 15x5 CF Props on 6S (22.2V)

| Throttle | Current/Motor | Thrust/Motor | 6-Motor Total | Power/Motor |
|----------|--------------|-------------|---------------|-------------|
| 50% | 3.6A | 820g | 4,920g | 80W |
| 65% | 6.1A | 1,200g | 7,200g | 135W |
| 75% | 9.5A | 1,500g | 9,000g | 211W |
| 100% | 13.3A | 1,880g | **11,280g** | 295W |

*Source: T-Motor MN3508 official thrust table*

---

## Weight Budget

| Item | Weight |
|------|--------|
| Tarot 680 PRO frame | 780g |
| 6x MN3508 380KV motors | 618g (103g each) |
| 6x 40A ESCs | 168g (~28g each) |
| 6x 15x5 CF props | 162g (~27g each) |
| 6S 10000mAh LiPo | 1,350g |
| Pixhawk 2.4.8 + GPS + RX | 80g |
| PDB + BEC + wiring | 140g |
| 6x MG90S servos + release mounts | 174g (~29g each) |
| Landing gear (fixed) | 100g |
| **Drone Dry Weight** | **~3,572g** |
| **Payload (6 x 500g)** | **3,000g** |
| **All-Up Weight (AUW)** | **~6,572g** |

### Thrust-to-Weight Ratios

| Condition | AUW | Thrust | Ratio | Status |
|-----------|-----|--------|-------|--------|
| Full load (6 payloads) | 6,572g | 11,280g | **1.72:1** | Safe, moderate agility |
| 5 payloads (1 dropped) | 6,072g | 11,280g | **1.86:1** | Good |
| 3 payloads (3 dropped) | 5,072g | 11,280g | **2.22:1** | Very good |
| Empty (all dropped) | 3,572g | 11,280g | **3.16:1** | Excellent, fast return |

---

## Flight Time Estimates

| Battery | Payload | Hover Throttle | Hover Current | Flight Time |
|---------|---------|---------------|--------------|-------------|
| 6S 10000mAh | Full (3kg) | ~57% | ~27A | **14-16 min** |
| 6S 10000mAh | Empty (0kg) | ~31% | ~11A | **30-35 min** |
| 6S 5000mAh | Full (3kg) | ~52% | ~23A | **8-9 min** |
| 6S 10000mAh | Progressive 6-drop mission | varies | avg ~20A | **18-20 min** |

> **Best scenario:** Progressive drop mission — as each 500g payload releases, the drone gets lighter and more efficient. Total mission time ~18-20 min on a single 6S 10000mAh battery.

---

## Multi-Payload Release Mechanism

### Design: Pin-Pull Servo Release (x6)

```
Each station:
    [Servo MG90S] ──pulls──> [2mm steel locking pin]
                                    │
                              [Payload hook/latch]
                                    │
                              [Payload hangs here]

    Flip switch → servo rotates 90° → pin pulls out → payload drops
```

- **Servo:** MG90S metal gear (2.2 kg-cm torque, 13.4g weight)
- **Latch:** Bent 2mm steel wire hook OR 3D-printed clip
- **Mount:** Between/below motor arms on Tarot 680 frame underside
- **Build time:** ~30 min per station, 3 hours total for all 6

### Wiring

```
                    ┌─ AUX1 → Servo 1 (signal)
                    ├─ AUX2 → Servo 2 (signal)
   Pixhawk AUX ────├─ AUX3 → Servo 3 (signal)
   (6 outputs)     ├─ AUX4 → Servo 4 (signal)
                    ├─ AUX5 → Servo 5 (signal)
                    └─ AUX6 → Servo 6 (signal)

   Dedicated 5V 5A BEC ──> Servo power rail (DO NOT power from receiver)
```

**CRITICAL:** All 6 servos must be powered from a **dedicated 5V 5A BEC**, NOT from the Pixhawk/receiver rail. 6 servos drawing power simultaneously will brown out the receiver.

### ArduPilot Configuration

```
# Map AUX outputs to relay functions
SERVO9_FUNCTION = 51    (Relay1 — Drop Station 1)
SERVO10_FUNCTION = 52   (Relay2 — Drop Station 2)
SERVO11_FUNCTION = 53   (Relay3 — Drop Station 3)
SERVO12_FUNCTION = 54   (Relay4 — Drop Station 4)
SERVO13_FUNCTION = 55   (Relay5 — Drop Station 5)
SERVO14_FUNCTION = 56   (Relay6 — Drop Station 6)

# Set servo PWM values
SERVOn_MIN = 1000       (locked position)
SERVOn_MAX = 2000       (release position)
```

**Channel usage:** You only need 1-3 RC channels for release control:
- **Option A:** 1 switch = "drop next" (sequential release via Lua script)
- **Option B:** 3 switches = pairs (drop 1+2, drop 3+4, drop 5+6)
- **Option C:** 6 individual switches (needs 12CH TX like RadioLink AT10II)

### TX/RX Options for 6 Servo Channels

| Transmitter | Channels | Spare After Sticks+Mode | Price (INR) | Verdict |
|------------|----------|------------------------|-------------|---------|
| FlySky FS-i6X + iA10B | 10 | 5 spare | 3,389 | Works with paired drops or Lua sequential |
| RadioLink AT10II + R12DS | 12 | 7 spare | ~9,000 | Comfortable, 1 channel per drop |
| FrSky Taranis QX7 + X8R | 16 | 11 spare | ~13,500 | Overkill, but OpenTX programmable |

> **Recommendation:** FlySky FS-i6X is enough if you use Pixhawk Lua scripting for sequential drops. One switch = one drop. Saves Rs 6,000+ over RadioLink.

---

## Where to Buy (Optimized)

### If buying mixed (India + China):
| Store | What to buy |
|-------|------------|
| **AliExpress** | Tarot 680 frame, 6x 3508 motors, Pixhawk 2.4.8, GPS, 6x servos |
| **Robokits** | 6S 10000mAh battery (GenX) |
| **RCDuniya / IndiaMART** | 6x 40A ESCs, 15x5.5 props, landing gear |
| **IndiaMART** | FlySky FS-i6X + iA10B, spare props |
| **Robocraze** | iMAX B6AC charger |
| **Robu.in** | PDB, BEC, wiring, connectors |

### If buying all India (fast):
| Store | What to buy |
|-------|------------|
| **Robokits** | 6x T-Motor MN3508 380KV, 6x Hobbywing XRotor 40A, 6S battery, charger |
| **IndiaMART** | Tarot 680 frame, Pixhawk 2.4.8, props, FlySky TX, landing gear |
| **Robocraze** | GPS M9N, iMAX B6AC charger |
| **Robu.in** | Servos, PDB, BEC, wiring |

---

## Assembly Notes

1. **Frame assembly:** Tarot 680 PRO is foldable — assemble arms, mount motors, route ESC wires through arms
2. **Motor rotation:** 3 CW + 3 CCW in alternating pattern (standard hex configuration)
3. **ESC calibration:** Calibrate all 6 ESCs to the same throttle range before first flight
4. **CG (Center of Gravity):** Mount battery at frame center. Distribute 6 payload stations symmetrically around the frame
5. **Release mechanism test:** Test each servo release on the ground 10+ times before flying
6. **Start light:** First flights with NO payload, then test with 1kg, 2kg, and work up to 3kg
7. **Prop balance:** Carbon fiber props MUST be balanced — unbalanced 15" props cause severe vibration
8. **Battery safety:** 6S LiPo is 22.2V — use XT90 connectors, never XT60. Store in fireproof bag.
9. **ArduPilot tuning:** Set `MOT_THST_HOVER` after first hover test. Use autotune in calm weather.

---

## Payload Station Layout (Top View)

```
         Motor 1
          /    \
   Motor 6      Motor 2
    |    [FRAME]    |
   Motor 5      Motor 3
          \    /
         Motor 4

   Payload stations P1-P6 mounted between motor arms:
   P1 (between M1-M2), P2 (between M2-M3), P3 (between M3-M4)
   P4 (between M4-M5), P5 (between M5-M6), P6 (between M6-M1)
```

---

## Comparison with Variant 7 (RC Payload Drop)

| Spec | Variant 7 (Quad) | Variant 8 (Hex) |
|------|-------------------|------------------|
| Frame | F450 (450mm) | Tarot 680 PRO (680mm) |
| Motors | 4x 2212 920KV | 6x 3508 380KV |
| Total Thrust | 2,200g | 11,280g |
| Max Payload | 500g (single) | 3,000g (6 x 500g) |
| Battery | 3S 4000mAh | 6S 10000mAh |
| Flight Time (loaded) | 8-12 min | 14-16 min |
| Release Stations | 1 | 6 (sequential) |
| Cost (India) | ~13,000 | ~77,600 |
| Cost (Mixed) | ~10,200 | ~60,500 |
| Thrust-to-Weight | 1.5:1 | 1.72:1 |
| Complexity | Beginner | Intermediate |

---

## Upgrade Paths

- **GPS-denied flight:** Add optical flow sensor (PMW3901) for indoor/GPS-jammed operation (+Rs 720 AliExpress)
- **FPV camera:** Add RunCam + 5.8GHz VTX for live payload drop aiming (+Rs 3,000-5,000)
- **Autonomous drops:** Add companion computer (Jetson Nano / RPi 4) + DroneKit for waypoint-based auto-drops (+Rs 8,000-10,000)
- **Heavier payload:** Upgrade to 6S 16000mAh battery and larger props for 4-5kg total payload (+Rs 4,000)
- **12CH TX:** RadioLink AT10II for individual control of all 6 drops (+Rs 9,000)

---

## Limitations

- 6S LiPo batteries are expensive (Rs 8,000+) and heavy (1.35kg)
- Tarot 680 PRO frame is large (680mm) — not portable, needs vehicle transport
- 15" carbon fiber props are fragile and expensive (Rs 1,350/pair) — budget for spares
- 3508 motors cost Rs 3,600-4,500 each — motor failure is expensive
- No redundancy: single motor/ESC failure = crash (unlike octocopter)
- 6S charging needs a capable charger — iMAX B6AC works but is slow (80W). Consider ISDT Q6 Pro for faster charging.
- Customs risk on AliExpress orders >Rs 5,000 — split orders

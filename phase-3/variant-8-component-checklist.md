# Variant 8 — Component Checklist & Compatibility

**Mission:** Hexacopter carrying 6 x 500g payloads (3kg total), dropping them individually at GPS waypoints via ArduPilot DO_SET_SERVO commands.

**Key Numbers:** 11,280g thrust | 6,863g AUW loaded | 1.64:1 TWR | ~14-15 min flight (drop mission)

---

## Final Component List

| # | Component | Qty | Robokits Price (ea) | Why This | Compatible? |
|---|-----------|-----|-------------------|----------|-------------|
| 1 | **T-Motor MN3508 380KV** | 6 | Rs. 2,957 + GST | 1,880g thrust/motor on 6S with 15x5 props. Industry standard, EZO bearings, 1000hr MTBF. Academic test data available | ✓ Proven with ZD850 frame, 15x5 props, 6S batteries |
| 2 | **Hobbywing XRotor 40A 2-6S ESC** | 6 | Rs. 1,138 | 40A rating = 3x headroom over 13.3A motor max. Supports 6S. OPTO (no BEC) — fine since FC has built-in BEC | ⚠ PWM only (no DShot). Works with ArduPilot `MOT_PWM_TYPE=0`. Loses telemetry + faster response |
| 3 | **MG90S Semi Metal Gear Servo** | 10 | Rs. 102 | 1.8 kg-cm torque = 3.6x safety factor for 500g pin-pull release. 14g each. 4 extras as spares | ✓ Powered by Matek H743's 8A BEC. 6x stall = 4.2A << 8A capacity |
| 4 | **GenX 22.2V 6S 5200mAh 40C LiPo** | 2 | Rs. 4,074 | Indian brand, BIS certified. 2x parallel = 10,400mAh. 40C = 208A/pack >> 80A max system draw. Comes with XT90S | ✓ 6S matches motor+ESC voltage. Parallel setup is standard practice |
| 5 | **UBlox Neo M8N GPS + Compass** | 1 | Rs. 1,084 + GST | 2-4m accuracy — sufficient for waypoint payload drops. ArduPilot compatible | ✓ UART+I2C to Matek H743. Mount on 10-15cm mast to avoid motor interference |
| 6 | **ISDT Q6 Retro 350W 16A Charger** | 1 | Rs. 4,871 + GST | 350W at 6S = ~15.7A charge rate. GenX recommends 1C max = 5.2A = **60-70 min per pack** | ⚠ DC-only — needs external 24V 400W PSU with XT60 (~Rs. 2,000-2,500 extra) |
| 7 | **Amass XT90 Female Connector** | 2 | In cart | 90A continuous / 120A burst. For PDB-side connections | ✓ Batteries come with XT90S (anti-spark) already |
| 8 | **10AWG Silicone Wire (Red + Black)** | 1m each | In cart | Rated ~100A continuous. For battery-to-PDB main power leads | ✓ Handles 80A peak system current with margin |

### Buy from Other Stores (NOT on Robokits)

| # | Component | Price | Store | Why This |
|---|-----------|-------|-------|----------|
| 9 | **Matek H743-WING V3 FC** | Rs. 7,295 | Indian Robo Store | 13 PWM outputs (6 motor + 6 servo). Built-in 8A servo BEC. Official ArduPilot target. The HPXGRC H743 on Robokits has unknown output count, weak BEC, and zero community support — **do not use it** |
| 10 | **ZD850 850mm CF Hex Frame** | Rs. 8,000-13,000 | IndiaMART (Eagletronics) | 850mm wheelbase = 44mm clearance for 15" props. Supports 6kg+ payload class. 20mm CF arms, foldable |
| 11 | **15x5 (1550) CF Propellers** | ~Rs. 1,700/pair | Indian Robo Store | T-Motor's rated prop for MN3508. Draws 13.3A at max (within 14A limit). The 1555 (15x5.5) in the Robokits cart draws ~14.6A — **exceeds motor rating, do not use** |

---

## Will It Carry & Drop 6 x 500g?

**Yes.** Here's why:

| Check | Value | Pass? |
|-------|-------|-------|
| Total thrust | 11,280g (6x MN3508 on 6S + 15x5) | ✓ |
| All-up weight (loaded) | ~6,863g (3,863g drone + 3,000g payload) | ✓ |
| Excess thrust at hover | 4,417g | ✓ |
| TWR at full load | 1.64:1 (functional in calm weather) | ⚠ Below 2:1 ideal — fly <15 km/h wind |
| TWR after 3 drops | 2.10:1 (excellent) | ✓ |
| TWR empty | 2.92:1 (outstanding) | ✓ |
| Servo torque vs payload | 1.8 kg-cm vs 0.5 kg-cm needed (3.6x margin) | ✓ |
| FC servo outputs | 6 dedicated PWM outputs (Matek H743 outputs 7-12) | ✓ |
| Drop method | ArduPilot DO_SET_SERVO at GPS waypoints — fully autonomous | ✓ |
| Flight time (6-drop mission) | ~14-15 min on 2x 5200mAh parallel | ✓ |

**Limitation:** TWR of 1.64:1 at full load means limited wind tolerance. Each drop improves performance. Upgrade to MN4012 400KV motors (+Rs. 6,000-12,000) for 1.98:1 TWR if budget allows.

---

## Estimated Total Cost

| Source | Items | Subtotal |
|--------|-------|----------|
| **Robokits** | Motors, ESCs, servos, batteries, GPS, charger, connectors, wire | ~Rs. 55,000-60,000 |
| **Indian Robo Store** | Matek H743-WING V3 + 15x5 props (x4 pairs) | ~Rs. 14,100 |
| **IndiaMART** | ZD850 frame | ~Rs. 8,000-13,000 |
| **Amazon/Local** | 24V PSU for charger + misc (zip ties, GPS mast, velcro, LiPo bag, multimeter) | ~Rs. 3,000-4,000 |
| | **TOTAL** | **~Rs. 80,000-92,000** |

---

## Tools, Supplies & Accessories

### Add to Robokits Cart (Available)

| Item | Product Name | Qty | Price |
|---|---|---|---|
| **XT90S Anti-Spark Pair** | Amass XT90S Male/Female Pair (XT90S-M/F-H) | 2 pairs | Rs. 162/pair = Rs. 324 |
| **Heat Shrink 3mm Black** | WOER Industrial Grade HST 3mm | 3m | ~Rs. 87 |
| **Heat Shrink 5mm Black** | WOER Industrial Grade HST 5mm | 2m | ~Rs. 34 |
| **Heat Shrink 8mm Yellow** | WOER Industrial Grade HST 8mm | 2m | ~Rs. 48 |
| **Servo Extension 12"** | Servo Extension Cable 12" Male-Female | 6x | Rs. 25 each = Rs. 150 |
| **Cell Voltage Checker** | Li-Po & Li-Ion 1-8S Voltage Checker + Alarm | 1 | Rs. 82 |
| **Robokits extras subtotal** | | | **~Rs. 725** |

> **Note:** Build the parallel battery harness yourself — use the 2x XT90S pairs above + the 10AWG silicone wire already in your main cart. No pre-made harness needed.

### Buy from Amazon / Local Shop (Not on Robokits)

| Item | Why Needed | Est. Price |
|---|---|---|
| **Multimeter** | Verify M8N GPS wire colors before soldering — critical to avoid dead module | Rs. 300-500 |
| **Soldering iron** | GPS wires must be soldered directly to Matek H743 solder pads | Rs. 500-1,500 (skip if you own one) |
| **24V 400W PSU (XT60 output)** | ISDT Q6 Retro is DC-only, won't work without external power supply | Rs. 2,000-2,500 |
| **GPS mast (15-20cm)** | Hex has 6 motors — needs taller mast to avoid compass interference | Rs. 150-300 |
| **Velcro straps (wide, 3x)** | GenX batteries mount externally (54mm height > 35mm plate gap) | Rs. 100-200 |
| **Non-slip battery pad** | Stops batteries sliding during flight maneuvers | Rs. 50-100 |
| **LiPo safe bag** | Storage + charging safety in Indian summer heat | Rs. 300-500 |
| **Zip ties (assorted)** | Wire management on arms, ESC mounting, GPS cable routing | Rs. 50-100 |
| **Loctite Blue (thread locker)** | Motor mount M3 bolts loosen from vibration — apply to all 24 bolts | Rs. 150-250 |
| **Double-sided foam tape (3M)** | FC vibration dampening mount inside frame | Rs. 100-200 |
| **Amazon/Local subtotal** | | **~Rs. 3,700-6,150** |

---

## Important Notes (Read Before Assembly)

### CRITICAL — Will Break Things If Ignored

1. **Matek H743 BEC Jumper — LEAVE AT 5V**
   The board has a solder jumper for servo BEC voltage (5V / 6V / 7.2V). Default is 5V. MG90S servos are rated 4.8-6V. Setting 7.2V **will fry all 6 servos instantly**. Do not touch this jumper.

2. **M8N GPS Connector Won't Plug Into Matek H743**
   The M8N comes with a 6-pin Pixhawk connector. Matek H743-WING V3 uses **solder pads**, not pin headers. You must:
   - Cut the connector off
   - Solder GPS serial wires to **UART2 (TX2/RX2)** pads
   - Solder compass wires to **I2C1 (DA1/CL1)** pads
   - **Use a multimeter to verify each wire** — colors on cheap M8N modules are frequently mislabeled. Swapped TX/RX = no GPS lock. Swapped VCC/GND = dead module.

3. **Charge at 1C ONLY (5.2A) — NOT 16A**
   GenX specifies 1C max charge rate. Charging at the Q6 Retro's full 16A (~3C) will damage cells and risk puffing/fire. Set charge current to **5.2A**. Real charge time = **60-70 min per pack**, not 25 min.

### IMPORTANT — Plan Around These

4. **GenX Batteries Don't Fit Between ZD850 Plates**
   Battery height is 54mm. ZD850 plate gap is ~35mm. **Mount externally on top plate** with Velcro straps + non-slip mat. This is standard practice on hex builds.

5. **Fake u-blox GPS Chip Risk**
   At Rs. 1,084 (~$12), moderate-high chance of counterfeit chip. On arrival, connect to **u-center** via USB and verify chip ID reads "NEO-M8N." Signs of fake: satellite count stuck at 0-3, no lock in clear sky. If fake, order from verified source (Rs. 2,000-3,000).

6. **GPS Mast Height — Use 15-20cm, Not 10cm**
   Hexacopters have 6 motors creating more magnetic interference than quads. Mount GPS/compass on a **15-20cm mast**. Run `COMPASS_MOT` calibration after first power-up. Some QMC5883L compass chips have an ArduPilot scaling bug — set `COMPASS_TYPEMASK` to force detection if compass readings look wrong.

7. **Landing Gear Clearance Check**
   ZD850 stock landing gear gives 200-250mm ground clearance. With servo-release mechanisms + hanging 500g payloads, clearance gets tight. **Measure your full release mechanism length** before first flight. If payloads hang lower than ~150mm from the bottom plate, extend the landing gear.

### GOOD TO KNOW

8. **GenX True C-Rating is ~28-30C (Not 40C)**
   Marketed as 40C but real-world internal resistance suggests 28-30C. Still adequate — 30C x 5.2Ah = 156A per pack >> 80A system max. Not a problem, just know the real number.

9. **Indian Heat + LiPo Safety**
   Summer temps (40-45°C) + motor heat can push batteries to 55-60°C. Never charge immediately after flight — wait 15+ min for cooldown. Store at 3.85V/cell (use ISDT Q6's storage charge mode). If batteries puff even slightly, **retire them immediately**.

10. **ISDT Q6 Retro Field Charging**
    DC-only charger. At home: use 24V 400W PSU with XT60 output. In field: runs from car battery (12V) but drops to ~170W = half charge speed. The Q6 Retro has 1.5A/cell balance current (best in class) — good for 6S balance charging.

11. **ESC Calibration is Timing-Sensitive**
    XRotor 40A uses PWM (not DShot). Use ArduPilot's all-at-once ESC calibration with `MOT_PWM_TYPE=0`. Follow the beep sequence carefully — miscalibrated ESCs cause uneven motor spin and unstable flight.

12. **DO_SET_SERVO Output Mapping**
    ArduPilot uses direct 1:1 numbering. Servo outputs 7-12 on Matek H743 map to `SERVO7_FUNCTION` through `SERVO12_FUNCTION`. Set each to GPIO or PassThru. In mission: `DO_SET_SERVO(9, 1100)` actuates output 9 directly. Motor outputs (1-6) and servo outputs (7-12) run on **separate timer groups** — zero conflict.

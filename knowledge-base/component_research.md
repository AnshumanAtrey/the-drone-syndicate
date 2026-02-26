# Heavy-Lift Hexacopter Component Research
## 6x500g Sequential Payload Drops | 3kg Total Payload | ~6.5kg AUW

---

## 1. BATTERY: 6S 10000mAh LiPo

### 1.1 Actual Weights by Brand

| Brand | Model | Capacity | C-Rating | Weight | Dimensions (mm) |
|-------|-------|----------|----------|--------|-----------------|
| Tattu (Gens Ace) | G-Tech 30C | 10000mAh 6S | 30C | 1350g (+/-20g) | 176 x 66 x 58 |
| Tattu | Standard 30C | 10000mAh 6S | 30C | 1357g | 175 x 65 x 58 |
| Tattu Plus | Smart 25C | 10000mAh 6S | 25C | 1442g | 165 x 65 x 62 |
| HRB | Standard 25C | 10000mAh 6S | 25C | 1226g | 165 x 64 x 63 |
| CNHL | Racing 100C | 10000mAh 6S | 100C | 1200g | 177 x 66 x 49 |

**Key finding:** Weight ranges from 1200g (CNHL) to 1442g (Tattu Plus). Budget for ~1.3-1.4kg for a quality battery. The CNHL at 1200g with 100C is remarkably light but verify real-world C-rating claims.

### 1.2 C-Rating Requirements

**Your load:** 6 motors x 15-20A each at hover = 90-120A total draw

| Battery Config | Capacity | C-Rating | Max Continuous Amps | Sufficient? |
|----------------|----------|----------|---------------------|-------------|
| 1x 10000mAh 25C | 10Ah | 25C | 250A | YES - large headroom |
| 1x 10000mAh 30C | 10Ah | 30C | 300A | YES - large headroom |
| 2x 5000mAh 50C parallel | 10Ah effective | 50C per pack | 250A per pack / 500A total | YES - overkill |

**Verdict:** Even a 25C 10000mAh battery delivers 250A continuous, which is well above your 90-120A hover draw. C-rating is NOT a concern at this capacity. A 25C pack is sufficient. Higher C-ratings (50C+) only matter for aggressive maneuvering or emergency full-throttle.

**Important caveat:** Many budget manufacturers inflate C-ratings. A "25C" from Tattu/Gens Ace is genuinely rated. A "100C" from a budget brand may deliver real-world 40-50C. Stick with verified brands (Tattu, Gens Ace) for reliable ratings.

### 1.3 Single 10000mAh vs 2x 5000mAh Parallel

**Weight comparison:**
- 1x Tattu 10000mAh 30C: ~1350g
- 2x Gens Ace 5000mAh 45C: ~716g x 2 = ~1432g
- 2x Gens Ace 5000mAh 60C: ~755g x 2 = ~1510g

**Analysis:**

| Factor | 1x 10000mAh | 2x 5000mAh Parallel |
|--------|-------------|---------------------|
| Total weight | ~1350g | ~1432-1510g |
| Weight penalty | Baseline | +80-160g heavier |
| Wiring complexity | Simple - one connector | Needs parallel harness, 2x balance leads |
| Failure mode | Single point of failure | Redundancy: one pack fails, other still works (degraded) |
| CG placement | One large mass to place | Can split fore/aft for CG balance |
| Charging | One charge cycle | Two charge cycles OR parallel charge board |
| Voltage sag under load | More sag (longer internal path) | Less sag (parallel internal resistance halved) |
| Physical fit on frame | Large brick, may not fit some frames | Two smaller packs, more mounting flexibility |

**Recommendation:** For a heavy-lift hexacopter, **2x 5000mAh 50C in parallel is the better choice** despite the ~100g weight penalty because:
1. CG balancing is easier (split mounting)
2. Internal resistance is halved, reducing voltage sag
3. Physical mounting is more flexible on hex frames
4. Redundancy benefit (partial function on one pack)

### 1.4 Flight Time Estimate at Hover (6.5kg AUW)

**Using T-Motor MN3508 380KV data with 15x5 prop on 6S:**
- Max thrust per motor: ~1880g at 13.3A
- Hover requires each motor to support: 6500g / 6 = ~1083g per motor
- 1083g is ~58% of max thrust (1880g)
- At ~58% throttle, estimated current per motor: ~6-8A (based on typical efficiency curves where current scales roughly with thrust^1.5)
- Total hover current: 6 x 7A (midpoint) = ~42A

**Flight time calculation:**
- Usable capacity: 10000mAh x 0.80 (never discharge below 20%) = 8000mAh = 8Ah
- Flight time = 8Ah / 42A x 60 = ~11.4 minutes at full 6.5kg AUW

**With payload drops (weight decreasing):**
- Start: 6.5kg -> ~42A draw -> drops first 500g payload
- After all 6 drops: 3.5kg AUW -> ~25A draw
- Average draw across mission: ~33A (rough midpoint)
- Effective flight time: 8Ah / 33A x 60 = ~14.5 minutes

**Conservative estimate:** 10-15 minutes total mission time depending on payload drop schedule and wind. Plan for 12 minutes with 20% reserve.

**Power validation:**
- Using the 170 W/kg rule of thumb from OmniCalculator:
- 6.5kg x 170W = 1105W hover power
- 1105W / 22.2V = ~50A (roughly aligns with our 42A estimate; difference is due to system losses)

### 1.5 Parallel Config: 2x 6S 5000mAh 50C vs 1x 6S 10000mAh 25C

| Parameter | 2x 5000mAh 50C Parallel | 1x 10000mAh 25C |
|-----------|------------------------|------------------|
| Effective capacity | 10000mAh | 10000mAh |
| Max continuous current | 500A (250A per pack) | 250A |
| Weight | ~1432g (2x 716g) | ~1350-1442g |
| Internal resistance | ~Half (parallel) | Standard |
| Voltage sag at 40A | Lower (better) | Higher |
| Cost (approx) | $80-100 (2 packs) | $90-120 (1 pack) |
| Charging convenience | Worse (2 packs) | Better (1 pack) |

**Winner: 2x 5000mAh 50C parallel** for voltage sag performance and redundancy, if you accept the wiring complexity.

---

## 2. PROPELLERS: 1555 (15x5.5 inch) Carbon Fiber

### 2.1 Prop Clearance on 850mm Hex Frame

**Hexacopter geometry:** In a regular hexacopter, motors are spaced 60 degrees apart. The distance between adjacent motors equals the arm length (which is half the wheelbase/diagonal).

**For 850mm frame:**
- Wheelbase (motor-to-motor diagonal) = 850mm
- Arm length = 850mm / 2 = 425mm
- Adjacent motor-to-motor distance = arm length (for a regular hexagon) = 425mm

**Prop clearance calculation:**
- 15-inch prop diameter = 381mm
- Available space between adjacent motors = 425mm
- Clearance per side = (425mm - 381mm) / 2 = 22mm per tip
- Total tip-to-tip gap = 44mm

**Safety standard:** Recommended minimum clearance is 10-15mm per tip (or 5-10% of prop diameter).

**Verdict: 1555 props FIT on 850mm hex frame with 22mm per-tip clearance.** This is adequate but not generous. The ZD850 frame is specifically marketed for 15-16 inch props, confirming this fit.

### 2.2 Maximum Prop Size for 680mm Hex Frame

**For 680mm frame:**
- Arm length = 680mm / 2 = 340mm
- Adjacent motor-to-motor distance = 340mm

**Max prop diameter calculation:**
- Available: 340mm between adjacent motors
- Subtract 2x 15mm safety clearance = 310mm usable
- 310mm = 12.2 inches

**Real-world confirmation:** The Tarot FY680 and Tarot 680PRO are rated for **12-13 inch propellers maximum**. The Tarot 680 specifically states 13-inch as the upper limit, which gives only ~7mm per-tip clearance (tight).

**1555 (15-inch) props DO NOT FIT on a 680mm frame.** You would need 381mm between motors but only have 340mm.

### 2.3 Prop Options for 680mm Frame

| Prop Size | Diameter (mm) | Clearance per tip (mm) | Fits 680mm? | Notes |
|-----------|---------------|----------------------|-------------|-------|
| 1555 (15") | 381mm | -20.5mm (OVERLAP!) | NO | Props would collide |
| 1455 (14") | 356mm | -8mm (OVERLAP!) | NO | Still too tight |
| 1355 (13") | 330mm | 5mm | BARELY | Dangerously tight, not recommended |
| 1255 (12") | 305mm | 17.5mm | YES | Safe minimum clearance |
| 1245 (12") | 305mm | 17.5mm | YES | Lower pitch, more efficient hover |

**Thrust penalty going from 1555 to smaller props:**

Using T-Motor MN3508 380KV test data as reference:
- 15x5 prop: ~1880g max thrust at 13.3A
- 13x5 prop: ~1300-1400g max thrust (estimated ~25-30% less thrust)
- 12x4.5 prop: ~1100-1200g max thrust (estimated ~35-40% less thrust)

**For 6.5kg AUW on 680mm frame with 1255 props:**
- Required thrust per motor: 1083g (hover)
- Max thrust per motor with 12" prop: ~1200g
- Thrust headroom: only 1.1:1 ratio
- PROBLEM: Recommended minimum thrust-to-weight ratio is 2:1 for safe flight

**Critical conclusion: A 680mm frame is TOO SMALL for a 6.5kg AUW hexacopter.** You need the 850mm frame (or larger) to accommodate 15-inch props and achieve adequate thrust margins. On a 680mm frame with 12-13" props, you would have dangerously low thrust headroom.

### 2.4 T-Motor 1555 vs Generic CF 1555

| Factor | T-Motor 1555 | Generic CF 1555 |
|--------|-------------|-----------------|
| Price (pair) | ~$25-55 | ~$5-14 |
| Balance out of box | Mixed reports - some users spent hours grinding hubs | Mixed - some perfect, some terrible |
| Consistency | Better batch consistency | Highly variable between batches |
| Surface finish | Polished, aerodynamic profile | Often rougher finish |
| Stiffness | High quality 3K CF layup | Variable; some reported as "less rigid than CF should be" |
| Vibration contribution | Lower (when balanced) | Higher (if poorly balanced) |
| Weight | ~14g each | ~13-15g each |

**Real-world user feedback:** Multiple users on RCGroups and forums report buying generic 1555 CF props at 1/4 to 1/5 the price of T-Motor and finding quality "far superior" or "identical side by side." However, other users report getting batches that are badly unbalanced and less rigid.

**Recommendation:** Buy generic CF 1555 props in bulk (~$7-10/pair), but:
1. ALWAYS balance them with a prop balancer before flight
2. Test stiffness by hand - flex should be minimal
3. Discard any that feel noticeably different from the set
4. Buy 2-3 extra pairs as spares since some may be duds
5. For competition or critical missions, use T-Motor for consistency

---

## 3. SERVOS FOR PAYLOAD RELEASE: MG90S Analysis

### 3.1 Is 1.8kg-cm Torque Enough for 500g Payload?

**Torque analysis for a simple latch/hook mechanism:**
- Payload weight: 500g = 0.5kg
- If the servo arm is 1cm from pivot: torque needed = 0.5kg x 1cm = 0.5 kg-cm
- MG90S torque: 1.8 kg-cm (at 4.8V) to 2.2 kg-cm (at 6.0V)
- Safety factor: 1.8 / 0.5 = 3.6x margin

**Verdict: YES, 1.8 kg-cm is more than enough** for a latch-style release mechanism where the servo rotates a pin or hook out of the way. The payload hangs from a fixed point; the servo only needs to move a small locking mechanism.

**Design tip:** Use a "pull-pin" mechanism where a 2mm steel spoke acts as the locking pin. The servo rotates to pull the pin out, releasing the payload instantly. This requires minimal torque since the pin slides rather than bears the load directly.

### 3.2 Vibration Reliability

**Known issues:**
- Digital servos like the MG90S constantly send PWM correction pulses, causing a characteristic whine/buzz
- Drone vibration can cause the servo to oscillate around its set position, increasing wear
- If driven to mechanical limits (0 or 180 degrees), the servo stalls, draws high current, and may strip gears
- Metal gears are more durable than plastic but still susceptible to repeated vibration loading

**Mitigation strategies:**
- Mount servos with rubber grommets or silicone standoffs for vibration isolation
- Wrap servo body in adhesive-backed felt or foam tape to dampen vibrations
- Never command servo to its absolute end-of-travel (stay within 10-170 degrees)
- Use a "hold" PWM signal that keeps the servo in position rather than detaching (to prevent drift)
- Power servos through a dedicated 5V BEC, not through the flight controller

### 3.3 Servo Alternatives Comparison

| Servo | Torque | Weight | Gears | Price | Suitability |
|-------|--------|--------|-------|-------|-------------|
| **SG90** | 1.2 kg-cm | 9g | Plastic | ~$1-2 | NOT RECOMMENDED - plastic gears strip under vibration, insufficient torque margin |
| **MG90S** | 1.8-2.2 kg-cm | 13-14g | Metal | ~$3-5 | GOOD - best weight/torque ratio for 500g payload |
| **MG996R** | 9.4-11 kg-cm | 55g | Metal | ~$5-8 | OVERKILL - far too heavy (6x = 330g unnecessary weight) |
| **DS3218** | 20 kg-cm | 60g | Metal, digital | ~$8-12 | MASSIVE OVERKILL - designed for robotic arms, far too heavy |

**Recommendation: MG90S is the correct choice.** It provides:
- 3.6x safety margin for 500g payload
- Only 14g weight (6 servos = 84g total)
- Metal gears resist vibration better than SG90 plastic gears
- Cheaply replaceable if one fails

**WARNING about counterfeits:** Authentic TowerPro MG90S servos have:
- Matte black gears (not shiny)
- White connector with gold contacts
- Smooth movement without "notchy" feel
Buy from reputable suppliers (GetFPV, RaceDayQuads, Amazon fulfilled by known vendors).

### 3.4 Mounting 6 Servos on a Hex Frame

**Approach 1: Under-arm mounting (RECOMMENDED)**
- Mount one servo under each arm, near the motor mount
- 3D print PETG brackets that clamp onto the carbon fiber arm tubes
- Each servo has its own payload hook hanging below
- Pros: Weight distributed evenly, natural CG balance, each payload hangs under a motor
- Cons: Payloads may affect prop wash

**Approach 2: Central belly mount**
- Mount all 6 servos on a central plate beneath the frame
- Each servo controls one release pin on a shared payload bay
- Pros: Centralized wiring, easier maintenance
- Cons: All payload weight concentrated at center, complex release mechanism

**Approach 3: Radial spoke mount**
- Mount servos at the intersection of arms and center plate
- Payload bags hang on short cables from servo-controlled hooks
- Good compromise between approaches 1 and 2

**Vibration isolation for all approaches:**
- Use M2 rubber grommets at each mounting screw
- Add thin foam tape (1-2mm) between servo body and bracket
- Print mounting brackets in PETG (not PLA - PLA gets brittle)
- Secure with thread-locking fluid on all fasteners

### 3.5 Power Requirements for 6 Servos

| Condition | Current per servo | Current for 6 servos | Notes |
|-----------|-------------------|----------------------|-------|
| Idle (holding position) | 2.7-10mA | 16-60mA | Negligible |
| Moving (no load) | 70mA | 420mA | During payload release |
| Moving (under load) | 120-250mA | 720-1500mA | Worst case during release |
| Stall (fault condition) | 400-700mA | 2.4-4.2A | Should never happen in normal operation |

**Power supply requirements:**
- Voltage: 5V (or 6V for higher torque - 2.2 kg-cm at 6V)
- Current capacity: Size BEC for at least 3A continuous (to handle all 6 moving simultaneously with margin)
- Recommended: Dedicated 5V 5A BEC (separate from flight controller BEC)
- NEVER power servos from the flight controller's built-in BEC - it cannot handle the current and could brown out the FC

**BEC recommendation:** Castle Creations 10A BEC or Matek UBEC 5V 5A. Total weight ~10-15g.

---

## 4. CHARGER COMPARISON

### 4.1 ToolkitRC M7

| Spec | Value |
|------|-------|
| Max power | 200W (DC input only) |
| Max charge current | 10A |
| Cell support | 1-6S LiPo/LiHV/LiFe/Li-ion |
| Balance current | 400mA (2-6S) |
| AC/DC | DC only - requires external PSU |
| Price | ~$35-45 |

**Can it handle 6S 10000mAh?** YES, but with a power limitation.
- At 6S (25.2V max charge voltage): 200W / 25.2V = 7.9A max charge current
- Charge time at ~8A: 10000mAh / 8000mA = ~1.25 hours (75 minutes)
- At the 10A maximum: limited to ~200W, so current drops as voltage rises

### 4.2 iMAX B6AC V2

| Spec | Value |
|------|-------|
| Max power | 50W |
| Max charge current | 6A |
| Cell support | 1-6S LiPo |
| Balance current | 200mA |
| AC/DC | Built-in AC adapter (100-240V) + DC input |
| Price | ~$30-40 |

**Can it handle 6S 10000mAh?** Technically yes, but VERY SLOWLY.
- At 6S (22.2V nominal): 50W / 22.2V = 2.25A maximum current
- Charge time at 2.25A: 10000mAh / 2250mA = ~4.4 hours
- This is a 0.22C charge rate - painfully slow for field use

### 4.3 ISDT D2 Mark II

| Spec | Value |
|------|-------|
| Max power | 200W per channel (dual channel) |
| Max charge current | 12A per channel |
| Cell support | 1-6S LiPo/LiHV/LiFe/Li-ion |
| Balance current | 1.5A per cell |
| AC/DC | Built-in AC (wide range) |
| Channels | 2 independent channels |
| Price | ~$80-100 |

**Can it handle 6S 10000mAh?** YES, and fastest of the three.
- At 6S: 200W / 25.2V = ~7.9A, but max 12A limit means power is the bottleneck
- Charge time at ~8A: ~75 minutes
- BONUS: Can charge BOTH 5000mAh packs simultaneously on dual channels

### 4.4 Charge Time Comparison

| Charger | Max Current at 6S | Charge Time (10000mAh) | Charge Time (2x 5000mAh) |
|---------|-------------------|------------------------|--------------------------|
| ToolkitRC M7 | ~8A (200W limited) | ~75 min | ~75 min (sequential) |
| iMAX B6AC V2 | ~2.25A (50W limited) | ~4.4 hours | ~2.2 hrs each (sequential) |
| ISDT D2 MK II | ~8A per channel | ~75 min | **~38 min** (simultaneous!) |

### 4.5 Safety Features Comparison

| Feature | ToolkitRC M7 | iMAX B6AC V2 | ISDT D2 MK II |
|---------|-------------|-------------|--------------|
| Cell balancing | Yes (400mA) | Yes (200mA) | Yes (1.5A/cell - fastest) |
| Over-voltage protection | Yes | Yes | Yes (OVP) |
| Over-current protection | Yes | Yes | Yes (SCP) |
| Over-temperature protection | Yes | Yes | Yes (OTP) |
| Overload protection | Yes | Limited | Yes (OLP) |
| Reverse polarity protection | Yes | Yes | Yes |
| Capacity limit | Yes | Yes | Yes |
| Timer safety cutoff | Yes | Yes | Yes |

### 4.6 Charger Recommendation

**Best overall: ISDT D2 Mark II**
- Built-in AC power (no external PSU needed)
- Dual channels - charge both 5000mAh packs simultaneously in ~38 minutes
- 1.5A balance current (3x faster balancing than M7, 7.5x faster than B6AC)
- Premium safety features

**Best budget: ToolkitRC M7**
- Excellent for the price at 200W
- Requires external DC power supply (~$20-30 additional)
- 75-minute charge time for 10000mAh is acceptable

**Avoid for this use case: iMAX B6AC V2**
- 50W is completely inadequate for 6S 10000mAh batteries
- 4.4-hour charge time is impractical for field operations
- The B6AC is designed for smaller 3S-4S batteries, not heavy-lift 6S packs

---

## 5. TRANSMITTER: FlySky FS-i6X

### 5.1 Channel Requirements Analysis

**Channels needed:**
- Channels 1-4: Roll, Pitch, Throttle, Yaw (standard - handled by FC)
- Channel 5: Flight mode switch (essential)
- Channel 6: Optional (RTL/failsafe switch, tuning knob, etc.)
- Channels 7-12: 6 individual servo payload releases (one per servo)

**Total needed: 12 channels minimum** (4 flight + 2 auxiliary + 6 payload servos)

### 5.2 FS-i6X Channel Limitations

| Configuration | Channels | Sufficient? |
|---------------|----------|-------------|
| FS-i6X stock firmware | 6 channels | NO - only 2 spare channels after flight controls |
| FS-i6X with 10ch firmware + FS-iA10B receiver | 10 channels | NO - only 6 spare channels, need mode switch too = 5 for servos |
| FS-i6X with iBUS protocol | 10 channels max | NO - same limitation |

**The FS-i6X CANNOT directly control 6 individual servo payload releases** even with the 10-channel firmware upgrade. You would be 2 channels short at minimum.

### 5.3 Physical Switch Limitation

Even if channels were available, the FS-i6X only has:
- 2 sticks (4 channels)
- 2 potentiometers (VRA, VRB)
- 4 switches (SWA, SWB, SWC, SWD)

That is 10 physical inputs maximum. You cannot independently trigger 6 payload drops from 6 different switches because you only have 4 switches available after assigning flight mode.

### 5.4 Solutions

**Solution A: ArduPilot DO_SET_SERVO in Mission Planner (RECOMMENDED)**

Rather than controlling each servo from the TX, use ArduPilot's mission planning:

1. Configure SERVO7_FUNCTION through SERVO12_FUNCTION as "RCPassThru" or use SERVOn_FUNCTION = 0 (disabled for manual override)
2. In Mission Planner, create waypoint mission:
   ```
   WP1 -> NAV_WAYPOINT (fly to drop zone 1)
   CMD -> DO_SET_SERVO (servo 7, PWM 1700)  // Release payload 1
   CMD -> DO_SET_SERVO (servo 7, PWM 1100)  // Reset servo 1
   WP2 -> NAV_WAYPOINT (fly to drop zone 2)
   CMD -> DO_SET_SERVO (servo 8, PWM 1700)  // Release payload 2
   ... repeat for all 6 drops
   ```
3. The DO_SET_SERVO command executes automatically when the copter reaches each waypoint
4. No extra TX channels needed - mission runs autonomously

**This is the correct approach for sequential payload drops at predetermined locations.**

**Solution B: ArduPilot Lua Scripts**

For more complex logic (conditional drops, sensor-triggered releases):
1. Upload .lua scripts to the autopilot's SD card APM/scripts/ folder
2. Set SCR_ENABLE = 1 and reboot
3. Lua can directly control outputs using Function IDs 94-109 (up to 16 outputs)
4. Script can sequence drops based on GPS position, altitude, time, or GCS commands

**Solution C: Upgrade Transmitter**

If manual TX control of each servo is required:

| Transmitter | Channels | Switches | Price | Notes |
|-------------|----------|----------|-------|-------|
| FlySky FS-i6X | 10 max | 4 switches | ~$55 | NOT ENOUGH |
| RadioMaster TX16S Mark II | 16 channels | 6 switches + 2 pots + 2 sliders | ~$150-200 | RECOMMENDED upgrade |
| RadioMaster Zorro | 16 channels | 4 switches | ~$100 | Compact option |
| FrSky X9D Plus | 16 channels | 6 switches + 2 pots + 2 sliders | ~$180 | Alternative |

**The RadioMaster TX16S Mark II** is the strongest upgrade path:
- 16 channels (plenty for 6 servos + all flight functions)
- Multi-protocol module supports ELRS, FrSky, FlySky, Spektrum protocols
- OpenTX/EdgeTX firmware with full switch programming
- 4.3" color display
- Hall sensor gimbals for precision
- Can run ELRS for long-range control

### 5.5 Recommended Configuration

**Best approach: ArduPilot DO_SET_SERVO via Mission Planner**
- Keep the FS-i6X as your TX (saves money)
- Use channels 5-6 for flight mode and a manual override/abort switch
- Program all 6 payload drops as mission commands in Mission Planner
- Payload drops execute automatically at GPS waypoints
- No extra TX channels needed
- GCS (ground control station) can also trigger drops via MAVLink if needed

**ArduPilot servo output configuration:**
```
SERVO7_FUNCTION = 0    (Manual/Script control - Payload 1)
SERVO8_FUNCTION = 0    (Manual/Script control - Payload 2)
SERVO9_FUNCTION = 0    (Manual/Script control - Payload 3)
SERVO10_FUNCTION = 0   (Manual/Script control - Payload 4)
SERVO11_FUNCTION = 0   (Manual/Script control - Payload 5)
SERVO12_FUNCTION = 0   (Manual/Script control - Payload 6)
```

Each servo is triggered by DO_SET_SERVO in the mission, or via Lua script, or via GCS MAVLink command. The TX only needs to handle flight controls and mode switching.

---

## 6. SUMMARY OF RECOMMENDATIONS

| Component | Recommendation | Key Reason |
|-----------|---------------|------------|
| **Battery** | 2x Gens Ace 6S 5000mAh 45C-60C in parallel | Better voltage sag, CG flexibility, ~1430-1510g |
| **Frame** | 850mm hex frame (e.g., ZD850) | Required for 15" props; 680mm is too small |
| **Props** | 1555 CF (generic, with prop balancer) | Fits 850mm frame with 22mm clearance; balance before use |
| **Servos** | MG90S (authentic TowerPro) x6 | Best weight/torque ratio; 84g total for 6 units |
| **Servo power** | Dedicated 5V 5A BEC | Never power servos from FC BEC |
| **Charger** | ISDT D2 Mark II | Dual channel, built-in AC, fast balance |
| **TX** | Keep FS-i6X | Sufficient when using ArduPilot mission commands |
| **Payload control** | ArduPilot DO_SET_SERVO in Mission Planner | Autonomous drops at waypoints, no extra channels needed |

### Estimated Weight Budget

| Component | Weight |
|-----------|--------|
| Frame (ZD850 with landing gear) | ~1200g |
| 6x Motors (MN3508 or similar) | ~6 x 102g = 612g |
| 6x ESC (30A) | ~6 x 30g = 180g |
| 6x Props (1555 CF) | ~6 x 14g = 84g |
| Flight controller + GPS | ~100g |
| 2x 5000mAh 6S batteries | ~1430g |
| 6x MG90S servos | ~84g |
| BEC + wiring | ~50g |
| Misc (PDB, receiver, fasteners) | ~100g |
| **Dry weight (no payload)** | **~3840g** |
| 6x 500g payloads | 3000g |
| **Max AUW** | **~6840g** |
| After all drops AUW | ~3840g |

### Thrust-to-Weight Verification

- 6x motors at max thrust (1880g each) = 11,280g total thrust
- Max AUW = 6840g
- Thrust-to-weight ratio = 11,280 / 6,840 = **1.65:1**
- NOTE: 1.65:1 is below the recommended 2:1 minimum
- **Action required:** Consider larger motors (e.g., T-Motor MN4006 380KV with 15" props for ~2.3kg thrust per motor) or accept the reduced maneuverability and safety margin

---

## SOURCES

### Battery Research
- [Tattu G-Tech 6S 10000mAh specs](https://genstattu.com/ta-30c-10000-6s1p-ec5.html)
- [Tattu Plus 10000mAh 6S 25C](https://genstattu.com/tattu-plus-22-2v-25c-6s-liPo-battery-10000-mah-with-as150-xt150-plug.html)
- [HRB 6S 10000mAh specs](https://hrb-power.com/products/hrb-22-2v-10000mah-6s-lipo-battery-xt90s-xt90-as150-xt150-for-plane-drone-boat)
- [CNHL Racing 10000mAh 6S](https://chinahobbyline.com/products/cnhl-racing-series-10000mah-22-2v-6s-100c-lipo-battery-with-ec5-plug)
- [Gens Ace 5000mAh 6S 60C](https://genstattu.com/gens-ace-5000mah-6s-60c-22-2v-g-tech-lipo-battery-pack-with-ec5-plug/)
- [Oscar Liang LiPo battery guide](https://oscarliang.com/lipo-battery-guide/)

### Propeller Research
- [Prop clearance calculation guide](http://www.dronefromchina.com/new/How-to-calculate-the-drone-frame-sizes-and-size-of-the-propeller-for-the-drone-frame.html)
- [ZD850 frame specifications](https://www.arrishobby.com/products/lji-zd850-6-axis-850mm-carbon-fiber-umbrella-folding-hexacopter-frame-with-landing-gear)
- [Tarot 680PRO specifications](https://hobbyking.com/en_us/tarot-680pro-hexacopter-folding-frame-3k-carbon-kit.html)
- [DroneVibes hex prop sizing discussion](https://dronevibes.com/forums/threads/how-to-choose-a-prop-for-hexacopter.15111/)

### Servo Research
- [MG90S datasheet and specs](https://components101.com/motors/mg90s-metal-gear-servo-motor)
- [MG90S power consumption](https://protosupplies.com/product/servo-motor-micro-mg90s/)
- [ServoDatabase MG90S specs](https://servodatabase.com/servo/towerpro/mg90s)
- [MG996R specs](https://components101.com/motors/mg996r-servo-motor-datasheet)
- [Payload dropper 3D print design](https://www.printables.com/model/1326088-payload-dropper-mechanism)
- [Universal drone payload release](https://cults3d.com/en/3d-model/gadget/universal-fpv-drone-payload-release-mechanism)

### Charger Research
- [ToolkitRC M7 official specs](https://www.toolkitrc.com/m7/)
- [ToolkitRC M7 review - Oscar Liang](https://oscarliang.com/toolkitrc-m7/)
- [iMAX B6AC V2 specs](https://www.skyrc.com/iMAX_B6AC_V2_Charger)
- [ISDT D2 Mark II specs](https://isdtshop.com/products/isdt-d2-mark-2)
- [ISDT D2 review - DroneNodes](https://dronenodes.com/isdt-d2-review-smart-battery-charger/)

### Transmitter Research
- [FlySky FS-i6X ArduPilot support discussion](https://discuss.ardupilot.org/t/flysky-fs-i6x-support/44174)
- [FS-i6X 10ch firmware mod](https://github.com/qba667/FlyPlusI6X)
- [RadioMaster TX16S review - Oscar Liang](https://oscarliang.com/radiomaster-tx16s/)
- [ArduPilot DO_SET_SERVO documentation](https://ardupilot.org/copter/docs/mission-command-list.html)
- [ArduPilot Lua Scripts documentation](https://ardupilot.org/copter/docs/common-lua-scripts.html)
- [ArduPilot servo output functions](https://ardupilot.org/copter/docs/common-rcoutput-mapping.html)

### Motor Data
- [T-Motor MN3508 380KV test data](https://www.electricwingman.com/tiger-motor-mn3508-29.aspx)
- [T-Motor MN3508 official page](https://store.tmotor.com/product/mn3508-motor-navigator-type.html)
- [eCalc multicopter calculator](https://www.ecalc.ch/xcoptercalc.php)

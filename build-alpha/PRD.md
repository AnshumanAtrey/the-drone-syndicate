# Build Alpha — Product Requirements Document

**Drone:** Hexacopter (6-arm)
**Mission:** Carry 6 independent 500g payloads and drop each one on demand via remote control or mobile app.

---

## 1. Core Requirement

The drone must:
- Take off carrying **6 payloads simultaneously** (500g each, 3kg total)
- Allow the operator to **drop any or all payloads** in any order, at any time
- Control interface: **RC remote** and/or **mobile app**

---

## 2. Payload Specs

| Property | Requirement |
|----------|-------------|
| Number of payloads | 6 |
| Weight per payload | 500g |
| Total payload weight | 3,000g (3kg) |
| Drop trigger | Operator-controlled (remote or app) |
| Drop order | Any order, independent per payload |
| Minimum drop height | 3–5m AGL |

---

## 3. Flight Requirements

| Property | Requirement |
|----------|-------------|
| Min thrust-to-weight ratio (fully loaded) | ≥ 1.5:1 |
| Target TWR (fully loaded) | ≥ 1.6:1 |
| Min flight time (full mission, all 6 drops) | 12 min |
| Target flight time | 14–15 min |
| Max wind tolerance (at full load) | ≤ 15 km/h |
| Max operating altitude | 120m AGL |

---

## 4. Drop Mechanism

Each payload is held by a **servo-actuated pin-pull release mechanism**.

| Property | Spec |
|----------|------|
| Release type | Servo pin-pull (mechanical, passive drop) |
| Servo per payload | 1x (6 total) |
| Servo torque (min) | 1.8 kg-cm |
| Actuation signal | PWM via flight controller |
| Independent control | Yes — each payload drops separately |

---

## 5. Control Interface

### 5a. RC Remote (Primary)
- Standard RC transmitter (min 10 channels)
- Dedicated switches for each payload release (channels 7–12)
- Manual override for all releases at once (kill-all switch)

### 5b. Mobile App (Secondary)
- Connects to drone via telemetry link (433 MHz or 915 MHz)
- App shows live payload status (armed / released) for each of 6 slots
- One-tap drop per payload
- "Drop All" button (requires hold for 2 seconds to prevent accidental trigger)
- Live battery %, GPS position, and altitude display

---

## 6. Safety Requirements

| Requirement | Detail |
|-------------|--------|
| Payload lock during arming | All servos locked in hold position until explicitly released |
| Failsafe on signal loss | Hover in place — do NOT auto-release payloads |
| Low battery cutoff | Return-to-home at 20% battery, no drops below 15% |
| Visual indicator | LED or buzzer confirms each drop |
| Ground clearance | Min 150mm clearance with all payloads hanging |

---

## 7. Success Criteria

- [ ] Drone lifts off with all 6 x 500g payloads attached
- [ ] Operator drops payload 1 via remote — drone stable within 3 seconds
- [ ] Operator drops payload 2 via app — drone stable within 3 seconds
- [ ] All 6 payloads can be dropped independently in any sequence
- [ ] Drone lands safely with zero payloads remaining
- [ ] Full mission (6 drops) completed within a single battery charge
- [ ] No unintended drops during takeoff, flight, or landing

---

## 8. Out of Scope (Build Alpha)

- Autonomous / GPS-waypoint drops (manual operator control only for this build)
- Payload return / retrieval
- Waterproofing
- Night operations

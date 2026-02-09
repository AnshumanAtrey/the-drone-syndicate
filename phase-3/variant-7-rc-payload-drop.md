# Variant 7 — RC Payload Drop Drone (400-500g)

**Additional Cost over Phase 1: Rs. 0 (standalone build)**
**Standalone Total Cost: Rs. 18,000 - 25,000**

Simple remote-controlled drone that flies and drops a single 400-500g payload. No AI, no cameras, no autonomous flight — just RC transmitter control and a servo-actuated release mechanism.

---

## Component Breakdown

| # | Component | Spec | Price (INR) |
|---|-----------|------|-------------|
| 1 | Frame | F450 quadcopter frame | 1,500 - 2,500 |
| 2 | Motors x4 | 2212 920KV brushless | 4,000 - 4,600 |
| 3 | ESCs x4 | 30A BLDC ESC | 1,600 - 2,500 |
| 4 | Flight Controller | CC3D or F405 | 975 - 2,000 |
| 5 | RC Transmitter + Receiver | FlySky FS-i6 (6CH) | 3,800 - 4,500 |
| 6 | Battery | 3S 4000-5000mAh LiPo | 3,000 - 4,000 |
| 7 | Propellers | 1045 (2 pairs + spares) | 150 - 300 |
| 8 | Payload Release Servo | MG90S metal gear servo | 400 |
| 9 | Tall Landing Gear | 150mm clearance skid set | 400 - 600 |
| 10 | Charger + Wiring + Misc | iMAX B6 charger, XT60, wires | 2,200 - 3,500 |

---

## Weight Budget

| Item | Weight |
|------|--------|
| F450 frame + landing gear | ~350g |
| 4x motors + ESCs | ~300g |
| Flight controller + RX | ~50g |
| 3S 4000mAh battery | ~300g |
| Payload release mechanism | ~50g |
| **Drone dry weight** | **~1,050g** |
| **Payload** | **400 - 500g** |
| **Total AUW** | **~1,450 - 1,550g** |

## Thrust Math

- 2212 920KV + 1045 props = ~550g thrust per motor
- 4 motors = ~2,200g total thrust
- Thrust-to-weight ratio with 500g payload: **~1.5:1** (flyable, limited agility)
- For better margin, upgrade to 2216 1000KV motors (~700g/motor, ratio jumps to ~1.9:1)

## Flight Time

- With 3S 4000mAh at 1.5kg AUW: **8-12 minutes** (loaded)
- Without payload: **12-15 minutes**

## Payload Release Mechanism

- MG90S servo mounted under frame center plate
- DIY hook/latch from bent steel wire or 3D-printed
- Connected to CH5 or CH6 on receiver
- Flip a switch on transmitter → servo rotates → payload drops
- Can be built in 30 minutes with basic tools

## Where to Buy (India)

- Robu.in — frames, ESCs, props
- Robocraze — flight controllers, frames
- Flipkart/Amazon India — motors, transmitters
- Quadkart.in — LiPo batteries
- ElectronicsComp — connectors, wiring

## Notes

- No soldering iron? Get a pre-soldered PDB (power distribution board) version of the F450 frame
- Always balance-charge LiPo batteries, never overcharge
- Test servo release mechanism on the ground before flying
- Start with lighter test payloads (~200g) and work up
- Keep payload center-of-gravity aligned with drone center

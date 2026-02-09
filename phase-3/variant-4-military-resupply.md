# Variant 4 — Military Forward Resupply Drone

**Additional Cost Over Phase 1: Rs. 12,000 - 25,000**

Autonomous drone that delivers ammunition, medical supplies, batteries, spare parts, food, and water to forward positions under fire — so soldiers don't have to expose themselves in supply convoys. This is exactly what **Elroy Air Chaparral** (US Marines), **Kaman KARGO** (US Army), and **TechEagle Vertiplane** (Indian Army trials) do.

> **Ref:** Indian Army trialed drone logistics in Ladakh 2022 (high-altitude, where convoys take days). Indian Navy uses drones for ship-to-shore supply. Elroy Air won USMC contract for Chaparral (300lb payload, 300mi range). India's TechEagle ran medical supply drone trials in Manipur/Meghalaya.

## Components (Full Build — Hexacopter needed for payload)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | Frame | Tarot 680PRO Hexacopter (680mm, foldable) | 8,000 - 12,000 | Amazon.in / Robocraze |
| 2 | Flight Controller | Pixhawk 2.4.8 PX4 | 8,514 | Robocraze |
| 3 | Motors x6 | 3508 380KV BLDC (heavy lift) | 9,000 - 12,000 | Amazon.in |
| 4 | ESC x6 | 40A ESC | 3,000 | Robocraze |
| 5 | Props x6 | 15" carbon fiber | 2,400 | Robocraze |
| 6 | GPS | NEO M9N multi-GNSS | 2,099 | Robocraze |
| 7 | Battery | 6S 10000mAh 25C LiPo | 8,000 - 12,000 | Amazon.in |
| 8 | RC Tx/Rx | FlySky FS-i6X | 5,109 | Robocraze |
| 9 | Companion Computer | Jetson Nano 4GB | 17,999 | Robocraze |
| 10 | 4G Module | EC200U 4G LTE | 1,988 | Robocraze |
| 11 | **Payload Release** | Servo parabolic mechanism (4-6kg) | 799 - 4,720 | Probots.co.in / Xbotics.in |
| 12 | **Winch System** | 12V DC motor + 15m rope + spool | 1,500 - 2,500 | Amazon.in |
| 13 | **Cargo Container** | Waterproof ABS case (IP67) | 800 - 3,000 | Amazon.in |
| 14 | **Parachute** | Drone cargo parachute (2-3kg class) | 3,000 - 8,000 | XBOOM.in / RC Hyderabad |
| 15 | Telemetry | 3DR 433MHz | 2,151 | Robocraze |
| 16 | Power Distribution | Heavy-duty PDB + UBEC | 1,000 | Robocraze |

## Delivery Methods (3 options)

### Method 1: Winch Lowering (Precision, Low Risk)
- Drone hovers at 10-15m, lowers cargo on rope via DC motor winch
- Soldier on ground detaches package, signals done
- Drone reels in rope, returns to base
- **Best for:** ammo boxes, sensitive equipment, medical kits
- **Accuracy:** sub-meter (drone maintains GPS hover)

### Method 2: Parachute Drop (Fast, Area Delivery)
- Drone flies over drop zone at 30-50m altitude
- Servo releases cargo container attached to parachute
- Parachute deploys, cargo descends and lands
- **Best for:** bulk supplies (food, water, batteries) to a general area
- **Accuracy:** ~10-20m circle (wind-dependent)

### Method 3: Precision Landing (Max Payload)
- Drone lands directly at delivery point
- Troops manually unload cargo
- Drone takes off and returns
- **Best for:** heavy/fragile items that can't be dropped
- **Requires:** flat landing zone, may expose drone to enemy fire

## Military Payload Examples
| Payload Type | Weight | Qty (per flight) | Priority |
|-------------|--------|-------------------|----------|
| 5.56mm ammo box (200 rds) | 3kg | 1 box | Critical in firefight |
| First-aid trauma kit | 1.5kg | 2 kits | Medevac |
| Radio batteries (Li-ion) | 0.5kg each | 4-6 batteries | Comms sustainment |
| MRE ration packs | 0.5kg each | 4-6 packs | Sustenance |
| Water bottles (500ml) | 0.5kg each | 4-6 bottles | Sustenance |
| Night vision batteries | 0.3kg each | 6-8 batteries | Night ops |
| Morphine auto-injector | 0.1kg | 10+ | Casualty care |
| Drone spare battery | 0.8kg | 2-3 batteries | Drone sustainment |

## Key Features
- **3-5kg payload** — enough for ammo box, trauma kits, batteries
- **Autonomous delivery** — program pickup + drop GPS coordinates
- **Multiple delivery methods** — winch, parachute, or landing
- **Hexacopter redundancy** — survives 1 motor failure
- **Night delivery** — ArduPilot + GPS works day/night
- **Waterproof container** — supplies protected from rain/dust
- **Return trip** — drone can bring back intel packages, blood samples, captured equipment

## Limitations
- 3-5kg limit with hexacopter (military drones carry 50-300kg)
- 15-20 min flight time under load (military needs hours)
- Not survivable in contested airspace (no armor, no EW)
- Needs 4G coverage for remote control (fails in remote mountains without satellite)
- DGCA regulations apply for any BVLOS flight

## Indian Military Context
- Indian Army uses mules/porters for Siachen logistics (takes days, costs lives)
- Drone supply to forward posts in Ladakh cuts delivery from days to minutes
- Indian Navy needs ship-to-ship and ship-to-shore supply drones
- BSF border posts in remote areas could use drone resupply
- DRDO developing indigenous logistics drones under TDF (Technology Development Fund)

## College Research Angle
- Demonstrate autonomous cargo delivery with winch lowering
- Test: payload weight vs flight time vs range curve
- Compare: accuracy of winch vs parachute vs landing delivery
- Measure: drone stability during winch operation (payload swing)
- Publish: "Autonomous Hexacopter-Based Military Logistics Delivery System"

# Variant 6 — Electronic Warfare Decoy / Countermeasure Dispenser

**Additional Cost Over Phase 1: Rs. 15,000 - 25,000**

Drone that carries and deploys electronic decoys, chaff simulators, and IR countermeasures to confuse enemy radar and missile systems. Inspired by **Leonardo BriteCloud** (expendable RF decoy), military chaff/flare pods, and electronic warfare drones used in Ukraine. This variant focuses on the **decoy dispensing mechanism and RF simulation** — no actual military-grade jamming.

> **Ref:** Leonardo BriteCloud 218 — flare-sized RF decoy that mimics aircraft radar signature. Russia uses drone swarms as radar decoys in Ukraine. DRDO develops indigenous EW systems for Indian forces. Chaff (aluminum strips) confuses radar; flares confuse IR-guided missiles.

> **LEGAL:** Active RF jamming is illegal without government license (Indian Wireless Telegraphy Act). This variant uses **simulated chaff** (metallic confetti) and **SDR-based RF research** on your own equipment in a lab setting. No actual military EW systems are built.

## Additional Components (on top of Phase 1 — Jetson Nano variant)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | **HackRF One** | 1MHz-6GHz SDR (for RF signature research) | 11,001 - 22,500 | Robokits / Amazon.in |
| 2 | **Chaff Simulator** | Metallic confetti dispenser (aluminum strips) | 500 - 1,000 | DIY (servo + container) |
| 3 | **Servo Dispensers x4** | SG90 micro servo (for 4 payload bays) | 348 (4x 87) | Robocraze |
| 4 | **IR Decoy** | High-power IR LED array (simulate flare signature) | 500 - 1,000 | Amazon.in |
| 5 | **ESP32 RF Beacon** | Programmable RF signal source | 379 | Robocraze |
| 6 | **Amplifier** | 2.4GHz 2W signal amplifier (lab use only) | 2,000 - 3,500 | Amazon.in |
| 7 | **Directional Antenna** | 2.4GHz patch antenna 8dBi | 500 - 1,000 | Amazon.in |
| 8 | **Payload Tubes x4** | PVC tubes for countermeasure canisters | 200 | Local hardware |
| 9 | **MicroSD Card** | 128GB (for logging) | 800 | Amazon.in |

## Countermeasure Types (Research Prototypes)

### 1. Simulated Chaff Dispenser
- Aluminum foil strips (cut to radar wavelength multiples)
- Loaded in PVC tubes under drone
- Servo opens tube bottom, strips fall and disperse in air
- Creates cloud of reflective material
- **Research:** measure how chaff cloud affects 2.4GHz/5.8GHz WiFi signal (simulates radar disruption)

### 2. RF Decoy (Electronic)
- HackRF One transmits radar-like signal to simulate a larger aircraft
- ESP32 generates known WiFi/Bluetooth patterns as decoy signatures
- Drone flies away from protected asset, drawing enemy attention
- **Research:** measure how SDR-generated signals affect SDR receiver (simulate radar deception in lab)

### 3. IR Countermeasure Simulator
- Array of high-power IR LEDs (940nm, 850nm)
- Pulse at patterns mimicking engine heat signature
- Research into IR signature simulation
- **Note:** not actual flares — LED-based IR source for lab testing

### 4. Multi-Decoy Swarm Concept
- Multiple cheap drones (ESP32-based) each carrying RF beacon
- Swarm appears as multiple targets on radar
- Overwhelm enemy detection systems with false targets
- **Research:** demonstrate swarm decoy concept with 3-5 cheap quads

## EW Research Capabilities

### Radar Cross Section (RCS) Simulation
- Use HackRF to generate signals at specific frequencies
- Measure how chaff/metallic strips affect signal reflection
- Characterize RCS enhancement from chaff deployment
- All testing done in controlled lab environment with your own equipment

### Decoy Effectiveness Testing
- Set up RTL-SDR as "enemy radar receiver"
- Deploy drone with RF beacon as decoy
- Measure: does the receiver track the decoy or the real target?
- Quantify deception effectiveness at different ranges

### IR Countermeasure Research
- Use MLX90640 thermal camera as "enemy IR seeker"
- Deploy IR LED decoy drone
- Measure: thermal signature vs real drone engine heat
- Study IR countermeasure patterns used in military flare dispensers

## Key Features
- **Multi-countermeasure** — chaff, RF decoy, IR decoy in one platform
- **Dispensable** — 4 payload tubes can carry different countermeasures
- **Programmable** — HackRF + ESP32 allow custom RF patterns
- **Research-grade** — measure and quantify EW effects in controlled setting
- **Reusable** — reload tubes, reprogram RF patterns, fly again
- **Swarm-capable** — concept scales to multiple decoy drones

## Limitations
- **NOT actual military EW** — no real jamming, no classified waveforms
- Active RF transmission requires amateur radio license at minimum
- All testing must be in controlled lab or shielded environment
- Chaff simulator uses harmless metallic confetti (not military chaff)
- IR LED array doesn't match real engine heat (research simulation only)
- HackRF transmit power is low (max ~15dBm) — short range only

## Indian Military Context
- Indian Air Force uses Israeli/Russian EW pods (ELTA, KNIRTI)
- DRDO Divya Drishti program — indigenous EW systems
- BEL manufactures EW equipment for Indian forces
- Indian Navy ships carry chaff launchers (KAVACH system by BEL)
- Pakistan and China use electronic warfare extensively — India needs countermeasures
- Growing need for drone-deployable EW payloads in the drone warfare era

## College Research Angle
- Build chaff dispenser, measure effect on WiFi signal strength
- HackRF RF decoy: measure tracking deviation on RTL-SDR receiver
- Compare: chaff vs RF decoy vs combined effectiveness
- Study military EW concepts through accessible hardware
- Publish: "Experimental Study of UAV-Deployed Electronic Countermeasures Using SDR"

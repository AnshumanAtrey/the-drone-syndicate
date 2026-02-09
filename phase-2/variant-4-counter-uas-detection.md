# Variant 4 — Counter-UAS Detection Platform

**Additional Cost Over Phase 1: Rs. 12,000 - 20,000**

Airborne drone-detection system. Detects, classifies, and tracks other drones using RF analysis + acoustic sensors + AI vision. Inspired by Dedrone, DroneShield, and Fortem Technologies' TrueView radar. This variant is **detection-only** (no active jamming or kinetic defeat — those require government licensing).

> **Ref:** Counter-UAS market growing at 30%+ CAGR. Key players: Dedrone (dedrone.com), DroneShield (droneshield.com), Fortem Technologies (fortemtech.com). India's BSF and CISF actively deploying C-UAS systems.

## Additional Components (on top of Phase 1)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | SDR Receiver | RTL-SDR Blog V4 (500kHz-1.7GHz) | 6,000 - 11,200 | Amazon.in / ElectroPi.in |
| 2 | Directional Antenna | 2.4GHz Yagi 12dBi | 800 - 1,500 | Amazon.in |
| 3 | Omnidirectional Antenna | Wideband whip (25MHz-6GHz) | 1,000 - 2,000 | Amazon.in |
| 4 | Acoustic Sensor | MEMS microphone array (INMP441 x4) | 400 (4x 100) | Robocraze |
| 5 | Camera (AI) | Pi Camera Module 3 (if not already) | 3,249 | Robocraze |
| 6 | MicroSD Card | 128GB Class 10 | 800 | Amazon.in |
| 7 | USB Hub | Powered USB 2.0 hub | 500 | Amazon.in |
| 8 | Optional: HackRF One | 1MHz-6GHz wideband SDR | 11,001 - 25,000 | Robokits (cheapest Rs.11K) / Amazon.in |

## Detection Methods (Layered)

### 1. RF Detection (RTL-SDR)
- Scan 2.4GHz and 5.8GHz bands for drone control signals
- Detect common drone protocols: DJI OcuSync, FrSky, Spektrum, WiFi FPV
- Classify drone type by RF fingerprint (signal pattern matching)
- Log frequency, signal strength, direction, timestamp

### 2. Acoustic Detection (MEMS Microphone Array)
- 4x INMP441 MEMS microphones in square arrangement
- Beamforming to determine direction of drone motor noise
- AI model trained on drone propeller acoustic signatures
- Detects drones up to 200-500m depending on ambient noise

### 3. Visual Detection (AI Camera)
- YOLOv5-nano trained on drone images (run on Jetson Nano at 30fps)
- Detect and track multiple drones simultaneously
- Estimate distance using known drone size + pixel size
- Works in daylight conditions

### 4. Multi-Sensor Fusion
- Combine RF bearing + acoustic bearing + visual track
- Triangulate drone position using multiple sensor inputs
- Reduce false positives through sensor cross-validation
- Generate threat assessment: drone type, distance, heading, risk level

## Software Stack
- **GNU Radio** — RF signal processing, drone protocol detection
- **PyAudio + NumPy** — acoustic beamforming and signature analysis
- **YOLOv5** — visual drone detection (TensorRT on Jetson)
- **Custom Python** — multi-sensor fusion, threat classification, logging
- **MQTT** — relay detection alerts to ground station in real-time

## Key Features
- **Passive only** — no active jamming, no licensing needed
- **Multi-layered** — RF + acoustic + visual for high detection probability
- **Mobile** — detection platform flies to where coverage is needed
- **AI classification** — distinguish drone from birds, aircraft, debris
- **Real-time alerts** — instant notification when drone detected
- **Logging** — full detection log with GPS coordinates for post-analysis

## Limitations
- Detection range limited (200-500m acoustic, 1-2km RF, 200m visual)
- Cannot actively defeat detected drones (detection only)
- RF detection depends on drone transmitting (fails against autonomous drones)
- Acoustic detection affected by wind and ambient noise
- Requires Jetson Nano or better for real-time AI vision

## College Research Angle
- Build multi-sensor drone detection prototype
- Compare detection rates: RF-only vs acoustic-only vs visual-only vs fused
- Publish: "Low-Cost Multi-Sensor Counter-UAS Detection Using Edge AI"
- Dataset: create open-source drone RF signature + acoustic dataset

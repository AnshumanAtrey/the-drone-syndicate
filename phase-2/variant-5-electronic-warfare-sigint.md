# Variant 5 — Electronic Warfare / SIGINT Research Drone

**Additional Cost Over Phase 1: Rs. 20,000 - 35,000**

Passive Signal Intelligence (SIGINT) platform for studying electronic warfare concepts. Detects, logs, and analyzes RF emissions across wide spectrum. Inspired by defense SIGINT/ELINT systems but built at college research scale. **Passive reception only — no jamming, no spoofing, no interception of encrypted comms.**

> **Ref:** L3Harris (l3harris.com) builds military SIGINT systems. Academic EW research is legal. Indian Wireless Telegraphy Act 1933 permits passive reception on most bands. Active jamming/spoofing is illegal without government license.

## Additional Components (on top of Phase 1)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | **HackRF One** | 1MHz-6GHz TX/RX SDR (half-duplex) | 11,001 - 25,000 | Robokits (Rs.11K cheapest) / Amazon.in |
| 2 | RTL-SDR Blog V4 | 500kHz-1.7GHz (2nd receiver) | 6,000 - 11,200 | Amazon.in / ElectroPi.in / Robu.in |
| 3 | Wideband Antenna | Log-periodic 200MHz-8GHz | 3,000 - 5,000 | Amazon.in |
| 4 | 2.4GHz Yagi Antenna | Directional, 12dBi | 800 - 1,500 | Amazon.in |
| 5 | LNA (Low Noise Amp) | Wideband 0.1-6GHz, 20dB gain | 1,500 - 2,500 | Amazon.in |
| 6 | SMA Cables/Adapters | Various pigtails and adapters | 500 - 800 | Amazon.in |
| 7 | MicroSD Card | 256GB Class 10 (IQ recording) | 1,500 | Amazon.in |
| 8 | USB Hub | Powered USB 3.0 hub | 800 | Amazon.in |
| 9 | GPS Module (2nd) | u-blox NEO M8N (for geo-tagging) | 1,084 | Robokits |

## Capabilities

### Spectrum Surveillance
- Sweep 1MHz to 6GHz continuously during flight
- Log signal strength vs frequency vs GPS position
- Generate 3D RF heatmaps (frequency x position x power)
- Identify active transmitters and their approximate locations

### Signal Classification (AI)
- Train ML model to classify signal types:
  - WiFi (802.11a/b/g/n/ac)
  - Bluetooth/BLE
  - Cellular (2G/3G/4G/5G)
  - Drone control signals (DJI, FrSky, etc.)
  - Walkie-talkie / PMR446
  - Radar emissions
- Run on Jetson Nano for real-time classification

### Direction Finding
- Use directional antenna rotation or multiple RTL-SDRs
- Estimate bearing to signal source
- Cross-reference with GPS for transmitter geolocation
- Works for signals above noise floor

### Electronic Order of Battle (EOB)
- Map all RF emitters in an area during flight
- Classify by type, frequency, power, modulation
- Output: "RF map" of the area showing all transmitters
- Military application: know what communications exist in a zone

## Software Stack
- **GNU Radio** — signal processing, spectrum scanning
- **SigMF** — Signal Metadata Format for recording IQ samples
- **inspectrum** — visual signal analysis
- **TensorFlow Lite** — signal classification model on Jetson
- **Custom Python** — geo-tagged logging, heatmap generation
- **QGIS** — post-flight RF heatmap visualization

## Key Features
- **Wideband coverage** — 1MHz to 6GHz with dual SDR setup
- **AI signal classification** — auto-identify signal types in real-time
- **Geo-tagged logging** — every signal logged with GPS coordinates
- **RF heatmap generation** — visualize electromagnetic environment
- **Passive only** — legal for research, no active transmission
- **Portable** — entire setup weighs ~300g added to drone

## Limitations
- HackRF One adds cost (Rs.15-20K)
- Half-duplex — can't TX and RX simultaneously (but we only RX)
- Direction finding with single antenna is slow (need to rotate)
- IQ recording generates large files (needs fast microSD)
- Analysis of encrypted signals limited to metadata only (legal requirement)

## College Research Angle
- Map RF spectrum of your college campus from the air
- Compare ground-level vs aerial RF propagation
- Classify signal types using ML (train on known signals, test on unknown)
- Publish: "Aerial RF Spectrum Survey and Signal Classification Using SDR and Edge AI"
- Study: signal propagation differences at various altitudes

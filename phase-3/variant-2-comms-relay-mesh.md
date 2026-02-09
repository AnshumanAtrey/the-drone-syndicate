# Variant 2 — Airborne Communications Relay / Mesh Node

**Additional Cost Over Phase 1: Rs. 5,000 - 12,000**

Drone acts as a flying cell tower / radio relay for ground troops. When terrain blocks ground comms (mountains, urban, jungle), a drone at 50-100m altitude provides line-of-sight between units. Indian Army uses this concept in Ladakh/Siachen. This is also how military MANET (Mobile Ad-hoc Network) systems work.

> **Ref:** Rajant Corporation sells military mesh radios for drone-based comms relay. Indian Army uses drones as radio relays on LAC. US military's MUOS and JTRS programs include airborne relay nodes. Meshtastic (open-source) runs encrypted LoRa mesh on ESP32.

## Additional Components (on top of Phase 1)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | **LoRa Module x2** | SX1278 433MHz (for mesh network) | 520 (2x 260) | Robokits |
| 2 | **ESP32 + LoRa + OLED** | TTGO LoRa32 (Meshtastic-compatible) | 1,769 | Robocraze |
| 3 | **High-Gain Antenna** | 433MHz 5dBi omnidirectional whip | 300 - 500 | Amazon.in |
| 4 | **Directional Antenna** | 433MHz Yagi 9dBi (for long range) | 800 - 1,500 | Amazon.in |
| 5 | **ESP32 Nodes x3** | Ground units (for mesh network demo) | 1,137 (3x 379) | Robocraze |
| 6 | **LoRa Gateway** (optional) | RAK2247 or RAK5146 concentrator | 8,000 - 12,000 | Amazon.in |
| 7 | **4G Module** | EC200U (if not already in Phase 1) | 1,988 | Robocraze |
| 8 | **USB WiFi Adapter** | High-gain 5dBi for WiFi relay | 500 - 800 | Amazon.in |

## How It Works

### Mode 1: LoRa Mesh Relay (Meshtastic)
1. Ground troops carry ESP32+LoRa nodes running **Meshtastic** firmware
2. Drone carries ESP32+LoRa node at 50-100m altitude
3. Drone's altitude gives line-of-sight to all ground units (even behind hills)
4. Ground units communicate via drone relay — text, GPS position, alerts
5. Range: ground-to-ground LoRa = 1-3km; via drone relay at altitude = **5-15km+**
6. All messages AES-256 encrypted by Meshtastic

### Mode 2: 4G Internet Backhaul
1. Drone carries 4G module connected to companion computer
2. Companion runs WiFi hotspot (hostapd)
3. Troops within 100-200m of drone connect to WiFi
4. Traffic routed through 4G to military command center
5. Essentially a flying WiFi-to-4G bridge
6. Useful when ground 4G coverage is spotty (rural, mountains)

### Mode 3: Radio Repeater
1. Two LoRa radios on drone: one facing forward unit, one facing rear
2. Drone acts as store-and-forward relay between isolated units
3. Can chain multiple drones for extended relay (drone mesh backbone)
4. Each drone extends range by 5-10km

## Network Architecture
```
[Unit Alpha] ←--LoRa--→ [DRONE RELAY @ 80m] ←--LoRa--→ [Unit Bravo]
                              |
                         [4G Backhaul]
                              |
                      [Command Center]
```

## Key Features
- **Beyond-line-of-sight comms** — drone at altitude bridges terrain obstacles
- **Encrypted** — Meshtastic uses AES-256 encryption for all messages
- **Mesh topology** — no single point of failure, self-healing network
- **Position sharing** — every node broadcasts GPS location to all others
- **Low power** — LoRa uses <100mW, doesn't drain drone battery
- **Lightweight** — ESP32+LoRa module weighs ~25g total
- **Open source** — Meshtastic firmware is free, runs on Rs.379 ESP32

## Meshtastic Features (Free, Open-Source)
- Text messaging between nodes
- GPS position sharing (Blue Force Tracker lite)
- Range test mode (measure link quality)
- Telemetry forwarding (sensor data relay)
- Channel-based encryption (different keys for different units)
- MQTT bridge (connect to internet for remote monitoring)
- Works on: ESP32, LoRa32, T-Beam, RAK WisBlock

## Limitations
- LoRa bandwidth is low (~300 bps to 50 kbps) — text and GPS only, no video
- Video relay needs WiFi or 4G (limited range)
- Single drone relay = single point of failure (need redundancy)
- 433MHz LoRa range drops in heavy rain/foliage
- Battery life: drone must stay airborne as long as relay is needed

## Military Applications
- **Forward Operating Base (FOB) comms** — connect patrols to base
- **Mountain warfare** — bridge valleys where radio can't reach (Ladakh/Siachen)
- **Urban warfare** — relay over buildings in city operations
- **Blue Force Tracking** — every unit's GPS position visible to command
- **Emergency relay** — deploy drone when ground comms infrastructure destroyed
- **Naval** — ship-to-shore relay, extend coastal comms range

## College Research Angle
- Deploy 3 ground nodes + 1 drone relay, measure range improvement vs ground-only
- Test: with drone at 30m, 60m, 100m altitude — how does range change?
- Measure: message latency through relay (should be <500ms)
- Stress test: max number of nodes before network congestion
- Publish: "LoRa Mesh Communication Enhancement Using UAV Relay Nodes"

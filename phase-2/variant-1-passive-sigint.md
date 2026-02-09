# Variant 1 — Passive RF Spectrum Monitor

**Additional Cost Over Phase 1: Rs. 10,000 - 18,000**

Passive-only RF monitoring. Receives and logs radio signals across a wide spectrum without transmitting. Used for spectrum mapping, identifying signal sources, and research into RF propagation.

> **Legal:** Passive listening on unencrypted public frequencies is generally legal in India. Do NOT decrypt, demodulate private communications, or interfere with licensed bands.

## Additional Components (on top of Phase 1)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | SDR Receiver | RTL-SDR Blog V4 (R828D, 500kHz-1.7GHz) | 6,000 - 11,200 | Amazon.in / ElectroPi.in / Robu.in |
| 2 | Wideband Antenna | Discone or Wideband Whip (25MHz-1.3GHz) | 1,500 - 3,000 | Amazon.in |
| 3 | SMA Cables/Adapters | SMA to MCX, pigtails | 300 - 500 | Robocraze |
| 4 | USB Hub | Powered USB 2.0 hub (for SDR + 4G) | 500 | Amazon.in |
| 5 | MicroSD Card | 128GB Class 10 (for logging) | 800 - 1,000 | Amazon.in |
| 6 | Optional: HackRF One | 1MHz-6GHz TX/RX SDR (for advanced research) | 11,001 - 25,000 | Robokits (cheapest Rs.11K) / Amazon.in |

## Features
- **Spectrum Scanning:** Sweep 500kHz - 1.7GHz, log signal strengths with GPS coordinates
- **RF Heatmap:** Generate geo-tagged RF spectrum maps during flight
- **Signal Detection:** Identify active frequencies, modulation types, signal strength
- **Software:** GNU Radio + RTL-SDR drivers on Jetson/RPi, SDR# compatible
- **Data Logging:** Store IQ samples to microSD for post-flight analysis
- **Lightweight:** RTL-SDR dongle weighs ~25g, minimal impact on flight

## Software Stack
- **GNU Radio** — signal processing framework
- **rtl_power** — wideband spectrum scanning
- **GQRX** — SDR receiver application
- **Custom Python scripts** — log frequency + GPS + signal strength to CSV

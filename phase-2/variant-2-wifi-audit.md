# Variant 2 — WiFi Network Audit Drone

**Additional Cost Over Phase 1: Rs. 5,000 - 10,000**

Airborne WiFi auditing platform for **authorized penetration testing** of your own networks. Automates wireless reconnaissance from the air — discovers APs, clients, signal coverage, and tests for common vulnerabilities.

> **LEGAL:** Only use on networks you OWN or have WRITTEN PERMISSION to test. Unauthorized access to computer networks is a criminal offense under Indian IT Act 2000, Section 66.

## Additional Components (on top of Phase 1)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | WiFi Adapter | Alfa AWUS036ACH (dual-band, monitor mode) | 3,500 - 4,500 | Amazon.in |
| 2 | Directional Antenna | 2.4GHz 8dBi panel or Yagi (optional) | 800 - 1,500 | Amazon.in |
| 3 | ESP32 Module | ESP32-WROOM-32 (auxiliary scanning) | 450 - 600 | Robocraze |
| 4 | USB Hub | Powered USB hub | 500 | Amazon.in |
| 5 | MicroSD Card | 64GB Class 10 | 500 | Amazon.in |

## Features
- **Passive Scanning:** Discover all APs + clients in range, log SSIDs, BSSIDs, channels, encryption
- **Signal Mapping:** Create geo-tagged WiFi coverage heatmaps during flight
- **Vulnerability Scan:** Test for WEP, open networks, WPS-enabled APs (authorized targets only)
- **Deauth Detection:** Monitor for deauthentication attacks on your network
- **ESP32 Auxiliary:** Dedicated WiFi scanner that runs independently, frees companion computer
- **Automated:** Pre-program flight path, drone scans automatically, download results after landing

## Software Stack
- **Aircrack-ng** — wireless auditing suite
- **Kismet** — wireless network detector/sniffer
- **Wifite2** — automated wireless attack tool (authorized use only)
- **Custom Python** — integrate scan results with GPS data, generate heatmaps
- **ESP32 firmware** — autonomous WiFi beacon scanner using Arduino/ESP-IDF

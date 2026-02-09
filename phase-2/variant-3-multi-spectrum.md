# Variant 3 — Multi-Spectrum Surveillance Drone

**Additional Cost Over Phase 1: Rs. 15,000 - 25,000**

Adds thermal imaging + enhanced optical camera for day/night surveillance, search and rescue, perimeter monitoring, and agricultural/infrastructure inspection.

## Additional Components (on top of Phase 1)

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | Thermal Camera | MLX90640 IR Array (32x24 pixels) | 3,500 - 5,000 | Robocraze / Amazon.in |
| 2 | Better Thermal (opt) | FLIR Lepton 3.5 (160x120) + breakout | 18,000 - 25,000 | Amazon.in / Ubuy |
| 3 | Gimbal | 2-axis servo gimbal for camera stabilization | 2,000 - 3,500 | Robocraze |
| 4 | Night Vision LEDs | 850nm IR LED array (invisible to eye) | 500 - 800 | Amazon.in |
| 5 | Wide-Angle Lens | 160-degree replacement lens for Pi Cam | 300 - 500 | Amazon.in |
| 6 | FPV Transmitter | 5.8GHz 600mW video TX (optional) | 1,500 - 2,500 | Robocraze |
| 7 | MicroSD Card | 128GB Class 10 | 800 - 1,000 | Amazon.in |

## Features
- **Thermal Imaging:** Detect heat signatures through darkness, smoke, foliage
- **MLX90640:** Budget thermal at 32x24px — enough to detect humans/vehicles at 20-50m
- **FLIR Lepton 3.5:** Higher-res thermal (160x120) with radiometric data (actual temps)
- **Dual Feed:** Overlay thermal on optical camera feed for enhanced situational awareness
- **Night Ops:** IR LED illumination + Pi Camera NoIR variant for true night vision
- **Gimbal Stabilized:** 2-axis gimbal keeps camera steady during flight maneuvers
- **AI Integration:** Jetson Nano can run person detection on both thermal + optical feeds

## Software Stack
- **OpenCV** — image processing, camera fusion
- **FLIR SDK / MLX90640 driver** — thermal camera interface
- **Custom Python** — thermal overlay, person detection, alert system
- **GStreamer** — low-latency video pipeline to ground station

## Use Cases (Legal)
- Search and rescue (detect people in darkness/smoke)
- Agricultural crop health monitoring
- Building thermal inspection (insulation leaks)
- Perimeter security of your own property
- Wildlife monitoring at night

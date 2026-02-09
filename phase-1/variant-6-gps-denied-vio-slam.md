# Variant 6 — GPS-Denied Navigation Drone (VIO/SLAM)

**Total Approx Cost: Rs. 75,000 - 95,000** (RealSense D435i is the major cost driver)

Flies autonomously **without GPS** using Visual-Inertial Odometry (VIO) and SLAM. When GPS is jammed or unavailable (indoors, urban canyons, electronic warfare), this drone navigates using cameras + IMU. Inspired by Skydio's autonomous obstacle avoidance and ModalAI's GPS-denied navigation.

> **Ref:** GPS-denied navigation is a top military R&D priority. ModalAI (USA) sells VIO modules. Patent area: MDPI research on Visual Odometry for fixed-wing UAVs in GPS-denied zones.

## Components

| # | Component | Spec | Price (INR) | Source |
|---|-----------|------|-------------|--------|
| 1 | Flight Controller | Pixhawk 2.4.8 PX4 32-Bit | 8,514 | Robocraze |
| 2 | Frame | S500 Carbon Fiber w/ Landing Gear | 3,419 | Robocraze |
| 3 | Motors x4 | A2212 920KV BLDC | 1,800 | Robocraze |
| 4 | ESC x4 | SimonK 30A | 1,288 | Robocraze |
| 5 | GPS Module | NEO M9N (backup, used when available) | 2,099 | Robocraze |
| 6 | Battery | 4S 2200mAh LiPo x2 | 3,948 | Robocraze |
| 7 | RC Transmitter | FlySky FS-i6X + iA10B | 5,109 | Robocraze |
| 8 | Companion Computer | **NVIDIA Jetson Nano 4GB** | 17,999 | Robocraze |
| 9 | **Depth Camera** | Intel RealSense D435i (stereo + IMU) | 37,199 - 51,299 | MGSL.in (authorized dealer) / Amazon.in |
| 10 | **Optical Flow Sensor** | PMW3901 (Holybro/Pimoroni breakout) | 1,500 - 3,260 | Fab.to.Lab / Zbotic.in / Amazon.in |
| 11 | Downward Camera | Pi Camera V2 (for VIO) | 1,882 | Robocraze |
| 12 | 4G Module | EC200U 4G LTE GNSS | 1,988 | Robocraze |
| 13 | LiDAR | TFMini-S (12m forward) | 3,259 | Prayog India |
| 14 | Power Distribution | PDB-XT60 + 5V UBEC | 665 | Robocraze |
| 15 | Propellers | 1045 Props (3 pairs) | 250 | Robocraze |

## How GPS-Denied Navigation Works
1. **Intel RealSense D435i** provides stereo depth + built-in IMU
2. Jetson Nano runs **ORB-SLAM3** or **VINS-Fusion** for real-time VIO
3. Visual features from camera + IMU data fused to estimate position/velocity
4. Position estimates sent to Pixhawk as fake GPS via MAVLink (`GPS_INPUT` message)
5. Pixhawk flies normally — it doesn't know GPS is actually VIO
6. **PMW3901 optical flow** provides additional velocity estimate (redundancy)
7. **TFMini-S LiDAR** provides altitude hold without barometer drift

## Navigation Modes
| Mode | Sensors Used | Accuracy | Use Case |
|------|-------------|----------|----------|
| Full GPS | M9N GPS + compass | ~2m | Outdoor, no jamming |
| VIO Primary | RealSense D435i + IMU | ~0.5m drift/100m | GPS jammed, outdoor |
| Indoor | Optical Flow + D435i + LiDAR | ~0.3m | Indoor flight, tunnels |
| Degraded | Optical Flow + IMU only | ~2m drift/100m | Low light, featureless |

## Key Features
- **GPS-independent** — flies autonomously using vision + IMU fusion
- **Obstacle avoidance** — RealSense D435i provides 3D depth map at 30fps
- **Seamless handover** — auto-switches from GPS to VIO when GPS degrades
- **Indoor capable** — can fly inside buildings, tunnels, warehouses
- **SLAM mapping** — builds 3D map of environment in real-time
- **Jetson CUDA** — ORB-SLAM3 runs at 30fps on Jetson Nano with GPU acceleration

## Software Stack
- **ORB-SLAM3** — state-of-the-art visual SLAM (stereo + IMU mode)
- **VINS-Fusion** — alternative VIO, better for fast motion
- **ROS2** — middleware connecting RealSense, SLAM, and MAVLink
- **MAVROS** — bridge between ROS2 and Pixhawk
- **realsense-ros** — Intel RealSense ROS2 driver

## Limitations
- RealSense D435i adds ~72g + Rs.12-18K cost
- VIO drifts over long distances without loop closure
- Doesn't work in completely featureless environments (blank walls, fog)
- Needs good lighting for visual features (fails in pitch dark)
- Compute-heavy — Jetson Nano at near-full utilization running SLAM

## College Research Angle
- Compare: GPS accuracy vs VIO accuracy vs fused GPS+VIO
- Test: fly same path with GPS, then with GPS jammed (simulate by disabling GPS in firmware)
- Publish: "Autonomous UAV Navigation in GPS-Denied Environments Using Visual-Inertial Odometry"
- Benchmark: ORB-SLAM3 vs VINS-Fusion on Jetson Nano (FPS, accuracy, CPU/GPU usage)

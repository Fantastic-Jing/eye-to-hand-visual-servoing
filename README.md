# Visual Servoing for Igus ReBeL 6DOF Robot

This project implements a visual servoing system for an Igus ReBeL 6DOF robot.

The goal is simple:

**detect a target in the image and move the robot to reduce the error.**

---

## System Overview

The system connects vision and robot control in one loop:

```

Image → Feature Detection → Pixel Error → Camera Space → Robot Space → Joint Control

```

Core idea:

The robot moves based on what the camera sees.

---

## Main Components

### 1. Vision
- Template matching
- ROI optimization
- Pixel coordinate extraction

### 2. Kinematics
- Forward kinematics (FK)
- Jacobian matrix
- Coordinate transformation (camera ↔ robot)

### 3. Control
- Visual feedback control (P control)
- Look-and-move strategy
- Joint velocity control

---

## Key Equation

```

Δq = J⁻¹ · A_cam0 · Jv⁻¹ · Δf

```

This connects:
- image space
- camera space
- robot joint space

---

## Robot & Setup

- Robot: Igus ReBeL 6DOF
- Camera: Raspberry Pi HQ Camera
- Configuration: Eye-to-hand (camera fixed above workspace)

---

## Experiments

- Template matching accuracy test
- Coordinate system transformation
- Visual servoing control loop
- Robot trajectory observation

---

## Why this works

Even without perfect calibration, the system can still converge because:
- feedback loop corrects error continuously
- P control is enough for stability in this setup

---

## Status

Work in progress. Core pipeline is being implemented and tested step by step.

---

## Future Work

- Improve calibration accuracy
- Add full inverse kinematics solver
- Compare different visual features (SIFT / ORB / template matching)
- Real-time performance optimization

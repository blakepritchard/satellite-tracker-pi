# SatTrackerPi: 3-Axis Telemetry & Edge Compute

**Watch the live hardware demonstration here:** [SatTrackerPi Overview & Demo](https://www.youtube.com/watch?v=HFVWX1Un5f8&pp=0gcJCb4KAYcqIYzv)

## Overview
This repository contains the edge-compute orchestration layer for an automated 3-axis (Azimuth, Elevation, Polarity) satellite tracking antenna rotator. It bridges the gap between digital orbital prediction algorithms and deterministic physical hardware actuation. 

## IT/OT Convergence Architecture
This system acts as a localized SCADA controller on the edge (Raspberry Pi). It translates incoming TCP/IP telemetry streams into physical state changes.

* **Predictive Input:** Integrates with GPredict orbit prediction software using the EasyComm II serial protocol.
* **The Daemon (`SatTrackerPiDaemon`):** A custom Python hardware abstraction layer that parses orbital mechanics data and calculates real-time positional deltas.
* **Hardware Actuation:** Executes deterministic mechanical movement via Stepper HATs, controlling NEMA stepper motors and reading encoder feedback.
* **Telemetry Visualization (`SatTrackerPiWebServer` / `Client`):** A localized web UI for real-time monitoring of the physical hardware state and manual override controls.

## Tech Stack
* **Hardware:** Raspberry Pi, Adafruit Stepper Motor HATs, NEMA Stepper Motors.
* **Software:** Python 3, Bash, HTML/JS (Web Client), EasyComm II Protocol.
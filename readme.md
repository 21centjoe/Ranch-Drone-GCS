# RanchDrone GCS — Comprehensive Readme & Community Guide

**An open-source, non-competitive Ground Control Station (GCS) designed to help communities design, build, and fly drones for local agricultural and ranching packages.**

---

## 1. What Is This Experiment?
Technology transfer often fails because tools are either locked behind expensive proprietary software or built for military/corporate scale rather than localized community empowerment. **RanchDrone GCS** is a lightweight, local-first Ground Control Station embedded inside a single self-contained HTML/JS application backed by a minimal Python MAVLink relay.

It is built for anyone who wants to:
* Learn the underlying tech (ArduPilot architecture, MAVLink telemetry, and mission planning).
* Build their own custom drone configurations using standard off-the-shelf hardware components (Holybro, CubePilot, mRo, etc.).
* Market customized crop scouting, livestock tracking, and pasture mapping packages to their local ranching communities.

---

## 2. Key Features
* **Zero-Cloud, Local-First Architecture:** Runs entirely on your local machine or an edge server. Your mission data and coordinates stay private.
* **Intelligent Mission Planning:** Supports manual waypoints, automated lawnmower survey patterns, and hexagonal scouting grids.
* **Weather & Airspace Overlays:** Direct integration with live NWS (National Weather Service) data to automatically calculate "Go / No-Go" wind safety thresholds, alongside FAA No-Fly Zones and utility power line overlays.
* **Mission Command Table:** Full MAVLink mission command editor that translates map coordinates directly into ArduPilot-compatible flight sequences (`NAV_TAKEOFF`, `NAV_WAYPOINT`, `NAV_RETURN_TO_LAUNCH`, etc.).
* **Live Telemetry & Simulation:** Built-in flight simulation mode to preview missions, plus real-time MAVLink telemetry dashboards for pitch, roll, altitude, battery status, and GPS fix.
* **Auto-Session Persistence:** LocalStorage tracking saves your entire session automatically on every keystroke, allowing you to close and reopen the browser without losing progress.

---

## 3. Quickstart Guide

### Step 1: Start the Local Relay Server
The relay server bridges your browser interface to the physical flight controller (or software-in-the-loop simulator) via MAVLink. Open your terminal in the toolkit directory and run:

```bash
python3 relay/ranch_server.py --connection udp:127.0.0.1:14550

# RanchDrone GCS — Comprehensive Readme & Community Guide

An open-source, non-competitive Ground Control Station (GCS) designed to help communities design, build, and fly drones for local agricultural and ranching packages.

---

## 1. What Is This Experiment?

Technology transfer often fails because tools are either locked behind expensive proprietary software or built for military/corporate scale rather than localized community empowerment. RanchDrone GCS is a lightweight, local-first Ground Control Station embedded inside a single self-contained HTML/JS application backed by a minimal Python MAVLink relay.

It is built for anyone who wants to:

* Learn the underlying tech (ArduPilot architecture, MAVLink telemetry, and mission planning).


* Build their own custom drone configurations using standard off-the-shelf hardware components (Holybro, CubePilot, mRo, etc.).


* Market customized crop scouting, livestock tracking, and pasture mapping packages to their local ranching communities.



---

## 2. Key Features

* **Zero-Cloud, Local-First Architecture:** Runs entirely on your local machine or an edge server. Your mission data and coordinates stay private.


* **Intelligent Mission Planning:** Supports manual waypoints, automated lawnmower survey patterns, and hexagonal scouting grids.


* **Weather & Airspace Overlays:** Direct integration with live NWS (National Weather Service) data to automatically calculate "Go / No-Go" wind safety thresholds, alongside FAA No-Fly Zones and utility power line overlays.


* **Mission Command Table:** Full MAVLink mission command editor that translates map coordinates directly into ArduPilot-compatible flight sequences (NAV_TAKEOFF, NAV_WAYPOINT, NAV_RETURN_TO_LAUNCH, etc.).


* **Live Telemetry & Simulation:** Built-in flight simulation mode to preview missions, plus real-time MAVLink telemetry dashboards for pitch, roll, altitude, battery status, and GPS fix.


* **Auto-Session Persistence:** LocalStorage tracking saves your entire session automatically on every keystroke, allowing you to close and reopen the browser without losing progress.



---

## 3. Quickstart Guide

### Step 1: Start the Local Relay Server

The relay server bridges your browser interface to the physical flight controller (or software-in-the-loop simulator) via MAVLink. Open your terminal in the toolkit directory and run:

python3 relay/ranch_server.py --connection udp:127.0.0.1:14550

### Step 2: Open the Ground Control Station

Open your browser and navigate to:
http://localhost:8765/
*(Note: Do not double-click the HTML file directly; it must be served through the local server to allow weather API fetches and map tile loading).*

### Step 3: Configure Your Drone

1. Go to the Setup tab.


2. Select your autopilot board make and airframe model (e.g., Holybro Pixhawk 6C, Cube Orange).


3. Confirm or adjust your MAVLink connection string (udp:127.0.0.1:14550 for simulation, or /dev/ttyUSB0,57600 for a physical telemetry radio).



### Step 4: Plan, Simulate, and Fly

1. Navigate to Plan & Fly to drop boundary pins or generate an automated lawnmower/hex scouting grid over your local pasture.


2. Check the Weather tab to verify that wind speeds are safe against your custom no-go threshold.


3. Click Fly The Mission (Sim) to visually verify the flight path, then head to Compile & Upload to send the mission package directly to your flight controller via MAVLink.



---

## 4. Architecture & Technical Details

The platform is engineered around principles tailored for field operators and independent tinkerers:

* **Minimalist Tech Stack:** Built using pure vanilla JavaScript, CSS, and HTML for the frontend, requiring zero node modules, npm builds, or complex compilation steps on the user end.


* **MAVLink Protocol Compatibility:** Communicates using standard MAVLink binary message framing over UDP or Serial, making it fully compatible with ArduPilot (ArduCopter / ArduPlane) and PX4 flight stacks.


* **Hardware Interoperability:** Designed to interface seamlessly with common ground telemetry modules, such as SiK telemetry radios and ESP32-based Wi-Fi/UDP bridges.


* **Offline Resilience:** Map tiles and waypoint templates can be cached locally, allowing field operators to deploy the system in remote rural areas with intermittent or zero cellular connectivity.



---

## 5. Advanced Customization & Deployment

To adapt the toolkit for specialized operational environments or alternative hardware setups, review the following deployment guidelines:

* **Edge Processing Integration:** The system can be configured to offload computer vision tasks—such as weed detection or livestock head-counting—to an onboard companion computer via MAVLink companion protocols.


* **Power Management Protocols:** Ensure your telemetry radios and relay servers are paired with an independent power regulation circuit to prevent brownouts during high-draw motor spool-ups.


* **Firmware Tuning:** Adjust PID loop filters directly through the interface's MAVLink parameter editor to compensate for heavy agricultural payload variances.



---

## 6. Community Guidelines & Contributions

RanchDrone GCS is a collaborative community project. Whether you are an agricultural extension agent, an open-source developer, or a rancher looking to automate pasture checks, your contributions are welcome:

* **Code Contributions:** Fork the repository, submit pull requests for new MAVLink message handlers, or improve the lawnmower pattern generation algorithms.


* **Hardware Profiles:** Share your tested configurations (motor/ESC pairings, battery capacities, and frame builds) to help others replicate successful builds.


* **Safety First:** Always follow local aviation regulations (such as FAA Part 107 guidelines or international equivalents), maintain visual line of sight, and test all flight plans in simulation mode before running live flights near livestock or property.
  
* https://translate.google.com/

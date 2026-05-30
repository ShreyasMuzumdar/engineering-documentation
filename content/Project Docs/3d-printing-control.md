# 🖨️ 3D Printing Manufacturing Control

## 🎯 Project Overview

This project documents my journey building a fully remote-controllable 3D printing setup — starting from a stock printer, working through hardware limitations, and eventually arriving at a system I can monitor and manage from anywhere. A core motivation was intentional: rather than jumping straight to a high-end printer, I wanted to deeply understand the engineering and software behind how 3D printers actually work.

---

## 🛠️ Hardware: Creality Ender 3 V2

### Starting Point

I started with a stock **Creality Ender 3 V2**. While it's a capable entry-level printer, I quickly ran into a few key issues that needed to be solved before I could get reliable prints.

### Upgrades & Modifications

#### 1. BL Touch — Automatic Bed Leveling
The first major issue was an unlevel bed, which caused inconsistent first layers and failed prints. I solved this by adding a **BL Touch probe**, which automatically maps the bed surface and compensates for any unevenness during printing.

#### 2. Dual Z-Axis
The stock Ender 3 V2 only has a single Z-axis motor on one side of the gantry. This caused the X-axis to tilt slightly over time, leading to inaccuracy across the full print width. Adding a **second Z-axis** (dual Z upgrade) kept the gantry level throughout the full build height, significantly improving print consistency.

#### 3. Direct Drive Extruder Upgrade
I also added a **direct drive extruder** conversion. While not strictly necessary, moving the extruder directly above the hotend reduced the distance filament had to travel, which improved retraction performance and reduced variability in extrusion — particularly useful for flexible or stringy filaments.

---

## 💻 Software & Remote Control

### OctoPrint on Raspberry Pi

To control the printer, I set up **OctoPrint** on a spare **Raspberry Pi**. OctoPrint is an open-source print server with a large plugin ecosystem, giving me a web-based dashboard to:

- Upload and manage print files
- Monitor print progress in real time
- Control printer settings and temperatures
- Access community plugins for extended functionality

### OctoEverywhere — Remote Access

To enable monitoring from anywhere, I integrated **OctoEverywhere**, which creates a secure tunnel to the OctoPrint instance. This lets me check in on active prints remotely — whether I'm in another room or away from home — and catch issues before they waste a full spool of filament.

---

## 📚 What I Learned

Deliberately starting with a budget printer that required troubleshooting and upgrading turned out to be one of the best engineering decisions I made. Over time, I gained a deep understanding of:

- How FDM 3D printers work mechanically and kinematically
- How print quality is affected by hardware tuning (bed leveling, Z-axis alignment, extrusion path)
- How to set up and self-host a print management server
- How to architect a system for reliable remote access

The ability to monitor and control the printer from anywhere wasn't just a convenience feature — it became a major driver of how well I understood the system end-to-end.

---

## 🔧 Technical Specifications

**Hardware:**
- Creality Ender 3 V2 (modified)
- BL Touch Auto Bed Leveling Probe
- Dual Z-Axis Upgrade Kit
- Direct Drive Extruder Conversion

**Software & Tools:**
- OctoPrint (self-hosted on Raspberry Pi)
- OctoEverywhere (remote access tunnel)
- Raspberry Pi (print server host)

**Skills Applied:**
- FDM hardware modification & calibration
- Embedded Linux / Raspberry Pi setup
- Self-hosted server configuration
- Remote system monitoring

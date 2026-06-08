# 🖨️ 3D Printing Manufacturing Control

## 🎯 Project Overview

This project documents my journey building a fully remote-controllable 3D printing setup, starting from a stock printer, working through hardware limitations, and eventually arriving at a system I can monitor and manage from anywhere. A core motivation was intentional: rather than jumping straight to a high-end printer, I wanted to deeply understand the engineering and software behind how 3D printers actually work.

The self-hosting mindset developed here carried directly into later projects. Setting up OctoPrint on a Raspberry Pi was the first time I ran a server for a real purpose, and that experience became the foundation for the [[Project Docs/Home Automation System|Home Automation System]] and eventually [[Project Docs/hermes-assistant|Hermes]].

## 🛠️ Hardware: Creality Ender 3 V2

### Starting Point

I started with a stock Creality Ender 3 V2. While it is a capable entry-level printer, I quickly ran into a few key issues that needed to be solved before I could get reliable prints.

### Upgrades and Modifications

#### 1. BL Touch, Automatic Bed Leveling
The first major issue was an unlevel bed, which caused inconsistent first layers and failed prints. I solved this by adding a BL Touch probe, which automatically maps the bed surface and compensates for any unevenness during printing.

#### 2. Dual Z-Axis
The stock Ender 3 V2 only has a single Z-axis motor on one side of the gantry. This caused the X-axis to tilt slightly over time, leading to inaccuracy across the full print width. Adding a second Z-axis kept the gantry level throughout the full build height, significantly improving print consistency.

#### 3. Direct Drive Extruder Upgrade
I also added a direct drive extruder conversion. While not strictly necessary, moving the extruder directly above the hotend reduced the distance filament had to travel, which improved retraction performance and reduced variability in extrusion, particularly useful for flexible or stringy filaments.

## 💻 Software and Remote Control

### OctoPrint on Raspberry Pi

To control the printer, I set up OctoPrint on a spare Raspberry Pi. OctoPrint is an open-source print server with a large plugin ecosystem, giving me a web-based dashboard to upload and manage print files, monitor print progress in real time, control printer settings and temperatures, and access community plugins for extended functionality.

### OctoEverywhere, Remote Access

To enable monitoring from anywhere, I integrated OctoEverywhere, which creates a secure tunnel to the OctoPrint instance. This lets me check in on active prints remotely and catch issues before they waste a full spool of filament. The tunnel architecture is conceptually identical to what I later used with Cloudflare Tunnels in the [[Project Docs/hermes-assistant|Hermes]] infrastructure stack.

## 📚 What I Learned

Deliberately starting with a budget printer that required troubleshooting and upgrading turned out to be one of the best engineering decisions I made. Over time, I gained a deep understanding of how FDM 3D printers work mechanically and kinematically, how print quality is affected by hardware tuning, how to set up and self-host a print management server, and how to architect a system for reliable remote access.

## 🔧 Technical Specifications

**Hardware:**
- Creality Ender 3 V2 (modified)
- BL Touch Auto Bed Leveling Probe
- Dual Z-Axis Upgrade Kit
- Direct Drive Extruder Conversion

**Software and Tools:**
- OctoPrint (self-hosted on Raspberry Pi)
- OctoEverywhere (remote access tunnel)
- Raspberry Pi (print server host)

**Skills Applied:**
- FDM hardware modification and calibration
- Embedded Linux / Raspberry Pi setup
- Self-hosted server configuration
- Remote system monitoring

**Related Projects:**
- [[Project Docs/Home Automation System|Home Automation System]], same Raspberry Pi self-hosting approach
- [[Project Docs/hermes-assistant|Hermes Assistant]], Cloudflare Tunnel remote access built on same concept

---
tags:
  - portfolio
  - robotics
  - engineering
  - hardware
  - software
  - computer-vision
  - automation
cssclasses:
  - engineering-portfolio
created: 2026-05-30
status: active
---

# ⚙️ Shreyas Muzumdar — Engineering Portfolio

> *"Engineering excellence isn't defined by the number of features, but by the robustness of the core mechanics under competition pressure."*

---

## 🧑‍🔧 About Me

**Shreyas Muzumdar** — Robotics & Hardware Engineer based in **Shrewsbury, Massachusetts**.

- 🏫 Student at **Saint John's High School**
- 🤖 Hardware Engineer @ **FTC Team 12589 — Pioneer Robotics** (sponsored by Coghlin Companies)
- 🏢 Former Intern @ **Robo Hub**
- 🌐 Portfolio: [shreyasmuzumdar.github.io](https://shreyasmuzumdar.github.io/reactwebsite)

I build things that move, think, and respond to the real world — from FTC competition robots to AI-powered cameras and custom voice assistants.

---

## 🗂️ Project Index

| Project | Category | Stack / Domain |
|---|---|---|
| [[MantisBot]] | 🤖 Robotics (FTC) | Mechanical Design, CAD, Agile |
| [[BlackBox]] | 🤖 Robotics | Hardware Engineering |
| [[ShreyBot]] | 🤖 Robotics | Hardware / Software |
| [[StretchBot]] | 🤖 Robotics | Hardware Engineering |
| [[OpenClaw Assistant]] | 🦾 Robotics / CV | Computer Vision, Servo Control |
| [[Satellite Tracking]] | 🛰️ Systems | Orbital Mechanics, Hardware |
| [[3D Printing Manufacturing Control]] | 🖨️ Manufacturing | Control Systems, Fabrication |
| [[Auto Tracking Camera]] | 📽 Computer Vision | ML, Face Detection, Servo |
| [[Hand Tracking Mouse]] | ✋ Computer Vision | MediaPipe, PyAutoGUI |
| [[Home Automation System]] | 🏠 IoT | Raspberry Pi, Smart Devices |
| [[ShreyAI Voice Assistant]] | 🤖 AI / NLP | DeepSeek, Ollama, TTS |
| [[Connect 4 AI Bot]] | 🧠 Algorithms | Python, Minimax, Alpha-Beta |
| [[Python Automations]] | 🐍 Software | Python Scripting |

---

## 🤖 Robotics — Hardware Engineering

### MantisBot
> *FTC "Into the Deep" season robot — Pioneer Robotics 12589*

**Overview:** MantisBot is a full FTC competition robot designed to collect underwater-themed samples and specimens and deposit them in scoring zones, ending with a bar-climb. The season began with ambitious goals (PTO + Differential Swerve) and evolved into a focused, reliable final system after a deliberate midseason simplification.

**Season Methodology:** Agile sprints (2-week cycles), daily standups, formal sprint reviews. Documentation of every design decision enabled the rapid midseason redesign.

#### 🔧 Mechanisms

**Chassis & Drivetrain**
- **Problem:** Previous live-axle drivetrain caused inconsistencies and floor-drag disconnect issues.
- **Solution:** Switched to a **dead-axle mecanum drivetrain** — reduced chassis footprint by 25%, relocated electronics, added a modular upper chassis detachable without touching the drive base. Spring-loaded **odometry pods** integrated for match-long localization accuracy.
- **Result:** Significantly more consistent. Modular chassis saved critical time during the midseason rebuild.

**Differential Claw** 🦀
- **Problem:** Initial claw was too bulky to maneuver inside the Submersible structure.
- **Solution:** Iterated through 3 designs. Final version used a **bevel gear differential mechanism** (knowledge from the abandoned PTO prototype) — rotates on two axes simultaneously in a compact form factor.
- **Result:** Lightweight, reliable, more rotational freedom than any prior iteration. *The failed PTO mechanism produced the knowledge that made the working claw.*

**Slides Actuation & Pivot** ⬆️
- **Problem:** Needed linear slides that could both extend and pivot without separate motors. Belt skipping caused position loss mid-match.
- **Solution:** Custom two-sided pulley with bearings spinning freely on the axle. Shifted motor mounting holes to fix belt tension. Switched to a single slide set. Replaced polycarbonate inserts with **custom aluminum inserts** after breaking 8 polycarbonate versions.
- **Result:** Single-slide system more reliable. Belt skipping resolved. Aluminum held through the full season.

**Ascent / Climb** 🧗
- **Problem:** End-game bar climbing without adding a dedicated mechanism.
- **Solution:** Climb attaches directly to existing linear slides. Static hooks engage the bar on slide retraction. Motor selected via torque calculation.
- **Result:** No dedicated climb mechanism needed — saved weight and motor ports entirely.

#### 💡 Key Takeaways

1. **Ambition Needs a Cutoff Date** — Set hard go/no-go dates for experimental mechanisms upfront.
2. **Failed Mechanisms Teach Working Ones** — PTO → bevel gear knowledge → differential claw.
3. **Test to Failure, Then Choose the Right Material** — 8 broken polycarbonate mounts gave conclusive data for aluminum.
4. **Simplicity Is a Design Decision, Not a Fallback** — A reliable simple robot beats a complex one that breaks.

---

## 📽 Computer Vision Projects

### Auto Tracking Camera
> *ML-powered camera that follows faces in real-time*

Intelligent camera attachment using ML and computer vision to detect, track, and follow human faces. Dynamically adjusts angle and position to keep the target centered.

**Tech:** Computer Vision · Face Detection · Servo Control · Real-time ML inference

---

### Hand Tracking Mouse ✋
> *Control your cursor with your hand — no mouse needed*

Hands-free input device converting hand position and gestures into mouse movements and clicks. Great for accessibility, presentations, and gaming.

**Tech:** MediaPipe · Python · PyAutoGUI · OpenCV

---

## 🏠 IoT & Systems

### Home Automation System
> *Unified control for 150+ smart devices*

Comprehensive home automation platform integrating **150+ smart devices** from various manufacturers, all controlled through a central **Raspberry Pi** server hub.

**Tech:** Raspberry Pi · MQTT · Home Assistant · Multi-vendor integration

---

### Satellite Tracking 🛰️
> *Hardware + software system for tracking orbital objects*

Combines orbital mechanics calculations with physical hardware to locate and follow satellites in real-time.

**Tech:** Orbital mechanics · Hardware control · Servo systems

---

## 🤖 AI / Software Projects

### ShreyAI Voice Assistant
> *A local, private voice assistant with a custom-cloned voice*

Sophisticated voice assistant combining a **custom-cloned voice** with advanced LLMs. Runs **fully local** on Mac or Raspberry Pi — no cloud, full privacy, smart device control.

**Powered by:** DeepSeek · Ollama · Custom TTS voice cloning

---

### Connect 4 AI Bot 🧠
> *A virtually unbeatable Connect 4 engine*

High-performance Connect 4 AI in Python using:
- **Minimax** — maximizes winning chance by simulating opponent moves
- **Alpha-Beta Pruning** — 10x+ fewer nodes evaluated, sub-second response
- **Transposition Table** — caches board states to eliminate redundant calculations

> 🎮 [Play the game](https://shreyasmuzumdar.github.io/connect-4/)

---

### 3D Printing Manufacturing Control System 🖨️

Automated control system for managing and orchestrating 3D printing manufacturing workflows.

**Tech:** Manufacturing automation · Print queue management · Control systems

---

### Python Automations 🐍

Toolkit of automation scripts:
- **QR Code Generator** — convert any text/URL instantly
- **Intelligent File Organizer** — auto-categorize and manage files

---

## 🛠️ Tech Stack & Skills

```
Hardware          │  Software            │  AI / ML
──────────────────┼──────────────────────┼────────────────────
FTC Robotics      │  Python              │  Computer Vision
CAD / Mechanical  │  Raspberry Pi        │  Face / Hand Detection
Servo Systems     │  Home Automation     │  Minimax / Alpha-Beta
Linear Slides     │  Shell Scripting     │  LLM Integration (Ollama)
Bevel Gears       │  Web (HTML/CSS/JS)   │  Voice Cloning / TTS
3D Printing       │  React               │  MediaPipe
Aluminum Fab      │  Git / GitHub        │  OpenCV
```

---

## 📎 Links

- 🌐 **Portfolio:** https://shreyasmuzumdar.github.io/reactwebsite
- 💼 **LinkedIn:** https://www.linkedin.com/in/shreyasmuzumdar/
- 🎮 **Connect 4:** https://shreyasmuzumdar.github.io/connect-4/
- 🤖 **FTC Team:** Pioneer Robotics 12589

---

*Last updated: 2026-05-30*

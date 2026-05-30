---
title: Shreyas's Engineering Notebook
---

# 🛠️ Shreyas Muzumdar — Engineering Notebook

I'm a mechanical engineering student at Northeastern University, but my engineering journey started long before university. It started with a robot that didn't work, a printer that wouldn't level, and a home network I refused to leave unautomated.

This notebook is a living record of that journey — not just what I built, but how I thought through it, what broke, what I changed, and what I learned.

---

## The Design Process as a Way of Thinking

Every project in this notebook follows the same underlying loop: understand the problem, research the constraints, prototype a solution, test it against reality, and iterate. That cycle — **define, research, design, build, test, improve** — isn't just a framework I apply to engineering. It's genuinely how I approach problems.

The earliest version of this showed up in robotics. Building FTC competition robots with Pioneer Robotics forced me to think about systems, not just parts. A mechanism that works in isolation fails on the field if it doesn't integrate cleanly with the drivetrain, the software, or the strategy. Three state finalist appearances and a state championship didn't come from any single great idea — they came from iterating faster and more deliberately than everyone else.

---

## From Mechanical to Software to Everything in Between

What surprised me as I got deeper into engineering was how artificial the boundary between hardware and software is. When I built out my [[Project Docs/home-automation|Home Automation System]], I wasn't just configuring smart devices — I was designing a network architecture, writing MQTT logic, and debugging Raspberry Pi firmware, all in service of a single goal: a home that responds intelligently to its environment.

The same was true for my [[Project Docs/3d-printing-control|3D Printing setup]]. What started as trying to get cleaner prints from a stock Ender 3 V2 turned into a full systems project — dual Z-axis hardware modifications, a BL Touch for automated bed leveling, a direct drive extruder upgrade, and eventually a self-hosted OctoPrint server on a Raspberry Pi with OctoEverywhere for remote monitoring. I could have bought a better printer. I chose not to, because I wanted to understand the system.

---

## Automating the Environment, Automating the Work

A recurring theme across my projects is using engineering to reduce friction — in my environment, in my workflow, and in my thinking. The [[Project Docs/hermes-assistant|Hermes Assistant]] is the clearest expression of this: a hybrid local/cloud AI system that monitors my home server infrastructure, controls IoT devices through natural language, and generates weekly automated health reports — running on consumer hardware I configured myself.

The [[Project Docs/voice-assistant|Voice Assistant]] took the same philosophy to personal productivity: a fully local, privacy-focused assistant with a custom-cloned voice, running on a Mac or Raspberry Pi without sending data to any external service.

[[Project Docs/python-automations|Python Automations]] and the [[Project Docs/auto-tracking-camera|Auto-Tracking Camera]] followed the same pattern — identify something tedious or manual, engineer a solution, and refine it until it actually works in the real world.

---

## The Notebook Itself

Even this documentation system is an engineering project. The [[Project Docs/setup-journey|Setup Journey]] documents how I connected Claude AI to this Obsidian vault using the Model Context Protocol — including every configuration error, SSL certificate issue, and session drop that had to be debugged along the way. The goal was a system where I can speak or type instructions and have Claude edit files, rename documents, and push commits to GitHub directly.

That's the mindset this notebook represents: if there's friction, engineer it away.

---

## 📚 Projects

- [[Project Docs/3d-printing-control|3D Printing Control]] — Ender 3 V2 hardware mods and remote monitoring via OctoPrint
- [[Project Docs/hermes-assistant|Hermes Assistant]] — Hybrid AI orchestration layer for home automation and infrastructure
- [[Project Docs/home-automation|Home Automation]] — Raspberry Pi, MQTT, and multi-vendor smart device integration
- [[Project Docs/voice-assistant|Voice Assistant]] — Local, private voice assistant with custom-cloned voice
- [[Project Docs/satellite-tracking|Satellite Tracking]] — Hardware and software system for real-time satellite tracking
- [[Project Docs/auto-tracking-camera|Auto-Tracking Camera]] — Computer vision camera that follows movement autonomously
- [[Project Docs/hand-tracking-mouse|Hand Tracking Mouse]] — MediaPipe-based hands-free mouse control
- [[Project Docs/connect4|Connect 4 AI]] — Minimax algorithm implementation with a web interface
- [[Project Docs/python-automations|Python Automations]] — Collection of scripts automating repetitive tasks
- [[Robot Docs/StretchBot|StretchBot]] — 2023 MA State Champion FTC robot
- [[Robot Docs/MantisBot|MantisBot]], [[Robot Docs/Shreybot|Shreybot]], [[Robot Docs/BlackBox|BlackBox]] — FTC competition robots across four seasons
- [[Project Docs/setup-journey|The Setup Journey]] — How this notebook was built and connected to Claude

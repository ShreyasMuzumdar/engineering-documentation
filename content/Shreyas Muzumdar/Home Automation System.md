---
tags:
  - portfolio
  - engineering
  - iot
  - home-automation
  - raspberry-pi
  - voice-assistant
  - ollama
cssclasses:
  - engineering-portfolio
created: 2022-01-01
updated: 2026-05-30
status: active
---

# 🏠 Home Automation System

> *Built in 2022 — the project that gave me the foundation for understanding how interconnected systems work.*

---

## Overview

The Home Automation System is a locally-hosted smart home platform built on **Home Assistant**, running on a central Raspberry Pi server. It unifies 150+ smart devices from different manufacturers into a single, private, fully automated ecosystem — with a custom voice assistant built on top.

This was one of the first major systems I built, and it became the foundation for everything that followed. At the time (2022), many of the tools I'd later rely on — local LLMs, mature voice pipelines — either didn't exist or weren't production-ready. This project taught me how to work around those gaps.

---

## Problem

### Fragmented Devices, Fragmented Control

Modern smart home devices come from dozens of different manufacturers — Philips, TP-Link, Nest, Ring, and more — each with their own app, their own cloud service, and their own communication protocol. To control everything, I would have needed to:

- Sign up for and maintain **100+ separate accounts and services**
- Accept that each service was **collecting and storing my personal data**
- Juggle a different app for every device category
- Accept **no cross-device automation** — a Philips light couldn't talk to a Nest sensor without routing through external cloud servers

The fragmentation wasn't just inconvenient — it was a privacy problem. Every device was phoning home to a different company.

---

## Solution

### A Single Local Hub — Home Assistant on Raspberry Pi

I deployed **Home Assistant** on a Raspberry Pi as a central hub for every device in the house. Home Assistant is an open-source home automation platform that runs entirely on your local network — no cloud required, no data leaving the house.

**How it works:**
- The Raspberry Pi runs 24/7 as a local server on the home network
- Every smart device connects to Home Assistant instead of its manufacturer's cloud
- Home Assistant speaks the native protocol of each device — Z-Wave, Zigbee, Matter, MQTT, and more — so no device needs to be replaced
- A single dashboard gives full control over every device from one place

**Key design decisions:**
- **Local-first**: All data stays on the Raspberry Pi. No third-party cloud services in the loop
- **Protocol agnostic**: Home Assistant's integration library supports 3,000+ devices natively, meaning I didn't have to compromise on which hardware to use
- **Modular**: New devices can be added without restructuring the existing setup

---

## Automation Logic

One of the most powerful features of Home Assistant is its **automation engine** — the ability to define rules that trigger actions based on time, device state, or sensor input.

### Examples of automations I built:

**Time-based lighting:**
- Lights in common areas automatically turn off at a set time each night, regardless of whether anyone remembered to switch them off manually
- Morning routines gradually increase light brightness to simulate a sunrise

**Security:**
- The alarm system arms automatically when the last person leaves the house (detected via phone presence on the home network)
- Motion sensors trigger alerts if movement is detected while the alarm is armed

**Energy management:**
- High-draw devices are scheduled to run during off-peak hours
- Lights in unoccupied rooms switch off automatically after a set idle period

These automations are written in Home Assistant's **YAML-based automation syntax**, which defines a trigger, optional conditions, and a sequence of actions. The logic runs entirely locally — no internet connection needed.

---

## Voice Assistant Subsystem

### Wyoming Protocol + Ollama — A Custom Local Voice Assistant

*(2024 — built after the Home Assistant core was stable)*

After the core system was running reliably, I added a custom voice assistant that integrated directly into Home Assistant. The goal was a fully local, privacy-preserving voice interface — no Alexa, no Google Assistant, no data sent to the cloud.

#### Wyoming Protocol

The **Wyoming protocol** is an open audio streaming protocol designed specifically for local voice assistant pipelines. It handles the communication between the individual components of a voice assistant:

- **Wake word detection** — listens passively for a trigger phrase
- **Speech-to-text (STT)** — converts spoken audio to text
- **Intent handling** — routes the transcribed text to a language model
- **Text-to-speech (TTS)** — converts the response back to audio

Each of these components runs as a separate service on the local network, communicating over Wyoming. Home Assistant acts as the orchestrator, connecting them all together.

#### Ollama Integration

**Ollama** is a local LLM runner — it lets you run large language models entirely on your own hardware without any API calls to external services. I used Ollama to power the intent-handling layer of the voice assistant.

**How the pipeline works:**
1. Wake word detected → audio stream opens
2. Audio transcribed to text via local STT model
3. Text passed to Ollama running a local LLM
4. LLM generates a response and/or triggers a Home Assistant action
5. Response passed to TTS, which speaks back using a **custom-cloned voice**

The custom voice was cloned from my own voice using a local TTS model, meaning the assistant speaks in my voice — a detail that makes the interaction feel noticeably more personal.

#### Why build this in 2024 and not earlier?

In 2022, local LLMs capable of running on consumer hardware didn't exist in any practical form. Ollama itself launched in 2023. The Wyoming protocol and Home Assistant's voice pipeline were also significantly less mature. This subsystem was only buildable once the underlying tools caught up — which is exactly why Home Assistant came first and the voice layer came second.

---

## Results

| Metric | Before | After |
|---|---|---|
| Apps needed | 10+ | 1 |
| Cloud services with data access | 10+ | 0 |
| Cross-device automation | None | Full |
| Voice control | Cloud-dependent | Fully local |
| Devices supported | Per-app | 150+ unified |

- **Privacy:** Zero data leaves the local network for device control or voice queries
- **Reliability:** No dependency on manufacturer cloud uptime — if their servers go down, everything still works
- **Extensibility:** Adding a new device or automation takes minutes, not a new app
- **Foundation:** This project became the basis for understanding local networking, protocol bridging, and LLM integration — skills that fed directly into later projects

---

## Timeline & Context

| Year | Milestone |
|---|---|
| 2022 | Home Assistant deployed, 150+ devices integrated |
| 2024 | Wyoming + Ollama voice assistant built and integrated |
| 2026 | Hermes released — a more advanced successor voice system |

The progression from Home Assistant → custom voice assistant → Hermes reflects how the tooling evolved. Each step was only possible because of what was built before it.

---

## Related Projects

- [[ShreyAI Voice Assistant]] — standalone version of the voice assistant, running outside Home Assistant
- [[Hermes]] — the 2026 successor voice system built on more mature tooling
- [[Python Automations]] — scripting work that paralleled the automation logic built here

---
cssclasses:
  - engineering-portfolio
created: 2022-01-01
updated: 2026-05-30
status: active
---

# 🏠 Home Automation System

> *Built in 2022, the project that gave me the foundation for understanding how interconnected systems work.*

## Overview

The Home Automation System is a locally-hosted smart home platform built on Home Assistant, running on a central Raspberry Pi server. It unifies 150+ smart devices from different manufacturers into a single, private, fully automated ecosystem, with a custom voice assistant built on top.

This was one of the first major systems I built, and it became the foundation for everything that followed. The self-hosting skills learned here fed directly into the [[Project Docs/3d-printing-control|3D Printing]] setup, the [[Project Docs/voice-assistant|Voice Assistant]] subsystem, the [[Project Docs/python-automations|Python Automations]] that paralleled the automation logic, and ultimately [[Project Docs/hermes-assistant|Hermes]], the more advanced AI orchestration layer built years later.

## Problem

### Fragmented Devices, Fragmented Control

Modern smart home devices come from dozens of different manufacturers, each with their own app, their own cloud service, and their own communication protocol. To control everything, I would have needed to sign up for and maintain 100+ separate accounts, accept that each service was collecting and storing my personal data, juggle a different app for every device category, and accept no cross-device automation.

The fragmentation was not just inconvenient, it was a privacy problem. Every device was phoning home to a different company.

## Solution

### A Single Local Hub, Home Assistant on Raspberry Pi

I deployed Home Assistant on a Raspberry Pi as a central hub for every device in the house. Home Assistant is an open-source home automation platform that runs entirely on your local network, no cloud required, no data leaving the house.

The Raspberry Pi runs 24/7 as a local server on the home network. Every smart device connects to Home Assistant instead of its manufacturer cloud. Home Assistant speaks the native protocol of each device, Z-Wave, Zigbee, Matter, MQTT, and more, so no device needs to be replaced. A single dashboard gives full control over every device from one place.

Key design decisions: all data stays on the Raspberry Pi with no third-party cloud services in the loop, Home Assistant supports 3,000+ devices natively, and new devices can be added without restructuring the existing setup.

## Automation Logic

One of the most powerful features of Home Assistant is its automation engine, the ability to define rules that trigger actions based on time, device state, or sensor input. The automation logic written here directly informed the [[Project Docs/python-automations|Python Automations]] project, where I extended the same thinking into general scripting.

Examples of automations I built: lights in common areas automatically turn off at a set time each night, morning routines gradually increase light brightness to simulate a sunrise, the alarm system arms automatically when the last person leaves the house, motion sensors trigger alerts if movement is detected while the alarm is armed, and high-draw devices are scheduled to run during off-peak hours.

These automations are written in Home Assistant YAML automation syntax, defining a trigger, optional conditions, and a sequence of actions. The logic runs entirely locally.

## Voice Assistant Subsystem

### Wyoming Protocol and Ollama, A Custom Local Voice Assistant

*(2024, built after the Home Assistant core was stable)*

After the core system was running reliably, I added a custom voice assistant that integrated directly into Home Assistant. The goal was a fully local, privacy-preserving voice interface, no Alexa, no Google Assistant, no data sent to the cloud. This subsystem later became its own standalone project documented in [[Project Docs/voice-assistant|Voice Assistant]].

The Wyoming protocol is an open audio streaming protocol designed for local voice assistant pipelines. It handles wake word detection, speech-to-text, intent handling, and text-to-speech as separate services communicating over the local network.

Ollama is a local LLM runner that lets you run large language models entirely on your own hardware. I used Ollama to power the intent-handling layer. The pipeline works as follows: wake word detected, audio transcribed to text via local STT model, text passed to Ollama running a local LLM, LLM generates a response and triggers a Home Assistant action, response passed to TTS which speaks back using a custom-cloned voice.

#### Why build this in 2024 and not earlier?

In 2022, local LLMs capable of running on consumer hardware did not exist in any practical form. Ollama itself launched in 2023. This subsystem was only buildable once the underlying tools caught up, which is exactly why Home Assistant came first and the voice layer came second.

## Results

| Metric | Before | After |
|---|---|---|
| Apps needed | 10+ | 1 |
| Cloud services with data access | 10+ | 0 |
| Cross-device automation | None | Full |
| Voice control | Cloud-dependent | Fully local |
| Devices supported | Per-app | 150+ unified |

## Timeline and Context

| Year | Milestone |
|---|---|
| 2022 | Home Assistant deployed, 150+ devices integrated |
| 2024 | Wyoming + Ollama voice assistant built and integrated |
| 2026 | Hermes released, a more advanced successor voice system |

The progression from Home Assistant to custom voice assistant to Hermes reflects how the tooling evolved. Each step was only possible because of what was built before it.

## Related Projects

- [[Project Docs/voice-assistant|Voice Assistant]], standalone version of the voice assistant subsystem
- [[Project Docs/hermes-assistant|Hermes Assistant]], the 2026 successor AI orchestration system
- [[Project Docs/python-automations|Python Automations]], scripting work that paralleled the automation logic built here
- [[Project Docs/3d-printing-control|3D Printing Control]], shared Raspberry Pi self-hosting approach

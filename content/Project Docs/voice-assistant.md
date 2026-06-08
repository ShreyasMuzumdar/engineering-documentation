# 🎙️ Voice Assistant

## Overview

The Voice Assistant is a fully local, privacy-focused voice assistant that runs entirely on my own hardware without sending any data to external services. It grew out of the voice subsystem I originally built for the [[Project Docs/Home Automation System|Home Automation System]] in 2024, and was later extracted into its own standalone system that could run independently of Home Assistant.

The core goal was simple: build a voice assistant that works without Alexa, Google Assistant, or any cloud dependency. Everything, from wake word detection to speech synthesis, runs on local hardware.

## How It Works

The pipeline runs on a Mac or Raspberry Pi and connects several open-source components through the Wyoming protocol:

Wake word detection listens passively for a trigger phrase. Once detected, audio is streamed to a local speech-to-text model which transcribes it. The transcription is passed to a local LLM running via Ollama, which generates a response or triggers an action. The response is passed to a text-to-speech model and spoken back using a custom-cloned voice.

The custom voice was cloned from my own voice using a local TTS model, making the assistant feel noticeably more personal.

## Skills Applied

Building this project required integrating knowledge from multiple earlier projects. The Raspberry Pi setup skills came from [[Project Docs/3d-printing-control|3D Printing Control]]. The Home Assistant pipeline architecture came from [[Project Docs/Home Automation System|Home Automation System]]. The local LLM infrastructure knowledge later fed directly into [[Project Docs/hermes-assistant|Hermes]].

## Technical Specifications

**Hardware:**
- Mac or Raspberry Pi (local inference host)

**Software and Tools:**
- Ollama (local LLM runner)
- Wyoming Protocol (audio pipeline)
- Custom TTS voice model
- Home Assistant (optional integration)

**Skills Applied:**
- Local LLM inference
- Audio pipeline integration
- Privacy-first system design
- Embedded Linux / Raspberry Pi

## Related Projects

- [[Project Docs/Home Automation System|Home Automation System]], where the voice subsystem originated
- [[Project Docs/hermes-assistant|Hermes Assistant]], successor system that expanded on this foundation
- [[Project Docs/3d-printing-control|3D Printing Control]], shared Raspberry Pi infrastructure approach

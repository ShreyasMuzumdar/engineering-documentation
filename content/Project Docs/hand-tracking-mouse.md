# 🖐️ Hand Tracking Mouse

## Overview

The Hand Tracking Mouse is a hands-free mouse control system that uses MediaPipe to detect hand landmarks in real time and translates finger position into cursor movement. No physical mouse required.

This project and the [[Project Docs/auto-tracking-camera|Auto-Tracking Camera]] were developed around the same time and share a common foundation: using Python and computer vision to map visual input to a system output. Where the auto-tracking camera maps subject position to servo movement, this project maps hand position to cursor coordinates.

## How It Works

A webcam feed is processed in real time using MediaPipe Hands, which identifies 21 hand landmarks per frame. The position of specific landmarks, particularly the index finger tip, is mapped to screen coordinates and used to control the cursor. Gestures such as pinching are used to simulate click events.

## Skills Applied

- Hand landmark detection with MediaPipe
- Real-time image processing with OpenCV
- Cursor control via Python
- Gesture recognition

The computer vision and Python skills developed across this project and the [[Project Docs/auto-tracking-camera|Auto-Tracking Camera]] form a core part of my software toolkit, feeding into the broader [[Project Docs/python-automations|Python Automations]] work and informing the perception layer thinking in [[Project Docs/hermes-assistant|Hermes]].

## Technical Specifications

**Software and Tools:**
- Python
- MediaPipe (hand landmark detection)
- OpenCV (image processing)
- PyAutoGUI or similar (cursor control)

**Skills Applied:**
- Computer vision and gesture recognition
- Real-time hand tracking
- Python scripting and automation

## Related Projects

- [[Project Docs/auto-tracking-camera|Auto-Tracking Camera]], parallel project using the same OpenCV and vision skill set
- [[Project Docs/python-automations|Python Automations]], shared Python scripting foundation

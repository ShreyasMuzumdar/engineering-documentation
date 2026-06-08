# 📷 Auto-Tracking Camera

## Overview

The Auto-Tracking Camera is a computer vision system that autonomously follows a moving subject in real time. A servo-mounted camera detects and tracks a target using OpenCV, adjusting its position continuously to keep the subject centered in frame.

This project and the [[Project Docs/hand-tracking-mouse|Hand Tracking Mouse]] were built around the same time and share a core skill set: using Python and computer vision libraries to translate visual input into physical output. Where the hand tracking mouse maps hand position to cursor movement, this project maps subject position to servo actuation.

## How It Works

A camera feed is processed frame-by-frame using OpenCV. A detection algorithm identifies the target, calculates its offset from the center of the frame, and sends correction signals to pan and tilt servos to reposition the camera. The loop runs continuously, keeping the subject centered as it moves.

## Skills Applied

- Computer vision with OpenCV
- Real-time image processing
- Servo control and actuation
- Python scripting

The Python scripting patterns used here connect directly to the [[Project Docs/python-automations|Python Automations]] project and the broader automation mindset developed across projects like [[Project Docs/Home Automation System|Home Automation System]] and [[Project Docs/hermes-assistant|Hermes]].

## Technical Specifications

**Software and Tools:**
- Python
- OpenCV (computer vision)
- Servo control library

**Skills Applied:**
- Computer vision and object detection
- Real-time control loops
- Python scripting and automation

## Related Projects

- [[Project Docs/hand-tracking-mouse|Hand Tracking Mouse]], built with the same OpenCV and MediaPipe skill set
- [[Project Docs/python-automations|Python Automations]], shared Python scripting foundation
- [[Project Docs/hermes-assistant|Hermes Assistant]], broader automation and control system

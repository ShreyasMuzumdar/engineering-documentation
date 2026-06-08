---
title: Hermes AI Assistant
---

# 🛰️ Hermes AI Assistant

## 🎯 Define the Problem

### Background and Motivation

As smart home ecosystems become increasingly fragmented, there is a growing need for a centralized, intelligent orchestration layer. Existing solutions often lock users into proprietary clouds or require significant manual configuration. Hermes was conceived to bridge this gap using modern LLM capabilities and self-hosted infrastructure.

Hermes is the direct successor to two earlier projects. The [[Project Docs/Home Automation System|Home Automation System]] established the local-first smart home foundation. The [[Project Docs/voice-assistant|Voice Assistant]] proved that local LLM inference was viable on consumer hardware. Hermes took both and pushed further, adding autonomous execution, infrastructure monitoring, and automated reporting.

### Problem Statement

Develop a low-latency, privacy-focused assistant capable of processing natural language intents to control heterogeneous IoT devices while maintaining high availability and providing proactive system health updates.

### Project Requirements

| Category | Requirement |
| :--- | :--- |
| **Functional** | Voice/Text intent recognition, Home Assistant integration, Weekly automated newsletters. |
| **Performance** | Less than 2s end-to-end latency for local triggers; 99% uptime for core monitoring. |
| **Security** | End-to-end encryption via Tailscale; Local-first processing for sensitive data. |
| **Constraints** | Must run on consumer hardware (Raspberry Pi/Mini PC); Minimal API costs. |

## 🔍 Research and Brainstorming

### Hermes as the Foundation

Derived from the concept of a "Universal Gripper" for data, Hermes acts as the middleware between raw sensor data (Netdata/Home Assistant) and high-level reasoning engines (Ollama/Gemini).

### Model Landscape Research

| Model | Host | Pros | Cons |
| :--- | :--- | :--- | :--- |
| **Llama 3 (8B)** | Local | Privacy, No Latency/Cost | Hardware Intensive |
| **Gemini 1.5 Flash** | Cloud | Massive Context, Multimodal | Internet Dependent |
| **GPT-4o mini** | Cloud | Highly Reliable | API Usage Costs |

### Infrastructure Stack

- **Netdata:** Real-time health monitoring of the cluster node.
- **Cloudflare:** Secure tunneling and DNS management.
- **Resend:** Transactional email service for automated newsletters.
- **Ollama:** Local inference engine for privacy-focused tasks.
- **Tailscale:** Mesh VPN for secure cross-device communication.

The Cloudflare tunneling approach is the same concept used in the [[Project Docs/3d-printing-control|3D Printing]] remote access setup, just applied at a larger infrastructure scale.

## 🛠️ Design and Prototyping

### Solution Brainstorming

- **Idea A: Fully Cloud (Gemini API):** Zero local compute needed, highest intelligence, easy scaling. Limitations include high latency for simple tasks and privacy concerns with home data.
- **Idea B: Fully Local (Ollama on RPi):** 100% private, works offline, zero variable cost. Limitations include Raspberry Pi struggling with models larger than 8B parameters.
- **Idea C: Hybrid Orchestration:** Best of both worlds. Local processing for quick home control, cloud for complex reasoning and summarization. Increased architectural complexity.

### Selection and Decision Matrix

| Criteria (Weight) | Cloud | Local | Hybrid |
| :--- | :--- | :--- | :--- |
| Latency (30%) | 7/10 | 9/10 | 9/10 |
| Intelligence (30%) | 10/10 | 6/10 | 10/10 |
| Privacy (40%) | 4/10 | 10/10 | 8/10 |
| **Weighted Score** | **6.7** | **8.5** | **8.9** |

**Selected Approach:** The Hybrid model was selected for its superior balance of privacy and power. Key components are containerized for portability across the home lab.

### Iteration Roadmap

- **v1.0 Basic Relay:** Simple Python script connecting Netdata spikes to Discord alerts. Issue: High noise floor, too many alerts. The scripting patterns here built on [[Project Docs/python-automations|Python Automations]].
- **v2.0 Logic Layer:** Introduced Home Assistant integration and local Ollama intent filtering. Issue: RPi 4 hardware limitations for concurrent LLM and Home Assistant.
- **v3.0 The Assistant:** Migrated to N100 Mini PC, added Gemini for newsletter synthesis.

### Final System Architecture

| Layer | Technology | Function |
| :--- | :--- | :--- |
| **Ingress** | Cloudflare Tunnel | Secure Exposure |
| **Compute** | Docker / Proxmox | Isolated services |
| **Orchestra** | Node-RED / Python | Event Routing |

### Implementation: Newsletter Pipeline

```python
# Pseudocode for the Newsletter Generation
data = fetch_netdata_stats(timeframe="7d")
security_logs = tailscale.get_logs()
summary = gemini.generate(
    prompt="Summarize this server health and security log for the week...",
    input=data + security_logs
)
resend.send_email(to="admin@home.local", content=summary)
```

### Key Challenges Solved

- **Context Window Management:** Implementing a rolling buffer for logs to avoid hitting Gemini token limits during peak activity.
- **Cold Start Latency:** Keeping the Ollama model warm in memory for instant local responses.

## 🧪 Testing and Evaluation

### Testing Checklist

- [x] **Power failure recovery:** All services auto-start via Docker Compose.
- [x] **Security:** External port scan shows 0 open ports (Cloudflare Tunnel success).
- [x] **Latency:** Average response for "Turn on lights" is 450ms.

### Performance Observations

| Metric | Target | Actual |
| :--- | :--- | :--- |
| Inference Time (Local) | Less than 1s | 850ms |
| Email Delivery | Less than 5s | 1.2s |

## 🔄 Iterate and Improve

### Lessons Learned

The biggest takeaway was the importance of data sanitization before sending it to an LLM. Raw Netdata logs are too verbose; pre-processing them into a "status delta" significantly improved summary quality.

### Future Roadmap

- **Short Term:** Integrate solar energy monitoring (Enphase API).
- **Medium Term:** Implement "Local-RAG" for home documentation (manuals/PDFs).
- **Long Term:** Voice-active spatial awareness using ESP32-S3-BOX.

## 🤖 Hermes, Autonomous AI Agent

Hermes serves as the autonomous AI agent powering the orchestration and ongoing development of this system. The documentation system itself was built using Claude MCP connected to Obsidian, documented in the [[Project Docs/setup-journey|Setup Journey]].

### Why Hermes?

Unlike standard LLM interfaces, Hermes provides a direct, autonomous bridge to my local environment. The primary benefits include autonomous execution of terminal commands, file management, and deployment updates, tool-integrated research via real-time web browsing, and persistent context through a durable memory system.

### Configuration

Hermes is configured as a high-level engineering assistant with access to a Linux terminal for Docker and Proxmox management, a browser for research, and a filesystem interface for direct documentation and code edits.

## 🛠️ Technical Specifications

**Tools and Technologies Used:**
- **Programming:** Python (CV, ML and AI), Web Development, Java, IoT Protocols
- **Infrastructure:** Docker, Proxmox, Cloudflare Tunnel, Tailscale
- **LLMs:** Ollama (Local), Gemini (Cloud)
- **Hardware:** N100 Mini PC, Raspberry Pi

## Related Projects

- [[Project Docs/Home Automation System|Home Automation System]], the predecessor smart home system Hermes builds on
- [[Project Docs/voice-assistant|Voice Assistant]], the local LLM voice pipeline that informed Hermes design
- [[Project Docs/python-automations|Python Automations]], scripting patterns that fed into the v1.0 relay
- [[Project Docs/setup-journey|Setup Journey]], how this documentation system was built using Claude MCP

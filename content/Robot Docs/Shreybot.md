# 🤖 Shreybot

**Season:** Freight Frenzy | **Achievement:** State Finalist | **Category:** Engineering

## Overview

Shreybot was my first robot with Pioneer Robotics during the Freight Frenzy season. This case study documents the mechanical design decisions, engineering tradeoffs, and lessons learned while building a robot to compete in FTC's rapid-freight logistics challenge.

**Challenge:** Design a robot to collect cubic and spherical freight from a warehouse and deposit them on alliance-specific shipping hubs at multiple heights, all within severe weight and space constraints.

## Tines Collection System

**Problem:** We needed a mechanism that could reliably pick up both cubic and spherical freight from the ground with minimal energy and jamming risk.

**Design Decision:** I prototyped tines with different materials in parallel: plastic tubing (rigid, precise) and 3D-printed flexible tines. Rather than choosing one, I designed a hybrid system that uses both materials in different configurations depending on which type of freight we're targeting.

**Result:** The hybrid tines system achieved consistent pickup rates across all freight types during competition, eliminating mechanical failures during match play.

![Shreybot tines collection system prototype with freight](/static/images/robot-photos/shreybot/IMG_3267.jpeg)

## Long Robotics Slides Vertical Stack

**Problem:** We needed to deposit freight at multiple heights. Misumi linear slides were prohibitively expensive and too heavy for our drive base load budget.

**Design Decision:** I chose a two-stage Long Robotics slide system , these slides extend to roughly 50% of their fully compressed length, cutting our footprint in half versus single-stage alternatives. They're significantly cheaper than Misumi and lighter.

**Result:** The Long Robotics solution proved reliable throughout the season with no wear-related failures. The cost savings let us allocate budget to other critical systems like intake redundancy.

![Shreybot Long Robotics slides mounted on robot](/static/images/robot-photos/shreybot/IMG_3280.jpeg)

## System Integration

The collection system and linear stack required tight integration to handle freight handoff smoothly. The intake tilts freight into the collection tines, then the slides extend to position it precisely for deposit. This sequential motion reduced jamming compared to simultaneous actuation, though it added roughly 1 second per cycle.

![Shreybot full robot , competition ready](/static/images/robot-photos/shreybot/IMG_3405.jpeg)

## Key Takeaways

1. **Prototype Early, Prototype Often** , The hybrid tines approach emerged only after building and testing both material options in parallel.
2. **Understand Your Tradeoffs** , Every design choice was a deliberate tradeoff. Being explicit about these tradeoffs made it easier to defend design decisions to teammates and coaches.
3. **Prioritize Reliability Over Speed** , In competition, a robot that works 100% of the time beats one that's fast but unreliable.
4. **Budget Constraints Are Features** , The cost and weight limits forced creative solutions that ended up being more elegant than best-of-breed alternatives. Constraints breed innovation.

## Related Robots
- [[Robot Docs/StretchBot|StretchBot]]
- [[Robot Docs/MantisBot|MantisBot]]
- [[Robot Docs/BlackBox|BlackBox]]

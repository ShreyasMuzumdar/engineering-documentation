# 🔩 Auger Subsystem

**Team:** Watney MKVII | **Competition:** URC / CIRC | **Category:** Rover Subsystem

## Overview

The Auger is a subsystem on the Watney MKVII rover designed to collect sand samples from the surface for life detection analysis, simulating the sample-collection conditions that would be encountered on a Mars mission.

![Auger final assembly mounted on the rover arm](/static/images/robot-photos/auger/Auger-final.png)

## Design Iteration 1: Straight Tube vs. Ice Auger

Two candidate designs were considered for the collection mechanism:

1. **Straight tube** — a simple hollow tube driven into the sand to collect a sample.
2. **Ice auger** — a helical drill bit (of the type normally used for drilling into ice) used to bore into and collect sand.

### Why the ice auger was attractive
- Despite being smaller in diameter than the tube, its helical drill geometry let it dig deeper into the sand column, whereas the straight tube struggled to penetrate to the same depth.
- It also demonstrated higher accuracy in sample placement/collection during testing.

### Why the ice auger was ultimately not used
- Because it was originally designed for ice (not sand), its flighting/sizing was too small in cross-section, which limited the *volume* of sand it could carry per pass.
- In practice: test footage showed the ice auger boring into a sand sample cleanly, with no mechanical issues digging in. However, when the collected sample was measured, the yield was far below the target amount needed for the life-detection tests.

### Decision
The team reverted to the straight tube design, which — despite the depth/accuracy tradeoffs — reliably collected an adequate volume of sand once implemented.

> **Design note:** the transition between the two concepts was intentionally kept low-friction — the initial mount was designed so switching from the ice auger back to the tube design would not require a major rebuild.

## Drive/Power Considerations

The shaft interface was originally driven by a **hexagonal-shaped shaft**, chosen specifically because it mated well with the hexagonal socket geometry of the ice auger bit.

*(Follow-up needed: document how the drive interface changed, if at all, once the design moved to the straight tube.)*

## Mount Redesign

The mount was changed from a single-piece to a **two-piece modular design**.

**Benefit:** the motor that lowers/raises the auger can now fully detach from the rest of the assembly, making minor system adjustments and maintenance significantly easier.

*(Expand later with more detail on the mount redesign.)*

## Media
- `Auger-final.png` — final assembly on rover
- `augervideo.mp4`, `ld auger 1.mov`, `IMG_8001–8006.mov` — test/deployment footage
- `IMG_7949, 7950, 7951, 7975, 7976, 7987, 8021` — supporting build photos

*Documentation to be expanded further — testing results (sand yield data) and final drive-shaft details pending.*

## Related Robots
- [[Robot Docs/robot-docs|Robot Docs]]
- [[Robot Docs/Watney MKVII|Watney MKVII]]

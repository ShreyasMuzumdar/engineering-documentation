# 🪐 Watney MKVII

**Team:** Northeastern University Rover Team | **Competitions:** URC / CIRC | **Category:** Mars-Analog Rover

## Overview

Watney MKVII is Northeastern's Mars-analog rover, built to compete in the University Rover Challenge (URC) and the Canadian International Rover Challenge (CIRC). These competitions push teams to build rovers capable of autonomous navigation, sample collection, and life detection tasks under Mars-mission-like conditions.

*(Expand later: team structure, mission tasks, overall rover architecture.)*

## Swerve Drive

The one major drivetrain change on this iteration of the rover was a switch to a **swerve drive**.

**Advantage:** the primary benefit of a swerve drive is omnidirectional mobility — the rover can move in any direction (forward, backward, sideways, diagonally) while independently maintaining or rotating to any facing orientation.

**Issue encountered:** the stiffness of the wheels was too low, which caused traction problems. The wheels would get "stuck" when turning and trying to move at the same time.

*(To add later: how the traction issue was diagnosed/fixed, final wheel spec changes.)*

## CIRC

*(To add: explanation of what happened at CIRC.)*

## Subsystems
## Auger

The Auger is a subsystem on the Watney MKVII rover designed to collect sand samples from the surface for life detection analysis, simulating the sample-collection conditions that would be encountered on a Mars mission.

![Auger final assembly mounted on the rover arm](/static/images/robot-photos/auger/Auger-final.png)

### Design Iteration 1: Straight Tube vs. Ice Auger

Two candidate designs were considered for the collection mechanism:

1. **Straight tube** — a simple hollow tube driven into the sand to collect a sample.
2. **Ice auger** — a helical drill bit (of the type normally used for drilling into ice) used to bore into and collect sand.

#### Why the ice auger was attractive
- Despite being smaller in diameter than the tube, its helical drill geometry let it dig deeper into the sand column, whereas the straight tube struggled to penetrate to the same depth.
- It also demonstrated higher accuracy in sample placement/collection during testing.

#### Why the ice auger was ultimately not used
- Because it was originally designed for ice (not sand), its flighting/sizing was too small in cross-section, which limited the *volume* of sand it could carry per pass.
- In practice: test footage showed the ice auger boring into a sand sample cleanly, with no mechanical issues digging in. However, when the collected sample was measured, the yield was far below the target amount needed for the life-detection tests.

#### Decision
The team reverted to the straight tube design, which — despite the depth/accuracy tradeoffs — reliably collected an adequate volume of sand once implemented.

> **Design note:** the transition between the two concepts was intentionally kept low-friction — the initial mount was designed so switching from the ice auger back to the tube design would not require a major rebuild.

### Drive/Power Considerations

The shaft interface was originally driven by a **hexagonal-shaped shaft**, chosen specifically because it mated well with the hexagonal socket geometry of the ice auger bit.

*(Follow-up needed: document how the drive interface changed, if at all, once the design moved to the straight tube.)*

### Mount Redesign

The mount was changed from a single-piece to a **two-piece modular design**.

**Benefit:** the motor that lowers/raises the auger can now fully detach from the rest of the assembly, making minor system adjustments and maintenance significantly easier.

*(Expand later with more detail on the mount redesign.)*

### Media
**Design comparison videos:**

Ice auger (initial design):
<video controls width="600" src="/static/images/robot-photos/auger/augervideo2.mp4"></video>

Straight tube (final design):
<video controls width="600" src="/static/images/robot-photos/auger/augervideo1.mp4"></video>

**Build/test photos:**

![Initial auger with 3D-printed motor-to-ice-auger coupler, which broke](/static/images/robot-photos/auger/auger-one.jpeg)
*Initial auger — 3D-printed coupler between the motor and the ice auger, which broke under use.*

![Ice auger with aluminum coupler](/static/images/robot-photos/auger/auger-two.jpeg)
*Ice auger fitted with an aluminum coupler after the 3D-printed one failed.*

![Ice auger mounted on the rover](/static/images/robot-photos/auger/auger-three.jpeg)
*Ice auger setup mounted on the rover.*

*Documentation to be expanded further — testing results (sand yield data) and final drive-shaft details pending.*

## Subsystems
*(Additional subsystems to be added here.)*

## Related Robots
- [[Robot Docs/robot-docs|Robot Docs]]

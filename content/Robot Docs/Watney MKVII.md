# 🪐 Watney MKVII

**Team:** Northeastern University Rover Team | **Competitions:** URC / CIRC | **Category:** Mars-Analog Rover

## Overview

Watney MKVII is Northeastern's Mars-analog rover, built to compete in the University Rover Challenge (URC) and the Canadian International Rover Challenge (CIRC). These competitions push teams to build rovers capable of autonomous navigation, sample collection, and life detection tasks under Mars-mission-like conditions.

*(Expand later: team structure, mission tasks, overall rover architecture.)*

## My Contributions

### Auger

The Auger is a subsystem on the Watney MKVII rover designed to collect sand samples from the surface for life detection analysis, simulating the sample-collection conditions that would be encountered on a Mars mission.

![Auger final assembly mounted on the rover arm](/static/images/robot-photos/auger/Auger-final.png)

#### Initial Coupler Prototype

One of the first steps in designing the auger was figuring out how to couple the drive motor to the auger bit itself.

The first attempt used a **3D-printed coupler**. It was not able to tension properly under load, so it broke.

![Initial 3D-printed motor-to-auger coupler, which broke](/static/images/robot-photos/auger/auger-one.jpeg)
*Initial 3D-printed coupler — could not hold tension and failed.*

After that failure, an **aluminum coupler** was ordered and used instead, which held up properly.

![Aluminum motor-to-auger coupler](/static/images/robot-photos/auger/auger-two.jpeg)
*Aluminum coupler that replaced the failed 3D-printed part.*

#### Design Iteration: Straight Tube vs. Ice Auger

Two candidate designs were considered for the collection mechanism:

1. **Straight tube** — a simple hollow tube driven into the sand to collect a sample.
2. **Ice auger** — a helical drill bit (of the type normally used for drilling into ice) used to bore into and collect sand.

![Ice auger setup mounted on the rover](/static/images/robot-photos/auger/auger-three.jpeg)
*Ice auger setup mounted on the rover during testing.*

##### Why the ice auger was attractive
- Despite being smaller in diameter than the tube, its helical drill geometry let it dig deeper into the sand column, whereas the straight tube struggled to penetrate to the same depth.
- It also demonstrated higher accuracy in sample placement/collection during testing.

Test footage of the ice auger digging into a sand sample:
<video controls style="width: 100%; max-width: 600px; height: auto;" src="/static/images/robot-photos/auger/augervideo2.mp4"></video>

##### Why the ice auger was ultimately not used
- Because it was originally designed for ice (not sand), its flighting/sizing was too small in cross-section, which limited the *volume* of sand it could carry per pass.
- In practice: the video above shows the ice auger boring into a sand sample cleanly, with no mechanical issues digging in. However, when the collected sample was measured, the yield was far below the target amount needed for the life-detection tests.

##### Decision
The team reverted to the straight tube design, which — despite the depth/accuracy tradeoffs — reliably collected an adequate volume of sand once implemented.

Straight tube (final design) in testing:
<video controls style="width: 100%; max-width: 600px; height: auto;" src="/static/images/robot-photos/auger/augervideo1.mp4"></video>

> **Design note:** the transition between the two concepts was intentionally kept low-friction — the initial mount was designed so switching from the ice auger back to the tube design would not require a major rebuild.

#### Drive/Power Considerations

The shaft interface was originally driven by a **hexagonal-shaped shaft**, chosen specifically because it mated well with the hexagonal socket geometry of the ice auger bit.

*(Follow-up needed: document how the drive interface changed, if at all, once the design moved to the straight tube.)*

#### Mount Redesign

The mount was changed from a single-piece to a **two-piece modular design**.

**Benefit:** the motor that lowers/raises the auger can now fully detach from the rest of the assembly, making minor system adjustments and maintenance significantly easier.

*(Expand later with more detail on the mount redesign.)*

*Documentation to be expanded further — testing results (sand yield data) and final drive-shaft details pending.*

### CIRC
I was team strategist for our runs at CIRC (Canadian International Rover Challenge) — deciding what to attempt, what to skip, and how to spend our set-up and run time on each mission.

#### Heist Mission

The Heist Mission scores points for evading a camera/tripwire system, disabling the cameras by cutting the correct wire, then decoding a security console and opening a vault by Morse code. Every stealth step scores on its own, but none of it matters if you never actually get the artifact out.

Our read going in: reaching the vault and getting the artifact out was worth far more, in points and in outcome, than doing the stealth portion cleanly — and the tripwire/camera avoidance and the wire-disable panel were also the hardest parts of the course to execute reliably. So we walked straight past the cameras and the wire panel and put all our effort into nailing the vault sequence.

That trade cost us 28 points outright — the full camera-avoidance points and the entire wire-disable stage. In exchange, we were one of only three teams at the competition to actually open the vault and retrieve the artifact.

| Stage | Max Points | Points Earned | Notes |
|---|---|---|---|
| Approach Camera Controls | 24 | 8 | Skipped tripwire/camera/light avoidance (16 pts) — walked straight to the controls |
| Disable Cameras | 12 | 0 | Skipped entirely — never cut a wire |
| Identify Vault Code | 27 | 27 | Full points — console decode and code retrieval went clean |
| Open Vault | 37 | 31 | Full points except the speed bonus for entering the code fast enough |
| **Total** | **100** | **66** | |

Wire-cutting vs. the vault sequence, side by side — this is the actual trade we made:

<svg viewBox="0 0 500 330" xmlns="http://www.w3.org/2000/svg" style="width:100%; max-width:500px; height:auto;">
  <rect x="150" y="10" width="14" height="14" fill="#c9c9c9"/>
  <text x="170" y="21" font-size="12" fill="#333">Max Points</text>
  <rect x="290" y="10" width="14" height="14" fill="#2f6690"/>
  <text x="310" y="21" font-size="12" fill="#333">Points Earned</text>

  <line x1="30" y1="260" x2="470" y2="260" stroke="#999" stroke-width="1"/>

  <rect x="80" y="194" width="60" height="66" fill="#c9c9c9"/>
  <text x="110" y="187" font-size="12" text-anchor="middle" fill="#333">12</text>
  <text x="190" y="253" font-size="12" text-anchor="middle" fill="#333">0</text>
  <text x="150" y="280" font-size="12" text-anchor="middle" fill="#333">Disable Cameras</text>
  <text x="150" y="294" font-size="11" text-anchor="middle" fill="#666">(cut the wire)</text>

  <rect x="280" y="56" width="60" height="204" fill="#c9c9c9"/>
  <text x="310" y="49" font-size="12" text-anchor="middle" fill="#333">37</text>
  <rect x="360" y="89" width="60" height="171" fill="#2f6690"/>
  <text x="390" y="82" font-size="12" text-anchor="middle" fill="#333">31</text>
  <text x="350" y="280" font-size="12" text-anchor="middle" fill="#333">Open Vault</text>
  <text x="350" y="294" font-size="11" text-anchor="middle" fill="#666">(vault sequence)</text>
</svg>

*Cutting the wire was worth up to 12 points; we scored 0. The vault sequence was worth up to 37 and we scored 31 — nearly the entire wire-disable stage's max value, just from the one decision to skip it and focus there instead.*

Here's how the 66 points we did earn broke down by stage:

<svg viewBox="0 0 320 400" xmlns="http://www.w3.org/2000/svg" style="width:100%; max-width:320px; height:auto;">
  <path d="M150,150 L150,30 A120,120 0 0,1 233,63 Z" fill="#4c9a8c"/>
  <path d="M150,150 L233,63 A120,120 0 0,1 127,268 Z" fill="#2f6690"/>
  <path d="M150,150 L127,268 A120,120 0 0,1 150,30 Z" fill="#e08a2c"/>
  <text x="178" y="80" font-size="13" fill="#fff" text-anchor="middle">12%</text>
  <text x="217" y="184" font-size="13" fill="#fff" text-anchor="middle">41%</text>
  <text x="75" y="143" font-size="13" fill="#fff" text-anchor="middle">47%</text>

  <rect x="10" y="300" width="14" height="14" fill="#4c9a8c"/>
  <text x="28" y="311" font-size="12" fill="#333">Approach Camera Controls — 8 pts (12%)</text>
  <rect x="10" y="322" width="14" height="14" fill="#c9c9c9"/>
  <text x="28" y="333" font-size="12" fill="#333">Disable Cameras — 0 pts (0%)</text>
  <rect x="10" y="344" width="14" height="14" fill="#2f6690"/>
  <text x="28" y="355" font-size="12" fill="#333">Identify Vault Code — 27 pts (41%)</text>
  <rect x="10" y="366" width="14" height="14" fill="#e08a2c"/>
  <text x="28" y="377" font-size="12" fill="#333">Open Vault — 31 pts (47%)</text>
</svg>

*Nearly 90% of our points came from the two stages we actually attempted — the vault sequence alone accounted for almost half of everything we scored.*

<details>
<summary>Full official rubric — Heist Mission</summary>

Rover mass: 49.9kg, no mass bonus (100%). Repair/modification penalties were 0 throughout, so Points Earned = Modified Points here.

| Stage | Action | Max | Earned |
|---|---|---|---|
| Approach Camera Controls | Avoid tripwires | 4 | 0 |
| | Avoid camera | 4 | 0 |
| | Avoid shining light on area viewed by camera | 8 | 0 |
| | Reach camera controls | 8 | 8 |
| Disable Cameras | Identify correct wire to cut | 3 | 0 |
| | Cut a wire | 6 | 0 |
| | Cut the correct wire | 3 | 0 |
| Identify Vault Code | Approach security console | 5 | 5 |
| | Attempt to decode security console password | 6 | 6 |
| | Correctly decode security console password | 4 | 4 |
| | Physically interface with security console | 6 | 6 |
| | Correctly find vault code | 6 | 6 |
| Open Vault | Approach Morse key | 4 | 4 |
| | Interact with Morse key | 6 | 6 |
| | Enter the vault code | 6 | 6 |
| | Enter the vault code fast enough | 6 | 0 |
| | Open the vault door | 5 | 5 |
| | Remove the artifact from the vault | 5 | 5 |
| | Return to the extraction point with the artifact | 5 | 5 |
| **Total** | | **100** | **66** |

</details>

#### RoverCooked

For RoverCooked, the strategist's job was juggling incoming orders — each with its own countdown timer, ingredients, and prep steps — while the rover worked through the queue.

Near the end of our run, two pancake orders came in and our rover didn't have the dexterity to actually flip and plate one. Rather than let both go untouched, I sent the first pancake order through anyway just to pick up the ingredient-touch point before moving on. It mattered more than it seemed at the time — that 1.04-point touch (after our rover's 104% mass bonus) turned out to be the exact margin we needed to win the RoverCooked award.

| Order | Item | Points Earned |
|---|---|---|
| 1 | Apple | 11.44 |
| 2 | Pancakes | 1.04 |
| 3 | Sub | 18.72 |
| 4 | Spaghetti | 2.08 |
| 5 | Apple | 10.4 |
| 6 | Pizza | 2.08 |
| 7 | Sub | 15.6 |
| 8 | Pancakes | 1.04 |
| **Total** | | **62.4** |

Share of the total 62.4 points earned, by order (same-item orders share a color — you can see how much both Subs carried the run, and how little the two pancake attempts contributed):

<svg viewBox="0 0 340 400" xmlns="http://www.w3.org/2000/svg" style="width:100%; max-width:340px; height:auto;">
  <path d="M150,150 L150,30 A120,120 0 0,1 260,101 Z" fill="#4c9a8c"/>
  <path d="M150,150 L260,101 A120,120 0 0,1 264,113 Z" fill="#e08a2c"/>
  <path d="M150,150 L264,113 A120,120 0 0,1 150,270 Z" fill="#2f6690"/>
  <path d="M150,150 L150,270 A120,120 0 0,1 125,267 Z" fill="#8a6bbf"/>
  <path d="M150,150 L125,267 A120,120 0 0,1 36,187 Z" fill="#4c9a8c"/>
  <path d="M150,150 L36,187 A120,120 0 0,1 31,163 Z" fill="#c94f4f"/>
  <path d="M150,150 L31,163 A120,120 0 0,1 137,31 Z" fill="#2f6690"/>
  <path d="M150,150 L137,31 A120,120 0 0,1 150,30 Z" fill="#e08a2c"/>

  <rect x="10" y="294" width="14" height="14" fill="#4c9a8c"/>
  <text x="28" y="305" font-size="11" fill="#333">1: Apple — 11.44 (18%)</text>
  <rect x="10" y="316" width="14" height="14" fill="#e08a2c"/>
  <text x="28" y="327" font-size="11" fill="#333">2: Pancakes — 1.04 (2%)</text>
  <rect x="10" y="338" width="14" height="14" fill="#2f6690"/>
  <text x="28" y="349" font-size="11" fill="#333">3: Sub — 18.72 (30%)</text>
  <rect x="10" y="360" width="14" height="14" fill="#8a6bbf"/>
  <text x="28" y="371" font-size="11" fill="#333">4: Spaghetti — 2.08 (3%)</text>

  <rect x="175" y="294" width="14" height="14" fill="#4c9a8c"/>
  <text x="193" y="305" font-size="11" fill="#333">5: Apple — 10.40 (17%)</text>
  <rect x="175" y="316" width="14" height="14" fill="#c94f4f"/>
  <text x="193" y="327" font-size="11" fill="#333">6: Pizza — 2.08 (3%)</text>
  <rect x="175" y="338" width="14" height="14" fill="#2f6690"/>
  <text x="193" y="349" font-size="11" fill="#333">7: Sub — 15.60 (25%)</text>
  <rect x="175" y="360" width="14" height="14" fill="#e08a2c"/>
  <text x="193" y="371" font-size="11" fill="#333">8: Pancakes — 1.04 (2%)</text>
</svg>

*The two Sub orders alone made up 55% of our total score. Both pancake orders together only made up 4% — but as it turned out, that 4% was the margin between winning the award and not.*

<details>
<summary>Full official rubric — RoverCooked</summary>

Rover mass: 46kg, 104% mass bonus (why "1 point earned" shows up as 1.04 modified). Repair/modification penalties were 0 throughout.

| Order | Action | Max | Earned | Modified |
|---|---|---|---|---|
| 1: Apple | Rover leaves start line | 1 | 1 | 1.04 |
| | Ingredient 1 touched | 1 | 1 | 1.04 |
| | Ingredient 1 prepared correctly | 3 | 3 | 3.12 |
| | Delivered without dropping any ingredient | 5 | 5 | 5.2 |
| | Delivered late | -2 | 0 | 0 |
| | Delivered early | 1 | 1 | 1.04 |
| 2: Pancakes | Ingredient 1 touched | 1 | 1 | 1.04 |
| | Ingredient 1 prepared correctly | 3 | 0 | 0 |
| | Delivered without dropping any ingredient | 5 | 0 | 0 |
| | Delivered late | -2 | 0 | 0 |
| | Delivered early | 1 | 0 | 0 |
| 3: Sub | Ingredient 1 touched | 1 | 1 | 1.04 |
| | Ingredient 1 prepared correctly | 3 | 3 | 3.12 |
| | Ingredient 2 touched | 1 | 1 | 1.04 |
| | Ingredient 2 prepared correctly | 3 | 3 | 3.12 |
| | Ingredient 3 touched | 1 | 1 | 1.04 |
| | Ingredient 3 prepared correctly | 3 | 3 | 3.12 |
| | Delivered without dropping any ingredient | 5 | 5 | 5.2 |
| | Delivered late | -2 | 0 | 0 |
| | Delivered early | 1 | 1 | 1.04 |
| 4: Spaghetti | Ingredient 1 touched | 1 | 1 | 1.04 |
| | Ingredient 1 prepared correctly | 3 | 0 | 0 |
| | Ingredient 2 touched | 1 | 1 | 1.04 |
| | Ingredient 2 prepared correctly | 3 | 0 | 0 |
| | Ingredient 3 touched | 1 | 0 | 0 |
| | Ingredient 3 prepared correctly | 3 | 0 | 0 |
| | Delivered without dropping any ingredient | 5 | 0 | 0 |
| | Delivered late | -2 | 0 | 0 |
| | Delivered early | 1 | 0 | 0 |
| 5: Apple | Ingredient 1 touched | 1 | 1 | 1.04 |
| | Ingredient 1 prepared correctly | 3 | 3 | 3.12 |
| | Delivered without dropping any ingredient | 5 | 5 | 5.2 |
| | Delivered late | -2 | 0 | 0 |
| | Delivered early | 1 | 1 | 1.04 |
| 6: Pizza | Ingredient 1 touched | 1 | 1 | 1.04 |
| | Ingredient 1 prepared correctly | 3 | 0 | 0 |
| | Ingredient 2 touched | 1 | 1 | 1.04 |
| | Ingredient 2 prepared correctly | 3 | 0 | 0 |
| | Ingredient 3 touched | 1 | 0 | 0 |
| | Ingredient 3 prepared correctly | 3 | 0 | 0 |
| | Delivered without dropping any ingredient | 5 | 0 | 0 |
| | Delivered late | -2 | 0 | 0 |
| | Delivered early | 1 | 0 | 0 |
| 7: Sub | Ingredient 1 touched | 1 | 1 | 1.04 |
| | Ingredient 1 prepared correctly | 3 | 3 | 3.12 |
| | Ingredient 2 touched | 1 | 1 | 1.04 |
| | Ingredient 2 prepared correctly | 3 | 3 | 3.12 |
| | Ingredient 3 touched | 1 | 1 | 1.04 |
| | Ingredient 3 prepared correctly | 3 | 3 | 3.12 |
| | Delivered without dropping any ingredient | 5 | 5 | 5.2 |
| | Delivered late | -2 | -2 | -2.08 |
| | Delivered early | 1 | 0 | 0 |
| 8: Pancakes | Ingredient 1 touched | 1 | 1 | 1.04 |
| | Ingredient 1 prepared correctly | 3 | 0 | 0 |
| | Delivered without dropping any ingredient | 5 | 0 | 0 |
| | Delivered late | -2 | 0 | 0 |
| | Delivered early | 1 | 0 | 0 |
| **Total** | | **97** | **60** | **62.4** |

</details>

## Subsystems

### Swerve Drive

The one major drivetrain change on this iteration of the rover was a switch to a **swerve drive**.

**Advantage:** the primary benefit of a swerve drive is omnidirectional mobility — the rover can move in any direction (forward, backward, sideways, diagonally) while independently maintaining or rotating to any facing orientation.

**Issue encountered:** the stiffness of the wheels was too low, which caused traction problems. The wheels would get "stuck" when turning and trying to move at the same time.

*(To add later: how the traction issue was diagnosed/fixed, final wheel spec changes.)*

*(Additional subsystems to be added here.)*

## Related Robots
- [[Robot Docs/robot-docs|Robot Docs]]

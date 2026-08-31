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

<svg viewBox="0 0 500 180" xmlns="http://www.w3.org/2000/svg" style="width:100%; max-width:500px; height:auto;">
  <rect x="150" y="4" width="14" height="14" fill="#c9c9c9"/>
  <text x="170" y="15" font-size="12" fill="#333">Max Points</text>
  <rect x="290" y="4" width="14" height="14" fill="#2f6690"/>
  <text x="310" y="15" font-size="12" fill="#333">Points Earned</text>

  <line x1="140" y1="30" x2="140" y2="165" stroke="#999" stroke-width="1"/>

  <text x="140" y="38" font-size="12" fill="#333">Disable Cameras (cut the wire)</text>
  <rect x="140" y="44" width="96" height="20" fill="#c9c9c9"/>
  <text x="242" y="58" font-size="12" fill="#333">12</text>
  <rect x="140" y="68" width="1" height="20" fill="#2f6690"/>
  <text x="146" y="82" font-size="12" fill="#333">0</text>

  <text x="140" y="108" font-size="12" fill="#333">Open Vault (vault sequence)</text>
  <rect x="140" y="114" width="296" height="20" fill="#c9c9c9"/>
  <text x="442" y="128" font-size="12" fill="#333">37</text>
  <rect x="140" y="138" width="248" height="20" fill="#2f6690"/>
  <text x="394" y="152" font-size="12" fill="#333">31</text>
</svg>

*Cutting the wire was worth up to 12 points; we scored 0. The vault sequence was worth up to 37 and we scored 31 — nearly the entire wire-disable stage's max value, just from the one decision to skip it and focus there instead.*

Here's how the 66 points we did earn broke down by stage:

<svg viewBox="0 0 500 380" xmlns="http://www.w3.org/2000/svg" style="width:100%; max-width:500px; height:auto;">
  <defs>
    <marker id="arrowhead-heist" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
      <path d="M0,0 L10,5 L0,10 z" fill="#333"/>
    </marker>
  </defs>
  <path d="M220,180 L220,80 A100,100 0 0,1 289,108 Z" fill="#4c9a8c"/>
  <path d="M220,180 L289,108 A100,100 0 0,1 201,278 Z" fill="#2f6690"/>
  <path d="M220,180 L201,278 A100,100 0 0,1 220,80 Z" fill="#e08a2c"/>
  <text x="244" y="120" font-size="13" fill="#fff" text-anchor="middle">12%</text>
  <text x="278" y="210" font-size="13" fill="#fff" text-anchor="middle">41%</text>
  <text x="155" y="174" font-size="13" fill="#fff" text-anchor="middle">47%</text>

  <line x1="274" y1="45" x2="259" y2="83" stroke="#333" stroke-width="1.5" marker-end="url(#arrowhead-heist)"/>
  <text x="280" y="32" font-size="12" fill="#333" text-anchor="start">Approach Camera Controls (8 pts)</text>

  <line x1="349" y1="246" x2="313" y2="228" stroke="#333" stroke-width="1.5" marker-end="url(#arrowhead-heist)"/>
  <text x="362" y="253" font-size="12" fill="#333" text-anchor="start">Identify Vault Code (27 pts)</text>

  <line x1="76" y1="166" x2="115" y2="170" stroke="#333" stroke-width="1.5" marker-end="url(#arrowhead-heist)"/>
  <text x="61" y="165" font-size="12" fill="#333" text-anchor="end">Open Vault (31 pts)</text>
</svg>

*Nearly 90% of our points came from the two stages we actually attempted — the vault sequence alone accounted for almost half of everything we scored. Disable Cameras isn't shown since it earned 0%.*

<details>
<summary>Full official rubric — Heist Mission</summary>

Rover mass: 49.9kg, no mass bonus (100%). Repair/modification penalties were 0 throughout, so Points Earned = Modified Points here.

| Stage | Action | Max | Earned |
|---|---|---|---|
| Approach Camera Controls | Avoid tripwires | 4 | 0 |
| Approach Camera Controls | Avoid camera | 4 | 0 |
| Approach Camera Controls | Avoid shining light on area viewed by camera | 8 | 0 |
| Approach Camera Controls | Reach camera controls | 8 | 8 |
| Disable Cameras | Identify correct wire to cut | 3 | 0 |
| Disable Cameras | Cut a wire | 6 | 0 |
| Disable Cameras | Cut the correct wire | 3 | 0 |
| Identify Vault Code | Approach security console | 5 | 5 |
| Identify Vault Code | Attempt to decode security console password | 6 | 6 |
| Identify Vault Code | Correctly decode security console password | 4 | 4 |
| Identify Vault Code | Physically interface with security console | 6 | 6 |
| Identify Vault Code | Correctly find vault code | 6 | 6 |
| Open Vault | Approach Morse key | 4 | 4 |
| Open Vault | Interact with Morse key | 6 | 6 |
| Open Vault | Enter the vault code | 6 | 6 |
| Open Vault | Enter the vault code fast enough | 6 | 0 |
| Open Vault | Open the vault door | 5 | 5 |
| Open Vault | Remove the artifact from the vault | 5 | 5 |
| Open Vault | Return to the extraction point with the artifact | 5 | 5 |
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

Share of the total 62.4 points earned, by order (same-item orders share a color):

<svg viewBox="0 0 520 400" xmlns="http://www.w3.org/2000/svg" style="width:100%; max-width:520px; height:auto;">
  <defs>
    <marker id="arrowhead-rc" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
      <path d="M0,0 L10,5 L0,10 z" fill="#333"/>
    </marker>
  </defs>
  <path d="M220,180 L220,80 A100,100 0 0,1 311,139 Z" fill="#4c9a8c"/>
  <path d="M220,180 L311,139 A100,100 0 0,1 315,149 Z" fill="#e08a2c"/>
  <path d="M220,180 L315,149 A100,100 0 0,1 220,280 Z" fill="#2f6690"/>
  <path d="M220,180 L220,280 A100,100 0 0,1 199,278 Z" fill="#8a6bbf"/>
  <path d="M220,180 L199,278 A100,100 0 0,1 125,211 Z" fill="#4c9a8c"/>
  <path d="M220,180 L125,211 A100,100 0 0,1 121,190 Z" fill="#c94f4f"/>
  <path d="M220,180 L121,190 A100,100 0 0,1 210,81 Z" fill="#2f6690"/>
  <path d="M220,180 L210,81 A100,100 0 0,1 220,80 Z" fill="#e08a2c"/>

  <line x1="302" y1="54" x2="277" y2="92" stroke="#333" stroke-width="1.5" marker-end="url(#arrowhead-rc)"/>
  <text x="308" y="47" font-size="11" fill="#333" text-anchor="start">1: Apple — 18%</text>

  <line x1="360" y1="126" x2="318" y2="142" stroke="#333" stroke-width="1.5" marker-end="url(#arrowhead-rc)"/>
  <text x="366" y="122" font-size="11" fill="#333" text-anchor="start">2: Pancakes — 2%</text>

  <line x1="341" y1="268" x2="305" y2="242" stroke="#333" stroke-width="1.5" marker-end="url(#arrowhead-rc)"/>
  <text x="347" y="275" font-size="11" fill="#333" text-anchor="start">3: Sub — 30%</text>

  <line x1="204" y1="329" x2="209" y2="284" stroke="#333" stroke-width="1.5" marker-end="url(#arrowhead-rc)"/>
  <text x="204" y="342" font-size="11" fill="#333" text-anchor="middle">4: Spaghetti — 3%</text>

  <line x1="120" y1="291" x2="150" y2="258" stroke="#333" stroke-width="1.5" marker-end="url(#arrowhead-rc)"/>
  <text x="114" y="304" font-size="11" fill="#333" text-anchor="end">5: Apple — 17%</text>

  <line x1="73" y1="211" x2="117" y2="202" stroke="#333" stroke-width="1.5" marker-end="url(#arrowhead-rc)"/>
  <text x="67" y="215" font-size="11" fill="#333" text-anchor="end">6: Pizza — 3%</text>

  <line x1="103" y1="86" x2="138" y2="114" stroke="#333" stroke-width="1.5" marker-end="url(#arrowhead-rc)"/>
  <text x="97" y="80" font-size="11" fill="#333" text-anchor="end">7: Sub — 25%</text>

  <line x1="212" y1="30" x2="215" y2="75" stroke="#333" stroke-width="1.5" marker-end="url(#arrowhead-rc)"/>
  <text x="212" y="20" font-size="11" fill="#333" text-anchor="middle">8: Pancakes — 2%</text>
</svg>

*The two Sub orders alone made up 55% of our total score. Both pancake orders together only made up 4% — but as it turned out, that 4% was the margin between winning the award and not.*

<details>
<summary>Full official rubric — RoverCooked</summary>

Rover mass: 46kg, 104% mass bonus (why "1 point earned" shows up as 1.04 modified). Repair/modification penalties were 0 throughout.

| Order | Action | Max | Earned | Modified |
|---|---|---|---|---|
| 1: Apple | Rover leaves start line | 1 | 1 | 1.04 |
| 1: Apple | Ingredient 1 touched | 1 | 1 | 1.04 |
| 1: Apple | Ingredient 1 prepared correctly | 3 | 3 | 3.12 |
| 1: Apple | Delivered without dropping any ingredient | 5 | 5 | 5.2 |
| 1: Apple | Delivered late | -2 | 0 | 0 |
| 1: Apple | Delivered early | 1 | 1 | 1.04 |
| 2: Pancakes | Ingredient 1 touched | 1 | 1 | 1.04 |
| 2: Pancakes | Ingredient 1 prepared correctly | 3 | 0 | 0 |
| 2: Pancakes | Delivered without dropping any ingredient | 5 | 0 | 0 |
| 2: Pancakes | Delivered late | -2 | 0 | 0 |
| 2: Pancakes | Delivered early | 1 | 0 | 0 |
| 3: Sub | Ingredient 1 touched | 1 | 1 | 1.04 |
| 3: Sub | Ingredient 1 prepared correctly | 3 | 3 | 3.12 |
| 3: Sub | Ingredient 2 touched | 1 | 1 | 1.04 |
| 3: Sub | Ingredient 2 prepared correctly | 3 | 3 | 3.12 |
| 3: Sub | Ingredient 3 touched | 1 | 1 | 1.04 |
| 3: Sub | Ingredient 3 prepared correctly | 3 | 3 | 3.12 |
| 3: Sub | Delivered without dropping any ingredient | 5 | 5 | 5.2 |
| 3: Sub | Delivered late | -2 | 0 | 0 |
| 3: Sub | Delivered early | 1 | 1 | 1.04 |
| 4: Spaghetti | Ingredient 1 touched | 1 | 1 | 1.04 |
| 4: Spaghetti | Ingredient 1 prepared correctly | 3 | 0 | 0 |
| 4: Spaghetti | Ingredient 2 touched | 1 | 1 | 1.04 |
| 4: Spaghetti | Ingredient 2 prepared correctly | 3 | 0 | 0 |
| 4: Spaghetti | Ingredient 3 touched | 1 | 0 | 0 |
| 4: Spaghetti | Ingredient 3 prepared correctly | 3 | 0 | 0 |
| 4: Spaghetti | Delivered without dropping any ingredient | 5 | 0 | 0 |
| 4: Spaghetti | Delivered late | -2 | 0 | 0 |
| 4: Spaghetti | Delivered early | 1 | 0 | 0 |
| 5: Apple | Ingredient 1 touched | 1 | 1 | 1.04 |
| 5: Apple | Ingredient 1 prepared correctly | 3 | 3 | 3.12 |
| 5: Apple | Delivered without dropping any ingredient | 5 | 5 | 5.2 |
| 5: Apple | Delivered late | -2 | 0 | 0 |
| 5: Apple | Delivered early | 1 | 1 | 1.04 |
| 6: Pizza | Ingredient 1 touched | 1 | 1 | 1.04 |
| 6: Pizza | Ingredient 1 prepared correctly | 3 | 0 | 0 |
| 6: Pizza | Ingredient 2 touched | 1 | 1 | 1.04 |
| 6: Pizza | Ingredient 2 prepared correctly | 3 | 0 | 0 |
| 6: Pizza | Ingredient 3 touched | 1 | 0 | 0 |
| 6: Pizza | Ingredient 3 prepared correctly | 3 | 0 | 0 |
| 6: Pizza | Delivered without dropping any ingredient | 5 | 0 | 0 |
| 6: Pizza | Delivered late | -2 | 0 | 0 |
| 6: Pizza | Delivered early | 1 | 0 | 0 |
| 7: Sub | Ingredient 1 touched | 1 | 1 | 1.04 |
| 7: Sub | Ingredient 1 prepared correctly | 3 | 3 | 3.12 |
| 7: Sub | Ingredient 2 touched | 1 | 1 | 1.04 |
| 7: Sub | Ingredient 2 prepared correctly | 3 | 3 | 3.12 |
| 7: Sub | Ingredient 3 touched | 1 | 1 | 1.04 |
| 7: Sub | Ingredient 3 prepared correctly | 3 | 3 | 3.12 |
| 7: Sub | Delivered without dropping any ingredient | 5 | 5 | 5.2 |
| 7: Sub | Delivered late | -2 | -2 | -2.08 |
| 7: Sub | Delivered early | 1 | 0 | 0 |
| 8: Pancakes | Ingredient 1 touched | 1 | 1 | 1.04 |
| 8: Pancakes | Ingredient 1 prepared correctly | 3 | 0 | 0 |
| 8: Pancakes | Delivered without dropping any ingredient | 5 | 0 | 0 |
| 8: Pancakes | Delivered late | -2 | 0 | 0 |
| 8: Pancakes | Delivered early | 1 | 0 | 0 |
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

# 📦 BlackBox

**Season:** CENTERSTAGE | **Achievement:** State Finalist | **Category:** Engineering

## Overview

BlackBox was Pioneer Robotics' entry for the CENTERSTAGE season. What makes this robot's story unusual is that it wasn't our first robot that year — we competed in our first two qualifiers with a claw-based robot, realized it wouldn't be competitive at States, and committed to a complete rebuild with a 7-week deadline. This case study documents the mechanical decisions behind that redesign: the custom carbon fiber chassis, the four-iteration intake, the laser-cut polycarbonate depositor, and the drone launcher we engineered from scratch.

**Challenge:** Design a robot to collect game pieces called "pixels" from the field and deposit them onto a backdrop at specific locations, while also launching a paper airplane drone into a designated zone at the end of each match.

## The Big Redesign

After our WPI qualifier, we did an honest debrief. Our claw-based robot had a match OPR of 20 points — not competitive for States. Rather than patch the existing design, we committed to a full rebuild with a hard deadline: 7 weeks to States. I designed the new chassis from scratch, iterated through four intake designs, and built a modular robot that could swap subsystems independently. The result was a match OPR of 98 points — nearly a 5x improvement.

## Custom Carbon Fiber Chassis

**Problem:** Our previous chassis used standard U-Channel framing, which forced us to work around the structure rather than design around our mechanisms. Electronics had to be placed awkwardly — the panel dragged against the floor and caused frequent disconnects. We had no vertical mounting space for mechanisms, and there was no easy access for maintenance between matches.

**Design Decision:** I designed Pioneer Robotics' first-ever fully custom chassis — a paneled side-plate design laser-cut from carbon fiber. Custom hole locations meant we could place every component exactly where it needed to be rather than compromising around a standard frame. The side plates are removable with 12 screws for fast maintenance, and I added a dedicated electronics access door on the side. Carbon fiber gave us the best strength-to-weight ratio available. Vertical component mounting eliminated the floor-dragging electronics issue entirely. I also integrated spring-loaded odometry pods directly into the chassis design so localization was built in from the start.

**Result:** The custom chassis eliminated the disconnect issues we'd fought all season. Vertical mounting kept all electronics clear of the ground, and the modular side plates meant any subsystem could be swapped with four screws during a match break — which we used repeatedly during the redesign period to iterate on the depositor while leaving the rest of the robot untouched.

## Intake System

**Problem:** CENTERSTAGE pixels are flat hexagonal tiles that need to be collected from both the ground and from stacks. We needed an intake that could handle both reliably without jamming, transfer cleanly to the depositor, and do it fast enough to be competitive. Our first attempt — a claw — was slow and unreliable. We went through four iterations before landing on the right solution.

**Design Decision:** Iteration 1 was a claw — simple to build, but slow cycle time and unreliable pickup. Iteration 2 used compliant wheels with a bar — better for drivers, worked on stacks, but too big and heavy, with a ramp transfer angle that was too steep. Iteration 3 was a tine system — fast intake, low maintenance, wide range — but couldn't collect from pixel stacks and had inconsistent transfer to the depositor. After connecting with iRobot engineers who showed us how to think about intake mechanisms, I combined the tine concept with O-ring belts into a single hybrid system: an arm that raises and lowers mini tines driven by chain and sprockets through a single motor. The O-ring belts replaced a direct drive and reduced jamming significantly. I built the structure from polycarbonate plates held together with structure beams, prototyped extensively in plywood first, and designed it as a fully self-contained module.

**Result:** The final intake collected pixels consistently from both the ground and stacks, required less driver precision than earlier iterations, and transferred cleanly to the depositor. The chain-and-sprocket drive ran faster than gears while using only one motor. The iRobot engineers' guidance on combining tines and belts was directly applied here and made the difference.

## Depositor

**Problem:** Scoring requires placing pixels precisely onto a backdrop. Our first depositor was a claw — simple, but never exactly level with the backdrop due to heavy servos, and inaccurate when depositing. Our second iteration was a rigid polycarbonate depositor — easier to sub-iterate, but it couldn't drop one pixel at a time and had inconsistent transfer from the intake.

**Design Decision:** The final depositor used a laser-cut polycarbonate body with compliant wheels that rotate to push pixels upward and allow releasing one at a time. It can tilt parallel to the backdrop within 1/16 of an inch — a precision requirement that took many iterations to achieve. I made all custom parts laser-cuttable so a new prototype could be produced in minutes and tested immediately. The custom servo hub takes 17 seconds to cut. Belt-driven Misumi linear slides integrated the depositor and hanging mechanism into one system, with two GoBilda servo gearboxes tilting the slides for accurate pixel placement anywhere on the board.

**Result:** Switching from the claw to the compliant-wheel depositor quintupled our average points scored per match — from 20 to 98. The ability to drop one pixel at a time gave drivers precise control over scoring placement. After breaking 8 polycarbonate slide mounts during testing, I switched to custom-machined aluminum versions which held through the rest of the season with no failures.

## Drone Launcher

**Problem:** CENTERSTAGE includes an end-game task where the robot must launch a paper airplane drone into a designated zone. Our first two rubber band launcher iterations misfired frequently — the rubber band release was inconsistent, the drone fell out during teleop, and the mechanism was too large to fit cleanly on the new robot.

**Design Decision:** I CADed a custom drone holder that was light and compact, giving the drone just enough space to rest securely without falling out. The launcher fires by tilting the holder upward with Axon servos, which releases a rubber band mounted to the front of the launcher in an L-configuration. I ran over 150 test trials to determine the optimal launch angle, testing at 20°, 25°, 35°, 45°, 60°, and 80° from multiple distances. The data showed 40° was optimal for consistent distance coverage. The earlier rubber band design had operated in a 53°–68° range — too steep and inconsistent.

**Result:** We successfully launched the drone in 100% of our matches at States. The 150-trial data-driven approach to finding the launch angle was the key — without empirical testing, we would have stayed in the wrong angle range.

## Full Robot

BlackBox was designed with modularity as the core principle — any subsystem removable with four screws. This wasn't just a design preference; it was what made the 7-week rebuild possible. While one member worked on the depositor, the rest of the robot remained intact and testable. LED lights integrated with color sensors change color to indicate pixel count in the depositor, automatically reversing the intake if more than two pixels are loaded. We hanged in 100% of matches using the linear slides — no separate hanging mechanism was needed, since the slides doubled as the hang point with two integrated hooks.

## Key Takeaways

1. **Know When to Rebuild** — Patching a fundamentally flawed design wastes more time than a clean restart. Committing fully to the rebuild is what produced a 5x improvement in match performance.
2. **Design for Iteration Speed** — The depositor went through many versions in 7 weeks because I could cut a new prototype in 17 seconds. Designing parts to be laser-cuttable from the start made that iteration rate possible.
3. **Use Data, Not Guesses** — 150 drone launcher trials to find the right angle wasn't excessive — it was necessary. When a parameter matters, test it systematically.
4. **Modularity Is a Constraint, Not a Feature** — Building every subsystem to be removable with four screws felt like extra work upfront. Under a 7-week deadline with parallel development, it became the only reason the rebuild was possible at all.

## Related Robots
- [[Robot Docs/StretchBot|StretchBot]]
- [[Robot Docs/MantisBot|MantisBot]]
- [[Robot Docs/Shreybot|Shreybot]]

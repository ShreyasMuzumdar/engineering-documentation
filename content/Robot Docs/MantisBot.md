# 🦾 MantisBot

**Season:** Into the Deep | **Achievement:** Live Portfolio | **Category:** Engineering

## Overview

MantisBot is Pioneer Robotics' entry for the Into the Deep season. The game requires collecting samples and specimens from an underwater-themed field and depositing them in scoring zones, with an end-game climb onto hanging bars. This case study documents the key mechanical decisions across the season — the chassis, claw, slide system, and climb — and the major redesign that shaped the final robot.

**Challenge:** Collect colored samples and metal specimens from the field and score them in designated zones at multiple heights, then ascend to hang on bars at the end of each match, all within tight size and weight limits.

## Season Approach

We began the season with ambitious goals — implementing a Power Take Off (PTO) and a Differential Swerve drivetrain, both of which we had never built before. We also applied an Agile development methodology with two-week sprints, daily team standups, and formal sprint reviews. Midseason we acknowledged the design was too complex and simplified to a more focused, reliable system. The final robot emphasizes simplicity and reliability — the two core values that emerged from every lesson this season.

## Chassis and Drivetrain

**Problem:** Our previous season used a live-axle drivetrain, which caused inconsistencies and wasted space. Electronics placed on the bottom panel dragged against the floor and caused disconnect issues mid-match. We needed a more reliable foundation going into a new season with more complex upper mechanisms.

**Design Decision:** I switched to a dead-axle mecanum drivetrain — stationary axles with wheels rotating freely around them — which reduced our chassis footprint by 25% and eliminated the excess motion from the live-axle system. Electronics were moved to the bottom for easy access during maintenance. The carbon fiber side plate chassis from last season was retained as the structural base, with a modular upper chassis that can be detached independently for mechanism work without touching the drive base. Spring-loaded odometry pods were integrated directly into the chassis to maintain ground contact for accurate localization throughout matches.

**Result:** The dead-axle system was significantly more consistent than the previous live-axle approach. The modular upper/lower chassis separation proved essential during the midseason redesign — we were able to rebuild the upper mechanisms without disturbing the drivetrain, which saved significant time under a tight competition deadline.

## Differential Claw

**Problem:** Into the Deep requires collecting both flat samples and cylindrical specimens from tight spaces inside the Submersible structure. Our first claw was large and difficult to maneuver inside the confined geometry. It used internal grip — effective for grouping samples — but was bulky and prone to breaking under repeated stress.

**Design Decision:** I iterated through three claw designs. The first used internal grip and rotated on two axes — flexible but large. The second introduced external grip contoured to the sample shape, which increased consistency and durability, but was still too bulky. The final design applied a differential mechanism — a concept we had explored in our PTO prototype — which allowed rotation on two axes simultaneously using bevel gears, creating a much smaller form factor. Bringing the points of rotation together reduced the distance between moving parts, shrinking the claw from bulky to compact while actually improving rotational freedom. The differential also reduced motor strain by distributing load more efficiently.

**Result:** The final differential claw was lightweight, reliable inside the Submersible, and gave us more rotational freedom than either previous iteration. The unexpected benefit was that the PTO development — which we ultimately didn't use on the final robot — directly taught us the bevel gear principles that made the claw work. The failed mechanism produced the knowledge that improved the working one.

## Slides Actuation and Pivot

**Problem:** We needed linear slides that could both extend for scoring and pivot to different angles for depositing at the high basket and bar. Running separate motors for extension and pivot creates coordination problems and wastes motor ports. Belt skipping on the original motor unit caused the slides to lose position during matches.

**Design Decision:** I designed a custom two-sided pulley with bearings that spin freely on the axle, allowing pivot and actuation on the same axis independently of one another. Both motors are housed together in one module, optimizing space and simplifying maintenance access. After belt skipping issues, I shifted the motor mounting holes back to correct belt tensioning — this also improved structural integrity by connecting the module to the side plates. I also switched from two sets of slides to a single set, which eliminated the need to coordinate two motors and proved more reliable in competition. Custom aluminum slide inserts replaced polycarbonate ones after breaking 8 of the polycarbonate versions during testing. A chain and sprocket system rotates the slides, with the motor selection determined by a torque calculation based on arm weight and extension distance.

**Result:** The single-slide system was meaningfully more reliable than the dual-slide approach. The hole-shift fix resolved belt skipping entirely. The aluminum inserts held through the full competition season with no failures.

## Ascent and Climb

**Problem:** The end-game requires climbing onto horizontal bars at increasing heights for bonus points. A separate dedicated climbing mechanism adds weight and complexity. We needed to achieve the climb without adding a new system to an already complex robot.

**Design Decision:** I designed the ascent component to attach directly to the linear slides, using the same system we already had for scoring to pull the robot onto the bars. Static hooks shaped by the upper chassis maintain a minimal profile during normal play and engage the bar when the slides extend and retract. I performed a torque calculation to determine the required motor force to lift the full robot weight, then selected the fastest motors that met that torque threshold — balancing speed with reliability.

**Result:** Integrating the climb into the existing slide system eliminated a dedicated mechanism entirely, saving weight and motor ports. The torque-calculated motor selection meant the climb was reliable without being over-engineered. The static hooks' minimal profile meant they didn't interfere with normal scoring operations during teleop.

## Full Robot

MantisBot went through more iterations than any previous Pioneer Robotics robot. We attempted PTO and Differential Swerve — two mechanisms we'd never built — before recognizing midseason that the complexity was hurting reliability. The final robot strips back to what works: a dead-axle mecanum base, a single belt-driven slide system, a differential claw, and an integrated climb. Every mechanism on the robot can be accessed or removed for maintenance without disturbing adjacent systems. The Agile sprint methodology meant we had clear documentation of every decision, which made the midseason pivot much faster to execute.

## Key Takeaways

1. **Ambition Needs a Cutoff Date** — We spent months on PTO and Differential Swerve before acknowledging they weren't competition-ready. Setting a hard go/no-go date for experimental mechanisms upfront would have saved weeks.
2. **Failed Mechanisms Teach Working Ones** — The PTO prototype never made it onto the final robot, but the bevel gear knowledge from building it directly enabled the differential claw. Time spent on an abandoned mechanism isn't always wasted — it depends on what you extract from it.
3. **Test to Failure, Then Choose the Right Material** — Breaking 8 polycarbonate slide mounts was frustrating but conclusive. Switching materials based on one failure is a guess — switching after repeated failures under real conditions is engineering.
4. **Simplicity Is a Design Decision, Not a Fallback** — The final robot is simpler than what we originally planned. That simplicity was earned — it came from understanding why the complex version didn't work, not from avoiding complexity in the first place.

## Related Robots
- [[Robot Docs/StretchBot|StretchBot]]
- [[Robot Docs/Shreybot|Shreybot]]
- [[Robot Docs/BlackBox|BlackBox]]

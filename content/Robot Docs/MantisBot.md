# 🦾 MantisBot

**Season:** Into the Deep | **Achievement:** Connect Award | **Category:** Engineering

## Overview

MantisBot is Pioneer Robotics' entry for the Into the Deep season. The game requires collecting samples and specimens from an underwater-themed field and depositing them in scoring zones, with an end-game climb onto hanging bars. This case study documents the key mechanical decisions across the season , the chassis, claw, slide system, and climb , and the major redesign that shaped the final robot.

**Challenge:** Collect colored samples and metal specimens from the field and score them in designated zones at multiple heights, then ascend to hang on bars at the end of each match, all within tight size and weight limits.

## Season Approach

We began the season with ambitious goals , implementing a Power Take Off (PTO) and a Differential Swerve drivetrain, both of which we had never built before. We also applied an Agile development methodology with two-week sprints, daily team standups, and formal sprint reviews. Midseason we acknowledged the design was too complex and simplified to a more focused, reliable system. The final robot emphasizes simplicity and reliability , the two core values that emerged from every lesson this season.

## Chassis and Drivetrain

**Problem:** Our previous season used a live-axle drivetrain, which caused inconsistencies and wasted space. Electronics placed on the bottom panel dragged against the floor and caused disconnect issues mid-match.

**Design Decision:** I switched to a dead-axle mecanum drivetrain , stationary axles with wheels rotating freely around them , which reduced our chassis footprint by 25%. The carbon fiber side plate chassis from last season was retained as the structural base, with a modular upper chassis that can be detached independently. Spring-loaded odometry pods were integrated directly into the chassis to maintain ground contact for accurate localization throughout matches.

**Result:** The dead-axle system was significantly more consistent than the previous live-axle approach. The modular upper/lower chassis separation proved essential during the midseason redesign.

## Differential Claw

**Problem:** Into the Deep requires collecting both flat samples and cylindrical specimens from tight spaces inside the Submersible structure. Our first claw was large, difficult to maneuver, and prone to breaking under repeated stress.

**Design Decision:** I iterated through three claw designs. The final design applied a differential mechanism , which allowed rotation on two axes simultaneously using bevel gears, creating a much smaller form factor. Bringing the points of rotation together reduced the distance between moving parts, shrinking the claw from bulky to compact while actually improving rotational freedom.

**Result:** The final differential claw was lightweight, reliable inside the Submersible, and gave us more rotational freedom than either previous iteration. The PTO development , which we ultimately didn't use , directly taught us the bevel gear principles that made the claw work.

![MantisBot differential claw CAD , bevel gear mechanism](/static/images/robot-photos/mantisbot/claw.png)

## Slides Actuation and Pivot

**Problem:** We needed linear slides that could both extend for scoring and pivot to different angles. Belt skipping on the original motor unit caused the slides to lose position during matches.

**Design Decision:** I designed a custom two-sided pulley with bearings that spin freely on the axle, allowing pivot and actuation on the same axis independently. I switched from two sets of slides to a single set, which proved more reliable in competition. Custom aluminum slide inserts replaced polycarbonate ones after breaking 8 of the polycarbonate versions during testing.

**Result:** The single-slide system was meaningfully more reliable. The aluminum inserts held through the full competition season with no failures.

![MantisBot slides pivot mechanism CAD](/static/images/robot-photos/mantisbot/slides_pivot.png)

## Ascent and Climb

**Problem:** The end-game requires climbing onto horizontal bars at increasing heights. A separate dedicated climbing mechanism adds weight and complexity.

**Design Decision:** I designed the ascent component to attach directly to the linear slides, using the same system we already had for scoring to pull the robot onto the bars. Static hooks engage the bar when the slides extend and retract. I performed a torque calculation to determine the required motor force to lift the full robot weight.

**Result:** Integrating the climb into the existing slide system eliminated a dedicated mechanism entirely, saving weight and motor ports.

![MantisBot climbing at competition](/static/images/robot-photos/mantisbot/climb.png)

## Full Robot

MantisBot went through more iterations than any previous Pioneer Robotics robot. We attempted PTO and Differential Swerve before recognizing midseason that the complexity was hurting reliability. The final robot strips back to what works: a dead-axle mecanum base, a single belt-driven slide system, a differential claw, and an integrated climb.

![MantisBot full robot CAD](/static/images/robot-photos/mantisbot/full_robot.png)

## Key Takeaways

1. **Ambition Needs a Cutoff Date** , Setting a hard go/no-go date for experimental mechanisms upfront would have saved weeks.
2. **Failed Mechanisms Teach Working Ones** , The PTO prototype never made it onto the final robot, but the bevel gear knowledge from building it directly enabled the differential claw.
3. **Test to Failure, Then Choose the Right Material** , Breaking 8 polycarbonate slide mounts was frustrating but conclusive. Switching materials based on one failure is a guess , switching after repeated failures under real conditions is engineering.
4. **Simplicity Is a Design Decision, Not a Fallback** , The final robot is simpler than what we originally planned. That simplicity was earned.

## Related Robots
- [[Robot Docs/StretchBot|StretchBot]]
- [[Robot Docs/Shreybot|Shreybot]]
- [[Robot Docs/BlackBox|BlackBox]]

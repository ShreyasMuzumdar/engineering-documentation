# 🏆 StretchBot

**Season:** PowerPlay | **Achievement:** State Champion | **Category:** Engineering

## Overview

StretchBot was Pioneer Robotics' entry for the PowerPlay season. Unlike a typical build cycle, we deliberately designed two robots that year , a restrained qualifier robot and the fully capable competition robot unveiled at States. This case study documents the mechanical decisions behind the chassis, extension, intake, and depositor, and what happened when we pushed further at the Maryland Tech Invitational.

**Challenge:** Design a robot to collect cones from ground stacks and deposits, then score them on junction poles at low, medium, and high heights as quickly as possible, within strict size and weight constraints.

## Season Strategy

We made the deliberate decision to field a less capable robot at the qualifier to avoid telegraphing our full design to competitors before States. Critically, I carried over key design elements from the qualifier robot so we wouldn't be starting from scratch for States.

## Chassis and Drivetrain

**Problem:** The robot needed to navigate freely between junction poles on a dense field. I needed a mathematically verified chassis size, not an eyeballed one.

**Design Decision:** I started with a 13" x 16" mecanum drive chassis, verifying field clearance by calculating the robot's diagonal using a hypotenuse check against the junction spacing. When mechanism changes required more internal space, I widened the chassis to 15" x 16". In the final revision I added custom side plates to protect the mecanum wheels.

**Result:** The three-version chassis evolution produced a footprint that satisfied field constraints while providing the internal volume needed for all mechanisms. The side plates proved their value , no wheel damage occurred across the full season including States.

## Extension and Cone Transfer

**Problem:** We needed horizontal extension to reach cones and transfer them internally for scoring. Our first attempt , belt-driven linear slides , couldn't achieve full extension because the belt geometry physically limited travel range.

**Design Decision:** I replaced the belt drive with polyplastic composite linkages on each end of the slides, running on servos rather than motors. After validating the linkage system, I upgraded to GoBilda 5-turn torque servos for finer rotational control over extension position.

**Result:** The linkage-driven system achieved reliable full extension throughout the season. The 5-turn servo upgrade noticeably tightened extension consistency.

![StretchBot linkage extension system CAD](/static/images/robot-photos/stretchbot/linkage.png)

## Intake and Cone Collection

**Problem:** PowerPlay cones are tapered, making them difficult to grip reliably at speed. We needed an intake that could grab a cone consistently without requiring the driver to precisely align the entire robot on every approach.

**Design Decision:** I went through three claw iterations, ultimately landing on a beveled claw: I calculated the cone's taper geometry (bottom diameter 65.4mm, top 60.9mm, height 14mm) to derive the correct bevel slope, CADed the profile in SolidWorks, and mounted it on a polycarbonate arm for horizontal reach.

**Result:** The arm-mounted beveled claw became our most reliable collection method. The bevel geometry caused cones to self-center on contact, reducing driver precision requirements and cutting collection time per cycle.

![StretchBot beveled claw CAD , mathematically derived taper geometry](/static/images/robot-photos/stretchbot/claw.png)

## Depositor and Aligner

**Problem:** Scoring required placing a cone onto a junction pole accurately and quickly. Our first depositor blocked the internal transfer path, making efficient cycling impossible.

**Design Decision:** I redesigned the depositor as an open ring shape , the cone slips in from above rather than requiring a full flip motion, which cleared the internal transfer path. I mounted it on vertical linear slides driven by a GoBilda SuperSpeed servo. The aligner was redesigned to physically grab the junction during scoring.

**Result:** The ring depositor eliminated the jam risk from the first version. Combined with the aligner physically latching onto the junction, drivers could execute deposits with significantly higher confidence , critical for achieving our 269-point high score.

![StretchBot ring depositor CAD](/static/images/robot-photos/stretchbot/depositor.png)

## Post-Season: Maryland Tech Invitational

After winning States, we were invited to the Maryland Tech Invitational , a field of the top 40 FTC teams in the world. I designed a spring-loaded odometry wheel for more accurate positioning, but switched to a fixed rigid mount under time pressure. During a match at MTI, contact with an opposing robot lifted the wheel momentarily, causing the autonomous routine to lose its reference frame and drive into the wall. The spring-loaded design I had originally prototyped would have absorbed that impact. It was an expensive lesson in not abandoning the original design intent under time pressure.

![StretchBot being assembled in the lab , Pioneer Robotics team 12589](/static/images/robot-photos/stretchbot/fullrobot.jpeg)

## Key Takeaways

1. **Strategy Is Part of Design** , Fielding a deliberate underperformer at the qualifier required designing upgrade paths into the robot from the start.
2. **Measure Before You Prototype** , The beveled claw only worked because I calculated the cone's taper mathematically first.
3. **Don't Compromise the Original Intent** , The spring-loaded odometry was the right design. Switching to a rigid mount to save time cost us at MTI.
4. **Public Failures Teach Better** , The MTI failure was livestreamed and spread widely. That visibility made the lesson about sensor robustness concrete in a way that no successful run could have.

## Related Robots
- [[Robot Docs/MantisBot|MantisBot]]
- [[Robot Docs/Shreybot|Shreybot]]
- [[Robot Docs/BlackBox|BlackBox]]

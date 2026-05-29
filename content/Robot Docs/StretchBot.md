---
dg-publish: true
---

﻿


    
    
    Stretchbot | Portfolio
                


    
        
            
                # Stretchbot


            
            
                
                    
                        
                            🌙
                        
                    
                
                ← Back
            
        

        
            Category

Engineering


            Achievement

🏆 State Champion


        

        
        
        
            Overview
            
                Stretchbot was Pioneer Robotics' entry for the PowerPlay season. Unlike a typical build cycle, we deliberately designed two robots that year — a restrained qualifier robot and the fully capable competition robot unveiled at states. This case study documents the mechanical decisions behind the chassis, extension, intake, and depositor, and what happened when we pushed further at the Maryland Tech Invitational.


                **Challenge:** Design a robot to collect cones from ground stacks and deposits, then score them on junction poles at low, medium, and high heights as quickly as possible, within strict size and weight constraints.


            

            
                Season Strategy
                We made the deliberate decision to field a less capable robot at the qualifier. The goal was to avoid telegraphing our full design to competitors before states — an element of surprise that gave us a strategic edge during alliance selections. Critically, I carried over key design elements from the qualifier robot so we wouldn't be starting from scratch for states.
            
        

        
        
            🔧 Chassis &amp; Drivetrain

            
                Problem
                The robot needed to navigate freely between junction poles on a dense field. Getting the footprint wrong would mean catching on poles or wasting internal volume. I needed a mathematically verified chassis size, not an eyeballed one.
            

            
                Design Decision
                I started with a 13" × 16" mecanum drive chassis, verifying field clearance by calculating the robot's diagonal using a hypotenuse check against the junction spacing. When mechanism changes required more internal space for servos, I widened the chassis to 15" × 16" — accounting for intake geometry and rewiring simultaneously. In the final revision I added custom side plates to protect the mecanum wheels, adding a half inch to each dimension but eliminating wheel damage risk during matches.
            

            
                Result
                The three-version chassis evolution produced a footprint that satisfied field constraints while providing the internal volume needed for all mechanisms. The side plates proved their value — no wheel damage occurred across the full season including states.
            
        

            

        
        
            ↔️ Extension &amp; Cone Transfer

            
                Problem
                We needed horizontal extension to reach cones and transfer them internally for scoring. The robot had to extend fully to reach the ground stack, but retract compactly within the size limit. Our first attempt — belt-driven linear slides — couldn't achieve full extension because the belt geometry physically limited travel range.
            

            
                Design Decision
                I replaced the belt drive with polyplastic composite linkages on each end of the slides. One linkage attached to the intake arm, the other to a GoBilda torque servo — the entire extension mechanism ran on servos rather than motors, freeing motor ports and allowing full slide travel. After validating the linkage system, I upgraded to GoBilda 5-turn torque servos for finer rotational control over extension position, which directly improved cone placement precision.
            

            
                Result
                The linkage-driven system achieved reliable full extension throughout the season. The 5-turn servo upgrade noticeably tightened extension consistency, reducing missed transfers during high-speed cycling. The tradeoff — increased mechanical complexity — was worth it for the scoring reliability gained.
            
        

            

        
        
            🎯 Intake &amp; Cone Collection

            
                Problem
                PowerPlay cones are tapered, making them difficult to grip reliably at speed. We needed an intake that could grab a cone consistently without requiring the driver to precisely align the entire robot on every approach.
            

            
                Design Decision
                I went through three claw iterations. The first was a rounded polyplastic composite claw with Dycem adhesive on the interior for friction — functional, but only worked when driving directly into the cone. The second was a beveled claw: I calculated the cone's taper geometry (bottom diameter 65.4mm, top 60.9mm, height 14mm) to derive the correct bevel slope, CADed the profile in SolidWorks, and powered it with a GoBilda superspeed servo. The third version mounted this claw on a polycarbonate arm, adding horizontal reach so the driver could collect cones from a distance rather than repositioning the whole robot.
            

            
                Result
                The arm-mounted beveled claw became our most reliable collection method. The bevel geometry caused cones to self-center on contact, reducing driver precision requirements and cutting collection time per cycle. The Dycem adhesive added a margin of safety on borderline grips.
            
        

            

        
        
            📍 Depositor &amp; Aligner

            
                Problem
                Scoring required placing a cone onto a junction pole accurately and quickly. Our first depositor — a cone-shaped insert that flipped the cone upright onto the pole — blocked the internal transfer path, making efficient cycling impossible. Separately, drivers needed a reliable way to align to junctions without burning time on visual guesswork each cycle.
            

            
                Design Decision
                I redesigned the depositor as an open ring shape — the cone slips in from above rather than requiring a full flip motion, which cleared the internal transfer path and enabled much faster cycling. I mounted it on vertical linear slides driven by a GoBilda SuperSpeed servo for rapid height changes between junction levels. For the aligner, I started with a thin PLA filament guide for visual positioning, then redesigned it to physically grab the junction during scoring. After checking the game manual I confirmed it needed to be at least 2 inches in radius to legally contact the pole, so I sized it accordingly.
            

            
                Result
                The ring depositor eliminated the jam risk from the first version. Combined with the aligner physically latching onto the junction, drivers could execute deposits with significantly higher confidence — which was critical for achieving our 269-point high score and maintaining consistency throughout states.
            
        

            

        
        
            🌍 Post-Season: Maryland Tech Invitational

            
                Context
                After winning states, we were invited to the Maryland Tech Invitational — a field of the top 40 FTC teams in the world. To compete at that level we needed more precise autonomous positioning. Our existing system used drive motor encoders, which accumulate drift over time. I decided to add a dedicated odometry wheel for more accurate real-time position tracking.
            

            
                Design Decision
                I designed the odometry wheel to be spring-loaded so it would maintain consistent ground contact regardless of field surface variation. The concept was correct, but the springs available weren't stiff enough to prevent the wheel from skipping under load. Rather than delay the build, I switched to a fixed rigid mount — simpler, and still a meaningful accuracy improvement over motor encoders alone.
            

            
                Result (and What Went Wrong)
                During a match at MTI, our robot made brief contact with an opposing robot. The impact lifted the rigidly-mounted odometry wheel off the ground momentarily. With no position feedback, the autonomous routine lost its reference frame and drove the robot directly into the wall. The spring-loaded design I had originally prototyped would have absorbed that impact and maintained contact. It was an expensive lesson in not abandoning the original design intent under time pressure — the failure was very public, but it made the reasoning stick.
            
        

            

        
        
            Key Takeaways
            StretchBot pushed the limits of linear extension and structural stability. Developing a stable multi-stage lift within tight weight constraints reinforced the value of material selection and the necessity of rigorous stress analysis during the initial design phase.


            
                
                    
                        1
                        
                            Strategy Is Part of Design
                            Fielding a deliberate underperformer at the qualifier required designing upgrade paths into the robot from the start. The strategic decision shaped every mechanical choice made in the first build.
                        
                    
                
                
                    
                        2
                        
                            Measure Before You Prototype
                            The beveled claw only worked because I calculated the cone's taper mathematically first. Starting from measured geometry gets you closer on iteration one and avoids chasing a shape by feel.
                        
                    
                
                
                    
                        3
                        
                            Don't Compromise the Original Intent
                            The spring-loaded odometry was the right design. Switching to a rigid mount to save time cost us at MTI. When a change is driven by schedule rather than engineering reasoning, it needs to be flagged — not quietly shipped.
                        
                    
                
                
                    
                        4
                        
                            Public Failures Teach Better
                            The MTI failure was livestreamed and spread widely. That visibility made the lesson about sensor robustness and mechanical redundancy concrete in a way that no successful run could have.
                        
                    
                
            
        

        
        
            
        📱 VIEW IN AR
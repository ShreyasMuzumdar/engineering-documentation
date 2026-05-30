# 🛰️ Science in Orbit: Interactive Satellite Exhibit

## 🌟 Introduction & Problem Statement

Children ages 7-11 in underserved communities across the Boston area face significant barriers to accessing and benefitting from modern technology infrastructure, including little exposure to concepts such as satellite communications and internet connectivity. This gap contributes to broader disparities in STEM interest and career aspirations among youth. Current educational resources tend to assume digital access and fail to provide children with meaningful, hands-on experiences that connect engineering principles to their everyday lives.

As a result, many of these children do not see engineering and technology as pathways available to them, limiting their aspirations and reducing the pipeline of future STEM innovators from these communities.

### 🎯 Project Goals
A well-designed travel campaign exhibit must address this specific educational gap by delivering a hands-on, interactive learning experience.

**Physical Requirements:**
- **Portability:** Fits within a 36x28" profile.
- **Durability:** Designed for interaction from energetic 7-11 year olds.
- **Budget:** Targeted strictly under $100 for the prototype.
- **Infrastructure:** Capable of operating with a standard power outlet.
- **Assembly:** Assembled by max 2 people in under 10 minutes.
- **Weight:** Modular components should not exceed 227 grams.

**Overarching Goal:**
To genuinely empower youth by demonstrating that they can understand and build complex systems that impact the world.

![Final Assembly](/static/finalassembly.jpeg)
*Fig. 1. The actual final assembly of the Science in Orbit interactive exhibit.*

---

## 📚 Research & Background

### 🌍 Satellite Utility
Satellites improve human lives and manage global infrastructure. While commercial projects get most attention, NASA projects like **SMAP (Soil Moisture Active Passive)** and **RADARSAT** are critical.
- **Project SMAP:** Measures soil moisture and freeze/thaw conditions every 2 days to better predict agricultural and climate issues.
- **Project RADARSAT:** Captures data for flood mapping, landslide detection, and damage assessment.

### 🌐 The Digital Divide
While 51% of the global population has access to 5G, coverage is uneven: 84% in high-income areas vs. only 4% in low-income areas. This "digital divide" is caused by the prohibitive cost of maintaining fiber optic cables in rural or underserved areas.

![Global Submarine Cable Network](/static/map.jpeg)
*Fig. 2. Global Submarine Cable Network showing the physical infrastructure of the internet.*

### 🚀 The Solution: LEO Satellites
Deploying satellites in **Low Earth Orbit (LEO)** allows for more equitable internet access without extensive ground infrastructure. This project applies **Humanitarian Engineering** and an **Entrepreneurial Mindset** to give students the resources to help themselves, empowering them to be changemakers.

---

## 🛠️ Methodology & Implementation

### 🔄 The Engineering Design Process (EDP)
The "Science in Orbit" exhibit followed a structured, iterative cycle:
1. **Problem Definition:** Analysis of users (children 7-11) using 20+ academic sources.
2. **Solution Generation:** Used rank-order charts and Kepner-Tregoe Decision Analysis (KTDA).
3. **Implementation:** Progressed through cardboard prototyping $\rightarrow$ CAD $\rightarrow$ 60% PoC $\rightarrow$ 90% prototype $\rightarrow$ Final prototype.

![Rank Order Table](/static/rankordertable.jpeg)
*Rank Order Table: Phase 1 Selection*

![KTDA Table](/static/ktdatable.jpeg)
*KTDA Table: Phase 2 Selection*

### 💻 Technical Development
I (Shreyas) handled the CAD modeling, coding, and circuitry.

**The Tracking Game:**
- **Input:** User controls sensor orientation via a joystick.
- **Logic:** Ultrasonic sensor provides readings to an Arduino.
- **Output:** Arduino controls servos to track physical satellites; a score is generated based on accuracy.

![User Interaction Flow Chart](/static/interactionflowchart.jpeg)
*Fig. 3. Detailed user interaction flow showing the logic of the satellite tracking game.*

### ⚡ Electronics & Challenges
The circuitry was complex and presented several hurdles:
- **Wiring Management:** Lack of labels led to hours of debugging.
- **Power Stability:** Initially used a 9V battery, which caused "jittery" servo behavior. Switching to a regulated **6V external battery** stabilized the system.

**Final Circuit Split:**
- **Circuit 1 (Main):** Ultrasonic sensor, pan/tilt servos, LCD screen, joystick, and LED strip.
- **Circuit 2 (Motor):** TT gear motor for the rotating ring, utilizing a separate motor driver.

![Initial Wiring Mess](/static/initial-wiring-mess.jpeg)
*Issue 1: The initial wiring mess.*

![Wiring 1](/static/wiring1.jpeg)
*Final Version: Main Circuit.*

![Wiring 2](/static/wiring2.jpeg)
*Final Version: Motor Circuit.*

---

## 📊 Results & Conclusion

### ✅ Final Outcome
The exhibit featured a motorized rotating ring with three 3D-printed satellites (LEO, MEO, and GEO) rotating around a central Earth model.

**Key Achievements:**
- **Budget:** Total cost was **$83.11**, well under the $100 limit.
- **Portability:** Successfully fit within the required transport bag.
- **Resources:** Utilized recycled parts from the FYELIC makerspace and cost-effective wood.

### ⚠️ The Expo Disaster
On the day of the final exhibition, a servo failed, rendering the scoring system non-functional. Attempting an on-site fix caused a cascading circuit failure.

**Resilience in Action:**
The team pivoted to a **facilitated interaction model**, using the physical ring and informational poster board to manually explain the concepts to the children.

![Exhibition Feedback](/static/feedback1.jpeg)
*Fig. 4. Educational poster and feedback wall indicating strong user engagement.*

### 💭 Reflection
- **Technical Lesson:** Always label wiring from the start.
- **Communication Lesson:** Clear, assertive communication is vital. I realized I should have spoken up sooner about technical feasibility (e.g., the initial maglev idea).

### 📈 Impact
Despite mechanical failure, the educational impact was proven. Children noted that "LEO satellites help u get jobs + schoolwork done" and "They are used for predicting weather," proving the core message was retained.

## 📚 Sources
1. [SMAP Mission Description](https://smap.jpl.nasa.gov/mission/description)
2. [UN Department of Economic and Social Affairs](https://sdgs.un.org/goals/goal9)
3. [Sufyan et al., "From 5G to beyond 5G"](https://doi.org/10.3390/electronics12102200)
4. [Westberg et al., "5G Infrastructure RF Solutions"](https://doi.org/10.1109/mmm.2019.2941631)

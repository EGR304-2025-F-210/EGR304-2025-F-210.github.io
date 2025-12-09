---
title: Product Requirements
tags:
- Requirements
---

## Project Objectives

- Design an inexpensive consumer water-quality monitor.
- Include multiple sensors for detection and measurement of harmful pollutants.
- Keep project scope reasonable to ensure completion within the course timeline.
- Gain experience in embedded systems, coding, sensor design, and small-scale electronics.
- While profit is a long-term consideration, the primary financial goal is to deliver an affordable environmental monitoring device accessible to low-income communities.

---

## Stakeholders

- **Manufacturers:** Must balance low cost, reliability, and ethical production practices.
- **Distributors:** Responsible for transporting finished units efficiently through established supply channels.
- **Financiers:** Provide the capital required to scale early manufacturing and distribution.
- **Retailers:** Sell the device to individuals and organizations concerned about water safety.
- **Customers:** Primarily low-income users or users at higher risk of exposure to contaminated water sources.
- **VibeWater:** Coordinates engineering, business, and distribution efforts to maximize the impact of a low-cost water-quality monitoring solution.

---


## Use Cases

**User Story #1: Sarah**
Sarah is a 42-year-old mom who regularly takes her young children to a local park. Her family just recently moved to this town because her husband, Bob, got a new job at a nearby manufacturing plant that dumps it's waste into a nearby river. She's noticed her kids have started to cough more often than usual, but they don't appear to be sick. After doing some research, she found that regulations about pollution are more relaxed in this new town compared to the rest of the country. She decides that someone needs to start monitoring the water for harmful pollutants before someone becomes seriously ill. However, no one is willing to support her investigation and she doesn't have enough money to hire a professional.

Sarah finds a new water quality monitoring system that is easily affordable and decides to take it upon herself to monitor the water. She does not have any kind of technical background, so she normally wouldn't be able to understand what all of the water quality tests mean. This low-cost device allows her quickly and easily diagnose pollution issues that she can explain to her community. Her findings will not change regulations on their own, but the easy-to-understand readings will show her community the issues they are facing due to the relaxed regulations. She can use these findings to further her cause in updating the environmental regulations.

**User Story #2: Jimmy**
Jimmy is a 79-year-old retiree who has a number of medical issues. He is looking for a new apartment to rent, but he also has a fixed income. He is worried about the water quality of these apartments, so he wants to know whether the water supplied to these apartments is drinkable. He doesn't trust findings published by large entities, so he searches for a water monitoring device that he can bring with him everywhere he goes. This way he can test the water himself.

This inexpensive monitor allows him to check the tap water in apartments he views. Since Jimmy has a fixed income, he cannot afford a significant amount of repairs and his aging body prohibits him from doing super intensive repairs and tests with the device. The device can change it's screen brightness, font size and is easy to follow directions. The majority of product issues can be solved by simply replacing the batteries or turning the device off and back on again. Jimmy would be able to easily peform his environmental tests, repair his device and change his settings easily.

---

## Design Aspects & Priorities

Priorities are standardized as:  
- **P0 = Critical (must-have)**  
- **P1 = Important (high-value)**  
- **P2 = Nice-to-have (optional)**  

### 1. Hardware and Product Design
- 1.1 The hardware should be somewhat portable (P2)  
- 1.2 The hardware should be durable (P2)  
- 1.3 The hardware should be compact (P2)  

### 2. Software Functionality
- 2.1 The product shall offer high accuracy in measurement and warning data (P0).  
- 2.2 The product shall include a calibration process to ensure unit accuracy after shipping or handling (P0).  
- 2.3 The software shall be distributed as free software following FSF’s four freedoms (P1).  
  - 2.3.1 If binary blobs are required, users will be notified and binaries will be provided (P2).  
- 2.4 The software shall use a single statically-typed systems language to improve reliability and performance (P1).  
- 2.5 The software shall be designed for portability and POSIX compliance (P2).  
- 2.6 The source code shall follow a consistent style guide (P0).  
  - 2.6.1 Google C++ Style Guide for C++  
  - 2.6.2 Linux Kernel Coding Style for C  
  - 2.6.3 Microsoft .NET Coding Conventions for C#  
  - 2.6.4 Industry-recognized guides for Rust, Haskell, LISP, Lua, Java, and others  
- 2.7 All sensors will define "SAFE" and "DANGER" thresholds for pH, opacity, and conductivity.  
  - 2.7.1 pH is “SAFE” between 6.5 and 8.5; outside this range is “DANGER.”  
  - 2.7.2 Opacity is “SAFE” below 25%; above 25% is “DANGER.”  
  - 2.7.3 Conductivity is “SAFE” between 0.5–3.0 µmhos/cm; outside is “DANGER.”  

### 3. Interactivity and UI/UX
- 3.1 The product should clearly indicate dangerous conditions using colors, lights, or universally understood symbols (P0).  
- 3.2 The product should adapt to user proficiency levels.  
  - 3.2.1 Include a simplified default interface (P0).  
  - 3.2.2 Provide an optional advanced data view (P2).  
- 3.3 The product should use minimal physical controls, relying on a menu-driven UI (P0).  
- 3.4 The display should remain readable in outdoor sunlight and low-light conditions (P0).  
- 3.5 Font and display sizes should be easily readable for all ages (P0).  
- 3.6 The interface should support future translation to other languages (P2).  

### 4. Customization
- 4.1 Schematics and case dimensions should be openly shared to allow user customization (P2).  

### 5. Manufacturing
- 5.1 The product must be compatible with both low-volume (3D printing, hand soldering) and high-volume (injection molding, reflow soldering) production methods (P0).  
- 5.2 Manufacturing must be safe and responsible (P1).  
- 5.3 PCB design must consider the capabilities of domestic U.S. PCB fabrication (P2).  

### 6. Safety
- 6.1 The exterior shall not have sharp edges (P1).  
- 6.2 The exterior shall not contain corrosive, carcinogenic, or toxic materials; internal materials requiring warnings must be labeled (P0).  
- 6.3 The product shall not emit harmful radiation (P0).  
- 6.4 The product shall be too large to swallow (P2).  
- 6.5 The product shall not emit noise above 18 dB during operation (P1).  
- 6.6 Users shall be protected from any moving parts (P1).  

---

## Requirement Criteria Specifications

| ID      | Requirement Description                                                        | Verification Method      | Priority |
|---------|--------------------------------------------------------------------------------|---------------------------|----------|
| 1.1.1   | Device radiation emissions ≤ IEC 60601 safety limits                            | Test & Certification      | P0       |
| 1.1.2   | Device exterior free from sharp edges & toxic materials                         | Inspection                | P0       |
| 1.1.3   | Hazardous conditions indicated through LED color codes                          | Demonstration              | P0       |
| 1.1.4   | Sensor data updated on UI within 200 ms                                         | Analysis/Test              | P1       |
| 1.1.5   | Calibration completes within 2 minutes after startup                            | Demonstration              | P1       |
| 1.1.6   | Display text height ≥ 5 mm at 30 cm viewing distance                            | Measurement                | P1       |
| 1.1.7   | Battery life ≥ 6 hours on a single charge                                       | Test                       | P1       |
| 1.1.8   | Device weight ≤ 500 g for portability                                           | Measurement                | P2       |
| 1.1.9   | Dimensions ≤ 15×10×5 cm for compact design                                      | Measurement                | P1       |
| 1.1.10  | Compatible with both 3D printing and injection molding manufacturing methods    | Inspection/Prototype       | P2       |

---

## Open Questions

- What chemicals, particulates, or contaminants should be included in future versions of the device?  
- Should the device prioritize ease of repairability or ease of replacement?  
- Are additional accessibility requirements needed for users with disabilities?  
- Final list of pollutants to detect?  
- Preferred battery chemistry (Li-ion vs LiPo)?  
- Should wireless connectivity be included or optional?  
- Which accessibility features should be incorporated into the UI?  

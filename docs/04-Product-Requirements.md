---
title: Product Requirements
tags:
- tag1
- Requirements
---

## Project Objectives
- Design an inexpensive water monitor
- Include multiple sensors for detection and measurement of harmful pollutants
- Reasonable scope of project so we can finish it on time
- Learn more about embedded systems, coding, sensors, focusing on smaller electronic devices rather than larger circuits
- While we will attempt to make a profit, our primary financial focus will be providing an inexpensive enviromental monitor


## Stakeholders

- **Manufactuers:** Balance high quality of product with low cost in an ethical manufacturing environment
- **Distributors** Utilize well-established supply lines to ship products to retailers and customers
- **Financiers:** Will need an entity with a large amount of captial that can finance getting the company off the ground
- **Retailers:** Sells product to the public and large entities interested in monitoring water quality
- **Customers:** Target customers who will have low income but higher risk of exposure to bad water quality
- **VibeWater:** Coordinate efforts between all stakeholders to maximize effectiveness of low-cost water quality monitor


## Use Cases

**User Story #1: Sarah**
Sarah is a 42-year-old mom who regularly takes her young children to a local park. Her family just recently moved to this town because her husband, Bob, got a new job at a nearby manufacturing plant that dumps it's waste into a nearby river. She's noticed her kids have started to cough more often than usual, but they don't appear to be sick. After doing some research, she found that regulations about pollution are more relaxed in this new town compared to the rest of the country. She decides that someone needs to start monitoring the water for harmful pollutants before someone becomes seriously ill. However, no one is willing to support her investigation and she doesn't have enough money to hire a professional.

Sarah finds a new water quality monitoring system that is easily affordable and decides to take it upon herself to monitor the water. She does not have any kind of technical background, so she normally wouldn't be able to understand what all of the water quality tests mean. This low-cost device allows her quickly and easily diagnose pollution issues that she can explain to her community. Her findings will not change regulations on their own, but the easy-to-understand readings will show her community the issues they are facing due to the relaxed regulations. She can use these findings to further her cause in updating the environmental regulations.

**User Story #2: Jimmy**
Jimmy is a 79-year-old retiree who has a number of medical issues. He is looking for a new apartment to rent, but he also has a fixed income. He is worried about the water quality of these apartments, so he wants to know whether the water supplied to these apartments is drinkable. He doesn't trust findings published by large entities, so he searches for a water monitoring device that he can bring with him everywhere he goes. This way he can test the water himself.

This inexpensive monitor allows him to check the tap water in apartments he views. Since Jimmy has a fixed income, he cannot afford a significant amount of repairs and his aging body prohibits him from doing super intensive repairs and tests with the device. The device can change it's screen brightness, font size and is easy to follow directions. The majority of product issues can be solved by simply replacing the batteries or turning the device off and back on again. Jimmy would be able to easily peform his environmental tests, repair his device and change his settings easily.

## Design Aspects & Priorities
Priorities have been standardized as follows:  
- **P0 = Critical (must-have)**  
- **P1 = Important (high-value)**  
- **P2 = Nice-to-have (optional)**  

1. **Hardware and Product Design**
      * 1.1 The hardware should be somewhat portable (P2)
      * 1.2 The hardware should be durable (P2)
      * 1.3 The hardware should be compact (P2)
  
2. **Software Functionality**
      * 2.1 The product shall offer high accuracy in it's measurement/warning data. (P0)
      * 2.2 The product shall include a calibration process to allow customers to be sure of their unit's accuracy due to any shipping/handling defects. (P0)
      * 2.3 The product's software shall be distributed as free software following the FSF's 4 freedoms of usage, study, sharing and modification. (P1)
        * 2.3.1 In the event that binary blobs are required, the user will be notified of these and the binaries will be made available. (P2)
      * 2.4 The product shall use a single statically-typed systems programming language only to improve reliability and performance. (P1)
      * 2.5 The product's software shall be designed for portability and POSIX compliance. (P2)
      * 2.6 The software source code will follow a single style/standards guide for consistency and readability.(P0)
        * 2.6.1 The Google C++ Style Guide will be used for C++ code
        * 2.6.2 The Linux Kernel Coding Style will be used for C code
        * 2.6.3 The Microsoft .NET Coding Conventions will be used for C# code
        * 2.6.4 An appropriate industry-recognized style guide will be used for Rust, Haskell, LISP, Lua, Java and any other language that may be chosen.
      * 2.7 All 3 sensors will define "SAFE" and 'DANGER" values for pH, opacity and conductivity.
        * 2.7.1 pH will be defined as being "SAFE" if it is measured to be between 6.5 and 8.5. Anywhere outside these boundaries will be considered "DANGER".
        * 2.7.2 Opacity will be defined as being "SAFE" if it is measured to be below 25%. Anything higher than 25% will be considered "DANGER".
        * 2.7.3 Conductivity will be defined as being "SAFE" if it is measured to be between 0.5 micromhos per centimeter and 3.0 micromhos per centimeter. Anywhere outside these boundaries will be considered "DANGER". 

3. **Interactivity and UI/UX**
      * 3.1 The product should clearly indicate a dangerous condition even if the user is unfamiliar with the measured values via colors, lights and/or other universally understood symbols. (P0)
      * 3.2 The product should be able to adapt to the user's proficiency and use-case level
        * 3.2.1 The product should feature a simplified default interface that does not display any extra or confusing data to the user (P0)
        * 3.2.2 The product should offer an optional advanced readout which shows all useful data collected for advanced users (P2)
      * 3.3 The product should require minimum amounts of physical controls to operate, relying on a menu-driven interface (P0)
      * 3.4 The UI and display hardware should be designed for readability in both outdoor direct-sunlight and low-light conditions (P0)
      * 3.5 The font and display size should be easily readable for all ages (P0)
      * 3.6 The interface should be designed in a manner that allows for easy translation to other languages in the future (P2)

4. **Customization**
      * 4.1 The product should allow for expandability of functions and packaging through releasing open schematics/dimensions for the casing (P2)

5. **Manufacturing**
      * 5.1 The product should be designed to be compatible with both low-volume hobbyist production methods (3d printing, through-hole soldering, hand tools) as well as high-volume manufacturing methods (injection molding, sheet metal, automated PNP systems, reflow or wave soldering, power/robotic tools) in order to facilitate a low-cost and accessible product (P0)
      * 5.2 The product's manufacturing should be safe and responsible (P1)
      * 5.3 The product shall be designed with the capabilities of domestic (USA) PCB fabs in mind (P2)
      
6. **Safety**
      * 6.1 The exterior of the product shall be free from sharp edges (P1)
      * 6.2 The exterior of the product shall be free from any corrosive, carcinogenic, or toxic materials. If such materials are included in the internals, an appropriate warning shall be affixed to the device. (P0)
      * 6.3 The product shall not emit any radiation above safe doses for children, including ionizing and laser radiation. (P0)
      * 6.4 The product shall be made in a size or shape that prevents swallowing by infants. (P2)
      * 6.5 The product shall not emit noise above 18 decibels during any mode of operation. (P1)
      * 6.6 The user's body shall be appropriately isolated or protected from any moving parts of the product. (P1)

## Requirement Criteria Specifications

| ID      | Requirement Description                                                        | Verification Method      | Priority |
|---------|--------------------------------------------------------------------------------|---------------------------|----------|
| 1.1.1   | Device radiation emissions ≤ IEC 60601 safety limits                            | Test & Certification      | P0       |
| 1.1.2   | Device exterior free from sharp edges & toxic materials                         | Inspection                | P0       |
| 1.1.3   | Hazardous conditions shown via LED color codes                                  | Demonstration              | P0       |
| 1.1.4   | Sensor data updated on UI within 200 ms                                         | Analysis/Test              | P1       |
| 1.1.5   | Calibration completes ≤ 2 min after startup                                     | Demonstration              | P1       |
| 1.1.6   | Display text height ≥ 5 mm at 30 cm viewing distance                            | Measurement                | P1       |
| 1.1.7   | Battery life ≥ 6 hours on single charge                                         | Test                       | P1       |
| 1.1.8   | Device weight ≤ 500 g for portability                                           | Measurement                | P2       |
| 1.1.9   | Dimensions ≤ 15×10×5 cm for compact design                                      | Measurement                | P1       |
| 1.1.10  | Compatible with both 3D printing & injection molding manufacturing methods      | Inspection/Prototype       | P2       |

## Open Questions

* What chemicals/gasses/particulates should be monitored?
* Should we make the device easy to repair or replace?
* Are there any disabilities we should account for when designing the user interaction?
* Final list of pollutants to detect?
* Target battery chemistry (Li-ion vs LiPo)?
* Wireless connectivity required or optional?
* Accessibility features for disabled users?
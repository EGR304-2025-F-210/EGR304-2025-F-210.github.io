---
title: Product Requirements
tags:
- tag1
- tag2
---

## Project Objectives
- Design an inexpensive enviromental monitor
- Include multiple sensors for detection and measurement of harmful pollutants
- Reasonable scope of project so we can finish it on time
- Learn more about embedded systems, coding, sensors, focusing on smaller electronic devices rather than larger circuits
- While we will attempt to make a profit, our primary financial focus will be providing an inexpensive enviromental monitor


## Stakeholders

- **Target group** People, students, families with low income that can not afford usual air, water quality monitors/testers. Also, universities and house renters of old houses are target audience for our product. 
- **Target purchaser** Target group profile with special attention to people who live near facilities that were built with asbestos and those who often have water with bacteria, microbes, nitrates, arsenic. We would like to focus for customers in Central and South Asia, Africa, Middle east since those countries have issues with humidity, bad air quality because of frequent dust and bad water quality.
- **Customer service** Prefers product with low repair need. The product has to be recyclable and easy-to-use  to fit with our intuitive user experience.
- **Marketing & Sales division** Looks for unique selling points around the bonoch-Explorer lifestyle and user experience.
- **Retailers** Prefer products that are very easy to use and very cheap in checking room temperature, humidity, and atmospheric pressure, CO2, TVOC, PM2.5 PM1.0 PM10, HCHO.


## Use Cases

**User Story #1: Sarah**
Sarah is a 42-year-old mom who regularly takes her young children to a local park. Her family just recently moved to this town because her husband, Bob, got a new job at a nearby manufacturing plant. She's noticed her kids have started to cough more often than usual, but they don't appear to be sick. After doing some research, she found that regulations about pollution are more relaxed in this new town compared to the rest of the country. She decides that someone needs to start monitoring the environment for harmful pollutants before someone becomes seriously ill. However, no one is willing to support her investigation and she doesn't have enough money to hire a professional.

Sarah finds a new enviromental monitoring system that is easily affordable and decides to take it upon herself to monitor the environment. This device only costs $100 and it allows her to quickly measure radon and particulate matter levels. It can also detect the presence of gasses such as hydrogen chloride, benzene and toluene or compounds and metals such as asbestos, cadmium, mercury and chromium. Armed with this information, Sarah plans to show the mayor, town council and other residents all of the things they are breathing in due to the relaxed pollution regulations.

**User Story #2: Jimmy**
Jimmy is a 79-year-old retiree who sometimes has trouble breathing. He is looking for a new apartment to rent, but he also has a fixed income. He hopes to avoid apartments built long ago, attempting to stay away from buildings that used asbestos during their construction. Landlords have done a good job making old buildings look like new ones, so he bought a new enviromental monitoring device to bring with him everywhere he goes.

This inexpensive monitor allows him to check the air in apartments he views for anything that would make breathing even harder for him. He can detect the presence of asbestos, carbon monoxide, particulate matter and large amounts of carbon dioxide. This allows Jimmy to be warned about apartments that he would struggle to live in and he appreciates how easy it is to use as well as being able to afford it on his fixed income.

## Aspects

The new product design will be based on that of the AirPods with improvements based on the following requirements. The **P1 - P10** is the "code" to indicate the priority of the requirement, from low to high.

1. **Hardware and Product Design**
      * 1.1 The product shall be visually easy to distinguish from existing water/air quality testers as well as main competitors MEXYBE, PERFORMANCE GURU, bonoch, Nanezan. (P10)
      * 1.1 The product shall be easy to recognize as an bonoch product without needing a logo on its exterior. (P10)
      * 1.2. The product shall avoid styling elements from our Powerbeats over-ear wireless headphones since those address a different market segment. (P8)
  
2. **Software Functionality**
      * 2.1 The product shall offer high accuracy in it's measurement/warning data. (P9)
      * 2.2 The product shall include a calibration process to allow customers to be sure of their unit's accuracy due to any shipping/handling defects. (P9)
      * 2.3 The product's software shall be distributed as free software following the FSF's 4 freedoms of usage, study, sharing and modification. (P6)
            * 2.4.1 In the event that binary blobs are required, the user will be notified of these and the binaries will be made available. (P1)
      * 2.4 The product shall use a single statically-typed systems programming language only to improve reliability and performance. (P6)
      * 2.5 The product's software shall be designed for portability and POSIX compliance. (P3)
      * 2.6 The software source code will follow the Google C++ Style Guide (irrespective of language choice) for consistency and readability. (P8)
3. **Interactivity and UI/UX**
      * 3.1 The product should clearly indicate a dangerous condition even if the user is unfamiliar with the measured values via colors, lights and/or other universally understood symbols. (P10)
      * 3.2 The product should be able to adapt to the user's proficiency and use-case level
            * 3.2.1 The product should feature a simplified default interface that does not display any extra or confusing data to the user (P9)
            * 3.2.2 The product should offer an optional advanced readout which shows all useful data collected for advanced users (P3)
      * 3.3 The product should require minimum amounts of physical controls to operate, relying on a menu-driven interface (P8)
      * 3.4 The UI and display hardware should be designed for readability in both outdoor direct-sunlight and low-light conditions (P9)
      * 3.5 The font and display size should be easily readable for all ages (P9)
      * 3.6 The interface should be designed in a manner that allows for easy translation to other languages in the future (P3)
4. **Customization**
      * 4.1 The product should allow for expandability of functions and packaging through releasing open schematics/dimensions for the casing (P1)
5. **Manufacturing**
      * 5.1 The product should be designed to be compatible with both low-volume hobbyist production methods (3d printing, through-hole soldering, hand tools) as well as high-volume manufacturing methods (injection molding, sheet metal, automated PNP systems, reflow or wave soldering, power/robotic tools) in order to facilitate a low-cost and accessible product (P9)
      * 5.2 The product's manufacturing should be safe and responsible (P6)
      * 5.3 The product shall be designed with the capabilities of domestic (USA) PCB fabs in mind (P6)
6. **Safety**
      * 6.1 The exterior of the product shall be free from sharp edges (P8)
      * 6.2 The exterior of the product shall be free from any corrosive, carcinogenic, or toxic materials. If such materials are included in the internals, an appropriate warning shall be affixed to the device. (P10)
      * 6.3 The product shall not emit any radiation above safe doses for children, including ionizing and laser radiation. (P10)
      * 6.4 The product shall be made in a size or shape that prevents swallowing by infants. (P7)
      * 6.5 The product shall not emit noise above 18 decibels during any mode of operation. (P7)
      * 6.6 The user's body shall be appropriately isolated or protected from any moving parts of the product. (P7)

## Requirement Criteria Specifications

* 1.1.1 - Regulate system power from 9 volts to 5 volts
* 1.1.2 - Provide over-amperage project to not exceed 1.5 amps.

## Open Questions

* What chemicals/gasses/particulates should be monitored?
* Should we make the device easy to repair or replace?
* Are there any disabilities we should account for when designing the user interaction?
---
title: Software Proposal
---

## Introduction
Our team utilizes a hub-and-spoke control/communication method for our project's software, with one subsystem (user input) acting as a motherboard to connect the other 3 sensor boards. The sensor boards can be arbitrarily attached to any of the 4 available headers, and can be removed or re-attached during operation.
The software proposal UML diagrams below are split into two sections, a state diagram representing the operation of the sensor boards, and an activity diagram representing the logic/operation of the controller board.
The main controller system utilizes the vector interrupt table on the PIC18F57Q43 MCU to handle concurrency and implement a fast-to-sleep design for power saving, allowing the CPU to be off when the display can remain on for idle usage. While currently not implemented, a idle shutdown feature could also be implemented utilizing interrupts. Our software design allows fast-to-sleep to be added in the future to each of the sensor boards as well in the same manner.

## Images

**Figure 1:** Sensors state diagram
![](Team210SoftwareProposal.png)

**Figure 2:** Controller activity diagram
![](ControllerSoftware.png)


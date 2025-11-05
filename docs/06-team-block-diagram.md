title: Group Block Diagram

**Figure 1:** Block Diagram
![](GroupBlockDiagram.png)

For individual subsystem/member block diagrams, please visit the individual datasheets.
The source file is available as a download [here](GroupBlockDiagram.drawio)

## Design Process

To design our block diagram, we focused on maximizing the independancy of our subsystems. We also focused on minimizing power rails, leading to all our systems outside the LCD and the power supplies operating within the 5V rail. We had to incorporate level shifters to supply logic to to our 3.3V LCD display, which necessitated a 3.3V power supply as well. We used a simple 2-lane header for UART data transmission between our boards to minimize the amount of data-carrying wires, which improves the reliability of our subsystem. 

## Requirements Conformity

Our team block diagram meets both our imposed requirements and the requirments of the project by providing a hub-and-spoke method for connection, a standard 9V unregulated power supply, 5V operation of the Curiosity Nano boards, 3 sensors and an actuator, all driven by custom circuitry and analog ICs, and debouncing our buttons. We meet our goals of testing water with the given 3 testing methods, as well as proving an intuitive and easy user interface.

## Signaling/Header Pin breakdown

The following table describes the connections between our team member subsystems:

| TX Pin # | TX Pin Label | TX Subsystem | RX Pin # | RX Pin Label | RX Subsystem | Signal type    | Data types          | Description                                                                                                    |
| -------- | ------------ | ------------ | -------- | ------------ | ------------ | -------------- | ------------------- | -------------------------------------------------------------------------------------------------------------- |
| 1N1      | sys_1_tx     | Neel         | 1A1      | hub_rx       | Asadbek      | Digital - UART | uint8               | Control signals from user interface, represented as a number between 1-4                                       |
| 1A2      | hub_tx       | Asadbek      | 1N1      | sys_1_rx     | Neel         | Digital - UART | uint8 (4 bit split) | Test results from sensor ( 4 bits), boolean safety value (1 bit), heartbeat signal (2 bits), parity bit        |
| 2N1      | sys_2_tx     | Neel         | 1K1      | Header_RX1   | K            | Digital - UART | uint8               | Control signals from user interface, represented as a number between 1-4                                       |
| 1K2      | Header_TX1   | K            | 2N2      | sys_2_rx     | Neel         | Digital - UART | uint8 (4 bit split) | Test results from sensor ( 4 bits), boolean safety value (1 bit), heartbeat signal (2 bits), parity bit        |
| 3N1      | sys_3_tx     | Neel         | 1J1      | hub_rx       | Jacob        | Digital - UART | uint8               | Control signals from user interface, represented as a number between 1-4                                       |
| 1J2      | hub_tx       | Jacob        | 3N2      | sys_3_rx     | Neel         | Digital - UART | uint8 (4 bit split) | Test results from sensor ( 4 bits), boolean safety value (1 bit), heartbeat signal (2 bits), parity bit        |
| 1N7      | 5V           | Neel         | 1A7      | 5V           | Asadbek      | power          | N/A                 | Shared power over headers. Can be switched to an analog signal input on Neel's subsystem header with a jumper. |
| 2N7      | 5V           | Neel         | 1K7      | 5V           | K            | power          | N/A                 | Shared power over headers. Can be switched to an analog signal input on Neel's subsystem header with a jumper. |
| 3N7      | 5V           | Neel         | 1J7      | 5V           | Jacob        | power          | N/A                 | Shared power over headers. Can be switched to an analog signal input on Neel's subsystem header with a jumper. |
| 1N8      | GND          | Neel         | 1A8      | GND          | Asadbek      | ground         | N/A                 | Synchronized ground                                                                                            |
| 2N8      | GND          | Neel         | 1K8      | GND          | K            | ground         | N/A                 | Synchronized ground                                                                                            |
| 3N8      | GND          | Neel         | 1J8      | GND          | Jacob        | ground         | N/A                 | Synchronized ground                                                                                            |
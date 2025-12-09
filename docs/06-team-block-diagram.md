# Group Block Diagram

**Figure 1:** Updated Team Block Diagram  
![](GroupBlockDiagram.png)

For individual subsystem/member block diagrams, please visit the individual datasheets.  
The source file is available as a download:  
[GroupBlockDiagram.drawio](GroupBlockDiagram.drawio)

---

## Design Process

The final block diagram was constructed to reflect the real physical and electrical design of the system. The architecture separates the project into four independent microcontroller subsystems, each connected through a standardized UART header interface and powered through a common 5V distribution rail, with each board also capable of regulating its own 9V input.

- **Neel’s subsystem** implements the user interface, including LCD display, debounced pushbuttons, a DAC-driven speaker, and global UART command routing.
- **Asadbek’s subsystem** performs conductivity measurement using zinc probes and an amplification stage.
- **K’s subsystem** performs optical LED sensing using a controlled light source and phototransistor detection with an amplification stage to evaluate water clarity.
- **Jacob’s subsystem** performs pH measurement using a pH probe and amplification stage..

The block diagram emphasizes consistency in power rails, communication reliability, and modularity. Each subsystem includes the required analog conditioning circuitry, debug interfaces, and connectors explicitly shown in the diagram.

---

## Requirements Conformity

The updated block diagram satisfies all system requirements.

### Communication Structure  
A hub-and-spoke UART communication model is used, with Neel’s subsystem controlling all test requests and receiving data packets returned from each sensing subsystem. The diagram reflects full-duplex UART lines for every connection pair, fulfilling the requirement for reliable, structured inter-module communication.

### Power Architecture  
The system uses a standardized 5V rail that can be shared between boards, and each subsystem also accepts 9V input for local regulation. This meets the requirement for a consistent and safe power delivery network.

### Sensing Requirements  
The system includes the three required water-sensing modalities: conductivity, optical LED sensing, and pH sensing. All analog front ends (op-amps, filters, and reference components) are included in the block diagram.

### User Interface  
Neel’s subsystem includes all required UI elements: LCD screen, pushbuttons, DAC, speaker, and debug LEDs. This satisfies the requirement for an intuitive and accessible interface.

### Modularity  
Each subsystem is fully self-contained, processes its own measurements, and communicates results upstream. This satisfies the modularity and subsystem independence requirements.

---

## Explanation of Each Block in the Block Diagram

### Shared Power System

**9V Unregulated Supplies**  
Each subsystem is capable of receiving a 9V input. The block diagram shows individual 9V sources to indicate independent operation and testing.

**5V Linear Regulators**  
Each board regulates 9V down to the standard 5V logic and sensor voltage used across the system.

**5V Rail Distribution**  
The 5V rail is shared over the subsystem headers, allowing optional power sharing.

**Common Ground**  
All subsystems share a synchronized ground reference, which is necessary for ADC accuracy and UART reliability.

---

## Neel Garde Subsystem (User Interface Hub)

**PIC18F57Q43 Microcontroller**  
Central controller for UI elements and coordination of test execution.

**Digital I/O (Pushbuttons + Debounce Circuits)**  
Implements user controls for navigation (Enter, Back, Up, Down). Debounce circuits ensure clean logic transitions.

**LCD Interface + Level Shifters**  
The LCD operates at 3.3V and requires level shifting from 5V signals. The LCD displays menus, test results, and system status.

**DAC and Speaker**  
Provides audible system feedback such as menu select tones and warnings.

**Debug LEDs**  
Indicate subsystem state, UART traffic, and user action confirmation.

**UART Interface**  
Communicates with each sensing subsystem using full-duplex TX/RX lines.

**Power Regulation Blocks**  
Show the subsystem’s local 9V-to-5V regulation and compatibility with the shared rail.

---

## Asadbek Ruziev Subsystem (Conductivity Sensing)

**PIC18F57Q43 Microcontroller**  
Controls probe excitation, ADC sampling, and UART data transmission.

**Zinc Probes**  
Measure conductivity based on ionic content in the water.

**Op-Amp (MCP6004)**  
Amplifies and conditions the probe output into a suitable range for ADC conversion.

**ADC Input**  
Digitizes the conditioned signal for analysis.

**Debug Buttons & LEDs**  
Assist in calibration and subsystem testing.

**UART Interface**  
Transmits conductivity results, safety flags, and heartbeat signals to Neel’s subsystem.

**Power Regulation Blocks**  
Show the subsystem’s ability to regulate 9V down to usable voltage levels.

---

## K Phang Subsystem (Optical LED Sensing)

**PIC18F57Q43 Microcontroller**  
Controls the illumination source, processes phototransistor readings, and ADC sampling, and UART data transmission..

**PWM-Controlled High-Power Green LED**  
Provides a controlled optical signal. PWM allows intensity adjustments during testing and calibration.

**Phototransistor + Resistor Network**  
Detects transmitted or scattered light to measure water clarity or turbidity.

**Analog Conditioning (Op-Amp / Filtering)**  
Scales and filters the phototransistor signal before digitization.

**ADC Input**  
Converts the conditioned optical reading into digital form.

**Debug LED & Button**  
Used for subsystem diagnostics and calibration routines.

**UART Interface**  
Transmits clarity measurements and safety data back to Neel.

**Power Regulation Blocks**  
Show 9V-to-5V regulation and compatibility with the shared rail.

---

## Jacob Andrus Subsystem (pH Sensing)

**PIC18F57Q43 Microcontroller**  
Handles pH measurement processing, ADC sampling, and UART data transmission..

**pH Probe**  
Outputs a small analog voltage proportional to the water’s hydrogen ion concentration.

**Analog Front-End (Op-Amp, Filtering, Reference Components)**  
Amplifies and conditions the probe’s millivolt-level signal into an ADC-readable range.

**ADC Input**  
Digitizes the conditioned pH signal.

**Debug Button & LED Indicators**  
Assist with calibration, testing, and verifying subsystem operation.

**UART Interface**  
Returns pH measurement data, safety flags, and heartbeat signals to Neel’s subsystem.

**Power Regulation Blocks**  
Show local regulation from the 9V input and integration with the shared 5V system.

---

## Signaling / Header Pin Breakdown

| TX Pin # | TX Pin Label | TX Subsystem | RX Pin # | RX Pin Label | RX Subsystem | Signal type    | Data types          | Description                                                                                                    |
| -------- | ------------ | ------------ | -------- | ------------ | ------------ | -------------- | ------------------- | -------------------------------------------------------------------------------------------------------------- |
| 1N1      | sys_1_tx     | Neel         | 1A1      | hub_rx       | Asadbek      | Digital - UART | uint8               | Control signals from UI subsystem (1–4).                                                                       |
| 1A2      | hub_tx       | Asadbek      | 1N2      | sys_1_rx     | Neel         | Digital - UART | uint8 (4-bit split) | Test results, safety flag, heartbeat, parity.                                                                  |
| 2N1      | sys_2_tx     | Neel         | 1K1      | Header_RX1   | K            | Digital - UART | uint8               | Control signals from UI subsystem (1–4).                                                                       |
| 1K2      | Header_TX1   | K            | 2N2      | sys_2_rx     | Neel         | Digital - UART | uint8 (4-bit split) | Test results, safety flag, heartbeat, parity.                                                                  |
| 3N1      | sys_3_tx     | Neel         | 1J1      | hub_rx       | Jacob        | Digital - UART | uint8               | Control signals from UI subsystem (1–4).                                                                       |
| 1J2      | hub_tx       | Jacob        | 3N2      | sys_3_rx     | Neel         | Digital - UART | uint8 (4-bit split) | pH results, safety flag, heartbeat, parity.                                                                    |
| 1N7      | 5V           | Neel         | 1A7      | 5V           | Asadbek      | power          | N/A                 | Shared 5V power rail.                                                                                          |
| 2N7      | 5V           | Neel         | 1K7      | 5V           | K            | power          | N/A                 | Shared 5V power rail.                                                                                          |
| 3N7      | 5V           | Neel         | 1J7      | 5V           | Jacob        | power          | N/A                 | Shared 5V power rail.                                                                                          |
| 1N8      | GND          | Neel         | 1A8      | GND          | Asadbek      | ground         | N/A                 | Common ground.                                                                                                 |
| 2N8      | GND          | Neel         | 1K8      | GND          | K            | ground         | N/A                 | Common ground.                                                                                                 |
| 3N8      | GND          | Neel         | 1J8      | GND          | Jacob        | ground         | N/A                 | Common ground.                                                                                                 |


## Old Signaling/Header Pin breakdown

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
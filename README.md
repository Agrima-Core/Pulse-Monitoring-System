# Pulse Rate Monitoring System using LM358 IC
 
A simple, low-cost, and portable analog circuit that detects human pulse activity using an optical pulse sensor and the LM358 operational amplifier. 
 
---
## Circuit Diagram
<img width="1250" height="867" alt="image" src="https://github.com/user-attachments/assets/ceb02962-e156-49d6-b0fb-f6a87a42abcf" />




 ## Bread-Board Implementation
 <img width="446" height="625" alt="image" src="https://github.com/user-attachments/assets/cf7fc803-92e9-4f74-9734-b82c713171fa" />


 
 ## Artium design and Schamatic
 <img width="446" height="625" alt="image" src="https://github.com/user-attachments/assets/707fa514-83f6-4728-afe2-c2c01f7520ff" />

 

## PCB Fabrication 
<img width="446" height="625" alt="image" src="https://github.com/user-attachments/assets/e7ad1a02-7308-4268-866b-f08867f30a21" />



---
 
## Table of Contents
 
- [Abstract](#abstract)
- [Introduction](#introduction)
- [Objectives](#objectives)
- [Block Diagram](#block-diagram)
- [Hardware Components Used](#hardware-components-used)
- [Circuit Diagram](#circuit-diagram)
- [Working Principle](#working-principle)
- [Hardware Implementation](#hardware-implementation)
- [Applications](#applications)
- [Advantages](#advantages)
- [Limitations](#limitations)
- [Result](#result)
- [Conclusion](#conclusion)
---
 
## Abstract
 
This project presents the design and implementation of a Pulse Rate Monitoring System using the LM358 operational amplifier. A pulse sensor detects variations in blood flow when a finger is placed on it, producing a weak analog signal. The LM358 amplifies this signal, which is then processed through an op-amp based full-wave rectifier and filter circuit to obtain a stable voltage proportional to the pulse waveform. A comparator stage with an adjustable reference voltage detects when the signal crosses a threshold, activating an LED indicator. The circuit is powered by a regulated 5V supply derived from a 9V battery, using only discrete components — making it compact, reliable, and low-cost.
 
---
 
## Introduction
 
Pulse rate is one of the primary indicators of cardiovascular health, providing insight into a person's physical activity level, stress, and fatigue. Traditional manual measurement (palpation) is time-consuming and unsuitable for continuous monitoring.
 
This system uses an **optical pulse sensor**: infrared light passes through the finger, and the amount of reflected light changes slightly with each heartbeat due to variation in blood volume. This produces a weak, noisy electrical signal that requires **signal conditioning** — amplification, rectification, filtering, and threshold detection — before it can be used for indication. The LM358 op-amp is used across multiple stages of this conditioning pipeline.
 
---
 
## Objectives
 
1. Design and implement a pulse detection circuit using the LM358 operational amplifier.
2. Detect variations in blood flow using a pulse sensor and convert them into electrical signals.
3. Study the acquisition of weak biomedical signals and the need for signal conditioning.
4. Amplify low-amplitude analog signals using an op-amp.
5. Implement an op-amp based full-wave rectifier to utilize both halves of the pulse waveform.
6. Remove noise and smooth the rectified signal using filter capacitors.
7. Design a comparator circuit for threshold-based pulse detection.
8. Indicate pulse presence using an LED.
9. Use a voltage regulator to provide a stable power supply to analog circuits.
10. Analyze the effect of resistor/capacitor values on circuit performance and response time.
11. Gain hands-on experience in circuit design, breadboard implementation, testing, and troubleshooting.
12. Study analog circuit behavior in real-time biomedical applications.
13. Observe practical limitations such as noise, delay, and signal fluctuation in biological signal measurement.
---
 
## Block Diagram
 
```
Power Supply (9V Battery)
        │
        ▼
Voltage Regulator (7805 – 5V Supply)
        │
        ▼
Pulse Sensor / IR Sensor (Signal Acquisition)
        │
        ▼
Amplifier (LM358 Op-Amp Gain Stage)
        │
        ▼
Full Wave Rectifier (Op-Amp + Diodes)
        │
        ▼
Filter Circuit (Smoothing Capacitor)
        │
        ▼
Comparator (LM358 Threshold Detector)
        │
        ▼
Indicator (LED / Buzzer Output)
```
 
---
 
## Hardware Components Used
 
| S. No. | Component | Specification / Value | Quantity |
|---|---|---|---|
| 1 | Operational Amplifier IC | LM358 | 2 |
| 2 | Pulse Sensor / IR Sensor | Heartbeat detection sensor | 1 |
| 3 | Voltage Regulator | 7805 (5V Regulator) | 1 |
| 4 | Diodes | 1N4148 Signal Diode | 2 |
| 5 | Resistor | 100 kΩ | 1 |
| 6 | Resistor | 10 kΩ | 2 |
| 7 | Resistor | 330 Ω / 1 kΩ (LED current limiting) | 1 |
| 8 | Potentiometer | 10 kΩ Variable Resistor | 1 |
| 9 | Capacitor (Electrolytic) | 10 µF | 1 |
| 10 | Capacitor (Electrolytic) | 100 µF | 1 |
| 11 | LED | Red LED Indicator | 1 |
| 12 | Battery | 9V Battery | 1 |
| 13 | Breadboard / PCB | General purpose | 1 |
| 14 | Connecting Wires | Jumper wires | As required |
 
---
 
## Circuit Diagram
 
The circuit consists of:
- **U1 (7805):** Regulates 9V battery input to a stable 5V supply, with filter capacitors C1 (100 µF) and C2 (10 µF) for supply smoothing.
- **U2:A (LM358):** First-stage amplifier for the weak pulse sensor signal, with gain set by R1 (100 kΩ) and R2 (10 kΩ).
- **U2:B (LM358) + D1/D2 (1N4007) + C3 (10 µF):** Full-wave rectifier and filter stage.
- **RV1 (10 kΩ Potentiometer):** Sets the comparator's reference/threshold voltage.
- **U3:A (LM358):** Comparator stage — output drives LED D3 through current-limiting resistor R3 (10 kΩ).
*(See circuit schematic and PCB layout in the project report.)*
 
---
 
## Working Principle
 
1. **Signal Acquisition:** When a finger is placed on the pulse sensor, infrared light penetrates the skin and is partially reflected by blood vessels. Blood volume changes with each heartbeat, altering the intensity of reflected light — the sensor converts this into a weak analog electrical signal.
2. **Amplification:** The raw signal is too small and noisy to use directly. The first LM358 stage amplifies it to a usable magnitude.
3. **Full-Wave Rectification:** The amplified signal (containing both positive and negative variations) is passed through an op-amp based full-wave rectifier, converting it into a single-polarity waveform and improving detection sensitivity.
4. **Filtering:** A capacitor filter smooths the rectified waveform, removing noise and producing a stable, slowly varying voltage proportional to pulse activity.
5. **Threshold Detection (Comparator):** The filtered signal is compared against a reference voltage set via a 10 kΩ potentiometer. When the pulse signal exceeds this threshold, the comparator output goes high.
6. **Indication:** The comparator's high output turns ON the LED, signaling detection of a heartbeat. A small delay is observed due to the RC time constant of the filter capacitor — this is expected behavior.
---
 
## Hardware Implementation
 
- Circuit powered by a 9V battery, regulated to a stable 5V via a 7805 regulator (with smoothing capacitors to remove supply fluctuations).
- Pulse sensor positioned for consistent finger contact; output fed into the first LM358 amplifier stage with resistor values chosen for adequate gain.
- Amplified signal passed through a full-wave rectifier (diodes + op-amp) and filter capacitor.
- Filtered signal fed to the second LM358 stage, configured as a comparator with a 10 kΩ potentiometer setting the adjustable reference/threshold.
- Comparator output drives an LED through a current-limiting resistor.
- Circuit was first tested and verified on a **breadboard**, then implemented on a **PCB**.
- Sensitivity is adjustable via the potentiometer; stable operation was observed when the sensor was properly placed and external light interference minimized.
---
 
## Applications
 
1. Basic heart rate monitoring in homes and clinics.
2. Preliminary health checkups to verify pulse presence.
3. Fitness and exercise monitoring during workouts and recovery.
4. First-aid and emergency situations to check whether a person has a pulse.
5. Elderly care and patient observation for periodic pulse monitoring.
6. Educational tool for understanding biomedical signal processing and analog electronics.
7. Laboratory demonstrations in electronics/biomedical engineering.
8. Stress and fatigue indication based on pulse variation.
9. Foundation for wearable and portable health monitoring devices.
---
 
## Advantages
 
- Simple circuit design using easily available components.
- Low cost and economical to build.
- Portable and battery operated.
- Low power consumption.
- Quick visual indication of pulse activity.
- Adjustable sensitivity via potentiometer.
- Easy to assemble, troubleshoot, and repair.
- Reinforces practical understanding of op-amps, rectifiers, filters, and comparators.
- Suitable for educational and lab demonstration purposes.
---
 
## Limitations
 
- Does not display exact heart rate in BPM (beats per minute).
- Accuracy depends on proper finger placement.
- Finger movement can cause incorrect indication.
- Small delay due to capacitor charging/discharging.
- External light and electrical noise may affect performance.
- Not suitable for professional medical diagnosis.
- Detection may vary between individuals due to differing pulse strength.
---
 
## Result
 
The Pulse Rate Monitoring System was successfully designed and implemented. When a finger was placed on the sensor, the circuit detected blood-flow variations and produced a corresponding electrical signal. This signal was amplified, rectified, filtered, and compared against a reference voltage — the LED indicator turned ON whenever the pulse signal crossed the threshold, confirming successful pulse detection. The circuit operated reliably on a regulated 5V supply derived from a 9V battery, with sensitivity tuned via the potentiometer.
 
---
 
## Conclusion
 
The Pulse Rate Monitoring System using the LM358 operational amplifier was successfully developed and tested, demonstrating the practical application of analog electronics in biomedical signal processing. The weak pulse signal was effectively amplified, processed, and converted into a visible LED indication via a comparator stage.
 
While the system does not provide a numerical BPM readout, it reliably indicates pulse activity and serves as a valuable educational and demonstration tool. The design is simple, economical, and portable, and can be extended in future work with **microcontrollers, digital displays, and wireless communication** for more advanced health-monitoring applications.
 
---
 ## Team
 
- Mehak Gupta (24116058)
- Agrima Adarsh (24116006)
**Branch:** ECE | **Semester:** 4th
**Project Supervisor:** Dr. Mayur Katwe, Dept. of ECE, NIT Raipur
*Department of Electronics and Communication Engineering, National Institute of Technology, Raipur*
 

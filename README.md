# IoT-Based Hand Rehabilitation Support System


<table>
  <tr>
    <td><img src=""https://github.com/user-attachments/assets/abf14948-dd71-494b-a9e0-fb750cf124be" alt="Robotic Glove Concept" width="500"/></td>
    <td><img src="https://github.com/user-attachments/assets/380ff9c8-cc43-4be5-acfe-ae3113b47555" alt="System Architecture" width="500"/></td>
  </tr>
  <tr>
    <td align="center"><em>Robotic Glove — Finger Actuation Concept</em></td>
    <td align="center"><em>System Architecture & Workflow</em></td>
  </tr>
</table>


An IoT-based rehabilitation support system built using ESP32, Servo Motor, and an embedded web interface to perform simple hand therapy exercises wirelessly.

This project is designed as a prototype for finger/hand rehabilitation assistance, where a servo motor performs controlled repetitive movements based on the selected exercise mode.

## Project Context

This repository is **Lehar Savla's contribution** to a larger group project — *Hand Rehabilitation using Robotic Glove* 

| Component | Who built it | In this repo? |
|---|---|---|
| ESP32 firmware + web server | Lehar Savla | ✅ Yes |
| Servo motor integration & rehab motion logic | Lehar Savla | ✅ Yes |
| Embedded HTML/CSS exercise control interface | Lehar Savla | ✅ Yes (inside `.ino`) |
| Python GUI — fixed exercise control panel | Teammate (rebuilt from above) | ❌ No |
| Python GUI — finger angle detection (MediaPipe + OpenCV) | Teammate | ❌ No |

The embedded HTML/CSS interface in this repo was the **original working control interface** for the project. The teammate's Python GUI exercise control panel was built subsequently, based on this foundation.

The MediaPipe + OpenCV finger angle detection module is a separate computer vision component developed by a teammate and is not part of this repository.

## Project Overview

This system uses an ESP32 microcontroller to host a local web server. When connected to the same Wi-Fi network, the user can open the ESP32's IP address in a browser and control the rehabilitation exercises through simple on-screen buttons.

The servo motor then performs predefined exercise motions such as:

- Full bend and release
- Partial bend and release
- Hold-and-release movement

This project can serve as a basic rehabilitation prototype and can be further extended into a multi-finger smart rehab glove.

## Features

- Wi-Fi Controlled
- Built-in Web Interface (HTML/CSS served directly from ESP32)
- Servo-Based Finger/Hand Motion
- 3 Predefined Rehabilitation Exercises
- Emergency STOP Button
- Safe Servo Angle Limiting
- Automatic Reset After Exercise

## Hardware Used

- ESP32 Development Board
- Servo Motor
- Jumper Wires
- 5V Power Supply
- Breadboard
- 
## Software / Libraries Used

- Arduino IDE
- `WiFi.h`
- `WebServer.h`
- `ESP32Servo.h`
- 
## Working Principle

1. The ESP32 connects to a Wi-Fi network.
2. It creates a web server and hosts a simple control page (HTML/CSS embedded in firmware).
3. The user opens the ESP32 IP address in a browser.
4. The user selects one of the rehabilitation exercises.
5. Based on the selected mode, the servo motor performs a predefined repetitive motion.
6. The user can press STOP anytime to immediately interrupt the movement.

## Rehabilitation Modes

**Exercise 1 — Full Range Motion**  
The servo moves between the safe minimum and maximum angles repeatedly.

**Exercise 2 — Partial Range Motion**  
The servo moves between a mid-angle and the minimum angle for controlled motion.

**Exercise 3 — Hold and Release**  
The servo moves to the maximum angle, holds for a longer duration, and then returns.

Each exercise is repeated 10 times by default.

## Safety Features

To avoid mechanical stress or unsafe movement:

- Servo motion is restricted between **30° (minimum)** and **90° (maximum)**
- A STOP command can interrupt the exercise at any time


## Python GUI (Teammate's Component)

The project also includes a Python-based desktop GUI developed by a teammate that communicates with the ESP32 over Wi-Fi. It consists of three separate windows:

**Window 1 — Custom Speed Control**  
Allows the user to manually set the servo motor speed using a slider. The servo sweeps from 0° to 90° at the selected speed, giving therapists fine-grained control over motion intensity.

**Window 2 — Preset Exercise Control**  
Contains the same 3 predefined rehabilitation exercises as the embedded interface (full range, partial range, hold and release). Exercises can be triggered directly from the GUI, which sends the corresponding commands to the ESP32 over Wi-Fi.

**Window 3 — Finger Angle Detection**  
Uses a live camera feed processed through MediaPipe and OpenCV to detect finger bending angle in real time. This allows the system to measure actual finger movement during rehabilitation, providing visual feedback on the patient's progress.

> This GUI is not included in this repository. It was built separately by a teammate in Python.


## Future Extensions

- Multi-finger control with independent servo channels
- Serial command interface as an alternative to Wi-Fi control
- Sensor feedback for real-time finger position tracking
- Integration of GUI angle detection with automated exercise triggering

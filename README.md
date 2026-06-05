# IoT-Based Hand Rehabilitation Support System


An IoT-based rehabilitation support system built using ESP32, Servo Motor, and an embedded web interface to perform simple hand therapy exercises wirelessly.

This project is designed as a prototype for finger/hand rehabilitation assistance, where a servo motor performs controlled repetitive movements based on the selected exercise mode.

## Project Context

This repository contains **Lehar Savla's contribution** to a larger group project — *Hand Rehabilitation using Robotic Glove* — developed as part of  project in Electronics & Telecommunication Engineering.

**Full team:** Lehar Savla, Kashyap Dattani, Manav Bosmiya, Pranita Kakirde | **Guide:** Prof. Ameya Kadam

This repo covers the ESP32 firmware, servo control logic, and the embedded HTML/CSS exercise control interface served directly from the microcontroller. The full group project additionally includes a Python GUI with finger angle detection using MediaPipe and OpenCV, developed by teammates and not part of this repository.
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

- Servo motion is restricted between **30° (minimum)** and **140° (maximum)**
- A STOP command can interrupt the exercise at any time

## Future Extensions

- Multi-finger control with independent servo channels
- Serial command interface for external GUI control
- Sensor feedback for real-time finger position tracking
- Integration with computer vision for gesture-based exercise triggering

  <img width="1043" height="695" alt="image" src="https://github.com/user-attachments/assets/bdf4d823-8774-45aa-9d97-bd519d06be60" />

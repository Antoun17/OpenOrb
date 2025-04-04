# OpenOrb

![OpenOrb Logo](https://i.ibb.co/DDrHsK5C/image.jpg) 

**OpenOrb** is an open-source project based around the Litter Robot 3 using an ESP32 microcontroller. The inspiration for this project came from https://github.com/xtrium-lnx/litter-eater and while his project does work I needed a simpler implementation as my issues with the Litter Robot 3 are due to malfunctioning sensors. 

This project avoids those sensor issues by simply being a web-based motor controller to manage the motor direction. Instead of a hall sensor to control motor direction simple timings are usted to run the sifiting cycle. This projet utilzies a simmple web portla to adjust these timings and run the cycle. This also allows for fine tuning of the motor and directial control at any time.
---

## Features

- **Web Interface**: Control the Litter Robot 3 via a mobile-friendly web portal.
- **Customizable Cycle Timings**: Adjust cleaning cycle durations (backward, wait, forward, overshoot, return) using sliders.
- **mDNS Support**: Access the device using a consistent hostname (`http://litter-robot-upper.local`) even if the IP changes.
- **Motor Control**: Drive the Litter Robot’s orb using an L298N motor driver connected to the ESP32.
- **Open Source**: Fully open-source under the MIT License, encouraging contributions and modifications.

---

## Hardware Requirements

- **ESP32 Microcontroller**: Any ESP32 development board (e.g., ESP32 Dev Module).
- **L298N Motor Driver**: To control the Litter Robot’s motor.
- **Litter Robot**: A compatible Litter Robot unit (e.g., Litter Robot 3) with manual homing capability.
- **Power Supply**: Suitable power for the ESP32 and motor driver (e.g., 5V for ESP32, 12V for the motor).

### Pin Connections
| ESP32 Pin | L298N Pin |
|-----------|-----------|
| GPIO5     | ENA       |
| GPIO18    | IN1       |
| GPIO19    | IN2       |

---

## Software Requirements

- **Arduino IDE**: For compiling and uploading the code.
- **ESP32 Board Support**: Install the ESP32 board package in the Arduino IDE.
- **Libraries**:
  - `ESPAsyncWebServer` (by Hristo Gochkov)
  - `AsyncTCP` (by Hristo Gochkov)
  - `LittleFS` (built-in with ESP32)
  - `ArduinoOTA` (built-in with ESP32)
  - `ESPmDNS` (built-in with ESP32)
  - `AsyncElegantOTA` (by Hristo Gochkov)

To install libraries:
1. Open the Arduino IDE.
2. Go to **Sketch > Include Library > Manage Libraries**.
3. Search for each library and click **Install**.

---

## Installation

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/OpenOrb.git
cd OpenOrb

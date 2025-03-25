OpenOrb
 <!-- Replace with the actual path to your logo once created -->

OpenOrb is an open-source project to control a Litter Robot using an ESP32 microcontroller. It provides a web-based interface to manage the cleaning cycle, adjust timings, and perform OTA (Over-The-Air) updates for both firmware and the web portal. The project uses mDNS for easy access (e.g., http://litter-robot-upper.local) and includes features like motor control, cycle timing adjustments, and a user-friendly web interface.

This project is ideal for DIY enthusiasts, pet owners, and developers looking to customize or automate their Litter Robot with modern IoT capabilities.

Features
Web Interface: Control the Litter Robot via a mobile-friendly web portal.
Customizable Cycle Timings: Adjust cleaning cycle durations (backward, wait, forward, overshoot, return) using sliders.
OTA Updates: Update both firmware and the web portal (LittleFS) wirelessly using AsyncElegantOTA.
mDNS Support: Access the device using a consistent hostname (http://litter-robot-upper.local) even if the IP changes.
Motor Control: Drive the Litter Robot’s orb using an L298N motor driver connected to the ESP32.
Open Source: Fully open-source under the MIT License, encouraging contributions and modifications.
Hardware Requirements
ESP32 Microcontroller: Any ESP32 development board (e.g., ESP32 Dev Module).
L298N Motor Driver: To control the Litter Robot’s motor.
Litter Robot: A compatible Litter Robot unit (e.g., Litter Robot 3) with manual homing capability.
Power Supply: Suitable power for the ESP32 and motor driver (e.g., 5V for ESP32, 12V for the motor).
Pin Connections
ESP32 Pin	L298N Pin
GPIO5	ENA
GPIO18	IN1
GPIO19	IN2
Software Requirements
Arduino IDE: For compiling and uploading the code.
ESP32 Board Support: Install the ESP32 board package in the Arduino IDE.
Libraries:
ESPAsyncWebServer (by Hristo Gochkov)
AsyncTCP (by Hristo Gochkov)
LittleFS (built-in with ESP32)
ArduinoOTA (built-in with ESP32)
ESPmDNS (built-in with ESP32)
AsyncElegantOTA (by Hristo Gochkov)
To install libraries:

Open the Arduino IDE.
Go to Sketch > Include Library > Manage Libraries.
Search for each library and click Install.
Installation
1. Clone the Repository
bash

Collapse

Wrap

Copy
git clone https://github.com/yourusername/OpenOrb.git
cd OpenOrb
2. Set Up the Web Interface
The web interface is stored in the data folder as index.html.
Place your index.html file in the data folder within the project directory:
text

Collapse

Wrap

Copy
OpenOrb/
├── OpenOrb.ino
└── data/
    └── index.html
If you don’t have an index.html, use the provided example in this repository.
3. Upload the Code and Filesystem
Open OpenOrb.ino in the Arduino IDE.
Update the Wi-Fi credentials in the code:
cpp

Collapse

Wrap

Copy
const char* ssid = "YourSSID";
const char* password = "YourPassword";
Upload the firmware via USB:
Go to Tools > Board and select your ESP32 board.
Go to Tools > Port and select your ESP32’s port.
Click Upload.
Upload the LittleFS filesystem:
Go to Tools > ESP32 LittleFS Data Upload to upload the contents of the data folder (e.g., index.html).
4. Access the Web Interface
After uploading, the ESP32 will connect to your Wi-Fi network.
Open a browser and go to http://litter-robot-upper.local to access the web portal.
If mDNS doesn’t work, check the Serial Monitor for the IP address (e.g., 192.168.1.179) and use that instead (e.g., http://192.168.1.179).
Usage
Web Interface
The web portal provides the following controls:

Control Buttons:
Start Forward: Manually rotate the orb forward.
Start Backward: Manually rotate the orb backward.
Stop: Halt the motor and any running cycle.
Start Cycle: Run a full cleaning cycle (backward, wait, forward, overshoot, return).
Timing Sliders:
Adjust the duration of each cycle phase (e.g., Backward Duration, Wait Duration).
Values are updated in real-time and applied to the next cycle.
Update Firmware/Filesystem:
Click the "Update Firmware/Filesystem" button to access the OTA update page (http://litter-robot-upper.local/update).
Upload new firmware or LittleFS images as needed.
OTA Updates
Firmware Updates:
In the Arduino IDE, select the network port (e.g., "litter-robot-upper at 192.168.x.x") under Tools > Port.
Upload new firmware wirelessly.
LittleFS Updates:
Generate a LittleFS .bin file:
Place updated files (e.g., index.html) in the data folder.
Go to Tools > ESP32 LittleFS Data Upload to generate the .bin file.
Access http://litter-robot-upper.local/update.
Upload the .bin file under the "Filesystem Update" section.
Code Structure
OpenOrb.ino: Main sketch with ESP32 setup, motor control, and web server logic.
data/index.html: Web interface for controlling the Litter Robot.
Libraries:
ESPAsyncWebServer and AsyncTCP: For the asynchronous web server.
LittleFS: For storing and serving the web interface.
ArduinoOTA: For firmware OTA updates.
ESPmDNS: For mDNS support (litter-robot-upper.local).
AsyncElegantOTA: For OTA updates of both firmware and LittleFS.
Contributing
Contributions are welcome! To contribute:

Fork the repository.
Create a new branch (git checkout -b feature/your-feature).
Make your changes and commit (git commit -m "Add your feature").
Push to your branch (git push origin feature/your-feature).
Open a Pull Request.
Please ensure your code follows the project’s style and includes appropriate documentation.

License
This project is licensed under the MIT License. See the  file for details.

# ESP32-CAM Smart Wi-Fi Camera Node

## 📌 Project Overview

This project implements a **Smart Wi-Fi Camera Node** using the **ESP32-CAM** module.
The system captures real-time images/video and hosts a web server so users can monitor the live feed remotely through a browser or mobile device.

The project demonstrates:

* IoT-based surveillance
* Embedded systems programming
* Wi-Fi communication
* Real-time video streaming
* Camera interfacing using ESP32-CAM

---

# 🚀 Features

* 📷 Real-time video streaming using ESP32-CAM
* 🌐 Wi-Fi enabled remote monitoring
* 🖥️ Web server hosted on ESP32
* 📺 OLED display for system status
* ⚡ Low-cost and compact IoT surveillance system
* 🔌 UART programming using FT232R USB-to-Serial module
* 📡 MJPEG streaming over HTTP

---

# 🛠️ Hardware Components

| Component                      | Quantity  | Purpose                           |
| ------------------------------ | --------- | --------------------------------- |
| ESP32-CAM (AI Thinker)         | 1         | Main controller and camera module |
| OV2640 Camera                  | 1         | Image/video capture               |
| FT232R USB-to-Serial Converter | 1         | Uploading code to ESP32-CAM       |
| OLED Display SSD1306 (0.96")   | 1         | Display system status             |
| Breadboard                     | 1         | Prototyping                       |
| Jumper Wires                   | As needed | Connections                       |

---

# 🔧 Software Requirements

## Required Software

* Arduino IDE
* ESP32 Board Package
* FTDI Drivers
* Required Arduino Libraries:

  * `WiFi.h`
  * `esp_camera.h`
  * `Wire.h`
  * `Adafruit_GFX`
  * `Adafruit_SSD1306`

---

# 📥 Arduino IDE Setup

## Step 1 — Install Arduino IDE

Download and install Arduino IDE:
https://www.arduino.cc/en/software

---

## Step 2 — Install ESP32 Board Package

Open:

* `File > Preferences`

Add this URL inside **Additional Boards Manager URLs**:

```txt
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
```

Now open:

* `Tools > Board > Boards Manager`

Search:

```txt
ESP32
```

Install:

```txt
esp32 by Espressif Systems
```

---

## Step 3 — Select Board

Go to:

```txt
Tools > Board > AI Thinker ESP32-CAM
```

Set:

```txt
Upload Speed: 115200
Flash Frequency: 40MHz
Partition Scheme: Huge APP
```

---

# 🔌 FT232R to ESP32-CAM Connections

| FT232R Pin | ESP32-CAM Pin    |
| ---------- | ---------------- |
| VCC (3.3V) | 3.3V             |
| GND        | GND              |
| TX         | U0R (GPIO3 / RX) |
| RX         | U0T (GPIO1 / TX) |
| GND        | IO0              |

⚠️ IMPORTANT:

* Set FT232R to **3.3V**
* Connect **IO0 to GND** while uploading code
* Remove IO0 from GND after upload and reset board

---

# 📺 OLED Connections

| OLED Pin | ESP32-CAM Pin |
| -------- | ------------- |
| SDA      | GPIO13        |
| SCL      | GPIO14        |
| VCC      | 3.3V          |
| GND      | GND           |

---

# 📂 Project Structure

```txt
ESP32-CAM-Smart-Wifi-Node/
│
├── Code.ino
├── app_httpd.cpp
├── README.md
├── circuit-diagram.png
└── project-report.pdf
```

---

# 💻 What the Code Does

The firmware performs the following operations:

1. Initializes OLED display
2. Initializes OV2640 camera
3. Connects ESP32 to Wi-Fi
4. Starts HTTP web server
5. Captures image frames
6. Streams MJPEG video to browser
7. Displays IP address on OLED

---

# 🌐 Accessing the Camera Stream

After uploading the code:

1. Open Serial Monitor
2. Wait for Wi-Fi connection
3. Note the IP address shown on OLED/Serial Monitor
4. Open browser and visit:

```txt
http://<ESP32_IP_ADDRESS>
```

Example:

```txt
http://192.168.1.100
```

You can now:

* View live stream
* Capture images
* Monitor remotely

---

# 📷 Streaming Workflow

```txt
Camera → Frame Buffer → HTTP Server → Wi-Fi → Browser
```

---

# ⚡ Technical Specifications

| Specification     | Details              |
| ----------------- | -------------------- |
| Processor         | Dual-core Xtensa LX6 |
| Clock Speed       | 80MHz – 240MHz       |
| Wi-Fi             | 802.11 b/g/n         |
| Bluetooth         | BLE 4.2              |
| Camera            | OV2640 2MP           |
| Resolution        | Up to 2048×1564      |
| Output Format     | JPEG                 |
| RAM               | 520KB + PSRAM        |
| Operating Voltage | 5V                   |

---

# 🧠 Applications

* Smart surveillance
* Home security
* Visitor monitoring
* Industrial monitoring
* IoT remote monitoring
* Smart agriculture
* Embedded vision systems

---

# ⚠️ Limitations

* Limited GPIO pins
* Requires stable power supply
* Limited RAM for heavy AI workloads
* Heating during continuous streaming

---

# 🔍 Future Improvements

* Motion detection
* Face recognition
* Cloud integration
* Telegram/Email alerts
* Mobile app integration
* AI-based object detection

---

# 🧪 Troubleshooting

## Brownout Detector Error

Use stable 5V power supply with sufficient current.

---

## Camera Init Failed

* Check camera ribbon cable
* Ensure correct board selected

---

## Upload Failed

* IO0 must be connected to GND during upload
* Press RESET button after connecting IO0

---

## Wi-Fi Not Connecting

* Verify SSID and password
* Ensure 2.4GHz Wi-Fi network

---

# 📚 Libraries Used

```cpp
#include "esp_camera.h"
#include <WiFi.h>
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
```

---

# 📖 References

* ESP32 Official Documentation
* Arduino ESP32 Core
* Adafruit SSD1306 Library
* ESP32 CameraWebServer Example

---

# 📜 License

This project is open-source and available under the MIT License.

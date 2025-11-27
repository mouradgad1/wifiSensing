 # WiFiSensing
 WiFiSensing is a lightweight framework for collecting Channel State Information (CSI) using two ESP32 devices (AP + STA). The setup streams CSI in real time, enabling experiments in device-free sensing, RF-based activity recognition, and wireless signal analysis.--
## Quick Start
 ### 1. Clone the repository
 ```bash
 git clone <repo-url>
 cd WifiSensing
 ```
 ### 2. Install ESP-IDF (Espressif Toolchain)
 Install ESP-IDF v4.3 (Linux/macOS).
 Follow the official guide: https://docs.espressif.com/projects/esp-idf/en/v4.3/esp32/get-started/--
## Hardware Setup- 2 x ESP32 boards
  - One acts as active AP
  - One acts as active STA
 Connect both boards via USB, then check their device paths:
 ```bash
 ls /dev/ttyUSB*
 ```
 Typical result:- AP -> /dev/ttyUSB0- STA -> /dev/ttyUSB1--
## Build & Flash
 1. Open two terminal windows
   Each terminal controls one ESP32.
 2. Activate ESP-IDF in each terminal:
 ```bash
 get_idf
 ```
 3. Build each firmware:
 From inside each project folder:
 ```bash
 idf.py build
 ```
 4. Flash & run
 Active AP (CSI sender):
 ```bash
 idf.py -p /dev/ttyUSB0 flash monitor | grep "CSI_DATA" >> ../../data/<filename>.csv
 ```
 Active STA:
 ```bash
 idf.py -p /dev/ttyUSB1 flash
 ```
## Data Output
CSI data is written in real time to:
 ```
 /data/<filename>.csv
 ```


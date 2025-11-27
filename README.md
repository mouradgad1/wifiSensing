# WiFiSensing
 WiFiSensing is a lightweight framework for collecting Channel State Information (CSI)
 using two ESP32 devices (AP + STA). The setup streams CSI in real time, enabling
 experiments in device-free sensing, RF-based activity recognition, and wireless signal
 analysis.--
## Quick start
### 1
 Clone the repository
 ```bash
 git clone
 cd WifiSensing
 ```
 ### 2
 Install ESP-IDF (Espressif Toolchain)
 Install ESP-IDF **v4.3** (Linux/macOS).
 Follow the official guide:
 https://docs.espressif.com/projects/esp-idf/en/v4.3/esp32/get-started/--
## 
 Hardware Setup- **2 × ESP32** boards- One acts as **active AP**- One acts as **active STA**
 Connect both boards via USB, then check their device paths:
 ```bash
 ls /dev/ttyUSB*
 ```
 Typical result:- AP → `/dev/ttyUSB0`- STA → `/dev/ttyUSB1`--
## Build & Flash
### 1
 Open two terminal windows
 Each terminal controls one ESP32.
 ### 2
 Activate ESP-IDF in each terminal:
 ```bash
 get_idf
 ```
 ### 3
 Build each firmware:
 From inside each project folder:
 ```bash
 idf.py build
 ```
 ### 4
 Flash & run
 #### **Active AP (CSI sender)**
 ```bash
 idf.py -p /dev/ttyUSB0 flash monitor | grep "CSI_DATA" >> ../../data/.csv
 ```
 #### **Active STA**
 bash
 ```
 idf.py -p /dev/ttyUSB1 flash
 ```
##  Build & Flash
 CSI data is written in real time to:
 ```
 /data/.csv
 ```
## Project Structure 
```
 WifiSensing/
 active_ap/
 active_sta/
 data/
 README.md
 ```
## 
 Notes- Use high-quality USB cables to avoid serial drops.- If the `grep "CSI_DATA"` filter is too aggressive, remove it to log full serial
 output.- For Windows users, replace `/dev/ttyUSB*` with COM ports

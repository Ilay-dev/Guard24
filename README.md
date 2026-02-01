# Guard 24

**Developed by Ilay Schönknecht**

Guard 24 is a high- security monitoring system based on the ESP32 microcontroller and the LD2410B mmWave radar sensor.
I wrote it in C++ and also designed a 3D-Printed Case for the ESP32, the Button, The Piezzo and the LD2410B.
The .stl and .blend files are in the "3D-Case" folder.


### Key Functionalities

* **mmWave Detection**: Utilizes LD2410B 24GHz radar to detect human presence.
* **Flash Memory Logging**: Automatic storage of alarm events with precise timestamps in the internal ESP32 flash memory (LittleFS).
* **NTP Time Synchronization**: Brief WiFi activation upon startup to synchronize the internal Real-Time Clock (RTC), followed by immediate WiFi deactivation to reduce heat and power consumption.
* **Triple-Click Deactivation**: A safety feature requiring three consecutive button presses to deactivate the system, preventing accidental shut-offs.
* **Night Mode**: Programmable inactive period (e.g., 22:00 to 07:00) where the alarm remains silent.



## Hardware Requirements

* **Controller**: ESP32 (DevKit V1 or similar)
* **Sensor**: HLK-LD2410B (mmWave Radar)
* **Output**: Piezo Buzzer (Active)
* **Input**: Momentary Tactile Button

### Pin Configuration

| Component | ESP32 Pin | Function |
| :--- | :--- | :--- |
| Radar RX | GPIO 27 | Serial Data Receive |
| Radar TX | GPIO 26 | Serial Data Transmit |
| Buzzer | GPIO 16 | Acoustic Alarm Output |
| Button | GPIO 17 | Manual Control Input |

## Console Interface

When connected via USB (Baud rate: 115200), the following commands can be issued through the Serial Monitor:

* `flash`: Retrieves and displays all stored alarm events from the log file.
* `del`: Permanently deletes the current alarm log from the flash memory.

## Installation and Configuration

1. **Dependencies**: Requires the `ld2410` library.
2. **Network**: Update the `WIFI_SSID` and `WIFI_PASSWORD` in the settings section for the initial time sync.
3. **Sensitivity**: Adjust `SENSE_THRESHOLD` and `MAX_DIST_CM` to match the specific dimensions of the monitored room.

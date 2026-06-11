# ioBroker Gobel Battery Monitor Adapter (PACE, JK, TDT BMS)

[![NPM version](http://img.shields.io/npm/v/iobroker.gobel-battery.svg)](https://www.npmjs.com/package/iobroker.gobel-battery)
[![Downloads](https://img.shields.io/npm/dm/iobroker.gobel-battery.svg)](https://www.npmjs.com/package/iobroker.gobel-battery)
![Number of Installations](http://iobroker.live/badges/gobel-battery-stable.svg)
[![Dependency Status](https://img.shields.io/david/fancyui/Gobel-Battery-ioBroker-Adapter.svg)](https://david-dm.org/fancyui/Gobel-Battery-ioBroker-Adapter)

[![NPM](https://nodei.co/npm/iobroker.gobel-battery.png?downloads=true)](https://nodei.co/npm/iobroker.gobel-battery/)

This adapter integrates Gobel Power Battery BMS (PACE BMS, JK BMS, and TDT BMS) into ioBroker, allowing real-time monitoring of battery health, individual cell voltages, state of charge (SoC), and warning alarms.

## Features
* **Multi-BMS Compatibility**: Supports Pace BMS, JK BMS (55AA protocol), and TDT BMS.
* **Flexible Interfaces**: Connect via Serial (RS232/RS485 USB adapter), WiFi, or Ethernet converters.
* **Auto-Discovery of Parallel Packs**: Connecting to the Master BMS automatically scans and maps all parallel slave battery packs.
* **Comprehensive Telemetry**:
  * Cell voltages and temperature sensors.
  * System values: Voltage, current, power, SoC, SoH, capacity, cycle count, charged/discharged energy.
  * Alarm status: Cell overvoltage, undervoltage, high/low temperature warnings, short circuit, and charge/discharge MOSFET states.

## Prerequisites
This adapter runs a lightweight Python 3 daemon in the background to interface with the battery BMS.
Ensure **Python 3** and **pyserial** are installed on your ioBroker host machine.

### Installation of prerequisites:
* **Linux (Debian/Ubuntu/Raspbian)**:
  ```bash
  sudo apt-get update
  sudo apt-get install python3 python3-pip
  pip3 install pyserial
  ```
* **Windows**:
  Download and install Python 3 from [python.org](https://www.python.org/). Ensure you check "Add Python to PATH" during installation.
  Open Command Prompt or PowerShell and install `pyserial`:
  ```cmd
  pip install pyserial
  ```

## How to Install the Adapter
During the initial release or development phase, install it directly from GitHub or local directory:
* Inside your ioBroker root folder (e.g., `/opt/iobroker` on Linux):
  ```bash
  npm install https://github.com/fancyui/Gobel-Battery-ioBroker-Adapter
  ```
* Or add it via the ioBroker admin panel (GitHub icon/Custom URL).

## Configuration
Configure the following options in the adapter admin panel:
1. **Connection Type**: Select `Serial (USB)`, `WiFi` or `Ethernet`.
2. **BMS Type**: Select `PACE_LV`, `JK_PB`, `TDT`, or `PACE_LV_WIFI`.
3. **BMS Interface Port**: Choose `RS232` or `RS485`.
4. **Serial Port Path** (Serial only): `/dev/ttyUSB0` on Linux or `COM3` on Windows.
5. **Baud Rate**: Typically `115200` (Pace/JK) or `9600`.
6. **IP Address & Port** (WiFi/Ethernet only): Specify the IP and port (default `8899`) of your RS232/RS485-to-WiFi/Ethernet server.
7. **Refresh Interval**: Frequency of BMS queries (default `5` seconds).
8. **Max Parallel Packs**: Scanning limit for parallel batteries (up to `16`).

## Wiring Guide
* **Pace BMS**: Connect to the **RS232** port or via WiFi converter. Set the Master BMS DIP switches to `1000`.
* **JK BMS**: Connect to the **RS485B** or **RS485C** interface. Set the Master BMS DIP switches to `0000`.
* **TDT BMS**: Connect to the **RS232** interface.

## License
Apache License 2.0 (Copyright 2026 fancyui)

# 🔧 Multi-Output Signal Simulator

<div align="center">

![Version](https://img.shields.io/badge/version-2.4-00d4ff?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![License](https://img.shields.io/badge/License-Proprietary-ff4444?style=for-the-badge)
![Arduino](https://img.shields.io/badge/Arduino-Compatible-00979D?style=for-the-badge&logo=arduino&logoColor=white)

**A professional desktop application for real-time Arduino signal control and monitoring.**  
Designed for industrial testing, sensor simulation, and hardware validation.

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Signal Types](#-signal-types)
- [Hardware Requirements](#-hardware-requirements)
- [Installation](#-installation)
- [Usage](#-usage)
- [Project Structure](#-project-structure)
- [Building from Source](#-building-from-source)
- [Creating the Installer](#-creating-the-installer)
- [Communication Protocol](#-communication-protocol)
- [Screenshots](#-screenshots)
- [License](#-license)

---

## 🌐 Overview

**Multi-Output Signal Simulator** is a powerful Windows desktop application built with Python and Tkinter,
designed to control and monitor Arduino microcontroller pins in real-time over a serial (COM) connection.

It is primarily designed to work with the **SIMIO_01** hardware module — a specialized
input/output simulation device for industrial sensor testing and signal generation.

The application supports a wide range of industrial signal types including voltage outputs,
current loops, RTD temperature sensors, and NTC thermistors — all configurable per channel
with an intuitive graphical interface.

---

## ✨ Features

### ⚡ Analog Inputs Write (AI01 – AI06)
- Control **6 PWM output pins** (Arduino pins 3, 5, 6, 9, 10, 11)
- **Per-channel signal type selection** from a dropdown menu
- Slider automatically **limits to the valid PWM range** for the selected signal type
- Full support for **inverted signal ranges** (e.g. NTC10K)
- **Fine adjustment buttons** (▲ / ▼) for precise control
- Real-time value display with unit and percentage

### 🔘 Digital Inputs Write (BI01 – BI06)
- Control **6 digital output pins** (Arduino pins 2, 4, 7, 8, 12, 13)
- One-click **HIGH / LOW** state switching
- Per-channel **Enable / Disable** toggle

### 📊 Analog Outputs Read (AO01 – AO06)
- Read **6 analog input pins** (Arduino pins A0–A5 / pins 14–19)
- Real-time **canvas progress bars** with percentage display
- **Manual read** and **Auto-read** (200 ms polling) modes

### 📋 Debug Console
- Real-time **serial communication log**
- Timestamped sent / received messages
- One-click **Clear Log** button

### 🖥️ General
- Modern **dark theme** UI
- COM port **auto-detection**
- Graceful **connect / disconnect** handling
- Built-in **About** tab with full documentation
- **PDF Instructions** viewer integration

---

## 📡 Signal Types

| Signal Type  | Range          | Unit  | PWM Min | PWM Max | Inverted |
|--------------|----------------|-------|---------|---------|----------|
| `0-5V`       | 0.0 – 5.0      | V     | 0       | 255     | ❌        |
| `0-10V`      | 0.0 – 10.0     | V     | 0       | 255     | ❌        |
| `0-20mA`     | 0.0 – 20.0     | mA    | 0       | 255     | ❌        |
| `4-20mA`     | 4.0 – 20.0     | mA    | 51      | 255     | ❌        |
| `0-4mA`      | 0.0 – 4.0      | mA    | 0       | 51      | ❌        |
| `LG-NI1000`  | -50.0 – 150.0  | °C    | 59      | 136     | ❌        |
| `PT100`      | -50.0 – 150.0  | °C    | 60      | 118     | ❌        |
| `PT1000`     | -50.0 – 150.0  | °C    | 60      | 118     | ❌        |
| `NTC10K`     | 0.0 – 50.0     | °C    | 113     | 22      | ✅        |
| `0-100%`     | 0.0 – 100.0    | %     | 0       | 255     | ❌        |
| `RAW PWM`    | 0 – 255        | PWM   | 0       | 255     | ❌        |

> ⚠️ **NTC10K** uses an inverted PWM range — higher PWM = lower temperature.  
> The application handles this automatically.

---

## 🔩 Hardware Requirements

| Component        | Details                                      |
|------------------|----------------------------------------------|
| **Microcontroller** | Arduino Uno / Nano / Mega (or compatible) |
| **Hardware Module** | SIMIO_01 (recommended)                   |
| **Connection**   | USB Serial (COM port)                        |
| **Baud Rate**    | 9600                                         |
| **OS**           | Windows 10 / 11                              |

### Arduino Pin Mapping

| Channel | Label  | Arduino Pin | Type          |
|---------|--------|-------------|---------------|
| AI01    | PWM    | 3           | Analog Output |
| AI02    | PWM    | 5           | Analog Output |
| AI03    | PWM    | 6           | Analog Output |
| AI04    | PWM    | 9           | Analog Output |
| AI05    | PWM    | 10          | Analog Output |
| AI06    | PWM    | 11          | Analog Output |
| BI01    | Digital| 2           | Digital Output|
| BI02    | Digital| 4           | Digital Output|
| BI03    | Digital| 7           | Digital Output|
| BI04    | Digital| 8           | Digital Output|
| BI05    | Digital| 12          | Digital Output|
| BI06    | Digital| 13          | Digital Output|
| AO01    | Analog | A0 (14)     | Analog Input  |
| AO02    | Analog | A1 (15)     | Analog Input  |
| AO03    | Analog | A2 (16)     | Analog Input  |
| AO04    | Analog | A3 (17)     | Analog Input  |
| AO05    | Analog | A4 (18)     | Analog Input  |
| AO06    | Analog | A5 (19)     | Analog Input  |

---

## 💾 Installation

### Option 1 — Windows Installer (Recommended)

1. Download the latest installer from the [Releases](../../releases) page
2. Run `MultiOutputSignalSimulator_v2.4_Setup.exe`
3. Follow the setup wizard
4. Launch from the **Start Menu** or **Desktop shortcut**

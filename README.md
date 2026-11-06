# ESP32 Hardware Diagnostics & Bring-up Testbed

[![Platform](https://img.shields.io/badge/Platform-PlatformIO-orange.svg)](https://platformio.org/)
[![Hardware](https://img.shields.io/badge/Hardware-ESP32--DevKit-blue.svg)](https://www.espressif.com/)
[![Category](https://img.shields.io/badge/Category-Hardware%20Validation-lightgrey.svg)](https://github.com/)

A baseline hardware verification and diagnostic firmware designed for initial ESP32 development board bring-up. It confirms core microcontroller operation, serial communication integrity at 115200 baud, and verifies GPIO output driving using the on-board status LED.

---

## Features

- **Bootloader & Core Verification**: Emits structured boot verification messages over serial console.
- **Heartbeat Indicator**: Oscillates GPIO 2 (the built-in blue LED on standard ESP32 DevKit boards) with 1000ms duty cycles to verify hardware clock timers.
- **Diagnostic Logging**: Continuous status streaming over the USB UART interface for testing connection stability.
- **Clean Baseline**: Serves as a validated hardware scaffolding template for integrating environmental sensors (such as MQ-135, MQ-2, DHT11) and Firebase cloud pipelines.

---

## Hardware Configuration

| Pin | Function | Notes |
| :--- | :--- | :--- |
| `GPIO 2` | Output | Built-in Blue LED indicator |
| `USB / UART` | Serial I/O | 115200 baud, 8-N-1 |

---

## PlatformIO Configuration

From [`platformio.ini`](platformio.ini):

```ini
[env:esp32dev]
platform = espressif32
board = esp32dev
framework = arduino
```

---

## Quick Start

```bash
# Build the project
pio run

# Upload to connected ESP32 board
pio run --target upload

# Monitor serial output
pio device monitor -b 115200
```

---

## Project Structure

```
air quality esp32 fb/
├── src/
│   └── main.cpp         # Hardware test and LED blink routines
└── platformio.ini       # PlatformIO build configuration
```

---

## License

Open source under the MIT License.

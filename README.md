## WiFiMulti_Generic

[![arduino-library-badge](https://www.ardu-badge.com/badge/WiFiMulti_Generic.svg?)](https://www.ardu-badge.com/WiFiMulti_Generic)
[![GitHub release](https://img.shields.io/github/release/khoih-prog/WiFiMulti_Generic.svg)](https://github.com/khoih-prog/WiFiMulti_Generic/releases)
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](#Contributing)
[![GitHub issues](https://img.shields.io/github/issues/khoih-prog/WiFiMulti_Generic.svg)](http://github.com/khoih-prog/WiFiMulti_Generic/issues)

---
---

## Table of Contents

* [Why do we need this WiFiMulti_Generic library](#why-do-we-need-this-WiFiMulti_Generic-library)
  * [Features](#features)
  * [Currently supported Boards](#currently-supported-boards)
  * [Currently supported WiFi shields/modules](#currently-supported-wifi-shieldsmodules)
* [Changelog](changelog.md)
* [Prerequisites](#prerequisites)
* [Installation](#installation)
  * [Use Arduino Library Manager](#use-arduino-library-manager)
  * [Manual Install](#manual-install)
  * [VS Code & PlatformIO](#vs-code--platformio)
* [Packages' Patches](#packages-patches)
  * [1. For Adafruit nRF52840 and nRF52832 boards](#1-for-adafruit-nRF52840-and-nRF52832-boards)
  * [2. For Teensy boards](#2-for-teensy-boards)
  * [3. For Arduino SAM DUE boards](#3-for-arduino-sam-due-boards)
  * [4. For Arduino SAMD boards](#4-for-arduino-samd-boards)
      * [For core version v1.8.10+](#for-core-version-v1810)
      * [For core version v1.8.9-](#for-core-version-v189-)
  * [5. For Adafruit SAMD boards](#5-for-adafruit-samd-boards)
  * [6. For Seeeduino SAMD boards](#6-for-seeeduino-samd-boards)
  * [7. For STM32 boards](#7-for-stm32-boards) 
    * [7.1. For STM32 boards to use LAN8720](#71-for-stm32-boards-to-use-lan8720)
    * [7.2. For STM32 boards to use Serial1](#72-for-stm32-boards-to-use-serial1)
  * [8. For RP2040-based boards using Earle Philhower arduino-pico core](#8-for-rp2040-based-boards-using-earle-philhower-arduino-pico-core)
    * [8.1. To use BOARD_NAME](#81-to-use-board_name)
    * [8.2. To avoid compile error relating to microsecondsToClockCycles](#82-to-avoid-compile-error-relating-to-microsecondstoclockcycles)
  * [9. For Portenta_H7 boards using Arduino IDE in Linux](#9-for-portenta_h7-boards-using-arduino-ide-in-linux)
* [Examples](#examples)
  * [ 1. WiFiMulti](examples/WiFiMulti)
* [Example WiFiMulti](#example-WiFiMulti)
  * [1. File WiFiMulti.ino](#1-File-WiFiMulti)
  * [2. File defines.h](#2-File-definesh)
* [Debug Terminal Output Samples](#debug-terminal-output-samples)
  * [ 1. WiFiMulti on RASPBERRY_PI_PICO](#1-WiFiMulti-on-RASPBERRY_PI_PICO)
  * [ 2. WiFiMulti on MBED RaspberryPi Pico](#2-WiFiMulti-on-MBED-RaspberryPi-Pico)
  * [ 3. WiFiMulti on Nano RP2040 Connect](#3-WiFiMulti-on-Nano-RP2040-Connect)
  * [ 4. WiFiMulti on NANO_RP2040_CONNECT](#4-WiFiMulti-on-NANO_RP2040_CONNECT)
  * [ 5. WiFiMulti on ESP8266_NODEMCU_ESP12E](#5-WiFiMulti-on-ESP8266_NODEMCU_ESP12E)
  * [ 6. WiFiMulti on ESP32C3_DEV](#6-WiFiMulti-on-ESP32C3_DEV)
  * [ 7. WiFiMulti on ESP32S3_DEV](#7-WiFiMulti-on-ESP32S3_DEV)
* [Debug](#debug)
* [Troubleshooting](#troubleshooting)
* [Issues](#issues)
* [TO DO](#to-do)
* [DONE](#done)
* [Contributions and Thanks](#contributions-and-thanks)
* [Contributing](#contributing)
* [License](#license)
* [Copyright](#copyright)


---
---

### Why do we need this [WiFiMulti_Generic library](https://github.com/khoih-prog/WiFiMulti_Generic)


#### Features

This [**WiFiMulti_Generic library**](https://github.com/khoih-prog/WiFiMulti_Generic) is a simple MultiWiFi library to adapt ESP32/ESP8266 `MultiWiFi` feature of WiFi libraries to all other WiFi modules and libraries. The functions are similar and compatible to those of [`ESP32 MultiWiFi`](https://github.com/espressif/arduino-esp32/tree/master/libraries/WiFi) and [`ESP8266 MultiWiFi`](https://github.com/esp8266/Arduino/tree/master/libraries/ESP8266WiFi) libraries to make life much easier to port sketches from ESP8266/ESP32.


#### Currently Supported Boards

This [**WiFiMulti_Generic library**](https://github.com/khoih-prog/WiFiMulti_Generic) currently supports these following boards:

 1. SAM DUE

 2. SAMD21

  - Arduino: ZERO, MKR, NANO_33_IOT, etc.
  - Adafruit SAMD21 (M0) : ItsyBitsy M0, Feather M0, Feather M0 Express, Metro M0 Express, Circuit Playground Express, Trinket M0, PIRkey, HalloWing M0, Crickit M0, etc.
  - Seeeduino:  LoRaWAN, Zero, Femto M0, XIAO M0, Wio GPS Board, etc.
  
 3. SAMD51

  - Adafruit SAMD51 (M4) : Metro M4, Grand Central M4, ItsyBitsy M4, Feather M44 Express, Trellis M4, Metro M4 AirLift lite, MONSTER M4SK Express, Hallowing EM4 xpress, etc.
  - Seeeduino: Wio Terminal, Grove UI Wireless
  
 4. Teensy (4.1, 4.0, 3.6, 3.5, 3,2, 3.1, 3.0, LC)
 5. All STM32F/L/H/G/WB/MP1 with more than 32KB flash memory.
 6. AVR Mega1280, 2560, ADK. **Not yet**

 7. RP2040-based boards, such as **Nano RP2040 Connect**, using [**Arduino mbed OS for Nano boards**](https://github.com/arduino/ArduinoCore-mbed).
 8. RP2040-based boards, such as **RASPBERRY_PI_PICO, ADAFRUIT_FEATHER_RP2040 and GENERIC_RP2040**, using [**Arduino-mbed RP2040** core](https://github.com/arduino/ArduinoCore-mbed) or [**Earle Philhower's arduino-pico** core](https://github.com/earlephilhower/arduino-pico).

 9. **ESP32**
 
  - ESP32 boards, such as `ESP32_DEV`, etc.
  - ESP32S2-based boards, such as `ESP32S2_DEV`, `ESP32_S2 Saola`, etc.
  - ESP32C3-based boards, such as `ESP32C3_DEV`, etc. **New**
  - ESP32_S3 (ESP32S3_DEV, ESP32_S3_BOX, UM TINYS3, UM PROS3, UM FEATHERS3, etc.) **New**
  
10. **ESP8266**

11. **Portenta_H7** **Not yet**

---

#### Currently supported WiFi shields/modules

1. WiFiNINA using [`WiFiNINA_Generic library`](https://github.com/khoih-prog/WiFiNINA_Generic)
2. WiFi101 using [`WiFi101 library`](https://github.com/arduino-libraries/WiFi101)  **Not yet**
3. u-blox W101, W102 using [`WiFiNINA_Generic library`](https://github.com/khoih-prog/WiFiNINA_Generic)
4. ESP8266-AT command using [`WiFiEspAT library`](https://github.com/jandrassy/WiFiEspAT)
5. ESP8266/ESP32-AT command using [`ESP_AT_Lib library`](https://github.com/khoih-prog/ESP_AT_Lib)
6. Built-in WiFi of ESP32, ESP8266
7. Built-in WiFi of Portenta_H7   **Not yet**

---
---

## Prerequisites

 1. [`Arduino IDE 1.8.19+` for Arduino](https://github.com/arduino/Arduino). [![GitHub release](https://img.shields.io/github/release/arduino/Arduino.svg)](https://github.com/arduino/Arduino/releases/latest)
 2. [`ESP32 Core 2.0.2+`](https://github.com/espressif/arduino-esp32) for ESP32-based boards. [![Latest release](https://img.shields.io/github/release/espressif/arduino-esp32.svg)](https://github.com/espressif/arduino-esp32/releases/latest/)
 3. [`ESP8266 Core 3.0.2+`](https://github.com/esp8266/Arduino) for ESP8266-based boards. [![Latest release](https://img.shields.io/github/release/esp8266/Arduino.svg)](https://github.com/esp8266/Arduino/releases/latest/).
 4. [`Arduino AVR core 1.8.3+`](https://github.com/arduino/ArduinoCore-avr) for Arduino (Use Arduino Board Manager) for AVR boards. [![GitHub release](https://img.shields.io/github/release/arduino/ArduinoCore-avr.svg)](https://github.com/arduino/ArduinoCore-avr/releases/latest) **Not yet**
 5. [`Teensy core v1.56+`](https://www.pjrc.com/teensy/td_download.html) for Teensy (4.1, 4.0, 3.6, 3.5, 3,2, 3.1, 3.0) boards.
 6. [`Arduino SAM DUE core v1.6.12+`](https://github.com/arduino/ArduinoCore-sam) for SAM DUE ARM Cortex-M3 boards.
 7. [`Arduino SAMD core 1.8.12+`](https://github.com/arduino/ArduinoCore-samd) for SAMD ARM Cortex-M0+ boards. [![GitHub release](https://img.shields.io/github/release/arduino/ArduinoCore-samd.svg)](https://github.com/arduino/ArduinoCore-samd/releases/latest)
 8. [`Adafruit SAMD core 1.7.9+`](https://github.com/adafruit/ArduinoCore-samd) for SAMD ARM Cortex-M0+ and M4 boards (Nano 33 IoT, etc.). [![GitHub release](https://img.shields.io/github/release/adafruit/ArduinoCore-samd.svg)](https://github.com/adafruit/ArduinoCore-samd/releases/latest)
 9. [`Seeeduino SAMD core 1.8.2+`](https://github.com/Seeed-Studio/ArduinoCore-samd) for SAMD21/SAMD51 boards (XIAO M0, Wio Terminal, etc.). [![Latest release](https://img.shields.io/github/release/Seeed-Studio/ArduinoCore-samd.svg)](https://github.com/Seeed-Studio/ArduinoCore-samd/releases/latest/)
10. [`Adafruit nRF52 v1.3.0+`](https://github.com/adafruit/Adafruit_nRF52_Arduino) for nRF52 boards such as Adafruit NRF52840_FEATHER, NRF52832_FEATHER, NRF52840_FEATHER_SENSE, NRF52840_ITSYBITSY, NRF52840_CIRCUITPLAY, NRF52840_CLUE, NRF52840_METRO, NRF52840_PCA10056, PARTICLE_XENON, **NINA_B302_ublox**, etc. [![GitHub release](https://img.shields.io/github/release/adafruit/Adafruit_nRF52_Arduino.svg)](https://github.com/adafruit/Adafruit_nRF52_Arduino/releases/latest)
11. [`Arduino Core for STM32 v2.2.0+`](https://github.com/stm32duino/Arduino_Core_STM32) for STM32F/L/H/G/WB/MP1 boards. [![GitHub release](https://img.shields.io/github/release/stm32duino/Arduino_Core_STM32.svg)](https://github.com/stm32duino/Arduino_Core_STM32/releases/latest)
12. [`Earle Philhower's arduino-pico core v1.12.0+`](https://github.com/earlephilhower/arduino-pico) for RP2040-based boards such as **RASPBERRY_PI_PICO, ADAFRUIT_FEATHER_RP2040 and GENERIC_RP2040**, etc. [![GitHub release](https://img.shields.io/github/release/earlephilhower/arduino-pico.svg)](https://github.com/earlephilhower/arduino-pico/releases/latest)
13. [`ArduinoCore-mbed mbed_rp2040, mbed_nano, mbed_portenta core 2.7.2+`](https://github.com/arduino/ArduinoCore-mbed) for Arduino (Use Arduino Board Manager) **Portenta_H7, RP2040-based boards, such as Nano_RP2040_Connect, RASPBERRY_PI_PICO**. [![GitHub release](https://img.shields.io/github/release/arduino/ArduinoCore-mbed.svg)](https://github.com/arduino/ArduinoCore-mbed/releases/latest)

14. [`WiFiNINA_Generic library v1.8.14-3+`](https://github.com/khoih-prog/WiFiNINA_Generic) if using WiFiNINA. To install. check [![arduino-library-badge](https://www.ardu-badge.com/badge/WiFiNINA_Generic.svg?)](https://www.ardu-badge.com/WiFiNINA_Generic).
15. [`Modified WiFi101 Library v0.16.1+`](https://github.com/khoih-prog/WiFi101) to use SAMD MKR1000, etc. boards with WiFi101. **Not yet**
16. [`WiFiEspAT library v1.3.2+`](https://github.com/jandrassy/WiFiEspAT) if using ESP8288/ESP32-AT shields. [![GitHub release](https://img.shields.io/github/release/jandrassy/WiFiEspAT.svg)](https://github.com/jandrassy/WiFiEspAT/releases/latest)

---
---

## Installation

### Use Arduino Library Manager

The best and easiest way is to use `Arduino Library Manager`. Search for `WiFiMulti_Generic`, then select / install the latest version.
You can also use this link [![arduino-library-badge](https://www.ardu-badge.com/badge/WiFiMulti_Generic.svg?)](https://www.ardu-badge.com/WiFiMulti_Generic) for more detailed instructions.

### Manual Install

1. Navigate to [WiFiMulti_Generic](https://github.com/khoih-prog/WiFiMulti_Generic) page.
2. Download the latest release `WiFiMulti_Generic-master.zip`.
3. Extract the zip file to `WiFiMulti_Generic-master` directory 
4. Copy the whole `WiFiMulti_Generic-master` folder to Arduino libraries' directory such as `~/Arduino/libraries/`.

### VS Code & PlatformIO:

1. Install [VS Code](https://code.visualstudio.com/)
2. Install [PlatformIO](https://platformio.org/platformio-ide)
3. Install [**WiFiMulti_Generic** library](https://registry.platformio.org/libraries/khoih-prog/WiFiMulti_Generic) by using [Library Manager](https://registry.platformio.org/libraries/khoih-prog/WiFiMulti_Generic/installation). Search for WiFiMulti_Generic in [Platform.io Author's Libraries](https://platformio.org/lib/search?query=author:%22Khoi%20Hoang%22)
4. Use included [platformio.ini](platformio/platformio.ini) file from examples to ensure that all dependent libraries will installed automatically. Please visit documentation for the other options and examples at [Project Configuration File](https://docs.platformio.org/page/projectconf.html)


---
---

### Packages' Patches

#### 1. For Adafruit nRF52840 and nRF52832 boards

**To be able to compile, run and automatically detect and display BOARD_NAME on nRF52840/nRF52832 boards**, you have to copy the whole [nRF52 Packages_Patches](Packages_Patches/adafruit/hardware/nrf52/1.3.0) directory into Adafruit nRF52 directory (~/.arduino15/packages/adafruit/hardware/nrf52/1.3.0). 

Supposing the Adafruit nRF52 version is 1.3.0. These files must be copied into the directory:
- `~/.arduino15/packages/adafruit/hardware/nrf52/1.3.0/platform.txt`
- `~/.arduino15/packages/adafruit/hardware/nrf52/1.3.0/boards.txt`
- `~/.arduino15/packages/adafruit/hardware/nrf52/1.3.0/cores/nRF5/Udp.h`
- `~/.arduino15/packages/adafruit/hardware/nrf52/1.3.0/cores/nRF5/Print.h`
- `~/.arduino15/packages/adafruit/hardware/nrf52/1.3.0/cores/nRF5/Print.cpp`
- `~/.arduino15/packages/adafruit/hardware/nrf52/1.3.0/variants/NINA_B302_ublox/variant.h`
- `~/.arduino15/packages/adafruit/hardware/nrf52/1.3.0/variants/NINA_B302_ublox/variant.cpp`
- `~/.arduino15/packages/adafruit/hardware/nrf52/1.3.0/variants/NINA_B112_ublox/variant.h`
- `~/.arduino15/packages/adafruit/hardware/nrf52/1.3.0/variants/NINA_B112_ublox/variant.cpp`
- **`~/.arduino15/packages/adafruit/hardware/nrf52/1.3.0/cores/nRF5/Udp.h`**

Whenever a new version is installed, remember to copy these files into the new version directory. For example, new version is x.yy.z
These files must be copied into the directory:

- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/platform.txt`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/boards.txt`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/cores/nRF5/Udp.h`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/cores/nRF5/Print.h`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/cores/nRF5/Print.cpp`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/variants/NINA_B302_ublox/variant.h`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/variants/NINA_B302_ublox/variant.cpp`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/variants/NINA_B112_ublox/variant.h`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/variants/NINA_B112_ublox/variant.cpp`
- **`~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/cores/nRF5/Udp.h`**

#### 2. For Teensy boards
 
 **To be able to compile and run on Teensy boards**, you have to copy the files in [**Packages_Patches for Teensy directory**](Packages_Patches/hardware/teensy/avr) into Teensy hardware directory (./arduino-1.8.19/hardware/teensy/avr/boards.txt). 

Supposing the Arduino version is 1.8.19. These files must be copied into the directory:

- `./arduino-1.8.19/hardware/teensy/avr/boards.txt`
- `./arduino-1.8.19/hardware/teensy/avr/cores/teensy/Stream.h`
- `./arduino-1.8.19/hardware/teensy/avr/cores/teensy3/Stream.h`
- `./arduino-1.8.19/hardware/teensy/avr/cores/teensy4/Stream.h`

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz
These files must be copied into the directory:

- `./arduino-x.yy.zz/hardware/teensy/avr/boards.txt`
- `./arduino-x.yy.zz/hardware/teensy/avr/cores/teensy/Stream.h`
- `./arduino-x.yy.zz/hardware/teensy/avr/cores/teensy3/Stream.h`
- `./arduino-x.yy.zz/hardware/teensy/avr/cores/teensy4/Stream.h`

#### 3. For Arduino SAM DUE boards
 
 **To be able to compile and run on SAM DUE boards**, you have to copy the whole [SAM DUE](Packages_Patches/arduino/hardware/sam/1.6.12) directory into Arduino sam directory (~/.arduino15/packages/arduino/hardware/sam/1.6.12). 

Supposing the Arduino SAM core version is 1.6.12. This file must be copied into the directory:

- `~/.arduino15/packages/arduino/hardware/sam/1.6.12/platform.txt`

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz
This file must be copied into the directory:

- `~/.arduino15/packages/arduino/hardware/sam/x.yy.zz/platform.txt`

#### 4. For Arduino SAMD boards
 
 ***To be able to compile, run and automatically detect and display BOARD_NAME on Arduino SAMD (Nano-33-IoT, etc) boards***, you have to copy the whole [Arduino SAMD Packages_Patches](Packages_Patches/arduino/hardware/samd/1.8.12) directory into Arduino SAMD directory (~/.arduino15/packages/arduino/hardware/samd/1.8.12).
 
#### For core version v1.8.10+

Supposing the Arduino SAMD version is 1.8.12. Now only one file must be copied into the directory:

- `~/.arduino15/packages/arduino/hardware/samd/1.8.12/platform.txt`

Whenever a new version is installed, remember to copy this files into the new version directory. For example, new version is x.yy.zz

This file must be copied into the directory:

- `~/.arduino15/packages/arduino/hardware/samd/x.yy.zz/platform.txt`
 
#### For core version v1.8.9-

Supposing the Arduino SAMD version is 1.8.9. These files must be copied into the directory:

- `~/.arduino15/packages/arduino/hardware/samd/1.8.9/platform.txt`
- ***`~/.arduino15/packages/arduino/hardware/samd/1.8.9/cores/arduino/Arduino.h`***

Whenever a new version is installed, remember to copy these files into the new version directory. For example, new version is x.yy.z

These files must be copied into the directory:

- `~/.arduino15/packages/arduino/hardware/samd/x.yy.z/platform.txt`
- ***`~/.arduino15/packages/arduino/hardware/samd/x.yy.z/cores/arduino/Arduino.h`***
 
 This is mandatory to fix the ***notorious Arduino SAMD compiler error***. See [Improve Arduino compatibility with the STL (min and max macro)](https://github.com/arduino/ArduinoCore-samd/pull/399)
 
```
 ...\arm-none-eabi\include\c++\7.2.1\bits\stl_algobase.h:243:56: error: macro "min" passed 3 arguments, but takes just 2
     min(const _Tp& __a, const _Tp& __b, _Compare __comp)
```

Whenever the above-mentioned compiler error issue is fixed with the new Arduino SAMD release, you don't need to copy the `Arduino.h` file anymore.

#### 5. For Adafruit SAMD boards
 
 ***To be able to compile, run and automatically detect and display BOARD_NAME on Adafruit SAMD (Itsy-Bitsy M4, etc) boards***, you have to copy the whole [Adafruit SAMD Packages_Patches](Packages_Patches/adafruit/hardware/samd/1.7.9) directory into Adafruit samd directory (~/.arduino15/packages/adafruit/hardware/samd/1.7.9). 

Supposing the Adafruit SAMD core version is 1.7.9. This file must be copied into the directory:

- `~/.arduino15/packages/adafruit/hardware/samd/1.7.9/platform.txt`
- `~/.arduino15/packages/adafruit/hardware/samd/1.7.9/cores/arduino/Print.h`
- `~/.arduino15/packages/adafruit/hardware/samd/1.7.9/cores/arduino/Print.cpp`

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz
This file must be copied into the directory:

- `~/.arduino15/packages/adafruit/hardware/samd/x.yy.zz/platform.txt`
- `~/.arduino15/packages/adafruit/hardware/samd/x.yy.zz/cores/arduino/Print.h`
- `~/.arduino15/packages/adafruit/hardware/samd/x.yy.zz/cores/arduino/Print.cpp`

#### 6. For Seeeduino SAMD boards
 
 ***To be able to compile, run and automatically detect and display BOARD_NAME on Seeeduino SAMD (XIAO M0, Wio Terminal, etc) boards***, you have to copy the whole [Seeeduino SAMD Packages_Patches](Packages_Patches/Seeeduino/hardware/samd/1.8.2) directory into Seeeduino samd directory (~/.arduino15/packages/Seeeduino/hardware/samd/1.8.2). 

Supposing the Seeeduino SAMD core version is 1.8.2. This file must be copied into the directory:

- `~/.arduino15/packages/Seeeduino/hardware/samd/1.8.2/platform.txt`
- `~/.arduino15/packages/Seeeduino/hardware/samd/1.8.2/cores/arduino/Arduino.h`
- `~/.arduino15/packages/Seeeduino/hardware/samd/1.8.2/cores/arduino/Print.h`
- `~/.arduino15/packages/Seeeduino/hardware/samd/1.8.2/cores/arduino/Print.cpp`

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz
This file must be copied into the directory:

- `~/.arduino15/packages/Seeeduino/hardware/samd/x.yy.zz/platform.txt`
- `~/.arduino15/packages/Seeeduino/hardware/samd/x.yy.zz/cores/arduino/Arduino.h`
- `~/.arduino15/packages/Seeeduino/hardware/samd/x.yy.zz/cores/arduino/Print.h`
- `~/.arduino15/packages/Seeeduino/hardware/samd/x.yy.zz/cores/arduino/Print.cpp`

#### 7. For STM32 boards

#### 7.1 For STM32 boards to use LAN8720

To use LAN8720 on some STM32 boards 

- **Nucleo-144 (F429ZI, NUCLEO_F746NG, NUCLEO_F746ZG, NUCLEO_F756ZG)**
- **Discovery (DISCO_F746NG)**
- **STM32F4 boards (BLACK_F407VE, BLACK_F407VG, BLACK_F407ZE, BLACK_F407ZG, BLACK_F407VE_Mini, DIYMORE_F407VGT, FK407M1)**

you have to copy the files [stm32f4xx_hal_conf_default.h](Packages_Patches/STM32/hardware/stm32/2.2.0/system/STM32F4xx) and [stm32f7xx_hal_conf_default.h](Packages_Patches/STM32/hardware/stm32/2.2.0/system/STM32F7xx) into STM32 stm32 directory (~/.arduino15/packages/STM32/hardware/stm32/2.2.0/system) to overwrite the old files.

Supposing the STM32 stm32 core version is 2.2.0. These files must be copied into the directory:

- `~/.arduino15/packages/STM32/hardware/stm32/2.2.0/system/STM32F4xx/stm32f4xx_hal_conf_default.h` for STM32F4.
- `~/.arduino15/packages/STM32/hardware/stm32/2.2.0/system/STM32F7xx/stm32f7xx_hal_conf_default.h` for Nucleo-144 STM32F7.

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz,
theses files must be copied into the corresponding directory:

- `~/.arduino15/packages/STM32/hardware/stm32/x.yy.zz/system/STM32F4xx/stm32f4xx_hal_conf_default.h`
- `~/.arduino15/packages/STM32/hardware/stm32/x.yy.zz/system/STM32F7xx/stm32f7xx_hal_conf_default.h


#### 7.2 For STM32 boards to use Serial1

**To use Serial1 on some STM32 boards without Serial1 definition (Nucleo-144 NUCLEO_F767ZI, Nucleo-64 NUCLEO_L053R8, etc.) boards**, you have to copy the files [STM32 variant.h](Packages_Patches/STM32/hardware/stm32/2.2.0) into STM32 stm32 directory (~/.arduino15/packages/STM32/hardware/stm32/2.2.0). You have to modify the files corresponding to your boards, this is just an illustration how to do.

Supposing the STM32 stm32 core version is 2.2.0. These files must be copied into the directory:

- `~/.arduino15/packages/STM32/hardware/stm32/2.2.0/variants/STM32F7xx/F765Z(G-I)T_F767Z(G-I)T_F777ZIT/NUCLEO_F767ZI/variant.h` for Nucleo-144 NUCLEO_F767ZI.
- `~/.arduino15/packages/STM32/hardware/stm32/2.2.0/variants/STM32L0xx/L052R(6-8)T_L053R(6-8)T_L063R8T/NUCLEO_L053R8/variant.h` for Nucleo-64 NUCLEO_L053R8.

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz,
theses files must be copied into the corresponding directory:

- `~/.arduino15/packages/STM32/hardware/stm32/x.yy.zz/variants/STM32F7xx/F765Z(G-I)T_F767Z(G-I)T_F777ZIT/NUCLEO_F767ZI/variant.h`
- `~/.arduino15/packages/STM32/hardware/stm32/x.yy.zz/variants/STM32L0xx/L052R(6-8)T_L053R(6-8)T_L063R8T/NUCLEO_L053R8/variant.h`

#### 8. For RP2040-based boards using [Earle Philhower arduino-pico core](https://github.com/earlephilhower/arduino-pico)

#### 8.1 To use BOARD_NAME

 **To be able to automatically detect and display BOARD_NAME on RP2040-based boards (RASPBERRY_PI_PICO, ADAFRUIT_FEATHER_RP2040, GENERIC_RP2040, etc) boards**, you have to copy the file [RP2040 platform.txt](Packages_Patches/rp2040/hardware/rp2040/1.4.0) into rp2040 directory (~/.arduino15/packages/rp2040/hardware/rp2040/1.4.0). 

Supposing the rp2040 core version is 1.4.0. This file must be copied into the directory:

- `~/.arduino15/packages/rp2040/hardware/rp2040/1.4.0/platform.txt`

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz
This file must be copied into the directory:

- `~/.arduino15/packages/rp2040/hardware/rp2040/x.yy.zz/platform.txt`

With core after v1.5.0, this step is not necessary anymore thanks to the PR [Add -DBOARD_NAME="{build.board}" #136](https://github.com/earlephilhower/arduino-pico/pull/136).

#### 8.2 To avoid compile error relating to microsecondsToClockCycles

Some libraries, such as [Adafruit DHT-sensor-library](https://github.com/adafruit/DHT-sensor-library), require the definition of microsecondsToClockCycles(). **To be able to compile and run on RP2040-based boards**, you have to copy the files in [**RP2040 Arduino.h**](Packages_Patches/rp2040/hardware/rp2040/1.4.0/cores/rp2040/Arduino.h) into rp2040 directory (~/.arduino15/packages/rp2040/hardware/rp2040/1.4.0).

Supposing the rp2040 core version is 1.4.0. This file must be copied to replace:

- `~/.arduino15/packages/rp2040/hardware/rp2040/1.4.0/cores/rp2040/Arduino.h`

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz
This file must be copied to replace:

- `~/.arduino15/packages/rp2040/hardware/rp2040/x.yy.zz/cores/rp2040/Arduino.h`

With core after v1.5.0, this step is not necessary anymore thanks to the PR [Add defs for compatibility #142](https://github.com/earlephilhower/arduino-pico/pull/142).


#### 9. For Portenta_H7 boards using Arduino IDE in Linux

  **To be able to upload firmware to Portenta_H7 using Arduino IDE in Linux (Ubuntu, etc.)**, you have to copy the file [portenta_post_install.sh](Packages_Patches/arduino/hardware/mbed_portenta/2.7.2/portenta_post_install.sh) into mbed_portenta directory (~/.arduino15/packages/arduino/hardware/mbed_portenta/2.7.2/portenta_post_install.sh). 
  
  Then run the following command using `sudo`
  
```
$ cd ~/.arduino15/packages/arduino/hardware/mbed_portenta/2.7.2
$ chmod 755 portenta_post_install.sh
$ sudo ./portenta_post_install.sh
```

This will create the file `/etc/udev/rules.d/49-portenta_h7.rules` as follows:

```
# Portenta H7 bootloader mode UDEV rules

SUBSYSTEMS=="usb", ATTRS{idVendor}=="2341", ATTRS{idProduct}=="035b", GROUP="plugdev", MODE="0666"
```

Supposing the ArduinoCore-mbed core version is 2.7.2. Now only one file must be copied into the directory:

- `~/.arduino15/packages/arduino/hardware/mbed_portenta/2.7.2/portenta_post_install.sh`

Whenever a new version is installed, remember to copy this files into the new version directory. For example, new version is x.yy.zz

This file must be copied into the directory:

- `~/.arduino15/packages/arduino/hardware/mbed_portenta/x.yy.zz/portenta_post_install.sh`


---
---

### Examples:

 1. [WiFiMulti](examples/WiFiMulti)

---
---

### Example [WiFiMulti](examples/WiFiMulti)

#### 1. File [WiFiMulti.ino](examples/WiFiMulti/WiFiMulti.ino)


```cpp
#include "defines.h"

WiFiMulti_Generic wifiMulti;

void setup()
{
  Serial.begin(115200);
  while (!Serial);

  delay(200);

  Serial.print(F("\nStarting WiFiMulti on ")); Serial.println(BOARD_NAME);
  Serial.println(WIFIMULTI_GENERIC_VERSION);

#if WIFI_USING_ESP_AT
  // initialize serial for ESP module
  EspSerial.begin(115200);
  // initialize ESP module
  WiFi.init(&EspSerial);

  Serial.println(F("WiFi shield init done"));
#endif

  wifiMulti.addAP(your_ssid, your_pass);
  wifiMulti.addAP("ssid_from_AP_1", "your_password_for_AP_1");
  wifiMulti.addAP("ssid_from_AP_2", "your_password_for_AP_2");
  wifiMulti.addAP("ssid_from_AP_3", "your_password_for_AP_3");

  Serial.println("Connecting WiFi...");

  if (wifiMulti.run() == WL_CONNECTED)
  {
    Serial.print("\nWiFi connected, IP address: ");
    Serial.println(WiFi.localIP());
  }
}

uint8_t connectMultiWiFi()
{
#if ESP32
  // For ESP32, this better be 0 to shorten the connect time.
  // For ESP32-S2/C3, must be > 500
  #if ( USING_ESP32_S2 || USING_ESP32_C3 )
    #define WIFI_MULTI_1ST_CONNECT_WAITING_MS           500L
  #else
    // For ESP32 core v1.0.6, must be >= 500
    #define WIFI_MULTI_1ST_CONNECT_WAITING_MS           800L
  #endif
#elif (ESP8266)
  // For ESP8266, this better be 2200 to enable connect the 1st time
  #define WIFI_MULTI_1ST_CONNECT_WAITING_MS             2200L
#else
  // For general board, this better be 1000 to enable connect the 1st time
  #define WIFI_MULTI_1ST_CONNECT_WAITING_MS             1000L
#endif

#define WIFI_MULTI_CONNECT_WAITING_MS                   500L

  Serial.println("WiFi lost. Trying to scan and reconnect");

  int i = 0;

  uint8_t status = wifiMulti.run();

  delay(WIFI_MULTI_1ST_CONNECT_WAITING_MS);

  while ( ( i++ < 20 ) && ( status != WL_CONNECTED ) )
  {
    status = WiFi.status();

    if ( status == WL_CONNECTED )
      break;
    else
      delay(WIFI_MULTI_CONNECT_WAITING_MS);
  }

  if ( status == WL_CONNECTED )
  {
    WFM_LOGERROR1(F("WiFi connected after time: "), i);
    WFM_LOGERROR3(F("SSID:"), WiFi.SSID(), F(",RSSI="), WiFi.RSSI());

#if (ESP32 || ESP8266)
    WFM_LOGERROR3(F("Channel:"), WiFi.channel(), F(",IP address:"), WiFi.localIP() );
#else
    WFM_LOGERROR1(F("IP address:"), WiFi.localIP() );
#endif
  }
  else
  {
    WFM_LOGERROR(F("WiFi not connected"));

    if (wifiMulti.run() != WL_CONNECTED)
    {
      Serial.println("WiFi not connected!");
      delay(1000);
    }
  }

  return status;
}

void loop()
{
  if ( (WiFi.status() != WL_CONNECTED) )
  {
    connectMultiWiFi();
  }
}
```

#### 2. File [defines.h](examples/WiFiMulti/defines.h)

```cpp
#ifndef defines_h
#define defines_h

#define DEBUG_WIFI_MULTI_GENERIC_PORT   Serial

// Debug Level from 0 to 4
#define _WIFIMULTI_LOGLEVEL_            4

#define _WIFI_LOGLEVEL_                 1
#define _WIFININA_LOGLEVEL_             3


#if ( defined(ARDUINO_PORTENTA_H7_M7) || defined(ARDUINO_PORTENTA_H7_M4) )

  #if defined(BOARD_NAME)
    #undef BOARD_NAME
  #endif

  #if defined(CORE_CM7)
    #warning Using Portenta H7 M7 core
    #define BOARD_NAME            "PORTENTA_H7_M7"
  #else
    #warning Using Portenta H7 M4 core
    #define BOARD_NAME            "PORTENTA_H7_M4"
  #endif

  #define USE_WIFI_PORTENTA_H7  true

  #define USE_WIFI_NINA         false

  // To use the default WiFi library here 
  #define USE_WIFI_CUSTOM       false

  #error USE_WIFI_PORTENTA_H7 not ready yet
  
#elif (ESP32)

  #define USE_WIFI_NINA         false

  // To use the default WiFi library here 
  #define USE_WIFI_CUSTOM       false

#elif (ESP8266)

  #define USE_WIFI_NINA         false

  // To use the default WiFi library here 
  #define USE_WIFI_CUSTOM       true

#elif ( defined(ARDUINO_SAMD_MKR1000)  || defined(ARDUINO_SAMD_MKRWIFI1010) )

  #define USE_WIFI_NINA         false
  #define USE_WIFI101           true
  #define USE_WIFI_CUSTOM       false

#elif ( defined(ARDUINO_NANO_RP2040_CONNECT) || defined(ARDUINO_SAMD_NANO_33_IOT) )

  #define USE_WIFI_NINA         true
  #define USE_WIFI101           false
  #define USE_WIFI_CUSTOM       false

#elif ( defined(ARDUINO_AVR_UNO_WIFI_REV2) || defined(ARDUINO_AVR_NANO_EVERY) )

  #error UNO_WIFI_REV2 and NANO_EVERY not supported yet

#elif ( defined(ARDUINO_AVR_UNO_WIFI_REV2) || defined(ARDUINO_AVR_NANO_EVERY) )

  #error UNO_WIFI_REV2 and NANO_EVERY not supported yet  
  
#else

  #define USE_WIFI_NINA         false
  #define USE_WIFI101           false
  
  // If not USE_WIFI_NINA, you can USE_WIFI_CUSTOM, then include the custom WiFi library here 
  #define USE_WIFI_CUSTOM       true

#endif

#define WIFI_USING_ESP8266_AT_WEBSERVER         false

#if (!USE_WIFI_NINA && USE_WIFI_CUSTOM)
  #if (ESP8266)
    #include "ESP8266WiFi.h"
  #elif WIFI_USING_ESP8266_AT_WEBSERVER
    #warning WIFI_USING_ESP8266_AT_WEBSERVER
    #error WIFI_USING_ESP8266_AT_WEBSERVER not ready yet
    #include "ESP8266_AT_WebServer.h"
    #define WIFI_USING_ESP_AT     true
  #else
    #warning WIFI_USING_WIFIESPAT
   //#include "WiFi_XYZ.h"
    #include "WiFiEspAT.h"
    #define WIFI_USING_ESP_AT     true  
  #endif
#endif

#if WIFI_USING_ESP_AT
  #define EspSerial       Serial1
#endif

#if USE_WIFI_PORTENTA_H7
  #warning Using Portenta H7 WiFi
  #define SHIELD_TYPE           "Portenta_H7 WiFi"
#elif USE_WIFI_NINA
  #warning Using WiFiNINA using WiFiNINA_Generic Library
  #define SHIELD_TYPE           "WiFiNINA using WiFiNINA_Generic Library"
#elif USE_WIFI101
  #warning Using WiFi101 using WiFi101 Library
  #error USE_WIFI101 not ready yet
  #define SHIELD_TYPE           "WiFi101 using WiFi101 Library"
#elif (ESP32 || ESP8266)
  #warning Using ESP WiFi with WiFi Library
  #define SHIELD_TYPE           "ESP WiFi using WiFi Library"  
#elif USE_WIFI_CUSTOM
  #warning Using Custom WiFi using Custom WiFi Library
  #define SHIELD_TYPE           "Custom WiFi using Custom WiFi Library"
#else
  #define SHIELD_TYPE           "Unknown WiFi shield/Library" 
#endif

#if ( defined(NRF52840_FEATHER) || defined(NRF52832_FEATHER) || defined(NRF52_SERIES) || defined(ARDUINO_NRF52_ADAFRUIT) || \
        defined(NRF52840_FEATHER_SENSE) || defined(NRF52840_ITSYBITSY) || defined(NRF52840_CIRCUITPLAY) || defined(NRF52840_CLUE) || \
        defined(NRF52840_METRO) || defined(NRF52840_PCA10056) || defined(PARTICLE_XENON) || defined(NINA_B302_ublox) || defined(NINA_B112_ublox) )
  #if defined(WIFI_USE_NRF528XX)
    #undef WIFI_USE_NRF528XX
  #endif
  #define WIFI_USE_NRF528XX          true
#endif

#if    ( defined(ARDUINO_SAMD_ZERO) || defined(ARDUINO_SAMD_MKR1000) || defined(ARDUINO_SAMD_MKRWIFI1010) \
      || defined(ARDUINO_SAMD_NANO_33_IOT) || defined(ARDUINO_SAMD_MKRFox1200) || defined(ARDUINO_SAMD_MKRWAN1300) || defined(ARDUINO_SAMD_MKRWAN1310) \
      || defined(ARDUINO_SAMD_MKRGSM1400) || defined(ARDUINO_SAMD_MKRNB1500) || defined(ARDUINO_SAMD_MKRVIDOR4000) || defined(__SAMD21G18A__) \
      || defined(ARDUINO_SAMD_CIRCUITPLAYGROUND_EXPRESS) || defined(__SAMD21E18A__) || defined(__SAMD51__) || defined(__SAMD51J20A__) || defined(__SAMD51J19A__) \
      || defined(__SAMD51G19A__) || defined(__SAMD51P19A__) || defined(__SAMD21G18A__) )
  #if defined(WIFI_USE_SAMD)
    #undef WIFI_USE_SAMD
  #endif
  #define WIFI_USE_SAMD      true
#endif

#if ( defined(ARDUINO_SAM_DUE) || defined(__SAM3X8E__) )
  #if defined(WIFI_USE_SAM_DUE)
    #undef WIFI_USE_SAM_DUE
  #endif
  #define WIFI_USE_SAM_DUE      true
  #warning Use SAM_DUE architecture
#endif

#if ( defined(STM32F0) || defined(STM32F1) || defined(STM32F2) || defined(STM32F3)  ||defined(STM32F4) || defined(STM32F7) || \
       defined(STM32L0) || defined(STM32L1) || defined(STM32L4) || defined(STM32H7)  ||defined(STM32G0) || defined(STM32G4) || \
       defined(STM32WB) || defined(STM32MP1) ) && ! ( defined(ARDUINO_PORTENTA_H7_M7) || defined(ARDUINO_PORTENTA_H7_M4) )
  #if defined(WIFI_USE_STM32)
    #undef WIFI_USE_STM32
  #endif
  #define WIFI_USE_STM32      true
#endif

#if ( defined(ARDUINO_NANO_RP2040_CONNECT) || defined(ARDUINO_ARCH_RP2040) || defined(ARDUINO_RASPBERRY_PI_PICO) || \
      defined(ARDUINO_ADAFRUIT_FEATHER_RP2040) || defined(ARDUINO_GENERIC_RP2040) )
  #warning RP2040-based board selected

  #if defined(WIFI_USE_RP2040)
    #undef WIFI_USE_RP2040
  #endif
  #define WIFI_USE_RP2040      true
  #warning Use RP2040 architecture from WiFiMulti_Generic
#endif

#ifdef CORE_TEENSY
  #if defined(__IMXRT1062__)
    // For Teensy 4.1/4.0
    #define BOARD_TYPE      "TEENSY 4.1/4.0"
  #elif defined(__MK66FX1M0__)
    #define BOARD_TYPE "Teensy 3.6"
  #elif defined(__MK64FX512__)
    #define BOARD_TYPE "Teensy 3.5"
  #elif defined(__MKL26Z64__)
    #define BOARD_TYPE "Teensy LC"
  #elif defined(__MK20DX256__)
    #define BOARD_TYPE "Teensy 3.2" // and Teensy 3.1 (obsolete)
  #elif defined(__MK20DX128__)
    #define BOARD_TYPE "Teensy 3.0"
  #elif defined(__AVR_AT90USB1286__)
    #error Teensy 2.0++ not supported yet
  #elif defined(__AVR_ATmega32U4__)
    #error Teensy 2.0 not supported yet
  #else
    // For Other Boards
    #define BOARD_TYPE      "Unknown Teensy Board"
  #endif

#elif defined(WIFI_USE_NRF528XX)
  #if defined(NRF52840_FEATHER)
    #define BOARD_TYPE      "NRF52840_FEATHER_EXPRESS"
  #elif defined(NRF52832_FEATHER)
    #define BOARD_TYPE      "NRF52832_FEATHER"
  #elif defined(NRF52840_FEATHER_SENSE)
    #define BOARD_TYPE      "NRF52840_FEATHER_SENSE"
  #elif defined(NRF52840_ITSYBITSY)
    #define BOARD_TYPE      "NRF52840_ITSYBITSY_EXPRESS"
  #elif defined(NRF52840_CIRCUITPLAY)
    #define BOARD_TYPE      "NRF52840_CIRCUIT_PLAYGROUND"
  #elif defined(NRF52840_CLUE)
    #define BOARD_TYPE      "NRF52840_CLUE"
  #elif defined(NRF52840_METRO)
    #define BOARD_TYPE      "NRF52840_METRO_EXPRESS"
  #elif defined(NRF52840_PCA10056)
    #define BOARD_TYPE      "NORDIC_NRF52840DK"
  #elif defined(NINA_B302_ublox)
    #define BOARD_TYPE      "NINA_B302_ublox"
  #elif defined(NINA_B112_ublox)
    #define BOARD_TYPE      "NINA_B112_ublox"
  #elif defined(PARTICLE_XENON)
    #define BOARD_TYPE      "PARTICLE_XENON"
  #elif defined(MDBT50Q_RX)
    #define BOARD_TYPE      "RAYTAC_MDBT50Q_RX"
  #elif defined(ARDUINO_NRF52_ADAFRUIT)
    #define BOARD_TYPE      "ARDUINO_NRF52_ADAFRUIT"
  #else
    #define BOARD_TYPE      "nRF52 Unknown"
  #endif

#elif defined(WIFI_USE_SAMD)
  #if defined(ARDUINO_SAMD_ZERO)
    #define BOARD_TYPE      "SAMD Zero"
  #elif defined(ARDUINO_SAMD_MKR1000)
    #define BOARD_TYPE      "SAMD MKR1000"
  #elif defined(ARDUINO_SAMD_MKRWIFI1010)
    #define BOARD_TYPE      "SAMD MKRWIFI1010"
  #elif defined(ARDUINO_SAMD_NANO_33_IOT)
    #define BOARD_TYPE      "SAMD NANO_33_IOT"
  #elif defined(ARDUINO_SAMD_MKRFox1200)
    #define BOARD_TYPE      "SAMD MKRFox1200"
  #elif ( defined(ARDUINO_SAMD_MKRWAN1300) || defined(ARDUINO_SAMD_MKRWAN1310) )
    #define BOARD_TYPE      "SAMD MKRWAN13X0"
  #elif defined(ARDUINO_SAMD_MKRGSM1400)
    #define BOARD_TYPE      "SAMD MKRGSM1400"
  #elif defined(ARDUINO_SAMD_MKRNB1500)
    #define BOARD_TYPE      "SAMD MKRNB1500"
  #elif defined(ARDUINO_SAMD_MKRVIDOR4000)
    #define BOARD_TYPE      "SAMD MKRVIDOR4000"
  #elif defined(ARDUINO_SAMD_CIRCUITPLAYGROUND_EXPRESS)
    #define BOARD_TYPE      "SAMD ARDUINO_SAMD_CIRCUITPLAYGROUND_EXPRESS"
  #elif defined(ADAFRUIT_FEATHER_M0_EXPRESS)
    #define BOARD_TYPE      "SAMD21 ADAFRUIT_FEATHER_M0_EXPRESS"
  #elif defined(ADAFRUIT_METRO_M0_EXPRESS)
    #define BOARD_TYPE      "SAMD21 ADAFRUIT_METRO_M0_EXPRESS"
  #elif defined(ADAFRUIT_CIRCUITPLAYGROUND_M0)
    #define BOARD_TYPE      "SAMD21 ADAFRUIT_CIRCUITPLAYGROUND_M0"
  #elif defined(ADAFRUIT_GEMMA_M0)
    #define BOARD_TYPE      "SAMD21 ADAFRUIT_GEMMA_M0"
  #elif defined(ADAFRUIT_TRINKET_M0)
    #define BOARD_TYPE      "SAMD21 ADAFRUIT_TRINKET_M0"
  #elif defined(ADAFRUIT_ITSYBITSY_M0)
    #define BOARD_TYPE      "SAMD21 ADAFRUIT_ITSYBITSY_M0"
  #elif defined(ARDUINO_SAMD_HALLOWING_M0)
    #define BOARD_TYPE      "SAMD21 ARDUINO_SAMD_HALLOWING_M0"
  #elif defined(ADAFRUIT_METRO_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_METRO_M4_EXPRESS"
  #elif defined(ADAFRUIT_GRAND_CENTRAL_M4)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_GRAND_CENTRAL_M4"
  #elif defined(ADAFRUIT_FEATHER_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_FEATHER_M4_EXPRESS"
  #elif defined(ADAFRUIT_ITSYBITSY_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_ITSYBITSY_M4_EXPRESS"
  #elif defined(ADAFRUIT_TRELLIS_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_TRELLIS_M4_EXPRESS"
  #elif defined(ADAFRUIT_PYPORTAL)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_PYPORTAL"
  #elif defined(ADAFRUIT_PYPORTAL_M4_TITANO)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_PYPORTAL_M4_TITANO"
  #elif defined(ADAFRUIT_PYBADGE_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_PYBADGE_M4_EXPRESS"
  #elif defined(ADAFRUIT_METRO_M4_AIRLIFT_LITE)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_METRO_M4_AIRLIFT_LITE"
  #elif defined(ADAFRUIT_PYGAMER_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_PYGAMER_M4_EXPRESS"
  #elif defined(ADAFRUIT_PYGAMER_ADVANCE_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_PYGAMER_ADVANCE_M4_EXPRESS"
  #elif defined(ADAFRUIT_PYBADGE_AIRLIFT_M4)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_PYBADGE_AIRLIFT_M4"
  #elif defined(ADAFRUIT_MONSTER_M4SK_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_MONSTER_M4SK_EXPRESS"
  #elif defined(ADAFRUIT_HALLOWING_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_HALLOWING_M4_EXPRESS"
  #elif defined(SEEED_WIO_TERMINAL)
    #define BOARD_TYPE      "SAMD SEEED_WIO_TERMINAL"
  #elif defined(SEEED_FEMTO_M0)
    #define BOARD_TYPE      "SAMD SEEED_FEMTO_M0"
  #elif defined(SEEED_XIAO_M0)
    #define BOARD_TYPE      "SAMD SEEED_XIAO_M0"
  #elif defined(Wio_Lite_MG126)
    #define BOARD_TYPE      "SAMD SEEED Wio_Lite_MG126"
  #elif defined(WIO_GPS_BOARD)
    #define BOARD_TYPE      "SAMD SEEED WIO_GPS_BOARD"
  #elif defined(SEEEDUINO_ZERO)
    #define BOARD_TYPE      "SAMD SEEEDUINO_ZERO"
  #elif defined(SEEEDUINO_LORAWAN)
    #define BOARD_TYPE      "SAMD SEEEDUINO_LORAWAN"
  #elif defined(SEEED_GROVE_UI_WIRELESS)
    #define BOARD_TYPE      "SAMD SEEED_GROVE_UI_WIRELESS"
  #elif defined(__SAMD21E18A__)
    #define BOARD_TYPE      "SAMD21E18A"
  #elif defined(__SAMD21G18A__)
    #define BOARD_TYPE      "SAMD21G18A"
  #elif defined(__SAMD51G19A__)
    #define BOARD_TYPE      "SAMD51G19A"
  #elif defined(__SAMD51J19A__)
    #define BOARD_TYPE      "SAMD51J19A"
  #elif defined(__SAMD51P19A__)
    #define BOARD_TYPE      "__SAMD51P19A__"
  #elif defined(__SAMD51J20A__)
    #define BOARD_TYPE      "SAMD51J20A"
  #elif defined(__SAM3X8E__)
    #define BOARD_TYPE      "SAM3X8E"
  #elif defined(__CPU_ARC__)
    #define BOARD_TYPE      "CPU_ARC"
  #elif defined(__SAMD51__)
    #define BOARD_TYPE      "SAMD51"
  #else
    #define BOARD_TYPE      "SAMD Unknown"
  #endif

#elif defined(WIFI_USE_STM32)
  #if defined(STM32F0)
    #warning STM32F0 board selected
    #define BOARD_TYPE  "STM32F0"
  #elif defined(STM32F1)
    #warning STM32F1 board selected
    #define BOARD_TYPE  "STM32F1"
  #elif defined(STM32F2)
    #warning STM32F2 board selected
    #define BOARD_TYPE  "STM32F2"
  #elif defined(STM32F3)
    #warning STM32F3 board selected
    #define BOARD_TYPE  "STM32F3"
  #elif defined(STM32F4)
    #warning STM32F4 board selected
    #define BOARD_TYPE  "STM32F4"
  #elif defined(STM32F7)
    #warning STM32F7 board selected
    #define BOARD_TYPE  "STM32F7"
  #elif defined(STM32L0)
    #warning STM32L0 board selected
    #define BOARD_TYPE  "STM32L0"
  #elif defined(STM32L1)
    #warning STM32L1 board selected
    #define BOARD_TYPE  "STM32L1"
  #elif defined(STM32L4)
    #warning STM32L4 board selected
    #define BOARD_TYPE  "STM32L4"
  #elif defined(STM32H7)
    #warning STM32H7 board selected
    #define BOARD_TYPE  "STM32H7"
  #elif defined(STM32G0)
    #warning STM32G0 board selected
    #define BOARD_TYPE  "STM32G0"
  #elif defined(STM32G4)
    #warning STM32G4 board selected
    #define BOARD_TYPE  "STM32G4"
  #elif defined(STM32WB)
    #warning STM32WB board selected
    #define BOARD_TYPE  "STM32WB"
  #elif defined(STM32MP1)
    #warning STM32MP1 board selected
    #define BOARD_TYPE  "STM32MP1"
  #else
    #warning STM32 unknown board selected
    #define BOARD_TYPE  "STM32 Unknown"
  #endif

#elif defined(ESP32)

  #warning ESP32 board selected
  #define BOARD_TYPE  "ESP32"
  
#elif defined(ESP8266)

  #warning ESP8266 board selected
  #define BOARD_TYPE  "ESP8266"

#elif WIFI_USE_RP2040

  #warning RP2040 board selected

#elif WIFI_USE_SAM_DUE  

  #warning SAM DUE board selected
  
#else

  #error AVR Mega, UNO, Nano, etc.  not supported yet
  #define BOARD_TYPE      "AVR Mega"
  
#endif

#ifndef BOARD_NAME
  #if defined(ARDUINO_BOARD)
    #define BOARD_NAME    ARDUINO_BOARD
  #elif defined(BOARD_TYPE)
    #define BOARD_NAME    BOARD_TYPE
  #else
    #define BOARD_NAME    "Unknown Board"
  #endif  
#endif

#include <WiFiMulti_Generic.h>

char your_ssid[] = "YOUR_SSID";        // your network SSID (name)
char your_pass[] = "12345678";        // your network password

#endif    //defines_h
```

---
---

### Debug Terminal Output Samples

#### 1. WiFiMulti on RASPBERRY_PI_PICO

The following are debug terminal output when running example [WiFiMulti](examples/WiFiMulti) on `RASPBERRY_PI_PICO` with ESP8266_AT shield using [RP2040 arduino-pico core](https://github.com/earlephilhower/arduino-pico) and [WiFiEspAT](https://github.com/jandrassy/WiFiEspAT) library

#### 1.1 First time => OK

```
Starting WiFiMulti on RASPBERRY_PI_PICO
WiFiMulti_Generic v1.0.0
WiFi shield init done
[WFM] [addAP] add SSID: HueNet1
[WFM] [addAP] add SSID: HueNet2
Connecting WiFi...
[WFM] [run] Scan done
[WFM] [run] Number of Networks found: 6
==============================================================
[WFM] Unknown => # 0 , Channel: 10
[WFM] 4D:AB:D3:E0:38:60
[WFM] SSID: HueNet , RSSI: -24 , Secured: y
==============================================================
[WFM]   Known => # 1 , Channel: 2
[WFM] A5:F4:94:74:7F:68
[WFM] SSID: HueNet1 , RSSI: -33 , Secured: y
==============================================================
[WFM] Unknown => # 2 , Channel: 11
[WFM] F1:9:E3:66:90:3C
[WFM] SSID: HueNetTek , RSSI: -33 , Secured: y
==============================================================
[WFM]   Known => # 3 , Channel: 4
[WFM] E1:EB:E2:E0:38:60
[WFM] SSID: HueNet2 , RSSI: -56 , Secured: y
==============================================================
[WFM] Unknown => # 4 , Channel: 1
[WFM] A6:2:69:6D:2C:E8
[WFM] SSID: SmartRG-02a2 , RSSI: -66 , Secured: y
==============================================================
[WFM] Unknown => # 5 , Channel: 0
[WFM] 1:BF:BA:9C:80:85
[WFM] SSID: -71 , RSSI: 8 , Secured: y
==============================================================
[run] Connecting BSSID: [WFM] A5:F4:94:74:7F:68
[WFM] SSID:  HueNet1 , Channel:  2 , Best dB:  -33
[WFM] [run] Connecting done.
[WFM] [run] SSID:  HueNet1 , IP:  192.168.2.109

WiFi connected, IP address: 192.168.2.109
```

#### 1.2 Lost WiFi => Scan and auto-reconnect

```
WiFi lost. Trying to scan and reconnect
[WFM] [run] Scan done
[WFM] [run] Number of Networks found: 6
==============================================================
[WFM] Unknown => # 0 , Channel: 10
[WFM] 4D:AB:D3:E0:38:60
[WFM] SSID: HueNet , RSSI: -26 , Secured: y
==============================================================
[WFM] Unknown => # 1 , Channel: 11
[WFM] F1:9:E3:66:90:3C
[WFM] SSID: HueNetTek , RSSI: -38 , Secured: y
==============================================================
[WFM]   Known => # 2 , Channel: 4
[WFM] E1:EB:E2:E0:38:60
[WFM] SSID: HueNet2 , RSSI: -57 , Secured: y
==============================================================
[WFM] Unknown => # 3 , Channel: 5
[WFM] 8A:20:11:2A:C3:E4
[WFM] SSID: DECO-5655 , RSSI: -70 , Secured: y
==============================================================
[WFM] Unknown => # 4 , Channel: 1
[WFM] A6:2:69:6D:2C:E8
[WFM] SSID: SmartRG-02a2 , RSSI: -72 , Secured: y
==============================================================
[WFM] Unknown => # 5 , Channel: 1
[WFM] 16:49:8A:35:94:C0
[WFM] SSID: Access , RSSI: -77 , Secured: y
==============================================================
[run] Connecting BSSID: [WFM] E1:EB:E2:E0:38:60
[WFM] SSID:  HueNet2 , Channel:  4 , Best dB:  -57
[WFM] [run] Connecting done.
[WFM] [run] SSID:  HueNet2 , IP:  192.168.2.109
[WFM] WiFi connected after time:  1
[WFM] SSID: HueNet2 ,RSSI= -65
[WFM] IP address: 192.168.2.109
```

---

#### 2. WiFiMulti on MBED RaspberryPi Pico

The following are debug terminal output when running example [WiFiMulti](examples/WiFiMulti) on `RaspberryPi Pico` with ESP8266_AT shield using [ArduinoCore-mbed mbed_rp2040 core](https://github.com/arduino/ArduinoCore-mbed) and [WiFiEspAT](https://github.com/jandrassy/WiFiEspAT) library

#### 2.1 First time => OK

```
Starting WiFiMulti on RaspberryPi Pico
WiFiMulti_Generic v1.0.0
WiFi shield init done
[WFM] [addAP] add SSID: HueNet1
[WFM] [addAP] add SSID: HueNet2
Connecting WiFi...
[WFM] [run] Scan done
[WFM] [run] Number of Networks found: 6
==============================================================
[WFM] Unknown => # 0 , Channel: 10
[WFM] 4D:AB:D3:E0:38:60
[WFM] SSID: HueNet , RSSI: -23 , Secured: y
==============================================================
[WFM]   Known => # 1 , Channel: 2
[WFM] A5:F4:94:74:7F:68
[WFM] SSID: HueNet1 , RSSI: -35 , Secured: y
==============================================================
[WFM] Unknown => # 2 , Channel: 11
[WFM] F1:9:E3:66:90:3C
[WFM] SSID: HueNetTek , RSSI: -35 , Secured: y
==============================================================
[WFM]   Known => # 3 , Channel: 4
[WFM] E1:EB:E2:E0:38:60
[WFM] SSID: HueNet2 , RSSI: -57 , Secured: y
==============================================================
[WFM] Unknown => # 4 , Channel: 1
[WFM] A6:2:69:6D:2C:E8
[WFM] SSID: SmartRG-02a2 , RSSI: -64 , Secured: y
==============================================================
[WFM] Unknown => # 5 , Channel: 3
[WFM] 15:F8:3F:80:9F:E8
[WFM] SSID: Linksys00043 , RSSI: -71 , Secured: y
==============================================================
[run] Connecting BSSID: [WFM] A5:F4:94:74:7F:68
[WFM] SSID:  HueNet1 , Channel:  2 , Best dB:  -35
[WFM] [run] Connecting done.
[WFM] [run] SSID:  HueNet1 , IP:  192.168.2.109

WiFi connected, IP address: 192.168.2.109
```

#### 2.2 Lost WiFi => Scan and auto-reconnect

```
WiFi lost. Trying to scan and reconnect
[WFM] [run] Scan done
[WFM] [run] Number of Networks found: 6
==============================================================
[WFM] Unknown => # 0 , Channel: 10
[WFM] 4D:AB:D3:E0:38:60
[WFM] SSID: HueNet , RSSI: -25 , Secured: y
==============================================================
[WFM] Unknown => # 1 , Channel: 11
[WFM] F1:9:E3:66:90:3C
[WFM] SSID: HueNetTek , RSSI: -42 , Secured: y
==============================================================
[WFM]   Known => # 2 , Channel: 4
[WFM] E1:EB:E2:E0:38:60
[WFM] SSID: HueNet2 , RSSI: -60 , Secured: y
==============================================================
[WFM] Unknown => # 3 , Channel: 1
[WFM] A6:2:69:6D:2C:E8
[WFM] SSID: SmartRG-02a2 , RSSI: -69 , Secured: y
==============================================================
[WFM] Unknown => # 4 , Channel: 0
[WFM] 5:8A:20:11:2A:C3
[WFM] SSID: -74 , RSSI: 0 , Secured: y
==============================================================
[WFM] Unknown => # 5 , Channel: 5
[WFM] 8A:20:11:2A:C3:E4
[WFM] SSID: DECO-5655 , RSSI: -75 , Secured: y
==============================================================
[run] Connecting BSSID: [WFM] E1:EB:E2:E0:38:60
[WFM] SSID:  HueNet2 , Channel:  4 , Best dB:  -60
[WFM] [run] Connecting done.
[WFM] [run] SSID:  HueNet2 , IP:  192.168.2.109
[WFM] WiFi connected after time:  1
[WFM] SSID: HueNet2 ,RSSI= -63
[WFM] IP address: 192.168.2.109
```


---

#### 3. WiFiMulti on Nano RP2040 Connect

The following are debug terminal output when running example [WiFiMulti](examples/WiFiMulti) on `Nano RP2040 Connect` with WiFiNINA shield using [ArduinoCore-mbed mbed_rp2040 core](https://github.com/arduino/ArduinoCore-mbed) and [WiFiNINA_Generic](https://github.com/khoih-prog/WiFiNINA_Generic) library

#### 3.1 First time => OK

```
Starting WiFiMulti on Nano RP2040 Connect
WiFiMulti_Generic v1.0.0
[WFM] [addAP] add SSID: HueNet1
[WFM] [addAP] add SSID: HueNet2
Connecting WiFi...
[WFM] [run] Scan done
[WFM] [run] Number of Networks found: 10
==============================================================
[WFM] Unknown => # 0 , Channel: 10
[WFM] 4D:AB:D3:E0:38:60
[WFM] SSID: HueNet , RSSI: -19 , Secured: y
==============================================================
[WFM]   Known => # 1 , Channel: 2
[WFM] A5:F4:94:74:7F:68
[WFM] SSID: HueNet1 , RSSI: -23 , Secured: y
==============================================================
[WFM]   Known => # 2 , Channel: 4
[WFM] E1:EB:E2:E0:38:60
[WFM] SSID: HueNet2 , RSSI: -49 , Secured: y
==============================================================
[WFM] Unknown => # 3 , Channel: 1
[WFM] A6:2:69:6D:2C:E8
[WFM] SSID: SmartRG-02a2 , RSSI: -72 , Secured: y
==============================================================
[WFM] Unknown => # 4 , Channel: 11
[WFM] F1:9:E3:66:90:3C
[WFM] SSID: HueNetTek , RSSI: -75 , Secured: y
==============================================================
[WFM] Unknown => # 5 , Channel: 1
[WFM] 16:49:8A:35:94:C0
[WFM] SSID: Access , RSSI: -79 , Secured: y
==============================================================
[WFM] Unknown => # 6 , Channel: 1
[WFM] D5:1C:15:BC:FA:EE
[WFM] SSID: ESP151CD5 , RSSI: -79 , Secured: y
==============================================================
[WFM] Unknown => # 7 , Channel: 3
[WFM] EA:73:DC:D2:B4:F2
[WFM] SSID: FishBowl , RSSI: -81 , Secured: y
==============================================================
[WFM] Unknown => # 8 , Channel: 5
[WFM] E6:D:11:2A:C3:E4
[WFM] SSID: DECO-5655 , RSSI: -82 , Secured: y
==============================================================
[WFM] Unknown => # 9 , Channel: 5
[WFM] 28:ED:8:2E:8F:68
[WFM] SSID: rogers786 , RSSI: -82 , Secured: y
==============================================================
[run] Connecting BSSID: [WFM] A5:F4:94:74:7F:68
[WFM] SSID:  HueNet1 , Channel:  2 , Best dB:  -23
[WFM] [run] Connecting done.
[WFM] [run] SSID:  HueNet1 , IP:  192.168.2.105

WiFi connected, IP address: 192.168.2.105
```

#### 3.2 Lost WiFi => Scan and auto-reconnect

```
WiFi lost. Trying to scan and reconnect
[WFM] [run] Scan done
[WFM] [run] Number of Networks found: 10
==============================================================
[WFM] Unknown => # 0 , Channel: 10
[WFM] 4D:AB:D3:E0:38:60
[WFM] SSID: HueNet , RSSI: -22 , Secured: y
==============================================================
[WFM] Unknown => # 1 , Channel: 11
[WFM] F1:9:E3:66:90:3C
[WFM] SSID: HueNetTek , RSSI: -32 , Secured: y
==============================================================
[WFM]   Known => # 2 , Channel: 4
[WFM] E1:EB:E2:E0:38:60
[WFM] SSID: HueNet2 , RSSI: -53 , Secured: y
==============================================================
[WFM] Unknown => # 3 , Channel: 1
[WFM] D5:1C:15:BC:FA:EE
[WFM] SSID: ESP151CD5 , RSSI: -77 , Secured: y
==============================================================
[WFM] Unknown => # 4 , Channel: 1
[WFM] A6:2:69:6D:2C:E8
[WFM] SSID: SmartRG-02a2 , RSSI: -80 , Secured: y
==============================================================
[WFM] Unknown => # 5 , Channel: 1
[WFM] 16:49:8A:35:94:C0
[WFM] SSID: Access , RSSI: -81 , Secured: y
==============================================================
[WFM] Unknown => # 6 , Channel: 5
[WFM] E6:D:11:2A:C3:E4
[WFM] SSID: DECO-5655 , RSSI: -83 , Secured: y
==============================================================
[WFM] Unknown => # 7 , Channel: 5
[WFM] E6:D:11:2A:C3:EA
[WFM] SSID: Guest5655 , RSSI: -83 , Secured: y
==============================================================
[WFM] Unknown => # 8 , Channel: 5
[WFM] 8A:20:11:2A:C3:E4
[WFM] SSID: DECO-5655 , RSSI: -84 , Secured: y
==============================================================
[WFM] Unknown => # 9 , Channel: 11
[WFM] 58:9:B:2E:8F:68
[WFM] SSID: Rogers 786 , RSSI: -85 , Secured: y
==============================================================
[run] Connecting BSSID: [WFM] E1:EB:E2:E0:38:60
[WFM] SSID:  HueNet2 , Channel:  4 , Best dB:  -53
[WFM] [run] Connecting done.
[WFM] [run] SSID:  HueNet2 , IP:  192.168.2.105
[WFM] WiFi connected after time:  1
[WFM] SSID: HueNet2 ,RSSI= -47
[WFM] IP address: 192.168.2.105
```

---

#### 4. WiFiMulti on NANO_RP2040_CONNECT

The following are debug terminal output when running example [WiFiMulti](examples/WiFiMulti) on `NANO_RP2040_CONNECT` with ESP8266_AT shield using [RP2040 arduino-pico core](https://github.com/earlephilhower/arduino-pico) and [WiFiNINA_Generic](https://github.com/khoih-prog/WiFiNINA_Generic) library

#### 4.1 First time => OK

```
Starting WiFiMulti on NANO_RP2040_CONNECT
WiFiMulti_Generic v1.0.0
[WFM] [addAP] add SSID: HueNet1
[WFM] [addAP] add SSID: HueNet2
Connecting WiFi...
[WFM] [run] Scan done
[WFM] [run] Number of Networks found: 10
==============================================================
[WFM]   Known => # 0 , Channel: 2
[WFM] A5:F4:94:74:7F:68
[WFM] SSID: HueNet1 , RSSI: -17 , Secured: y
==============================================================
[WFM] Unknown => # 1 , Channel: 10
[WFM] 4D:AB:D3:E0:38:60
[WFM] SSID: HueNet , RSSI: -21 , Secured: y
==============================================================
[WFM] Unknown => # 2 , Channel: 11
[WFM] F1:9:E3:66:90:3C
[WFM] SSID: HueNetTek , RSSI: -31 , Secured: y
==============================================================
[WFM] Unknown => # 3 , Channel: 4
[WFM] E1:EB:E2:E0:38:60
[WFM] SSID: HueNet2 , RSSI: -50 , Secured: y
==============================================================
[WFM] Unknown => # 4 , Channel: 1
[WFM] A6:2:69:6D:2C:E8
[WFM] SSID: SmartRG-02a2 , RSSI: -72 , Secured: y
==============================================================
[WFM] Unknown => # 5 , Channel: 1
[WFM] D5:1C:15:BC:FA:EE
[WFM] SSID: ESP151CD5 , RSSI: -83 , Secured: y
==============================================================
[WFM] Unknown => # 6 , Channel: 3
[WFM] EA:73:DC:D2:B4:F2
[WFM] SSID: FishBowl , RSSI: -83 , Secured: y
==============================================================
[WFM] Unknown => # 7 , Channel: 6
[WFM] 42:8E:4D:42:5E:F8
[WFM] SSID: El khoury , RSSI: -85 , Secured: y
==============================================================
[WFM] Unknown => # 8 , Channel: 6
[WFM] 7:9:F8:1:F2:40
[WFM] SSID: BELL627 , RSSI: -87 , Secured: y
==============================================================
[WFM] Unknown => # 9 , Channel: 11
[WFM] A0:E9:61:BF:92:F4
[WFM] SSID: house , RSSI: -88 , Secured: y
==============================================================
[run] Connecting BSSID: [WFM] A5:F4:94:74:7F:68
[WFM] SSID:  HueNet1 , Channel:  2 , Best dB:  -17
[WFM] [run] Connecting done.
[WFM] [run] SSID:  HueNet1 , IP:  192.168.2.105

WiFi connected, IP address: 192.168.2.105
```

#### 4.2 Lost WiFi => Scan and auto-reconnect

```
WiFi lost. Trying to scan and reconnect
[WFM] [run] Scan done
[WFM] [run] Number of Networks found: 10
==============================================================
[WFM] Unknown => # 0 , Channel: 10
[WFM] 4D:AB:D3:E0:38:60
[WFM] SSID: HueNet , RSSI: -22 , Secured: y
==============================================================
[WFM] Unknown => # 1 , Channel: 11
[WFM] F1:9:E3:66:90:3C
[WFM] SSID: HueNetTek , RSSI: -32 , Secured: y
==============================================================
[WFM]   Known => # 2 , Channel: 4
[WFM] E1:EB:E2:E0:38:60
[WFM] SSID: HueNet2 , RSSI: -53 , Secured: y
==============================================================
[WFM] Unknown => # 3 , Channel: 1
[WFM] D5:1C:15:BC:FA:EE
[WFM] SSID: ESP151CD5 , RSSI: -77 , Secured: y
==============================================================
[WFM] Unknown => # 4 , Channel: 1
[WFM] A6:2:69:6D:2C:E8
[WFM] SSID: SmartRG-02a2 , RSSI: -80 , Secured: y
==============================================================
[WFM] Unknown => # 5 , Channel: 1
[WFM] 16:49:8A:35:94:C0
[WFM] SSID: Access , RSSI: -81 , Secured: y
==============================================================
[WFM] Unknown => # 6 , Channel: 5
[WFM] E6:D:11:2A:C3:E4
[WFM] SSID: DECO-5655 , RSSI: -83 , Secured: y
==============================================================
[WFM] Unknown => # 7 , Channel: 5
[WFM] E6:D:11:2A:C3:EA
[WFM] SSID: Guest5655 , RSSI: -83 , Secured: y
==============================================================
[WFM] Unknown => # 8 , Channel: 5
[WFM] 8A:20:11:2A:C3:E4
[WFM] SSID: DECO-5655 , RSSI: -84 , Secured: y
==============================================================
[WFM] Unknown => # 9 , Channel: 11
[WFM] 58:9:B:2E:8F:68
[WFM] SSID: Rogers 786 , RSSI: -85 , Secured: y
==============================================================
[run] Connecting BSSID: [WFM] E1:EB:E2:E0:38:60
[WFM] SSID:  HueNet2 , Channel:  4 , Best dB:  -53
[WFM] [run] Connecting done.
[WFM] [run] SSID:  HueNet2 , IP:  192.168.2.105
[WFM] WiFi connected after time:  1
[WFM] SSID: HueNet2 ,RSSI= -47
[WFM] IP address: 192.168.2.105
```


---

#### 5. WiFiMulti on ESP8266_NODEMCU_ESP12E

The following are debug terminal output when running example [WiFiMulti](examples/WiFiMulti) on `ESP8266_NODEMCU_ESP12E`

#### 5.1 First time => OK

```
Starting WiFiMulti on ESP8266_NODEMCU_ESP12E
WiFiMulti_Generic v1.0.0
[WFM] [APlistAdd] Add SSID: SSID = HueNet1
[WFM] [APlistAdd] Add SSID: SSID = HueNet2
Connecting WiFi...
[WFM] Connecting saved WiFi

WiFi connected, IP address: 192.168.2.103
```

#### 5.2 Lost WiFi => Scan and auto-reconnect

```
WiFi lost. Trying to scan and reconnect
[WFM] Start scan
[WFM] Sorted indices: 
[WFM] Known networks index = 3
[WFM] Connecting SSID = HueNet2
[WFM] WiFi connected after time:  1
[WFM] SSID: HueNet2 ,RSSI= -56
[WFM] Channel: 4 ,IP address: 192.168.2.103
```

---

#### 6. WiFiMulti on ESP32C3_DEV

The following are debug terminal output when running example [WiFiMulti](examples/WiFiMulti) on `ESP32C3_DEV`

#### 6.1 First time => OK


```
Starting WiFiMulti on ESP32C3_DEV
WiFiMulti_Generic v1.0.0
[WFM] [addAP] add SSID: HueNet1
[WFM] [addAP] add SSID: HueNet2
Connecting WiFi...
[WFM] [run] Scan done
[WFM] [run] Number of Networks found: 23
==============================================================
[WFM] Unknown => # 0 , Channel: 10
[WFM] 60:38:E0:D3:AB:4D
[WFM] SSID: HueNet , RSSI: -24 , Secured: y
==============================================================
[WFM]   Known => # 1 , Channel: 2
[WFM] 68:7F:74:94:F4:A5
[WFM] SSID: HueNet1 , RSSI: -40 , Secured: y
==============================================================
[WFM]   Known => # 2 , Channel: 4
[WFM] 60:38:E0:E2:EB:E1
[WFM] SSID: HueNet2 , RSSI: -45 , Secured: y
==============================================================
[WFM] Unknown => # 3 , Channel: 11
[WFM] 3C:90:66:E3:9:F1
[WFM] SSID: HueNetTek , RSSI: -47 , Secured: y
==============================================================
[WFM] Unknown => # 4 , Channel: 1
[WFM] E8:2C:6D:69:2:A6
[WFM] SSID: SmartRG-02a2 , RSSI: -64 , Secured: y
==============================================================
[WFM] Unknown => # 5 , Channel: 6
[WFM] F8:5E:42:4D:8E:42
[WFM] SSID: El khoury , RSSI: -67 , Secured: y
==============================================================
[WFM] Unknown => # 6 , Channel: 3
[WFM] E8:9F:80:3F:F8:15
[WFM] SSID: Linksys00043 , RSSI: -71 , Secured: y
==============================================================
[WFM] Unknown => # 7 , Channel: 5
[WFM] E4:C3:2A:11:D:E6
[WFM] SSID: DECO-5655 , RSSI: -72 , Secured: y
==============================================================
[WFM] Unknown => # 8 , Channel: 5
[WFM] EA:C3:2A:11:D:E6
[WFM] SSID: Guest5655 , RSSI: -72 , Secured: y
==============================================================
[WFM] Unknown => # 9 , Channel: 5
[WFM] 68:8F:2E:8:ED:28
[WFM] SSID: rogers786 , RSSI: -72 , Secured: y
==============================================================
[WFM] Unknown => # 10 , Channel: 11
[WFM] 68:8F:2E:B:9:58
[WFM] SSID: Rogers 786 , RSSI: -75 , Secured: y
==============================================================
[WFM] Unknown => # 11 , Channel: 5
[WFM] E4:C3:2A:11:20:8A
[WFM] SSID: DECO-5655 , RSSI: -76 , Secured: y
==============================================================
[WFM] Unknown => # 12 , Channel: 1
[WFM] C0:94:35:8A:49:16
[WFM] SSID: Access , RSSI: -77 , Secured: y
==============================================================
[WFM] Unknown => # 13 , Channel: 1
[WFM] EE:FA:BC:15:1C:D5
[WFM] SSID: ESP151CD5 , RSSI: -80 , Secured: y
==============================================================
[WFM] Unknown => # 14 , Channel: 3
[WFM] F0:B4:D2:EC:73:EA
[WFM] SSID: FishTank , RSSI: -80 , Secured: y
==============================================================
[WFM] Unknown => # 15 , Channel: 3
[WFM] 70:8B:CD:C8:B0:F0
[WFM] SSID: ericnetwork , RSSI: -81 , Secured: y
==============================================================
[WFM] Unknown => # 16 , Channel: 1
[WFM] F8:5E:42:A2:94:B7
[WFM] SSID: Offline5 , RSSI: -82 , Secured: y
==============================================================
[WFM] Unknown => # 17 , Channel: 1
[WFM] 54:64:D9:31:39:A4
[WFM] SSID: VIRGIN874 , RSSI: -82 , Secured: y
==============================================================
[WFM] Unknown => # 18 , Channel: 3
[WFM] F2:B4:D2:DC:73:EA
[WFM] SSID: FishBowl , RSSI: -82 , Secured: y
==============================================================
[WFM] Unknown => # 19 , Channel: 11
[WFM] F4:92:BF:61:E9:A0
[WFM] SSID: house , RSSI: -84 , Secured: y
==============================================================
[WFM] Unknown => # 20 , Channel: 5
[WFM] EA:C3:2A:11:20:E
[WFM] SSID: Guest5655 , RSSI: -85 , Secured: y
==============================================================
[WFM] Unknown => # 21 , Channel: 11
[WFM] 80:D0:4A:48:F2:DA
[WFM] SSID: Jessie , RSSI: -86 , Secured: y
==============================================================
[WFM] Unknown => # 22 , Channel: 11
[WFM] 98:42:65:FF:22:F6
[WFM] SSID: BELL042 , RSSI: -87 , Secured: y
==============================================================
[run] Connecting BSSID: [WFM] 68:7F:74:94:F4:A5
[WFM] SSID:  HueNet1 , Channel:  2 , Best dB:  -40
[WFM] [run] Connecting done.
[WFM] [run] SSID:  HueNet1 , IP:  192.168.2.86
[WFM] [run] MAC:  68:7F:74:94:F4:A5 , Channel:  2

WiFi connected, IP address: 192.168.2.86
```

#### 6.2 Lost WiFi => Scan and auto-reconnect

```
WiFi lost. Trying to scan and reconnect
[WFM] [run] delete old wifi config...
[WFM] [run] start scan
WiFi not connected!
WiFi lost. Trying to scan and reconnect
WiFi not connected!
WiFi lost. Trying to scan and reconnect
WiFi not connected!
WiFi lost. Trying to scan and reconnect
WiFi not connected!
WiFi lost. Trying to scan and reconnect
WiFi not connected!
WiFi lost. Trying to scan and reconnect
WiFi not connected!
WiFi lost. Trying to scan and reconnect
[WFM] [run] Scan done
[WFM] [run] Number of Networks found: 16
==============================================================
[WFM] Unknown => # 0 , Channel: 10
[WFM] 60:38:E0:D3:AB:4D
[WFM] SSID: HueNet , RSSI: -26 , Secured: y
==============================================================
[WFM] Unknown => # 1 , Channel: 11
[WFM] 3C:90:66:E3:9:F1
[WFM] SSID: HueNetTek , RSSI: -39 , Secured: y
==============================================================
[WFM]   Known => # 2 , Channel: 4
[WFM] 60:38:E0:E2:EB:E1
[WFM] SSID: HueNet2 , RSSI: -45 , Secured: y
==============================================================
[WFM] Unknown => # 3 , Channel: 1
[WFM] E8:2C:6D:69:2:A6
[WFM] SSID: SmartRG-02a2 , RSSI: -68 , Secured: y
==============================================================
[WFM] Unknown => # 4 , Channel: 3
[WFM] E8:9F:80:3F:F8:15
[WFM] SSID: Linksys00043 , RSSI: -69 , Secured: y
==============================================================
[WFM] Unknown => # 5 , Channel: 6
[WFM] F8:5E:42:4D:8E:42
[WFM] SSID: El khoury , RSSI: -69 , Secured: y
==============================================================
[WFM] Unknown => # 6 , Channel: 11
[WFM] 68:8F:2E:B:9:58
[WFM] SSID: Rogers 786 , RSSI: -72 , Secured: y
==============================================================
[WFM] Unknown => # 7 , Channel: 1
[WFM] C0:94:35:8A:49:16
[WFM] SSID: Access , RSSI: -77 , Secured: y
==============================================================
[WFM] Unknown => # 8 , Channel: 1
[WFM] EE:FA:BC:15:1C:D5
[WFM] SSID: ESP151CD5 , RSSI: -78 , Secured: y
==============================================================
[WFM] Unknown => # 9 , Channel: 1
[WFM] F8:5E:42:A2:94:B7
[WFM] SSID: Offline5 , RSSI: -81 , Secured: y
==============================================================
[WFM] Unknown => # 10 , Channel: 1
[WFM] 54:64:D9:31:39:A4
[WFM] SSID: VIRGIN874 , RSSI: -82 , Secured: y
==============================================================
[WFM] Unknown => # 11 , Channel: 11
[WFM] 80:D0:4A:48:F2:DA
[WFM] SSID: Jessie , RSSI: -83 , Secured: y
==============================================================
[WFM] Unknown => # 12 , Channel: 11
[WFM] F4:92:BF:61:E9:A0
[WFM] SSID: house , RSSI: -84 , Secured: y
==============================================================
[WFM] Unknown => # 13 , Channel: 11
[WFM] 98:42:65:FF:22:F6
[WFM] SSID: BELL042 , RSSI: -85 , Secured: y
==============================================================
[WFM] Unknown => # 14 , Channel: 11
[WFM] 60:32:B1:52:59:B6
[WFM] SSID: TP-Link_59B6 , RSSI: -87 , Secured: y
==============================================================
[WFM] Unknown => # 15 , Channel: 6
[WFM] FA:8F:CA:8E:DF:36
[WFM] SSID: Living Room Speaker 2.o , RSSI: -88 , Secured: n
==============================================================
[run] Connecting BSSID: [WFM] 60:38:E0:E2:EB:E1
[WFM] SSID:  HueNet2 , Channel:  4 , Best dB:  -45
[WFM] [run] Connecting done.
[WFM] [run] SSID:  HueNet2 , IP:  192.168.2.86
[WFM] [run] MAC:  60:38:E0:E2:EB:E1 , Channel:  4
```

---

#### 7. WiFiMulti on ESP32S3_DEV

The following are debug terminal output when running example [WiFiMulti](examples/WiFiMulti) on `ESP32S3_DEV`

#### 7.1 First time => OK


```
Starting WiFiMulti on ESP32S3_DEV
WiFiMulti_Generic v1.0.0
[WFM] [addAP] add SSID: HueNet1
[WFM] [addAP] add SSID: HueNet2
Connecting WiFi...
[WFM] [run] Scan done
[WFM] [run] Number of Networks found: 29
==============================================================
[WFM]   Known => # 0 , Channel: 2
[WFM] 68:7F:74:94:F4:A5
[WFM] SSID: HueNet1 , RSSI: -27 , Secured: y
==============================================================
[WFM] Unknown => # 1 , Channel: 10
[WFM] 60:38:E0:D3:AB:4D
[WFM] SSID: HueNet , RSSI: -28 , Secured: y
==============================================================
[WFM] Unknown => # 2 , Channel: 11
[WFM] 3C:90:66:E3:9:F1
[WFM] SSID: HueNetTek , RSSI: -43 , Secured: y
==============================================================
[WFM]   Known => # 3 , Channel: 4
[WFM] 60:38:E0:E2:EB:E1
[WFM] SSID: HueNet2 , RSSI: -51 , Secured: y
==============================================================
[WFM] Unknown => # 4 , Channel: 1
[WFM] EE:FA:BC:15:1C:D5
[WFM] SSID: ESP151CD5 , RSSI: -69 , Secured: y
==============================================================
[WFM] Unknown => # 5 , Channel: 1
[WFM] E8:2C:6D:69:2:A6
[WFM] SSID: SmartRG-02a2 , RSSI: -72 , Secured: y
==============================================================
[WFM] Unknown => # 6 , Channel: 11
[WFM] 68:8F:2E:B:9:58
[WFM] SSID: Rogers 786 , RSSI: -75 , Secured: y
==============================================================
[WFM] Unknown => # 7 , Channel: 3
[WFM] E8:9F:80:3F:F8:15
[WFM] SSID: Linksys00043 , RSSI: -76 , Secured: y
==============================================================
[WFM] Unknown => # 8 , Channel: 5
[WFM] E4:C3:2A:11:D:E6
[WFM] SSID: DECO-5655 , RSSI: -76 , Secured: y
==============================================================
[WFM] Unknown => # 9 , Channel: 5
[WFM] EA:C3:2A:11:D:E6
[WFM] SSID: Guest5655 , RSSI: -76 , Secured: y
==============================================================
[WFM] Unknown => # 10 , Channel: 5
[WFM] E4:C3:2A:11:20:8A
[WFM] SSID: DECO-5655 , RSSI: -78 , Secured: y
==============================================================
[WFM] Unknown => # 11 , Channel: 5
[WFM] EA:C3:2A:11:20:8A
[WFM] SSID: Guest5655 , RSSI: -78 , Secured: y
==============================================================
[WFM] Unknown => # 12 , Channel: 1
[WFM] C0:94:35:8A:49:16
[WFM] SSID: Access , RSSI: -79 , Secured: y
==============================================================
[WFM] Unknown => # 13 , Channel: 5
[WFM] 68:8F:2E:8:ED:28
[WFM] SSID: rogers786 , RSSI: -80 , Secured: y
==============================================================
[WFM] Unknown => # 14 , Channel: 6
[WFM] F8:5E:42:4D:8E:42
[WFM] SSID: El khoury , RSSI: -81 , Secured: y
==============================================================
[WFM] Unknown => # 15 , Channel: 11
[WFM] F4:92:BF:61:E9:A0
[WFM] SSID: house , RSSI: -84 , Secured: y
==============================================================
[WFM] Unknown => # 16 , Channel: 1
[WFM] 3A:B7:F1:BB:17:B1
[WFM] SSID: Waterhome , RSSI: -85 , Secured: y
==============================================================
[WFM] Unknown => # 17 , Channel: 3
[WFM] F0:B4:D2:EC:73:EA
[WFM] SSID: FishTank , RSSI: -85 , Secured: y
==============================================================
[WFM] Unknown => # 18 , Channel: 1
[WFM] 3A:B7:F1:BA:9E:C9
[WFM] SSID: Waterhome , RSSI: -87 , Secured: y
==============================================================
[WFM] Unknown => # 19 , Channel: 11
[WFM] 4C:71:D:97:4D:C0
[WFM] SSID: WirelessMississauga , RSSI: -87 , Secured: n
==============================================================
[WFM] Unknown => # 20 , Channel: 1
[WFM] 3A:B7:F1:BB:45:9
[WFM] SSID: Waterhome , RSSI: -88 , Secured: y
==============================================================
[WFM] Unknown => # 21 , Channel: 1
[WFM] 54:64:D9:31:39:A4
[WFM] SSID: VIRGIN874 , RSSI: -90 , Secured: y
==============================================================
[WFM] Unknown => # 22 , Channel: 6
[WFM] F4:92:BF:61:EA:FC
[WFM] SSID: Access 2.0 , RSSI: -90 , Secured: y
==============================================================
[WFM] Unknown => # 23 , Channel: 6
[WFM] F8:5E:42:BA:CE:CA
[WFM] SSID: labib , RSSI: -90 , Secured: y
==============================================================
[WFM] Unknown => # 24 , Channel: 11
[WFM] AC:20:2E:6:7:28
[WFM] SSID: Jasmine , RSSI: -90 , Secured: y
==============================================================
[WFM] Unknown => # 25 , Channel: 5
[WFM] E4:C3:2A:11:20:E
[WFM] SSID: DECO-5655 , RSSI: -91 , Secured: y
==============================================================
[WFM] Unknown => # 26 , Channel: 6
[WFM] 40:F2:1:F8:9:7
[WFM] SSID: BELL627 , RSSI: -93 , Secured: y
==============================================================
[WFM] Unknown => # 27 , Channel: 11
[WFM] 70:4F:57:14:C4:15
[WFM] SSID: SamLAN , RSSI: -93 , Secured: y
==============================================================
[WFM] Unknown => # 28 , Channel: 11
[WFM] 18:D6:C7:23:A4:B2
[WFM] SSID: JJ Realestate Investments , RSSI: -93 , Secured: y
==============================================================
[run] Connecting BSSID: [WFM] 68:7F:74:94:F4:A5
[WFM] SSID:  HueNet1 , Channel:  2 , Best dB:  -27
[WFM] [run] Connecting done.
[WFM] [run] SSID:  HueNet1 , IP:  192.168.2.83
[WFM] [run] MAC:  68:7F:74:94:F4:A5 , Channel:  2

WiFi connected, IP address: 192.168.2.83
```


#### 7.2 Lost WiFi => Scan and auto-reconnect

```
WiFi lost. Trying to scan and reconnect
[WFM] [run] Scan done
[WFM] [run] Number of Networks found: 18
==============================================================
[WFM] Unknown => # 0 , Channel: 10
[WFM] 60:38:E0:D3:AB:4D
[WFM] SSID: HueNet , RSSI: -26 , Secured: y
==============================================================
[WFM]   Known => # 1 , Channel: 2
[WFM] 68:7F:74:94:F4:A5
[WFM] SSID: HueNet1 , RSSI: -27 , Secured: y
==============================================================
[WFM] Unknown => # 2 , Channel: 11
[WFM] 3C:90:66:E3:9:F1
[WFM] SSID: HueNetTek , RSSI: -39 , Secured: y
==============================================================
[WFM]   Known => # 3 , Channel: 4
[WFM] 60:38:E0:E2:EB:E1
[WFM] SSID: HueNet2 , RSSI: -49 , Secured: y
==============================================================
[WFM] Unknown => # 4 , Channel: 1
[WFM] EE:FA:BC:15:1C:D5
[WFM] SSID: ESP151CD5 , RSSI: -72 , Secured: y
==============================================================
[WFM] Unknown => # 5 , Channel: 1
[WFM] E8:2C:6D:69:2:A6
[WFM] SSID: SmartRG-02a2 , RSSI: -74 , Secured: y
==============================================================
[WFM] Unknown => # 6 , Channel: 11
[WFM] 68:8F:2E:B:9:58
[WFM] SSID: Rogers 786 , RSSI: -75 , Secured: y
==============================================================
[WFM] Unknown => # 7 , Channel: 3
[WFM] E8:9F:80:3F:F8:15
[WFM] SSID: Linksys00043 , RSSI: -76 , Secured: y
==============================================================
[WFM] Unknown => # 8 , Channel: 6
[WFM] F8:5E:42:4D:8E:42
[WFM] SSID: El khoury , RSSI: -79 , Secured: y
==============================================================
[WFM] Unknown => # 9 , Channel: 3
[WFM] F2:B4:D2:DC:73:EA
[WFM] SSID: FishBowl , RSSI: -80 , Secured: y
==============================================================
[WFM] Unknown => # 10 , Channel: 3
[WFM] 70:8B:CD:C8:B0:F0
[WFM] SSID: ericnetwork , RSSI: -81 , Secured: y
==============================================================
[WFM] Unknown => # 11 , Channel: 1
[WFM] C0:94:35:8A:49:16
[WFM] SSID: Access , RSSI: -83 , Secured: y
==============================================================
[WFM] Unknown => # 12 , Channel: 11
[WFM] F4:92:BF:61:E9:A0
[WFM] SSID: house , RSSI: -84 , Secured: y
==============================================================
[WFM] Unknown => # 13 , Channel: 11
[WFM] 98:42:65:FF:22:F6
[WFM] SSID: BELL042 , RSSI: -86 , Secured: y
==============================================================
[WFM] Unknown => # 14 , Channel: 6
[WFM] 8C:6A:8D:4A:D5:7C
[WFM] SSID: AdeyemiHome , RSSI: -87 , Secured: y
==============================================================
[WFM] Unknown => # 15 , Channel: 6
[WFM] F4:92:BF:61:EA:FC
[WFM] SSID: Access 2.0 , RSSI: -89 , Secured: y
==============================================================
[WFM] Unknown => # 16 , Channel: 6
[WFM] 98:52:4A:74:56:AF
[WFM] SSID: Waterhome , RSSI: -90 , Secured: y
==============================================================
[WFM] Unknown => # 17 , Channel: 1
[WFM] 28:BD:89:F0:A1:AD
[WFM] SSID: Home , RSSI: -92 , Secured: y
==============================================================
[run] Connecting BSSID: [WFM] 68:7F:74:94:F4:A5
[WFM] SSID:  HueNet1 , Channel:  2 , Best dB:  -27
[WFM] [run] Connecting done.
[WFM] [run] SSID:  HueNet1 , IP:  192.168.2.83
[WFM] [run] MAC:  68:7F:74:94:F4:A5 , Channel:  2
[WFM] WiFi connected after time:  1
[WFM] SSID: HueNet1 ,RSSI= -31
[WFM] Channel: 2 ,IP address: 192.168.2.83
```

---
---

### Debug

Debug is enabled by default on Serial. Debug Level from 0 to 4. To disable, change the _WIFIMULTI_LOGLEVEL_ to 0

```cpp
// Use this to output debug msgs to Serial
#define DEBUG_WIFI_MULTI_GENERIC_PORT       Serial

// Use this to disable all output debug msgs
// Debug Level from 0 to 4
#define _WIFIMULTI_LOGLEVEL_                0
```

---

## Troubleshooting

If you get compilation errors, more often than not, you may need to install a newer version of the board's core, applying Libraries' Patches, Packages' Patches or this library latest version.

---
---


### Issues ###

Submit issues to: [WiFiMulti_Generic issues](https://github.com/khoih-prog/WiFiMulti_Generic/issues)

---
---

### TO DO

 1. Bug Searching and Killing
 2. Add support to **Portenta_H7 boards**, using [**Arduino-mbed mbed_portenta** core](https://github.com/arduino/ArduinoCore-mbed)
 3. Add support to [`WiFi101 library`](https://www.arduino.cc/en/Reference/WiFi101)
 4. Add support to Arduino AVR boards, such as Arduino Mega, UNO, Nano, 32U4, 16U4, etc.
 5. Add support to Arduino megaAVR boards, such as `Nano_Every`, `UNO_WIFI_REV2`

### DONE

 1. Add support to Arduino SAMD21, Adafruit SAMD21/SAMD51, Seeeduino SAMD21/SAMD51
 2. Add support to nRF52-based boards
 3. Add support to SAM DUE.
 4. Add support to all STM32F/L/H/G/WB/MP1.
 5. Add support to WiFiNINA using [**WiFiNINA_Generic library**](https://github.com/khoih-prog/WiFiNINA_Generic)
 6. Add support to [`WiFiEspAT library`](https://github.com/jandrassy/WiFiEspAT).
 7. Add support to **Arduino Nano RP2040 Connect** using [**Arduino mbed OS for Nano boards**](https://github.com/arduino/ArduinoCore-mbed).
 8. Add support to RP2040-based boards, such as **RASPBERRY_PI_PICO, ADAFRUIT_FEATHER_RP2040 and GENERIC_RP2040**, using [**Earle Philhower's arduino-pico** core](https://github.com/earlephilhower/arduino-pico).
 9. Add support to RP2040-based boards, such as **RASPBERRY_PI_PICO, ADAFRUIT_FEATHER_RP2040 and GENERIC_RP2040**, using [**Arduino-mbed mbed_rp2040** core](https://github.com/arduino/ArduinoCore-mbed).
10. Optimize library code and examples by using **reference-passing instead of value-passing**.
11. Add support to ESP32-based boards including new **ESP32-S3** and **ESP32_C3**
12. Add support to ESP8266-based boards

---
---

### Contributions and Thanks


Many thanks for everyone for bug reporting, new feature suggesting, testing and contributing to the development of this library.

1. Based on the [Ivan Grokhotkov's ESP8266 WiFi](https://github.com/esp8266/Arduino/tree/master/libraries/ESP8266WiFi) library.
2. Based on the [Me No Dev's ESP32 WiFi](https://github.com/espressif/arduino-esp32/tree/master/libraries/WiFi) library.
3. Thanks to [Juraj Andrássy](https://github.com/jandrassy) to request in [WiFiMulti? #17](https://github.com/khoih-prog/WiFiNINA_Generic/discussions/17) and the [WiFiEspAT](https://github.com/jandrassy/WiFiEspAT) library


<table>
  <tr>
    <td align="center"><a href="https://github.com/igrr"><img src="https://github.com/igrr.png" width="100px;" alt="igrr"/><br /><sub><b>⭐️ Ivan Grokhotkov</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/me-no-dev"><img src="https://github.com/me-no-dev.png" width="100px;" alt="me-no-dev"/><br /><sub><b>⭐️ Me No Dev</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/jandrassy"><img src="https://github.com/jandrassy.png" width="100px;" alt="jandrassy"/><br /><sub><b>⭐️ Juraj Andrássy</b></sub></a><br /></td>
  </tr> 
</table>

---

### Contributing

If you want to contribute to this project:
- Report bugs and errors
- Ask for enhancements
- Create issues and pull requests
- Tell other people about this library

---

### License

- The library is licensed under [GPLv3](https://github.com/khoih-prog/WiFiMulti_Generic/blob/main/LICENSE)

---

## Copyright

Copyright 2022- Khoi Hoang



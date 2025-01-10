---
title: "CORE-V DevKits"
date: 2019-05-04T10:00:45-04:00
headline: "CORE-V DevKits"
hide_sidebar: true
hide_page_title: true
---

Created by OpenHW members, CORE-V DevKits are tailored to facilitate the
evaluation and development of OpenHW system-on-chips (SoCs), offering essential
tools for innovation and testing.

## CORE-V MCU DevKit

<!-- Add image -->

The [CORE-V MCU DevKit](https://github.com/openhwgroup/core-v-mcu-devkit) 
is a turnkey, open source development and prototyping platform for the 
[CORE-V MCU SoC](https://github.com/openhwgroup/core-v-mcu). 
The DevKit was built by OpenHW Members for OpenHW Members enables makers of IoT
and embedded systems to evaluate CORE-V MCU performance, connect seamlessly
with WiFi and IoT cloud services, and to build and test software using the
[CORE-V SDK](https://github.com/openhwgroup/core-v-sdk), offering a versatile
foundation for prototyping and development.

### Features

- CORE-V MCU
- CV32E40P processor core
- Quicklogic ArticPro 2 eFPGA
- 4 MB flash memory
- Ashling Opella-LD onboard JTAG debug module
- USB-C for terminal and onboard debug access
- JTAG connector for external debug access
- Espressif AWS IoT ExpressLink Module for AWS IoT cloud interconnect
- mikroBUS onboard socket, allowing access to a vast range of 
  [mikroBUS modules](https://www.mikroe.com/mikrobus)
- Himax HM01B0 Ultralow Power CMOS Image Sensor
- I2C temperature sensor
- Several LEDs
- Reset button and general purpose button
- Dimensions 75 mm x 100 mm
- Power supply via USB-C or barrel connector (5V - 18V in)

### CORE-V MCU SDK (supports the CORE-V MCU DevKit)

- Eclipse-based IDE
- Debug support
- FreeRTOS
- CORE-V GNU GCC tool chain
- Peripheral driver libraries
- Example Code

The [CORE-V MCU SDK Quickstart Guide](https://github.com/openhwgroup/core-v-sdk/blob/main/README.md) 
includes links and instructions to download and bring up the SDK on Linux and
Windows. A [DevKit User Manual](https://docs.openhwgroup.org/projects/core-v-mcu-devkit-user-manual/en/latest/) 
is also available.

## CORE-V MCU Emulation Platform

<!-- Insert image -->

The [CORE-V MCU](https://github.com/openhwgroup/core-v-mcu) 
emulation platform integrates the [CV32E40P Processor IP](https://github.com/openhwgroup/cv32e40p) 
using the PULPissimo SoC from the [PULP Platform](https://pulp-platform.org/) 
and the [Quicklogic ArticPro eFPGA](https://www.quicklogic.com/products/efpga/arcticpro/). 
The CORE-V-MCU has been implemented on the Nexys A7 FPGA platform to support
evaluation of processor functionality and software development using the [CORE-V SDK](https://github.com/openhwgroup/core-v-sdk).

To get started with the CORE-V-MCU, consult the [CORE-V-MCU Quick Start Guide](https://github.com/openhwgroup/core-v-mcu/blob/master/emulation/quickstart/README.md)
and the [CORE-V-SDK Quick Start Guide](https://github.com/openhwgroup/core-v-sdk/blob/main/README.md).

---
title: "CORE-V DevKits"
date: 2019-05-04T10:00:45-04:00
hide_sidebar: true
hide_page_title: true
---

# CORE-V DevKits

Welcome to the OpenHW Group CORE-V DevKits page.

CORE-V DevKits that support evaluation of and development for OpenHW SoCs are developed by the OpenHW Hardware Task Group and the OpenHW Software Task Group contributing members.

Available CORE-V DevKits are listed below.

## CORE-V MCU DevKit

![CORE-V MCU DevKit. Described in detail below.](/images/core-v-devkits/core-v-mcu-devkit-top.png)

CORE-V MCU DevKit

### Description

The [CORE-V MCU DevKit](https://github.com/openhwgroup/core-v-mcu-devkit) is a turnkey, open-source development and prototyping platform for the [CORE-V MCU System on Chip](https://github.com/openhwgroup/core-v-mcu). The CORE-V MCU DevKit enables makers of IoT and embedded systems to evaluate the performance of the CORE-V MCU, to interconnect with WiFi and the IoT cloud, and to develop and test software using the [CORE-V SDK](https://github.com/openhwgroup/core-v-sdk).

The CORE-V MCU DevKit includes these features

- CORE-V MCU
- CV32E40P processor core
- Quicklogic ArticPro 2 eFPGA
- 4 MB flash memory
- Ashling Opella-LD onboard JTAG debug module
- USB-C for terminal and onboard debug access
- JTAG connector for external debug access
- Espressif AWS IoT ExpressLink Module for AWS IoT cloud interconnect
- mikroBUS onboard socket, allowing access to a vast range of [mikroBUS modules](https://www.mikroe.com/mikrobus)
- Himax HM01B0 Ultralow Power CMOS Image Sensor
- I2C temperature sensor
- Several LEDs
- Reset button and general purpose button
- Dimensions 75 mm x 100 mm
- Power supply via USB-C or barrel connector (5V - 18V in)

The CORE-V MCU DevKit is supported by OpenHW Group’s open-source CORE-V MCU SDK. The SDK comprises the following features

- Eclipse based IDE
- Debug support
- FreeRTOS
- CORE-V GNU GCC tool chain
- Peripheral driver libraries
- Example Code

The [CORE-V MCU SDK Quickstart Guide](https://github.com/openhwgroup/core-v-sdk/blob/main/README.md) includes links and instructions to download and bring up the SDK on Linux and Windows. The [DevKit User Manual](https://docs.openhwgroup.org/projects/core-v-mcu-devkit-user-manual/en/latest/) is available on Read the Docs.

### Ordering the CORE-V MCU DevKit

The CORE-V MCU DevKit  is currently available for early access order on the [GroupGets website](https://groupgets.com/) with anticipated delivery of November 14, 2023. Visit the [GroupGets CORE-V MCU DevKit early access campaign page](https://groupgets.com/campaigns/1040-core-v-mcu-devkit) to reserve your DevKit, as early access quantities are limited.

## CORE-V MCU Emulation Platform

![Nexsys A7. Described in detail below.](/images/core-v-devkits/nexys-a7.jpg)

Digilent Nexsys A7 board configured as CORE-V MCU Emulation platform

### Description

The [CORE-V MCU](https://github.com/openhwgroup/core-v-mcu) emulation platform integrates the [CV32E40P Processor IP](https://github.com/openhwgroup/cv32e40p) using the PULPissimo SoC from the [PULP Platform](https://pulp-platform.org/) and the [Quicklogic ArticPro eFPGA](https://www.quicklogic.com/products/efpga/arcticpro/). The CORE-V-MCU has been implemented on the Nexys A7 FPGA platform to support evaluation of processor functionality and software development using the [CORE-V SDK](https://github.com/openhwgroup/core-v-sdk).

To get started with the CORE-V-MCU, consult the [CORE-V-MCU Quick Start Guide](https://github.com/openhwgroup/core-v-mcu/blob/master/emulation/quickstart/README.md) and the [CORE-V-SDK Quick Start Guide](https://github.com/openhwgroup/core-v-sdk/blob/main/README.md)

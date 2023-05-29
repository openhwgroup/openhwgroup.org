---
title: UVM Verification of OpenHW Group's CORE-V MCU in the Cloud for Pennies per Minute 
headline: UVM Verification of OpenHW Group's CORE-V MCU in the Cloud for Pennies per Minute
subtitle: null
date: 2023-05-29
hide_page_title: true
categories: ["blogs"]
summary: |
  ""
author: OpenHW Group
container: container margin-top-40
---

## Introduction

While UVM is the most popular verification methodology for ASIC and FPGA
development, it requires expensive SystemVerilog simulators to run. In
addition, setting up a new UVM testbench is a complex task requiring specialist
skill sets and the "time to first bug found" can be excessive. It is therefore
no surprise that up to 70% of chip engineering budgets is spent on this task.

With Metrics DSim Cloud and Datum UVMx & Moore.io, this is no longer the case.
DSim Cloud operates in the cloud, requires no local computing hardware, and
costs only $.02-.04/minute. Datum UVMx & Moore.io (MIO) provide testbench code
generation and a DevOps toolchain that reduces design time-to-market by up to
30% with a per-transaction Verification IP (VIP) pricing model.

This blog will give an overview of the use of these products to specify and
generate a UVM test bench to verify the CORE-V MCU RTL design from the OpenHW
Group.

## Product Overviews

### Datum Moore.io

{{< grid/div class="row" isMarkdown="false" >}}
  {{< grid/div class="col-sm-19" >}}
Moore.io CLI (mio) is a Free & Open-Source (FOS) hardware DevOps toolchain that
performs IP management, automates EDA software, and much more. IP is stored and
downloaded from the [Moore.io IP Catalog](https://www.mooreio.com/).
  {{</ grid/div >}}
  {{< figure class="col-sm-5" src="images/moore-io.jpg" >}}
{{</ grid/div >}}

### Datum UVMx

{{< grid/div class="row" isMarkdown="false" >}}
  {{< grid/div class="col-sm-19" >}}
UVMx breaks down any digital design into specifications captured entirely via
spreadsheets from which all DV code is automatically generated.
  {{</ grid/div >}}
  {{< figure class="col-sm-5" src="images/uvmx.jpg" >}}
{{</ grid/div >}}

### Metrics DSim Cloud

{{< grid/div class="row" isMarkdown="false" >}}
  {{< grid/div class="col-sm-19" >}}
DSim Cloud is the first and only cloud-native RTL Simulator. It combines the
agility of the cloud with the high performance of a SystemVerilog and VHDL
simulator, while letting you perform unlimited regression tests without
licenses or upfront fees. Key simulator features include:

* SystemVerilog LRM-compliant
* VHDL 1993 and 2008
* Mixed VHDL, Verilog, and SV
* UVM, Constraint solver, SV Assertions

  {{</ grid/div >}}
  {{< figure class="col-sm-5" src="images/dsim-cloud.jpg" >}}
{{</ grid/div >}}

## Reproducing the results

[Installing the DSIM Cloud CLI](https://support.metrics.ca/hc/en-us/articles/9644829166989-Installing-the-DSim-Cloud-CLI)

[Installing Moore.io CLI](https://mio-cli.readthedocs.io/en/latest/installation.html)

Getting the source code

```
git clone https://github.com/Datum-Technology-Corporation/core-v-mcu-uvm.git -b empty cvmcu_uvm
```

## Design Under Test (DUT)

{{< figure class="margin-top-20 margin-bottom-40" src="images/design-under-test.jpg" >}}

[User Manual](https://core-v-mcu.readthedocs.io/en/latest/index.html)

### Verification Strategy

{{< figure class="margin-top-20 margin-bottom-40" src="images/verification-strategy.jpg" >}}

Our primary verification approach is to replace the processor core with UVM
Agents that model the Instruction Fetch and Load/Store memory interfaces. As
the processor core is already fully verified, this approach allows the DV team
to focus their attention on the components of the CORE-V-MCU without the
overhead and complexity of the core itself and its associated toolchains. APB
peripherals will be explored both in sub-system and block-level environments
and testbenches. Agents for driving/monitoring IO protocols JTAG, I2C, SPI,
UART and SDIO as well as support (clock, reset, IRQ) and libraries (scoreboard)
are Datum VIP.

This yields the following system model for the MCU, from a DV standpoint:

{{< figure class="margin-top-20 margin-bottom-40" src="images/system-model.jpg" >}}

The DV specifications must therefore cover the following:

- 1 Chip: cvmcu
- 2 Sub-Systems (with internal structure)
  - apb_timer
  - apb_adv_timer
- 4 Agents
  - cvmcu_io: transport agent to drive and monitor the MCU's IO ports for I2C,
    UART, SPI, SDIO, CPI
  - cvmcu_cpi: drives and monitors the Camera Parallel Interface
  - cvmcu_event and cvmcu_dbg: monitor event and debug interfaces for
    prediction and debugging
- 3 Blocks: tcounter, tprescaler, adv_timer

## DV Specifications

The Design Verification (DV) specifications are captured entirely with
spreadsheets using the UVMx notation (located under /docs):

-	cvmcu.uvmx.ods
-	peripherals.uvmx.ods
-	udma.uvmx.ods
-	efpga.uvmx.ods

The specifications from the sheet "chip@cvmcu" track closely with the block
diagram introduced in the previous section:

ADD IMAGE / TABLE

## Code Generation

The source code (VIP) is generated by UVMx from the spreadsheet specifications:
`mio gen --all *`

Generated VIP:

{{< grid/div isMarkdown="false" >}}
  <table>
    <thead>
      <tr>
        <th>Agents</th>
        <th>Environments</th>
        <th>Testbenches</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <ul>
            <li>uvma_cvmcu_io</li>
            <li>uvma_cvmcu_dbg</li>
            <li>uvma_cvmcu_event</li>
            <li>uvma_tcounter_b</li>
            <li>uvma_tprescaler_b</li>
            <li>uvma_adv_timer_b</li>
          </ul>
        </td>
        <td>
          <ul>
            <li>uvme_cvmcu_chip</li>
            <li>uvme_apb_timer_ss</li>
            <li>uvme_apb_adv_timer_ss</li>
            <li>uvme_cvmcu_io_st</li>
            <li>uvme_cvmcu_dbg_st</li>
            <li>uvme_cvmcu_event_st</li>
            <li>uvme_tcounter_b</li>
            <li>uvme_tprescaler_b</li>
            <li>uvme_adv_timer_b</li>
          </ul>
        </td>
        <td>
          <ul>
            <li>uvmt_cvmcu_chip</li>
            <li>uvmt_apb_timer_ss</li>
            <li>uvmt_apb_adv_timer_ss</li>
            <li>uvmt_cvmcu_io_st</li>
            <li>uvmt_cvmcu_dbg_st</li>
            <li>uvmt_cvmcu_event_st</li>
            <li>uvmt_tcounter_b</li>
            <li>uvmt_tprescaler_b</li>
            <li>uvmt_adv_timer_b</li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>
{{</ grid/div >}}

## Simulation and Regression

Before we can simulate, we must first install IP from the Moore.io IP server:

```
mio install uvmt_cvmcu_chip
```

To run the chip-level bit bash test in DSim interactive mode:

```
mio sim uvmt_cvmcu_chip -t reg_bit_bash -s 1 -a mdc
```

In addition to the simulation log and waveforms, UVMx provides transaction logs
for ease of debugging. The following is a printout for the OBI agent log:

ADD TABLE

Of particular use in register tests, reg.log neatly prints out each and every
access:

ADD OUTPUT

To run the chip-level sanity regression with DSim:

```
mio regr uvmt_cvmcu_chip sanity -a mdc
```

The regression report is automatically generated by the MIO CLI upon completion:

ADD IMAGE

## Conclusion

To learn more about the industrial-grade verification of the MCU using
per-minute and per-transaction pricing models, please see the [full version of this paper](https://metrics.ca/uvm-verification-saas-solution/).

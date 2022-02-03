---
Title: "OpenHW industrial-grade verification for open-source CORE-V IP cores"
subtitle: "This brief outline gives an overview of the open methodology and standards-based environment for the verification of the RISC-V based open-source CV32E40P core."
headline: "OpenHW industrial-grade verification for open-source CORE-V IP cores"
date: 2021-10-26T01:10:00-00:00
hide_page_title: true
categories: ["blogs"]
summary: This brief outline gives an overview of the open methodology and standards-based environment for the verification of the RISC-V based open-source CV32E40P core. 
author: Kevin McDermott, Imperas Software, a Founding member of OpenHW Group
---

<br />

*Author: Kevin McDermott, Imperas Software, a Founding member of OpenHW Group*

This brief outline gives an overview of the open methodology and standards-based environment for the verification of the RISC-V based open-source CV32E40P core.

**open-source hardware** 

Open-source has two attractive aspects, typically the freedom to modify and adapt the base design offers flexibility beyond the more constrained options with commercial solutions. Secondly, the price - at least the upfront investment is just the time and effort to download and review the base features and capabilities. With the success of open-source software projects, there is increasing interest in open-source hardware and reusable IP for custom SoCs. While the IP selection and decision process has many factors, the main difference between commercial and open-source options might be simplified to a risk assessment of the quality of the deliverables. Software and hardware share some similarities as engineering projects, but a hardware project typically has a cost of manufacture, which drives the requirement for verification - this is especially true for SoC prototypes.

**RISC-V**

As an open standard ISA (Instruction Set Architecture), RISC-V supports a modular and flexible framework for optimized processor implementations. The open standard [RISC-V specification](https://riscv.org/technical/specifications/) not just allows design freedoms but also options for IP selection, as an SoC developer can develop a core themselves, or license a commercial product, or use one of the available open-source projects. In addition, in all of these cases, the developer can further enhance and expand the core functionality with custom instructions. Although open-source hardware IP is an attractive option for chip or SoC designs, for complex IP such as processor cores, quality concerns remain a barrier for broad adoption and acceptance.

**SoC Verification**

In the past, SoC Design Verification (DV) was based on the basic assumption of known-good processor IP. However, with the open standard of RISC-V, instead of the IP being supplied by the established mainstream providers, anyone can design a custom processor. This, in turn, moves the verification task from a few specialist suppliers to all SoC developers. RISC-V verification is an essential part of the process that it is practically becoming a standalone market segment.  

**The OpenHW group**

The [OpenHW Group](https://www.openhwgroup.org/) objective is to deliver open-source IP with industrial-grade verification based on established and trusted standards. To support this vision, its full verification environment and flows are openly available. The aim is to help build confidence in the IP quality and serve as a platform, enabling future adopters to modify or extend the cores. 

The freely available resources can be used either ‘out of the box’ or as a template for other DV teams to follow. They include: 
- Testbench
- Documentation
- Scripts for test case control
- Checklist of completed milestones,
- Code and functional coverage results

Importantly, the project presents some technologies and verification methodologies that may otherwise only be known by a few experienced processor DV teams. Having all the freely available resources and results of the project on GitHub, enables adopters to continue to use the test flow. Also, other design teams can use this as a guide to improve their verification process and achieve the level of quality generally associated with commercial IP. 

**The Design Verification plan**

The Verification task group, which was established by the OpenHW Group, set up a verification strategy [plan](https://core-v-docs-verif-strat.readthedocs.io/en/latest/). Documenting everything that adopters may need while they modify or extend cores enables them to perform their due diligence. These documents are available on the OpenHW Group’s GitHub repository, [CORE-V-DOCS](https://github.com/openhwgroup/core-v-docs). 

By using UVM (Universal Verification Methodology) to develop the [core-v-verif](https://github.com/openhwgroup/core-v-verif) test plans, the project is transferable and easier to adopt by the wider SoC community. The verification environment is not specific to any single EDA vendor, using class libraries based on SystemVerilog. 

Initially, the focus was to address the verification of the [CV32E40P](https://github.com/openhwgroup/cv32e40p) core, a power-efficient 32-bit RISC V core that uses in-order execution with a 4-stage pipeline. Already in several commercial SoC designs, it is small in size but big in popularity. These include IoT devices and a general-purpose 32-bit microcontroller. 

The core-v-verif verification environment (Figure 1), provides a simulation environment for the [CV32E40P](https://github.com/openhwgroup/core-v-docs/tree/master/verif/CV32E40P) RTL core based on the RISC-V specification (RV32IMCZifencei). Plus, the environment will be adapted to other future CORE-V cores, including the CV32E40X, CV32E40S, CVA6 and future cores on the OpenHW roadmap plan.

{{< figure src="/resources/blog/images/core-v-verif-testbench.jpg" alt="Register for OpenHW TV S2 E04: Software Task Group Project Updates" class="margin-10" >}}  

The project’s key goal was to make it an open, EDA vendor-neutral environment that is based on standards, such as UVM. The aim was to enable industrial-grade verification, which is compatible with the common SoC design verification flows. These targets were achieved with the environment running on any SystemVerilog-compliant simulator. Supported by open and complete verification plans, it delivers complete code coverage and comprehensive functional coverage. 

The verification environment consists of six main components, shown in Figure 1. These include: 
- DUT (Design Under Test), which is the CV32E40P RTL
- RISC-V Reference Model (RM) and the COREV-DV
- Extension to the Google open-source ISG (Instruction Stream Generator). 
- Step-and-Compare state machine, which synchronizes the DUT and RM
- UVM Agents that assert Debug requests and interrupts, which happen asynchronously under control of the test program
- Functional coverage models, which correspond to the DV plans

In the core-v-verif environment, the ISG (core-dv) is an extension to the open-source ISG [(riscv-dv) developed by Google](https://github.com/google/riscv-dv). This particular ISG is popular, supporting several RISC-V ISA configurations. The standard riscv-dv is a useful DV tool as it provides instruction sequences to test a processor and, as an open-source project, it can also be extended by users. The OpenHW verification task group’s implementation extends the SystemVerilog/UVM classes with enhanced debug and interrupt capabilities. These extensions build on the demanding instruction sequences and corner-case scenarios that are provided by riscv-dv. Without changing the core riscv-dv implementation, this is achieved so that core-v-verif stays aligned with any future improvements while also employing the OpenHW Group’s specific capabilities.

Using the SystemVerilog DPI (Direct Programming Interface), test programs are compiled and executed on both the DUT and RM. Such a methodology enables the testbench to simulate the core (in RTL form), RM and testbench components at the same time. The opcodes of the instructions executed are captured during simulation, which allows a comparison between the RTL core and RM. As any variations are presented in real time as UVM errors, no post-processing is required to find out whether a test has passed or failed. RISC-V International and RISC-V architectural validation test suites can also be applied. 

**The Step-and-Compare method**

The verification flow defined above is essential to the verification methodology for processor design teams. The instruction stream identifies some unique corner cases. However, another important task is to understand what is happening under asynchronous conditions, such as interrupts. 

Also known as ‘lock-step’, the Step-and-Compare approach keeps the DUT and RM synchronized at the instruction boundary. This method allows asynchronous events to be analyzed in a repeatable way, and any discrepancies can be examined as part of the debug process. Finding the root cause of a bug provides a seamless switch between debug and analysis. 

The Imperas RM is fully configurable across all RISC-V specifications. It covers subset extensions of those under development s well as those already ratified. The extensions that are currently under development that are covered by the Imperas RM include Vectors (0.7 through to 1.0) and Bit Manipulation (0.90 through to the current draft). In addition, it supports DSP, Crypto (Scalar) and Debug, and the various release levels across the base User and Privileged specifications. 

It is anticipated that future cores may be based on combinations of RISC-V specifications across a variety of the base and standard extensions and thus all with independent specification versions and revisions. The Imperas envelope RM can support all of these combinations within its configuration granularity. It covers all the features and incremental versions of the RISC-V specifications. In the core-v-verif flow the Imperas RISC V RM is integrated into the SystemVerilog testbench as a binary object, linked to the SystemVerilog executable through the DPI. The model’s control and state interface provide synchronization and extraction of architectural states for RTL comparison of the in-order pipeline of CV32E40P. For RISC-V core designs featuring multi-harts or out-of-order pipelines, the Imperas RM allows detailed control features. These ensure complete synchronization and the ability to compare with the RTL under test. For more details, see www.imperas.com/riscv.


**Summary**

The RISC-V ISA is becoming extremely popular. This is thanks to its open-standard nature as well as the features and benefits offered by the open-source cores it enables. The OpenHW CV32E40P is popular with developers targeting new SoC designs for a range of industrial and commercial applications. 

The OpenHW Verification task group works hard to fully test and verify the open source CV32E40P RISC-V core. In doing so, it has also produced the core-v-verif testbench, which is freely available on GitHub and works with any tools that support UVM/SystemVerilog standards. Providing all documentation for the project, it is a valuable source of information for any design team looking to evaluate, adopt and/or modify the core. With a focus on the need for an industrial-grade verification solution for RISC-V, the OpenHW Verification task group has truly delivered a reference that others can build the future on. 

---
Author  
Kevin McDermott  
Imperas Software, a Founding member of OpenHW Group  
www.imperas.com/riscv

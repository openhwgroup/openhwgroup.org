---
Title: "Ensuring Correctness and Quality of RISC-V Testbenches"
subtitle: "When most people think about OpenHW Group, they probably think first about our RISC-V cores. The group name implies providing hardware designs compliant with the widely adopted free and open RISC-V instruction set architecture (ISA). But supporting an ISA requires much more than the register transfer level (RTL) code to implement the hardware."
headline: "Ensuring Correctness and Quality of RISC-V Testbenches"
date: 2022-03-30T09:00:00-04:00
hide_page_title: true
categories: ["blogs"]
summary: "When most people think about OpenHW Group, they probably think first about our RISC-V cores. The group name implies providing hardware designs compliant with the widely adopted free and open RISC-V instruction set architecture (ISA). But supporting an ISA requires much more than the register transfer level (RTL) code to implement the hardware."
author: Gabriel Raducan, R&D Team Lead, AMIQ EDA
---

<br />

*Author: Gabriel Raducan, R&D Team Lead, AMIQ EDA*

When most people think about OpenHW Group, they probably think first about our RISC-V cores. The group name implies providing hardware designs compliant with the widely adopted free and open RISC-V instruction set architecture (ISA). But supporting an ISA requires much more than the register transfer level (RTL) code to implement the hardware. Many leaders in industry and academia provide a wide range of RISC-V software tools: compilers, assemblers, debuggers, development environments, ISA simulators, firmware, and much more.

The software component closest to the hardware is the verification environment used to ensure that a hardware design is fully compliant to the ISA and operates as advertised in its specification. The scope of OpenHW Group includes not only robust and flexible RISC-V open-source cores, but also best-in-class open-source verification testbenches and support for the use of formal verification. Since the RISC-V ISA supports expanded instruction sets and other optional features, the verification environment must also be extensible and customizable.

A recent blog [post](https://www.openhwgroup.org/resources/blog/openhw-industrial-grade-verification-for-open-source-core-v-ip-cores/) provided a concise overview of the core-v-verif RISC-V verification environment provided by OpenHW Group. I've taken the liberty of including the diagram they used just to give an idea of what's included in this environment. For the purposes of this post, the details of its functionality are not important. However, I will note that this is a very sophisticated testbench written primarily in SystemVerilog and compliant with the Universal Verification Methodology (UVM).

INSERT IMAGE 1
{{< figure src="/resources/blog/ensuring-correctness-and-quality-of-risc-v-testbenches/images/core-v-verif-testbench.jpg" alt="core-v-verif testbench" class="margin-10" >}}

SystemVerilog is a very powerful language with many advanced features such as object-oriented programming (OOP), constrained-random stimulus generation, extensive coverage metrics, assertions suitable for both simulation and formal verification, and much more. The latest language reference manual from IEEE runs more than 1300 pages. UVM adds much more power on top of the base language, but with another 450 pages to read and understand. There are multiple ways to perform similar functions and many less common constructs that may be used incorrectly. More troubling, SystemVerilog implementation varies from tool to tool and vendor to vendor, with differing behavior and inconsistent language support.
For all these reasons, when OpenHW Group was starting its testbench work the Verification Task Group was looking for a high-quality SystemVerilog/UVM linter that would check for proper syntax and semantics while warning about constructs that are troublesome for tool performance or cross-tool portability. Given the open-source nature of the environment and the fact that it must be usable by a wide range of verification teams using a wide range of tools, the testbench code must be readable, maintainable, and vendor-neutral.

The task group surveyed the [available](https://dvteclipse.com/uvm-verissimo/1/main/index.html) open-source tools and found that none supported all the SystemVerilog constructs that they planned to use. At this point, AMIQ EDA was approached by Mike Thompson, OpenHW Group Director of Engineering, Verification Task Group. He asked whether our Verissimo SystemVerilog Linter might be capable of enforcing the level of code quality they needed. I began working with Mike and his team, with the goal of deploying Verissimo within OpenHW Group if it could handle the core-v-verif environment.
There were four main parts to the project. We started by doing initial linting on the testbench code and discussing the results with Mike and members of his team. We found we aligned quite well on what we considered acceptable, but that some of the rules we checked were less important to the task group than others. Since the rule set used by Verissimo is highly customizable, we next worked together to refine the rules and develop a set that matched the group's verification goals. It is easy to waive individual checks or suppress specific rules entirely.

Verissimo found many dozens of issues in the testbench code. The Verification Task Group had developed extensive coding guidelines for SystemVerilog and UVM, but they had not previously had an automated way to check them. Unsurprisingly, there were some violations. Some of the rules in our starting set were ones the group had not previously considered, but they decided that they were valuable and included them in the refined rule set. In a few cases the rule set was further refined, but most of the violations we found resulted in fixes in the code.

Of course, everyone makes mistakes when writing code, and finding and fixing them early adds clear value to the development process. But the more subtle issues of tool portability were also important to the verification team. For example, some simulators allow using a null class in a logical expression, but this combination is illegal in the SystemVerilog standard. Verissimo also reports coding styles that are technically correct but that waste simulation time and memory, such as specifying an override that doesn't make any changes to the base class.

Once we had refined the rule set and everything was running smoothly, we entered the third phase of the project. We worked to set up a continuous integration (CI) flow so that the lint checks would run automatically as the testbench code evolved. This is something that we at AMIQ EDA have done before; we run CI lint checks every few hours on the contents of the Github repository for the Universal Verification Methodology (UVM) reference implementation. Any new or changed code is checked quickly and the results are made publicly available.

We set up a similar flow for the core-v-verif testbench in the OpenHW repository. Whenever any member of the Verification Task Group checks in code, it is linted within a few hours and the results are [posted](https://www.dvteclipse.com/core5verif-verissimo/1/main/index.html) openly in a dashboard format. These regular regression runs ensure that everyone's contributions meet the OpenHW coding guidelines and quality metrics. In the final phase, we added the rule and waiver files to the repository so that they are accessible to everyone on the verification team. We expect that some engineers will choose to run Verissimo themselves prior to code check-in to get even earlier notification of errors and portability issues.

INSERT IMAGE 2
{{< figure src="/resources/blog/ensuring-correctness-and-quality-of-risc-v-testbenches/images/verissimo.jpg" alt="Image 2 - Verissimo " class="margin-10" >}}

Personally, I have found working with the OpenHW Group team a rewarding experience and I am proud that we have been able to enhance the quality of the verification environment shared by so many RISC-V development teams. I look forward to continuing our close cooperation.

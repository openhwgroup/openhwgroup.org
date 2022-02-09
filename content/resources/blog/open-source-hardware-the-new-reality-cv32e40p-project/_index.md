---
Title: "Open Source Hardware the New Reality CV32E40P project"
subtitle: "Open-source hardware is a new reality that aims to follow the path that Linux and other open-source software projects have achieved"
headline: "Open Source Hardware the New Reality CV32E40P project"
date: 2021-10-26T01:10:00-00:00
hide_page_title: true
categories: ["blogs"]
summary: When thinking about open-source, Linux is probably the first thing one thinks of, a successful project that everyone relies on. Open-source hardware is a new reality that aims to follow the path that Linux and other open-source software projects have achieved.  
author: Davide Schiavone - OpenHW Group Director of Engineering, Cores Task Group
---

<br />

*Author: Davide Schiavone- OpenHW Group Director of Engineering, Cores Task Group*

When thinking about open-source, Linux is probably the first thing one thinks of, a successful project that everyone relies on. From end-users to academic, industrial, and governmental institutions, Linux has been implemented in microcontrollers and smartphones, all the way up to servers and high-performance computing machines.

Open-source hardware is a new reality that aims to follow the path that Linux and other open-source software projects have achieved. Open-source hardware will be one of the leading paradigms to build the next generation of System-on-Chips (SoCs) thanks to:  
- the lower barrier to access technology for both research and development activities; 
- the fewer dependencies to specific IP vendors; 
- enhanced security thanks to its transparency; 
- and the opportunity to increase expertise on the IPs in both educational and industrial institutions.

You may be thinking: “yes, that’s all cool - but who is developing such open-source hardware, and how can I trust them?”

This is where the [OpenHW Group](https://www.openhwgroup.org/#about-us) comes in.  The OpenHW Group is a non-profit organization that develops open-source hardware and related software in a collaborative manner. The OpenHW Group is driven by a growing number of member and partner ecosystem companies, providing an infrastructure for hosting high-quality, collaborative developments in line with industry best practices. The initial OpenHW Group open-source projects cope with developing and verifying a family of cores called CORE-V based on the free and open [RISC-V](http://riscv.org/) Instruction Set Architecture (ISA).

The first entry of the CORE-V family is CV32E40P, previously known as RI5CY.  
CV32E40P is a RISC-V 32bits, in-order, 4 pipeline-stage CPU optimized for edge-computing platforms. 

{{< figure src="/resources/blog/open-source-hardware-the-new-reality-cv32e40p-project/images/cv32e40p.png" alt="CV32E40P" class="margin-10" >}}  

CV32E40P was born as the result of several projects at [ETH Zurich](https://ethz.ch/) and open-sourced back in 2016 on GitHub. What made this core different were the following features:  
- energy-efficient core optimized for multicore platforms targeting mW budget applications; 
- custom ISA extensions proposed ahead of the RISC-V draft current proposals including SIMD, DSP, HW loops, bit manipulation, and many more operations to increase the energy efficiency, performance, and code density; 
- proven in Silicon on different nodes from130nm to 22nm; 
- written in high-quality SystemVerilog to ease the integration of the core in already existing systems; 
- last but not least its permissive license based on Solderpad (Apache 2.0) which encouraged fast and easy adoption in the industry.

For scientific and technical details, please refer to the following most relevant papers that have received more than 300 citations to date:  
- [Near-Threshold RISC-V Core With DSP Extensions for Scalable IoT Endpoint Devices](https://ieeexplore.ieee.org/document/7864441)
- [Slow and steady wins the race? A comparison of ultra-low-power RISC-V cores for Internet-of-Things applications](https://ieeexplore.ieee.org/document/8106976)

The main driver of the development of such a CPU core was the [PULP](https://pulp-platform.org/) (Parallel Ultra Low Power) project. This PULP project aims to push forward the state-of-the-art energy efficiency and performance of ~mW range programmable applications for the Internet-Of-Things (IoT) by leveraging multicore architectures and near-threshold computing (NTC).

In this context, the CV32E40P core was developed to be the primary processing element of the PULP microcontrollers. It has been shown to be powerful in multicore platforms from Artificial Intelligence and Deep Learning tasks as described in [A 1.3 TOPS/W@ 32GOPS Fully Integrated 10-Core SoC for IoT End-Nodes with 1.7 μW Cognitive Wake-Up From MRAM-Based State-Retentive Sleep Mode](https://ieeexplore.ieee.org/abstract/document/9365939), to Brain-Computer-Interface (BCI) devices as shown in [Biowolf: A sub-10-mw 8-channel advanced brain–computer interface platform with a nine-core processor and ble connectivity](https://ieeexplore.ieee.org/abstract/document/8758394), as well as in single-core platforms for microcontroller applications like in [Quentin: an Ultra-Low-Power PULPissimo SoC in 22nm FDX](https://ieeexplore.ieee.org/abstract/document/8640145).

Since the publication of the open-source code, the core has been used by companies and academic institutions all around the world in products like in [GAP-8: A RISC-V SoC for AI at the Edge of the IoT](https://ieeexplore.ieee.org/abstract/document/8445101), where 9 CV32E40P cores are implemented in a product by Greenwaves Technology; prototypes as the [NXP Vega board](https://open-isa.org/), as a possible candidate for the [Pixel Visual Core](https://www.youtube.com/watch?v=m7aAUlHoV2E) by Google, to test tools, algorithms, in several research projects, and many more. Please refer to the PULP's users [webpage](https://pulp-platform.org/pulp_users.html) to explore more projects.

The wide use of the core required it to graduate from University and enter the industry such that documentation, maintenance, support, and verification could be provided at industrial grade. In February 2020, the code repository of the core and its maintenance and responsibilities had been donated to OpenHW Group by ETH Zurich.

Since then, several changes have been applied to the RTL and documentation of the core, with the first milestone being industrial grade verification of the RV32IMC ISA subset of the core achieved in December 2020. The significant changes are:  
- RISC-V compliancy in all the features like interrupts, debug, and performance counters;
- RTL bugs fixing;
- 100% code coverage achieved in an open-source [verification environment](https://github.com/openhwgroup/core-v-verif) based on STEP & COMPARE methodologies using the Imperas Instruction Set Simulator (ISS);
- versions maintenance rules based on the RISC-V implementation ID and logical equivalence;
- and Github issues organizations based on topics and features.

Finally, to demonstrate the capability of the core in silicon, the OpenHW Group CORE-V MCU project aims to implement a microcontroller in pre-production volumes using the GlobalFoundries GF22FDX technology node. The CORE-V MCU is a microcontroller based on the PULP platform using a verified CV32E40P CPU based on [Arnold: An eFPGA-Augmented RISC-V SoC for Flexible and Low-Power IoT End Nodes](https://ieeexplore.ieee.org/abstract/document/9369856).

There is still a lot going on for CV32E40P and we will have more to share. In a future blog post, we will discuss the second project related to the core which aims to achieve full industrial grade verification on the XPULP custom ISA extensions, RV32F, and more.

If you work on RISC-V CPUs or in the ecosystem like co-processors, microcontrollers, simulators, compilers, operating systems, and software, reach out to us at the OpenHW Group. You can contact us at <info@openhwgroup.org>, or by contacting me directly at <davide@openhwgroup.org>. We encourage you to [explore our projects](https://www.openhwgroup.org/projects/), subscribe to our [mailing lists](https://share.hsforms.com/1XdNvwOBNRTONOVdZjwVleg4o9yd), and contact us for more information about getting involved and becoming a member of the OpenHW Group.

Follow us on [Twitter](https://twitter.com/openhwgroup) and [Linkedin](https://www.linkedin.com/company/openhwgroup/mycompany/)
---
title: Security for all - OpenHW Group leads the charge towards a secure future
subtitle: OpenHW Group leads the charge towards a secure future
headline: Security For All
date: 2023-03-06
hide_page_title: true
categories: ["blogs"]
summary: |
  Security has become a critical issue for the entire IoT supply chain in recent years, as the number of connected devices continues to grow and our reliance on them increases.
author: Chris Jones, Director of Applications at Crypto Quantique
container: container margin-top-40
---

_Author: Chris Jones, Director of Applications at Crypto Quantique_

Security has become a critical issue for the entire IoT supply chain in recent
years, as the number of connected devices continues to grow and our reliance on
them increases. With more devices connected to the internet, the potential for
security breaches and data theft also increases. In this blog post, we will
discuss the following:

- The complexity of IoT security
- The current vulnerabilities of hardware
- The benefits of having a root of trust or physical uncountable function (PUF)
  in your device

Along with this, I will give a brief overview of what we are doing in our
collaboration with the OpenHW Group as part of the CORE-V Trusted MCU Project to
ensure we have the option for the very best security right from the design phase
on all OpenHW devices going forward.

## The complexity of security

IoT security is a complex issue because of the many layers involved in
protecting connected devices. This includes hardware, software, network, and
cloud security. Each layer presents its own set of challenges and risks, and
ensuring the security of the entire system requires a comprehensive approach
that takes all of these into account.

{{< figure class="flex-center" src="./images/iot-devices-worldwide-2015-to-2025.jpg" caption="The number of IoT devices in circulation is set to continue to rise year after year." alt="Bar chart displaying 30.73 billion IoT devices in 2020 and growing to 75.44 billion by 2025." >}}

That’s where Crypto Quantique comes in. We offer a comprehensive suite of
products to cover both the hardware and software elements of the supply chain.
QDID, our patented semiconductor IP design is the most secure hardware
root-of-trust available on the market to create unforgeable device identities
and cryptographic keys. QuarkLink then looks after the rest of the supply chain
once the hardware has been shipped. It is an IoT device management platform that
allows users to provision, onboard and manage devices with a cloud service
provider securely. However, as this is the OpenHW Group blog, we will focus on
the hardware for now.

{{< figure class="flex-center margin-10" src="./images/crypto-quantique-securing-supply-chain.jpg" caption="Crypto Quantique eases the complexity of securing the supply chain." >}}

## The vulnerability of hardware

Hardware is a critical component of IoT security, as it is often the first line
of defense against attacks. However, hardware can also be a point of
vulnerability if it is not designed with security in mind. This is why it is
essential to use secure chips and devices resistant to tampering and attacks.
Additionally, firmware updates and security patches must be kept up to date to
ensure that the device remains secure.

To ensure this OpenHW Group and Crypto Quantique have teamed up with Low Power
Futures and formed the CORE-V Trusted MCU Project to create the most secure
hardware systems incorporating CORE-V cores and QDID.

## The benefits of having a root of trust in your device

Having a root of trust in your device means that there is a secure and trusted
foundation that the entire system can build. This can help to prevent attacks
and ensure that data and devices are secure. A root of trust integrated with a
secure boot process will protect against firmware tampering, which is critical
for the overall security of the device.

Providing additional security measures not only protects your customers' data
and devices but also adds value to your brand. Consumers are becoming
increasingly aware of the importance of security, and are more likely to choose
brands that provide it. Additionally, having a secure reputation can help to
establish trust with customers and differentiate your brand from competitors.

## So what are the benefits of QDID compared to other PUFs?

There are many advantages to using QDID compared to other PUF technology.

PUFs are an essential component in many applications that require secure data
encryption and protection. However, PUFs are not without limitations. One of the
most significant limitations is that they typically spawn additional
cryptographic keys from the same original number, known as the seed. This can
lead to a lack of true randomness, as the same seed can be used to generate
additional keys which could not be classed as uncorrelated. Another issue is
that cells don't always start up in the same state, leading to unreliable
performance. The error rate for SRAM can be up to 30%, which can affect the
reliability of the output. The memory quality used in PUF can also impact its
overall performance. Additionally, the protection against side-channel attacks
is questionable, making RNGs vulnerable to hacking.

### With QDID you get the benefit of:

- The cost and risks of key injection are eliminated
- Identities are not stored in memory
- Uses standard CMOS transistors
- Immune to traditional side channel attacks
- Low error rate
- Multiple uncorrelated keys
- High entropy
- Cannot be simulated/emulated by a quantum computer

## So how does QDID fit into CORE-V?

QDID can work with any RISC-V-based core. For CORE-V I’ll give examples of how
QDID would slot into the design. First, we start with the overall SoC showing
the secure block with an integrated QDID, you can see it in the top right-hand
corner of the following diagram. This system is a two-core system with the
secure block protecting the main CORE-V only allowing it to boot once its
application code has been verified by the security block.

{{< figure class="flex-center margin-10" src="./images/soc-example-for-iot-device.jpg" caption="An example SoC for a typical IoT device." alt="A diagram of a SoC example for a typical IoT device described in detail below." >}}

If we look closer at the following diagram, the secure block is made up of the
usual components for a trusted execution environment. You can see how the setup
works between the QDID and the CORE-V core. It acts as a separate bit of the
block to ensure a secure design, almost like a fingerprint for the SoC. The
CORE-V executes an immutable secure boot sequence in ROM that verifies the
signature of any first-level bootloader. Once the security block is up and
running it can verify the firmware for the main core and only allow it out of
reset if all is well.

{{< figure class="flex-center margin-10" src="./images/inner-look-at-secure-block.jpg" caption="An inner look at the secure block." alt="Diagram of the secure block." >}}

So if we put this together in an example use case, let’s say a Programmable
Logic Controller, you can see in the following diagram how that setup would
look.

{{< figure class="flex-center margin-10" src="./images/programmable-logic-controller-with-integrated-qdid-and-core-v.jpg" caption="A Programmable Logic Controller with integrated QDID and Core-V." alt="Diagram of how the setup looks." >}}

## Securing RISC-V IoT devices, one at a time

In conclusion, IoT security is a complex issue that requires a comprehensive
approach to ensure the security of connected devices. This includes protecting
hardware, having a root of trust in your device, and providing additional
security measures. By doing so, you can protect your customers, differentiate
your brand, and establish trust with your customers. We started this security
council because the collaboration will bring you:

- The most complete and secure RISC-V solution
- Highly optimized processor cores
- Extensive software stacks
- Root of Trust incorporating quantum-driven security
- Cloud-based security platform

All of this put together will enable your customers to build products that:

**Have the most secure, high-performance RISC-V technology**

- without having to trust partners in the supply channel
- with the easiest-to-use onboarding and life-cycle management platform
- without having to be an expert in security and cloud connectivity

_Crypto Quantique is an IoT security pioneer that has combined cryptography and
quantum physics to develop security products that drive end-to-end security and
unlock scalability for IoT networks._

Follow them on [Twitter](https://twitter.com/CryptoQuantique),
[LinkedIn](https://www.linkedin.com/company/crypto-quantique) and you can
contact them on their website at: [www.cryptoquantique.com](https://www.cryptoquantique.com)

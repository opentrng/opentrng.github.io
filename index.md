---
title: "Open-source TRNG"
layout: single
toc: true
---

## Introduction

Welcome to **OpenTRNG** the open-source TRNG! This project is dedicated to delivering the community open-source implementations of reference Physical True Random Number Generator (TRNG or PTRNG) based on ring oscillators. Through **OpenTRNG**, you have the ability to:

1. [Emulate noisy ring oscillators](/docs/emulator/#emulate-noisy-ring-oscillators)
2. [Emulate raw random number](/docs/emulator/#emulate-raw-random-numbers)
3. [Simulate](/docs/hardware/#simulate-hdl-sources), [compile](/docs/hardware/#compile-for-fpga) and [run](/docs/remote) the PTRNG on hardware
4. [Analyze and evaluate their outcomes](/docs/analysis/#analyze-and-evaluate-outputs)

<!-- > **OpenTRNG** is fully compatible with [OpenTitan](https://opentitan.org), our PTRNG can be used as input for OpenTitan's hardware IP blocks. Please find more information in the hardware section.
{: .notice--info} -->

## Why OpenTRNG?

The objective of **OpenTRNG**, the open-source TRNG, is to offer reference architectures of ring-oscillator based True Random Number Generators (TRNG), also known as PTRNG, to the community. With the advancement of certification standards like [BSI AIS20/31](https://www.bsi.bund.de/dok/randomnumbergenerators) (used in the Common Criteria) and [NIST SP 800-90B](https://csrc.nist.gov/pubs/sp/800/90/b/final), the stochastic model of the entropy source is increasingly crucial in relation to validating statistical tests on output data. Here, we publish straightforward yet effective entropy sources for PTRNG to facilitate the validation of their stochastic models across various FPGA and ASIC targets.

In RO-based True Random Number Generators (TRNGs), the RO serves as the entropy source. Specifically, the inherent jitter between two (or more) ROs generates relative phase noise, which is known random, uncontrollable, and unpredictable. This relative phase noise is then converted into random bits through a sampling mechanism.

As of now, **OpenTRNG** includes the following reference sampling architectures:

* Elementary based Ring Oscilator ([ERO](docs/hardware/#ero)),
* Multi Ring Oscilator ([MURO](docs/hardware/#muro)),
* Coherent Sampling Ring Oscilator ([COSO](docs/hardware/#coso)).

## License and contributions

The **OpenTRNG** project is distributed under the GNU GPLv3 license.

Pull requests are welcome and will be reviewed before being merged. No integration timelines are promised. The code is maintained by [CEA](https://www.cea.fr/english)-[Leti](https://www.leti-cea.com/cea-tech/leti/english/Pages/Applied-Research/Facilities/cyber-security-platform.aspx).

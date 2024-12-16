---
title: "Publications"
layout: single
toc: true
---

## Publication at DTTIS 2024

**Title**: [OpenTRNG: an open-source initiative for ring-oscillator based TRNGs](https://ieeexplore.ieee.org/document/10780212)

**Authors**:
- [Florian PEBAY-PEYROULA](contributors#florian-pebay-peyroula)
- [Licinius BENEA](contributors#licinius-benea)
- [Mikael CARMONA](contributors#mikael-carmona)
- [Romain WACQUEZ](contributors#romain-wacquez)

**Abstract:** OpenTRNG initiative introduces an open-source framework for physical True Random Number Generators (TRNG), focusing on ring-oscillator-based architectures. This project offers a comprehensive toolkit comprising reference designs, emulation tools, and analytical tools aiming at facilitating the development and characterization of hardware TRNG implementations. Key components include emulators capable of simulating noisy ring oscillators and digital noise sources, hardware descriptions for FPGA implementations, and analytical tools for assessing randomness metrics such as variance, entropy and autocorrelation. By providing accessible resources and fostering collaboration within the community, OpenTRNG aims to accelerate the advancement and validation of TRNG architectures at different technology nodes and at the highest level of security. It also seeks to promote good design practices, methodology, and reproducibility in the field of random number generation.

Bibtex reference:
```
@inproceedings{pebay2024,
  author={Pebay-Peyroula, Florian and Benea, Licinius-Pompiliu and Carmona, Mikael and Wacquez, Romain},
  booktitle={2024 IEEE International Conference on Design, Test and Technology of Integrated Systems (DTTIS)}, 
  title={OpenTRNG: an open-source initiative for ring-oscillator based TRNGs}, 
  year={2024},
  volume={},
  number={},
  pages={1-6},
  keywords={Ring oscillators;Emulation;Collaboration;Throughput;Hardware;Entropy;Reliability;Security;Random number generation;Field programmable gate arrays;TRNG;PTRNG;FPGA;ASIC;Ring-oscillator},
  doi={10.1109/DTTIS62212.2024.10780212}
}
```

## Publication in WiPiEC Journal (DSD 2024)

**Title**: [COSOI: True Random Number Generator Based on Coherent Sampling using the FD-SOI technology](https://wipiec.digitalheritage.me/index.php/wipiecjournal/article/view/60)

**Authors**:
- [Licinius BENEA](contributors#licinius-benea)
- [Florian PEBAY-PEYROULA](contributors#florian-pebay-peyroula)
- [Mikael CARMONA](contributors#mikael-carmona)
- [Romain WACQUEZ](contributors#romain-wacquez)

**Abstract:** This work presents a proof of concept of the implementation of a Coherent Sampling Ring Oscillator TRNG (COSO-TRNG) using the Fully Depleted Silicon On Insulator (FD-SOI) technology. COSO-TRNG appears as one of the best structures optimizing the throughput per area trade-off and having a model for its entropy source. The back-biasing capability of the FD-SOI technology is proved here to be a very simple and efficient technique for the ring oscillator frequency calibration needed for the coherent sampling method. This is the first demonstration of feasibility of COSO-TRNG validated on ASIC FD22nm. A throughput of 3.36 Mbits/s was obtained, equivalent to results in the literature.True random number generator.

Bibtex reference:
```
@article{benea2024,
  title = {{COSOI}: {True} {Random} {Number} {Generator} {Based} on {Coherent} {Sampling} using the {FD}-{SOI} technology},
  volume = {10},
  copyright = {Copyright (c) 2024 Licinius Benea, Florian Pebay-Peyroula, Mikael Carmona, Romain Wacquez},
  issn = {2980-7298},
  number = {2},
  urldate = {2024-12-13},
  journal = {WiPiEC Journal - Works in Progress in Embedded Computing Journal},
  author = {Benea, Licinius and Pebay-Peyroula, Florian and Carmona, Mikael and Wacquez, Romain},
  month = aug,
  year = {2024},
  note = {Number: 2},
  keywords = {Fully Depleted Silicon On Insulator}
}
```

## Publication at CHES 2024

**Title**: [Impact of the Flicker Noise on the Ring Oscillator-based TRNGs](https://tches.iacr.org/index.php/TCHES/article/view/11450)

**Authors**:
- [Licinius BENEA](contributors#licinius-benea)
- [Mikael CARMONA](contributors#mikael-carmona)
- Viktor FISCHER
- [Florian PEBAY-PEYROULA](contributors#florian-pebay-peyroula)
- [Romain WACQUEZ](contributors#romain-wacquez)

**Abstract:** Ring Oscillators (RO) are often used in true random number generators (TRNG). Their jittered clock signal, used as randomness source, originates from thermal and flicker noises. While thermal noise jitter is generally used as the main source of randomness, flicker noise jitter is not due to its autocorrelation. This work aims at qualitatively settling the issue of the influence of flicker noise in TRNGs, as its impact increases in newer technology nodes. For this, we built a RO behavioural model, which generates time series equivalent to a jittered RO signal. It is then used to generate the output of an elementary RO-TRNG. Despite general expectations, the autocorrelation inside the output bit stream is reduced when the amplitude of flicker noise increases. The model shows that this effect is caused by the sampling of the jittered signal by the second oscillator, which hides the behaviour of the absolute jitter, causes resetting of the perceived phase, and suppresses any memory effect. The inclusion of flicker noise as a legitimate noise source can increase the TRNG output bit rate by a factor of four for the same output entropy rate. This observation opens new perspectives towards more efficient stochastic models of the RO-TRNGs.

Bibtex reference:
```
@article{FlickerCHES2024,
  author={Benea, Licinius and Carmona, Mikael and Fischer, Viktor and Pebay-Peyroula, Florian and Wacquez, Romain},
  title={Impact of the Flicker Noise on the Ring Oscillator-based TRNGs},
  journal={IACR Transactions on Cryptographic Hardware and Embedded Systems},
  volume={2024},
  number={2},
  year={2024},
  month={Mar.},
  pages={870–889},
  doi={10.46586/tches.v2024.i2.870-889}
}
```

## Publication at DSD 2022

**Title**: [On the Characterization of Jitter in Ring Oscillators using Allan variance for True Random Number Generator Applications](https://ieeexplore.ieee.org/document/9996678)

**Authors**:
- [Licinius BENEA](contributors#licinius-benea)
- [Mikael CARMONA](contributors#mikael-carmona)
- [Florian PEBAY-PEYROULA](contributors#florian-pebay-peyroula)
- [Romain WACQUEZ](contributors#romain-wacquez)

**Abstract:** The description of the physical noise source is of utmost importance for any TRNG certification. In the case of ring oscillators, Allan variance is a reliable and comprehensive tool which enables the distinction between the jitter coming from flicker noise (autocorrelated) and from thermal noise (random). In this paper, we realize measurements directly on the analog source of numerous TRNG structures: a ring oscillator. Our data, along with evidence from the literature, indicates the presence of a third noise source. The quantization noise has not been so far taken into consideration, but is unquestionably present in all TRNG reliant on jitter. Its importance is key to an accurate estimation of thermal noise contribution, which can be shadowed by it. Measurements presented in this paper show that insufficient sampling (i.e. higher quantization noise) can lead to an overestimation of jitter coming from thermal noise and therefore an overestimation of the calculated entropy. The latter is the only type of noise considered reliable in currently existing ring oscillator-based TRNG models. As a rule of thumb, three orders of magnitude between the sampling and the sampled signal are necessary in order to determine the thermal noise jitter correctly.

Bibtex reference:
```
@inproceedings{9996678,
  author={Benea, L. and Carmona, M. and Pebay-Peyroula, F. and Wacquez, R.},
  booktitle={2022 25th Euromicro Conference on Digital System Design (DSD)}, 
  title={On the Characterization of Jitter in Ring Oscillators using Allan variance for True Random Number Generator Applications}, 
  year={2022},
  volume={},
  number={},
  pages={534-538},
  doi={10.1109/DSD57027.2022.00077}
}
```

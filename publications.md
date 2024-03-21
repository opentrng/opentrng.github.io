---
title: "Publications"
layout: single
toc: true
---

## Publication at CHES 2024

**Title**: [Impact of the Flicker Noise on the Ring Oscillator-based TRNGs](https://tches.iacr.org/index.php/TCHES/article/view/11450)

**Authors**:
- [Licinius BENEA](contributors/#licinius-benea)
- [Mikael CARMONA](contributors/#mikael-carmona)
- Viktor FISCHER
- [Florian PEBAY-PEYROULA](contributors/#florian-pebay-peyroula)
- [Romain WACQUEZ](contributors/#romain-wacquez)

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
- [Licinius BENEA](contributors/#licinius-benea)
- [Mikael CARMONA](contributors/#mikael-carmona)
- [Florian PEBAY-PEYROULA](contributors/#florian-pebay-peyroula)
- [Romain WACQUEZ](contributors/#romain-wacquez)

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

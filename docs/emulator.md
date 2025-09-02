---
title: "Emulator"
layout: single
toc: true
---

## Introduction

The `emulator` directory includes all Python files dedicated to the emulation of [ring oscillators](#emulate-noisy-ring-oscillators) and [raw random numbers](#emulate-raw-random-numbers) . These emulators can be executed directly using the provided scripts (refer to the sections below for details).

> For detailed information on script **parameters**, use the `-h` option
{: .notice--info}

The `emulator` directory also includes a [jupyter notebook](https://jupyter.org) named `playground.ipynb`, providing an interactive environment to explore and utilize the emulator's routines.

## Emulate noisy ring oscillators

The emulator, introduced in our [CHES 2024 paper](/publications), is capable of generating time series for ring oscillators (RO) while incorporating realistic phase noise. Each successive value in the series represents the absolute timing of the rising edge of the RO signal. The phase noise models include both [thermal](https://en.wikipedia.org/wiki/White_noise) noise (white noise) and [flicker noise](https://en.wikipedia.org/wiki/Flicker_noise) (colored noise).

To simulate 10,000,000 cycles of a ring oscillator running at 100 MHz, execute the following command:

```
$ python ro.py -size 10e6 -freq 100e6 ro.txt
```

Below is an example of the generated file, where each line represents a ring oscillator period in femtoseconds (fs):

```
10041823
10012169
10001670
9993447
9944616
10027199
...
10002230
9996430
```

The distributions of periods is given in the figure below as an example (see [analysis tools](/docs/analysis) for help on distribution plots).

![100MHz noisy ring oscillator periods distribution (fs)](/assets/images/rodistribution.png)

By default, the thermal and flicker noise amplitude coefficients, `a1` and `a2`, are calibrated for a ring oscillator operating at 100 MHz on a Xilinx Artix-7 FPGA. Optionally, these coefficients can be customized to define a specific thermal and flicker noise model. For example, using coefficients from a 500 MHz ring oscillator measured on a 28nm industrial FD-SOI (Fully Depleted [Silicon on Insulator](https://en.wikipedia.org/wiki/Silicon_on_insulator)) technology node:

```
$ python ro.py -size 10e6 -freq 100e6 -a1 1.334e-14 -a2 7.985e-09 ro.txt
```

## Emulate raw random numbers

Raw random numbers (RRN) can be emulated using Python scripts based on the [noisy ring-oscillator emulation](#emulate-noisy-ring-oscillators) described in the previous section.

By specifying the frequencies of the target ring oscillators and selecting a sampling architecture — [ERO](hardware#ero), [MURO](hardware#muro), or [COSO](hardware#coso) — the script will generate a file containing the raw random output.

### Elementary RO based TRNG

For instance, to generate a stream of 1,000,000 bits using the [ERO](hardware#ero) architecture, with the first ring oscillator operating at 100 MHz and a divisor of 1,000 sampling the second ring oscillator at 101 Hz, run the following command:

```
$ python ero.py -size 1e6 -freq0 100e6 -freq1 101e6 -div 1000 ero.txt
```

This command produces the following output:

```
Number of bits to generate: 1.00e+06
Ring-oscillators frequencies:
 - RO0: 1.000e+08 Hz / 1000
 - RO1: 1.010e+08 Hz
Noise amplitude coefficiens:
 - Thermal (a1): 1.421673e-13
 - Flicker (a2): 1.155723e-25
Output bits bias: 0.50
```

### Multi-RO based TRNG

The [MURO](hardware#muro) utilizes multiple ring oscillators. For example, to generate a stream of 1,000,000 bits with a sampling frequency of 100 MHz, divided by 1000, which samples a tuple of ring oscillators operating at frequencies of 99 MHz and 101 MHz, use the following command:

```
$ python muro.py -size 1e6 -freq 100e6 99e6 101e6 -div 1000 muro.txt
```

This command produces the following output:

```
Number of bits to generate: 1.00e+06
Number of ring-oscillators: 3 (t=2)
Ring-oscillators frequencies:
 - RO0: 1.000e+08 Hz / 1000
 - RO1-ROt: 9.900e+07, 1.010e+08 Hz
Noise amplitude coefficiens:
 - Thermal (a1): 1.421673e-13
 - Flicker (a2): 1.155723e-25
Output bits bias: 0.50
```

### Coherent Sampling TRNG

In a more straightforward configuration, the [COSO](hardware#coso) only requires two ring-oscillator frequencies as inputs. To generate a stream of 1,000,000 bits with a [COSO](hardware#coso) operating at 99.91 MHz and 100.52 MHz, use the following command:

```
$ python coso.py -size 1e6 -freq0 121e6 -freq1 122e6 coso.txt
```

This command produces the following output:

```
Number of bits to generate: 1.00e+06
Ring-oscillators frequencies:
 - RO0: 9.991e+07 Hz
 - RO1: 1.005e+08 Hz
Noise amplitude coefficiens:
 - Thermal (a1): 1.421673e-13
 - Flicker (a2): 1.155723e-25
Average counter value: 150.28
Output bits bias: 0.51
```

Below is an illustration of the raw random output for the [COSO](hardware#coso).

![An example of raw binary output for the COSO](/assets/images/cosorawbinary.png)

Optionnaly, as explained in the [previous section](#emulate-noisy-ring-oscillators), noise amplitudes `a1` and `a2` can be modified accordingly to your own hardware target with custom thermal and flicker noise model.

The RRN emulators are used as golden model for [HDL simulation](hardware#simulate-hdl-sources).

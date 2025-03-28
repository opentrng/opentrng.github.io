---
title: "Analyze and evaluate outputs"
layout: single
toc: true
---

The directory `analysis` contains all analyze and evaluation tools.

The `analysis` directory contains all the tools for analyzing and evaluating the outcomes from [emulator](emulator) and [hardware target](hardware).

> For more details on their **parameters**, call the scripts with `-h`.
{: .notice--info}

## Allan variance

The Allan Variance for a ring-oscillator time series, whether obtained from measurement or emulation, can be computed. The Python script `allanvariance.py` plots the normalized Allan Variance versus the sample accumulation. For example, the following command can be used to plot the Allan Variance of an emulated ring oscillator:

```
$ python allanvariance.py -t "Plot title" ro.txt allanvar.png
```

![Allan variance example for a 500Mz ring oscillator](/assets/images/allanvariance.png)

The Allan variance can also be plotted for the [COSO](hardware#coso) output values in order to estimate respective thermal and flicker noise contributions.

## COSO counter distribution

The counter values generated by the [COSO](hardware#coso), whether emulated or obtained from the FPGA board, can be visualized by creating a histogram using the following Python script:

```
$ python distribution.py --log -t "Plot title" coso.txt distribution.png
```

![COSO values with RO pair at 500MHz and 505MHz](/assets/images/cosodistribution.png)

The provided example illustrates the generation of a [COSO](hardware#coso) log-distribution plot using data from produced through emulator of two ring-oscillators at 500MHz and 505MHz.

## Entropy estimation

Entropy estimators take binary files as input. The script `tobinary.py` can be used to convert [ERO](hardware#ero), [MURO](hardware#muro) and [COSO](hardware#coso) text output files to binary. This script takes one integer per line (value should be `0`, `1` or `n`), then extracts the less significant bit (LSB) for each line and pack successive bits to bytes.

You can estimate entropy of the generated binary streams with the script `entropy.py` that offers different estimators:
* Shannon entropy ([Wikipedia](https://en.wikipedia.org/wiki/Entropy_(information_theory)))
* Most Common Value (from [NIST SP800-90B](https://csrc.nist.gov/pubs/sp/800/90/b/final))
* Markov (from [NIST SP800-90B](https://csrc.nist.gov/pubs/sp/800/90/b/final))
* T8 from [BSI AIS 20/31](https://www.bsi.bund.de/dok/randomnumbergenerators) test procedure B

Estimators can be computed for different samples width, from 1 bit numbers to 32 bits numbers.

```
$ python entropy.py -e mcv -b 8 ero.bin
```

The example above computes the Most Common Value (MCV) estimator on 8 bits samples read from the `ero.bin` binary file.

## Auto-correlation

The Python script `autocorrelation.py` plots the autocorrelations for a random binary file, reading the file by words of `b` bits. The `d` parameter limits the maximum correlation lag (depth) of the signal with itself.

```
$ python autocorrelation.py -b 8 -d 100 -t "Plot title" coso.bin autocorr.png
```

This example plots the autocorrelation of the signal in a maximum lag of 100 samples of 8 bits each.

<!-- ## Howtos and recipies -->
<!-- TODO -->

<!-- ### How to estimate thermal and flicker noise amplitude factors -->
<!-- TODO -->

<!-- ### How to run standardized test -->
<!-- TODO -->

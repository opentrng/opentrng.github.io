---
title: "Documentation"
layout: single
toc: true
---

This section provides user and developer documentation for **OpenTRNG** the open-source TRNG framework.

## Repository organization

The OpenTRNG [repository](https://github.com/opentrng/ptrng) is organized into the following main directories:

* `analysis`: contains the tools (such as entropy estimators and auto-correlations) for the [analysis](analysis#analyze-and-evaluate-outputs) of the resulting random binary sequences,
* `emulator`: includes the ring oscillator [time series emulator](emulator#emulate-noisy-ring-oscillators) and the [raw random number emulators](emulator#emulate-raw-random-numbers),
* `hardware`: encloses HDL sources for [simulation](hardware#simulate-hdl-sources) and [FPGA implementation](hardware#compile-for-fpga) of the PTRNG,
* `remote`: include scripts for [remote controlling](remote) the **OpenTRNG** hardware target from a PC.

## Prerequisites

To take full advantage of **OpenTRNG**, you will need: Python 3, an HDL simulator, and a hardware toolchain (for FPGA or ASIC). Running on Ubuntu Linux is recommended, though it is compatible with other Linux distributions as well as Windows.

### Python

To get the required installation of Python 3, please install the following packages:

```
$ sudo apt install python3 python3-venv python3-dev
```

Create a virtual environment `python3 -m venv .venv` activate the venv `source .ven/bin/activate` and install required packages with `pip install -r requirements.txt`. For other Python environment or package managers (like `conda`), all required modules are listed in `requirements.txt`.

### HDL simulator

All **OpenTRNG** blocks are ported to Verilog and VHDL. HDL can be simulated with [Verilator](https://www.veripool.org/verilator/), [GHDL](https://github.com/ghdl/ghdl) or any other simulators such as QuestaSim. Ensure that the `verilator`, `ghdl`, or the appropriate simulator command is accessible in your system's path. Testbenches for simulation and verification are written in Python using [cocotb](https://www.cocotb.org). The generated waveforms (`vcd` files) can be visualized with [GTKWave](https://sourceforge.net/projects/gtkwave).

If not using `ghdl`, refer to the `config.mk` file in the `hardware/sim` directory to configure your preferred simulator for all testbenches.

### Hardware

To go beyond the use of **OpenTRNG** emulators, you will need a hardware target. This allows you to run the provided HDL implementations on an FPGA (as instance), interact with the TRNG in real conditions, and generate random numbers directly from the physical entropy source.

#### Hardware target

**OpenTRNG** comes with direct compatibility to [Digilent Arty7 FPGA](https://digilent.com/reference/programmable-logic/arty-a7/start) board. It can be ordered from [Farnell](https://farnell.com), [Digikey](https://www.digikey.com), [Mouser](https://www.mouser.fr), etc. Other FPGA targets and boards can be easily supported, please find more information on the [hardware](hardware#fpga-targets) documentation page.

![image-center](/assets/images/arty7.png)

#### Hardware tool-suite

As of now the **OpenTRNG** project only supports [Vivado for Xilinx](https://www.xilinx.com) FPGAs. The project is tested on Vivado versions `2018.3`, `2020.2` and `2021.1`.

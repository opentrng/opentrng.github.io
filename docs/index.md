---
title: "Documentation"
layout: single
toc: true
---

## Repository organization

Take a look at [repository](https://github.com/opentrng/ptrng) organization below and, based on your requirements, navigate to the relevant directory to begin using **OpenTRNG**. The repository structure contains these main folders:

* `analysis`: contains the tools for the [analysis](analysis/#analyze-and-evaluate-outputs) of the resulting random binary sequences (such as entropy estimators and auto-correlations),
* `emulator`: includes the [ring oscillator time series emulator](emulator/#emulate-noisy-ring-oscillators) and the [raw random number emulators](emulator/#emulate-raw-random-numbers),
* `hardware`: encloses HDL sources for [simulation](hardware/#simulate-hdl-sources) and [FPGA implementation](hardware/#compile-for-fpga) of the PTRNG,
* `remote`: include scripts for [remote control](remote) the **OpenTRNG** FPGA target from a PC.

## Prerequisites

In order to fully take benefit of **OpenTRNG**, you will need: python 3, an HDL simulator and an hardware (FPGA) tool-suite.

### Python

To get the required installation of Python 3, please install the following packages:

```
$ sudo apt install python3 python3-venv python3-dev
```

Create a virtual environment `$ python3 -m venv .venv` activate the venv `$ source .ven/bin/activate` and install required packages with `$ pip install -r requirements.txt`. For other Python environment or package managers (like `conda`), all required modules are listed in `requirements.txt`.

### HDL simulator

You can perform VHDL simulation for **OpenTRNG** blocks using [GHDL](https://github.com/ghdl/ghdl) or other various simulators such as QuestaSim. Ensure that the `ghdl` command (or other simulator command) is accessible in your path. Testbenches for simulation and verification are written in python with [cocotb](https://www.cocotb.org). The generated waves (`vcd` files) can be displayed with [GTKWave](https://sourceforge.net/projects/gtkwave).

If you are not using `ghdl`, please refer to the file `hardware/sim/config.mk` to configure your own simulator for all the testbenches.

### Hardware

If you want to use more than just the **OpenTRNG** emulators, you will need a hardware target.

#### Hardware target

**OpenTRNG** comes with direct compatibility to [Digilent Arty7 FPGA 35T](https://digilent.com/reference/programmable-logic/arty-a7/start) board. It can be ordered from [Farnell](https://farnell.com), [Digikey](https://www.digikey.com), [Mouser](https://www.mouser.fr), etc. Other FPGA targets and boards can be easily supported, please find more information on the [hardware](hardware#fpga-targets) documentation page.

![image-center](/assets/images/arty7.png)

#### Hardware tool-suite

As of now the **OpenTRNG** project only supports [Vivado for Xilinx](https://www.xilinx.com) FPGAs. The project is tested on Vivado versions `2018.3`, `2020.2` and `2021.1`.

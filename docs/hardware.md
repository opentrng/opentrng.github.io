---
title: "Hardware"
layout: single
toc: true
---

## Hardware architecture

### Digital noise sources

#### ERO

#### MURO

#### COSO

### Dependencies

OpenTRNG projects depends on the following submodules:

| GitHub | Descrition |
| :----- | :--------- |
| [vhdl-extras](https://github.com/kevinpt/vhdl-extras) | Provides a set of standard and common VHDL entities. |
| [fluart](https://github.com/marcj71/fluart) | The feature-less UART to provide communication between PC and target. |
| [cmd_proc](https://github.com/marcj71/cmd_proc) | handle simple read-write adress/data packet processing on the UART. |

We also use the [Corsair](https://github.com/esynr3z/corsair) tool to generate the register map (see [this section](#register-map)).

## Simulate HDL sources

Testbenches for simulating HDL sources are scripted using [cocotb](https://www.cocotb.org) in Python, and are located in the `hardware/sim` directory. Each testbench comprises multiple test cases. The python [ring-oscillator emulator](emulator#emulate-noisy-ring-oscillators) is used to generate noisy clock signals for the testcases.

For example, to run the simulation of the COSO testbench, use the following commands:

```
cd hardware/sim/test_coso
make
```

The summary of the testbench simulation is displayed in the terminal:

```
********************************************************************************************
** TEST                                STATUS  SIM TIME (ns)  REAL TIME (s)  RATIO (ns/s) **
********************************************************************************************
** test_coso.test_total_failure_alarm   PASS       10010.00           0.09     113097.26  **
** test_coso.test_gen_random_100        PASS       63706.73           3.67      17337.83  **
********************************************************************************************
** TESTS=2 PASS=2 FAIL=0 SKIP=0                    73716.73           4.04      18252.38  **
********************************************************************************************
```

Thanks to `ghdl` simulator, all testbenches record their waveforms in the `waves.vcd` file. Waveform files can be visualized using tools like [GTKWave](https://sourceforge.net/projects/gtkwave) or [Wavedrom](https://wavedrom.com), for example.

![COSO testbench waves](/assets/images/cosowaves.png)

## Compile for FPGA

The VHDL provided in the `hardware/hdl` directory is target agnostic, it can be synthetized for all FPGA vendors (even ASIC). On the contrary, ring-oscillator implementations are specific to the target. As instance, the directory `target/common/xilinx` provides a `ring.vhd` dedicated implementation for Xilinx FPGAs.

### FPGA targets

As of now, 35T and 100T ? (correct this in docs/index.md)

![image-center](/assets/images/arty7.png)

Add new target

### Synthetize, place route and program device

Scaffold script `generate_vivado_project.tcl` is provided to generate Xilinx Vivado projects for any targets, the `tcl` script is located here `hardware/target/fpga`. Use the following command to generate the Vivado project `opentrng_arty_a7_35t.xpr` in the directory `arty_a7_35t` for the target `xc7a35ticsg324-1L`:

```
cd hardware/target/fpga
vivado -mode tcl -source generate_vivado_project.tcl -tclargs arty_a7_35t xc7a35ticsg324-1L
```

The start Vivado with the command:

```
vivado -mode gui arty_a7_35t/opentrng_arty_a7_35t.xpr
```

By runing synthesis, implementation and bitstream generation, you will be able to program your target.

Program

Scripting

### Custom configurations

#### Register map

[Register map](registers)

#### Ring oscillators

<!-- ## OpenTitan compatibility -->
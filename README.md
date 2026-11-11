# RISC-V instruction decoder

A SystemVerilog simulation of instruction fetch and decode for a subset of RV32 instructions. The decoder extracts opcode, register, and function fields, assembles immediates, and prints a trace of the instruction at each program counter value.

The [decode logic](rtl/cpu.sv) is the coursework contribution. The memory model and testbench provide the simulation harness. This is a decoder demo: the trace does not execute arithmetic, branches, or memory instructions.

## Run the sample

With Icarus Verilog and `vvp` installed, run from the repository root:

```sh
iverilog -g2012 -s system_tb -o sim.out -c sim/files.f
vvp sim.out
```

The simulation reads [init.mem](init.mem), which encodes the four instructions in [sample.S](examples/sample.S). In the trace, addresses `0x00` through `0x0c` decode to `add`, `xor`, `andi`, and `ori`. The simulator also writes `simulation_results.vcd` for waveform inspection in GTKWave. The sample uses only four words of the ROM, so a short-memory-image warning can appear before the trace.

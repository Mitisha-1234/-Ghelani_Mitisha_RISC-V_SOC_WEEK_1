<div align="center">

# Day 2 - Timing Libraries, Synthesis Approaches, and Efficient Flip-Flop Coding

</div>
Today, we are going to:
1.Learn about the .lib timing library and explore the Sky130 PDK timing file.
2.Understand the role of timing libraries in mapping RTL to real hardware.
3.Compare hierarchical vs. flat synthesis and see when each is useful.
4.Practice efficient flip-flop coding styles in Verilog for better synthesis results.

## Table of Content
1.Introduction to timing.libs

2.Hierarchical vs Flat Synthesis

3.Various Flop coding styles and optimization

## Introduction to timing.libs
In digital design, a timing library (.lib) is a file that describes how each standard cell (like gates, flip-flops, and multiplexers) behaves in terms of timing, power, and functionality. These libraries are essential for synthesis and static timing analysis because they help tools estimate how fast a circuit will run and how much power it will consume.

Follow the commands to open sky130_fd_sc_hd__tt_025C_1v80.lib file:
```bash
gvim sky130_fd_sc_hd__tt_025C_1v80.lib
```
![Alt Text](Palak_ysoys.png)

## Hierarchical vs Flat Synthesis
1.Hierarchical Synthesis:
The design is kept in separate modules (like blocks or subcircuits). Each module is synthesized on its own, and then they are connected together. This makes large designs easier to manage, reuse, and debug, but sometimes leads to less optimization across modules.Hierarchical synthesis is good when you want modularity, reuse, and easier debugging.
2.Flat Synthesis:
All modules are combined into a single large design before synthesis. This allows the tool to optimize the entire circuit globally, which can improve performance and reduce area, but it makes the design harder to read, debug, or reuse.Flat synthesis is good when you want maximum optimization for speed or area.

### Example of Hierarchical Synthesis
![Alt Text](Palak_ysoys.png)

### Example of Flat Synthesis
![Alt Text](Palak_ysoys.png)

## Various Flop coding styles and optimization



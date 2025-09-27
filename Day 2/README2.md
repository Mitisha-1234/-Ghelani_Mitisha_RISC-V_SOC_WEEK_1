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
<img width="1917" height="1076" alt="Day 2  lib file" src="https://github.com/user-attachments/assets/10635e06-377b-4f41-944c-953939590821" />

## Hierarchical vs Flat Synthesis
1.Hierarchical Synthesis:
The design is kept in separate modules (like blocks or subcircuits). Each module is synthesized on its own, and then they are connected together. This makes large designs easier to manage, reuse, and debug, but sometimes leads to less optimization across modules.Hierarchical synthesis is good when you want modularity, reuse, and easier debugging.
2.Flat Synthesis:
All modules are combined into a single large design before synthesis. This allows the tool to optimize the entire circuit globally, which can improve performance and reduce area, but it makes the design harder to read, debug, or reuse.Flat synthesis is good when you want maximum optimization for speed or area.

### Example of Hierarchical Synthesis
<img width="1917" height="1076" alt="Day 2 hierarchy" src="https://github.com/user-attachments/assets/718bd04c-0b1c-44a8-917d-397013edf175" />

### Example of Flat Synthesis
<img width="1917" height="1076" alt="Day 2 Flatten" src="https://github.com/user-attachments/assets/8e86309e-d1bb-450d-9944-4fe166707122" />

## Various Flop coding styles and optimization
Flip-flops are the basic storage elements in digital systems, holding one bit of data and updating it on clock edges. In Verilog, there are multiple ways to describe flip-flops depending on how resets and sets are handled. For example, you can code flops with asynchronous reset, synchronous reset, or set/reset combinations.

Using clear and efficient coding styles is important because synthesis tools (like Yosys) can then map them directly to the most suitable flip-flop cells in the standard cell library. This not only improves area and timing but also avoids unnecessary logic.

### Asynchronous Reset D Flip-Flop
An asynchronous reset D flip-flop is a storage element that updates its output (Q) on the clock edge but can be reset immediately when the reset signal is active, regardless of the clock. This makes it useful for quickly initializing circuits to a known state after power-up.
<img width="1917" height="1076" alt="Day 2 Asynchronous Reset D Flip-Flop" src="https://github.com/user-attachments/assets/86ad2c67-e837-4660-a6b3-a16a6e531a31" />

### Asynchronous Set D Flip-Flop
An asynchronous set D flip-flop updates its output (Q) on the active clock edge, but when the set signal is activated, the output is forced to 1 immediately, without waiting for the clock. It is commonly used when a circuit must be initialized or forced into a logic high state instantly.
<img width="1917" height="1076" alt="Day 2 Asynchronous Set D Flip-Flop" src="https://github.com/user-attachments/assets/139e703c-3887-47f1-b218-9ee2d26847be" />


### Synchronous Reset D Flip-Flop
A synchronous reset D flip-flop updates its output (Q) on the clock edge. The reset signal only takes effect together with the clock, meaning the output is cleared to 0 only at the next active clock edge. This makes it easier to control and analyze timing in digital circuits.
<img width="1917" height="1076" alt="Day 2 Synchronous Reset D Flip-Flop" src="https://github.com/user-attachments/assets/fc9af3d0-263d-41f8-a738-0471a16befe3" />

To view the gtkwave of these Flip-Flop, run the following commands:
```bash
iverilog dff_asyncres.v tb_dff_asyncres.v
```
```bash
./a.out
```
```bash
gtkwave tb_dff_asyncres.vcd
```
<img width="1917" height="1076" alt="Day 2 asyncres vcd" src="https://github.com/user-attachments/assets/ea8257d4-2abe-40f8-8b79-ff09d879cd7e" />

Run the same commands for async_set and syncres...
<img width="1917" height="1076" alt="Day 2 async_set vcd" src="https://github.com/user-attachments/assets/290e619b-7980-4dbc-8aea-a1fbefe7d87f" />

<img width="1917" height="1076" alt="Day 2 syncres v" src="https://github.com/user-attachments/assets/55cc6385-b3fc-4a7e-b296-a69b53e5e41a" />

To view the synthesis with Yosys of these Flip-Flop, run the following commands:
```bash
yosys
```
```bash
read_liberty -lib /address/to/your/sky130/file/sky130_fd_sc_hd__tt_025C_1v80.lib
```
```bash
read_verilog /path/to/dff_asyncres.v
```
```bash
synth -top dff_asyncres
```
```bash
dfflibmap -liberty /address/to/your/sky130/file/sky130_fd_sc_hd__tt_025C_1v80.lib
```
```bash
abc -liberty /address/to/your/sky130/file/sky130_fd_sc_hd__tt_025C_1v80.lib
```
```bash
show
```
<img width="1917" height="1076" alt="Day 2 asyncres " src="https://github.com/user-attachments/assets/1c14cdec-d4b0-4c3f-adc6-04e90fb3651b" />

Run the same commands for asyncres and syncres...

<img width="1917" height="1076" alt="Day 2 async set" src="https://github.com/user-attachments/assets/26cb7cac-0bc0-4c85-828c-5c9c390a4242" />
<img width="1917" height="1076" alt="Day 2  syncres" src="https://github.com/user-attachments/assets/2895ec3a-7882-4321-8cac-a6d0fe3df092" />



This session has given me a strong foundation in three important aspects of digital design: understanding timing libraries and how they connect RTL descriptions to actual hardware behavior, exploring different synthesis methods and their effect on optimization, and practicing efficient flip-flop coding styles for better synthesis results. Working with these topics has improved my coding discipline and shown me how design choices influence performance, area, and power. By continuing to experiment with these concepts, I can deepen my knowledge and build greater confidence in RTL design.





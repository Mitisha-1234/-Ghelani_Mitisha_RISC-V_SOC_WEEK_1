<div align="center">

# Day 4: Gate-Level Simulation (GLS), Blocking vs. Non-Blocking in Verilog, and Synthesis-Simulation Mismatch

</div>

Welcome to Day 4 of the RTL Workshop! In today’s session, we’ll explore important aspects of digital design, including gate-level simulation, the distinction between blocking and non-blocking Verilog assignments, and issues that can arise from synthesis versus simulation differences. The workshop blends concepts with practical exercises, allowing you to apply what you learn through hands-on labs.

## Table of Content

1.GLS,Synthesis-Simulation Mismatch and Blocking/Non-blocking statements

2.Labs on GLS and Synthesis-Simulation Mismatch

3.Labs on synth-sim mismatch for blocking statement

## GLS,Synthesis-Simulation Mismatch and Blocking/Non-blocking statements

### Gate-Level Simulation (GLS):
Gate-Level Simulation is a crucial step in verifying a digital circuit after RTL has been synthesized into a gate-level netlist. It allows designers to check the functional correctness, timing behavior, power consumption, and test structures like scan chains used for design-for-testability. GLS is performed after synthesis but before the physical design phase to catch potential issues early. There are two main types: functional GLS, which focuses on logic verification without realistic delays, and timing GLS, which incorporates timing information to detect real-world issues such as setup or hold violations. This process ensures that the synthesized design faithfully implements the intended RTL behavior.

### Synthesis-Simulation Mismatch:
A synthesis-simulation mismatch arises when the behavior observed in RTL simulation does not match the behavior of the synthesized gate-level netlist or the actual hardware. This can happen due to the use of non-synthesizable constructs, incomplete or ambiguous coding practices, or differences in how synthesis and simulation tools interpret the code. To prevent such mismatches, designers must write clear, synthesizable RTL and adhere to best coding practices, avoiding constructs that are not supported by synthesis.

### Blocking vs. Non-Blocking Assignments in Verilog:
Verilog provides two types of assignments in procedural blocks: blocking (=) and non-blocking (<=). Blocking assignments execute immediately in the order they appear, making them ideal for modeling combinational logic. Non-blocking assignments, on the other hand, schedule updates to occur concurrently at the end of the time step, which is suitable for sequential logic driven by clock edges. Using the correct type of assignment is essential for accurately representing combinational and sequential behaviors in hardware designs.

## Labs on GLS and Synthesis-Simulation Mismatch

2x1 MUX using a ternary operator is given below:
<img width="1917" height="1076" alt="Day 4 ternary_operator_mux v" src="https://github.com/user-attachments/assets/01e43628-8187-4217-b15c-ba3b37dd87a0" />

The gtkwave for above code is:
<img width="1917" height="1076" alt="Day 4 tb_ternary_operator_mux vcd" src="https://github.com/user-attachments/assets/7b13756b-491b-4fbf-9f9c-65878f20c1e0" />

The Yosys output for above code is:
<img width="1917" height="1076" alt="Day 4 ternary_operator_mux" src="https://github.com/user-attachments/assets/2efd65ec-647e-4441-9709-686d8a192052" />

GLS gtkwave for above synthesized file:
<img width="1917" height="1076" alt="Day 4 tb_ternary_operator_mux vcd 2" src="https://github.com/user-attachments/assets/c6a7abcd-d8f3-4b42-bf6a-6abff1cdbc2f" />

Now,following is the verilog code which has got some deliberate error like the sensitivity list is incomplete and should include all relevant signals, specifically i0, i1, and sel. Additionally, a non-blocking assignment is used in combinational logic, whereas blocking assignments (=) would be more appropriate in this context.
<img width="1917" height="1076" alt="Day 4 bad_mux v" src="https://github.com/user-attachments/assets/6885b28f-f38b-4643-beda-94739a09629c" />

The gtkwave for above code is:
<img width="1917" height="1076" alt="Day 4 tb_bad_mux vcd" src="https://github.com/user-attachments/assets/ed611e25-08a5-4739-addd-442cfdbb2d86" />

GLS gtkwave for above code:
<img width="1917" height="1076" alt="Day 4 tb_bad_mux vcd 2" src="https://github.com/user-attachments/assets/7e4614cb-4394-43cb-98f0-ecdbd8252049" />


## Labs on synth-sim mismatch for blocking statement
In the context of blocking assignments (=) in Verilog, synthesis-simulation mismatches can occur when the intended sequential behavior is incorrectly modeled as combinational. Since blocking statements execute immediately and in order, using them in sequential logic (e.g., inside a clocked always block) can lead to simulation results that differ from the synthesized hardware, where flip-flops and registers follow clock edges. To avoid such mismatches, blocking assignments should generally be reserved for combinational logic, ensuring that the simulation closely reflects the behavior of the synthesized design.

Here is the example file for above problem statement where the problem is because of the way the assignments are ordered, d ends up taking the earlier value of x instead of the updated result. A better approach is to ensure that all temporary or intermediate values are calculated first before being utilized in later expressions.
<img width="1917" height="1076" alt="Day 4 blocking_caveat v" src="https://github.com/user-attachments/assets/cb0e25d1-dbfa-4bda-b132-581aa60dbbd1" />

The gtkwave for above code is:
<img width="1917" height="1076" alt="Day 4 tb_blocking_caveat vcd" src="https://github.com/user-attachments/assets/60e899fd-f6ad-4810-9e41-8ccb19b252aa" />

The Yosys output for above code is:
<img width="1917" height="1076" alt="Day 4 blocking_caveat" src="https://github.com/user-attachments/assets/3fa93a62-f045-4491-b5de-78da5647c69d" />

GLS gtkwave for above code:
<img width="1917" height="1076" alt="Day 4 tb_blocking_caveat vcd 2" src="https://github.com/user-attachments/assets/b2257549-90da-4c05-8b2a-10a15c02fc15" />

Gate-Level Simulation (GLS) plays a crucial role in verifying that a synthesized netlist behaves correctly, meets timing requirements, and maintains test structures like scan chains. Differences between RTL simulation and post-synthesis behavior, known as synthesis-simulation mismatches, often arise from unclear or non-synthesizable coding, so writing precise and fully synthesizable RTL is essential to prevent unexpected results. In Verilog, proper use of assignments is key: blocking assignments (=) are best suited for modeling combinational logic, while non-blocking assignments (<=) accurately represent sequential circuits triggered by clock edges. Hands-on labs complement these concepts by providing practical experience, helping learners identify and avoid common pitfalls in RTL coding and ensuring that simulations align closely with actual synthesized hardware behavior.


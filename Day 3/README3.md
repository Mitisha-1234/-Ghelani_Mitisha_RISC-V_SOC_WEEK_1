<div align="center">

  # Day 3 - Combinational and Sequential Optimization
  
</div>
Optimization of combinational and sequential circuits along with introduction of techniques to enhance efficiency and performance is discussed in this section.

## Table of Contents

1. Introduction to Optimization Techniques
2. Combinational Logic Optimizations
3. Sequential Logic Optimizations
4. Sequential optimization for unused output

## Introduction to Optimization Techniques

### Optimization Techniques in VLSI Design

In modern VLSI flows, synthesis tools apply several optimization strategies to improve area, power, and timing while keeping the functional behavior of the design intact. Below are four widely used optimization techniques explained in detail.

### 1.Constant Propagation
Constant propagation is when signals that always stay fixed (like always 0 or always 1) are directly replaced with those values. This removes extra logic and makes the circuit simpler. For example, if an AND gate always gets 0 on one input, the output will always be 0, so the gate can be removed. This reduces circuit size, improves speed, and saves power.

### 2.State Optimization in FSMs
Finite State Machines (FSMs) can sometimes have extra or redundant states. State optimization cleans them up by merging similar states, removing unused ones, and choosing better ways to encode states (like binary, one-hot, or gray coding). This makes the FSM smaller, uses fewer flip-flops, and runs more efficiently. Extra techniques like clock gating can also reduce power usage.

### 3.Cloning
Cloning means duplicating a cell or module when one element is overloaded with too many connections. Splitting the load between the original and the clone reduces delay and helps signals travel faster. This method improves timing, balances loads, and sometimes reduces power by avoiding large drivers.

### 4.Retiming
Retiming is when flip-flops are moved around inside the circuit without changing its overall behavior. By shifting registers before or after logic, the longest paths can be made shorter. This allows the design to run at a higher clock speed, balances delays between stages, and can even save power.

## Combinational Logic Optimizations
Combinational logic optimization is the process of simplifying logic circuits without changing their function. It reduces the number of gates, shortens paths, and lowers power consumption. Common methods include Boolean algebra simplification, removing redundant logic, and factoring expressions. The goal is to make the design smaller, faster, and more efficient.

We will perform the Combinational Logic Optimization for following verilog files:
![Alt Text](Palak_ysoys.png)
![Alt Text](Palak_ysoys.png)
![Alt Text](Palak_ysoys.png)
![Alt Text](Palak_ysoys.png)
![Alt Text](Palak_ysoys.png)
![Alt Text](Palak_ysoys.png)
![Alt Text](Palak_ysoys.png)

Take the steps from the Day 1 Synthesis Lab, and insert the following commands in the flow right after abc -liberty but before synth -top.
```bash
opt_clean -purge
```
Do the same for all 7 files and observe the yosys output:
![Alt Text](Palak_ysoys.png)
![Alt Text](Palak_ysoys.png)
![Alt Text](Palak_ysoys.png)
![Alt Text](Palak_ysoys.png)
![Alt Text](Palak_ysoys.png)
![Alt Text](Palak_ysoys.png) (multiple_module_opt)
![Alt Text](Palak_ysoys.png) (multiple_module_opt2)

## Sequential Logic Optimizations
Sequential logic optimization focuses on improving circuits that use memory elements like flip-flops and latches. The goal is to reduce area, power, and delay while keeping the same behavior. Common techniques include retiming (moving registers to balance delays), state optimization (simplifying FSMs), and register sharing or removal. These methods help designs run faster and use fewer resources. 

I have shown one example of Sequential Logic Optimizations






   

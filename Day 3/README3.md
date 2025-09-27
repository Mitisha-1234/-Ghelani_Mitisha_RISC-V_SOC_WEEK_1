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




   

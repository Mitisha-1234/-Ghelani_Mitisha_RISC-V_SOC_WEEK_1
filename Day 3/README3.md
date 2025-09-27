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

<img width="1917" height="1076" alt="Day 3 opt_check v" src="https://github.com/user-attachments/assets/24b616bf-301e-4d50-ab99-06af592c775c" />
<img width="1917" height="1076" alt="Day 3 opt_check2 v" src="https://github.com/user-attachments/assets/95afe3ed-8f31-497e-9b2c-8896774e0882" />
<img width="1917" height="1076" alt="Day 3 opt_check3 v" src="https://github.com/user-attachments/assets/362fb616-cfb4-4639-a986-1d07879be125" />
<img width="1917" height="1076" alt="Day 3 opt_check4 v" src="https://github.com/user-attachments/assets/55ebff8b-497d-4d87-92df-76fdacf7d746" />
<img width="1917" height="1076" alt="Day 3 multiple_module_opt v" src="https://github.com/user-attachments/assets/1f34737e-7693-4892-9906-91fb74acb1bd" />
<img width="1917" height="1076" alt="Day 3 multiple_module_opt2 v" src="https://github.com/user-attachments/assets/d01374d2-24f8-4ebe-9fd4-a7ee5e923ad1" />



Take the steps from the Day 1 Synthesis Lab, and insert the following commands in the flow right after abc -liberty but before synth -top.
```bash
opt_clean -purge
```
Do the same for all 7 files and observe the yosys output:
<img width="1917" height="1076" alt="Day 3 opt_check" src="https://github.com/user-attachments/assets/f9fbc1a1-afd3-4084-aed2-9976abb5b5ed" />
<img width="1917" height="1076" alt="Day 3 opt_check2" src="https://github.com/user-attachments/assets/de051b08-2af1-4301-82ae-000fb38bfc76" />
<img width="1917" height="1076" alt="Day 3 opt_check3" src="https://github.com/user-attachments/assets/dd8f9cda-ec16-4ef5-9c79-fe55010ec66a" />
<img width="1917" height="1076" alt="Day 3 opt_check4" src="https://github.com/user-attachments/assets/4474c217-86c3-4540-9b27-84d2ff43b658" />
<img width="1917" height="1076" alt="Day 3 multiple_module_opt" src="https://github.com/user-attachments/assets/0e075bdd-9772-43d7-a493-1c8f8e9d60cb" />
<img width="1917" height="1076" alt="Day 3 multiple_module_opt2" src="https://github.com/user-attachments/assets/e3f3fe41-5607-47cc-b53f-813b8170751e" />

## Sequential Logic Optimizations
Sequential logic optimization focuses on improving circuits that use memory elements like flip-flops and latches. The goal is to reduce area, power, and delay while keeping the same behavior. Common techniques include retiming (moving registers to balance delays), state optimization (simplifying FSMs), and register sharing or removal. These methods help designs run faster and use fewer resources. 

I have shown one example of Sequential Logic Optimization.
Below is the verilog file
<img width="1917" height="1076" alt="Day 3 const1 v" src="https://github.com/user-attachments/assets/eb7e4c2b-f734-4b2c-bf89-763f93a5468e" />

Follow the steps from Day 1 to observe the gtkwave:
<img width="1917" height="1076" alt="Day 3 const1 gtkwave" src="https://github.com/user-attachments/assets/400527cc-7b90-488c-ad9c-ff02fdf0efb5" />

Follow the steps from Day 1 to observe the ysoys outptut:
<img width="1917" height="1076" alt="Day 3 const1" src="https://github.com/user-attachments/assets/31a496ef-1614-485f-8ac4-a03599dd876a" />

## Sequential optimization for unused output
If a flip-flop or register drives an output that is never used in the design, synthesis tools can remove it. This prevents unnecessary storage elements, reduces area, and lowers power consumption without affecting the circuit’s functionality. 

Below is the verilog code for unused output:
<img width="1917" height="1076" alt="Day 3 counter_opt v" src="https://github.com/user-attachments/assets/f7df62d4-2a6b-4094-a0f6-4879e1901bb4" />

Below is the verilog code when all counter bits are used:
<img width="1917" height="1076" alt="Day 3 counter_opt2 v" src="https://github.com/user-attachments/assets/1855485d-660f-4a45-b437-de8b8f1f0798" />

Below is the synthesized netlist visualization for the above code:

<img width="1917" height="1076" alt="Day 3 counter_opt" src="https://github.com/user-attachments/assets/fd2bdde9-1140-404d-acc8-a0394eac5575" />
You can see that Yosys optimizes away the unused bits of the counter, keeping only the logic required for count[0].

<img width="1917" height="1076" alt="Day 3 counter_opt2" src="https://github.com/user-attachments/assets/d428f75e-a351-4c09-ae0a-aa73b994c6d9" />
This time, the full counter logic is preserved since all bits of count are required to compute the output.

This course focuses on improving the efficiency of combinational and sequential digital circuits through practical Verilog exercises. It covers techniques like constant propagation to simplify logic, state optimization to reduce and encode FSM states efficiently, cloning to enhance timing and balance load, and retiming to reposition registers for better performance. Six hands-on labs demonstrate these concepts with examples of optimized combinational circuits and D flip-flop behaviors, including code snippets and output visualizations.





   

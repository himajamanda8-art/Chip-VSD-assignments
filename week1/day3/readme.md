# Day 3: Combinational and Sequential Optimization

Welcome to Day 3 of this workshop! Today we discuss optimization of combinational and sequential circuits, introducing techniques to enhance efficiency and performance.

---

## Table of Contents

- [1. Constant Propagation](#1-constant-propagation)
- [2. State Optimization](#2-state-optimization)
- [3. Cloning](#3-cloning)
- [4. Retiming](#4-retiming)
- [5. Labs on Optimization](#5-labs-on-optimization)
  - [Lab 1](#lab-1)
  - [Lab 2](#lab-2)
  - [Lab 3](#lab-3)
  - [Lab 4](#lab-4)
  - [Lab 5](#lab-5)
  - [Lab 6](#lab-6)

---

## 1. Constant Propagation

In VLSI design, constant propagation is a compiler optimization technique used to replace variables with their constant values during synthesis. This can simplify design and enhance performance.

**How it works:**  
Constant propagation analyzes the design code to identify variables with constant values. These are replaced directly, allowing tools to simplify logic and reduce circuit size.

**Benefits:**
- **Reduced Complexity:** Simpler logic, smaller circuit.
- **Performance Improvement:** Faster execution and reduced delays.
- **Resource Optimization:** Fewer gates or flip-flops required.

- ![Alt Text]!<img width="660" height="298" alt="day3(1)" src="https://github.com/user-attachments/assets/cdc771ad-a707-48a5-b85b-1315266a33de" />

---

## 2. State Optimization

State optimization refines finite state machines (FSMs) to improve efficiency in IC design. It reduces the number of states, optimizes encoding, and minimizes logic.

**How it is done:**
- **State Reduction:** Merge equivalent states using algorithms.
- **State Encoding:** Assign optimal codes to states.
- **Logic Minimization:** Use Boolean algebra or tools for compact equations.
- **Power Optimization:** Techniques like clock gating reduce dynamic power.

---

## 3. Cloning

Cloning duplicates a logic cell or module to optimize performance, reduce power, or improve timing by balancing load or reducing wire length.

**How it’s done:**
- Identify critical paths using analysis tools.
- Duplicate the target cell/module.
- Redistribute connections to balance load.
- Place and route the cloned cell.
- Verify improvement via timing and power analysis.

-  ![Alt Text]!<img width="549" height="349" alt="day3(2)" src="https://github.com/user-attachments/assets/00261d5b-9ccd-413e-9b3e-bb13de1a88ef" />

---

## 4. Retiming

Retiming is a design optimization technique that improves circuit performance by repositioning registers (flip-flops) without changing functionality.

**How it is done:**
1. **Graph Representation:** Model circuit as a directed graph.
2. **Register Repositioning:** Move registers to balance path delays.
3. **Constraints Analysis:** Maintain timing and functional equivalence.
4. **Optimization:** Adjust register positions to minimize clock period and optimize power.

---

## 5. Labs on Optimization

### Lab 1

Below is the Verilog code for Lab 1:

```verilog
module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule
```

**Explanation:**
- `assign y = a ? b : 0;` means:
  - If `a` is true, `y` is assigned the value of `b`.
  - If `a` is false, `y` is 0.

Follow the steps from [Day 1 Synthesis Lab](https://github.com/Ahtesham18112011/RTL_workshop/tree/main/Day_1#6-synthesis-lab-with-yosys) and add the following between `abc -liberty` and `synth -top`:
```shell
opt_clean -purge
```

 ![Alt Text]!<img width="1798" height="704" alt="day3(3)" src="https://github.com/user-attachments/assets/7f58c266-1f60-416d-a78a-9781916c37a5" />

 ### Lab 2

Verilog code:

```verilog
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```

**Code Analysis:**
- Acts as a multiplexer:
  - `y = 1` if `a` is true.
  - `y = b` if `a` is false.

![Lab 2 Output]<img width="1810" height="564" alt="day3(4)" src="https://github.com/user-attachments/assets/df107158-3fd4-41f2-9daf-26e1438e43bd" />

---

### Lab 3

Verilog code:

```verilog
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```

**Functionality:**  
2-to-1 multiplexer; `y = a ? 1 : b` (outputs `1` when `a` is true, otherwise `b`).

![Lab 3 Output]<img width="1803" height="705" alt="day3(5)" src="https://github.com/user-attachments/assets/5f597e95-e2ee-48ac-9a37-7742273bf208" />

---

### Lab 4

Verilog code:

```verilog
module opt_check4 (input a , input b , input c , output y);
 assign y = a?(b?(a & c ):c):(!c);
 endmodule
```

**Functionality:**
- Three inputs (`a`, `b`, `c`), output `y`.
- Nested ternary logic:
  - If `a = 1`, `y = c`.
  - If `a = 0`, `y = !c`.
- Logic simplifies to:  
  `y = a ? c : !c`

![Lab 4 Output]<img width="1811" height="707" alt="day3(6)" src="https://github.com/user-attachments/assets/ce66fa28-490a-457a-bd0e-525218673d18" />


---

### Lab 5

Verilog code:

```verilog
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end
endmodule
```

**Functionality:**
- D flip-flop with:
  - Asynchronous reset to 0
  - Loads constant `1` when not in reset

![Lab 5 Output]<img width="1784" height="618" alt="day3(7)" src="https://github.com/user-attachments/assets/42473584-51d1-45c7-ab2d-3a80833b159f" />


---

### Lab 6

Verilog code:

```verilog
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end
endmodule
```

**Functionality:**
- D flip-flop always sets output `q` to `1` (regardless of reset or clock).

![Lab 6 Output]<img width="705" height="574" alt="day3(8)" src="https://github.com/user-attachments/assets/c7404448-ef65-4ca3-be77-f323ab807eab" />



---

## Summary
- **Focus:** Optimization techniques for combinational and sequential circuits in digital design, with practical Verilog labs.
  
- **Topics Covered:**
  1. **Constant Propagation:** Replacing variables with constant values to simplify logic and improve circuit efficiency.
  2. **State Optimization:** Reducing states and optimizing encoding in finite state machines to use less logic and power.
  3. **Cloning:** Duplicating logic cells/modules to improve timing and balance load.
  4. **Retiming:** Repositioning registers in a circuit to enhance performance without altering its function.

- **Labs:** Six practical Verilog labs illustrate these concepts, including examples of combinational logic optimizations and D flip-flop behaviors, each with code snippets and output images.





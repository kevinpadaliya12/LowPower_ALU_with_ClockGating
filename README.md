# LowPower_ALU_with_ClockGating
# Low-Power ALU with Clock Gating (Verilog HDL)

 Introduction
An **Arithmetic Logic Unit (ALU)** is the heart of a CPU, performing arithmetic and logical operations.  
In modern VLSI design, **low power consumption** is crucial — especially in battery-powered and embedded systems.

This project implements a **4-bit ALU** in **Verilog HDL** that integrates **clock gating** to reduce dynamic power consumption.  
The design was created, simulated, and analyzed using **Intel Quartus Prime** and **ModelSim**.

---

 Project Goal
The aim of this project is to:
1. Design a functional 4-bit ALU capable of performing common arithmetic and logic operations.
2. Integrate **clock gating** to disable unused parts of the circuit when not in operation, reducing switching activity.
3. Verify functionality and measure the effect of clock gating on power usage.

---

 How It Works
The ALU accepts:
- **Two 4-bit inputs**: `A` and `B`
- **Control signal (Opcode)**: Selects which operation to perform
- **Clock & Enable signals**: Used for power optimization

When the **Enable** signal is LOW, the clock to the ALU is gated (disabled), preventing unnecessary toggling in registers and logic circuits — this directly reduces **dynamic power consumption**.

---

Supported Operations
| Opcode | Operation             |
|--------|-----------------------|
| 000    | Addition (`A + B`)    |
| 001    | Subtraction (`A - B`) |
| 010    | Bitwise AND           |
| 011    | Bitwise OR            |
| 100    | Bitwise XOR           |
| 101    | Logical Shift Left    |
| 110    | Logical Shift Right   |
| 111    | Pass-Through (`A`)    |

---
 Low Power Concept: Clock Gating
Dynamic power in digital circuits is given by:

**P = α × C × V² × f**

Where:
- `α` = Switching activity
- `C` = Capacitance
- `V` = Supply voltage
- `f` = Clock frequency

By **gating the clock** when the ALU is idle:
- Switching activity (`α`) is reduced
- Registers and combinational logic stop toggling
- Overall dynamic power decreases

---

Design and Verification Steps
1. **RTL Design**:  
   - Wrote the ALU in Verilog with a separate clock gating module.
2. **Testbench Creation**:  
   - Created a self-checking testbench in Verilog.
3. **Simulation**:  
   - Verified correct outputs for all operations using ModelSim.
4. **Synthesis & Implementation**:  
   - Synthesized the design in Quartus Prime.
5. **Power Analysis**:  
   - Used Quartus PowerPlay Analyzer to measure power **with and without** clock gating.

---

 Results
- The ALU functioned correctly for all test cases.
- Clock gating reduced dynamic power consumption (measured via Quartus Power Analyzer).
- Significant power savings observed when the ALU was idle for extended periods.

---


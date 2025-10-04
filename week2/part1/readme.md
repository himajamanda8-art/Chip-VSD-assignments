#  Week 2 – BabySoC Fundamentals & Functional Modelling

![SoC](https://img.shields.io/badge/Topic-SoC%20Fundamentals-blue?style=for-the-badge)
![BabySoC](https://img.shields.io/badge/Learning-BabySoC-green?style=for-the-badge)
![Simulation](https://img.shields.io/badge/Tools-Icarus%20Verilog%20%7C%20GTKWave-orange?style=for-the-badge)

---

##  What is a System-on-Chip (SoC)?
A **System-on-Chip (SoC)** is an integrated circuit (IC) that contains all the essential components of a computer system packed into a single chip.  
It combines CPU, memory, peripherals, and interconnect into one **compact, fast, and power-efficient system**.

**Key benefits:**
- Reduced chip size  
- Lower power consumption  
- Faster communication between components  
- Cost-effective compared to multi-chip systems  

---

##  Components of a Typical SoC
1. ** CPU (Processor)**  
   - Executes instructions and controls the system.  
   - Examples: ARM Cortex, RISC-V core.  
   - Can be simple (BabySoC) or complex (multi-core SoCs).  

2. ** Memory**  
   - **ROM / Flash** → Stores program permanently.  
   - **RAM** → Temporary storage for CPU operations.  
   - Memory hierarchy is important in real SoCs for speed optimization.  

3. ** Peripherals**  
   - Allow the SoC to interact with the outside world.  
   - Examples: UART, SPI, I2C, GPIO, timers, ADC/DAC.  
   - Peripheral blocks are often modular and can be added or removed as needed.  

4. ** Interconnect / Bus**  
   - The “highway” connecting CPU, memory, and peripherals.  
   - Types: Shared bus, crossbar, network-on-chip.  
   - Ensures data moves correctly and efficiently between blocks.  

5. ** Clock & Reset**  
   - Clock synchronizes all operations in the chip.  
   - Reset initializes the system into a known state.  

6. ** Power Domains**  
   - Different parts of the SoC can have separate power supplies for efficiency.  
   - Allows selective powering down of unused blocks.  

---

##  Why BabySoC?
- A **simplified SoC model** for beginners.  
- Includes only the **basic blocks** (CPU + memory + few peripherals).  
- Helps students **understand interaction and communication** between components.  
- Ideal for practicing **functional modelling** before dealing with full-scale SoCs.  

---

##  Functional Modelling
Functional modelling is **the first step in SoC design**:

- Write **behavioral models** of CPU, memory, and peripherals in Verilog.  
- Simulate the system using **Icarus Verilog (iverilog)**.  
- View signal waveforms in **GTKWave**.  

**Purpose:**  
- Verify correct communication and logic of the BabySoC.  
- Detect errors early and reduce risks before RTL and physical design.  

---

##  Importance of Functional Modelling
✔️ Detects errors early  
✔️ Saves time and cost  
✔️ Ensures proper communication between CPU, memory, and peripherals  
✔️ Builds foundation for **RTL design → synthesis → physical implementation** 

---

##  Basic SoC Design Principles (from Week-2 notes)
1. **Hierarchy:** SoC is divided into modules (CPU, memory, peripherals).  
2. **Modularity:** Each module can be designed, tested, and reused independently.  
3. **Communication:** All modules must follow a defined protocol (bus/interconnect).  
4. **Timing & Synchronization:** All blocks work under a common clock; reset ensures initialization.  
5. **Scalability:** A simple SoC (like BabySoC) can later be scaled to more complex designs.  

---

##  Additional Week-2 Basics

1. **SoC Design Flow (High-Level)**  
   Functional Modelling → RTL Design → Simulation → Synthesis → Physical Design → Tapeout  

2. **Design Abstraction Levels**  
   - Behavioral / Functional → Focus on what the system does.  
   - RTL (Register Transfer Level) → Hardware structure using registers and logic.  
   - Gate-Level / Physical → Fabrication-ready stage.  

3. **Peripherals & Interfaces**  
   - UART → Serial communication  
   - SPI/I2C → Sensors or memory  
   - GPIO → Buttons, LEDs  

4. **Clocking and Reset Strategy**  
   - Clock synchronizes all modules.  
   - Reset initializes modules to a known state.  

5. **Dataflow Concept**  
   - Visualizes how information moves between CPU, memory, and peripherals.  

6. **Simulation & Verification Basics**  
   - Simulation → Check if BabySoC behaves as intended.  
   - Verification → Compare actual behavior vs expected.  

7. **Design Trade-Offs**  
   - Area vs Power vs Performance (PPA)  
   - Even simple SoCs introduce these trade-offs.  

---

##  BabySoC Block Diagram

```mermaid
graph TD;
    CPU[ CPU] -->|Bus| MEM[ Memory];
    CPU[ CPU] -->|Bus| PERI[ Peripherals];
    MEM -->|Interconnect| PERI;

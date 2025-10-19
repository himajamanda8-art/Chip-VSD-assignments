#  Week 4 – Day 3: CMOS Switching Threshold & Dynamic Simulations – Ngspice + sky130

![CMOS](https://img.shields.io/badge/CMOS-Circuit%20Design-blue?style=for-the-badge)
![Day 3](https://img.shields.io/badge/Day-3-orange?style=for-the-badge)
![EDA](https://img.shields.io/badge/EDA-Ngspice%20Sky130-brightgreen?style=for-the-badge)

---

##  Objective
- Create SPICE deck for **CMOS inverter**  
- Simulate **VTC** and extract **switching threshold (Vm)**  
- Perform **dynamic simulations** to observe rise/fall behavior  
- Study effect of **PMOS/NMOS sizing** on Vm  
- Connect simulations to **STA concepts** and timing analysis  

---

##  Lectures / Tasks with Briefs
| Lecture | Topic | Brief Description |
|---------|------|-----------------|
| 30-L1 | SPICE deck creation for CMOS inverter | Writing SPICE netlist for CMOS inverter simulation. |
| 31-L2 | SPICE simulation for CMOS inverter | Running simulation and observing inverter output. |
| 32-L3 | Labs Sky130 SPICE simulation for CMOS | Hands-on lab: plot VTC and verify switching behavior. |
| 33-L1 | Switching Threshold Vm | Extract Vm where Vin = Vout. |
| 34-L2 | Analytical expression of Vm as function of (W/L)p & (W/L)n | Derive Vm in terms of PMOS/NMOS sizing ratio. |
| 35-L3 | Analytical expression of (W/L)p & (W/L)n as function of Vm | Reverse calculation of transistor sizing from desired Vm. |
| 36-L4 | Static & dynamic simulation of CMOS inverter | Observe rise/fall propagation delays (tPLH, tPHL). |
| 37-L5 | Simulation with increased PMOS width | Study effect of PMOS sizing on Vm and delay. |
| 38-L6 | Applications in clock network & STA | Discuss how CMOS inverter timing affects critical paths. |

---

##  SPICE Netlist Examples

### CMOS Inverter – VTC & Switching Threshold
* CMOS inverter netlist
.include sky130_fd_pr__nfet_01v8.lib
.include sky130_fd_pr__pfet_01v8.lib
M1 out in vdd vdd sky130_fd_pr__pfet_01v8 W=2u L=0.15u
M2 out in 0 0 sky130_fd_pr__nfet_01v8 W=1u L=0.15u
Vdd vdd 0 1.8
.dc Vin 0 1.8 0.01
.print dc v(out)
.end

### Transient Simulation – Rise/Fall Delays
* CMOS inverter transient response
Vinp in 0 PULSE(0 1.8 0 0.1n 0.1n 2n 4n)
.tran 0.1n 10n
.plot tran v(in) v(out)
.end

---

##  Plots / Figures
- VTC curve with **switching threshold (Vm)** annotated  
- Transient waveform showing **tPLH and tPHL**  
- Effect of increased PMOS width on Vm and rise/fall times  

---

##  Observations & Analysis
- Switching threshold Vm shifts with **PMOS/NMOS sizing**  
- Rise delay (tPLH) is higher than fall delay (tPHL) due to PMOS mobility  
- VTC shape confirms **balanced inverter operation**  
- SPICE dynamic simulations provide **realistic delay information** for STA  

---

##  Conclusion
- Vm and propagation delays are directly influenced by transistor sizing  
- Dynamic simulation validates CMOS inverter behavior for STA timing  
- Understanding these simulations helps predict **critical path delays**  

---

##  Useful Links
- [sky130CircuitDesignWorkshop GitHub](https://github.com/kunalg123/sky130CircuitDesignWorkshop/)  
- [VSDIAT Platform](https://vsdiat.org/)

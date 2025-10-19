#  Week 4 – Day 1: NMOS Basics (Id vs Vds) – Ngspice + sky130

![CMOS](https://img.shields.io/badge/CMOS-Circuit%20Design-blue?style=for-the-badge)
![Day 1](https://img.shields.io/badge/Day-1-orange?style=for-the-badge)
![EDA](https://img.shields.io/badge/EDA-Ngspice%20Sky130-brightgreen?style=for-the-badge)

---

##  Objective
- Understand NMOS transistor operation in **linear (resistive) and saturation regions**  
- Learn SPICE simulation setup and syntax  
- Plot **Id vs Vds curves** for various Vgs  
- Introduce **threshold voltage** and strong inversion  

---

##  Lectures / Tasks with Briefs
| Lecture | Topic | Brief Description |
|---------|------|-----------------|
| 3-L1 | Why do we need SPICE simulations? | Importance of SPICE to simulate real transistor behavior and validate circuits. |
| 4-L2 | Introduction to basic element in Circuit design – NMOS | Introduces NMOS transistor, terminals, and basic operation. |
| 5-L3 | Strong inversion and threshold voltage | Discusses strong inversion and threshold voltage (Vt). |
| 6-L4 | Threshold voltage with positive substrate potential | How Vt changes with substrate bias (body effect). |
| 7-L1 | Resistive region with small drain-source voltage | Linear/ohmic region of NMOS for small Vds. |
| 8-L2 | Drift current theory | Drift current model governing carrier flow. |
| 9-L3 | Drain current model – linear region | Id formula derivation for linear region. |
| 10-L4 | SPICE conclusion – resistive operation | Validate linear region Id behavior with SPICE. |
| 11-L5 | Pinch-off region condition | Vds condition where channel pinches off and enters saturation. |
| 12-L6 | Drain current model – saturation region | Id formula for saturation region; short-channel effects. |
| 13-L1 | Basic SPICE setup | Ngspice environment, libraries, and tools setup. |
| 14-L2 | Circuit description in SPICE syntax | Writing SPICE netlist for NMOS circuits. |
| 15-L3 | Define technology parameters | Device parameters like W/L, Vt, mobility. |
| 16-L4 | First SPICE simulation | Run Id vs Vds simulation. |
| 17-L5 | SPICE Lab with sky130 models | Hands-on lab; plot Id–Vds curves. |

---

##  SPICE Netlist Example
* NMOS Id vs Vds characteristic
.include sky130_fd_pr__nfet_01v8.lib
M1 drain gate source 0 sky130_fd_pr__nfet_01v8 W=1u L=0.15u
Vgs gate 0 0.8
Vds drain source 0
.dc Vds 0 1.8 0.05
.plot dc i(Vds)
.end

---

##  Plots / Figures
- Annotate linear and saturation regions  
- Mark threshold voltage (Vt) on plots  

---

##  Observations & Analysis
- Linear region: Id increases linearly with Vds  
- Saturation region: Id flattens as Vds increases (channel pinch-off)  
- Threshold voltage visible from onset of strong inversion  
- SPICE simulations match theoretical predictions  

---

##  Conclusion
- NMOS operation clearly divided into linear and saturation regions  
- SPICE provides a practical way to visualize transistor physics  
- Understanding Id–Vds lays foundation for VTC and CMOS inverter analysis  

---

##  Useful Links
- [sky130CircuitDesignWorkshop GitHub](https://github.com/kunalg123/sky130CircuitDesignWorkshop/)  
- [VSDIAT Platform](https://vsdiat.org/)

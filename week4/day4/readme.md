#  Week 4 – Day 4: CMOS Noise Margin Robustness – Ngspice + sky130

![CMOS](https://img.shields.io/badge/CMOS-Circuit%20Design-blue?style=for-the-badge)
![Day 4](https://img.shields.io/badge/Day-4-orange?style=for-the-badge)
![EDA](https://img.shields.io/badge/EDA-Ngspice%20Sky130-brightgreen?style=for-the-badge)

---

##  Objective
- Analyze **noise margins (NML, NMH)** of CMOS inverters  
- Understand how **PMOS/NMOS sizing** affects robustness  
- Plot **VTC** with annotated logic voltage levels (VIL, VIH, VOL, VOH)  
- Study inverter behavior under **process and design variations**  

---

##  Lectures / Tasks with Briefs
| Lecture | Topic | Brief Description |
|---------|------|-----------------|
| 39-L1 | Introduction to noise margin | Importance of noise margin for robust digital design. |
| 40-L2 | Noise margin voltage parameters | Define VOL, VOH, VIL, VIH from VTC. |
| 41-L3 | Noise margin equation & summary | Compute NML = VIL − VOL, NMH = VOH − VIH. |
| 42-L4 | Noise margin variation w.r.t PMOS width | Observe how increasing PMOS W/L affects Vm and NML/NMH. |
| 43-L5 | Sky130 Noise margin labs | Hands-on lab: simulate and annotate noise margins. |

---

##  SPICE Netlist Example

### CMOS Inverter VTC for Noise Margin
* Include both NMOS and PMOS
.include sky130_fd_pr__nfet_01v8.lib
.include sky130_fd_pr__pfet_01v8.lib
M1 out in vdd vdd sky130_fd_pr__pfet_01v8 W=2u L=0.15u
M2 out in 0 0 sky130_fd_pr__nfet_01v8 W=1u L=0.15u
Vdd vdd 0 1.8
.dc Vin 0 1.8 0.01
.print dc v(out)
.end

---

##  Plots / Figures
- Annotated VTC showing **VIL, VIH, VOL, VOH**  
- Highlight **NML and NMH**  
- Compare curves for different **PMOS W/L ratios**  

---

##  Observations & Analysis
- Noise margins increase with **larger PMOS width**  
- VTC midpoint shifts slightly as W/L ratio changes  
- Balanced sizing gives optimal **robustness**  
- Observed behavior aligns with SPICE simulation predictions  

---

##  Conclusion
- CMOS inverter noise margins are strongly affected by transistor sizing  
- Accurate VTC plotting is essential for **robust logic design**  
- Simulations provide insight into **design trade-offs** for STA timing margins  

---


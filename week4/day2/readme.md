#  Week 4 – Day 2: Velocity Saturation & CMOS Inverter VTC – Ngspice + sky130

![CMOS](https://img.shields.io/badge/CMOS-Circuit%20Design-blue?style=for-the-badge)
![Day 2](https://img.shields.io/badge/Day-2-orange?style=for-the-badge)
![EDA](https://img.shields.io/badge/EDA-Ngspice%20Sky130-brightgreen?style=for-the-badge)

---

##  Objective
- Understand **velocity saturation effects** in short-channel NMOS devices  
- Simulate **Id vs Vgs** for long and short channel devices  
- Build a CMOS inverter and obtain **Voltage Transfer Characteristic (VTC)**  
- Identify **switching threshold (Vm)** from VTC  
- Connect SPICE simulations to CMOS inverter operation and STA timing  

---

##  Lectures / Tasks with Briefs
| Lecture | Topic | Brief Description |
|---------|------|-----------------|
| 18-L1 | SPICE simulation for lower nodes | Simulation setup for low voltage NMOS devices. |
| 19-L2 | Drain current vs gate voltage for long & short channel | Observe Id-Vgs curves; note short-channel effects. |
| 20-L3 | Velocity saturation at lower & higher electric fields | How carrier velocity saturates under high fields. |
| 21-L4 | Velocity saturation drain current model | Id expression considering velocity saturation. |
| 22-L5 | Labs Sky130 Id–Vgs | Hands-on simulation for Id–Vgs extraction. |
| 23-L6 | Labs Sky130 Vt | Extract threshold voltage from Id–Vgs curves. |
| 24-L1 | MOSFET as a switch | Conceptual explanation of MOSFET switching behavior. |
| 25-L2 | Standard MOS voltage-current parameters | PMOS/NMOS I-V parameters for modeling. |
| 26-L3 | PMOS/NMOS drain current vs drain voltage | Plotting Id vs Vds for both PMOS and NMOS. |
| 27-L4 | Step 1 – Convert PMOS gate-source voltage to Vin | Map PMOS voltage to inverter input. |
| 28-L5 | Step 2 & 3 – Convert PMOS/NMOS drain-source voltage to Vout | Map transistor outputs to inverter output. |
| 29-L6 | Step 4 – Merge PMOS & NMOS load curves and plot VTC | Final VTC plot for CMOS inverter; identify switching threshold. |

---

##  SPICE Netlist Examples

### Id vs Vgs (Velocity Saturation)
* NMOS Id vs Vgs characteristic
.include sky130_fd_pr__nfet_01v8.lib
M1 drain gate source 0 sky130_fd_pr__nfet_01v8 W=1u L=0.15u
Vds drain source 1.8
Vgs gate 0 0
.dc Vgs 0 1.8 0.05
.plot dc i(Vds)
.end

### CMOS Inverter VTC
* CMOS Inverter VTC
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
- Id vs Vgs curves for long and short channel NMOS  
- Annotate onset of velocity saturation  
- VTC plot with switching threshold (Vm) marked  

---

##  Observations & Analysis
- Short-channel devices show **velocity saturation**, deviating from ideal square-law  
- VTC is **sharper near Vm** for balanced PMOS/NMOS sizing  
- Switching threshold (Vm) depends on W/L ratio of PMOS and NMOS  
- SPICE simulation matches theoretical predictions for CMOS inverter operation  

---

##  Conclusion
- Velocity saturation significantly impacts Id–Vgs in short-channel devices  
- CMOS inverter VTC demonstrates the effect of transistor sizing on switching point  
- Understanding VTC and Vm is critical for delay and STA analysis  

---

##  Useful Links
- [sky130CircuitDesignWorkshop GitHub](https://github.com/kunalg123/sky130CircuitDesignWorkshop/)  
- [VSDIAT Platform](https://vsdiat.org/)

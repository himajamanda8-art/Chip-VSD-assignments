#  Week 4 – CMOS Circuit Design (Ngspice + sky130)

![CMOS](https://img.shields.io/badge/CMOS-Circuit%20Design-blue?style=for-the-badge)
![EDA](https://img.shields.io/badge/EDA-Ngspice%20Sky130-brightgreen?style=for-the-badge)
![Week](https://img.shields.io/badge/Week-4-orange?style=for-the-badge)

---

##  Objective
Perform transistor-level CMOS simulations using Ngspice with sky130 PDKs to understand:

- NMOS Id–Vds and Id–Vgs behavior  
- CMOS inverter voltage transfer characteristics (VTC)  
- Switching thresholds, rise/fall delays, noise margins  
- Power-supply and device variation effects on robustness  
- Connection between transistor physics and STA concepts

---

##  Why This Task Matters
This task strengthens intuition about how **real device physics** drives digital circuit timing:

- SPICE simulations reveal the "real" Id–Vds and VTC behavior that STA approximates  
- Observe effects of **sizing, supply variation, and short-channel phenomena**  
- Understand **noise margins and robustness** of CMOS inverters  
- Connect device-level behavior to **STA delay models and PVT variations**

**Workshop Collateral:** [sky130CircuitDesignWorkshop GitHub](https://github.com/kunalg123/sky130CircuitDesignWorkshop/)  
**Platform:** VSDIAT

---

##  Week 4 Task Breakdown (5 Days)

### Day 1 – NMOS Basics: Id vs Vds
| Lecture | Topic |
|---------|------|
| 3-L1 | Why do we need SPICE simulations? |
| 4-L2 | Introduction to basic element in Circuit design – NMOS |
| 5-L3 | Strong inversion and threshold voltage |
| 6-L4 | Threshold voltage with positive substrate potential |
| 7-L1 | Resistive region with small drain-source voltage |
| 8-L2 | Drift current theory |
| 9-L3 | Drain current model – linear region |
| 10-L4 | SPICE conclusion – resistive operation |
| 11-L5 | Pinch-off region condition |
| 12-L6 | Drain current model – saturation region |
| 13-L1 | Basic SPICE setup |
| 14-L2 | Circuit description in SPICE syntax |
| 15-L3 | Define technology parameters |
| 16-L4 | First SPICE simulation |
| 17-L5 | SPICE Lab with sky130 models |

---

### Day 2 – Velocity Saturation & CMOS Inverter VTC
| Lecture | Topic |
|---------|------|
| 18-L1 | SPICE simulation for lower nodes |
| 19-L2 | Drain current vs gate voltage for long & short channel |
| 20-L3 | Velocity saturation at lower & higher electric fields |
| 21-L4 | Velocity saturation drain current model |
| 22-L5 | Labs Sky130 Id–Vgs |
| 23-L6 | Labs Sky130 Vt |
| 24-L1 | MOSFET as a switch |
| 25-L2 | Standard MOS voltage-current parameters |
| 26-L3 | PMOS/NMOS drain current vs drain voltage |
| 27-L4 | Step 1 – Convert PMOS gate-source voltage to Vin |
| 28-L5 | Step 2 & 3 – Convert PMOS/NMOS drain-source voltage to Vout |
| 29-L6 | Step 4 – Merge PMOS & NMOS load curves and plot VTC |

---

### Day 3 – CMOS Switching Threshold & Dynamic Simulations
| Lecture | Topic |
|---------|------|
| 30-L1 | SPICE deck creation for CMOS inverter |
| 31-L2 | SPICE simulation for CMOS inverter |
| 32-L3 | Labs Sky130 SPICE simulation for CMOS |
| 33-L1 | Switching Threshold Vm |
| 34-L2 | Analytical expression of Vm as function of (W/L)p & (W/L)n |
| 35-L3 | Analytical expression of (W/L)p & (W/L)n as function of Vm |
| 36-L4 | Static & dynamic simulation of CMOS inverter |
| 37-L5 | Simulation with increased PMOS width |
| 38-L6 | Applications in clock network & STA |

---

### Day 4 – CMOS Noise Margin Robustness
| Lecture | Topic |
|---------|------|
| 39-L1 | Introduction to noise margin |
| 40-L2 | Noise margin voltage parameters |
| 41-L3 | Noise margin equation & summary |
| 42-L4 | Noise margin variation w.r.t PMOS width |
| 43-L5 | Sky130 Noise margin labs |

---

### Day 5 – Power-Supply & Device Variation Robustness
| Lecture | Topic |
|---------|------|
| 44-L1 | SPICE simulation for power supply variations |
| 45-L2 | Advantages/disadvantages using low supply voltage |
| 46-L3 | Sky130 Supply Variation Labs |
| 47-L1 | Sources of variation – Etching process |
| 48-L2 | Sources of variation – Oxide thickness |
| 49-L3 | SPICE simulation for device variations |
| 50-L4 | Conclusion |
| 51-L5 | Sky130 Device Variation Labs |

---

##  Deliverables
Your Week 4 submission should include:

- **Introduction / Background**: Purpose of each experiment (Id vs Vds, VTC, transient, variation)  
- **SPICE Netlists**: Full SPICE code for all experiments  
- **Plots / Figures**: Id vs Vds, Id vs Vgs, VTC, transient waveforms, variations  
- **Tabulated Results**:

| Parameter | Value | Observation |
|-----------|-------|-------------|
| NMOS Vt | ... V | From Id–Vgs sweep |
| Vm | ... V | CMOS inverter switching threshold |
| Rise delay (tPLH) | ... ns | From transient waveform |
| Fall delay (tPHL) | ... ns | From transient waveform |
| NML | ... V | Noise margin low |
| NMH | ... V | Noise margin high |
| Variation Effects | ... | Effect of W/L or Vdd changes |

- **Observations / Analysis**: What you see, why it happens, STA connection  
- **Conclusions**: Transistor-level constraints on timing, noise margin & variation effects  
- **References**: sky130 PDK models, literature, workshop materials

---

##  Useful Links
- [sky130CircuitDesignWorkshop GitHub](https://github.com/kunalg123/sky130CircuitDesignWorkshop/)  
- [VSDIAT Platform](https://vsdiat.org/)

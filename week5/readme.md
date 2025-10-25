#  Week 5 — OpenROAD Flow Setup & Physical Design (Floorplan + Placement)

![VLSI](https://img.shields.io/badge/VLSI-Physical%20Design-blue?style=for-the-badge&logo=openroad)
![Tools](https://img.shields.io/badge/OpenROAD-Flow%20Scripts-green?style=for-the-badge&logo=linux)
![Progress](https://img.shields.io/badge/Progress-Week%205-success?style=for-the-badge)

---

##  Introduction

Welcome to **Week 5** of my **RISC-V SoC Physical Design Journey**!  
This week’s focus was on setting up **OpenROAD Flow Scripts** and executing the **Floorplan** and **Placement** stages — the initial steps of the **backend physical design flow**.

> *“This week marks the moment when the design leaves the abstract world of logic and begins to take physical shape on silicon.”*

---

##  Objective

To install, configure, and execute the **OpenROAD Flow Scripts** environment up to the **Floorplan** and **Placement** stages, analyzing how physical constraints influence area, timing, and cell arrangement.

---

##  Tools & Environment Setup

| Tool | Purpose | Status |
|------|----------|--------|
|  **OpenROAD Flow Scripts** | Automated RTL-to-GDSII backend design flow | ✅ Installed |
|  **Ubuntu 22.04 LTS** | Host environment for open-source EDA tools | ✅ Configured |
|  **TCL & Make** | Flow orchestration and scripting | ✅ Verified |
|  **Git** | Version control and repository management | ✅ Functional |

---

##  Reference Repository

Used as the base for installation and flow guidance:  
👉 [OpenROAD Reference – spatha_vsd-hdp/Day14](https://github.com/spatha0011/spatha_vsd-hdp/blob/main/Day14/README.md)

---

##  Step 1 — Installing OpenROAD Flow Scripts

<pre>
# Clone the OpenROAD repository
git clone https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts.git

# Enter the flow directory
cd OpenROAD-flow-scripts

# Run setup to install prerequisites
sudo ./setup.sh

# Build the flow
make
</pre>

 **Verification:**
<pre>
./flow.tcl -design &lt;your_design_name&gt;
</pre>

A successful launch without errors confirms proper environment setup.

---

##  Step 2 — Executing Floorplan & Placement

The **physical design** process begins once the synthesized netlist is ready.  
We execute **only two stages** this week: *Floorplanning* and *Placement*.

###  Floorplan Stage
- Defines **core area** and **die boundaries**.  
- Determines **aspect ratio**, **utilization factor**, and **power grid layout**.  
- Allocates space for macros, IO pins, and blockages.  

 *Common Parameters in flow.tcl*:
set ::env(DESIGN_NAME) "picorv32a"
set ::env(FP_ASPECT_RATIO) 1.0
set ::env(FP_CORE_UTIL) 50
set ::env(FP_IO_MODE) 1

yaml
Copy code

###  Placement Stage
- Arranges **standard cells** within the defined core region.  
- Optimizes for **timing**, **congestion**, and **power distribution**.  
- Generates DEF files and reports for cell density and placement quality.

 *Example Command*
<pre>
./flow.tcl -design picorv32a -to placement
</pre>

---

## ✅ Verification Checklist

| Task | Description | Status |
|------|-------------|--------|
| Floorplan | Core and die area generated successfully | ✅ Done |
| Placement | Standard cells placed with minimal overlap | ✅ Done |
| DEF Files | Created in results directory | ✅ Verified |
| Logs | Generated for both stages | ✅ Captured |
| Visuals | Layout screenshots taken | ✅ Attached |

---

##  Output Directory Structure

<pre>
Week5_OpenROAD/
├── screenshots/
│   ├── openroad_installation.png
│   ├── floorplan_result.png
│   └── placement_result.png
├── logs/
│   ├── floorplan.log
│   └── placement.log
├── results/
│   ├── floorplan.def
│   └── placement.def
└── README.md
</pre>

---

##  Output Snapshots

| Stage | Screenshot |
|--------|-------------|
| Floorplan | ![Floorplan](./screenshots/floorplan_result.png) |
| Placement | ![Placement](./screenshots/placement_result.png) |
| Terminal Proof | ![Terminal](./screenshots/openroad_installation.png) |

---

##  Observations & Analysis

| Parameter | Description | Observation |
|------------|-------------|-------------|
| **Core Utilization** | Ratio of active cell area to total core area | ~50 % (default) |
| **Aspect Ratio** | Height : Width of core region | 1.0 (Square layout) |
| **Standard Cell Density** | Number of cells per µm² | Moderate |
| **Congestion Report** | Identified after placement | No major hotspots |
| **DEF File Check** | Verified in results folder | ✅ Generated |

> Placement logs showed smooth cell spreading and congestion values within threshold, indicating a balanced floorplan suitable for next-stage CTS.

---

##  Technical Insight

- **Floorplanning** defines the blueprint for your silicon — once fixed, it directly impacts timing closure.  
- **Placement** ensures that signal paths remain short, minimizing **delay** and **power loss**.  
- The **OpenROAD placer** uses a *global + detailed placement* algorithm to iteratively reduce wirelength.  
- The **DEF (Design Exchange Format)** files created will be used by **CTS**, **Routing**, and **DRC/LVS** steps in later weeks.  
- Physical design quality can be evaluated by metrics like **HPWL (Half-Perimeter Wire Length)** and **cell density maps**.

---

##  Summary

> Successfully installed and executed the OpenROAD Flow Scripts.  
> Generated and analyzed floorplan + placement results for the target design.  
> Encountered dependency errors (libboost, tclsh) — resolved via apt install.  
> Verified logs, DEF outputs, and visual layouts confirming correct execution.  
> This experiment helped me understand how front-end design transitions into physical reality.

---

##  Key Learnings

- Understood how **floorplan parameters** (utilization, aspect ratio) influence design quality.  
- Learned how **placement algorithms** distribute cells efficiently across the die.  
- Gained hands-on experience with **OpenROAD directory structure** (`logs/`, `results/`, `screenshots/`).  
- Observed how **core area**, **timing**, and **power** are interconnected.  
- Built a functional physical design setup ready for Clock Tree Synthesis (CTS).  

---

##  Next Week Preview — CTS & Routing

| Stage | Objective |
|--------|-----------|
|  **CTS (Clock Tree Synthesis)** | Build balanced clock distribution network |
|  **Routing** | Connect placed cells with optimized interconnects |
|  **Sign-off Checks** | Verify DRC/LVS clean GDSII generation |

---

##  Beyond Week 5 — Concept Bridge

The Floorplan and Placement phases form the **foundation for timing-driven design**.  
Here’s how this stage connects to the complete flow:

 **Synthesis Output (Netlist)** →  **Floorplan + Placement (Week 5)** → 🕒 **CTS (Week 6)** → 🛣️ **Routing (Week 7)** → 🎯 **GDSII Sign-off (Week 8)**

Each stage carries forward constraints like:
- **Timing requirements**
- **Power distribution**
- **Congestion maps**
- **Cell density targets**

These parameters determine **whether your SoC will meet performance and manufacturability goals**.

---

##  Additional Notes

- OpenROAD integrates multiple internal tools like `RePlAce`, `TritonFP`, and `TritonRoute`.  
- The *Floorplan DEF* can be visualized using **Magic VLSI** or **KLayout** for a better physical view.  
- Recommended log review: `floorplan.log` and `placement.log` — look for keywords like `core area`, `placed instances`, and `wirelength`.  
- Ensure your `config.mk` is updated with your design name and correct PDK path (sky130A).

---

 **Contributor:** [himajabuilds](https://github.com/himajamanda8-art/Chip-VSD-assignments.git)

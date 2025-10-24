
---
# Non-Isolated Buck Converter (24V → 10V) - Simulink R2025b

## Overview
This repository contains a **Simulink model** of a **non-isolated asynchronous buck converter** that steps down **24V DC input to 10V DC output**.  
Built entirely using **Simscape Electrical** blocks in **MATLAB R2025b**, without requiring Specialized Power Systems.

**Applications:**
- Power electronics education
- DC-DC converter design and simulation
- CCM mode analysis and PWM switching behavior
- Research and academic projects

---

## Model Specifications

| Parameter | Value |
|-----------|-------|
| Input Voltage (Vin) | 24 V |
| Output Voltage (Vout) | 10 V |
| Load Current | 2 A |
| Load Resistance (R) | 5 Ω |
| Switching Frequency (fs) | 200 kHz |
| Inductor (L) | 47 µH, ≥ 3 A |
| Output Capacitor (C) | 4.7 µF, ≥ 16 V |
| Inductor Ripple (ΔIL) | 0.6 A |
| Output Ripple (ΔVout) | 0.1 V |
| Duty Cycle (D) | 0.417 |

---

## Buck Converter Topology



```
   +24V
     +
     |
   MOSFET
     |---------> L -----------+------> Vout 10V
     |                        |
    Diode                     C
     |                        |
     --------------------------
               GND
```



---

## Parameter Calculations (Design Equations)

### 1. Duty Cycle
\[
D = \frac{V_{out}}{V_{in}} = \frac{10}{24} = 0.417
\]

### 2. Inductor Value
Ripple current:
\[
\Delta I_L = 0.3 \cdot I_{out} = 0.6\text{ A}
\]
\[
L = \frac{(V_{in} - V_{out}) \cdot D}{f_s \cdot \Delta I_L}
= \frac{(24 - 10) \cdot 0.417}{200000 \cdot 0.6}
= 47\,\mu H
\]

### 3. Capacitor Value
Output ripple:
\[
\Delta V_{out} = 0.01 \cdot V_{out} = 0.1\text{ V}
\]
\[
C = \frac{\Delta I_L}{8 \cdot f_s \cdot \Delta V_{out}}
= \frac{0.6}{8 \cdot 200000 \cdot 0.1}
= 4.7\,\mu F
\]

---

## Simulink Block Requirements

| Component | Source |
|-----------|--------|
| DC Voltage Source | Simscape > Electrical > Sources |
| MOSFET | Simscape > Electrical > Semiconductors |
| Diode | Simscape > Electrical > Semiconductors |
| Series R-L Branch | Simscape > Electrical > Elements |
| Capacitor | Simscape > Electrical > Elements |
| Resistor (Load) | Simscape > Electrical > Elements |
| PWM Generator | Simulink > Sources |
| Voltage Sensor | Simscape > Sensors |
| PS-Simulink Converter | Simscape > Utilities |
| Scope | Simulink > Sinks |
| Solver Configuration | Simscape |

---

## How to Run Simulation

1. Open the model in MATLAB **R2025b**.
2. Add **Solver Configuration** and **Electrical Reference** blocks.
3. Set simulation time to **0.01 sec**.
4. Use solver: **ode23tb** or **ode3** (recommended for switching circuits).
5. Run and observe **Vout** and **Inductor Current**.

---

## File Structure Example
```

📂 Buck-Converter-Simulink
├── BuckConverter.slx
├── README.md
└── images/
└── buck_diagram.png

```


---

## Author
**Animesh Kumar**  
📧 Email: un.animesh@gmail.com 

🔗 LinkedIn: https://www.linkedin.com/in/un-animesh

💻 GitHub: https://github.com/unanimesh 

---

If you like this project, please ⭐ the repository!



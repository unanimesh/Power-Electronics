
---

# 🔧 Non-Isolated Buck Converter (24V → 10V) – Simulink R2025b

## ✅ Overview
This repository contains a **Simulink model** of a **non-isolated asynchronous buck converter** that steps down **24V DC to 10V DC**.  
Built entirely using **Simscape Electrical** in **MATLAB R2025b**, without Specialized Power Systems.

**🔋 Applications**
- Power electronics education and simulation
- DC-DC converter design
- Continuous Conduction Mode (CCM) analysis
- PWM switching behavior study
- Academic and research projects

---

## ⚙️ Model Specifications

| Parameter | Value |
|-----------|--------|
| Input Voltage (Vin) | 24 V |
| Output Voltage (Vout) | 10 V |
| Load Current (Iout) | 2 A |
| Load Resistance (R) | 5 Ω |
| Switching Frequency (fs) | 200 kHz |
| Inductor (L) | 47 µH, ≥3 A |
| Output Capacitor (C) | 4.7 µF, ≥16 V |
| Inductor Ripple (ΔIL) | 0.6 A |
| Output Ripple (ΔVout) | 0.1 V |
| Duty Cycle (D) | 0.417 |

---

## 🔧 Buck Converter Topology

+24V + | MOSFET |---------> L -----------+------> Vout = 10V |                        | Diode                     C |                        | -------------------------- GND

---

## ✏️ Design Calculations

### ✅ 1. Duty Cycle
\[
D = \frac{V_{out}}{V_{in}} = \frac{10}{24} = 0.417
\]

---

### ✅ 2. Inductor Value
\[
\Delta I_L = 0.3 \cdot I_{out} = 0.3 \cdot 2 = 0.6\,A
\]
\[
L = \frac{(V_{in} - V_{out}) \cdot D}{f_s \cdot \Delta I_L}
= \frac{(24 - 10) \cdot 0.417}{200000 \cdot 0.6}
= 47\,\mu H
\]

---

### ✅ 3. Output Capacitor
\[
\Delta V_{out} = 0.01 \cdot V_{out} = 0.01 \cdot 10 = 0.1\,V
\]
\[
C = \frac{\Delta I_L}{8 \cdot f_s \cdot \Delta V_{out}}
= \frac{0.6}{8 \cdot 200000 \cdot 0.1}
= 4.7\,\mu F
\]

---

## 🧩 Simulink Block Requirements

| Component | Block Location |
|-----------|----------------|
| DC Voltage Source | Simscape → Electrical → Sources |
| MOSFET | Simscape → Electrical → Semiconductors |
| Diode | Simscape → Electrical → Semiconductors |
| Series R-L Branch | Simscape → Electrical → Elements |
| Capacitor | Simscape → Electrical → Elements |
| Resistor (Load) | Simscape → Electrical → Elements |
| PWM Generator | Simulink → Sources |
| Voltage Sensor | Simscape → Sensors |
| PS-Simulink Converter | Simscape → Utilities |
| Scope | Simulink → Sinks |
| Solver Configuration | Simscape |
| Electrical Reference | Simscape |

---

## ▶️ How to Run Simulation

1. Open `BuckConverter.slx` in **MATLAB R2025b**.
2. Connect **Electrical Reference** and **Solver Configuration**.
3. Set simulation stop time: `0.01 s`.
4. Use solver: **ode23tb** (recommended) or **ode3**.
5. Run simulation ✅
6. Observe:
   - Output voltage waveform (Vout)
   - Inductor current ripple (IL)

---

## 📂 File Structure

Buck-Converter-Simulink/ ├── BuckConverter.slx ├── README.md └── images/ └── buck_diagram.png

---

## ✍️ Author
**Animesh Kumar**  
📧 Email: un.animesh@gmail.com  
🔗 LinkedIn: https://www.linkedin.com/in/un-animesh  
💻 GitHub: https://github.com/unanimesh  

---

⭐ If you found this helpful, don't forget to **star this repository**!


---
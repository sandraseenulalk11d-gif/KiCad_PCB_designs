# 230V AC to 5V DC Transformerless Power Supply

A compact, non-isolated capacitive dropper AC-DC power supply designed to provide low-current DC rails for microcontrollers and embedded sensors directly from single-phase utility mains.

---

## Technical Specifications

| Parameter | Value |
| :--- | :--- |
| **Input Voltage** | 230V AC ±10%, 50 Hz |
| **Output Voltage** | 5V DC (clamped and filtered) |
| **Output Current** | 30 mA – 40 mA continuous |
| **Topology** | Series capacitive dropper with full-bridge rectification and Zener shunt regulator |
| **Cooling** | Passive convection |

---

## Circuit Working & Key Stages

* **Capacitive Dropping Stage:** Uses the AC reactance ($X_C = \frac{1}{2\pi f C}$) of a high-voltage film capacitor to drop the mains voltage without the resistive heat dissipation of standard dropper resistors.
* **Transient & Inrush Suppression:** A flameproof fusible wirewound resistor limits high inrush current spikes during mains switch-on, paired with a metal-oxide varistor (MOV) to clamp utility voltage transients.
* **Discharge Mechanism:** A high-value bleeder resistor connected across the AC dropper capacitor ensures rapid discharge of stored energy when disconnected from mains.
* **Rectification & Filtering:** A full-wave diode bridge converts AC to pulsating DC, followed by an electrolytic reservoir capacitor with low ESR to smooth voltage ripple.
* **Regulation:** A precision Zener diode clamps the output rail, maintaining stable DC regulation across changing load currents.

---

## High-Voltage Safety Guidelines

* **Galvanic Isolation Warning:** This design contains **no isolation transformer**. The output DC ground rail floats directly at AC mains line potential.
* **Operational Hazard:** Direct contact with any point on this board during operation poses a severe electric shock risk.
* **Testing Requirement:** Always use an **isolated AC source (isolation transformer)** and an insulated probe setup during bench debugging and oscilloscope measurements.
* **Enclosure:** This module must be housed in a non-conductive, sealed plastic enclosure (flame-retardant ABS or polycarbonate) with no exposed metal headers or test pins.

---

## Repository Contents

* `/Design_Files` — Complete KiCad schematic (`.kicad_sch`), PCB layout (`.kicad_pcb`), and project configuration.
* `/Gerbers` — Production-ready Gerber files (copper layers, solder mask, silkscreen, and drill files).
* `/BOM` — Bill of Materials detailing component footprints, tolerances, and dielectric ratings (specifically X2 safety ratings).
* `/Docs` — Schematic PDF prints, board dimensions, and 3D top/bottom visual renders.

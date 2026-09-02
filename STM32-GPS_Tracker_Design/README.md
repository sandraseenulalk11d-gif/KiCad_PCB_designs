# STM32-Based GPS & Cellular Asset Tracker

An embedded hardware tracking system featuring an STM32 ARM Cortex-M microcontroller interfaced with a SIMCom SIM808 module for real-time GNSS positioning and GPRS telemetry.

---

## Technical Specifications

| Parameter | Specification |
| :--- | :--- |
| **Microcontroller** | STM32 ARM Cortex-M (e.g., STM32F103C8T6 / STM32F4 series) |
| **Connectivity & GNSS** | SIM808 (Quad-band GSM/GPRS + High-sensitivity GPS/GLONASS) |
| **Power Input** | 5V DC via USB-C / External DC source (or Li-Ion battery with onboard charger) |
| **Antenna Interfaces** | Onboard U.FL / IPEX coaxial connectors for external active GPS and GSM antennas |
| **SIM Interface** | Standard Mini-SIM / Micro-SIM socket with ESD protection |
| **Communication Bus** | Hardware USART / UART for AT command communication and NMEA stream parsing |

---

## Circuit Architecture & Hardware Design

* **Microcontroller Processing Stage:** The STM32 manages cellular network registration, handles the power sequencing of the modem via dedicated `PWRKEY` and `RESET` control nets, and processes incoming NMEA GPS sentences.
* **Cellular & GNSS Subsystem:** Driven by the SIM808 transceiver module, utilizing dedicated RF paths and discrete U.FL coaxial terminations for remote antenna mounting.
* **SIM Card Protection:** The SIM interface lines (`VCC`, `RST`, `CLK`, `I/O`) integrate low-capacitance TVS diode arrays (`SMF05C` / `SOT-363`) to safeguard against electrostatic discharge during card insertion.
* **Power Regulation & Current Handling:** Uses dedicated low-dropout (LDO) or high-efficiency buck regulation (`LM5017` / `TPS5430`) with bulk capacitance to absorb the 2A transient current pulses typical of 2G burst transmissions.
* **Programming & Telemetry:** Dedicated SWD header pins (`SWDIO`, `SWCLK`) for flashing and real-time hardware debugging, alongside a secondary UART debug port.

---

## PCB Layout Considerations

* **RF Grounding & Trace Impedance:** RF tracks connecting the SIM808 RF pins to the U.FL connectors are designed as coplanar waveguides with ground stitching to maintain a target 50Ω characteristic impedance.
* **High-Current Power Routing:** Power traces supplying the GSM power rail (`VBAT`) are sized with wide copper pours to minimize $IR$ drop during burst transmissions.
* **Decoupling & Noise Immunity:** High-frequency ceramic decoupling capacitors are placed directly adjacent to the MCU and transceiver supply pins with minimal via inductance.

---

## Repository Contents

* `/Design_files_GPStracker` — KiCad schematic files (`.kicad_sch`), PCB layout (`.kicad_pcb`), and project settings.
* `/Gerbers_GPStracker` — Drill files, copper layers, solder mask, and silkscreen files ready for fabrication.


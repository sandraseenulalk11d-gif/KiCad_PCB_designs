# Non-Isolated Capacitive Dropper Power Supply

A compact, transformerless AC-DC power supply designed to power low-current microcontroller and sensor circuits directly from 230V AC mains.

## Technical Specifications
- **Input Voltage:** 230V AC @ 50 Hz
- **Output:** 5V DC / ~30-50 mA
- **Topology:** Capacitive dropper with bridge rectification and Zener shunt regulation

## Safety & Component Implementation
- **Dropping Element:** Metallized polypropylene X2 safety capacitor
- **Shock Protection:** Bleeder resistor for passive capacitive discharge on disconnect
- **Transient & Surge Handling:** Inrush surge limiter resistor + MOV overvoltage clamp
- **Isolation Note:** Non-isolated topology; designed strictly for fully enclosed, touch-safe enclosures.

<div align="center">

# 🌿 Environmental Data Logger
### Custom PCB Design · ATmega328-P · KiCad 9.0.4

*Built from bare components — not breakout boards.*

<br>

[![KiCad](https://img.shields.io/badge/KiCad-9.0.4-blue?style=for-the-badge&logo=kicad&logoColor=white)](https://www.kicad.org/)
[![MCU](https://img.shields.io/badge/ATmega328--P-Bare%20IC-green?style=for-the-badge&logo=arduino&logoColor=white)]()
[![Protocol](https://img.shields.io/badge/SPI%20%2B%20I²C-Protocol-orange?style=for-the-badge)]()
[![Status](https://img.shields.io/badge/Status-Design%20Complete-brightgreen?style=for-the-badge)]()

<br>

</div>

---

## 📸 PCB Preview

<div align="center">

| 📋 Schematic | 🔲 PCB Layout | 🧊 3D Render |
|:---:|:---:|:---:|
| ![Schematic](Screenshot%202026-02-12%20193738.png) | ![Layout](Screenshot%202026-02-12%20193911.png) | ![3D](Screenshot%202026-02-12%20194128.png) |

</div>

---

## 🧠 What Is This?

A fully custom-designed PCB for real-time environmental monitoring — measuring **temperature**, **humidity**, **light intensity**, and **air quality**, logging everything to a **MicroSD card** over SPI, and displaying live data on an **I²C LCD**.

Designed with a clean **three-block modular architecture** for reliable signal routing, noise immunity, and ease of debugging.

> No Arduino shields. No breakout boards. Just bare components, thoughtfully placed.

---

## 🏗️ System Architecture

```
        ┌─────────────────────────────┐
        │       USB 5V Input          │
        └──────────────┬──────────────┘
                       │
                       ▼
        ┌─────────────────────────────┐
        │      Power Management       │
        │   AMS1117-3.3 LDO           │
        │   5V → 3.3V Regulated Rail  │
        │   Decoupling + Status LED   │
        └──────────────┬──────────────┘
                       │
                       ▼
        ┌─────────────────────────────┐
        │       Control Unit          │
        │   ATmega328-P @ 16MHz       │
        │   Crystal Oscillator        │
        │   RESET + Push Button       │
        └────────┬────────────┬───────┘
                 │            │
          SPI Bus             I²C Bus
                 │            │
          MicroSD Card     LCD Display
                 │            │
        ┌────────┴────────────┴───────┐
        │    BSS138 Level Shifters    │
        │     5V  ↔  3.3V Logic      │
        └─────────────────────────────┘
```

---

## 🔩 Hardware Blocks

<details>
<summary><b>⚡ Power Management Block</b></summary>
<br>

- **AMS1117-3.3** LDO regulator — 5V USB → clean 3.3V rail
- **10µF bulk capacitors** on input and output for stability
- **0.1µF ceramic decoupling caps** to suppress switching noise
- **Schottky diode** on VBUS for reverse polarity protection
- **Status LED** with 1kΩ current-limiting resistor for power-on indication

</details>

<details>
<summary><b>🧠 Control Unit</b></summary>
<br>

- **ATmega328-P** bare IC — no bootloader dependency, full register control
- **Crystal oscillator (Y2)** with 22pF load capacitors for precise 16MHz clock
- **Push button** on RESET line with pull-up resistor
- **0.1µF decoupling cap** placed directly at VCC pin for noise filtering

</details>

<details>
<summary><b>📡 Sensors & Interfaces</b></summary>
<br>

- **MicroSD card** in SPI mode with 2.2kΩ pull-ups on all data lines
- **BSS138 MOSFET level shifters** — bidirectional 5V ↔ 3.3V on SDA/SCL lines
- **3.3kΩ pull-down resistors** preventing floating logic on unused inputs
- **4-pin I²C expansion header (J2)** for LCD or additional sensor modules

</details>

---

## 💡 Key Design Decisions

| Decision | Why |
|----------|-----|
| **ATmega328-P bare IC** | Full control over power rail, clock source, footprint. No Arduino bootloader overhead |
| **BSS138 level shifters** | N-channel MOSFET bidirectional shifter — ideal for open-drain I²C. Cheaper & smaller than dedicated ICs |
| **AMS1117-3.3 LDO** | Low-dropout with enough headroom for ATmega + SD + sensors. Stable with ceramics |
| **10µF + 0.1µF decoupling** | Standard mixed-signal bypassing — bulk cap handles transients, ceramic handles HF noise |
| **2.2kΩ SD pull-ups** | Ensures defined logic high on SPI lines during idle and card initialization |

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| **KiCad 9.0.4** | Schematic capture, PCB layout, 3D rendering |
| **ATmega328-P** | Main microcontroller |
| **AMS1117-3.3** | LDO voltage regulator |
| **BSS138 MOSFET** | Bidirectional level shifter |

---

## 📁 Repository Structure

```
Environmental_data_logger/
│
├── 📄 environmental_data_logger.kicad_sch   ← Full KiCad schematic
├── 🖼️  Screenshot 2026-02-12 193738.png      ← Schematic view
├── 🖼️  Screenshot 2026-02-12 193911.png      ← PCB layout
├── 🖼️  Screenshot 2026-02-12 194128.png      ← 3D render
└── 📝 README.md
```

---

## 🚀 Future Improvements

- [ ] Route copper ground pours for noise immunity
- [ ] Add ISP header for direct ATmega flashing (no bootloader)
- [ ] Integrate BME280 footprint directly on board
- [ ] Add UART debug header
- [ ] Submit for fabrication — JLCPCB / PCBWay

---

<div align="center">

*Designed by **Soham Vashistha** · KiCad 9.0.4 · January 2026*

</div>

# RS232 to TTL Serial Converter using MAX232

A hardware serial communication interface that converts **RS232 voltage levels to 5V TTL levels and vice versa** using the **MAX232CPE** transceiver IC.

The project includes the complete circuit design, regulated power supply, PSpice simulation, KiCad schematic, PCB layout, and 3D PCB model.

## 📌 Project Overview

RS232 and TTL use different voltage levels and cannot be directly connected. This project provides a reliable interface between a **5V TTL microcontroller** and **RS232 serial equipment**.

The **MAX232** performs bidirectional level translation between TTL and RS232 signals using an internal charge-pump circuit.

### Main Signal Paths

```text
TTL TX → MAX232 T1IN → T1OUT → RS232
RS232 → MAX232 R1IN → R1OUT → TTL RX
```

## ⚙️ Features

* RS232 ↔ TTL bidirectional level conversion
* MAX232CPE dual RS232 transceiver
* 12V DC input with LM7805 voltage regulation
* Regulated 5V supply
* Internal ±10V charge-pump generation
* DB9 RS232 interface
* 3-pin TTL interface
* KiCad schematic and PCB design
* 2-layer FR4 PCB
* PSpice simulation and verification
* Through-hole components suitable for hand assembly

## 🔧 Hardware Components

| Component                | Part / Value         | Quantity |
| ------------------------ | -------------------- | -------: |
| RS232 Transceiver        | MAX232CPE            |        1 |
| Voltage Regulator        | LM7805CT             |        1 |
| Charge Pump Capacitors   | 1µF / 16V            |        4 |
| Supply Filter Capacitors | 10µF / 100nF         |        2 |
| RS232 Connector          | DB9 Female           |        1 |
| TTL Header               | 3-Pin, 2.54mm        |        1 |
| Power Connector          | 2-Pin Screw Terminal |        1 |
| PCB                      | Custom KiCad PCB     |        1 |

## 🔌 Block Diagram

```text
              +----------------+
12V DC ------>|    LM7805      |
              |  12V → 5V      |
              +-------+--------+
                      |
                     +5V
                      |
              +-------v--------+
TTL TX ------>|                |------> RS232 TX
TTL RX <------|    MAX232      |<------ RS232 RX
              |                |
              +-------+--------+
                      |
                 Charge Pump
                  ±10V Rails
                      |
                  DB9 Port
```

## 🔋 Power Supply

The power section uses an **LM7805 linear regulator** to convert the 12V DC input into a regulated 5V supply for the MAX232 and TTL interface.

```text
12V DC Input
     ↓
  LM7805
     ↓
   +5V DC
     ↓
 MAX232 + TTL Interface
```

The project documentation reports a stable **5.0V regulated output** during simulation.

## 🔄 RS232 ↔ TTL Conversion

TTL logic operates between approximately **0V and 5V**, while RS232 uses bipolar voltage levels.

The MAX232 solves this compatibility problem by:

* Translating TTL signals to RS232 levels
* Translating RS232 signals back to TTL
* Generating the required positive and negative rails using an internal charge pump
* Providing two transmitters and two receivers

## 🖥️ Software & Design Tools

* **KiCad EDA** — Schematic and PCB design
* **OrCAD PSpice** — Circuit simulation
* **SPICE component models** — Simulation verification

## 📐 PCB Design

The PCB was designed as a:

* 2-layer PCB
* FR4 substrate
* 1.6 mm thickness
* Through-hole component design
* Bottom-layer ground plane
* DB9 PCB-mounted connector

The KiCad design also includes a **3D PCB model** for checking component placement and connector clearance.

## 🧪 Simulation Results

| Parameter         |   Result |
| ----------------- | -------: |
| Regulated VCC     |     5.0V |
| RS232 Rail Swing  |     ±10V |
| Maximum Data Rate | 120 kbps |
| TTL Input         |  0V / 5V |

PSpice simulation verified the LM7805 output, MAX232 charge-pump operation, and TTL/RS232 signal inversion.

## 🚀 Applications

This converter can be used for:

* Arduino ↔ RS232 communication
* STM32 ↔ RS232 interfaces
* PC serial communication
* PLC and HMI communication
* GPS receivers
* Barcode readers
* Legacy modems
* Industrial automation
* Embedded firmware debugging
* Serial telemetry

## 📁 Repository Structure

```text
RS232-to-TTL-Serial-Converter/
│
├── README.md
│
├── Documentation/
│   └── Serial-Converter.pptx
│
├── KiCad/
│   ├── Schematic/
│   ├── PCB/
│   └── 3D_Model/
│
├── PSpice/
│   ├── Simulation/
│   └── Results/
│
├── Images/
│   ├── Schematic.png
│   ├── PCB_Layout.png
│   └── PCB_3D.png
│
└── LICENSE
```

## 🎯 Project Objectives

1. Design an RS232 ↔ TTL level converter using MAX232.
2. Design a regulated 5V power supply using LM7805.
3. Verify the power supply using PSpice.
4. Simulate and validate the serial level conversion.
5. Design the schematic and PCB using KiCad.
6. Develop a compact module for serial communication applications.

## 👨‍💻 Author

**Vivekanand Shivshankar Swami**

Electronics & Telecommunication Engineering
SGGS-IET, Nanded

## 📚 Project Type

**SETU Project-Based Internship / Hardware Design Project**

## ✅ Project Status

**Completed**

The project covers the complete workflow from circuit analysis and simulation to KiCad PCB design and fabrication-ready documentation.

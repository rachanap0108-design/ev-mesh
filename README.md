# EV-MESH: Autonomous Mobile Energy Orchestration Hub

> **Smart India Hackathon (SIH) Project**  
> *Turning parked electric vehicles into decentralized, intelligent mobile energy networks.*

---

## 📌 Overview

**EV-MESH** is a platform that transforms parked Electric Vehicles (EVs) into active energy storage nodes. Instead of treating EVs as passive loads that strain the power grid, EV-MESH enables safe, bidirectional energy sharing between **EVs, rooftop solar PVs, stationary storage batteries, and microgrids**.

Powered by our proprietary **MAREN (Mobile Autonomous Reserve Energy Negotiation)** engine, EV-MESH automatically calculates driver commute needs to ensure a donor vehicle is **never left stranded**, while unlocking passive revenue through peak-hour energy trading.

---

## 💥 The Problem vs. The EV-MESH Solution

| Today's Bottlenecks | The EV-MESH Fix |
| :--- | :--- |
| **Stranded EVs & Range Anxiety:** No quick roadside charging option if an EV runs out of power away from a station. | **Peer-to-Peer V2V Rescue:** Nearby EVs can safely transfer emergency power directly to a stranded vehicle anywhere. |
| **Wasted Daytime Solar Energy:** Rooftop solar produces peak power midday when home energy demand is low. | **Smart Capture:** Excess solar is automatically routed into parked EV batteries as decentralized storage. |
| **Grid Transformer Overloads:** Simultaneous EV fast-charging during peak evening hours stresses local power grids. | **Peak Shaving:** Parked EVs discharge surplus energy back into home/facility loads during peak tariff hours. |

---

## ⚡ Core Features

* 🤖 **MAREN Safety Engine:** Calculates target travel distance, traffic buffers, and battery health to guarantee donor peace of mind before transferring a single watt.
* 🔋 **Isolated Bidirectional Power Electronics:** Safe DC-DC voltage stepping across different battery pack voltages ($12\text{V} - 400\text{V}$) without dangerous inrush currents.
* 💰 **Time-of-Day (ToD) Arbitrage:** Automatically charges when power is cheap (or free via solar) and sells surplus energy back during peak tariff hours (earning ₹4.00 – ₹6.50 per kWh shared).
* 🛡️ **Hardware-Enforced Multi-Layer Safety:** Integrated thermal interrupts ($<15\text{ms}$ response) and optical isolation to prevent cell degradation or thermal runaway.
* 📡 **Dual Connectivity (MQTT + BLE):** Syncs with cloud telemetry via MQTT over Wi-Fi/4G, with automatic fallback to offline Bluetooth Low Energy (BLE) direct peer handshakes.

---

## 📐 System Architecture

```text
[ Rooftop Solar PV ] ──┐
                       ├──> [ EV-MESH Hub ] <──> [ EV 1 (Donor) ]
[ Microgrid / Grid ] ──┘          │          <──> [ EV 2 (Receiver) ]
                                  └──> [ Home / Facility Loads ]

🔄 Operational Flow[Telemetry Ingestion] ➔ [Peer Discovery] ➔ [MAREN Optimization] ➔ [Cryptographic Handshake] ➔ [Active Power Flow]
Telemetry Ingestion: Reads battery State of Charge ($\text{SoC}$), State of Health ($\text{SoH}$), and temperature parameters via CAN Bus / OBD-II protocol interfaces.Peer Discovery: Dynamic spatial matching algorithm that pairs requesting nodes with available donor nodes within a defined geofenced radius.MAREN Engine Optimization: Calculates maximum allowable transfer energy ($E_{\text{safe}}$) while maintaining required reserve power based on the donor's next scheduled commute.Cryptographic Handshake: Hardware-level mutual authentication verifying device identity, session parameters, and tokenized access.Active Power Flow: Executes galvanically isolated DC-DC current transfer with continuous, closed-loop thermal and voltage safety monitoring.🛠️ Tech Stack & SpecificationsHardware SubsystemMicrocontroller: ESP32-WROOM-32D (Dual-Core 32-bit LX6 @ 240MHz)Power Stage: Isolated Bidirectional Buck-Boost DC-DC ConverterSensors:INA219 ($\text{I}^2\text{C}$ High-Side Voltage/Current Monitor)ACS712 Hall-Effect Current Sensor Module$NTC$ Thermistors (Direct Thermal Monitoring)Communication & Safety: SN65HVD230 CAN Transceiver, PC817 Optocoupler Isolation RelaysSoftware & Cloud ArchitectureEdge Firmware: Embedded C++ / ESP-IDF (Real-time PWM control, CAN/OBD-II protocol stack, BLE fallback)Optimization Engine: Python (MAREN Algorithm, Matrix Solvers)Backend & Broker: Node.js / FastAPI, EMQX MQTT Broker, InfluxDB (Time-series telemetry database)Frontend Dashboard: React.js, Tailwind CSS, Recharts, Framer Motion💻 Web Dashboard ViewportsThe platform features two specialized viewports designed for real-time monitoring and control:1. Driver & EV Owner App (/driver)Live Battery Telemetry: Visual status ring displaying real-time $\text{SoC}$, $\text{SoH}$, core temperature, and pack voltage.MAREN Commute Slider: Interactive tool allowing users to set target travel distance to automatically reserve and lock necessary driving energy.Power Transfer Monitor: Real-time power flow animations accompanied by a one-tap Emergency Disconnect safety button.Arbitrage Wallet: Live financial tracker reporting passive income earnings (in ₹) from peer-to-peer grid support.2. Grid & Facility Operator Console (/facility)Microgrid Topology: Interactive visual topology map highlighting active node-to-node energy paths across the local grid.Demand Response Analytics: 24-hour peak-shaving chart comparing baseline transformer load against optimized grid load profiles.Thermal Heatmap & Overrides: Node-level thermal tracking matrix with administrative remote shutdown controls.📊 Quantified System ImpactMetricTarget ImpactGrid Peak Stress15% – 20% reduction in local peak transformer loadRenewable UtilizationUp to 30% reduction in daytime solar energy waste (curtailment)Stranded EVs40% decrease in roadside zero-charge emergency eventsOwner Monetization₹2,500 – ₹4,000/month passive revenue generated per active donor vehicle



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

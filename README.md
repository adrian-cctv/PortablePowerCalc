# Portable Power Architect ⚡

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Click%20Here-blue?style=for-the-badge)](#) [![Version](https://img.shields.io/badge/Version-2.1-orange?style=flat-square)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)](https://opensource.org/licenses/MIT)

## 📖 Description
The **Portable Power Architect** is a standalone, browser-based engineering tool designed for Security Architects, Field Technicians, and Systems Integrators. It provides a "Single Pane of Glass" for designing off-grid CCTV trailers, solar skids, and remote communications nodes. 

Instead of relying on guesswork, this tool calculates the exact relationship between continuous DC hardware draw, battery autonomy, environmental degradation, and solar recharge requirements to ensure 24/7 uptime in harsh environments.

## ✨ Core Features
* **Hardware Load Profiling:** Calculate the cumulative continuous draw of IP cameras, industrial routers, and PoE switches.
* **NREL PVWatts Integration:** Built-in guidance for establishing worst-case Peak Sun Hours (PSH) for your specific deployment latitude.
* **Battery Lifecycle Forecasting:** Dynamically predicts End-of-Life (EOL) dates and Low Voltage Disconnect (LVD) thresholds based on chemistry (Lithium vs. AGM) and daily Depth of Discharge (DoD).
* **Environmental Intelligence:** Applies customizable system efficiency buffers and thermal degradation multipliers (vital for high-heat deployments).
* **Zero-Dependency Architecture:** A single HTML file utilizing Vanilla JavaScript and Tailwind CSS. No build tools, Node modules, or backend servers required.

---

## 🚀 How to Use

1. **Clone or Download** the repository.
2. **Open `index.html`** in any modern web browser (Chrome, Edge, Firefox, Safari).
3. **Design Flow:**
    * **Step 1:** Use the **Hardware Load Schedule** to add all active components. Include LED/IR power overheads for night-time operation.
    * **Step 2:** Configure **Site Parameters**. Select the system voltage (12V/24V/48V) and battery chemistry.
    * **Step 3:** Establish your **Sun Hours** using the integrated NREL guide (always design for the Winter Solstice).
    * **Step 4:** Set your **Autonomy Days** and **Efficiency Buffer** based on site conditions.
4. **Export:** Click "Export Design" to generate a clean, print-ready technical submittal for clients or engineering peers.

---

## 🧮 Formula Reference

This tool relies on established electrical engineering principles. Below is the core logic used in the engine:

**1. Daily Energy Consumption (Amp-hours):**
$$Ah_{daily} = \frac{P_{total} \times 24}{V_{system}}$$
*(Where $P_{total}$ is total continuous wattage and $V_{system}$ is the DC bus voltage).*

**2. Minimum Battery Bank Sizing:**
$$C_{bank} = \frac{Ah_{daily} \times Days_{autonomy}}{DoD_{limit}}$$
*(Where $DoD_{limit}$ is 0.9 for LiFePO4 and 0.5 for AGM to prevent chemical damage).*

**3. Required Solar Array:**
$$P_{solar} = \frac{(P_{total} \times 24) / PSH}{\eta_{system}}$$
*(Where $PSH$ is Peak Sun Hours and $\eta_{system}$ is the system efficiency buffer).*

---

## 🏜️ Deployment Best Practices

When designing for extreme environments (such as the Pilbara, Goldfields, or general heavy industrial sites), adhere to the following baseline parameters:

* **The 80% Rule:** Never set the Efficiency Buffer above **80%**. You must account for MPPT conversion heat, PoE step-up injector losses, and panel soiling (dust/salt buildup).
* **Design for June:** Never use annual average Sun Hours. Always extract the lowest monthly value (typically June in the Southern Hemisphere) to ensure the system survives the Winter Solstice without deep-cycling the batteries.
* **Heat Degradation:** Ambient temperatures exceeding 35°C will severely impact battery chemistry. For internal enclosure temperatures operating continuously above 40°C, assume a **20% to 30% reduction** in projected lifecycle, regardless of lithium cell resilience.

---

## ⚙️ Technical Specifications
* **Framework:** HTML5 / Vanilla ES6 JavaScript
* **Styling:** Tailwind CSS (via CDN)
* **Typography:** Inter (UI) & JetBrains Mono (Data Metrics)
* **Storage:** Stateless execution (No local storage or cookies utilized)

---

## 📜 Version History
* **v2.1 (Current):** Added Battery Lifecycle Forecasting, LVD cut-off calculations, and Thermal Degradation logic.
* **v1.8:** Introduced NREL PVWatts design guide and adjustable System Efficiency loss slider.
* **v1.5:** Initial Off-Grid pivot. Added System Voltage selection, daily Ah conversions, and solar array sizing.
* **v1.0:** Base PoE hardware load calculator.

---

## ⚠️ Disclaimer
**For Estimation Purposes Only.** This tool provides theoretical design parameters based on mathematical constants and user inputs. It does not replace the requirement for certified electrical engineering review. Actual system performance will vary based on hardware quality, shading, cable gauge resistance, and extreme weather anomalies. Always consult with a licensed professional before finalizing off-grid power infrastructure.

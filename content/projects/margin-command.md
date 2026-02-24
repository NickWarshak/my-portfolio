---
title: "Margin Command: Inventory Intelligence HUD"
date: 2026-02-24
draft: false
description: "A Python-based inventory telemetry dashboard designed to track floorplan interest bleed and sales velocity."
tags: ["Python", "Streamlit", "Data Visualization", "Financial Logic", "Plotly"]
showToc: true
weight: 10
---

[Live Application](https://margincommand.streamlit.app) | [View Source Code on GitHub](https://github.com/NickWarshak/margin-command)

### Project Overview
**Margin Command** is a strategic "Command Center" for automotive inventory management. Moving away from traditional, static spreadsheets, this tool provides a high-contrast, visual HUD (Heads-Up Display) for dealership principals to identify which units are generating profit and which are "bleeding" capital due to floorplan interest.

---

### Technical Stack
* **Framework:** Built with **Streamlit** for a responsive, web-based UI.
* **Visualization:** Utilizes **Plotly Express** for hierarchical data exploration (Sunburst charts) and interactive data matrices.
* **Data Processing:** Leverages **Pandas** and **NumPy** to execute complex pivot table subtractions for "Gap Analysis."
* **Styling:** Custom **CSS Injection** to create a "Gallery" aesthetic—moving beyond standard dashboard templates into a bespoke, luxury-brand interface.

---

### Key Features & Logic
The engine focuses on the "cost of time," transforming raw stock data into actionable financial insights:

* **Floorplan Bleed Calculation:** Automatically calculates the daily interest "bleed" of every unit based on its days on lot, exposing the hidden costs of aged inventory.
* **Performance Gap (The Delta Engine):** A custom algorithm that subtracts 30-day sales velocity from current stock levels to instantly highlight **Shortages** (lost opportunity) and **Overstock** (capital risk).
* **Asset Composition Sunburst:** A multi-level drill-down chart that allows users to navigate inventory depth from Model Family → Trim Level → Exterior Color in a single view.
* **CRM Demand Integration:** Bridges the gap between physical inventory and shopper intent by visualizing "Demand Heat" scores directly alongside stock status.

---

### Why This Matters
This project demonstrates my ability to take raw operational data and translate it into a high-end User Experience. It showcases proficiency in **state management** (handling simulated data arrays), **financial logic implementation**, and **UI/UX design** within a data-science context.
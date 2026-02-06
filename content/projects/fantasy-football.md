---
title: "NFL Player Prop Projection Engine"
date: 2026-02-05
draft: false
description: "A C# analytical tool that leverages market data from The Odds API to project fantasy football performance."
tags: ["C#", ".NET", "Data Analytics", "API Integration", "Fantasy Football"]
showToc: true
weight: 20
---

[View Source Code on GitHub](https://github.com/NickWarshak/fantasy-football-analyzer)

### Project Overview
This project is a high-performance C# application designed to bridge the gap between sports betting markets and fantasy football projections. By pulling real-time player prop data, the engine calculates "implied" fantasy scores based on market probability rather than just historical averages.

---

### Technical Implementation
* **Language & Framework:** Built using **C#** and **.NET** in Visual Studio.
* **API Integration:** Utilizes **Asynchronous Programming (`async/await`)** to fetch real-time event and market data from *The Odds API*.
* **Data Parsing:** Leverages **System.Text.Json** for efficient serialization of complex, nested JSON responses from multiple bookmakers.
* **Security:** Implemented **Environment Variables** to manage sensitive API credentials, ensuring no hardcoded keys are exposed in version control.

---

### The Logic (The Math)
The engine doesn't just look at yardage totals; it calculates a "Weighted Component Score":
* **Implied Probability:** Converts American odds into a decimal percentage to weigh the likelihood of touchdown outcomes.
* **Positional Logic:** Uses a custom **Switch Expression** to apply different scoring weights (PPR, Passing, Rushing) based on the player's detected position (QB, RB, WR, TE).
* **Combined TD Analysis:** Uniquely combines Passing Touchdowns (PTD) and Anytime Touchdowns (ATD) into a single "Touchdown Impact" metric for more accurate ceiling projections.

---

### Professional Takeaway
This project demonstrates my ability to handle **real-time data pipelines**, manage **asynchronous API calls**, and translate complex business logic (betting odds) into actionable insights (fantasy projections).

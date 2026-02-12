---
title: "Predictive Analytics: Polynomial Regression Engine"
date: 2026-02-05
draft: false
description: "A machine learning analysis utilizing Python to predict housing values through advanced feature engineering and regression modeling."
tags: ["Python", "Data Science", "Machine Learning", "Predictive Modeling"]
showToc: true
weight: 30
---

[View Source Code on GitHub](https://github.com/NickWarshak/gradient-descent-optimization)

### Project Overview
Developed a predictive modeling engine to analyze the California Housing dataset. This project moves beyond standard linear estimation by implementing feature expansion and statistical validation to map complex, non-linear relationships between geographic/economic variables and real estate market values.

---

### Technical Stack
* **Language:** Python (Jupyter Ecosystem)
* **Data Manipulation:** Pandas & NumPy
* **Visualization:** Matplotlib & Seaborn
* **Modeling:** Scikit-Learn (PolynomialFeatures, LinearRegression)

---

### Key Features & Implementation
* **Advanced Feature Engineering:** Utilized **Polynomial Features** to transform raw data into a 2nd-degree polynomial matrix ($x_1^2, x_1x_2$, etc.), enabling the model to capture multidimensional interactions.
* **Exploratory Data Analysis (EDA):** Architected a **Correlation Heatmap** to identify high-impact variables and reduce model noise by dropping redundant features like total room counts and geographic outliers.
* **Comparative Performance Analysis:** Implemented a dual-model workflow, testing a standard **Linear Baseline** against an optimized **Polynomial Engine** to quantify accuracy improvements.
* **Error Visualization:** Developed **Residual Histograms** and **Mean Squared Error (MSE)** comparison plots to statistically validate the model's predictive reliability.



---

### The Logic (The Math)
The project focuses on minimizing the variance between predicted and actual values through two distinct stages:
* **Residual Analysis:** Evaluated the frequency and distribution of absolute errors to ensure the model was not biased toward specific price brackets.
* **Complexity Management:** Balanced the trade-off between model depth and computational efficiency, successfully reducing the **Mean Absolute Error** through polynomial expansion without causing over-fitting.



---

### Why This Matters
This project demonstrates proficiency in the full data science lifecycle: from raw data ingestion and cleaning to feature engineering and statistical validation. It showcases an ability to use industry-standard Python libraries to derive actionable insights from complex datasets.

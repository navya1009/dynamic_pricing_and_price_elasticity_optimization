# 📈 Retail Price Optimization & Prescriptive Analytics Engine

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Statsmodels](https://img.shields.io/badge/Statsmodels-Econometrics-orange.svg)
![Status](https://img.shields.io/badge/Status-Complete-green.svg)

## 📌 Executive Summary
Most retail pricing strategies rely on static historical margins or pure guesswork. This project builds a **prescriptive econometric model** to transition pricing from a guessing game into a mathematically optimized strategy. 

By utilizing a Multivariate Log-Log OLS Regression, this engine explicitly calculates the **Price Elasticity of Demand (PED)** while isolating external market noise (competitor pricing, holidays). The final optimization algorithm simulates hundreds of pricing scenarios to identify the exact unit price that **maximizes total category revenue by a projected 34.8%**.

## 🎯 Business Objectives
1. **Estimate True Demand:** Calculate Own-Price and Cross-Price elasticity for the `garden_tools` retail category.
2. **Isolate Market Noise:** Control for macro-environmental factors like holiday seasonality and competitor price fluctuations.
3. **Revenue Optimization:** Build an algorithm to prescribe the exact maximum-profit price point without triggering severe customer churn (Sticker Shock).

---

## 🔬 Methodology & Architecture

Unlike black-box predictive models (e.g., XGBoost, Neural Networks) that suffer from overfitting on limited transactional data, this project utilizes rigid statistical inference to provide actionable business metrics.

* **Data Engineering:** Aggregated raw transactional data into weekly time-series formats, engineering new features like total landed cost (base price + freight).
* **Econometric Modeling:** Deployed a Log-Log Ordinary Least Squares (OLS) regression to linearize the demand curve and extract constant elasticity coefficients.
* **Multivariate Controls:** Factored in `comp_1` (competitor pricing) and `holiday` (seasonality dummy variables) to prevent Omitted Variable Bias.
* **Prescriptive Simulation:** Engineered a mathematical loop to test hypothetical price points against the trained elasticity curve to pinpoint the revenue-maximizing threshold.

---

## 📊 Key Business Insights

### 1. Own-Price Elasticity (-0.67) = Inelastic Demand
The model revealed an elasticity coefficient of -0.67. Because the absolute value is < 1, the product is mathematically inelastic. 
* **Insight:** The business is currently leaving money on the table. Customers are highly tolerant of price increases in this specific category.

### 2. Cross-Price Elasticity (-1.13) = Market Leader Dependency
Standard substitute goods show positive cross-price elasticity. This dataset revealed a *negative* correlation (-1.13) to competitor pricing.
* **Insight:** The competitor acts as the "Category Anchor." When they raise prices, overall market traffic drops, dragging our sales down with them. We cannot simply price-gouge when they do.

### 3. Consumer Psychology (The Freight Cost Penalty)
Exploratory Data Analysis (EDA) correlation matrices revealed consumers are more deterred by high shipping costs (-0.39) than high base unit prices (-0.30).

---

## 🚀 Strategic Recommendations & Implementation

Based on the prescriptive model, I recommend the following executive actions:

1. **Adjust Base Pricing:** Safely scale the unit price from the historical average of ~$80 toward the optimized threshold of $190-$200. The simulation projects a **34.8% increase in total revenue**.
2. **Geo-Targeted A/B Testing:** To avoid the "Analytics Trap" of dangerous mathematical extrapolation, do not deploy the $200 price point globally. Roll out the optimized price to a 10% traffic variant (Control vs. Variant) for two weeks to validate the revenue projection against real-world "sticker shock" before scaling.
3. **Free Shipping Subsidies:** Leverage the EDA freight insight by baking shipping costs into the newly optimized, higher base price to trigger psychological "Free Shipping" conversions.

---

## 💻 Tech Stack
* **Language:** Python
* **Analytics & Math:** Pandas, NumPy, Statsmodels (OLS)
* **Data Visualization:** Matplotlib, Seaborn
* **Environment:** Jupyter Notebook / Google Colab

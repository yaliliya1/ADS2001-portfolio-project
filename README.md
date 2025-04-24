# Stock Portfolio Optimisation (ADS2001 Project – Monash University)

This project was developed for the ADS2001 unit at Monash University. The goal was to explore and compare different portfolio allocation strategies using historical S&P 500 stock data. Multiple optimisation approaches were implemented, including static weighting, breakout strategies, and dynamic allocation using Support Vector Regression (SVR).

---

## 🎯 Objective

To determine optimal portfolio weights that maximise the **Sharpe ratio**, a metric representing risk-adjusted return. The project compares:
- **Absolute static weights**: fixed proportions across time
- **Relative static weights**: periodic rebalancing based on yearly trends
- **Dynamic weights**: machine learning-based portfolio adaptation
- **Equal weights**: implemented via a breakout strategy

---

## 📚 Dataset

- Historical adjusted closing prices for S&P 500 stocks over ~16 years
- Source: Publicly available financial databases (CSV format)
- Preprocessing steps:
  - Forward/backward fill to address missing data
  - Feature engineering (returns, volatility, rolling windows)

---

## 🧠 Methods

### 1. Absolute Static Weights
- Randomly generated 1000 portfolios and evaluated Sharpe ratios
- Used **SLSQP optimisation** from `scipy.optimize` to minimise negative Sharpe ratio
- Annualised return, volatility, and Sharpe ratio plotted for both methods

### 2. Relative Static Weights
- Monthly investment strategy with yearly re-optimisation
- Portfolio re-selection based on year-end price conditions
- Compared randomly generated portfolios vs. standard optimisation

### 3. Equal Weights – Breakout Strategy
- Moving average crossover (5-day vs. 15-day) to generate buy/sell signals
- Used **GridSearchCV** to tune stop-loss and take-profit thresholds
- Achieved Sharpe ratio improvement from **0.35 → 3.14** post optimisation

### 4. Dynamic Weights – Support Vector Regression (SVR)
- Trained **SVR (RBF kernel)** on rolling stats (90/180/360 days)
- Target: future return and volatility per stock
- Portfolio weights were optimised using predicted returns/risks
- Achieved a **mean actual Sharpe ratio of 2.92**, outperforming other strategies

---

## 📊 Results Summary

| Strategy              | Actual Mean Sharpe Ratio |
|-----------------------|---------------------------|
| Random Static Weights | 1.76                      |
| Static Optimisation   | 1.65                      |
| Breakout (Optimised)  | 3.14                      |
| **SVR Dynamic Weights** | **2.92** (most consistent) |

---

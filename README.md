# 📊 Market Risk — Value at Risk (VaR) Analysis
### NSE Equity Portfolio | Excel + Power BI | Jan 2022 – Dec 2024

![Risk Analysis](https://img.shields.io/badge/Domain-Market%20Risk-1E3A5F?style=for-the-badge)
![Tool](https://img.shields.io/badge/Tool-Microsoft%20Excel-217346?style=for-the-badge&logo=microsoft-excel)
![Tool](https://img.shields.io/badge/Tool-Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Status](https://img.shields.io/badge/Status-Completed-2ecc71?style=for-the-badge)

---

## 📌 Project Overview

This project estimates the **daily Value at Risk (VaR)** of a diversified NSE-listed equity portfolio using two industry-standard methodologies — **Historical Simulation** and **Variance-Covariance**. The model is validated through a **Basel Traffic Light backtesting framework**, and all findings are presented in an interactive **Power BI dashboard**.

> **Key Question:** *On a bad day (1% probability), how much can this portfolio lose?*

---

## 🏦 Portfolio Composition

| # | Company | Sector | Ticker | Weight |
|---|---------|--------|--------|--------|
| 1 | Reliance Industries | Energy / Conglomerate | RELIANCE.NS | 20% |
| 2 | Tata Consultancy Services | Information Technology | TCS.NS | 20% |
| 3 | Infosys | Information Technology | INFY.NS | 20% |
| 4 | ICICI Bank | Banking & Financial Services | ICICIBANK.NS | 20% |
| 5 | ITC Limited | FMCG | ITC.NS | 20% |

**Total Portfolio Value assumed:** ₹10,00,000 (₹10 Lakhs)

---

## 🗂️ Repository Structure

```
Market-Risk-VaR-Analysis/
│
├── VaR_Analysis_Portfolio.xlsx   # Main Excel model (4 sheets)
│   ├── Price Data                # Raw daily closing prices (742 days)
│   ├── Log Returns               # Daily log returns for all 5 stocks
│   ├── VaR Model                 # Portfolio returns + VaR calculations
│   └── Backtesting               # Breach flags + Basel summary
│
├── VaR_Dashboard.pbix            # Interactive Power BI dashboard
│
├── VaR_Project_Report.docx       # Full project report with findings
│
└── README.md                     # This file
```

---

## ⚙️ Methodology

### Step 1 — Data Collection
- Daily closing prices downloaded for **742 trading days** (Jan 2022 – Dec 2024)
- Sources: Investing.com and NSE India official website
- Date alignment verified across all 5 stocks

### Step 2 — Log Returns
Daily log returns calculated using:
```
Log Return = LN(Today's Price / Yesterday's Price)
```
Portfolio return = weighted sum of individual stock log returns (20% each)

### Step 3 — VaR Estimation

#### Method 1: Historical Simulation
- Sorted all 742 portfolio returns empirically
- Extracted 1st percentile (99% VaR) and 5th percentile (95% VaR)
- No distributional assumptions — captures actual tail events

#### Method 2: Variance-Covariance
- Computed mean and standard deviation of portfolio returns
- Applied formula: `VaR = Mean − (Z-score × Std Dev)`
- Z-scores: **2.326** (99%) and **1.645** (95%)
- Assumes normally distributed returns

### Step 4 — Backtesting
- Flagged every day where actual loss exceeded VaR threshold
- Compared actual vs expected breaches using **Basel Traffic Light Test**

---

## 📈 Results

### Descriptive Statistics

| Metric | Value |
|--------|-------|
| Total Trading Days | 742 |
| Mean Daily Return | +0.0384% |
| Standard Deviation | 0.9402% |
| Observation Period | Jan 2022 – Dec 2024 |

### VaR Results

| Method | Confidence | VaR (Daily %) | VaR (₹) |
|--------|-----------|---------------|---------|
| Historical Simulation | 99% | **-2.45%** | **-₹24,459** |
| Historical Simulation | 95% | -1.44% | -₹14,353 |
| Variance-Covariance | 99% | **-2.15%** | **-₹21,486** |
| Variance-Covariance | 95% | -1.50% | -₹15,036 |

### Backtesting — Basel Traffic Light

| Confidence | Actual Breaches | Expected | Breach Rate | Verdict |
|-----------|----------------|----------|-------------|---------|
| 99% | 10 | 7 | 1.35% | ⚠️ Exceeds Basel Limit |
| 95% | 35 | 37 | 4.72% | ✅ Within Basel Limit |

---

## 🔍 Key Findings

1. **99% VaR slightly breached the Basel limit** — 10 actual breaches vs 7 expected. This is attributed to the extreme market volatility of 2022 (US Fed rate hikes, global inflation, Russia-Ukraine crisis) which produced tail losses beyond the model's historical estimation capability.

2. **95% VaR performed with high accuracy** — 35 breaches vs 37 expected, confirming the model is reliable at moderate confidence levels.

3. **Historical Simulation > Variance-Covariance at 99%** — HS captured actual extreme events (-2.45%) more conservatively than the normality-assuming VCV method (-2.15%), consistent with known fat-tail behaviour in equity markets.

4. **Portfolio maintained positive drift** — Mean daily return of +0.038% confirms the portfolio's upward trajectory over the 3-year cycle despite significant volatility.

---

## ⚠️ Limitations

- Historical Simulation cannot predict unprecedented macro shocks (black swan events)
- Variance-Covariance assumes normality — underestimates tail risk during stress periods
- Analysis limited to daily VaR — Basel III requires 10-day VaR (square root of time scaling)
- Constant correlation assumed between stocks

## 🔭 Future Scope

- Monte Carlo Simulation as a third VaR methodology
- Expected Shortfall / CVaR calculation
- 10-day VaR scaling using square root of time rule
- Dynamic Conditional Correlation (DCC) model for stress periods

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Microsoft Excel | Data cleaning, log returns, VaR model, backtesting |
| Power BI Desktop | Interactive dashboard, DAX measures |
| NSE India / Investing.com | Data sourcing |

---

## 👤 About

**FRM Candidate** | B.Com + MA Economics  
Certifications: Risk Management Specialisation (NYIF) · BI Essentials Power BI (CFI) · Data Analysis Excel (CFI)  
Seeking: Risk Analyst roles in Banking, NBFC, or Financial Services

---

*This project was built as part of a self-initiated risk analytics portfolio to demonstrate practical application of FRM concepts.*

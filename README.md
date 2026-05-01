# Financial Risk & Portfolio Stress-Testing Model

<div align="center">

**An institutional-grade, multi-sheet Excel model for portfolio risk quantification, macro shock simulation, and predictive drawdown analysis across 20 securities and 4 asset classes.**

[📥 Download Model](Portfolio_Risk_Stress_Testing_Model.xlsx) &nbsp;·&nbsp; [📊 View Screenshots](#screenshots) &nbsp;·&nbsp; 
</div>

---

## Overview

This project simulates the workflow of a **quantitative risk analyst** at an investment firm. It ingests a 20-security multi-asset portfolio and runs it through a complete risk analytics pipeline — from raw data ingestion and KPI computation, through parametric Value at Risk modelling, to a five-scenario macro stress-test engine with live severity classification.

The model is built entirely in **Microsoft Excel** with zero external dependencies, demonstrating mastery of advanced formula architecture, financial modelling conventions, and interactive dashboard design.

---

## Objectives

1. **Portfolio Performance Measurement** — Compute core KPIs including annualized return, weighted average beta, Sharpe ratio, and diversification score across all asset classes using dynamic cross-sheet formula linkages.

2. **Risk Quantification via VaR** — Implement the industry-standard **Parametric Value at Risk** model using `NORM.INV` and the square-root-of-time rule (Basel III compliant), alongside **Expected Shortfall (CVaR)** for tail-risk estimation.

3. **Monte Carlo Simulation** — Simulate 10,000 portfolio paths over a 10-day horizon using Gaussian return distributions, with a 30-path sample table showing breach detection against the VaR threshold.

4. **Macro Scenario Stress-Testing** — Model five distinct market shock scenarios — Rate Hike, Liquidity Crunch, Equity Market Crash, Currency Devaluation, and Stagflation — computing asset-class-level P&L impact, total drawdown, and automatic severity classification per scenario.

5. **Executive Dashboard Visualisation** — Present all findings on a single interactive dashboard with live-linked KPI cards, a portfolio allocation doughnut chart, a stress-test drawdown bar chart, and a top-5 securities return chart — all auto-updating when inputs change.

---

## Features

### 🏠 Interactive Dashboard
- 8 live KPI cards — portfolio value, P&L, return, VaR, CVaR, beta, Sharpe ratio, security count
- 3 embedded interactive charts linked to live formula outputs via a hidden `_ChartData` sheet
- Stress-test severity summary table with colour-coded scenario flags
- Freeze panes, no gridlines — clean executive presentation layout

### 📊 Raw Data Engine
- 20 securities across Equity, Fixed Income, Commodity, and Real Estate
- 15 data columns — beta, correlation to SPX, P/E ratio, dividend yield, 52-week high/low
- Industry-standard colour coding: **blue = hardcoded inputs · black = formulas · green = cross-sheet links**
- Auto-filter on all columns for dynamic slicing by sector, market, and asset class
- Heat-map conditional formatting on current values and annualized returns

### 📈 KPI Engine
- 10 portfolio-level KPIs using `SUMPRODUCT`, `AVERAGEIF`, `COUNTIF`, and array logic
- Asset class breakdown with count, total value, allocation %, average return, and average volatility
- Sharpe ratio and diversification score auto-calculated from weighted inputs

### 🎯 Scenario Stress-Test
- 5 parameterized macro shock scenarios with editable blue-cell inputs
- Per-scenario P&L decomposed by asset class
- Auto-severity flags: **✅ TOLERABLE · ⚡ SEVERE · ⚠ CRITICAL**
- Drawdown heat-map using 3-colour conditional formatting scale

### 📉 VaR Model
- Parametric VaR at 95% confidence over a 10-day horizon (Basel III standard)
- `NORM.INV` z-score extraction with square-root-of-time scaling
- CVaR at 1.25× VaR for fat-tail adjustment
- 30-path Monte Carlo simulation table with breach detection per path
- P&L conditional formatting across all simulation paths

### 🔍 Assumptions Documentation
- Full source documentation for every model input
- References: Federal Reserve H.15, Basel III, IFRS 13, Bloomberg Terminal conventions

---

## Methodology

```
Raw Portfolio Data (20 Securities)
            │
            ▼
┌─────────────────────────────┐
│        KPI Engine            │  SUMPRODUCT · AVERAGEIF · Weighted Beta · Sharpe
└─────────────┬───────────────┘
              │
      ┌───────┴────────┐
      ▼                ▼
┌───────────┐   ┌──────────────────────┐
│ VaR Model  │   │  Stress-Test Engine   │
│           │   │                      │
│ NORM.INV  │   │  5 Shock Scenarios    │
│ CVaR      │   │  Asset-Class P&L      │
│ Monte     │   │  Severity Auto-Flag   │
│ Carlo     │   │  Drawdown Heatmap     │
└─────┬─────┘   └──────────┬───────────┘
      │                    │
      └──────────┬─────────┘
                 ▼
      ┌──────────────────────┐
      │  Executive Dashboard  │
      │  8 KPI Cards          │
      │  3 Live Charts        │
      │  Severity Summary     │
      └──────────────────────┘
```

### VaR Formula Chain

| Step | Formula | Output |
|---|---|---|
| Daily Std Dev | `=SUMPRODUCT(weights, volatilities) / SQRT(252)` | Daily portfolio σ |
| 10-Day Std Dev | `= Daily σ × SQRT(10)` | Scaled σ |
| Z-Score | `= NORM.INV(0.95, 0, 1) × −1` | 1.645 |
| Parametric VaR | `= Portfolio Value × 10-Day σ × Z` | $ amount at risk |
| CVaR | `= VaR × 1.25` | Tail-risk estimate |

---

## Tech Stack

| Layer | Detail |
|---|---|
| Primary Tool | Microsoft Excel (Advanced) |
| Formula Engine | `NORM.INV`, `SUMPRODUCT`, `AVERAGEIF`, `SUMIF`, `COUNTIF`, Array Formulas |
| Simulation | Monte Carlo — Gaussian distribution, 10,000 paths |
| Risk Framework | Parametric VaR, CVaR, Basel III aligned |
| Visualisation | Doughnut Chart, Horizontal Bar Chart, Column Chart — live-linked |
| Data Integrity | 3-colour Conditional Formatting, Heat-map CF, Auto-Filter |
| Documentation | Assumptions sheet with Basel III / IFRS 13 / Bloomberg source references |

---

## Key Financial Concepts Applied

| Concept | Application in Model |
|---|---|
| Value at Risk (VaR) | Maximum expected loss at 95% confidence over 10 days |
| Expected Shortfall (CVaR) | Average tail-loss beyond the VaR threshold |
| Monte Carlo Simulation | Stochastic 10-day portfolio path modelling |
| Beta | Market sensitivity of each security vs S&P 500 |
| Sharpe Ratio | Risk-adjusted return per unit of volatility |
| Drawdown Analysis | Peak-to-trough loss under each macro shock scenario |
| Basel III | Regulatory framework for VaR confidence and time horizon |
| IFRS 13 | Fair value hierarchy for mark-to-market pricing convention |

---

## Author

**Devika Pavithran**

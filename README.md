# Financial Econometrics – Time Series Forecasting & Term Structure Analysis

A Python-based empirical study combining multivariate time series forecasting with interest rate term structure analysis. The project applies VAR, ARIMA, and unit root testing frameworks to exchange rates, price indices, and US Treasury yields over a 25-year horizon (2001–2025).

---

## Objective

This project addresses two related empirical questions:

1. **Forecasting:** Which model — a differenced VAR (DVAR) or univariate ARIMA — produces more accurate out-of-sample forecasts for exchange rate and price dynamics?
2. **Term Structure:** Do US Treasury yield spreads exhibit stationarity, and what does this imply for the Expectations Hypothesis (EH) of the yield curve?

---

## Repository Structure

```
financial-econometrics/
├── README.md
├── Results.md
├── financial_econometrics.ipynb     # Main analysis notebook
├── data/
│   ├── financial econometrics.csv   # Exchange rate and price index data
│   └── interest rates.csv           # US Treasury yields (3M, 2Y, 5Y, 10Y)
└── images/
    ├── dvar_forecasts
        ├── dvar_de.png
        ├── dvar_dp1.png
        ├── dvar_dp2.png
    ├── arima_forecasts
        ├── arima_de.png
        ├── arima_dp1.png
        ├── arima_dp2.png
    ├── individual_rates_stationarity.png
    └── spreads_stationarity.png
```

---

## Methodology

### Part 1 — DVAR Forecasting

A differenced Vector Autoregression (DVAR) model is estimated on monthly first differences of exchange rate (Δe), US price index (Δp1), and UK price index (Δp2) from January 2001 to December 2022. Lag order p = 2 is imposed from prior analysis. The fitted model generates 36-month out-of-sample forecasts covering 2023–2025, evaluated against realised values.

### Part 2 — Univariate ARIMA Models (`UnivariateForecastingTask`)

A class-based ARIMA framework fits separate models to each of the three variables. Model order selection is automated via AIC grid search over ARIMA(p, 0, q) for p, q ∈ {0, 1, 2, 3}, with d = 0 applied since all series are already first-differenced. For each variable, the notebook produces ACF/PACF diagnostics, in-sample fit statistics, and 36-month forecasts with 95% confidence intervals.

### Part 3 — Forecast Comparison & Diebold–Mariano Test (`ForecastComparisonTask`)

DVAR and ARIMA forecasts are compared using MAE and RMSE computed at four forecast horizons: 1–3 months, 4–12 months, 13–24 months, and 25–36 months. Statistical equivalence of forecast accuracy is tested using the **Diebold–Mariano (DM) test**, with the null hypothesis that the two models have equal predictive accuracy.

### Part 4 — Interest Rate Integration & Expectations Hypothesis

US Treasury yields (3-month, 2-year, 5-year, 10-year) are sourced at monthly frequency from January 2001 to February 2026. Three term structure spreads are constructed (10Y–3M, 5Y–3M, 2Y–3M) and tested for stationarity using both the **Augmented Dickey–Fuller (ADF)** and **KPSS** tests in combination. Stationarity of the spread series is interpreted as evidence of cointegration between long and short rates, which is a necessary condition for the Expectations Hypothesis to hold.

--

## How to Run

**Requirements:** Python 3.8+

Install dependencies:
```bash
pip install pandas numpy matplotlib statsmodels scipy
```

Place the data files in the same directory as the notebook (or update the `path` variable in the first cells), then run `financial_econometrics.ipynb` from top to bottom. Each section is clearly labelled by task (Step 1 through Step 4).

---

## Data Sources

| Dataset | Description | Source |
|---|---|---|
| `financial econometrics.csv` | Monthly exchange rate (e), US price index (p1), UK price index (p2), 2001–2025 | Bloomberg |
| `interest rates.csv` | Monthly US Treasury yields: 3M, 2Y, 5Y, 10Y, January 2001–February 2026 | Federal Reserve H.15 / FRED |

---

## Skills & Tools

`Python` `pandas` `NumPy` `Matplotlib` `statsmodels` `SciPy`  
`Vector Autoregression (VAR)` `ARIMA` `AIC Model Selection` `Diebold–Mariano Test`  
`ADF Unit Root Test` `KPSS Test` `Cointegration` `Expectations Hypothesis`  
`Time Series Forecasting` `Term Structure Analysis` `Financial Econometrics`

---

## Potential Extensions

- **Johansen cointegration test** to formally determine the number of cointegrating vectors among the yield series, as a natural follow-on to the unit root results
- **Granger causality testing** to assess whether yield spreads predict future short rate movements, directly testing a core implication of the Expectations Hypothesis
- **VECM (Vector Error Correction Model)** to exploit any identified cointegrating relationships in the forecasting framework
- **Rolling window estimation** to test parameter stability and assess whether DVAR vs ARIMA performance varies across macroeconomic regimes
- **GARCH extensions** to account for time-varying volatility in exchange rate and price dynamics

---

## Author

**Kobby Akuoko**  

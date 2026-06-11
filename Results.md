## Key Results
 
### Forecast Accuracy (36-Month Out-of-Sample)
 
| Variable | DVAR RMSE | ARIMA RMSE | DM Significant? |
|---|---|---|---|
| Δe (Exchange Rate) | 0.019822 | 0.020001 | No |
| Δp1 (US Prices) | 0.004256 | 0.004210 | No |
| Δp2 (UK Prices) | 0.002627 | 0.002713 | No |
 
### Unit Root Test Summary
 
| Series | ADF Order | KPSS Order | Final Order | EH Support |
|---|---|---|---|---|
| US3M | I(1) | I(0) | Mixed | Partial |
| US2Y | I(0) | I(0) | I(0) | Yes |
| US5Y | I(1) | I(1) | I(1) | No |
| US10Y | I(1) | I(1) | I(1) | No |
| 10Y–3M Spread | I(1) | I(1) | I(1) | No |
| 5Y–3M Spread | I(1) | I(1) | I(1) | No |
| 2Y–3M Spread | I(0) | I(1) | Mixed | Partial |

---
 
## Interpretation of Results
 
### Forecasting: DVAR vs ARIMA
 
Across all three variables, the DVAR model marginally outperforms the univariate ARIMA on RMSE. DVAR produces a lower error for Δe (0.0198 vs 0.0200), Δp2 (0.0026 vs 0.0027), while ARIMA has a very slight edge on Δp1 (0.00421 vs 0.00426). However, none of these differences are statistically significant: the Diebold–Mariano test fails to reject the null of equal predictive accuracy for any variable.
 
This is a substantively meaningful finding rather than a null result. It suggests that the cross variable dynamics captured by the VAR, such as lagged exchange rate and price interactions, add negligible forecasting value over a 36-month horizon once the series have been differenced. In practical terms, a practitioner could use the simpler univariate ARIMA models without meaningful loss of forecast precision. The result is broadly consistent with the well documented finding in the forecasting literature that parsimony often outperforms richer multivariate models out of sample, particularly at longer horizons where parameter estimation error compounds.
 
### Term Structure: Unit Root Tests and the Expectations Hypothesis
 
The EH holds that long-term interest rates are determined by expected future short term rates, implying that the spread between any long and short rate should be stationary (mean reverting). The unit root tests provide only weak and mixed support for this hypothesis.
 
**Individual rates:** Three of the four series (US5Y, US10Y, and US3M by ADF) are classified as I(1), consistent with the well established result that interest rates behave like near random walks over long samples. The notable exception is US2Y, where both ADF and KPSS agree on I(0), a finding that suggests the 2 year yield may be more anchored to Federal Reserve policy expectations than longer maturities, which are more heavily influenced by term premia and market sentiment.
 
**Spread series:** The results provide little support for the EH at longer maturities. Both the 10Y–3M and 5Y–3M spreads are classified as I(1) by both tests, implying that long and short rates can drift apart indefinitely rather than being bound by a stable equilibrium relationship. This is inconsistent with the EH and may reflect the influence of time varying term premia, shifts in the inflation regime, or structural changes in monetary policy over the 2001–2026 sample period. The 2Y–3M spread produces mixed results (ADF: I(0), KPSS: I(1)), providing at best partial and ambiguous support at the short end of the curve.
 
Taken together, the evidence suggests the US yield curve over this period is better characterised by non stationary dynamics than by the equilibrium anchoring that the Expectations Hypothesis would imply, a conclusion that motivates formal cointegration testing (Johansen) as a natural next step.

---

# B401 Assignment Handover — EWMA vs Historical Std Dev Experiment

## Context

This is a B401 Continuous-time Derivatives Pricing assignment (Uni Tübingen, due July 6 2026).
The notebook is `B401_Assignment_2026.ipynb`. The underlying is Rheinmetall AG (RHM.DE).
The traded certificate being valued in Part 2 is DU2076 (DZ BANK bonus cap certificate on RHM.DE).

---

## Current Methodology (what exists in the notebook)

**Volatility split — known inconsistency:**

| Tasks | Method | Variable |
|---|---|---|
| V, VI, VII (Part 2) | EWMA (λ=0.94) | `ewma_vol` dict, `sigmas_used` array |
| VIII–XI (Part 3) | Historical std dev | `sigma_mc = log_returns.std() * sqrt(252)` |

The inconsistency is acknowledged. Tasks VIII–XI use historical std dev because the assignment brief (Task IX) explicitly says "prices are based on the historical volatility of the underlying."

**Current EWMA results for Task V (error vs DU2076 market prices, 183 days):**

```
Mean Error (ME)   = -85.54 EUR
MAE               =  94.49 EUR
RMSE              = 108.92 EUR  (6.92% of mean market price 1574.75 EUR)
MAPE              =   6.11%
Mean EWMA vol     =  44.27%  (time-varying, reacts to Nov 2025 crash)
Mean implied vol  =  37.77%  (back-solved from cert prices — circular, not used elsewhere)
```

**Historical std dev (already computed in notebook):**
```
sigma_mc = log_returns.std() * sqrt(252) = 39.88%
```
This is a single constant value used for all 183 days. It is already in the notebook as `sigma_mc`.

---

## What the Experiment Should Do

Replace EWMA with historical std dev as the vol input for Tasks V, VI, VII and compare results.

### Exact change in Cell 37 (the pricing loop)

Current code (inside the for loop):
```python
sigma_est = float(np.clip(ewma_vol.get(date, SIGMA_DESIGN), 0.10, 0.60))
```

Replace with:
```python
sigma_est = float(np.clip(sigma_mc, 0.10, 0.60))  # constant historical std dev
```

`sigma_mc` is already computed earlier in the notebook (Cell 57 area) as:
```python
sigma_mc = float(log_returns.std() * np.sqrt(252))  # = 39.88%
```

But note: `sigma_mc` is defined in a later cell. To avoid dependency ordering issues, just hardcode the value or recompute it inline:
```python
SIGMA_HIST = float(log_returns.std() * np.sqrt(252))
```
Then use `SIGMA_HIST` in the pricing loop instead of `ewma_vol.get(date, SIGMA_DESIGN)`.

### Tasks VI and VII also use sigmas_used

- **Task VI (Greeks, Cell 45):** Uses `RISK_FREE` and a single reference sigma — already uses `SIGMA_DESIGN` or current EWMA snapshot. Check what sigma is passed at the reference point.
- **Task VII (Replicating portfolio, Cell 49):** Uses `sigmas_used[i]` in a daily loop. Replace with `SIGMA_HIST` constant.
- **Task VII (Equity fraction vs S, Cell 53):** Uses `float(np.median(sigmas_used))` as `sig_snap`. Replace with `SIGMA_HIST`.

---

## What to Compare and Report

Run both versions and produce a side-by-side table:

```
Metric          EWMA (λ=0.94)    Hist Std Dev
ME (EUR)           -85.54           ???
MAE (EUR)           94.49           ???
RMSE (EUR)         108.92           ???
MAPE (%)             6.11           ???
Mean vol            44.27%         39.88% (constant)
```

Then give a verdict: which method produces lower RMSE/MAPE? Is the difference meaningful?

---

## Key Background Facts

- RHM.DE had a major crash in Nov 2025 — EWMA vol spiked to ~50%+ in response
- Historical std dev is 39.88% — closer to the market-implied vol of 37.77%
- EWMA overestimates vol (44.27% vs 37.77% implied) → underprices cert → negative ME
- If historical std dev (39.88%) is closer to 37.77%, it may produce lower RMSE
- But historical std dev is flat — it won't capture the vol clustering around the Nov 2025 crash

---

## Files

- Notebook: `B401_Assignment_2026.ipynb`
- Cert prices: `data/cert_prices.csv` (onvista.de export, DU2076)
- RHM prices: downloaded via yfinance (Jan 2023 – Jun 2026)
- ECB rates: `data/ECB Data Portal_20260615151519.csv` (Svensson params)
- Current comparison CSV: `data/du2076_daily_comparison.csv`

---

## Important Constraints

- Do NOT change Tasks VIII–XI — they correctly use historical std dev per assignment brief
- Do NOT make API calls at runtime — all data is in local files
- The risk-free rate is `RISK_FREE = svensson(10.0, ...)` = 3.07% — do not change this for Part 1/MC
- For Part 2 daily valuation, risk-free rate is maturity-matched daily via `get_risk_free_rate(date, T_rem)` — keep this
- Do NOT remove the IV back-solve block from Cell 40 — just add the historical std dev comparison alongside
- After the experiment, revert the notebook to EWMA if EWMA gives better results

---

## Expected Outcome Hypothesis

Historical std dev (39.88%) is closer to market-implied vol (37.77%) than EWMA (44.27%) is.
So historical std dev will likely give lower RMSE. But it will be a flat line — it won't track the
vol clustering around the Nov 2025 crash as well as EWMA. The question is whether the vol-level
accuracy of hist std dev outweighs EWMA's time-variation benefit.

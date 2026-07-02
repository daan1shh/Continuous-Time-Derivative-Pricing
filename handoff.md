# B401 Assignment – Session Handoff

**Student:** Daanish Muzaffar | **ID:** 7259472  
**Due:** Monday 6 July 2026, 1:00 PM  
**Submission:** Ilias – poster (A3) + code + data  

---

## What this project is

B401: Continuous-Time Derivatives Pricing, Eberhard Karls Universität Tübingen, Summer 2026.  
The assignment has three parts; all implemented in one Jupyter notebook.

**File:** `B401_Assignment_2026.ipynb` (68 cells, in `/Users/daanishmuzaffar/Daanish/MEF/Contionuous Time derivative Pricing/Assignment/`)

---

## Product summary

**Part 1 – Fictitious product (designed):**  
Capped Capital Protected Participation Note on Rheinmetall AG (RHM.DE).  
- 3-year maturity, normalised S₀ = 100  
- ZCB (100% protection) + long ATM call (K=100) + short OTM call (K=130)  
- α ≈ 83.1% participation rate, max gain ≈ +24.9% of nominal  
- σ = 39%, q = 0.54%, r = 2.62% (Svensson 3y spot)

**Part 2 – Traded product (valued):**  
DU2076 – Deutsche Bank Bonus Cap Certificate on RHM.DE  
- Cap/Bonus K = 2,000 EUR, Barrier B = 1,050 EUR, Maturity 18 Jun 2027  
- Valuation window: 1 Oct 2025 – Apr 2026 (124 trading days)  
- Method: CRR binomial tree, N=200 steps, EWMA vol (λ=0.94), maturity-matched Svensson r

**Part 3 – Portfolio insurance (Monte Carlo):**  
- W₀ = €10,000, T* = 1 year, underlying RHM.DE  
- GBM: μ = 58.57% (historical), σ = 39.25%, 50,000 paths × 252 steps, seed = 2026  
- Insurance via fictitious BS-priced puts

---

## Key parameters (global, in cell 447bcb96)

```python
TICKER       = 'RHM.DE'
DIV_YIELD    = 0.0054     # €7.20 / €1,342 = 0.537%
SIGMA_CPN    = 0.39       # 252-day historical vol = 39.25%
Q_CPN        = 0.0054
SIGMA_DESIGN = 0.39
K_CPN        = 100.0      # ATM call strike
K_CAP_CPN    = 130.0      # OTM cap call
T_CPN        = 3.0
BARRIER_PCT  = 0.70       # DU2076 barrier = 70% of spot
BONUS_PCT    = 1.15       # DU2076 bonus = 115% of spot
```

**Svensson parameters** (Bundesbank, 01 Jun 2026, cell `a0eb1795`):
```python
SV_P1 = dict(b0=1.330382, b1=0.700052, b2=1.816755,
             b3=7.130184, tau1=0.966763, tau2=15.839369)
```

---

## Cell map (all 68 cells)

```
 0  [mark] title
 1  [mark] Setup heading
 2  [mark] imports explanation
 3  [code] 24caaa02   imports
 4  [mark] global params heading
 5  [code] 447bcb96   GLOBAL PARAMETERS
 6  [mark] 8398145b   Design Parameter Sources (table with hyperlinks)
 7  [mark] Svensson heading
 8  [code] a0eb1795   Svensson function + α computation + r for Part 2
 9  [mark] Svensson source
10  [mark] PART 1 heading
11  [mark] e7c1dd26   Task I – Investor profile
12  [mark] 479d5960   Task II – Product design (with LaTeX payoff formula)
13  [mark] Task III heading
14  [mark] payoff explanation
15  [code] 55db50e3   Task III payoff diagram (with regime labels)
16  [mark] Task IV heading
17  [mark] market size source
18  [mark] market size explanation
19  [code] 06856bfb   Task IV market size + Bonus/Discount comparison table
20  [mark] PART 2 heading
21  [mark] Data Download heading
22  [mark] data download explanation
23  [code] 5d41e79d   yfinance download + stock chart + EWMA vol
24  [mark] data sources
25  [mark] Pricing Engine heading
26  [code] d248833d   4 functions: bs_put, bs_call, down_and_out_put (CRR N=200), bonus_cap_cert_price
27  [mark] Task V heading
28  [mark] ecbfb957   DU2076 data sources
29  [mark] Task V loop explanation
30  [code] bb1a1e41   Task V valuation loop (124 days, EWMA vol, maturity-matched r)
31  [mark] Task V error metrics heading
32  [code] b20ac924   Error metrics: ME, MAE, RMSE, MAPE, Corr + Q5/Q25/Q50/Q75/Q95
33  [mark] c0323d7b   Error interpretation
34  [mark] Task VI heading
35  [mark] Greeks explanation
36  [code] 14eebb61   Greeks (central FD): Delta, Gamma, Vega, Theta — 4-panel plot
37  [mark] 44547020   Gamma note + Theta (positive, explained) + Vega dual attribution
38  [mark] Task VII heading
39  [mark] replicating portfolio explanation
40  [code] bb5e66de   Task VII time series: daily delta + equity fraction
41  [mark] vii-ts-interp  Task VII time series INTERPRETATION (falling market)
42  [mark] equity fraction vs S heading
43  [code] f5f5262c   equity fraction vs S (static snapshot T=1.5y)
44  [mark] PART 3 heading
45  [mark] 8560c7c0   MC parameter sources (table)
46  [mark] MC setup explanation
47  [code] 523bdd1b   MC simulation (GBM, 50k paths, seed=2026)
48  [mark] Task VIII heading
49  [mark] Task VIII explanation
50  [code] 57c143b5   performance_stats function + unhedged return distribution
51  [mark] fa0ccc52   drift note + GBM structural limitations (fat tails, jumps, etc.)
52  [code] drift-sensitivity  drift sensitivity table (μ=6/12/30/58.6%)
53  [mark] Task IX heading
54  [mark] Task IX explanation
55  [code] a10bacc9   insured_return function + 4×4 grid (alpha × strike)
56  [mark] Task IX heatmaps heading
57  [code] 64a46d3f   heatmaps: VaR and mean return
58  [mark] ix-heatmap-interp  Task IX DISCUSSION (high-drift counter-intuition, regime caveat)
59  [mark] Task X heading
60  [mark] Task X explanation
61  [code] 05e45d7e   stress scenarios (baseline, vol±5pp, -20% shock)
62  [mark] b0c6f7ef   Task X interpretation (Vol+5pp VaR=15.8% breaches Task XI limit)
63  [mark] Task XI heading
64  [mark] Task XI explanation
65  [code] 857539ab   brentq solver for α* + VaR-vs-α plot
66  [mark] 8b2844ea   Task XI interpretation (α* is MAXIMUM, not floor; VaR increases with α)
67  [mark] output files summary
```

---

## Critical conceptual points (grader-facing)

**Task XI (most important):** Under μ = 58.57%, VaR *increases* with α. This is because at the 5th percentile, RHM has still risen and puts expire OTM — the premium is a pure drag. α* ≈ 14.3% is the **maximum** allowed allocation (constraint ceiling), not an optimal floor. The text in cell `8b2844ea` correctly reflects this.

**Task X:** Vol+5pp raises VaR to ~15.8%, which **breaches** the Task XI 15% regulatory limit. This is explicitly stated in cell `b0c6f7ef`.

**Task V:** Error quantiles (Q5/Q25/Q50/Q75/Q95) are included — this was explicitly required by the assignment text ("error quantile").

**Pricing logic:** Bonus Cap = [Forward − Call(K_cap)] + DO_Put(K_cap, B). The CRR binomial tree with N=200 steps handles the path-dependent DO-put. This is validated by the session 2 slides.

**α computation:** Solved at runtime. α = (100 − ZCB₀) / (Call(K=100) − Call(K=130)) ≈ 83.1% using Svensson 3y rate and σ=39%.

---

## Files on disk

```
B401_Assignment_2026.ipynb    ← main notebook
data/cert_prices.csv          ← DU2076 market prices from ariva.de (semicolon, German decimal)
graphs/                       ← output PNG files (regenerated on run)
  payoff_profile.png
  stock_data.png
  valuation_comparison.png
  greeks.png
  replicating_portfolio_time.png
  equity_fraction_vs_S.png
  mc_unhedged.png
  insurance_heatmap.png
  stress_scenarios.png
  var_constraint.png
CTDP_Assignment_2026.pdf      ← assignment PDF
CTDP2026_Session2_01062026.pdf ← session 2 slides
handoff.md                    ← this file
```

---

## Working with the notebook (important notes for Claude)

**Reading the notebook:** The `.ipynb` file is large (~2MB with outputs). Always strip outputs first before using the Read tool:
```python
import json
with open('B401_Assignment_2026.ipynb') as f:
    nb = json.load(f)
for c in nb['cells']:
    if c['cell_type'] == 'code':
        c['outputs'] = []
        c['execution_count'] = None
with open('B401_Assignment_2026.ipynb', 'w') as f:
    json.dump(nb, f, indent=1, ensure_ascii=False)
```

**Editing the notebook:** Use Python JSON direct editing (write script to `/tmp/nb_edit.py` with the Write tool, then run with Bash). Do NOT use Bash `cat/echo` to write the script — use the Write tool to avoid shell escaping issues. The NotebookEdit tool is unreliable: it fails if Bash has read the file between the Read and the edit.

**Pattern for all edits:**
```python
import json
path = '/Users/daanishmuzaffar/Daanish/MEF/Contionuous Time derivative Pricing/Assignment/B401_Assignment_2026.ipynb'
with open(path) as f:
    nb = json.load(f)
ids = [c.get('id', f'cell-{i}') for i, c in enumerate(nb['cells'])]
def idx(cid): return ids.index(cid)
def gs(cell): s = cell.get('source',''); return ''.join(s) if isinstance(s, list) else s
def ss(cell, src): cell['source'] = src
# ... make changes ...
with open(path, 'w') as f:
    json.dump(nb, f, indent=1, ensure_ascii=False)
```

**Inserting cells:**
```python
new_cell = {"cell_type": "markdown", "id": "new-id", "metadata": {}, "source": "content"}
i_after = ids.index('target-cell-id')
nb['cells'].insert(i_after + 1, new_cell)
ids.insert(i_after + 1, 'new-id')
```

---

## What has been done (session history condensed)

1. Added markdown explanations to every code cell (all cells have headings + prose)
2. Fixed `DIV_YIELD` from 1.5% → 0.54% (€7.20/€1,342); `SIGMA_CPN` from 30% → 39%
3. Removed Part 1 Greeks (not required by assignment)
4. Removed junk cells: sqrtT_cpn, alpha_uncapped, bonus_cert_price, cpn_price, two sanity checks
5. Fixed `ALPHA_CPN` from 83.8% → 83.1% (Task II markdown updated)
6. Print bug fixed: `MAX_GAIN_CPN:.1%` was showing `2491.9%`, now `+24.9% of nominal`
7. Added error quantiles Q5/Q25/Q50/Q75/Q95 + MAPE + correlation to Task V
8. Added market regime labels (BEARISH / MODERATELY BULLISH / STRONGLY BULLISH) to payoff diagram
9. Added Bonus/Discount Certificate comparison table to Task IV market size
10. Expanded Task VI note: positive Theta explained, dual Vega attribution added
11. Corrected Task XI interpretation: α* is a maximum (upper bound), not a protection floor
12. Updated Task X: Vol+5pp scenario explicitly flagged as breaching Task XI 15% VaR limit
13. Expanded GBM limitations: constant vol, no jumps, log-normal tails, non-stationary drift
14. Added Task VII time-series interpretation markdown (falling market Delta/equity fraction)
15. Added Task IX heatmap discussion (counter-intuitive high-drift result, drift caveat)
16. Added drift sensitivity analysis code cell (μ = 6%, 12%, 30%, 58.6%)

---

## Things that could still be improved (optional, time permitting)

- **Add Rho subplot** to the Greeks 4-panel chart (currently Delta/Gamma/Vega/Theta only)
- **LaTeX for key formulas** — most math is in plain text; only Task II has `$$...$$` blocks
- **4th product component** (e.g. digital cash-or-nothing call) would boost complexity score — this is the #1 grade driver per the assignment sheet and session slides
- **MC convergence diagnostic** for Task XI brentq solver (show α* is stable across seeds)
- Task III payoff table has a hard-coded `breakeven_bond` — verify it still prints correctly after Svensson rate changes

---

## Feedback/preferences for Claude in this project

- Do NOT make API calls at runtime in the notebook. Download external data as files instead.
- Use the Write tool (not Bash cat/echo) to create Python scripts.
- Keep responses terse. No trailing summaries after diffs.
- Use Python JSON direct editing for all notebook changes — do not rely on NotebookEdit.

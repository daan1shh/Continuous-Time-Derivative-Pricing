# Meta-Prompt: Generate an A3 Poster Design Prompt for B401

Feed this entire document to an AI. It will output a complete, ready-to-use poster design prompt — containing exact layout wireframes, section text, graph placements, and typography specs — that can then be handed to a designer or used in a design tool (Canva, InDesign, LaTeX/beamer, PowerPoint) to build the final poster.

---

## YOUR TASK

You are a scientific poster designer with experience in academic finance posters. Read all the content below carefully. Then write a complete, self-contained design prompt for an A3 academic poster. The design prompt you produce should be specific enough that someone with no knowledge of this assignment could use it alone — with the graphs listed — to produce the finished poster. It should include: a precise layout wireframe, word-for-word draft text for every section, exact graph placement and sizing, font sizes, color scheme, and any visual hierarchy decisions.

Do not produce the poster itself. Produce the design prompt that will be used to create it.

---

## ASSIGNMENT CONTEXT

**Course:** B401 — Continuous-Time Derivatives Pricing, University of Tübingen, Summer Term 2026  
**Instructor:** Prof. Dr. Christian Koziol, Faculty of Economics and Social Sciences, Department of Finance  
**Student name and ID must appear in the top-left corner of the poster** (per the assignment sheet — leave a placeholder: [Name] / [Matriculation Number])  
**Underlying asset:** Rheinmetall AG (RHM.DE), Frankfurt Stock Exchange  
**Discussion partners (top-left corner):** [Fellow student names]  

The poster covers three parts and eleven tasks. It must be self-explanatory — a reader who has not seen the code should be able to understand what was done, what the numbers mean, and why the conclusions follow.

---

## MANDATORY FORMAT CONSTRAINTS

- **Size:** A3, portrait orientation (297 mm wide × 420 mm tall)
- **Minimum font size:** 11 pt body text everywhere
- **Page count:** exactly 1 page, no overflow
- **Layout:** 3-column grid. Column 1 = Part 1, Column 2 = Part 2, Column 3 = Part 3
- **Header band:** full-width strip at the top (university name, course code, poster title, student name/ID, discussion partners)
- **No placeholder text in the final poster.** Every metric cell must show a real number
- **All 8 graphs must be embedded** (see graph list below). Graphs that are too small to read are worse than no graph — prioritise legibility over quantity
- **Tables for quantitative results** must appear in Tasks V, VIII, IX, X, XI
- **Writing language:** English. Clear, academically appropriate sentences. No em dashes. No filler phrases ("it is worth noting", "delve into", "it is important to highlight", "showcase", "in the realm of"). Avoid passive constructions where active is natural. Concise is better than comprehensive

---

## AVAILABLE GRAPHS (exact filenames, all in `graphs/` folder)

| Filename | Content | Assigned to |
|---|---|---|
| `payoff_profile.png` | Payoff diagram: capital-protected note vs direct RHM stock across three S_T scenarios | Task III |
| `valuation_comparison.png` | Daily model price (EWMA binomial tree) vs observed DU2076 market price, Sep 2025–Jun 2026 | Task V |
| `greeks.png` | Four-panel plot: Delta, Gamma, Vega, Theta of DU2076 vs stock price S | Task VI |
| `equity_fraction_vs_S.png` | Equity fraction (Delta × S / Cert. value) of replicating portfolio vs S at a fixed point in time | Task VII |
| `mc_unhedged.png` | Return distribution histogram (50,000 GBM paths, no insurance) with 95% VaR line | Task VIII |
| `insurance_heatmap.png` | Side-by-side heatmaps: 95% VaR and mean return across α (5–20%) × K (90–105% of S₀) | Task IX |
| `stress_scenarios.png` | Overlapping return distributions for four stress scenarios at α=10%, K=95%S₀ | Task X |
| `var_constraint.png` | VaR vs α curve at K=95%S₀ with 15% regulatory limit line and α*=7.90% marked | Task XI |

**Layout priority:** Tasks III, V, VIII, IX are the most data-rich — give their graphs more vertical space. Tasks VI, VII, X, XI graphs can be smaller since they are supplemented by tables or short text.

---

## FULL CONTENT DATA

### PART 1 — DESIGNING CERTIFICATES (Column 1)

**Task I — Investor Profile**

Target investor: German retail investor, aged 40–60, approaching retirement in 10–15 years. Holds existing savings (pension fund, real estate) and is looking for a satellite equity position. Bullish on European defence spending following NATO budget commitments and Germany's Sondervermögen (special defence fund), but cannot stomach direct stock ownership: RHM.DE has annualised volatility of approximately 54%, which exceeds the investor's stated risk ceiling. Prefers capital preservation with structured upside participation. Investment horizon: 3 years (matching the product tenor). Compares the product to: (i) direct RHM.DE stock — too volatile; (ii) a defence sector ETF — lower volatility but diversifies away RHM-specific upside; (iii) a money market fund — no equity exposure.

**Task II — Product Design**

Product: **Capped Capital Protected Participation Note** on Rheinmetall AG  
Components: Zero-Coupon Bond + 93.4% × ATM Call (K = EUR 1,207) − 93.4% × OTM Cap Call (K = EUR 1,569)  

Pricing at design date (S₀ = EUR 1,207, σ = 54.17%, r = 2.62% 3-year Svensson rate, q = 0.60%, T = 3 years):
- ZCB present value: EUR 1,115.79
- Long ATM call (K = 1,207): EUR 451.04
- Short OTM cap call (K = 1,569): EUR 353.43
- Net spread (long − short): EUR 97.61
- Participation rate α = 1,115.79 / (1,115.79 + 97.61 / α) solved at-par → **α = 93.4%**
- Maximum gain at maturity (S_T ≥ 1,569): EUR 338.36 per unit (+28.0% above nominal)

Intuition: The ZCB guarantees return of the EUR 1,207 nominal at maturity regardless of RHM performance. The bull call spread (long ATM, short OTM) provides 93.4% participation in any RHM gain up to the 30% cap level. The short cap call monetises the investor's low probability of a gain above 130% of S₀, financing the higher participation rate.

**Task III — Product Payoff**

Graph: `payoff_profile.png` — shows three zones:
- BEARISH (S_T < 1,207): certificate pays EUR 1,207 (capital floor); direct stock pays S_T < 1,207 — certificate wins
- MODERATELY BULLISH (1,207 ≤ S_T ≤ 1,569): certificate pays 1,207 + 0.934 × (S_T − 1,207); outperforms stock in lower portion, underperforms above ~1,384
- STRONGLY BULLISH (S_T > 1,569): certificate pays capped EUR 1,569; direct stock pays S_T — stock wins

**Task IV — Market Size**

Germany structured products market: EUR 112 bn total (BSW 2023 data)  
Capital protection (Kapitalschutz) segment: 3.8% = EUR 4.26 bn  
Participation notes (Partizipationsprodukte): 55% of segment = EUR 2.34 bn  
Approximately 130 active issues, average issue size EUR 33 mn  
Addressable market for this specific product: estimated EUR 200–300 mn (single-name, defence-theme capital protection)

---

### PART 2 — VALUATION OF CERTIFICATES (Column 2)

**Product priced:** DU2076 — Bonus Certificate with Cap on Rheinmetall AG, issued by DZ BANK  
**Decomposition:** `Down-and-Out Put (barrier monitoring) + Capped Forward`  
**Key product parameters:**
- Observation start: 4 September 2025; maturity: 18 June 2027 (T ≈ 1.80 years)
- Barrier B = EUR 1,050 (≈ 61.5% of S₀ at emission)
- Bonus/Cap level K = EUR 2,000 (≈ 117% of S₀ at emission)
- Underlying price at valuation start (4 Sep 2025): EUR 1,707.93

**Task V — Valuation**

Method: CRR binomial tree, N = 200 steps. Daily ECB Svensson spot rate, maturity-matched each day.  
Valuation window: 183 trading days (4 Sep 2025 to 1 Jun 2026)  
Volatility models: (i) EWMA (λ = 0.94), mean 44.27%; (ii) back-solved implied vol (brentq, N = 50), mean 37.77%

Error metrics table (include in poster):

| Metric | EWMA Model | Implied Vol Model |
|---|---|---|
| Mean Error (EUR) | -85.54 | -8.89 |
| MAE (EUR) | 94.49 | 9.82 |
| RMSE (EUR) | 108.92 | 12.37 |
| MAPE (%) | 6.11 | 0.64 |
| Mean vol used | 44.27% | 37.77% |

Observation: The EWMA model systematically underprices DU2076 by EUR 85.54 on average (ME = −85.54 EUR). Once implied volatility is used, the error drops to −EUR 8.89 and MAPE to 0.64%, confirming that the EWMA vol overestimates the option-implied risk and the model structure is sound.

Graph: `valuation_comparison.png` — shows daily model vs market price time series. The systematic gap in the EWMA series and the near-perfect fit of the IV model are the key visual.

**Task VI — Sensitivity / Greeks**

Greeks computed via central finite differences at: S_ref = EUR 1,708, T = 1.79 y, σ = 44.6% (median EWMA), r = 2.14%

Reference point values:
| Greek | Value | Interpretation |
|---|---|---|
| Delta | 0.245 | Low delta because stock is far above barrier; cert behaves like a capped forward |
| Gamma | ≈ 0 (at reference) | Substantial near barrier; chart shows the spike |
| Vega | -13.55 per pp | Negative: higher vol increases probability of barrier breach, destroying put protection |
| Theta | +0.36 per day | Positive: time passing reduces knock-out risk, increasing cert value |

Negative Vega is the key non-obvious result: unlike a vanilla option, higher volatility hurts the Bonus Certificate holder because it raises the chance of losing the bonus.

Graph: `greeks.png` — four-panel plot vs S. Note binomial tree sawtooth in Gamma/Vega is a discretisation artifact.

**Task VII — Replicating Portfolio**

The replicating portfolio holds Delta × S in RHM.DE stock and the remainder in a risk-free bond.  
Equity fraction = (Delta × S) / Certificate Value.  
Near the barrier (S ≈ EUR 1,050): equity fraction exceeds 130% — the portfolio is leveraged long equity to hedge the put component. Far above the barrier: equity fraction falls toward zero as the cert behaves like a capped forward. At the cap (S ≥ EUR 2,000): cert is fully capped; equity fraction → 0.

In falling markets: as S approaches the barrier, Delta rises sharply, the bond position shrinks, and the portfolio shifts toward an almost fully-equity position. If the barrier is breached, the put component vanishes and the cert converts to a leveraged capped forward with no capital protection.

Graph: `equity_fraction_vs_S.png`

---

### PART 3 — PORTFOLIO INSURANCE STRATEGY (Column 3)

**Setup:** EUR 10,000 initial capital, T* = 1 year, underlying = RHM.DE  
**GBM parameters (estimated from 866-day log-return series, Yahoo Finance):**
- S₀ = EUR 1,207
- μ_hist = 54.05% p.a. (geometric log-price drift, annualised mean log-return)
- σ = 39.88% p.a.
- r = 3.07% (10-year Svensson rate)
- Simulation: 50,000 paths × 252 steps, seed 2026

**Task VIII — Performance without Risk Management**

Results (unhedged stock position):

| Measure | Value |
|---|---|
| Mean log-return | 54.03% |
| Median log-return | 54.17% |
| Std deviation | 39.92% |
| Skewness | 0.007 |
| Sharpe ratio | 1.277 |
| 95% VaR (loss) | 11.32% |
| 95% CVaR (loss) | 28.38% |
| P(loss) | 8.7% |

The log-return distribution is approximately symmetric (skewness ≈ 0), consistent with a GBM model where log-prices follow a normal distribution. With a drift of 54.05%, 91.3% of simulated paths end above the starting price after one year.

Graph: `mc_unhedged.png`

**Task IX — Performance with Risk Management**

Portfolio: (1 − α) × stock + α × European put options (priced via Black-Scholes at historical σ = 39.88%)  
Grid: α ∈ {5%, 10%, 15%, 20%}, K ∈ {90%, 95%, 100%, 105%} × S₀

Selected results from the full 4×4 table (include in poster — compact version):

| α | K | Mean | Sharpe | 95% VaR |
|---|---|---|---|---|
| 5% | 95% | 49.50% | 1.201 | 13.63% |
| 10% | 95% | 44.66% | 1.105 | 16.00% |
| 10% | 100% | 44.79% | 1.115 | 12.97% |
| 15% | 95% | 39.49% | 0.990 | 16.07% |
| 20% | 95% | 33.98% | 0.855 | 19.87% |

Key finding: In a high-drift regime (μ = 54.05%), VaR increases with α for most strikes. At the 5th percentile, RHM has typically still risen (put expires out of the money) and the put premium paid at t = 0 is a pure drag on wealth. Higher α means more premium spent with no offsetting payoff at the VaR quantile, so tail outcomes worsen. Higher strikes (K = 100%, 105%) reduce VaR for a given α because the ITM put's payoff offsets the premium drag in bad scenarios.

Graph: `insurance_heatmap.png` — two panels: VaR heatmap (lower = better) and mean return heatmap (higher = better)

**Task X — Stress Scenario Analysis**

Allocation tested: α = 10%, K = 95% × S₀

| Scenario | Mean return | 95% VaR | 95% CVaR | P(loss) |
|---|---|---|---|---|
| Baseline | 44.66% | 16.00% | 16.79% | 13.7% |
| Vol +5pp (to 44.88%) | 44.52% | 16.77% | 19.40% | 13.7% |
| Vol -5pp (to 34.88%) | 44.84% | 13.62% | 14.73% | 13.7% |
| -20% price shock at T/2 | 24.82% | 17.07% | 17.70% | 29.8% |

The baseline at α = 10% already produces a VaR of 16.00%, above the 15% regulatory limit in Task XI. The Vol +5pp scenario worsens VaR to 16.77%, while Vol −5pp is the only compliant scenario (13.62%). The -20% mid-horizon shock has the largest impact on expected return (collapses to 24.82%) and P(loss) (nearly triples to 29.8%).

Graph: `stress_scenarios.png`

**Task XI — Capital Requirement / VaR Constraint**

Binding constraint: 95% one-year VaR ≤ 15%  
Strike fixed: K = 95% × S₀  
Solver: brentq root-finding on VaR(α) = 0.15

**Result: α* = 7.90%**  
- Resulting VaR at α* = 7.90%: **exactly 15.00%**
- Expected return at α* = 46.73%
- Sharpe ratio at α* = 1.148
- Unhedged VaR (α = 0): 11.32%

Interpretation: Under the observed high-drift regime, VaR is an increasing function of α — more put coverage raises the 5th-percentile loss because put premiums are the dominant cost at that quantile. The unhedged position (VaR = 11.32%) is actually the best outcome for the VaR metric. α* = 7.90% is therefore the **maximum** permitted allocation, not an investor-preferred target: allocating beyond 7.90% violates the regulatory constraint. The optimal allocation that fully utilises the 15% VaR budget is α = 7.90%, delivering an expected return of 46.73% with Sharpe 1.148.

Graph: `var_constraint.png` — shows VaR vs α curve, 15% limit line, and α* = 7.90% marked

---

## WRITING STYLE CONSTRAINTS FOR THE POSTER TEXT

These constraints apply to every word of text in the poster design prompt you generate:

1. **No em dashes** (—). Use a comma, colon, semicolon, or a new sentence instead.
2. **No AI filler phrases.** Banned: "it is worth noting", "it is important to highlight", "in the realm of", "delve into", "showcase", "robust", "leverage" (when used metaphorically), "seamlessly", "nuanced", "multifaceted", "holistic approach", "shed light on", "game-changer".
3. **No passive voice where active is natural.** Not "the constraint is violated" but "the strategy violates the constraint."
4. **Academic competence without jargon inflation.** A reader who studied finance at undergraduate level should follow every sentence without a dictionary.
5. **Numbers beat adjectives.** Do not write "a significant reduction in VaR." Write "VaR falls from 16.00% to 13.62%."
6. **Section labels should be plain.** "Task I: Investor Profile" not "I. Comprehensive Investor Profiling Framework."
7. **Interpretations must be present.** Every table and graph must have at least one sentence explaining what the number means, not just what it shows.

---

## WHAT THE POSTER DESIGN PROMPT MUST SPECIFY

When you produce the design prompt, it must include all of the following:

1. **Exact layout wireframe** with pixel or millimetre dimensions for each column, the header strip, and each content block within each column. Three columns, portrait A3.

2. **Header strip content:** University name (Eberhard Karls Universitat Tubingen), Faculty of Economics and Social Sciences, Department of Finance, "B401: Continuous-Time Derivatives Pricing — Summer Term 2026", student name/ID placeholder top-left, discussion partner names top-left, poster title ("Portfolio Insurance and Structured Product Pricing on Rheinmetall AG").

3. **Word-for-word draft text** for every section (Tasks I through XI), written to the style constraints above. Each section text should be tight: 2–5 sentences of explanation plus the table or graph reference. No section should be a wall of text — use bullet points and tables where numbers are involved.

4. **Graph placement and dimensions** for each of the 8 graphs. Specify: which column, vertical position in the column (top/middle/bottom), approximate height in mm, caption text.

5. **Typography spec:** font family (suggest a clean serif or sans-serif available in Word/Google Docs), body size (11 pt minimum), heading sizes, line spacing.

6. **Colour scheme:** suggest 2–3 accent colours that match a finance/academic aesthetic. The Tübingen university colours are dark red (#8B0000 or similar) and white. Suggest using those as the primary accent for headers and table borders, with the rest in clean black on white or light grey.

7. **Table formatting** for every numeric table: all cells filled with real numbers from the data above, column headers, units stated, borders minimal.

8. **A note on graph sizing:** graphs must be at a minimum width of 60 mm (landscape) so axis labels remain legible at A3 print size. If 8 graphs cannot all fit at this size, specify which 2 to drop and replace with a compact summary table — prioritise payoff_profile, insurance_heatmap, valuation_comparison, and var_constraint as the 4 non-negotiable graphs.

9. **Column balance check:** estimate the content height of each column and confirm it fits within the available body area (A3 portrait body ≈ 390 mm tall after header). If overflowing, specify which sections to condense and how.

---

## OUTPUT FORMAT

Produce the poster design prompt as a structured document with clearly labeled sections matching the 9 items above. The prompt should be usable as a standalone design brief — hand it to a designer or paste it into a design AI and the poster can be built without any additional questions.

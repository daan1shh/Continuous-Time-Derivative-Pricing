# B401 Poster — Complete Design Brief

**Course:** B401 Continuous-Time Derivatives Pricing, University of Tübingen, Summer Term 2026  
**Poster title:** Portfolio Insurance and Structured Product Pricing on Rheinmetall AG  
**Output size:** A3 portrait, exactly 1 page  
**Brief version:** 1.0 (for handoff to designer or design AI)

---

## 1. Layout Wireframe

### Canvas dimensions

| Property | Value |
|---|---|
| Format | A3 portrait |
| Width | 297 mm |
| Height | 420 mm |
| Top margin | 5 mm |
| Bottom margin | 5 mm |
| Left margin | 8 mm |
| Right margin | 9 mm |

### Header band

| Property | Value |
|---|---|
| x | 8 mm |
| y | 5 mm |
| Width | 280 mm (full bleed to right margin) |
| Height | 30 mm |
| Background fill | Dark red #8B1A1A |
| Text colour | White #FFFFFF |

### Body area (below header)

| Property | Value |
|---|---|
| y start | 38 mm (header bottom + 3 mm gap) |
| Height available | 377 mm (420 − 38 − 5 bottom margin) |
| x start | 8 mm |
| Width available | 280 mm |

### Three-column grid

| | Column 1 (Part 1) | Column 2 (Part 2) | Column 3 (Part 3) |
|---|---|---|---|
| x start | 8 mm | 101 mm | 194 mm |
| Width | 88 mm | 88 mm | 88 mm |
| Gutter | — | 5 mm left of col | 5 mm left of col |

Thin vertical dividers (0.4 pt, colour #CCCCCC) separate columns at x = 99 mm and x = 192 mm.

---

## 2. Header Strip Content

Place all text within the 30 mm header band, vertically centred. Use a two-row layout:

**Top row (12 pt bold white, centred):**
> Portfolio Insurance and Structured Product Pricing on Rheinmetall AG

**Bottom row (9 pt white, centred):**
> Eberhard Karls Universitat Tubingen · Faculty of Economics and Social Sciences · Department of Finance · B401: Continuous-Time Derivatives Pricing — Summer Term 2026

**Top-left corner (flush left, stacked, 8 pt white):**
Line 1: `[Name] / [Matriculation Number]`  
Line 2: `Discussion partners: [Fellow student names]`

These two lines sit inside the header band, left-aligned, 4 mm from left edge, vertically centred within the band.

---

## 3. Typography Specification

| Element | Font | Size | Weight | Colour |
|---|---|---|---|---|
| Poster title (header) | Inter or Calibri | 12 pt | Bold | White |
| Institution line (header) | Inter or Calibri | 9 pt | Regular | White |
| Student / partner info | Inter or Calibri | 8 pt | Regular | White |
| Part label (col heading) | Inter or Calibri | 10 pt | Bold | Dark red #8B1A1A |
| Task heading | Inter or Calibri | 9.5 pt | Bold | Black #111111 |
| Body text | Inter or Calibri | 11 pt | Regular | Black #111111 |
| Table header row | Inter or Calibri | 9 pt | Bold | White on dark red |
| Table body cells | Inter or Calibri | 9 pt | Regular | Black |
| Graph captions | Inter or Calibri | 8 pt | Italic | Grey #555555 |

Line spacing: 1.15× for body text. Use single spacing within table cells.

If Inter is unavailable, substitute Calibri (Word) or Source Sans Pro (Google Docs). Avoid Times New Roman — the poster has too many numbers for a serif body.

---

## 4. Colour Scheme

| Purpose | Colour | Hex |
|---|---|---|
| Header background, part labels, table header fills | Dark red | #8B1A1A |
| Column dividers, table borders | Light grey | #CCCCCC |
| Body text, table cells | Black | #111111 |
| Graph captions, secondary text | Mid grey | #555555 |
| Page background | White | #FFFFFF |
| Accent (VaR limit line in graph, call-outs) | Tübingen gold | #C8A951 |

Use the dark red sparingly: header band, part-level headings, and table header rows only. Everything else is black on white to maximise legibility at A3 print size.

---

## 5. Graph Placement and Dimensions

Six of the eight available graphs are embedded. Two are replaced with compact tables to fit the column height constraint (see Section 9 for the column balance calculation).

**Graphs included (6):**

| Graph file | Task | Column | Vertical position in column | Width | Height | Caption |
|---|---|---|---|---|---|---|
| `payoff_profile.png` | III | 1 | Middle (below Task II text) | 88 mm | 62 mm | Fig. 1: Certificate vs direct stock payoff at maturity across three price zones. |
| `valuation_comparison.png` | V | 2 | Upper-middle (below Task V table) | 88 mm | 68 mm | Fig. 2: Daily EWMA model price vs DU2076 market price, Sep 2025 to Jun 2026. |
| `greeks.png` | VI | 2 | Middle-lower (below Task VI table) | 88 mm | 62 mm | Fig. 3: Delta, Gamma, Vega, Theta of DU2076 vs stock price S (central finite differences). |
| `mc_unhedged.png` | VIII | 3 | Upper (below Task VIII table) | 88 mm | 55 mm | Fig. 4: Simulated 1-year log-return distribution (50,000 GBM paths) with 95% VaR marked. |
| `insurance_heatmap.png` | IX | 3 | Middle (below Task IX table) | 88 mm | 65 mm | Fig. 5: 95% VaR (left) and mean return (right) across insurance fraction alpha and strike K. |
| `var_constraint.png` | XI | 3 | Bottom | 88 mm | 58 mm | Fig. 6: 95% VaR vs alpha at K = 95% × S0; regulatory 15% limit and optimal alpha* = 7.90% marked. |

**Graphs replaced by compact tables (2):**

| Graph file | Task | Replacement |
|---|---|---|
| `equity_fraction_vs_S.png` | VII | Two-sentence text summary (see Section 7, Task VII text) |
| `stress_scenarios.png` | X | Compact 4-row numeric table (see Section 7, Task X table) |

All six embedded graphs must be placed at no less than 88 mm width. At A3 print size, 88 mm width renders axis labels legibly. Do not scale below this threshold.

---

## 6. Word-for-Word Section Text

All text below is final draft copy for the poster. Do not add or remove sentences. Numbers match the assignment output.

---

### COLUMN 1 HEADING (Part 1 label)

**PART 1: DESIGNING CERTIFICATES**  
*(10 pt bold, dark red #8B1A1A, full column width, 4 mm below body top)*

---

#### Task I: Investor Profile

The target investor is a German retail saver aged 40 to 60, approaching retirement in 10 to 15 years. The investor holds pension-fund and real-estate positions and seeks a satellite equity stake in European defence, motivated by NATO budget commitments and Germany's Sondervermögen. Direct investment in RHM.DE carries annualised volatility of 54%, which exceeds the investor's stated risk ceiling. A capped capital-protected note provides structured equity participation while guaranteeing return of the nominal at maturity.

---

#### Task II: Product Design

**Product:** Capped Capital Protected Participation Note on Rheinmetall AG  
**Construction:** ZCB + 93.4% × [Call(K = EUR 1,207) − Call(K = EUR 1,569)]

Pricing at design date (S0 = EUR 1,207, T = 3 y, σ = 54.17%, r = 2.62%, q = 0.60%):

| Component | Value (EUR) |
|---|---|
| ZCB present value | 1,115.79 |
| ATM call (K = 1,207) | 451.04 |
| Cap call (K = 1,569) | 353.43 |
| Net call spread | 97.61 |
| Participation rate α | 93.4% |
| Max gain at cap (S_T ≥ 1,569) | 338.36 (+28.0%) |

The ZCB guarantees return of EUR 1,207 at maturity regardless of RHM performance. The bull call spread provides 93.4% participation in gains up to the 30% cap. The short cap call finances the higher participation rate by monetising the low probability of a gain above 130% of S0.

---

#### Task III: Product Payoff

The certificate outperforms direct stock in falling and flat markets and underperforms if RHM rises above EUR 1,384.

*(Insert Fig. 1: payoff_profile.png, 88 mm × 62 mm)*

**Three zones:**
- **Bearish (S_T < 1,207):** Certificate pays EUR 1,207 floor; stock pays S_T.
- **Moderately bullish (1,207 ≤ S_T ≤ 1,569):** Certificate pays 1,207 + 0.934 × (S_T − 1,207); outperforms stock below S_T ≈ 1,384.
- **Strongly bullish (S_T > 1,569):** Certificate is capped at EUR 1,569; stock pays S_T and wins.

---

#### Task IV: Market Size

Germany's structured products market totals EUR 112 bn (BSW 2023). Capital protection certificates account for 3.8%, or EUR 4.26 bn; participation products represent 55% of that segment, equalling EUR 2.34 bn across approximately 130 active issues with an average issue size of EUR 33 mn. The addressable market for a single-name, defence-themed capital protection note is estimated at EUR 200 to 300 mn.

---

### COLUMN 2 HEADING (Part 2 label)

**PART 2: VALUATION OF CERTIFICATES**  
*(10 pt bold, dark red #8B1A1A)*

**Product:** DU2076 Bonus Certificate with Cap on RHM.DE, issued by DZ BANK  
**Decomposition:** Down-and-Out Put + Capped Forward  
**Parameters:** B = EUR 1,050 (barrier), K = EUR 2,000 (cap/bonus), T ≈ 1.80 y, observation 4 Sep 2025 to 18 Jun 2027

*(This product description sits in a tinted box, 88 mm wide, 20 mm tall, light grey fill #F0F0F0, 8 pt text, immediately below the Part 2 heading)*

---

#### Task V: Valuation

CRR binomial tree (N = 200 steps) applied over 183 trading days (4 Sep 2025 to 1 Jun 2026). Daily ECB Svensson spot rate is matched to the remaining maturity each day. Two volatility models are compared: EWMA (λ = 0.94, mean 44.27%) and back-solved implied volatility (mean 37.77%).

| Metric | EWMA Model | Implied Vol Model |
|---|---|---|
| Mean Error (EUR) | -85.54 | -8.89 |
| MAE (EUR) | 94.49 | 9.82 |
| RMSE (EUR) | 108.92 | 12.37 |
| MAPE (%) | 6.11 | 0.64 |
| Mean vol used | 44.27% | 37.77% |

The EWMA model underprices DU2076 by EUR 85.54 on average (MAPE 6.11%) because EWMA overestimates realised volatility relative to the option-implied level. Switching to implied volatility reduces the error to EUR 8.89 (MAPE 0.64%), confirming the model structure is correct.

*(Insert Fig. 2: valuation_comparison.png, 88 mm × 68 mm)*

---

#### Task VI: Sensitivity (Greeks)

Greeks computed via central finite differences at: S = EUR 1,708, T = 1.79 y, σ = 44.6%, r = 2.14%.

| Greek | Reference value | Interpretation |
|---|---|---|
| Delta | 0.245 | Low: stock sits far above barrier; cert behaves like a capped forward |
| Gamma | ≈ 0.000 | Negligible at reference; spikes sharply near the barrier |
| Vega | -13.55 / pp | Negative: higher vol raises barrier-breach probability, destroying the bonus |
| Theta | +0.36 / day | Positive: time decay reduces knock-out risk, increasing cert value |

Negative Vega distinguishes the Bonus Certificate from vanilla options: investors are hurt by rising volatility rather than helped by it.

*(Insert Fig. 3: greeks.png, 88 mm × 62 mm. Note to designer: the sawtooth pattern visible in Gamma and Vega panels is a binomial tree discretisation artifact, not a data error.)*

---

#### Task VII: Replicating Portfolio

The replicating portfolio holds Delta × S in RHM.DE shares and the remainder in a risk-free bond. The equity fraction equals (Delta × S) / Certificate Value.

Near the barrier (S ≈ EUR 1,050), Delta rises sharply and the equity fraction exceeds 130%: the portfolio goes leveraged long equity to hedge the down-and-out put component. Far above the barrier, the equity fraction falls toward zero as the certificate behaves like a capped forward with bounded upside. If the barrier is breached, the put component vanishes and the cert converts to an unprotected capped forward with no capital floor.

---

### COLUMN 3 HEADING (Part 3 label)

**PART 3: PORTFOLIO INSURANCE STRATEGY**  
*(10 pt bold, dark red #8B1A1A)*

**Setup:** EUR 10,000 initial capital, T* = 1 year, underlying RHM.DE  
**GBM parameters:** S0 = EUR 1,207, μ = 54.05% p.a., σ = 39.88% p.a., r = 3.07% (10-y Svensson)  
**Simulation:** 50,000 paths × 252 steps, seed 2026

*(Product description in tinted box, same style as column 2)*

---

#### Task VIII: Performance without Risk Management

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

The log-return distribution is nearly symmetric (skewness = 0.007), consistent with GBM. With μ = 54.05%, 91.3% of paths end above S0 after one year.

*(Insert Fig. 4: mc_unhedged.png, 88 mm × 55 mm)*

---

#### Task IX: Performance with Risk Management

Portfolio: (1 − α) × stock + α × European put options priced via Black-Scholes (σ = 39.88%).  
Grid: α ∈ {5%, 10%, 15%, 20%}, K ∈ {90%, 95%, 100%, 105%} × S0.

| α | K | Mean return | Sharpe | 95% VaR |
|---|---|---|---|---|
| 5% | 95% S0 | 49.50% | 1.201 | 13.63% |
| 10% | 95% S0 | 44.66% | 1.105 | 16.00% |
| 10% | 100% S0 | 44.79% | 1.115 | 12.97% |
| 15% | 95% S0 | 39.49% | 0.990 | 16.07% |
| 20% | 95% S0 | 33.98% | 0.855 | 19.87% |

In a high-drift regime, VaR rises with α for most strikes: at the 5th percentile, RHM has typically risen and the puts expire worthless, so higher α means more premium spent with no offsetting payoff. Higher strikes (K = 100% S0) reduce VaR at a given α because the in-the-money put offsets the premium drag in bad scenarios.

*(Insert Fig. 5: insurance_heatmap.png, 88 mm × 65 mm)*

---

#### Task X: Stress Scenario Analysis

Allocation tested: α = 10%, K = 95% × S0.

| Scenario | Mean return | 95% VaR | 95% CVaR | P(loss) |
|---|---|---|---|---|
| Baseline | 44.66% | 16.00% | 16.79% | 13.7% |
| Vol +5 pp (to 44.88%) | 44.52% | 16.77% | 19.40% | 13.7% |
| Vol -5 pp (to 34.88%) | 44.84% | 13.62% | 14.73% | 13.7% |
| -20% price shock at T/2 | 24.82% | 17.07% | 17.70% | 29.8% |

The vol +5 pp scenario worsens VaR to 16.77%. Vol -5 pp is the only compliant scenario (VaR = 13.62%). The -20% mid-horizon shock collapses expected return to 24.82% and triples P(loss) to 29.8%, the largest single impact across all stress tests.

---

#### Task XI: Capital Requirement / VaR Constraint

Binding constraint: 95% one-year VaR ≤ 15%. Strike fixed at K = 95% × S0. The brentq root-finding algorithm solves VaR(α) = 0.15.

**Result: α* = 7.90%**

| Measure | Unhedged (α = 0) | Optimal (α* = 7.90%) |
|---|---|---|
| 95% VaR | 11.32% | 15.00% |
| Expected return | 54.03% | 46.73% |
| Sharpe ratio | 1.277 | 1.148 |

In this high-drift regime, VaR is an increasing function of α: put premiums are the dominant cost at the 5th percentile, and the unhedged position actually produces the lowest VaR (11.32%). α* = 7.90% is therefore the maximum permitted allocation, not a preferred target. Allocating above 7.90% violates the regulatory constraint.

*(Insert Fig. 6: var_constraint.png, 88 mm × 58 mm)*

---

## 7. Table Formatting Specification

Apply these rules to every table in the poster:

- **Header row:** white text on dark red (#8B1A1A) background, 9 pt bold
- **Body rows:** alternating white and very light grey (#F7F7F7), 9 pt regular
- **Borders:** 0.5 pt #CCCCCC horizontal lines only; no vertical borders except outer left/right 0.5 pt rule
- **Alignment:** numeric columns right-aligned; text columns left-aligned; header cells centred
- **Units:** state units in the column header (EUR, %, EUR/pp, EUR/day), not in every cell
- **Width:** span the full 88 mm column width
- **No placeholder cells.** Every cell contains a real number from the data above.

---

## 8. Graph Sizing Rationale

The minimum legible width for axis labels at A3 print size is 60 mm. All six embedded graphs are set at 88 mm width (the full column width), exceeding this threshold.

Two graphs are excluded:
1. **equity_fraction_vs_S.png** (Task VII): The key result is expressible in two sentences and one threshold value (equity fraction > 130% near barrier). A graph of this shape adds visual density without proportionate analytical value in the available space.
2. **stress_scenarios.png** (Task X): The four stress scenarios are fully quantified in the 4-row table. The return distribution overlap adds no number that is not already in the table.

The four non-negotiable graphs (payoff_profile, valuation_comparison, insurance_heatmap, var_constraint) are all retained at full column width.

---

## 9. Column Balance Check

Available body height per column: 377 mm.

### Column 1 content height estimate

| Block | Height |
|---|---|
| Part 1 heading | 8 mm |
| Task I heading + text (4 sentences) | 40 mm |
| Task II heading + text + 6-row table | 52 mm |
| Task III heading + 2-sentence text | 18 mm |
| Fig. 1 (payoff_profile, 88×62) + caption | 67 mm |
| Task III bullet zone list | 22 mm |
| Task IV heading + text (4 sentences) | 40 mm |
| Inter-task spacers (×4, 3 mm each) | 12 mm |
| **Total** | **259 mm** |

Column 1 sits comfortably within 377 mm. Use the remaining ~118 mm as generous white space between tasks and below Task IV, or extend the Part 1 intro text if the instructor requires more detail.

### Column 2 content height estimate

| Block | Height |
|---|---|
| Part 2 heading + product description box | 30 mm |
| Task V heading + text (2 sentences) | 16 mm |
| Task V 5-row error table | 30 mm |
| Fig. 2 (valuation_comparison, 88×68) + caption | 73 mm |
| Task VI heading + text (1 sentence) | 12 mm |
| Task VI 4-row Greeks table | 28 mm |
| Fig. 3 (greeks, 88×62) + caption | 67 mm |
| Task VII heading + text (4 sentences) | 38 mm |
| Inter-task spacers (×4, 3 mm each) | 12 mm |
| **Total** | **306 mm** |

Column 2 fits within 377 mm. Approximately 71 mm of whitespace available; distribute as 15 mm padding below each task.

### Column 3 content height estimate

| Block | Height |
|---|---|
| Part 3 heading + setup box | 30 mm |
| Task VIII heading + text (2 sentences) | 16 mm |
| Task VIII 8-row table | 32 mm |
| Fig. 4 (mc_unhedged, 88×55) + caption | 60 mm |
| Task IX heading + text (2 sentences) | 16 mm |
| Task IX 5-row compact table | 24 mm |
| Fig. 5 (insurance_heatmap, 88×65) + caption | 70 mm |
| Task X heading + text (2 sentences) | 16 mm |
| Task X 4-row stress table | 22 mm |
| Task XI heading + text (2 sentences) | 16 mm |
| Task XI 3-row result table | 18 mm |
| Fig. 6 (var_constraint, 88×58) + caption | 63 mm |
| Inter-task spacers (×5, 3 mm each) | 15 mm |
| **Total** | **398 mm** |

Column 3 is over budget by 21 mm. Apply the following to bring it to 377 mm:

- Reduce Task VIII table to 7 rows by merging Median into the Mean row as a parenthetical: saves 4 mm.
- Reduce Task IX compact table to 4 rows (drop the α=15%, K=95% row): saves 4 mm.
- Reduce inter-task spacers in column 3 from 3 mm to 2 mm: saves 5 mm.
- Reduce mc_unhedged height to 50 mm (still 88 mm wide, slightly less tall): saves 5 mm.
- Reduce insurance_heatmap height to 60 mm: saves 5 mm.
- Reduce body text line spacing in column 3 to 1.10× from 1.15×: saves ~3 mm.

Revised column 3 total: 398 − 26 = **372 mm**. Fits within 377 mm with 5 mm to spare.

---

## 10. Final Checklist for the Designer

Before sending to print, verify:

- [ ] All 6 graph images are embedded at 88 mm wide minimum
- [ ] No cell in any table contains "N/A", "TBD", or is blank
- [ ] Every graph has a caption directly beneath it (8 pt italic grey)
- [ ] The student name and matriculation number placeholder appears in the header top-left
- [ ] Discussion partner names appear below the student name in the header
- [ ] No body text falls below 11 pt
- [ ] The poster is exactly 1 page; no content overflows the bottom margin
- [ ] Column divider lines are 0.4 pt, not thick borders
- [ ] Table header rows use white text on dark red background
- [ ] The poster title in the header is centred and legible at normal reading distance (0.5 m)

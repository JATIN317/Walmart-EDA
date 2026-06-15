# Business Recommendations — Walmart Retail EDA

> Prioritised by execution speed and estimated revenue impact.
> Each is traceable to a specific analytical finding.

---

## Priority 1 — Launch VIP Win-Back for Retention Risk Segment (Fastest ROI)

**Trigger**: 73,285 customers misclassified as "Low Value" have median ticket $8,207 — above Champions $8,028 (Insight 4).

**Why first**: Requires CRM list + campaign creative. No capital expenditure. These customers already demonstrated premium purchasing power. The acquisition cost has already been paid.

**Actions**:

| Action | Detail |
|---|---|
| Reclassify segment | Rename "Low Value" → "Retention Risk" in CRM. Add per-item AIV column to segmentation logic. |
| Campaign message | Premium framing — not "come back for a discount." Position as exclusive access, new Category 1 launch, or loyalty recognition. |
| Target: second purchase | The goal is not a one-time win-back — it is triggering the second purchase, which is the inflection point for lifetime value growth. |
| A/B test | Run with a holdout group. Measure second-purchase rate in test vs control. Scale if conversion rate is statistically significant. |

**Success metric**: Second-purchase conversion rate in Retention Risk segment > holdout rate within 60 days.

**Opportunity size**: ~$120M at 20% conversion (estimate only — validate with A/B test before scaling budget).

---

## Priority 2 — Route Category 1 Inventory to Tier C / Deploy Upsell in Tier A (Medium Complexity)

**Trigger**: Tier C allocates 55% of top-category wallet share to Category 1 ($13.6k avg). Tier A allocates only 48% (Insight 2). Category 1 drives ~2× the transaction value of Categories 5 and 8.

**Why second**: Supply chain changes require planning lead time, but the revenue impact per unit sold is immediate once implemented.

**Actions**:

| Action | Tier | Detail |
|---|---|---|
| Deepen Category 1 stock | Tier C | Current 55% wallet share in Category 1 suggests demand already exists — stockouts are the primary risk in Tier C. Increase order depth. |
| Point-of-sale upsell | Tier A | Place Category 1 items at eye level. Add "customers also bought" prompts at checkout. Train staff on Category 1 benefits. |
| 90-day pilot | Tier A | Measure Category 1 wallet share shift from 48% baseline. If it moves to 50%+, the mechanism is placement, not demography. |
| Mapping table | Both | Requires actual category names from business before supply chain can execute. Abstract "Category 1" is not an operational instruction. |

**Success metric**: Tier A Category 1 wallet share moves from 48% → 51%+ within 90 days of placement change.

---

## Priority 3 — Freeze Tier A Expansion / Reallocate to Tier C (Longest Lead Time, Highest Long-Term Impact)

**Trigger**: Tier A has lowest MOV ($7,931) and lowest total revenue ($1.31B) despite metro cost premium (Insight 1). Big Spender cohort generates 6.8× revenue in Tier C vs Tier A (Insight 3).

**Why third**: Real estate decisions have long lead times and are irreversible in the short term. This requires a cost data overlay before confident action — this analysis is a directional signal, not a confirmed P&L conclusion.

**Actions**:

| Action | Detail |
|---|---|
| Freeze new Tier A locations | Hold until operating cost data confirms or disproves the margin inversion hypothesis |
| Cost audit | Overlay Tier A operating costs (lease, utilities, headcount) against transaction-level revenue. If cost-per-transaction exceeds Tier C by more than the revenue premium Tier A would need to justify, the thesis is confirmed. |
| Redirect Q3 marketing CapEx | Shift acquisition budget from Tier A to Tier C regions. The 6.8× Whale Multiplier is the ROI argument. |
| Mapping requirement | Tier A/B/C must be mapped to actual cities before real estate decisions can be made. |

**Success metric**: Cost audit delivers margin-per-transaction by tier within one quarter. If Tier A margin-per-transaction is confirmed below Tier C, freeze is extended and becomes a divestment review.

---

## Pre-requisites for Implementation

All three recommendations require resolving the mapping table dependency identified in the DQR:

| Mapping Required | Blocks |
|---|---|
| City Tier A/B/C → actual city names | CapEx reallocation, marketing budget decisions |
| Product Category 1/5/8 → actual product names | Inventory routing, upsell campaign creative |
| Occupation 1–20 → actual job roles | Demographic targeting refinement |

**These mappings are not analytical gaps — they are operational translation steps.** The analysis is directionally valid without them. Implementation requires them.

---

## Summary Table

| Priority | Action | Insight | Effort | Time to Revenue |
|---|---|---|---|---|
| 1 | VIP win-back for Retention Risk cohort | Retention Failure | Low | 30–60 days |
| 2 | Category 1 inventory routing + Tier A upsell | Product Cannibalization | Medium | 60–90 days |
| 3 | Tier A expansion freeze + Tier C CapEx shift | Metro Margin Trap + Whale Multiplier | High | 6–12 months |

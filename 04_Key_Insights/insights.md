# Key Insights — Walmart Retail EDA

> Framework: **Finding → Implication → Action**
> Every number is tied to a business decision.

---

## Insight 1: The Metro Margin Trap

**Finding**: Tier A (metro) generates the lowest Median Order Value ($7,931) and the lowest total revenue ($1.31B) — despite carrying the highest assumed operating costs.

**Implication**: The assumption that metro flagship stores are the margin engine of the business is likely wrong. We are subsidising premium real estate with our weakest ticket economics.

**Action**: Freeze Tier A expansion. Audit whether convenience transaction volume justifies per-sqft overhead before committing further CapEx to metro locations.

**Confidence level**: Directional — no cost data in this dataset. Requires cost overlay to confirm margin thesis.

---

## Insight 2: Product Mix Cannibalization

**Finding**: Tier A allocates 51% of top-category wallet share to lower-ticket Categories 5 & 8 ($6k–$7.5k). Tier C allocates 55% to premium Category 1 ($13.6k). Category 1 generates ~2× the transaction value of Categories 5 and 8.

**Implication**: The Tier A vs Tier C MOV gap is partly explained by product mix, not just customer quality. The same customers may convert to Category 1 if the store experience supports it.

**Action**: Route Category 1 inventory depth to Tier C. Deploy Category 1 upselling in Tier A — eye-level placement, cross-sell prompts at checkout. Measure wallet share shift over 90 days.

---

## Insight 3: The Whale Multiplier

**Finding**: The Big Spender segment (Low Frequency, High Monetary) generates $57.3M in Tier C vs $8.5M in Tier A — a 6.8× revenue multiplier for the identical behavioral cohort.

**Implication**: Tier C is the natural concentration point for the business's highest-value customers. Marketing budget allocated to Tier A acquisition is working against a 6.8× less favorable revenue base.

**Action**: Reallocate regional marketing budgets from Tier A acquisition to Tier C premium buyer acquisition. The magnitude of the multiplier makes this a capital allocation priority, not an optimisation.

---

## Insight 4: The Retention Failure

**Finding**: The "Low Value" CRM segment (73,285 customers) has a median ticket size of $8,207 after outlier adjustment — slightly exceeding Champions at $8,028. They are premium Category 1 buyers with purchasing power matching the business's best customers. They visit once or twice and do not return.

**Implication**: The CRM is misclassifying a large cohort of high-potential customers as low-value, causing them to receive low-priority retention treatment (or none). The business is losing premium customers it has already paid to acquire.

**Action**: Reclassify segment as "Retention Risk." Launch VIP win-back campaign — premium messaging, not discount-led. Second-purchase conversion is the trigger event that compounds lifetime value.

**Opportunity size**: ~$120M recoverable at 20% second-purchase conversion rate (order-of-magnitude estimate; requires cost data and A/B test to validate).

---

## Insight 5: The Lie of the Average

**Finding**: Mean spend = $9,263. Median spend = $8,047. Gap = $1,216 (13% overstatement).

**Implication**: Any strategy built on mean spend as "average customer value" is targeting a customer that does not exist. Marketing messages, minimum spend thresholds, and acquisition cost limits calibrated to $9,263 will miss the typical customer by over $1,200.

**Action**: Replace mean with median in all CRM reporting, KPI dashboards, and campaign calibration. Document the switch — this is not a minor formatting change, it changes which customers qualify for which campaigns.

---

## Non-Finding: Marital Status

**Finding**: AOV variance between single ($9,266) and married ($9,261) customers is under $5 across 550,000 records.

**Implication**: Marital status has no purchase behavior signal worth acting on at this scale.

**Action**: Remove from targeting criteria. Not every variable that exists in a dataset is worth segmenting on. Documenting non-findings is part of analytical completeness — it prevents wasted campaign budget on a demographic split that produces no behavioral difference.

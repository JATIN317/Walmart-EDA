# Insight 4: The Retention Failure (Outlier-Adjusted)

**Chart Type**: Combo Chart — Clustered Bars (User Volume) + Line (Median Ticket Size)
**Deck Position**: Slide 6

---

## The Data

| Segment | User Count | Median Ticket Size (Outlier-Adjusted) |
|---|---|---|
| Big Spenders | 6,958 | $11,939 |
| **Low Value** | **73,285** | **$8,207** |
| Champions | 459,573 | $8,028 |
| Frequent Shoppers | 10,252 | $7,052 |

---

## The Finding

The "Low Value" classification is wrong.

After stripping outliers and calculating median ticket size, the **Low Value segment's per-item spend ($8,207) slightly exceeds the Champions segment ($8,028)**. These are not cheap customers. They are **premium Category 1 buyers** who match the spending quality of our best customers — but were never retained past their first or second visit.

The CRM classification was built on **total cumulative spend**, not per-item value. Total spend = Frequency × Ticket Size. Champions accumulate high total spend through frequent purchases. Low Value customers accumulate low total spend because they visit rarely — not because they spend less per visit.

The formula error:
- Champions: High frequency × Moderate ticket = High total spend → labelled "Champion" ✓
- Low Value: Low frequency × High ticket = Low total spend → labelled "Low Value" ✗

The correct label for this segment: **Retention Risk** or **Unretained Premium Buyers**.

---

## Why This Only Emerged After Outlier Adjustment

Without outlier adjustment, the Low Value segment's average ticket was inflated by a small number of extreme high-ticket transactions — making it look inconsistent. After stripping those outliers and using median:

- The true central tendency of the segment became clear
- The comparison against Champions ($8,207 vs $8,028) became reliable
- The misclassification became visible

This is the direct consequence of the DQR decision to use median-based metrics throughout. Under mean-based analysis, this finding does not appear.

---

## Why a Combo Chart

The combo chart shows two variables simultaneously:
- **Bars**: User volume per segment — reveals that Champions (459,573 users) dwarf all other segments
- **Line**: Median ticket size — reveals that despite low user count, Low Value sits higher on the line than Champions

The crossing of the line (Low Value above Champions despite far fewer users) is the visual signal of the misclassification. A single-variable chart cannot show this.

---

## Churn Inference Limitation

Without a date column, "churned after 1–2 visits" cannot be confirmed — it is inferred from behavioral frequency. Low Frequency + High Spend = likely visited rarely and did not return. The most business-logical explanation is early-stage churn.

Two alternative explanations:
1. **Episodic buyer**: Visits once a year by nature, not by churn. A date column would distinguish annual buyers from one-time churners.
2. **New customer**: Recently acquired, not yet returned. Timestamps would show whether these customers are recent or long-tenured.

Either way, the first-to-second purchase conversion is the right intervention — it applies whether the customer is a churner, an episodic buyer, or a new acquisition.

---

## The Opportunity Size

73,285 customers × $8,207 median ticket = the addressable opportunity if even a fraction converts to a second purchase.

If 20% of this segment makes one additional purchase:
- 14,657 additional transactions × $8,207 = approximately **$120M in recoverable revenue**

This is an order-of-magnitude estimate only — it requires conversion rate assumptions and cost data to validate. But the scale signals this is a strategic priority, not a marginal optimization.

---

## Actions

- **Overhaul CRM classification**: Add per-item ticket size (AIV) as a segmentation axis alongside total spend. Reclassify the Low Value segment as "Retention Risk" or "Unretained Premium Buyers."
- **Launch VIP win-back campaign**: Target this cohort specifically — not with a generic coupon, but with premium messaging matching their Category 1 preference. They are price-insensitive buyers; a discount signals wrong brand positioning.
- **Measure second-purchase conversion**: Run as an A/B test with a holdout group. If the test group converts to a second purchase at a higher rate than holdout, scale immediately.
- **The second purchase is the conversion point**: In retail loyalty economics, the probability of a third purchase increases sharply after the second. Getting this segment to visit twice is not the end goal — it is the trigger that makes them Champions.

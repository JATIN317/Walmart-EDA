# S.C.A.N. Customer Profiling Matrix

**Deck Position**: Slide 7

The S.C.A.N. framework assigns each segment a **strategic role** — not just a label and demographics. A label tells you what the customer is. A strategic role tells you what to do about it.

---

## Segmentation Method

**Median-split 2×2 matrix** using Frequency and Monetary as axes.

```excel
=IF(AND(B4>=$B$1, C4>=$B$2), "Champions",
 IF(AND(B4<$B$1,  C4>=$B$2), "Big Spenders",
  IF(AND(B4>=$B$1, C4<$B$2), "Frequent Shoppers",
   "Low Value")))
```

Where `$B$1` = Median Frequency (54) and `$B$2` = Median Monetary (521,213).

**Why median split, not quartile split**:

Quartile segmentation produces four equal-sized groups of 25% each by construction. This is mechanically clean but has a business interpretation problem: calling the top 25% "Champions" is arbitrary — the threshold shifts every time the dataset changes, and the labels carry no stable meaning.

Median split is more defensible:
- The median frequency (54) and median spend (521,213) represent what a **typical customer** actually looks like
- Anyone above both thresholds is genuinely above-average on both dimensions — that is what "Champion" should mean
- With a right-skewed monetary distribution, quartile splits get distorted by the upper tail; the median is resistant to that distortion
- The `>=` operator means borderline customers at the exact median threshold are classified in the higher segment — a deliberate choice that gives borderline customers the benefit of the doubt

---

## Segment Profiles

### Champions
| Attribute | Detail |
|---|---|
| Median AOV | $8,028 |
| User count | 459,573 |
| Primary region | Tier B |
| Demographic | Males, Age 26–35 |
| Top category | Category 1 & 5 |
| **Strategic role** | **Volume Engine** |

High frequency, but median ticket diluted by Category 5 mix. These are the reliable core. The risk is over-indexing on this segment — their AOV is actually lower than both Big Spenders and Retention Risk customers.

**Campaign logic**: Retention and loyalty. Do not discount — they are already buying. Introduce new Category 1 products to lift ticket size.

---

### Big Spenders
| Attribute | Detail |
|---|---|
| Median AOV | $11,938 |
| User count | 6,958 |
| Primary region | Tier C |
| Demographic | Males, Age 26–35 |
| Top category | Category 1 |
| **Strategic role** | **Premium Revenue Drivers** |

The highest-value customers in the dataset. They live in low-cost Tier C operational regions — which means they generate the strongest margin profile of any segment. Small in count but outsized in revenue contribution.

**Campaign logic**: Premium exclusives, early product access, new launches. They are price insensitive. Discounts are brand-diluting for this segment. The Tier C concentration ($57.3M) vs Tier A ($8.5M) is the 6.8× Whale Multiplier finding.

---

### Frequent Shoppers
| Attribute | Detail |
|---|---|
| Median AOV | $7,051 |
| User count | 10,252 |
| Primary region | Tier C |
| Demographic | Males, Age 26–35 |
| Top category | Category 5 |
| **Strategic role** | **Upsell Candidates (Volume Drags)** |

High foot traffic, low basket size. These customers visit often but spend the least per transaction. They generate store traffic without the ticket size that justifies the cost of serving them at premium locations.

**Campaign logic**: Cross-sell Category 1 at point of purchase. If one in five Frequent Shoppers adds a Category 1 item per visit, the segment's ticket climbs toward Champions territory. This is the upsell test — measure incrementally, not via blanket promotion.

---

### Retention Risk (formerly "Low Value")
| Attribute | Detail |
|---|---|
| Median AOV | $8,207 |
| User count | 73,285 |
| Primary region | Tier C |
| Demographic | Males, Age 26–35 |
| Top category | Category 1 |
| **Strategic role** | **Retention Target** |

Misclassified as "Low Value" by total cumulative spend. After outlier adjustment and median-based profiling, their per-item ticket ($8,207) slightly exceeds Champions ($8,028). These are premium Category 1 buyers who demonstrated strong purchasing power and then did not return.

**Campaign logic**: VIP win-back. Premium messaging (not discount-led). The second purchase is the conversion trigger — once a customer buys twice, lifetime value compounds. Priority 1 action in this dataset.

---

## Technical Appendix: Demographic Baseline

| Finding | Data |
|---|---|
| Dominant age bracket | 26–35 (219,587 users) |
| Highest-median age bracket | 51–55 (Median ticket $9,534) — **underserved by current marketing** |
| Gender split | 75.31% Male / 24.69% Female |
| Top occupation | Occupation 4 (72,308 users) |
| Marital status impact | Negligible — under $5 AOV variance (non-factor, excluded from targeting) |

**Age bracket note**: Marketing captures the 26–35 volume bracket but misses the 51–55 bracket — which carries the highest median ticket in the dataset ($9,534 vs $8,047 overall). This is not an actionable finding without knowing what Occupation 4 and Age 51–55 represent in real-world terms (mapping table required), but it is a signal worth investigating.

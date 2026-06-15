# Methodology Decisions — Walmart Retail EDA

> This document explains the key analytical choices made in this project and the reasoning behind each one. These decisions distinguish the analysis from a standard EDA output.

---

## Decision 1: DQR Before Any Analysis

**What**: The first analytical output was a Data Quality Review (Slide 2 of the deck) — before any insight slide.

**Why**: Data quality constraints determine what an analysis can and cannot claim. Building insights before checking the data means you may be building on false assumptions. The three hazards found in the DQR (missing date column, right-skewed data, masked categoricals) shaped every methodological choice that followed.

**What would have gone wrong**: Without the DQR, any claim about cohort retention or churn would have been methodologically unsound — the dataset has no date column. The DQR creates a documented, pre-emptive answer to "can you do X with this data?"

---

## Decision 2: Median Over Mean for All Unit Economics

**What**: All segment profiling, tier comparisons, and unit economics use **Median Order Value**, not mean.

**Why**: The purchase amount distribution is right-skewed (Mean $9,263 vs Median $8,047 — a $1,216 gap). In right-skewed data, the mean is pulled upward by high-ticket outliers and misrepresents the typical customer. Reporting mean spend tells stakeholders their average customer spends $9,263 — which is false for the typical transaction.

**What would have gone wrong**: The Retention Failure insight depends entirely on median-based ticket comparison. Under mean-based analysis, the Low Value segment still appears low value. The finding that their per-item spend rivals Champions ($8,207 vs $8,028) only emerges when outlier distortion is removed.

**Implementation**: Median was calculated per segment using Excel's MEDIAN function on the Purchase Amount column after grouping by segment label.

---

## Decision 3: Median-Split Segmentation Instead of Quartile Split

**What the bootcamp specified**: Four segments using quartile splits of Frequency and Monetary (25th, 50th, 75th percentile boundaries — four groups of 25% each).

**What was done instead**: Single median split on both dimensions — creating a 2×2 matrix with four behavioural quadrants.

```excel
=IF(AND(B4>=$B$1, C4>=$B$2), "Champions",
 IF(AND(B4<$B$1,  C4>=$B$2), "Big Spenders",
  IF(AND(B4>=$B$1, C4<$B$2), "Frequent Shoppers",
   "Low Value")))
```

Where `$B$1` = Median Frequency (54), `$B$2` = Median Monetary (521,213).

**Why**:

| Quartile Split | Median Split |
|---|---|
| Four equal 25% groups by construction | Four groups of variable size based on actual data distribution |
| "Champions" = top 25%, arbitrary | "Champions" = above-median on both dimensions, interpretable |
| Threshold shifts every time dataset changes | Threshold is the stable population median |
| No clear business action per group | Each quadrant maps directly to a distinct campaign strategy |

With a right-skewed monetary distribution, quartile splits are distorted by the upper tail. The median is resistant to that distortion.

The `>=` operator in the formula is deliberate: customers exactly at the median threshold are classified in the higher segment, giving borderline customers the benefit of the doubt.

---

## Decision 4: Outlier Adjustment for the Retention Failure Insight

**What**: When profiling the Low Value segment, outliers were stripped before calculating median ticket size.

**Why**: The raw segment average for Low Value customers was inflated by a small number of anomalous high-ticket transactions. Without removing these, the segment's true central tendency was obscured. After outlier stripping, the median ticket emerged as $8,207 — revealing it slightly exceeds Champions at $8,028.

**What would have gone wrong**: Without this step, the Low Value segment looks exactly like its label — cheap customers. The Retention Failure insight disappears entirely. The entire strategic opportunity (73,285 misclassified premium buyers) becomes invisible.

**Outlier method**: IQR method — values below Q1 − 1.5×IQR or above Q3 + 1.5×IQR were flagged as statistical outliers. High-ticket outliers in the upper tail were stripped from the median calculation for this specific comparison. They were not removed from the dataset — they represent real customer behavior.

---

## Decision 5: Document the Non-Finding

**What**: Marital status was explicitly tested as a segmentation variable and documented as a non-factor. AOV variance between single ($9,266) and married ($9,261) cohorts is under $5.

**Why this matters**: Analytical completeness means reporting what you looked for and did not find — not just positive results. This protects the business from allocating campaign budget to a demographic split that carries no behavioral signal.

Most analysts only report findings. Reporting non-findings is what separates a careful analyst from a pattern-matcher.

---

## Decision 6: S.C.A.N. Framework — Strategic Roles, Not Just Labels

**What**: Each segment was assigned a **strategic role** in addition to a demographic profile.

| Segment | Strategic Role |
|---|---|
| Big Spenders | Premium Revenue Drivers |
| Champions | Volume Engine |
| Frequent Shoppers | Upsell Candidates |
| Retention Risk | Retention Target |

**Why**: A segment label tells an executive what the customer is. A strategic role tells them what to do about it. A consulting deliverable always ends in action — a student report ends in description.

The strategic role determines which campaign type, which messaging, and which budget allocation applies to each group. Without the role, the segmentation is decorative.

---

## Statistical Concepts Applied

| Concept | Where Applied | Why It Mattered |
|---|---|---|
| Right skew detection | DQR → all unit economics | Mean-median gap of $1,216 required switching to median; directly changed segmentation findings |
| IQR outlier method | Retention Failure insight | Stripping outliers revealed Low Value segment's true $8,207 median ticket |
| Central Limit Theorem | Segment AOV comparisons | At 550,000 records, all segment means are stable, reliable population estimates — not noise |
| Correlation (conceptual) | Tier C vs AOV, Category 1 vs spend | Identified geographic and product mix relationships; documented confounding variable risk |
| Non-finding documentation | Marital status analysis | AOV variance under $5 across 550k records — explicitly removed from targeting |

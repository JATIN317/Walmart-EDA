# Data Quality Review (DQR) — Walmart Retail EDA

> The DQR was completed before any analysis. It is Slide 2 of the executive deck — before the first insight slide. This sequencing is intentional: data quality constraints determine what the analysis can and cannot claim.

## Dataset Profile

| Attribute | Value |
|---|---|
| Total records | 550,068 transaction rows |
| Null values | 0 (100% complete) |
| Data grain | 1 item per user per row |
| Date column | ❌ Not present |

## Critical Business Hazards

### Hazard 1: Missing Temporal Dimension

**What it means**: The dataset has no date or timestamp column.

**What it prevents**:
- Cohort retention analysis (grouping customers by acquisition period and tracking drop-off)
- Churn modeling (confirming whether low-frequency customers churned or buy episodically)
- Seasonality detection (identifying peak purchase periods for campaign timing)
- Purchase velocity analysis (how quickly do Champions return vs other segments?)

**How the analysis adapted**: All retention observations are inferred from cross-sectional frequency (number of transactions per User ID), not observed over time. The "Low Value / Churned" label is a behavioral inference — Low Frequency + High Spend = likely churned premium buyer. Timestamps would confirm or reject this.

**What validation would look like**: A single date column would enable building a cohort retention curve — group customers by first purchase month, measure percentage returning in month 2, 3, 4. That curve would confirm whether the Retention Failure insight describes early churn or episodic buying.

---

### Hazard 2: Right-Skewed Unit Economics

**What it means**: Purchase amount is not normally distributed. It has a long right tail — most customers spend at moderate levels, but a small cohort of very high-ticket buyers pulls the mean upward.

| Metric | Value |
|---|---|
| Mean spend | $9,263 |
| Median spend | ~$8,047 |
| Gap | $1,216 (13% overstatement) |

**What it prevents**: Reporting mean spend as "average customer value" — this describes a customer that doesn't exist. The typical customer spends $8,047, not $9,263.

**How the analysis adapted**: All segment profiling, unit economics, and tier comparisons use **Median Order Value (MOV)**. This is not a cosmetic choice — it directly changed the segmentation findings. The Retention Failure insight (Low Value MOV $8,207 vs Champions MOV $8,028) only emerges after switching to median. Under mean-based analysis, the Low Value segment still appears low value.

**Outlier handling**: Rather than removing high-ticket outliers from the dataset, the analysis uses median-based metrics throughout so outliers do not distort segment comparisons. This is the correct approach when outliers represent real customer behavior, not data entry errors.

---

### Hazard 3: Abstract Categoricals

**What it means**: Two key segmentation variables are masked:
- **City Category**: A, B, C — no city names available
- **Occupation**: 1–20 — no role labels available

**What it prevents**: Naming specific cities in recommendations, identifying occupational segments by job type.

**How the analysis adapted**: All geographic analysis uses the A/B/C tier framework as-is. Tier C is identified as the high-efficiency geography from data behavior — the business must apply its own mapping to identify which actual cities this covers.

**What implementation requires**: A mapping table translating Tier A/B/C → actual city names, and Occupations 1–20 → actual job categories. Without this, no recommendation in this analysis can be operationalised at the field level.

---

## Variables Overview

| Variable | Type | Notes |
|---|---|---|
| User_ID | Categorical | Unique per customer |
| Gender | Binary | 75.31% Male / 24.69% Female |
| Age | Ordinal | Brackets: 0-17, 18-25, 26-35, 36-45, 46-50, 51-55, 55+ |
| Occupation | Categorical | Masked (1–20) |
| City_Category | Categorical | Masked (A/B/C) |
| Stay_In_Current_City_Years | Ordinal | 0, 1, 2, 3, 4+ |
| Marital_Status | Binary | 0 = Single, 1 = Married |
| Product_Category | Categorical | 1–20 (masked) |
| Purchase | Continuous | Right-skewed; use median |

## Non-Factor Variables (Tested and Eliminated)

**Marital Status**: AOV variance between single ($9,266) and married ($9,261) is under $5. This is statistically negligible across 550,000 records. Marital status was explicitly tested and removed from targeting recommendations. Not every variable in a dataset is worth acting on.

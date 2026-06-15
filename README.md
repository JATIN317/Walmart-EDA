## Deliverables

- Technical EDA Analysis
- Business Recommendations
- Executive Presentation Deck

### Executive Deck

[View Executive Deck](07_Executive_Deck/walmart_executive_deck.pdf)

# Walmart Retail Performance Audit & Strategic Segmentation

## Business Problem

550,068 transaction records. A standard EDA would report averages, chart top categories, and label four customer segments. This project treated the data as a **revenue strategy audit** — asking not "what does the data show?" but "what lever is the business failing to pull?"

The result: a retention failure hiding inside a misclassified customer segment, a metro store structure with inverted unit economics, and a 6.8× revenue multiplier sitting in an underinvested geography.

## Dataset

| Attribute | Detail |
|---|---|
| Records | 550,068 transaction rows |
| Grain | 1 item per user per row |
| Data health | Zero nulls |
| Key constraint | No date/time column — cohort and churn analysis not possible |
| Variables | User ID, Gender, Age, Occupation (masked 1–20), City Category (A/B/C), Marital Status, Product Category, Purchase Amount |

## What This Project Did Differently

| Dimension | Standard Approach | This Project |
|---|---|---|
| Data quality | None documented | Full DQR — 3 critical business hazards identified before any analysis |
| Central tendency | Mean everywhere | Median-first with documented outlier justification |
| Segmentation method | 4 quartile buckets | Median-split 2×2 matrix — stable, interpretable business boundaries |
| Segmentation output | 4 labels + demographics | S.C.A.N. matrix with strategic roles per segment |
| Insight framing | "Tier A has lowest revenue" | "Metro Margin Trap — premium rent for weakest unit economics" |
| Counterintuitive finding | None | 'Low Value' segment outspends Champions per item after outlier adjustment |
| Limitation handling | None | Temporal gap, masked variables, and skew all documented upfront |

## Analysis Performed

| Insight | Finding |
|---|---|
| Metro Margin Trap | Tier A (metro) generates lowest median order value ($7,931) despite highest operating costs |
| Product Cannibalization | Tier A wallet share diluted by low-ticket Categories 5 & 8; Tier C concentrates 55% in premium Category 1 ($13.6k) |
| Geographic Segmentation Anomaly | Same behavioral cohort produces 6.8× more revenue in Tier C ($57.3M) vs Tier A ($8.5M) |
| Retention Failure | "Low Value" segment median ticket ($8,207) exceeds Champions ($8,028) after outlier adjustment — misclassified premium buyers |
| Non-finding | Marital status — AOV variance under $5; documented and removed from targeting |

## Key Business Insights

- **The Metro Margin Trap**: We are subsidising premium metropolitan real estate with our weakest transaction economics. Tier C suburban stores outperform Tier A by $654 in median order value per transaction.
- **The Retention Failure**: 73,285 customers classified as "Low Value" are actually premium buyers who never returned. Their median ticket ($8,207) exceeds Champions ($8,028). The CRM label is wrong — these are not cheap customers, they are unretained customers.
- **The Whale Multiplier**: The identical behavioral segment (low frequency, high spend) generates 6.8× more revenue in Tier C than Tier A. The business is underinvesting in the geography that best captures its most valuable customers.
- **The Lie of the Average**: Mean spend ($9,263) overstates the typical customer by $1,216 vs median ($8,047). Every strategic decision built on mean spend is directionally wrong for the typical customer.

## Recommendations

- **Freeze Tier A expansion**: Audit whether convenience volume justifies metro real estate overhead before opening new Tier A locations.
- **Route Category 1 inventory to Tier C**: Tier C customers concentrate 55% of top-category spend in premium Category 1. Tier A needs upsell mechanics, not more premium inventory.
- **Launch VIP win-back for the "Low Value" cohort**: These 73,285 customers are premium buyers who churned. A second-purchase conversion campaign is the highest-ROI action in this dataset.
- **Reclassify CRM segments**: Add per-item ticket size as a segmentation axis. Total spend alone misclassifies high-ticket low-frequency buyers as low value.

## Statistical Methods Used

`Exploratory Data Analysis` `Right-Skew Detection` `Median vs Mean Analysis` `Outlier Detection (IQR Method)` `FM Segmentation` `Median-Split 2×2 Matrix` `Correlation Analysis` `Central Limit Theorem Application` `Distribution Analysis`

## Tools Used

- Python (Pandas, Matplotlib, Seaborn)
- Excel (Pivot Tables, Nested IF segmentation formula, Conditional Formatting)
- PowerPoint (Executive deck — 8-slide audit format)

---

> **Project Summary (for job boards):**
> Conducted a 550,000-row retail EDA on Walmart transaction data, identifying a misclassified customer segment whose median ticket size exceeded core Champions after outlier adjustment, a metro store structure with inverted unit economics (Tier A lowest MOV despite highest costs), and a 6.8× geographic revenue multiplier in Tier C. Applied median-first methodology, DQR-led data validation, and median-split FM segmentation to generate three capital reallocation recommendations.

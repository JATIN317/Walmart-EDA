# Business Context — Walmart Retail Performance Audit

## Project Framing

Most EDA projects on retail data answer: *"Who buys what, and how much?"*

This project answered: *"Where is the business destroying value it thinks it is creating — and where is value sitting uncaptured?"*

That reframe changes what you look for, what you report, and what you recommend.

## Business Pain Points

| Pain Point | Business Question |
|---|---|
| Geographic efficiency | Are metro stores actually the profit engine — or is that assumption wrong? |
| Customer misclassification | Is the CRM labelling the right customers as high-value? |
| Campaign misdirection | Is marketing budget going to the right geography and segment? |
| Product mix | Are lower-ticket products displacing higher-margin categories in high-cost stores? |
| Retention blind spot | Are premium buyers churning undetected because of how segments are defined? |

## The "Revenue Audit" Mindset

> "What lever is the business trying to pull — and is it pulling the right one?"

Standard framing: *"Champions are our best customers."*
Revenue audit framing: *"Are our Champions actually our best customers, or just our most frequent ones?"*

That question is what exposed the Retention Failure insight — after outlier adjustment, the "Low Value" segment outspent Champions per item.

## Dataset Constraints That Shaped the Analysis

Three constraints were identified during the Data Quality Review and documented before any insight work:

| Constraint | Impact on Analysis |
|---|---|
| No date column | Cohort decay and churn modeling are impossible. Retention is inferred from cross-sectional frequency, not observed over time. |
| Right-skewed purchase distribution | Mean spend overstates the typical customer by $1,216. All unit economics standardised to median. |
| Masked categoricals | City tiers (A/B/C) and occupations (1–20) have no real-world labels. All recommendations require a mapping table before implementation. |

These are not limitations discovered after the fact — they were identified in Slide 2 of the deck, before any insight slide. That sequencing is deliberate.

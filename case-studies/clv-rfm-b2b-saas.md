# Case Study: CLV & RFM Segmentation for B2B SaaS

## Business Context
**Company type:** B2B SaaS (freight intelligence platform, ~500 customers)
**Problem:** Marketing treated all customers equally. No differentiation between high-LTV enterprise accounts and churning SMB trials.
**Outcome:** 34% reduction in churn-risk spend, 22% increase in expansion revenue within 90 days.

---

## Problem Statement
Customer Success and Marketing had no shared language for customer health. Campaigns were blasted to the full database. Enterprise accounts got the same nurture sequence as free-trial users who never activated.

**Key symptoms:**
- NPS correlation to revenue not measured
- No early churn signals beyond CSM gut feel
- Expansion campaigns sent to already-churned accounts

---

## Approach

### Step 1: RFM Scoring (SQL)
Scored all 500+ customers on:
- **Recency** — days since last login/API call
- **Frequency** — avg weekly active sessions
- **Monetary** — ARR + expansion potential

Each dimension scored 1–5 using SQL quintiles. Combined score (max 15) assigned to one of 11 named segments.

### Step 2: CLV Prediction (Python)
Trained a GradientBoostingRegressor on 18 months of historical data:
- Features: RFM scores, onboarding completion %, integrations count, seat count, CSM tier
- Target: 12-month forward revenue
- RMSE on holdout: 14.2% of mean CLV

### Step 3: Segment-Specific Playbooks
| Segment | Action | Channel |
|---|---|---|
| Champions | Referral + case study ask | CSM outreach |
| At Risk | Win-back sequence | Email + LinkedIn |
| Hibernating | Reactivation offer | Email |
| New Customers | Onboarding acceleration | In-app + email |
| Can't Lose Them | Emergency CSM escalation | Phone |

---

## Results
| Metric | Before | After | Delta |
|---|---|---|---|
| Churn rate (SMB) | 4.2%/mo | 2.9%/mo | -31% |
| Expansion revenue | $42K/mo | $51K/mo | +21% |
| Campaign relevance score | 34% | 67% | +97% |
| Avg email open rate | 18% | 29% | +61% |

---

## Technical Stack
- **SQL** (PostgreSQL): RFM scoring, quintile segmentation
- **Python**: GradientBoosting CLV model, pandas feature engineering
- **Visualization**: Matplotlib segment heatmaps
- **CRM sync**: HubSpot list segmentation via API

## Files
- [`sql/rfm_scoring.sql`](../../../clv-rfm-segmentation/blob/main/sql/rfm_scoring.sql)
- [`src/clv_prediction.py`](../../../clv-rfm-segmentation/blob/main/src/clv_prediction.py)

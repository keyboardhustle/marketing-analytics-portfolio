# Case Study: Multi-Touch Attribution for Paid Channels

## Business Context
**Company type:** B2B SaaS (~$2M ARR, Series A)
**Problem:** $80K/month across Google Ads, LinkedIn Ads, Meta Ads. Last-click attribution showed Google as the top performer — but pipeline analysis told a different story.
**Outcome:** 28% improvement in CAC efficiency by reallocating budget based on Markov Chain attribution.

---

## Problem Statement
The VP of Marketing had a classic attribution blindspot: last-click showed Google Search converting 68% of pipeline. LinkedIn looked expensive and underperforming.

But Customer Success anecdotes suggested LinkedIn was where enterprise buyers first discovered the product. Last-click was hiding the assist.

**Core questions:**
1. Which channels actually initiate pipeline (first touch)?
2. Which channels close it (last touch)?
3. What's the true contribution of each channel across the full journey?

---

## Approach

### 6 Attribution Models Implemented
| Model | Logic | Best For |
|---|---|---|
| First Touch | 100% to first channel | Brand awareness measurement |
| Last Touch | 100% to last channel | Close-to-revenue correlation |
| Linear | Equal split across all touches | Simple team reporting |
| Position-Based | 40/20/40 (first/mid/last) | Balanced view |
| Time Decay | Exponential weight to recent | Short sales cycles |
| Markov Chain | Probabilistic removal effect | Statistical accuracy |

### Markov Chain Findings
Using transition probability matrix across 1,200 customer journeys:
- LinkedIn: +31% removal effect vs. last-click credit
- Meta Retargeting: +18% vs. last-click
- Google Brand: -12% (over-credited)
- Google Non-Brand: consistent across models

---

## Budget Reallocation
| Channel | Before | After | ROAS Before | ROAS After |
|---|---|---|---|---|
| Google Search | $45K | $38K | 3.2x | 3.4x |
| LinkedIn Ads | $20K | $28K | 1.8x | 2.6x |
| Meta Retargeting | $15K | $14K | 2.1x | 2.3x |

**Net result:** Same $80K budget, +28% pipeline generated within 60 days.

---

## Technical Stack
- **Python**: 6-model attribution engine, Markov Chain transition matrices
- **SQL**: Funnel query joining ad spend to CRM opportunities
- **Data sources**: Google Ads API, LinkedIn Campaign Manager export, HubSpot CRM

## Files
- [`src/channel_attribution.py`](../../../paid-channel-performance-analysis/blob/main/src/channel_attribution.py)
- [`sql/channel_funnel.sql`](../../../paid-channel-performance-analysis/blob/main/sql/channel_funnel.sql)

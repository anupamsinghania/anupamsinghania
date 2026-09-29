# KPI Framework & A/B Experiment Analysis: New Onboarding Flow

**Business question:** Should the redesigned onboarding experience be launched to all users?

**Recommendation:** Yes. Roll out the new onboarding flow and keep monitoring refund rate, support ticket rate and engagement score.

**Tools:** Python (Pandas, NumPy, SciPy), Google Colab, Microsoft Excel, GitHub
**Skills shown:** A/B testing, hypothesis testing, KPI framework design, data validation, segment analysis, business recommendation

---

## Key Findings

| Metric | Control | Treatment |
|---|---|---|
| Paid Conversion Rate | 3.19% | 7.04% |

- Test: independent two-sample Welch's t-test, one-tailed, alpha = 0.05
- Result: t = 3.291, p = 0.001, so the null hypothesis is rejected
- Sample: 1,400 unique users after removing 8 exact duplicate records

---

## Business Problem

A subscription-based digital product company wants more users to become paying customers without hurting customer experience. An A/B experiment compared the existing onboarding flow (Control) with a redesigned flow (Treatment). Leadership needs statistical evidence and business impact before deciding on a full rollout.

---

## Dataset

**File:** `data/campaign_experiment_data.xlsx`

<!-- Add the data source here, for example "Course-provided sample dataset, BITS School of Management". Confirm the dataset is allowed to be public. -->

User-level fields: User ID, Signup Date, Experiment Group, Region, Device Type, Traffic Source, Plan Type, Landing Page Visits, Trial Starts, Onboarding Completion, Paid Conversion, Revenue (30 Days), Support Tickets, Refund Requests, Days to Convert, Engagement Score.

---

## Methodology

1. **Data validation:** checked missing values and duplicate User IDs, removed 8 exact duplicates, confirmed binary fields contain only 0 and 1, reviewed revenue for outliers, checked segment distribution, standardized Signup Date to DD-MM-YYYY.
2. **KPI framework:** defined a North Star metric, driver metrics, supporting metrics and guardrails (below).
3. **Experiment analysis:** compared Control and Treatment on all KPIs, then by Region, Device Type and Traffic Source.
4. **Hypothesis test:** Welch's t-test on Paid Conversion.
5. **Recommendation:** rollout decision with guardrail monitoring.

---

## KPI Framework

**North Star Metric:** Paid Conversion Rate. It measures the share of users who become paying customers after onboarding, so it ties directly to subscription growth and recurring revenue.

| Layer | Metrics |
|---|---|
| Primary drivers | User Acquisition, User Activation, Monetization |
| Supporting metrics | Landing Page Visit Rate, Trial Start Rate, Onboarding Completion Rate, Average Revenue per User, Average Revenue per Converted User |
| Guardrail metrics | Refund Rate, Support Ticket Rate, Engagement Score |

![KPI tree](screenshots/kpi_tree_preview.png)

---

## Results

![Summary metrics](screenshots/summary_metrics.png)

**Hypotheses**

- H0: No difference in Paid Conversion Rate between Control and Treatment.
- H1: Treatment has a higher Paid Conversion Rate than Control.

| Metric | Value |
|---|---|
| Control Paid Conversion Rate | 3.19% |
| Treatment Paid Conversion Rate | 7.04% |
| T-statistic | 3.291 |
| P-value | 0.001 |

![Hypothesis test output](screenshots/hypothesis_test_output.png)

<!-- Add the guardrail results here from outputs/experiment_summary.xlsx, using only your real values:

### Guardrail Metrics
| Metric | Control | Treatment |
|---|---|---|
| Refund Rate | | |
| Support Ticket Rate | | |
| Average Engagement Score | | |

### Segment Findings
One or two sentences on what the Region, Device Type and Traffic Source analysis showed.
-->

---

## Business Recommendation

Roll out the Treatment onboarding flow. Paid Conversion Rate rose from 3.19% to 7.04%, and the difference is statistically significant (t = 3.291, p = 0.001). After launch, keep tracking Refund Rate, Support Ticket Rate and Engagement Score so higher conversion does not come at the cost of customer satisfaction or revenue quality.

---

## Assumptions

- Duplicate User IDs were exact duplicates and were removed.
- Binary variables contained only 0 or 1.
- Users were randomly assigned to Control and Treatment.
- The dataset accurately reflects user behaviour during the experiment period.

## Limitations

- The analysis covers only the provided dataset.
- Seasonality and marketing campaigns were not considered.
- Statistical significance does not guarantee the same result in future.
- Long-term retention was outside the scope of this experiment.

---

## Repository Structure

```
kpi-framework-experiment-analysis/
├── data/          campaign_experiment_data.xlsx
├── analysis/      experiment_analysis.xlsx, hypothesis_test_notes.md
├── outputs/       experiment_summary.xlsx, kpi_tree.png, recommendation_memo.md
├── screenshots/   summary_metrics.png, hypothesis_test_output.png, kpi_tree_preview.png
└── README.md
```

<!-- Add the Google Colab notebook (.ipynb) to the repository and list it here, for example notebooks/experiment_analysis.ipynb -->

---

## Contact

Anupam Singhaniya | Junior Business Analyst | Ghaziabad / Delhi NCR
[LinkedIn](https://www.linkedin.com/in/anupam-singhaniya/) | anupamsinghania0157@gmail.com

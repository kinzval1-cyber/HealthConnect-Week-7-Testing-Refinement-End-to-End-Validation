# HealthConnect – Week 7: Testing, Refinement & End-to-End Validation

## Project Overview

Week 7 focused on testing and validating the analytical outputs developed during Week 6.

Rather than repeating the previous analysis, the goal was to verify that key KPIs, analytical findings, dashboard functionality, and cross-track conclusions remained reliable and suitable for decision support.

---

## Week 7 Objectives

- Validate important Week 6 KPIs
- Check analytical findings against the underlying data
- Test dashboard filters and calculations
- Investigate unexpected or inconsistent results
- Refine analytical interpretations where necessary
- Validate findings across different segments
- Conduct cross-track testing with Data Science
- Document testing results, decisions, limitations, and remaining issues

---

## Testing & Validation

### 1. KPI Validation

The key dashboard KPIs were independently checked using Power BI calculations.

| KPI | Validated Result | Status |
|---|---:|---|
| No-Show Rate | 48.45% | PASS |
| Attendance Rate | 46.27% | PASS |
| Reminder Effectiveness | 4.03% | PASS |
| High-Risk No-Show Rate (2+ previous no-shows) | 61.02% | PASS |
| Long Lead-Time No-Show Rate (>45 days) | 68.09% | PASS |

All five KPIs returned the expected results.

---

## 2. Previous No-Shows Validation

The Week 6 finding that previous no-shows are associated with higher no-show rates was retested.

| Previous No-Shows | No-Show Rate |
|---:|---:|
| 0 | 43.51% |
| 1 | 53.49% |
| 2 | 59.36% |
| 3 | 67.95% |
| 4 | 66.67% |
| 5 | 100.00% |

The overall pattern remained consistent: patients with more previous no-shows generally showed higher no-show rates.

**Result: PASS**

This supports the use of previous attendance behaviour as an important risk indicator.

---

## 3. Booking Lead-Time Validation

The Week 6 analysis showed a strong relationship between booking lead time and no-show rate.

The validated total no-show rates across the lead-time bands were:

- 30.60%
- 43.04%
- 52.82%
- 67.16%
- 68.09%

The overall pattern remained consistent, with no-show rates increasing substantially at longer booking lead times.

**Result: PASS**

The finding remains useful for stakeholder-facing risk interpretation.

---

## 4. Distance × Reminder Validation

The distance, previous no-shows, and reminder analysis was also retested.

The overall pattern remained consistent, although higher-distance segments showed greater variability and smaller sample sizes.

**Result: PASS**

Distance is therefore retained as a **supporting risk indicator**, rather than being treated as the primary intervention or predictive factor.

---

## 5. Dashboard Usability Testing

The Week 5 dashboard filters were tested to ensure that they responded correctly.

Tested slicers:

- Gender
- Appointment Day
- Appointment Time
- Appointment Type

All four slicers functioned as expected.

**Result: PASS**

No dashboard functionality issue requiring correction was identified.

---

# Cross-Track Validation: Data Analytics × Data Science

A key part of Week 7 was validating whether analytical findings also provided additional predictive value.

The Data Science track compared three approaches:

1. Raw `booking_lead_days`
2. Raw `booking_lead_days` + lead-time bands
3. Lead-time bands alone

Cross-validation showed that accuracy and ROC-AUC were practically identical across the approaches.

### Finding

The lead-time bands clearly communicate the increase in no-show risk at longer booking intervals, particularly the risk increase after 45 days.

However, the bands did **not** provide meaningful additional predictive performance compared with raw booking lead days.

### Decision

The lead-time bands were retained for **stakeholder interpretation and communication**, while raw booking lead days remain appropriate for predictive modelling.

This distinction helped separate:

**Descriptive / business value**  
from  
**Predictive modelling value**

---

## Refinement

One wording refinement was made to the Week 6 analytical page.

### Before

> Greater distance ↑

### After

> Greater distance ↑ (supporting indicator)

This change reflects the testing results and avoids presenting distance as a stronger predictive factor than the evidence supports.

![week7](20%week7.png)

---

# Key Validated Findings

### 1. Previous No-Shows

Previous no-show behaviour remains an important indicator of future appointment attendance risk.

### 2. Booking Lead Time

Longer booking lead times are associated with substantially higher no-show rates.

The lead-time bands are particularly useful for communicating this pattern to stakeholders.

### 3. Distance

Greater distance can provide supporting context for attendance risk, but the relationship is more variable at higher distances.

### 4. Reminders

Reminder status remains relevant when examining no-show behaviour, particularly among patients with previous no-shows. However, observed relationships should be interpreted as associations rather than causal effects.

---

# Business Implications

Based on the validated findings:

- Patients with previous no-shows can be considered for targeted reminder and confirmation strategies.
- Appointments booked far in advance may benefit from additional confirmation closer to the appointment date.
- Distance can be considered when investigating potential accessibility or attendance barriers.
- Lead-time bands can help stakeholders understand and communicate risk patterns even though they did not improve predictive model performance.

---

# Limitations

- Some high-distance and high previous-no-show segments contain relatively small sample sizes.
- The analysis identifies associations and does not establish causation.
- Lead-time bands improve interpretability but did not improve predictive performance.
- Further validation with new appointment data would be required before operational deployment.

---

# Week 7 Outcome

Week 7 moved the HealthConnect project from analysis toward validated decision support.

The testing process confirmed the reliability of the major KPIs and Week 6 findings, validated dashboard functionality, and introduced an important distinction between findings that improve business interpretation and features that improve predictive performance.

The cross-track validation with Data Science helped ensure that analytical findings were not automatically treated as modelling features without testing their actual predictive contribution.

---

## Tools Used

- Microsoft Power BI
- Power Query
- DAX
- Excel
- Python / Data Science modelling workflow
- GitHub

## Project Progression

**Week 5:** Exploratory Analysis & Dashboard  
→ **Week 6:** Advanced Analytics & Decision Support  
→ **Week 7:** Testing, Refinement & End-to-End Validation  
→ **Week 8:** Solution Readiness & Next Steps

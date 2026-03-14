# nps-cohort-analysis
NPS cohort and segment analysis using SQL and product analytics concepts

## Objective
Analyze Net Promoter Score (NPS) one month after signup to understand trends by cohort and user segment.

## Dataset
Anonymized CRM and survey data used for analytical practice.
## Dataset Structure

The analysis is based on two main tables:

### users
| column | description |
|------|-------------|
| user_id | Unique identifier for each user |
| created_at | Date when the user signed up |
| role | User type (Admin or Regular) |

### surveys
| column | description |
|------|-------------|
| user_id | User who answered the survey |
| surveyed_at | Date when the survey was completed |
| score | NPS score (0–10) |

Users were grouped into **cohorts based on signup month**, and NPS was calculated **one month after signup** to measure early satisfaction.

## Methodology
- Defined cohorts based on signup month
- Calculated NPS = %Promoters – %Detractors
- Segmented users by role (Admin vs Regular)
- Analyzed trends over time and by segment

## Key Findings
- Admin users consistently show higher NPS than regular users.
- Overall NPS declined due to a change in user composition.
- The decreasing proportion of Admin users lowered aggregate NPS.

## Business Insight
Improving the experience of Regular users could significantly improve overall NPS.

## Tools
- SQL
- Python (Jupyter Notebook)
- Data analysis and visualization
## Example SQL Logic

```sql structure
SELECT
  DATE_TRUNC(created_at, MONTH) AS cohort_month,
  COUNT(user_id) AS users_in_cohort
FROM users
GROUP BY cohort_month
ORDER BY cohort_month;

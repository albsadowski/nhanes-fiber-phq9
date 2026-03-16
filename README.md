# Dietary Fiber Intake and Depression Severity in U.S. Adults

Survey-weighted ordinal logistic regression analysis of the association between dietary fiber intake and PHQ-9 depression severity using NHANES 2021-2023 data.

## Key Findings

- **Fully adjusted OR 0.89 per 1 SD fiber increase (p = 0.012)** — ordinal model captures a spectrum-wide association that binary (depressed/not) models miss (binary OR 0.93, p = 0.284)
- Monotonic dose-response across quartiles: Q2 0.69, Q3 0.63, Q4 0.60 (all p < 0.01)
- Strongest symptom-level associations: anhedonia (OR 0.72) and sleep disturbance (OR 0.87)

## Methodology

| Element | Detail |
|---------|--------|
| Data | NHANES 2021-2023 (N ≈ 3,400 adults ≥ 18) |
| Outcome | 5-level ordinal PHQ-9 severity (None / Mild / Moderate / Mod. Severe / Severe) |
| Model | `svyolr` (survey-weighted proportional odds) via R `survey` package |
| Exposure | Total dietary fiber (g/day) from two 24-hour recalls |
| Covariates | Age, sex, race/ethnicity, education, income, BMI, smoking, alcohol, physical activity, energy intake |
| Scaling | All continuous predictors centered and scaled (z-scored) for numerical stability |

Progressive covariate adjustment: crude → demographics → fully adjusted (including total energy intake).

## Running

Open `nhanes_fiber_phq9.Rmd` in RStudio and knit. NHANES data files are downloaded automatically on first run to `.data/`.

### Dependencies

R packages: `haven`, `dplyr`, `tidyr`, `survey`, `MASS`, `splines`, `ggplot2`, `knitr`, `DiagrammeR`

## Outputs

- `cohort_flow_ordinal.pdf` — cohort selection flowchart
- `dose_response_ordinal.pdf` — RCS and linear dose-response curves
- `symptom_forest_ordinal.pdf` — forest plot of per-symptom associations

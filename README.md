# GHG Emissions — Bayesian Multilevel Modeling

Group project (3 members) for an Applied Bayesian Statistics course. Team: Sviatoslav Naumov, Fuad Mahamed, Fabio Pugno.

**My contribution**: primary responsibility for model comparison, best-model interpretation, and RMSE evaluation (Q4–Q6), with additional review and refinement across the team's modeling and diagnostics work.

## Task

Model company-level Scope 1 greenhouse gas emissions (300 observations: 100 of the world's largest companies, 2022–2024) as a function of revenue, sector, country, and national renewable-energy share.

## Approach

- **Models**: three Bayesian multilevel regressions (`brms`), differing in their grouping structure — varying intercepts by sector only, by sector + country, and by sector with year as a population-level effect
- **Likelihood**: switched from Gaussian to lognormal after a prior sensitivity analysis showed the Gaussian models were a poor fit for positive, right-skewed emissions data
- **Model checking**: prior sensitivity analysis (`priorsense`) and posterior predictive checks (`bayesplot`) for every model
- **Model comparison**: 10-fold cross-validation, models compared on the log-score (ELPD via `loo`), confirmed on a held-out test set
- **Result**: the sector + country model was selected; variance decomposition shows emissions are driven mainly by sector (~66%) and country (~23%), with revenue contributing very little once those are accounted for

## Files

- `g3_ABMpv5.Rmd` — full analysis source
- `g3_ABMpv5.html` — rendered report with all output and plots

## Data

[GHG Emissions and Finance — Global Companies 2022–2024](https://www.kaggle.com/datasets/hussnainmamoon1/ghg-emissions-and-finance-global-companies-2022-2024) (Kaggle). Not redistributed here — download from the source above.

## Tech stack

R, brms, bayesplot, priorsense, loo, dplyr, ggplot2

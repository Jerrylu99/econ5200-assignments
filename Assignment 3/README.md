# ECON 3916 Assignment 3 – Causal Inference

This project explores several causal inference techniques using simulated and observational data. The goal is to distinguish correlation from true causal effects and address issues such as skewed distributions and selection bias.

## Phase 1: Bootstrap Inference

In the first phase, a zero-inflated tip distribution is simulated to represent gig-economy driver tips. Because the data are heavily skewed and contain many zeros, standard parametric inference may not work well. A manual bootstrap procedure with 10,000 resamples is implemented to estimate the sampling distribution of the median and construct a 95% confidence interval.

## Phase 2: Permutation Test for A/B Testing

In this phase, simulated A/B testing data are generated to evaluate the effect of a new routing algorithm on delivery time. Since the treatment group contains extreme outliers, a non-parametric permutation test is used instead of a standard t-test. The permutation distribution is generated using 5,000 random shuffles to calculate the empirical p-value.

## Phase 3: Propensity Score Matching (PSM)

This phase analyzes an observational dataset related to a loyalty program ("SwiftPass"). A naive comparison suggests that subscribers spend significantly more than non-subscribers. However, this difference may be driven by selection bias. Propensity scores are estimated using logistic regression based on pre-treatment covariates, and nearest-neighbor matching is used to estimate the Average Treatment Effect on the Treated (ATT).

## Phase 4: Love Plot Visualization

Finally, a Love Plot is used to evaluate covariate balance before and after matching. Standardized Mean Differences (SMD) are calculated for key covariates, and the plot visually demonstrates that matching improves balance between treated and control groups.

## Tools Used

- Python  
- NumPy  
- Pandas  
- Scikit-learn  
- Matplotlib  
- Seaborn

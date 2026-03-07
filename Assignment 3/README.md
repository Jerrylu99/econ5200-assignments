# ECON 3916 Assignment 3 – Causal Inference

This project analyzes causal effects in an observational logistics dataset using several econometric techniques.

## Methods

1. Bootstrap inference for non-parametric uncertainty
2. Permutation test for A/B testing
3. Propensity Score Matching (PSM) to correct for selection bias
4. Love Plot visualization to evaluate covariate balance

## Key Findings

The naive difference in means suggests that loyalty program subscribers spend significantly more than non-subscribers. However, after applying propensity score matching, the estimated treatment effect becomes smaller, indicating that part of the observed difference was due to selection bias.

The Love Plot shows that the covariate balance improves substantially after matching, providing visual evidence that the matching procedure reduces selection bias.

## Tools

Python, NumPy, Pandas, Scikit-learn, Matplotlib, Seaborn

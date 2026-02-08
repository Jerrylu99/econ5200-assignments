# Audit 02: Deconstructing Statistical Lies
**Assignment 2 – The Algorithmic Audit (ECON 3916)**

## Overview
This project audits algorithmic metrics that appear “perfect” on the surface but hide statistical distortions underneath.  
Across four phases, I demonstrate how **averages, accuracy, and experimental balance can systematically mislead** when data is skewed, rare, or selectively observed.

---

## Phase 1: Robustness Audit — Latency
**Task:** Evaluate whether mean latency is reliable in a skewed system.

- Simulated 1,000 requests with rare latency spikes
- Implemented **Median Absolute Deviation (MAD)** manually
- Compared MAD with Standard Deviation (SD)

**Result:**  
- MAD remains stable (~7.5 ms)  
- SD explodes due to outliers (~428 ms)

**Conclusion:** Mean-based metrics are unreliable in heavy-tailed systems.

---

## Phase 2: Probability Audit — False Positives
**Task:** Audit a detector claiming 98% accuracy using Bayes’ Theorem.

Tested three base-rate scenarios:
- 50% → P(Cheater | Flagged) ≈ 98%
- 5% → ≈ 72%
- 0.1% → ≈ 4.7%

**Conclusion:** In low-prevalence settings, most positive flags are false positives.  
Accuracy alone is a misleading metric.

---

## Phase 3: Bias Audit — Sample Ratio Mismatch (SRM)
**Task:** Validate a 50/50 A/B test assignment.

- Observed: 50,250 vs. 49,750 users
- Chi-square statistic: χ² = 2.5
- Critical value (α = 0.05): 3.84

**Conclusion:** No statistically significant SRM detected.  
Experiment assignment appears valid.

---

## Phase 4: AI Expansion — Survivorship Bias
**Task:** Simulate survivorship bias in crypto markets.

- Simulated 10,000 token launches using a Pareto distribution
- Compared all tokens vs. top 2% survivors

**Result:**  
- Mean (All tokens): ~1.7M  
- Mean (Survivors only): ~29.0M  
- Bias multiplier: ~16.6×

**Conclusion:** Excluding failed assets inflates perceived performance by more than an order of magnitude.

---

## Final Insight
Across all cases, **“perfect” metrics emerge only when critical data is ignored**.  
Robust analysis requires distributional awareness, base-rate reasoning, and inclusion of failures.

---

## Tools
Python, NumPy, Pandas, Matplotlib, Seaborn

## Reproducibility
Random seeds are set to ensure reproducible and auditable results.

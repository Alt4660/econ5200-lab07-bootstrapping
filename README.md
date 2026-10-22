# econ5200-lab07-bootstrapping

Objective: I tested when nominal 95% confidence intervals fail to cover the true value, and what fixes them.

Methodology
- Bootstrapped the median of 32,561 integer ages and looked at the standard error and at what BCa returned.
- Simulated skewed data (n = 50, 400 experiments) and measured the coverage of nominal 95% parametric and bootstrap intervals for both the mean and the median.
- Bootstrapped wages from 25 firms as if the workers were independent, then compared that to resampling whole firms (a cluster bootstrap).
- Used a bootstrap_utils.py module with percentile, i.i.d. and cluster bootstrap functions.
- Had an AI write a coverage function, revised my prompt once, and checked its output against my own coverage numbers.

Key Findings
- Degenerate bootstrap: The median of the 32,561 integer ages had a bootstrap SE of 0. BCa returned nan with a warning instead of an interval.
- Coverage on skewed data (nominal 95%):
  - Mean: parametric 92.5%, bootstrap 92.0%.
  - Median: parametric 66.8%, bootstrap 92.8%.
- Clustered wages: Treating workers from 25 firms as independent gave an interval 5.7x too narrow, with 19.5% coverage. Resampling whole firms brought coverage to 91.0%.
- AI check: The AI-written coverage function matched my own coverage numbers exactly (naive 19.5% vs 19.5%, clustered 91.0% vs 91.0%).

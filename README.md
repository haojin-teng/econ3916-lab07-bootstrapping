# Estimation & Bootstrapping — Quantifying Uncertainty Without a Formula

## Objective
I measured the uncertainty of estimates from the UCI Adult Census Income data with CLT-based intervals and the bootstrap, and tested how often each kind of interval covers the true value.

## Methodology
- Loaded the UCI Adult Census Income data (32,561 respondents).
- Separated the standard deviation of the data from the standard error of an estimate, and checked the s/√n relationship across four sample sizes.
- Built parametric confidence intervals from the CLT and compared how quickly it converges for age and for capital gains.
- Ran the bootstrap by hand, then with `scipy.stats.bootstrap`.
- Bootstrapped the standard error of the median age.
- Compared percentile and BCa intervals on a heavily skewed variable.
- Bootstrapped a two-sample difference in mean weekly hours.
- Asked an AI to write a bootstrap-interval function, revised my prompt once, and checked the function against my own intervals.
- Ran a coverage simulation on lognormal data at n = 50 for the mean and the median.

## Key Findings
- The CLT converges quickly for age and slowly for capital gains.
- The bootstrap SE of the median of 32,561 whole-number ages is exactly 0.0000. With that many ties the median is pinned, so every resample returns the same value. The bootstrap is reporting a real property of the data, not failing.
- For the mean, the nominal 95% parametric interval covered [YOUR VALUE]% and the percentile bootstrap covered [YOUR VALUE]%. The gap is inside the Monte Carlo standard error of about 1.3 points, so I can't tell the two methods apart here. Both under-cover slightly.
- For the median, the mean-centred parametric interval covered only about [YOUR VALUE]%, while the bootstrap stayed near its nominal 95%.

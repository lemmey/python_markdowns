___
[[testing & errors]]
#test 
___
Use when you have one measurement variable and one nominal variable. 

The nominal variable has only two values, like Male/Female or Site_A/Site_B.

It tests whether the means of the measurement variable are different in the two groups .
___
The test statistic t:
Gets larger as the means get farther apart, the variances get smaller, or the sample sizes increase

DoF = (Group 1 n + gr. 2 n) - 2
___
Assumptions:
* Null=Equal means
* Normality
* Homoscedasticity (equal variances in the two groups)
___
If sample sizes (>10) are similar for both groups the test is resilient to heteroscedasticity. -> USE Welch‘s-t #test for groups with strongly different SD‘s.

Not at all sensitive to assumptions of normal distribution

If the two groups have completely different distributions (left skewed vs. Right skewed) transformations or non-parametrics wont help, consider lowering p-value.

Test is identical for One-way ANOVA.
___
#statstrick
Non-parametric alternative Mann-Whitney U- #test only, if instead of a measurement variable you have a true ranked variable. Even if distributions are shaped different and non-normal this MWU-test would not perform better than parametric alternatives.
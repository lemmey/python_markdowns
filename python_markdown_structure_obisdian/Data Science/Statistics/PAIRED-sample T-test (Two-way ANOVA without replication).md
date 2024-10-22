___
[[testing & errors]]
#test 
___
Use when there is one measurement variable and two nominal variables. 

One of the nominal variables has only two values, so that you have multiple pairs of observations (e.g. a species abundance compared between a pair of sites...also among more sites).
___
The test statistic t:
Is used in a one-sample t-test of the prior calculated differences to compare mean differences to 0.
___
Assumptions:
* Null hypothesis: Mean difference between pairs is zero
* Normality of difference between pairs (normality of residuals?)
* Homoscedasticity is not assumed for the paired t-test
___
#statstrick 
If the two sets of measurements are correlated with each other, the paired t–test will be more powerful than a two-sample t–test

A paired t-test can only be used if there is just one observation for each combination of the two-level nominal variable. -> USE Two-way ANOVA with replication for more than one observation.

Also, use two-way ANOVA, if you're interested in testing both null hypotheses (equality of means of the two treatments and equality of means of the individuals

If residuals are non-normal —> USE: Wilcoxon‘s signed-rank #test .
___
[[testing & errors]]
___
## I. Assumption of Independence

*Non-independent observations can make your statistical test give too many false positives.*

Example: By observation, coral species on reef A are generally bigger than those on reef B. 
If we test one species X only on reef A against specimen found only on reef B, I naturally will have a naturally inflated chance for false positive, so to find a significant relation within size, because the location might actually a determining factor/proxy for size. 

Example 2: Comparison between new born size of African- and Indian elephants is very species dependent)

Considering independence in biology is mostly a matter of knowing your target organisms/systems and adjusting the research design accordingly.

#statstrick Use a nested ANOVA, to treat the dividing variable as a second nominal variable.
___
Regression and correlation assume that observations are independent. If one of the measurement variables is #time, or if the two variables are measured at different times, the data are often non-independent. 
However, there are tests especially for that case of a time-series.

___
## II. Assumptions of equal variance

*Parametric tests assume equal SDs (as measure for variance) for data of different groups.*

If this is not the case the chance for false positive, #type1 error, is increased, thus greater than the desired alpha level.
Heteroscedasticity is less a problem if groups have similar to equal sample size.

Consider data transformations before using a non-parametric test. And test for heterogeneity to see the effect of different transformations.
In other cases, heterogeneity in the SDs might be the variable of interest to compare between groups!

In any case to identify differences in variance use:

* Barlett‘s #test
* Levenes #test
___

### One– and two tailed assumptions

One-tailed probability testing is more powerful, since two-tailed testing increases the chance for a #type2 error (false negative). 

Still, using one-tailed tests might require proper justification as alpha levels are more easily achieved.
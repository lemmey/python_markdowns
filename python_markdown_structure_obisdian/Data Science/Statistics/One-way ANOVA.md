___
[[testing & errors]]
#test 
___
Use when there is one measurement variable and one nominal variable (with two or more groups). 

You make multiple observations of the measurement variable for each group of the nominal variable. Frequency of observations can vary, but one-way ANOVA is most safe for a balanced design.
___
The test statistic F:
Is the ratio of the variance among means divided by the average variance within groups.

Dof= among-group degrees of freedom is, number of groups -1 . 

The within-groups degrees of freedom is the total number of observations, - the number of groups.  Dof are usually reported for the  F statistics.
___
Assumptions:

* Null=Equal means of the measurement variable among groups
* Normality (or close)
* Homoscedasticity (non-sensitive in a balanced design)
___
#statstrick 
If normality of residuals is off, transform.

If none of the transformations work, you can use Kruskal-Wallis #test. However, this assumes a similar shape of distribution and that it doesn't test the same null hypothesis. #statstrick: use one-way anova even with non-normal data (if transformation does not work), but tend to only accept very small p-values.

USE: less powerful Welch‘s ANOVA for large deviations in the SDs and for unbalanced designs.
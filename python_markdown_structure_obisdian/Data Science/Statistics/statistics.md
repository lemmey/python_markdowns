___
[[descriptive analysis]]
[[inferential analysis]]
___
## Classical statistics

**Relies largely on probability statistics (p-value).**

Generally about, whether the statistical inferred rejection/acceptance justifies the biological rejection/or acceptance of a hypothesis.
## Bayesian 

Bayesian statistics and ‘prior/varying probabilities‘

Other indicators include effect sizes and confidence intervals, which should be put into perspective parallel to p-values.
___
## Hypothesis testing

___
## Testing Variables

### Nominal (e.g. Gender, blood type)

Relation to: qualitative, discrete, categorical data

Often summarized as proportions or percentage, nominal data might only resemble measurement data if measured e.g. as 50% branching coral and 50% massive coral. However, the variable of interest, the observation that has been made here is growth form. In  statistics I would compute with the n-amount of branching observed vs. the n-amount of massive ones observed.
___
### Ranked

'You could do a lifetime of biology and never use a true ranked variable'

This could be data with a natural order from e.g. lowest to highest, without knowing the actual values. Also in social science, subjective data is commonly ranked (e.g. Likert-Scale).

#statstrick
Note: A common use of ranked data is to downgrade/rank continuous data for assuming fewer statistical assumptions on the data and then use non-parametric tests instead.
___
### Interval/Measurement (length, weight, pH, counts)

Most tests theoretically assume continuous data (possibly taking any values depending on the precision of the measurement method/equipment). 

However computation also works with discrete data, unless there are too few observations for which it becomes nominal/binary data
(usually >6 observations).
___
### Ratios

When comparing ratios of two measurement variables, e.g. comparing the ratio of two or more genera of coral live-tissue to diameter instead of each separate, note that this would assume a linear relation. Meaning that the ratio would be the same for all coral sizes. Check by relating the two variables to one another and see whether the regression line is hitting close to an origin intercept (min. values).
___
### Categorizing

Measurement —> Categorical

E.g. based on a range.  This reduces statistical power, so decreasing chances of finding a relationship between the variables if there is in fact one (or increasing the chance for a Type II error). 
Categorizing biological measurement data also yields problems in analysis, since tests might be ambiguous to different sub-divisions.
___
### Confounding variables, collinearity and covariate analysis

*A confounding variable/factor, next to the independent variable, affects the behaviour of a dependent variable.* 

This is the reason why correlation seldom describes causation. To avoid false conclusions over the effect of an independent variable, research designs should be build on principals of randomization or should include blocking or a control.

### Controlling confounding variables (research design)

Expose/accept confounding factors to/for all researched units in the same amount the further.
In some cases you can simply control for confounding factors by creating a ratio variable. E.g. if one wants to ascertain the effect of coral diameter on the corals volume, coral height is a confounding factor, so one could create a ratio already relating both to one another (Or take 3D surface area which is related to height inherently).

### Randomization

Meaning all picked samples are proportionally under the same influence of confounding factors (e.g. assign Id numbers and let a non-human decide the picks) and have the same chance of ending up in the sample.
Differentiate between pseudo-randomization and true random sampling.

### Matching

### Controls


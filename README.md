# Hypothesis_Testing

Let us consider a subset of the survey responses from users who identified as Data Scientists from Stack-overflow survey.

Hypothesizing about the mean:

Let's hypothesize that the mean annual compensation of the population of data scientists is 110,000 dollars. Hypothesize mean = 110,000$
We can initially examine the mean annual compensation from the sample survey data by using np.mean().The result is different from our hypothesis, but is it meaningfully different?

Since variables have arbitrary units and ranges, before we test our hypothesis, we need to standardize the values. A common way of standardizing values is to subtract the mean, and divide by the standard deviation. Since variables have arbitrary ranges and units, we need to standardize them. For example, a hypothesis test that gave different answers if the variables were in Euros instead of US dollars would be of little value. Standardization avoids that.

For hypothesis testing, we use a variation where we take the sample statistic, subtract the hypothesized parameter value, and divide by the standard error. The result is called a z-score.

Hypothesis testing use case:
Determining whether sample statistics are close to or far away from expected(hypothesized) values.

Plot of the probability density function for the standard normal distribution, which is a normal distribution with mean of zero and standard deviation of one. It's often called the z-distribution, and z-scores are related to this distribution.

The z-score is a standardized measure of the difference between the sample statistic and the hypothesized statistic

df['column'].std(ddof=1) 
- ddof: delta degrees of freedom

Hypothesis Testing:

Hypothesis tests compare two competing hypotheses. 

These two hypotheses are the 

null hypothesis (Ho) --> representing the existing idea, and 

alternative hypothesis (Ha) --> representing a new idea that challenges the existing one. 

The tails of a distribution are the left and right edges of its PDF. 

Hypothesis tests determine whether the sample statistics lie in the tails of the null distribution, which is the distribution of the statistic if the null hypothesis was true. 

There are three types of tests, 

1. If we are checking for a difference compared to a hypothesized value, we look for extreme values in either tail and perform a two-tailed test.
2. If the alternative hypothesis uses language like "less" or "fewer", we perform a left-tailed test.
3. Words like "greater" or "exceeds" correspond to a right-tailed test.

**P Values:**

p-values measure the strength of support for the null hypothesis, or in other words, they measure the probability of obtaining a result, assuming the null hypothesis is true.

Large p-values mean our statistic is producing a result that is likely not in a tail of our null distribution.

Small p-values mean our statistic is producing a result likely in the tail of our null distribution. Because p-values are probabilities, they are always between zero and one.

**Calculating p value:**

We pass the z-score to the standard normal CDF, norm.cdf, from scipy.stats with the default values of mean zero and standard deviation of one. 

For right-tail test, the p-value is calculated by taking one minus the norm.cdf result. 

P value = norm.cdf(z_score, loc = 0, scale=1) --> for left tail test
P value = 1 - norm.cdf(z_score, loc = 0, scale=1) --> for right tail test 

p-values quantify how much evidence there is for the null hypothesis. 

Large p-values indicate a lack of evidence for the alternative hypothesis, sticking with the assumed null hypothesis instead. 

Small p-values make us doubt this original assumption in favor of the alternative hypothesis. 

What defines the cutoff point between a small p-value and a large one? --> Significance level (alpha)

The cutoff point is known as the significance level, and is denoted alpha. The appropriate significance level depends on the dataset and the discipline worked in. 
Most common choices for alpha are 0.1, 0.05 and 0.01.

If p <= alpha --> We reject null hypothesis 
   p< alpha --> We fail to reject null hypothesis.
It's important that we decide what the appropriate significance level should be before we run our tests.

Types of Errors:

Type I: If we support the alternative hypothesis when the null hypothesis was correct, we made a false positive error. 

Type II: If we support the null hypothesis when the alternative hypothesis was correct, we made a false negative error. 

**T-tests:**

In the above example we considered only annual compensation and found the hypothesis.
T-tests is used if there are two groups.
for example- considering annual compensation and the age data scientists started coding (child or adult) from the example mentioned above: 
We have a smaller sample size.
The population standard deviation is unknown.
Used to determine whether there is a significant difference between the means of two groups.

Hypothesis: 

H0: The null hypothesis is that the population mean for the two groups is the same, and 
H0: population mean of child = population mean of adults 
    population mean of child - population mean of adults = 0

Ha: the alternative hypothesis is that the population mean for users who started coding as children is greater than for users who started coding as adults
Ha: population mean of child > population mean of adults 
    population mean of child - population mean of adults > 0

In the two sample case, 

the test statistic(t) : We take the difference between the sample statistics for the two groups, subtract the population difference between the two groups, then divide by the standard error.

Calculating p-values from t-statistics:

The test statistic, t, follows a t-distribution. t-distributions have a parameter called the degrees of freedom,df.

As we increase the degrees of freedom, the t-distribution gets closer to the normal distribution. 
In fact, a normal distribution is a t-distribution with infinite degrees of freedom. 
Degrees of freedom are defined as the maximum number of logically independent values in the data sample.

df = n(first group) + n(second group) - 2

P value = t.cdf(t_stat, df=degrees_of_freedom) --> for left tail test (We use t distribution here instead of norm)
P value = 1 - t.cdf(t_stat, df=degrees_of_freedom) --> for right tail test

**Paired t tests**

For paired analyses, rather than considering the two variables separately, we can consider a single variable of the difference.

pingouin.ttest()

**Anova test** (Analysis of Variance)

Used to compare more than two groups.ANOVA tests determine whether there are differences between the groups.
We use the pingouin anova method to compare values across multiple groups. 

pingouin.anova()

**Chi-square test:**

The test to compare proportions of successes in a categorical variable across groups of another categorical variable is called a chi-square test of independence.
The chi-square test statistic is a square number, so it is always non-negative, so only the right tail tends to be of interest.


A/B testing lets you compare scenarios to see which best achieves some goal.

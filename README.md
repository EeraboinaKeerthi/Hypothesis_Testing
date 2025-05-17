# Hypothesis_Testing

Let us consider a subset of the survey responses from users who identified as Data Scientists fron Stack-overflow survey.

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

P avlue = norm.cdf(z_score, loc = 0, scale=1) --> for left tail test
P value = 1 - norm.cdf(z_score, loc = 0, scale=1) --> for right tail test 




A/B testing lets you compare scenarios to see which best achieves some goal.

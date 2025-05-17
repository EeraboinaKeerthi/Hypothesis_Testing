# Hypothesis_Testing

Let us consider a subset of the survey responses from users who identified as Data Scientists fron Stack-overflow survey.

Hypothesizing about the mean:

Let's hypothesize that the mean annual compensation of the population of data scientists is 110,000 dollars. Hypothesize mean = 110,000$
We can initially examine the mean annual compensation from the sample survey data by using np.mean().The result is different from our hypothesis, but is it meaningfully different?

Since variables have arbitrary units and ranges, before we test our hypothesis, we need to standardize the values. A common way of standardizing values is to subtract the mean, and divide by the standard deviation. 

For hypothesis testing, we use a variation where we take the sample statistic, subtract the hypothesized parameter value, and divide by the standard error. The result is called a z-score.

Hypothesis testing use case:

Determining whether sample statistics are close to or far away from expected(hypothesized) values.

Plot of the probability density function for the standard normal distribution, which is a normal distribution with mean of zero and standard deviation of one. It's often called the z-distribution, and z-scores are related to this distribution.


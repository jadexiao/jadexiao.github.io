---
layout: post
title: how to parameterize probability distributions for PSA
date: 2024-04-21
description:
tags: cea simulation code 
categories:
---
*This is a joint blog post with <a href="https://www.andrewelhabr.com/" target="_blank">Andrew ElHabr</a>.*

In probabilistic sensitivity analysis (PSA), model parameters are repeatedly sampled from the joint parameter space to generate a set of model runs.

Typically, for each parameter, we will have a base case value ($$B$$), a lower value ($$L$$), and an upper value ($$U$$). One common approach to designing a probability distribution is to assume $$B$$ is the median (i.e., the 50<sup>th</sup> percentile), and $$L$$ and $$U$$ are the bounds of the 95% confidence interval (i.e., the 2.5<sup>th</sup> and 97.5<sup>th</sup> percentiles).

The choice of probability distribution for a given parameter depends on the parameter's range. If the parameter is constrained between 0 and 1, the beta distribution is commonly used. If only non-negativity is desired, the gamma distribution is a good choice. If there are no constraints on the parameter's range and $$L$$ and $$U$$ are equidistant from $$B$$, the normal distribution should suffice.

This tutorial explains how to parameterize the normal, beta, and gamma distributions.

<p style="margin-top: 25px"></p>

##### **Normal distribution**

Recall from high school statistics, that (1) due to symmetry of the probability density function, the mean and median are equal; and (2) 1.96 standard deviations above and below the mean delineate the 95% confidence interval. Therefore, the distribution we need is simply:

$${\rm Normal}\bigg(B,\ \frac{B-L}{1.96}\bigg).$$

<p style="margin-top: 25px"></p>

##### **Beta distribution**

There is no analytical way to do this so we have to resort to some kind of calibration approach. Here is an example using simulated annealing in R:

{% highlight R %}
library(GenSA)

# Quantile targets
target <- c(L, B, U)

# MSE between estimated quantiles and target quantiles
score <- function(params) {
  est <- qbeta(c(0.025, 0.5, 0.975), shape1 = params[1], shape2 = params[2])
  return(sum((est - target)^2))
}

# Upper and lower bounds for shape1 and shape2
lower <- c(1, 1)
upper <- c(1000, 1000)

# Setting the random seed is good practice
set.seed(1)

# Run calibration
opt <- GenSA(par = mapply(runif, 1, lower, upper),
            fn = score,
            lower = lower,
            upper = upper)

# Extract the optimal parameter values
opt$par
{% endhighlight %}

<p style="margin-top: 25px"></p>

##### **Gamma distribution**

Same as the beta distribution, we have to use calibration. Simply replace the previous score function with:

{% highlight R %}
score <- function(params) {
  est <- qgamma(c(0.025, 0.5, 0.975), shape = params[1], scale = params[2])
  return(sum((est - target)^2))
}
{% endhighlight %}

You may need to adjust the upper and lower bounds of calibration.

<p style="margin-top: 25px"></p>

##### **Validation**

The final step is to check that the fitted distribution looks reasonable and its quantiles do indeed match up with $$B$$, $$L$$, and $$U$$. Here is some plotting code for the beta distribution:

{% highlight R %}
x <- seq(0, 1, by = 0.001)
y <- dbeta(x, shape1 = opt$par[1], shape2 = opt$par[2])
plot(x, y, type = 'l')
abline(v = target, col = 'red')
{% endhighlight %}
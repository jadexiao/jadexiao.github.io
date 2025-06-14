---
layout: post
title: tornado plot in ggplot2
date: 2025-06-13
description:
tags: cea simulation code
categories:
---

Sharing some general purpose code for making tornado plots in ggplot2.

First, save the data in this format:

<img style="display: block; margin: auto; width: 45%" src="{{site.baseurl}}/assets/img/blog/2025-06-13-tornado-plot-in-ggplot2-1.png">

Here is the code:

{% highlight R %}
library(dplyr)
library(tidyverse)
library(ggplot2)

# Base case outcome
outcome.base <- 0

# Order by the difference between the High and Low value
df <- read_csv('DSA.csv') %>%
  group_by(parameter) %>%
  mutate(diff = sum(abs(outcome))) %>%
  arrange(diff, direction)

# Keep the top 8 parameters
df <- head(df, 8 * 2)

# Enforce the ordering in the plot
df <- df %>%
  mutate(parameter = factor(parameter, levels = unique(df$parameter)))

ggplot(df, aes(x = parameter, y = outcome, fill = direction)) +
  coord_flip() +
  geom_bar(stat = 'identity', position = 'identity', width = 0.5) +
  geom_hline(yintercept = outcome.base) +
  geom_text(data = df %>% filter(direction == 'Low', outcome < outcome.base),
            aes(label = value), vjust = 0.5, hjust = 2) +
  geom_text(data = df %>% filter(direction == 'Low', outcome > outcome.base),
            aes(label = value), vjust = 0.5, hjust = -1) +
  geom_text(data = df %>% filter(direction == 'High', outcome < outcome.base),
            aes(label = value), vjust = 0.5, hjust = 2.5) +
  geom_text(data = df %>% filter(direction == 'High', outcome > outcome.base),
            aes(label = value), vjust = 0.5, hjust = -1.5) +
  xlab('') +
  ylab('') +
  ylim(-35, 45) +
  theme_bw() +
  theme(legend.position = 'top',
        legend.title = element_blank(),
        legend.key.spacing.x = unit(0.75, 'cm'))
{% endhighlight %}

<p style="margin-top: 18px"></p>

Here is the result:

<img style="display: block; margin: auto; width: 80%; margin-top: -15px;" src="{{site.baseurl}}/assets/img/blog/2025-06-13-tornado-plot-in-ggplot2-2.png">
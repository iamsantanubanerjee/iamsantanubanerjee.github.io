---
title: "Linear Regression"
description: ""
summary: ""
date: 2024-02-17T22:39:47+05:30
lastmod: 2024-02-17T22:39:47+05:30
draft: false
menu:
  statistics:
    parent: ""
    identifier: "linear-regression"
weight: 2
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---
## Dataset

Imagine we have the following dataset:

|  X  |  Y  |
| --- | --- |
|  1  |  3  |
|  2  |  6  |
|  3  |  8  |
|  4  |  7  |
|  5  |  10 |

![Scatter plot of the dataset](01-linear-regression.png)

## Overview of Linear Regression

In short, with linear regression, we try to **best fit** a **linear line** to the dataset, so that we can use that line to predict the output whenever new data comes in, the best way possible.

## Mathematical Details

### Defining the straight line and cost function

The equation of a straight line can be written as:
{{< math class=text-center >}}
$$
h_\theta(x) = \theta_0 + \theta_1x
$$
{{< /math >}}
where, {{< math >}}$h_\theta(x)${{< /math >}} = Dependent variable<br>
{{< math >}}$\theta_0${{< /math >}} = y-intercept<br>
{{< math >}}$\theta_1${{< /math >}} = slope<br>
{{< math >}}$x${{< /math >}} = Independent variable

"Placeholder for a random linear line fitted into dataset"

We start off with a random line ( random values of {{< math >}}$\theta_0${{< /math >}} and {{< math >}}$\theta_1${{< /math >}}). In order to determine how our _random_ line is performing we define a function, also known as the **cost function**, as follows:
{{< math class=text-center >}}
$$
J(\theta_0,\theta_1) = (1/2m)\sum_{i=1}^{m}(h_\theta(x^i)-y^i)^2
$$
{{< /math >}}
where, {{< math >}}$m${{< /math >}} = Total number of data points<br>
{{< math >}}$y^i${{< /math >}} = Actual value of {{< math >}}$y${{< /math >}} for {{< math >}}$x^i${{< /math >}}<br>
{{< math >}}$h_\theta(x^i)${{< /math >}} = Predicted value of {{< math >}}$y${{< /math >}} for {{< math >}}$x^i${{< /math >}}

In our [example](#dataset), {{< math >}}$m${{< /math >}} = 5<br>
{{< math >}}$x^1${{< /math >}} = 1, {{< math >}}$x^2${{< /math >}} = 2, ... , and so on<br>
{{< math >}}$y^1${{< /math >}} = 3, {{< math >}}$y^2${{< /math >}} = 6, ... , and so on

### Interpretation of the cost function
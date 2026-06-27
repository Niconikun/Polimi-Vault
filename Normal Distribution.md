---
title: Normal Distribution
tags:
  - probability
  - statistics
  - stochastic processes
  - uncertainty quantification
---

# Normal Distribution

## Formal Definition

The **normal distribution** (also called Gaussian distribution) is a continuous [[Probability Theory|probability distribution]] characterized by a bell-shaped curve, symmetric about its mean. It is defined by two parameters: the mean $\mu$ (location) and standard deviation $\sigma$ (spread). The normal distribution is fundamental to [[Statistics]], [[Probability Theory]], and uncertainty quantification, appearing ubiquitously in natural phenomena, measurement noise, and as the limiting distribution of sums of independent random variables via the [[Central Limit Theorem]].

## Historical Development

### Key Milestones
- **1733:** Abraham de Moivre discovers the normal distribution as limiting case of binomial distribution
- **1809:** Carl Friedrich Gauss develops the method of least squares and introduces the "normal law" in astronomical error analysis
- **1835:** Adolphe Quetelet applies normal distribution to social phenomena ("bell curve")
- **1901:** Karl Pearson formalizes goodness-of-fit testing for normal distributions
- **20th Century:** Normal distribution becomes universal tool in quality control, hypothesis testing, and uncertainty quantification

### Foundational Contributors
1. **Carl Friedrich Gauss (1777–1855):** Derived distribution in context of error analysis; "Gaussian" distribution named after him
2. **Pierre-Simon Laplace (1749–1827):** Contributed to asymptotic theory and limit theorems
3. **Florence Nightingale (1820–1910):** Popularized normal distribution in statistics and visualization
4. **Ronald A. Fisher (1890–1962):** Developed statistical inference methods based on normal distribution

## Mathematical Formulation

### Probability Density Function (PDF)

The probability density function of a normal distribution is:
$$
f(x) = \frac{1}{\sigma\sqrt{2\pi}} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)
$$

Where:
- $\mu$: mean (center of distribution)
- $\sigma$: standard deviation (spread)
- $\sigma^2$: variance

**Standard Normal Distribution** ($\mu = 0, \sigma = 1$):
$$
\phi(z) = \frac{1}{\sqrt{2\pi}} e^{-z^2/2}
$$

### Cumulative Distribution Function (CDF)

$$
F(x) = \Phi\left(\frac{x-\mu}{\sigma}\right) = \frac{1}{2}\left[1 + \text{erf}\left(\frac{x-\mu}{\sigma\sqrt{2}}\right)\right]
$$

Where $\Phi$ is the standard normal CDF and $\text{erf}$ is the error function.

### Key Statistics

**Mean:** 
$$
E[X] = \mu
$$

**Variance:**
$$
\text{Var}(X) = E[(X-\mu)^2] = \sigma^2
$$

**Standard Deviation:**
$$
\sigma = \sqrt{\text{Var}(X)}
$$

**Skewness** (symmetry):
$$
\gamma_1 = 0
$$

**Kurtosis** (tail heaviness):
$$
\gamma_2 = 0
$$

### Special Cases

1. **Standard Normal ($\mu = 0, \sigma = 1$):**
   $$
   Z \sim N(0,1)
   $$

2. **Standardization Transformation:**
   $$
   Z = \frac{X - \mu}{\sigma}
   $$

3. **Linear Transformation:** If $X \sim N(\mu, \sigma^2)$, then $aX + b \sim N(a\mu + b, a^2\sigma^2)$

## Fundamental Principles

### Core Properties

1. **Symmetry:** Distribution is symmetric about mean $\mu$
2. **68-95-99.7 Rule:** 
   - 68% of data within $\pm 1\sigma$
   - 95% within $\pm 2\sigma$
   - 99.7% within $\pm 3\sigma$
3. **Addition Property:** Sum of independent normal variables is normal
4. **Stability:** Normal distribution is the unique stable distribution of infinite divisibility

### Central Limit Theorem Connection

Regardless of the underlying distribution, the sum (or average) of a large number of independent identically distributed random variables approaches a normal distribution. For a sample mean $\bar{X}$ from $n$ independent samples:
$$
\bar{X} \sim N\left(\mu, \frac{\sigma^2}{n}\right) \text{ as } n \to \infty
$$

## Theoretical Framework

### Multivariate Normal Distribution

In multiple dimensions, the joint distribution of random vector $\mathbf{X} \in \mathbb{R}^k$ is:
$$
f(\mathbf{x}) = \frac{1}{(2\pi)^{k/2}|\boldsymbol{\Sigma}|^{1/2}} \exp\left(-\frac{1}{2}(\mathbf{x}-\boldsymbol{\mu})^T\boldsymbol{\Sigma}^{-1}(\mathbf{x}-\boldsymbol{\mu})\right)
$$

Where:
- $\boldsymbol{\mu}$: mean vector
- $\boldsymbol{\Sigma}$: [[Covariance]] matrix

**Properties:**
- Linear combinations of multivariate normal variables are normal
- Marginal distributions are normal
- Conditional distributions given other variables are normal

### Relationship to Other Concepts

1. **Connection to [[Central Limit Theorem]]:**
   - Explains ubiquity of normal distribution in practice
   - Any sum of many random effects appears normal

2. **Connection to [[Gaussian White Noise]]:**
   - White noise with normal distribution is fundamental in signal processing and [[Control Systems]]

3. **Connection to [[Kalman Filter]]:**
   - Assumes Gaussian measurement and process noise
   - Optimal estimator under normal distribution assumption

4. **Connection to [[Covariance]] and [[Correlation]]:**
   - Fully characterized by mean and covariance matrix
   - Independence equivalent to zero correlation for jointly normal variables

## Parameter Estimation

### Maximum Likelihood Estimation

For sample $\{x_1, x_2, \ldots, x_n\}$:

**Mean Estimate:**
$$
\hat{\mu} = \bar{x} = \frac{1}{n}\sum_{i=1}^n x_i
$$

**Variance Estimate:**
$$
\hat{\sigma}^2 = \frac{1}{n}\sum_{i=1}^n (x_i - \bar{x})^2
$$

**(Unbiased) Sample Variance:**
$$
s^2 = \frac{1}{n-1}\sum_{i=1}^n (x_i - \bar{x})^2
$$

### Confidence Intervals

For true mean with known variance, 95% confidence interval:
$$
\bar{x} \pm 1.96 \cdot \frac{\sigma}{\sqrt{n}}
$$

With unknown variance, use $t$-distribution with $n-1$ degrees of freedom.

## Statistical Inference

### Hypothesis Testing

**Null hypothesis:** $H_0: \mu = \mu_0$  
**Test statistic:** $Z = \frac{\bar{x} - \mu_0}{\sigma/\sqrt{n}} \sim N(0,1)$

**Goodness-of-Fit Tests:**
- Kolmogorov-Smirnov test
- Shapiro-Wilk test
- Anderson-Darling test
- Q-Q plot comparison

### Power Analysis

Normal distribution used extensively in power analysis and sample size determination for [[Reliability Theory|statistical reliability]].

## Applications

### Engineering and Systems

- **Measurement Uncertainty:** Sensor noise and measurement errors often normally distributed
- **Manufacturing:** Quality control via control charts assumes normality
- **Reliability Theory:** Equipment failure times often modeled with normal distribution
- **Stress Analysis:** Structural loads and responses analyzed using normal distribution

### Control and Estimation

- **[[Kalman Filter]]:** Optimal for Gaussian measurement and process noise
- **System Identification:** [[Noise Temperature|noise]] and disturbances modeled as Gaussian
- **Robust Control:** Uncertainty quantification using normal distribution

### Probability and Statistics

- **Hypothesis Testing:** Foundation for t-tests, ANOVA, regression analysis
- **[[Confidence Interval]]:** Standard confidence intervals based on normal distribution
- **Monte Carlo Simulation:** Normal distribution used for generating random [[Random Variable|samples]]

### Signal Processing

- **[[Gaussian White Noise]]:** White noise with normal distribution
- **Thermal Noise:** Johnson noise in electronics has normal amplitude distribution
- **Clutter Modeling:** Radar and sonar clutter often modeled as normal

## Computational Aspects

### Generation of Normal Random Variables

**Box-Muller Transform:** Generate two independent standard normal variables from uniform random numbers:
$$
Z_1 = \sqrt{-2\ln U_1}\cos(2\pi U_2)
$$
$$
Z_2 = \sqrt{-2\ln U_1}\sin(2\pi U_2)
$$

Where $U_1, U_2 \sim U(0,1)$ are independent uniform random variables.

## See Also

- [[Probability Theory]]
- [[Central Limit Theorem]]
- [[Standard Deviation]]
- [[Covariance]]
- [[Gaussian White Noise]]
- [[Kalman Filter]]
- [[Statistics]]
- [[Random Variable]]
- [[Reliability Theory]]
- [[Signal Processing]]

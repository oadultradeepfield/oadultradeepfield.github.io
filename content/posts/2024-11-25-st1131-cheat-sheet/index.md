---
title: "ST1131 Introduction to Statistics and Statistical Computing"
date: "2024-11-25"
summary: "Concepts I Often Forget or Get Mixed Up"
toc: true
readTime: true
autonumber: false
math: true
tags: ["Cheatsheet"]
showTags: true
---

**Note**: Taken in AY2024/25 Semester 1

## Central Tendency and Variability

- **Mean**, **standard deviation**, and **variance** can be sensitive to outliers, while the **median** and **interquartile range** are more robust and less affected by them.
- When you transform data linearly from $X$ to $Y = aX + b$, the **mean** changes from $\overline{X}$ to $a\overline{X} + b$, and the **variance** changes from $S^2$ to $a^2 S^2$.
- For two **random variables** $X$ and $Y$, there are few interesting properties to note:
  - **Linearity of Expectation**: $E(X\pm Y)=E(X)\pm E(Y)$.
  - **Linearity of Variance**: $\text{Var}(X\pm Y)=\text{Var}(X)+\text{Var}(Y)$.

---

## Conditional Probability

Conditional probability is the probability of an event $A$ occurring given that another event $B$ has already occurred. It’s expressed as:

$$
P(A | B) = \frac{P(A \cap B)}{P(B)}
$$

### Law of Total Probability

The **Law of Total Probability** helps us find the probability of an event $A$ by considering all possible ways it could occur, broken down by other events ($B_1, B_2, ..., B_n$):

$$
P(A) = P(A \cap B_1) + P(A \cap B_2) + ... + P(A \cap B_n)
$$

### Bayes’ Theorem

**Bayes' Theorem** is a formula that helps us update the probability of an event $B_i$ based on new evidence ($A$). It’s written as:

$$
P(B_i | A) = \frac{P(A | B_i) P(B_i)}{P(A | B_1) P(B_1) + P(A | B_2) P(B_2) + ... + P(A | B_n) P(B_n)}
$$

### Some Notes on Probability Concepts

- Events $A$ and $B$ are said to be **independent** if and only if $P(A\cap B)=P(A)P(B)$.
- Events $A$ and $B$ are said to be **(mutually) disjoint** events if and only if $P(A\cap B)=0$, which means the events **cannot happen together**.

---

## Binomial Distribution

The number of ways to choose $k$ successes out of $n$ trials is given by the combination formula:

$$
\binom{n}{k} = \frac{n!}{k!(n-k)!}
$$

### 3 Conditions for Binomial Distribution:

1. There are $n$ trials, each with two possible outcomes (success or failure).
2. Each trial has a probability $p$ of success.
3. All trials are independent of each other.

### Binomial Random Variable

- The number of successes in $n$ trials is modeled by a **Binomial Distribution**: $Bin(n, p)$.

- A **Bernoulli Distribution** is a special case of the binomial distribution when $n = 1$: $Bin(1, p)$. The sum of independent Bernoulli random variables follows a **Binomial Distribution**.

### Binomial Formula (for $X \sim \text{Bin}(n, p)$):

- The probability of exactly $x$ successes is given by: $$P(X = x) = \binom{n}{x} p^x (1 - p)^{n - x}$$
- The **Expected Value** (mean) of $X$ is:
  $E(X) = np$.
- The **Variance** of $X$ is: $\text{Var}(X) = np(1 - p)$.

---

## Point Estimate

- $\overline{X} \to \mu$ and $\hat{p} \to p$ represent point estimates.
- Point estimates don't show how close they are to the true value (**population parameters**).

---

## Standard Error and Margin of Error

These terms are quite similar, but they differ slightly in how they’re used:

- **Standard Error (SE)** is the standard deviation of the measured sample mean. A lower **SE** indicates **more accurate results**.
- **Margin of Error (MOE)** represents the range within which we expect the true population parameter to fall, given a certain confidence level. A smaller **MOE** suggests more **precise estimates**.

---

## Confidence Intervals (CI)

In the long run, **95% of intervals** will contain the true population parameter. **CI = Point Estimate $\pm$ Margin of Error.** The width of confidence interval ($D$) $=2\times$ MOE.

### Confidence Interval for Proportion

To find the CI given a confidence level ($x$):

1. Calculate $\hat{p}$ and check if $n\hat{p}(1 - \hat{p}) \geq 5$.
2. Let $\alpha = 1 - x$.
3. CI $=\hat{p} \pm Z_{1-\frac{\alpha}{2}} \times \sqrt{\displaystyle\frac{\hat{p}(1 - \hat{p})}{n}}$.

**Determine Sample Size ($n$) Before Study**:

1. Decide on the confidence level ($x$) and the width of the CI ($D$).
2. Use the formula:
   $n \geq \left(\displaystyle\frac{2Z_{1-\frac{\alpha}{2}}}{D}\right)^2 \times \hat{p}(1 - \hat{p})$, where $\hat{p} = 0.5$.

### Confidence Interval for Mean

t-distribution ($t_{\text{df}}$) approaches $N(0, 1)$ as degrees of freedom ($df$) increase.
To find the CI given a confidence level ($x$):

1. **Assumptions**: The sample is random (not biased), and the data distribution is symmetric (or the sample size is large enough).
2. CI $=\overline{X} \pm t_{n-1; 1-\frac{\alpha}{2}} \times \displaystyle\frac{s}{\sqrt{n}}$.

**Determine Sample Size ($n$) Before Study**:

1. Decide on the confidence level ($x$) and the width of the CI ($D$).
2. Use the formula:
   $n \geq \left(\displaystyle\frac{2Z_{1-\frac{\alpha}{2}} \times s}{D}\right)^2$.
3. For $s$, look for similar studies (as given in the context). Ensure $n \geq 30$ to apply the t-distribution comfortably.

---

## Hypothesis Testing

Hypothesis testing is all about making decisions based on data. The main idea is to test a **null hypothesis** ($H_0$) against an **alternative hypothesis** ($H_1$). Here's a breakdown of the key terms:

- **Null hypothesis ($H_0$)** vs. **Alternative hypothesis ($H_1$)**
- **Test statistic**: How far the point estimate is from our initial guess (the null hypothesis).
- **Null distribution**: The distribution of the test statistic under $H_0$.
- **p-Value**: This tells you how unlikely your observed result is if $H_0$ is true.
- **Significance level ($\alpha$)**: If the p-Value is less than or equal to α, you reject $H_0$.
- A test is statistically significant when we reject $H_0$.
- **Type I Error**: Rejecting $H_0$ when it's actually true.
- **Type II Error**: Not rejecting $H_0$ when it is false.
- Increasing your sample size can help reduce both types of errors.

### One Sample, Proportion

Here’s how you would test a proportion in one sample:

1. **Assumptions**: The data is categorical, random, and we have $np_0(1 - p_0) \geq 5$.
2. **Hypothesis**:
   - $H_0: p = p_0$
   - $H_1: p \neq p_0$
3. **Test statistic**:
   $$
   z = \displaystyle\frac{p - p_0}{\sqrt{\frac{p_0(1 - p_0)}{n}}}
   $$
   where $z \sim N(0,1)$.
4. **p-Value**:
   - For a right-sided test: $P(z \geq \text{Test stat.} \\| z \sim N(0,1))$
   - For a two-sided test: $2 \times P(z \geq \text{Test stat.} \\| z \sim N(0,1))$
5. **Conclusion**:  
   If the p-Value $\leq \alpha$, reject $H_0$. Otherwise, you cannot reject $H_0$.

### One Sample, Mean

Testing the mean of one sample:

1. **Assumptions**: The data is quantitative, random, and normally distributed (or $n \geq 30$).
2. **Hypothesis**:
   - $H_0: \mu = \mu_0$
   - $H_1: \mu \neq \mu_0$
3. **Test statistic**:
   $$
   T = \displaystyle\frac{\overline{X} - \mu_0}{s / \sqrt{n}}
   $$
   where $T \sim t_{n-1}(0,1)$.
4. **p-Value and Conclusion**: This works the same as the proportion test.
   - The result of a two-sided test for the mean is equivalent to using a confidence interval.

### Two Sample, Independent, Equal Variance

When comparing the means of two independent samples with equal variances:

1. **Assumptions**: The data is quantitative, random, independent, and the population distribution is approximately normal (or $n$ is large enough). For the equal variance test, $p > 0.05$.
2. **Hypothesis**:
   - $H_0: \mu_1 = \mu_2$
   - $H_1: \mu_1 \neq \mu_2$
3. **Test statistic**:
   $$
   T = \displaystyle\frac{\overline{X} - \overline{Y}}{se}
   $$
   where
   $$
   se = \displaystyle\sqrt{\frac{s_p^2}{n_1} + \frac{s_p^2}{n_2}}
   $$
   and
   $$
   s_p^2 = \displaystyle\frac{(n_1 - 1)s_1^2 + (n_2 - 1)s_2^2}{n_1 + n_2 - 2}
   $$
   (Pooled estimate of common variance).  
   Where $T \sim t_{n_1 + n_2 - 2}$.

### Two Sample, Independent, Unequal Variance

This is similar to the previous test, but with unequal variances:

1. **Assumptions**: Same as above, but the population variances are different.
2. **Hypothesis**:
   - $H_0: \mu_1 = \mu_2$
   - $H_1: \mu_1 \neq \mu_2$
3. **Test statistic**:
   $$
   T = \displaystyle\frac{\overline{X} - \overline{Y}}{se}
   $$
   where
   $$
   se = \displaystyle\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}
   $$
   and $T \sim t_{\text{df}}$.

### Two Sample, Dependent

When the two samples are dependent (e.g., before and after comparisons):

- Each observation has a matching pair.
- Take the difference of the paired observations and compare the mean of those differences to 0. This is similar to performing a one-sample test.

---

## QQ Plot - Check Normality

A QQ plot helps check if your data follows a normal distribution.

- **Right tail below/above the line**: This indicates a **longer/shorter** right tail.
- **Left tail below/above the line**: This indicates a **shorter/longer** left tail.

# Chapter 5 - Specific Formulas for Discrete Distributions

## Uniform Distribution
- **Probability Mass Function (PMF):** $$ P(X = x) = 
  \begin{cases} 
    \frac{1}{n} & \text{for } x = a, a+1, \ldots, b-1, b \\
    0 & \text{otherwise} 
  \end{cases} $$
- where \(a\) and \(b\) are the bounds of the distribution and \(n = b - a + 1\).
- **Expected Value (E[X]):** $$ \frac{a + b}{2} $$
- **Variance (Var[X]):** $$ \frac{(b - a + 1)^2 - 1}{12} $$

## Bernoulli Distribution
- **PMF:** $$ P(X = x) = 
  \begin{cases} 
    p & \text{for } x = 1 \\
    1 - p & \text{for } x = 0 
  \end{cases} $$
- **Expected Value (E[X]):** $$ p $$
- **Variance (Var[X]):** $$ p(1 - p) $$

## Geometric Distribution
- **PMF:** $$ P(X = x) = p(1 - p)^{x - 1} $$
- for \(x = 1, 2, 3, ...\).
- **Expected Value (E[X]):** $$ \frac{1}{p} $$
- **Variance (Var[X]):** $$ \frac{1 - p}{p^2} $$

## Binomial Distribution
- **PMF:** $$ P(X = x) = \binom{n}{x} p^x (1 - p)^{n - x} $$
- for \(x = 0, 1, 2, ..., n\).
- **Expected Value (E[X]):** $$ np $$
- **Variance (Var[X]):** $$ np(1 - p) $$

## Poisson Distribution
- **PMF:** $$ P(X = x) = \frac{e^{-\lambda} \lambda^x}{x!} $$
- for \(x = 0, 1, 2, ...\).
- **Expected Value (E[X]):** $$ \lambda $$
- **Variance (Var[X]):** $$ \lambda $$
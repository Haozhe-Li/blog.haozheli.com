# Chapter 4 - Discrete Random Variables

## Discrete Random Variable (X)
- **Definition:** A variable that can take on a countable number of distinct outcomes.
- **Notation:** $$ X $$

## Probability Distribution of a Random Variable
- **Definition:** A function that gives the probability that a discrete random variable is exactly equal to some value.
- **Notation:** $$ P(X = x) $$

## Cumulative Distribution Function (CDF)
- **Definition:** A function that gives the probability that a random variable is less than or equal to a certain value.
- **Notation/Formulation:** $$ F_X(x) = P(X \leq x) $$

## Joint Distribution of Two Discrete Random Variables (X, Y)
- **Definition:** A function giving the probability that each of two random variables falls within a specific range or set of discrete values.
- **Notation/Formulation:** $$ P(X = x \text{ and } Y = y) $$ or $$ f_{X,Y}(x, y) $$

## Marginal Probability of a Random Variable
- **Definition:** The probability distribution of a subset of a collection of random variables.
- **Notation/Formulation:** For variable $$ X $$, $$ P(X = x) = \sum_y P(X = x \text{ and } Y = y) $$

## Independent Random Variables
- **Definition:** Two random variables $$ X $$ and $$ Y $$ are independent if the probability distribution of one variable is not affected by the known outcome of the other variable.
- **Condition:** $$ P(X = x \text{ and } Y = y) = P(X = x)P(Y = y) $$

## Expected Value (EV or E[X])
- **Definition:** A measure of the center of the distribution of the variable. Also known as the mean.
- **Notation/Formulation:** For a discrete random variable $$ X $$, $$ E[X] = \sum_x x P(X = x) $$

## Variance (Var(X))
- **Definition:** A measure of the spread of the distribution of the variable.
- **Notation/Formulation:** $$ \sigma^2_X = Var(X) = E[(X - E[X])^2] = \sum_x (x - E[X])^2 P(X = x) $$

## Covariance (Cov(X, Y))
- **Definition:** A measure of the extent to which two random variables change together.
- **Notation/Formulation:** $$ Cov(X, Y) = E[(X - E[X])(Y - E[Y])] $$

## Markov's Inequality
- **Statement:** For any non-negative random variable $$ X $$ and $$ a > 0 $$, $$ P(X \geq a) \leq \frac{E[X]}{a} $$

## Chebyshev's Inequality
- **Statement:** For any random variable $$ X $$ with finite expected value $$ \mu $$ and finite non-zero variance $$ \sigma^2 $$, for any $$ k > 0 $$: $$ P(|X - \mu| \geq k\sigma) \leq \frac{1}{k^2} $$

## Weak Law of Large Numbers
- **Statement:** The sample average of a sequence of iid random variables converges in probability towards the expected value as the sample size goes to infinity.

## Independent Identically Distributed Samples (iid Samples)
- **Definition:** A sequence of random variables where each variable has the same probability distribution as the others and all are mutually independent.

## Property of Expectations
- **Linearity:** $$ E[aX + b] = aE[X] + b $$

## Property of Variance
- **Scaling:** $$ Var(aX) = a^2Var(X) $$
- **For independent variables:** $$ Var(X + Y) = Var(X) + Var(Y) $$

## Property of Covariance
- **Symmetry:** $$ Cov(X, Y) = Cov(Y, X) $$
- **For independent variables:** $$ Cov(X, Y) = 0 $$

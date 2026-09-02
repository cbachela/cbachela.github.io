---
layout: post
title: "Portfolio Optimization: A Practical Tutorial"
date: 2026-09-02 13:00:00 +0000
mathjax: true
---

Portfolio optimization is the process of choosing asset weights to balance expected return against risk. The classic framework is to maximize return for a given level of risk, or equivalently minimize risk for a target return.

## 1. The mean-variance problem

Let $w$ be the vector of portfolio weights, $\mu$ the vector of expected returns, and $\Sigma$ the covariance matrix of asset returns. The portfolio expected return is

$$
\mu_p = w^T \mu
$$

and the portfolio variance is

$$
\sigma_p^2 = w^T \Sigma w.
$$

The Markowitz problem is:

$$
\min_w \; \frac{1}{2} w^T \Sigma w
$$

subject to

$$
w^T \mu = \mu_{target}, \qquad \sum_i w_i = 1.
$$

This is the foundation of modern portfolio theory.

## 2. Why diversification matters

Diversification reduces risk because asset returns are not perfectly correlated. If the covariance matrix has off-diagonal terms smaller than variance terms, the portfolio variance can be reduced relative to holding a single asset.

In a two-asset case,

$$
\sigma_p^2 = w_1^2 \sigma_1^2 + w_2^2 \sigma_2^2 + 2 w_1 w_2 \sigma_{12},
$$

where $\sigma_{12}$ is the covariance between the two assets. This shows that mixing assets can lower the overall variance if the correlation is less than 1.

## 3. The efficient frontier

By sweeping through different target returns, we trace out the efficient frontier. Each point on this frontier is a portfolio with the minimum risk for a given expected return.

The risk-return tradeoff is often summarized as:

$$
\text{maximize } w^T \mu - \frac{\gamma}{2} w^T \Sigma w,
$$

where $\gamma$ controls the investor's risk aversion. A higher $\gamma$ places more weight on minimizing variance.

## 4. A practical example

Suppose an investor holds three assets with expected returns and covariance matrix:

$$
\mu =
\begin{bmatrix}
0.08 \\
0.10 \\
0.12
\end{bmatrix},
\qquad
\Sigma =
\begin{bmatrix}
0.04 & 0.01 & 0.02 \\
0.01 & 0.09 & 0.03 \\
0.02 & 0.03 & 0.07
\end{bmatrix}.
$$

The optimal portfolio depends on the target return or the chosen risk penalty. In practice, the problem is solved numerically by quadratic programming or by using a convex optimization routine.

## 5. Implementation idea

A simple optimization routine looks like this conceptually:

1. Define expected returns $\mu$.
2. Define the covariance matrix $\Sigma$.
3. Impose budget and target-return constraints.
4. Solve the quadratic program.
5. Inspect the resulting weights and efficient frontier.

The general optimization problem can be written as:

$$
\min_w \; \frac{1}{2} w^T \Sigma w - \lambda w^T \mu
$$

subject to $\sum_i w_i = 1$.

This form highlights the tradeoff between expected return and risk.

## 6. Takeaways

Portfolio optimization is most useful when you want to:

- control total portfolio risk,
- choose a reasonable balance between return and volatility,
- diversify across assets with imperfect correlation,
- build a disciplined quantitative investment framework.

In practice, the optimal portfolio depends on assumptions about expected returns, covariances, and the investor's risk preferences. Even a simple mean-variance model can provide a strong starting point.

---

This tutorial is intentionally compact, but it illustrates the central intuition behind portfolio optimization: choose weights that efficiently trade off expected return and risk.

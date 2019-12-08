---
title: Nonlinear Programming - Homework 5
author: Jaan Tollander de Balsch - 452056
date: \today
bibliography: bibliography.bib
cls: https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl
# https://www.zotero.org/styles/frontiers-in-applied-mathematics-and-statistics
link-citations: true
urlcolor: blue
---
# Exercise 5.2
Quadratic problem
$$
\begin{aligned}
\mathrm{minimize} \quad & c^T x + \frac{1}{2} x^T Q x \\
\mathrm{subject\,to} \quad & Ax = b \\
& x ≥ 0
\end{aligned}
$$
with variables $x∈𝐑^n$, symmetric positive definite matrix $Q∈𝐑^{n×n}$, and parameters $c∈𝐑^n$, $A∈𝐑^{m×n}$, and $b∈𝐑^m$.


## a)
With objective $f(x) = c^T x + \frac{1}{2} x^T Q x$, and constraints $g(x)=-x$ and $h(x) = Ax - b$, the KKT conditions are
$$
\begin{aligned}
∇f(\bar{x}) + ∇g(\bar{x}) u + ∇h(\bar{x}) v &= 0 \\
c + Q \bar{x} - u + A^T v &= 0 
\end{aligned}
$$
where $u∈𝐑^n$, $u≥0$ and $v∈𝐑^m$. Also, $g(\bar{x})≤0$, $h(\bar{x})=0$ and $v^T g(\bar{x})=0$.

## b)
We have the barrier problem
$$
\begin{aligned}
\mathrm{minimize} \quad & f(x) + μ B(x) \\
\mathrm{subject\,to} \quad & Ax = b
\end{aligned}
$$
where $μ>0$ and the barrier function is the logarithmic barrier
$$
B(x) = -∑_{i=1}^{n}\ln(x_i).
$$

Gradient of the barrier function
$$
∇B(x) = -\left(\frac{1}{x_1},...,\frac{1}{x_n}\right) = -X^{-1}e,
$$
where $e=𝟏$ is a vector of ones and $X=\operatorname{diag}(x)$.

Then the KKT conditions are
$$
\begin{aligned}
∇(f(\bar{x})+μB(\bar{x})) + ∇h(\bar{x}) v &= 0 \\
c + Q \bar{x} - μ\bar{X}^{-1}e + A^T v &= 0 \\
\end{aligned}
$$
where $v∈𝐑^m$. Also, $h(\bar{x})=0$ and $\bar{x}>0$.


## c)



<!-- # References -->

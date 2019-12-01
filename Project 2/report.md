---
# title: Solving Large-Scale Optimization Problems with ADMM
# author: Jaan Tollander de Balsch
# date: \today
documentclass: artikel3
header-includes: |
    \paperheight = 29.70 cm  \paperwidth = 21.0 cm  \hoffset        = 0.46 cm
    \headheight  =  0.81 cm  \textwidth  = 15.0 cm  \evensidemargin = 0.00 cm
    \headsep     =  0.81 cm  \textheight = 9.00 in  \oddsidemargin  = 0.00 cm
    \usepackage{enumerate}
    \usepackage{amsfonts}
    \usepackage{amsmath}
    \usepackage{url}
    \usepackage{graphicx}
    \usepackage{float}
    \usepackage[font=small,labelfont=bf]{caption}
    \usepackage{setspace}
    \usepackage{booktabs}
    \allowdisplaybreaks
    \onehalfspacing
urlcolor: blue
bibliography: bibliography.bib
csl: https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl
---

\begin{center}
{\Large \onehalfspacing \bf Solving Large-Scale Optimization Problems with ADMM}
\end{center}
\vspace{10pt}

\begin{center}
Jaan Tollander de Balsch\\
{\textit{{\small{Aalto University School of Science, Department of Computer Science, 
                \{de.tollander@aalto.fi\}}}}}
\end{center}

# Background
In this report, we examine the *alternating direction method of multipliers* (ADMM), a distributed constrained convex optimization method, suitable for solving large scale optimization problems. ADMM combines the benefits of *dual decomposition* and *augmented Lagrangian* methods for constrained optimization. The dual decomposition method is a distributed variant of the *dual ascent* method possible when the objective function is *separable*. The augmented Lagrangian brings robustness to the *dual ascent* method and yields convergence without assumptions such as strict convexity finiteness of the objective function.

ADMM is extensively covered by @admm, and this report heavily relies on this paper, especially sections 1, 2, 3 and 5.

## Algorithm
The ADMM algorithm solves problems in the form
$$
\begin{aligned}
\mathrm{minimize}\quad & f(x) + g(z) \\
\mathrm{subject\, to}\quad & Ax + Bz = c
\end{aligned}
$$
with variables $x∈𝐑^n$ and $z∈𝐑^m$, and parameters $A∈𝐑^{p×n}$, $B∈𝐑^{p×m}$, and $c∈𝐑^p.$

The augmented Lagrangian takes form
$$
L_ρ(x,z,y) = f(x) + g(z) + y^T (Ax+Bz-c) + (ρ/2) \|Ax+Bz-c\|_2^2,
$$
where $ρ>0$ is referred as the *penalty parameter*.

The ADMM algorithm consists of the following iterations
$$
\begin{aligned}
x_{k+1} &= \operatorname{argmin}_x L_p(x, z_{k}, y_{k}) \\
z_{k+1} &= \operatorname{argmin}_z L_p(x_{k+1}, z, y_{k}) \\
y_{k+1} &= y_{k} + ρ(Ax_{k+1}+Bz_{k+1}-c).
\end{aligned}
$$

The algorithm updates the variables $x$ and $z$ in alternating fashion, hence the term *alternating direction*.


## Convergence and Stopping Criteria
A *residual* at iteration $k$ is defined as
$$
r_k = Ax_k + Bz_k - C.
$$

If we assume that the functions $f$ and $g$ are closed, proper and convex, and the unaugmented Lagrangian has as saddle point.

Then the convergence as the iterations $k→∞$

* The *residual converges* towards zero, that is, $r→0$.
* The *objective value converges* towards the optimal.
* The *dual variable converges* towards the dual optimal point.

ADMM stops once the residual is below some tolerance $ϵ>0$, that is, $r<ϵ$. 

ADMM converges slowly to high accuracy, but modest accuracy can be reached with relatively few iterations. 

In practice, high accuracy is not required for many applications.


## Generic Algorithm
We focus on applying the ADMM to generic constrained optimization problem
$$
\begin{aligned}
\mathrm{minimize}\quad & f(x) \\
\mathrm{subject\, to}\quad & x ∈ X
\end{aligned}
$$

Reduced to ADMM
$$
\begin{aligned}
\mathrm{minimize}\quad & f(x) + g(z) \\
\mathrm{subject\, to}\quad & x - z = 0 \\
& x∈X
\end{aligned}
$$

Augmented Lagrangian function
$$
L_ρ(x,z,y) = f(x) + g(z) + y^T (x-z) + (ρ/2) \|x-z\|_2^2.
$$

Residual
$$
r = x - z
$$

# Applications
TODO: ADMM for stochastic capacity expansion problem

We applied ADMM to stochastic capacity expansion problem.

Minimize
$$
∑_{i∈I} c_i x_i + ∑_{s∈S} p_s \left(∑_{i∈I}∑_{j∈J}f_{i,j}y_{i,j,s} + ∑_{j∈J} q_j u_{j,s}\right)
$$

separable in terms of $S$

---

ADMM formulation
$$
∑_{s∈S} p_s \left(∑_{i∈I} c_i x_{i,s} + ∑_{i∈I}∑_{j∈J}f_{i,j}y_{i,j,s} + ∑_{j∈J} q_j u_{j,s}\right) 
$$

$$
∑_{s∈S} p_s c^T x_s
$$

\pagebreak

# Discussion and Conclusions
Number of iterations $k$ to convergence as a function of the penalty parameter $\rho$ with solution tolerance $ϵ=10^{-3}$.

\pagebreak

# References
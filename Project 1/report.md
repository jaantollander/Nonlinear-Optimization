---
# title: Comparing Unconstrained Optimization Methods
# author: Jaan Tollander de Balsch
# date: \today
documentclass: artikel3
header-includes: |
    \paperheight = 29.70 cm  \paperwidth = 21.0 cm  \hoffset        = 0.46 cm
    \headheight  =  0.81 cm  \textwidth  = 15.0 cm  \evensidemargin = 0.00 cm
    \headsep     =  0.81 cm	 \textheight = 9.00 in  \oddsidemargin  = 0.00 cm
urlcolor: blue
bibliography: bibliography.bib
csl: https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl
---

# Project description
The purpose of this project is to compare the performance of different unconstrained optimization methods. As a reference to the theory of unconstained optimization methods, lecture notes by @lectures are used.

## Unconstrained Optimization Method
Conceptually, an unconstrained optimization method is implemented as follows:

<!-- TODO: implemented as a minimization problem -->

---

**Input**: Function $f$, solution tolerance $ϵ$, maximum iteration limit $N$ and method specific parameters.

**Output**: Point $x_k$ in which the function value $f(x_k)$ is optimal.

1) Initialize with iteration counter $k=0$ and starting point $x_0$.

2) Each iteration $k$, compute direction $d_k$ and stepsize $λ_k$. Then update the current position $x_{k+1} = x_k + λ_k d_k$ and the iteration counter $k=k+1$.

3) Stop when either $|∇f(x_k)|<ϵ$ or an iteration limit $N$ is reached. Return $x_k$.

---

The idea is that the algorithm takes a step of size $λ_k$ into a direction $d_k$ each iteration $k$ until optimality condition is reached. Numerically, the optimality condition is that the gradient is close enough to zero, that is, the norm of the gradient is less than the set tolerance $ϵ$. 

If the function $f$ is convex, the solution $x_k$ is global optimal solution. Otherwise, $x_k$ is local optimal solution.

The algorithms used to analyze the optimization methods may also collect and return the whole iteration sequence $x_1,...,x_k$.


## Optimization Methods
Different variants of unconstrained optimization methods are implemented by using different methods to compute the direction and stepsize. The direction and stepsize can be computed using exact or inexact (heuristic) algorithms. The direction algorithm can be implemented using first-order derivative information (gradient) or second-order derivative information (Hessian). In this project, four variants of direction algorithms and two variants of stepsize algorithms were implemented. 

Direction algorithm computes the direction at the current position $x$.

1) *Gradient method*. Uses gradient for computing the direction.

2) *Gradient method with momentum (Heavy-Ball)*. Uses current and previous gradient for computing the direction. It has weight parameter $w∈(0, 1)$.

3) *Newton's method*. Uses Hessian for computing the direction.

4) *Broyden–Fletcher–Goldfarb–Shanno (BFGS) method*. Uses an  approximation of Hessian for computing the direction.

Stepsize algorithm finds the optimal stepsize $\bar{λ}$ by solving the unidimensional optimization problem
$$
\bar{λ}=\operatorname{argmin}_λ f(x+λd)
$$
where $x$ is the current position and $d$ is the current direction.

1) *Golden linesearch*. An exact algorithm. It has two parameters, initial lower bound $a_0$ and initial upper bound $b_0$.

2) *Armijo linesearch*. An inexact algorithm. It has three parameters, slope reduction factor $α_0$, $λ$-reduction factor $β_0$ and initial step size $λ_0$.

Direction and stepsize algorithm can be combined into an optimization method. Then, the performance of different combinations can be measured and compared against each other.

## Implementation
The algorithms were implemented and tested using [Julia programming language](https://julialang.org/), version 1.1, in [Jupyter](https://jupyter.org/) notebook.  `TimerOutputs.jl` was used for timing and comparing performance of functions. Timing in Julia is explained in depth by @timing_in_julia. Plotting was done using `Plots.jl`. The full code for the optimization methods and performance metrics is available in a Jupyter notebook: `optimization_methods.ipynb`.


# Numerical results
| Detail | Value |
|--------|-------|
| Operating system | Ubuntu 16.04 |
| Memory (RAM) | 16 GiB |
| Processor | Intel Core i5-7600K CPU @ 3.80GHz $\times$ 4 |

Table: Computer details \label{fig:1}

The optimization methods were tested against four different functions. Each subsection describes the particular test function, plots the convergence of each optimization method and execution times of each optimization method tested against the function. Details about the computer used for timing are listed in table \ref{fig:1}.

The numerical paramater for the different optimization methods are set as follows:

* $α_0$
* $β_0$
* $w$
* $N=10000$
* $a_0=0$
* $b_0=10$
* $λ_0=1$
* $ϵ = 10^{-5}$

In the results, the optimization methods are referred using notation *direction - stepsize*, for example, *Gradient - Golden* refers to Gradient method with Golden linesearch.


## Function 1
![Contour lines of function 1 and convergence of different optimization methods. \label{fig:f1}](figures/function1.svg)

Function 1 is defined as
$$
f_1(x_1,x_2) = 0.26 (x_1^2+x_2^2) - 0.48 x_1 x_2.
$$
The function $f_1$ is a convex function. 

The iteration starting point
$$
x_0 = (7.0, 3.0)
$$

| Method | Time | Iterations
| ------ | ---- | ----------
| Gradient - Armijo | $206\,μs$ | 142
| Heavy Ball - Armijo | $148\,μs$ | 94
| Gradient - Golden | $96\,μs$ | 15
| Heavy Ball - Golden | $84\,μs$ | 13

Table: Performance of optimization methods on function 1.


## Function 2
![Contour lines of function 2 and convergence of different optimization methods. \label{fig:f2}](figures/function2.svg)

Function 2 is defined as
$$
f_2(x_1,x_2) = \exp(x_1+3x_2-0.1) + \exp(x_1-3x_2-0.1)+\exp(-x_1-0.1).
$$
The function $f_2$ is a convex function.

The iteration starting point
$$
(1, 1.5)
$$

| Method | Time | Iterations
| ------ | ---- | ----------
| Gradient - Golden | $135\,μs$ | 17
| BFGS - Armijo | $106\,μs$ | 31
| BFGS - Golden | $95\,μs$ | 8
| Gradient - Armijo | $78\,μs$ | 32
| Heavy Ball - Armijo | $71\,μs$ | 33
| Newton - Golden | $66\,μs$ | 5
| Heavy Ball - Golden | $63\,μs$ | 7
| Newton - Armijo | $56\,μs$ | 9

Table: Performance of optimization methods on function 2.


## Function 3
![Contour lines of function 3 and convergence of different optimization methods. \label{fig:f3}](figures/function3.svg)

Function 3 is defined as
$$
f_3(x_1,x_2) = (x_1^2+x_2-11)^2+(x_1+x_2^2-7)^2.
$$
Function $f_3$ is not a convex function. This is evident from the figure \ref{fig:f3} where *Heavy Ball - Golden* can be seen to convergence to different local optimum compared to the other methods.

The iteration starting point
$$
(-2, 2)
$$

| Method | Time | Iterations
| ------ | ---- | ----------
| Gradient - Golden | $266\,μs$ | 8
| Heavy Ball - Golden | $240\,μs$ | 11
| BFGS - Armijo | $236\,μs$ | 37
| Gradient - Armijo | $232\,μs$ | 35
| Newton - Armijo | $175\,μs$ | 25
| Heavy Ball - Armijo | $159\,μs$ | 28
| Newton - Golden | $124\,μs$ | 4
| BFGS - Golden | $99\,μs$ | 4

Table: Performance of optimization methods on function 3.

## Function 4
The function 4 is defined as
$$
f_4(x) = (1/2) x^T Ax - b^T.
$$
The function $f_ 4$ is a convex function.

Two cases: $A$ has

1) Low condition number
2) High condition number

![](figures/performance_plot_1.svg)

![](figures/performance_plot_2.svg)


# Discussion and conclusions



# References

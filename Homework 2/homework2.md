---
title: Nonlinear Programming - Homework 2
author: Jaan Tollander de Balsch - 452056
date: \today
---
## Exercise 2.1
**Farkas' theorem**: Let $A$ be an $m×n$ matrix and $c$ be an $n$-vector. Then exatcly one of the following two systems has a solution:

1) $Ax≤0, c^Tx>0, x∈𝐑^n$
2) $A^Ty=c, y≥0, y∈𝐑^m.$

---

TODO: proof?

We can modify the systems such the system 1 can't be equal to zero, but the system 2 can. Otherwise, the solutions to the systems remain unaffected.

1) $Ax<0, c^Tx≥0, x∈𝐑^n$
2) $A^Ty=c, y≥0, y∈𝐑^m$.

Hence, if we let $c=0$, the system

1) $Ax<0, x∈𝐑^n$
2) $A^Ty=0, y≥0, y∈𝐑^m$.

has only one solution.


## Exercise 2.2


## Exercise 2.3
**The definition of a convex set**: A set $S⊆𝐑^n$ is said to be convex if $\overline{x}=∑_{j=1}^k λ_j x_j$ belongs to $S$, where $∑λ_j=1$, $λ_j≥0$ and $x_j∈S$ for $j=1,...,k.$

### (a)
The set $S$ is convex if
$$
α≤a^T\overline{x}≤β.
$$

...
$$
a^T\overline{x} = a^T∑_{j=1}^k λ_j x_j=∑_{j=1}^k λ_j (a^T x_j)
$$
Lower bound
$$
∑_{j=1}^k λ_j (a^T x_j) ≥ ∑_{j=1}^k λ_j α = α ∑_{j=1}^k λ_j = α
$$
Upper bound
$$
∑_{j=1}^k λ_j (a^T x_j) ≤ ∑_{j=1}^k λ_j β = β ∑_{j=1}^k λ_j = β
$$
Set $S$ is convex.

### (b) 
$$
β≤\overline{x}≤α
$$
$α,β$ are vectors

$$
\overline{x}=∑_{j=1}^k λ_j x_j
$$

Lower bound
$$
∑_{j=1}^k λ_j x_j ≥ ∑_{j=1}^k λ_j α = α ∑_{j=1}^k λ_j = α
$$
Upper bound
$$
∑_{j=1}^k λ_j x_j ≤ ∑_{j=1}^k λ_j β = β ∑_{j=1}^k λ_j = β
$$
Set $S$ is convex.

### (c)
$$
a_i^T \overline{x}= a_i^T ∑_{j=1}^k λ_j x_j = ∑_{j=1}^k λ_j (a_i^T x_j) ≤ ∑_{j=1}^k λ_j b_i = b_i ∑_{j=1}^k λ_j = b_i, i∈\{1,2\}
$$
Set $S$ is convex.

### (d)
$$
\overline{x}=∑_{j=1}^k λ_j x_j = ∑_{j=1}^k λ_j A^T y = A^T y ∑_{j=1}^k λ_j = A^T y
$$
Set $S$ is convex.

## Exercise 2.4


## References

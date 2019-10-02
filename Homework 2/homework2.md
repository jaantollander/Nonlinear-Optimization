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

We can move the element $\{0\}$ from system 1 to system 2 by modifying the systems. Otherwise, the solutions to the systems remain unaffected.

1) $Ax<0, c^Tx≥0, x∈𝐑^n$
2) $A^Ty=c, y≥0, y∈𝐑^m$.

Hence, if we let $c=0$, the system

1) $Ax<0, x∈𝐑^n$
2) $A^Ty=0, y≥0, y∈𝐑^m$.

has only one solution.


## Exercise 2.2


## Exercise 2.3
**The definition of a convex set**: A set $S⊆𝐑^n$ is said to be convex if $\overline{x}=∑_{j=1}^k λ_j x_j$ belongs to $S$, where $∑λ_j=1$, $λ_j≥0$ and $x_j∈S$ for $j=1,...,k.$

In each of the following sections we determine the convexity of set $S$ by testing if element $\overline{x}$ belong to the set $S.$ 

### (a)
Let test if element $\overline{x}$ belong to the set $S.$ Elements of set $S$ must satisfy the constraint $α≤a^T x≤β$ for all $x∈S$. Then
$$
a^T\overline{x} = a^T∑_{j=1}^k λ_j x_j=∑_{j=1}^k λ_j (a^T x_j)
$$
Lower bound 
$$
a^T\overline{x} = ∑_{j=1}^k λ_j (a^T x_j) ≥ ∑_{j=1}^k λ_j α = α ∑_{j=1}^k λ_j = α
$$
Upper bound
$$
a^T\overline{x} = ∑_{j=1}^k λ_j (a^T x_j) ≤ ∑_{j=1}^k λ_j β = β ∑_{j=1}^k λ_j = β
$$
Therefore
$$
α≤a^T\overline{x}≤β,
$$
which implies that $\overline{x}∈S$ and set $S$ is convex.

### (b) 
Let test if element $\overline{x}$ belong to the set $S.$ Elements of set $S$ must satisfy the constraint $α≤x≤β$ for all $x∈S$. Then:

Lower bound
$$
\overline{x}=∑_{j=1}^k λ_j x_j ≥ ∑_{j=1}^k λ_j α = α ∑_{j=1}^k λ_j = α
$$
Upper bound
$$
\overline{x}=∑_{j=1}^k λ_j x_j ≤ ∑_{j=1}^k λ_j β = β ∑_{j=1}^k λ_j = β
$$
Therefore
$$
α≤\overline{x}≤β,
$$
which implies that $\overline{x}∈S$ and set $S$ is convex.

### (c)
Let test if element $\overline{x}$ belong to the set $S.$ Elements of set $S$ must satisfy the constraints $a_i^Tx≤b_i$ for all $x∈S$ and $i∈\{1,2\}$. Then
$$
a_i^T \overline{x}= a_i^T ∑_{j=1}^k λ_j x_j = ∑_{j=1}^k λ_j (a_i^T x_j) ≤ ∑_{j=1}^k λ_j b_i = b_i ∑_{j=1}^k λ_j = b_i, ∀i∈\{1,2\}
$$
which implies that $\overline{x}∈S$ and set $S$ is convex.

### (d)
Let test if element $\overline{x}$ belong to the set $S.$ Elements of set $S$ must satisfy the constraints $x=A^Ty$ for all $x∈S$. Then
$$
\overline{x}=∑_{j=1}^k λ_j x_j = ∑_{j=1}^k λ_j A^T y = A^T y ∑_{j=1}^k λ_j = A^T y
$$
which implies that $\overline{x}∈S$ and set $S$ is convex.

## Exercise 2.4


## References

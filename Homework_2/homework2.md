---
title: Nonlinear Programming - Homework 2
author: Jaan Tollander de Balsch - 452056
date: \today
---
# Exercise 2.1
**Farkas' theorem**: Let $A$ be an $m×n$ matrix and $c$ be an $n$-vector. Then exactly one of the following two systems has a solution:

1) $Ax≤0, c^Tx>0, x∈𝐑^n$
2) $A^Ty=c, y≥0, y∈𝐑^m.$

---

We can move the element $\{0\}$ from system 1 to system 2 by modifying the systems. Otherwise, the solutions to the systems remain unaffected.

1) $Ax<0, c^Tx≥0, x∈𝐑^n$
2) $A^Ty=c, y≥0, y∈𝐑^m$.

Hence, if we let $c=0$, the system

1) $Ax<0, x∈𝐑^n$
2) $A^Ty=0, y≥0, y∈𝐑^m$.

has only one solution.


# Exercise 2.2
**Closest point theorem**: Let $S≠∅$ be a closed convex set in $𝐑^n$ and $y∉S.$ Then, there exists a unique point $\overline{x}∈S$ with minimum distance from $y.$ In addition, $\overline{x}$ is the minimizing point if and only if
$$
(y-\overline{x})^T(x-\overline{x})≤0,
$$
for all $x∈S.$

---

Using the closest point theorem we have
$$
\begin{cases}
(x-\overline{x})^T(z_1-\overline{x})≤0, ∀z_1∈S \\
(y-\overline{y})^T(z_2-\overline{y})≤0, ∀z_2∈S
\end{cases}.
$$
Now, we can choose $z_1=\overline{y}∈S$ and $z_2=\overline{x}∈S$
$$
\begin{cases}
(x-\overline{x})^T(\overline{y}-\overline{x})≤0 \\
(y-\overline{y})^T(\overline{x}-\overline{y})≤0
\end{cases}.
$$
By adding the inequalities together we have
$$
\begin{aligned}
(x-\overline{x})^T(\overline{y}-\overline{x}) + (y-\overline{y})^T(\overline{x}-\overline{y}) &≤ 0 \\
x^T\overline{y} - x^T\overline{x} - \overline{x}^T\overline{y} + \overline{x}^T\overline{x} + y^T\overline{x} - y^T\overline{y} - \overline{y}^T\overline{x} + \overline{y}^T\overline{y} &≤0
\end{aligned}
$$
By collecting the terms we get
$$
\begin{aligned}
(\overline{x}-\overline{y})^T(\overline{x}-\overline{y}) - (x-y)^T(\overline{x}-\overline{y})&≤0 \\
(\overline{x}-\overline{y})^T(\overline{x}-\overline{y}) &≤ (x-y)^T(\overline{x}-\overline{y}) \\
&= \|(x-y)\| \|\overline{x}-\overline{y}\| \cos θ \\ 
&≤ \|(x-y)\| \|\overline{x}-\overline{y}\| \\
\|\overline{x}-\overline{y}\|^2 &≤ \|(x-y)\| \|\overline{x}-\overline{y}\|
\end{aligned}
$$
Finally dividing by $\|\overline{x}-\overline{y}\|≥0$ we have
$$
\|\overline{x}-\overline{y}\| ≤ \|x-y\|.
$$

# Exercise 2.3
**The definition of a convex set**: A set $S⊆𝐑^n$ is said to be convex if $\overline{x}=∑_{j=1}^k λ_j x_j$ belongs to $S$, where $∑λ_j=1$, $λ_j≥0$ and $x_j∈S$ for $j=1,...,k.$

In each of the following sections, we determine the convexity of set $S$ by testing if element $\overline{x}$ belong to the set $S.$ 

## (a)
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

## (b) 
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

## (c)
Let test if element $\overline{x}$ belong to the set $S.$ Elements of set $S$ must satisfy the constraints $a_i^Tx≤b_i$ for all $x∈S$ and $i∈\{1,2\}$. Then
$$
a_i^T \overline{x}= a_i^T ∑_{j=1}^k λ_j x_j = ∑_{j=1}^k λ_j (a_i^T x_j) ≤ ∑_{j=1}^k λ_j b_i = b_i ∑_{j=1}^k λ_j = b_i, ∀i∈\{1,2\}
$$
which implies that $\overline{x}∈S$ and set $S$ is convex.

## (d)
Let test if element $\overline{x}$ belong to the set $S.$ Elements of set $S$ must satisfy the constraints $x=A^Ty$ for all $x∈S$. Then
$$
\overline{x}=∑_{j=1}^k λ_j x_j = ∑_{j=1}^k λ_j A^T y = A^T y ∑_{j=1}^k λ_j = A^T y
$$
which implies that $\overline{x}∈S$ and set $S$ is convex.

# Exercise 2.4
**Convexity of function**: Let $f:S→𝐑$  where $S⊆𝐑^n$ is a nonempty convex set. The function $f$ is said to be convex on $S$ if 
$$
f(λx_1+(1-λ)x_2) ≤ λf(x_1) + (1-λ)f(x_2)
$$
for each $x_1,x_2∈S$ and for each $λ∈(0,1).$

**Convexity under composition**: Let $S⊆𝐑^n$ be a nonempty convex set. Let $h:S→𝐑$ be a convex function, and let $g:𝐑→𝐑$ be a monotonically non-decreasing convex function over the set $\{h(x):x∈S\}.$ Then the composition 
$$
f(x)=g(h(x))
$$
is convex.

## (a)
Let $g:𝐑→𝐑$ be a convex function, $A$ an $m×n$ matrix, and $b$ a vector in $𝐑^m.$ Show that 
$$
f(x)=g(Ax+b)
$$
is a convex function.

---

We can show the convexity directly using the definition
$$
\begin{aligned}
f(λx_1+(1-λ)x_2) &= g(A(λx_1+(1-λ)x_2)+b) \\
&= g(λAx_1+(1-λ)Ax_2+λb+(1-λ)b) \\
&= g(λ(Ax_1+b)+(1-λ)(Ax_2+b)) \\
&≤ λg(Ax_1+b)+(1-λ)g(Ax_2+b) \\
&= λf(x_1)+(1-λ)f(x_2).
\end{aligned}
$$

## (b)
Let $h:𝐑^n→𝐑$ be a convex function, and let $α∈𝐑$, $β∈𝐑$ be scalars with $α≥0.$ Show that
$$
f(x)=αh(x)+β
$$
is a convex function

---

Using the definition we have
$$
h(λx_1+(1-λ)x_2) ≤ λh(x_1) + (1-λ)h(x_2)
$$
Then multiplying by $α≥0$ and adding $β$ we get
$$
\begin{aligned}
f(λx_1+(1-λ)x_2) &= αh(λx_1+(1-λ)x_2)+β \\
&≤ αλh(x_1) + α(1-λ)h(x_2) + β \\
&= αλh(x_1) + α(1-λ)h(x_2) + λβ+(1-λ)β \\
&= λ(αh(x_1)+β)+(1-λ)(αh(x_2)+β) \\
&= λf(x_1)+(1-λ)f(x_2)
\end{aligned}
$$

(I could also have used convexity under composition here.)

## (c)
Let $A$ be a positive semidefinite symmetric $n×n$ matrix and $β∈𝐑$ a scalar with $β>0$. Show that
$$
f(x)=\exp(βx^TAx)
$$
is convex.

---

We can write the function $f$ as a composition
$$
f(x)=g(h(x))
$$
where $g(y) = \exp(βy)$ and $h(x) = x^TAx.$ 

Now we can show that $f(x)$ is convex using convexity under composition:

1) $g$ is monotonically non-decreasing convex function over the set $\{h(x):x∈S\}.$ 

Because $A$ is positive semidefinite, $h(x)=x^TAx≥0$ for all $x∈S$. Since $g$ is exponential function and coefficient $β$ is positive, it is non-decreasing over the set $\{h(x):x∈S\}$ because the elements are greater of equal to zero.

2) $h(x)$ is a convex function.

We can write $h(x)$ into form $g'(h'(x))$ where $g'(x)=x^T h'(x)$ and $h'(x)=Ax.$ Since $g'$ is convex and $h'$ is affine, the function $h(x)$ is convex.

<!-- $$
\begin{aligned}
h(λx_1+(1-λ)x_2)&=(λx_1+(1-λ)x_2)^T A (λx_1+(1-λ)x_2) \\
&= λ^2 x_1^T A x_1 + λ(1-λ) (x_1^T A x_2 + x_2^T A x_1) + (1-λ)^2 x_2^T A x_2
\end{aligned}
$$

...

$$
\begin{aligned}
&≤λx_1^T A x_1 + (1-λ)x_2^T A x_2 \\
&=λh(x_1) + (1-λ)h(x_2)
\end{aligned}
$$ -->


<!-- # References -->

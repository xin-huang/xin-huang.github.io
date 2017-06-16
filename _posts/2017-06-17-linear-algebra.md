---
layout: post
title: Linear Algebra
date: 2017-06-17
category: notes
tags: [Mathematics]
use_math: true
---

Here, I record several notes for linear algebra.

<!-- more -->

1. **Subspace**: A subspace of $\mathbb{R}^n$ is a set $S$ satisfying conditions:
    1. $\vec{0}\in S$.
    2. $\vec{v}_1,\vec{v}_2\in S\Rightarrow \vec{v}_1+\vec{v}_2\in S$.
    3. $c\in\mathbb{R}, \vec{v}\in S\Rightarrow c\vec{v}\in S$.
    
Note: $\mathbb{R}^n$ is a set with elements $\left(x_1,x_2,\cdots,x_n\right)^\top, x_i\in\mathbb{R}^n, 1\leq i \leq n$.

2. **Invariant subspace**: A subspace $\mathcal{V}\subset\mathbb{F}^n$ is called invariant for $A$ if $A\mathcal{V}\subset\mathcal{V}$.

3. **Null space**: The nullspace of a matrix $A$ is $\mathcal{N}(A)=\{\vec{x}\in\mathbb{R}^n|A\vec{x}=\vec{0}\}$. Here, $A\vec{x}=\vec{0}$ is so-called *homogeneous*. If $\mathcal{N}(A)=\left\{\vec{0}\right\}$, then the column vectors of $A$ are linearly independent.

4. **Column space**:

5. The Fundamental Theorem of Linear Algebra:
    1. (Dimensions of four subspaces) The column space and row space have equal dimension $r$ = rank. The null space $\mathcal{N}(A)$ has dimension $n-r$, $\mathcal{N}(A^\top)$ has dimension $m-r$.
    2. (Relationship between subspaces):
        1. $\mathcal{C}(\mathbf{A}^\top)=\mathcal{N}(\mathbf{A})^\bot$ in $\mathbb{R}^n$
        2. $\mathcal{N}(\mathbf{A}^\top)=\mathcal{C}(\mathbf{A})^\bot$ in $\mathbb{R}^m$
    3. (Orthonormal bases for four subspaces)
    
6. Real matrices can have complex eigenvalues. If complex eigenvalues exist, then they occur in complex conjugate pairs. In other words, if $(\lambda,\vec{x})$ is an eigenpair of the real matrix $A$, then $(\bar{\lambda},\bar{\vec{x}})$ is also an eigenpair of $A$.
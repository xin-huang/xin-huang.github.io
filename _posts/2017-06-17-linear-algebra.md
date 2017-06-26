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

1. For matrices, there are three kinds:
    1. Fat matrices: The number of columns is larger than the number of rows.
    2. Slim matrices: The number of rows is larger than the number of columns.
    3. Squared matrices: The number of rows is equal to the number of columns. We like squared matrices most, because they have nice properties. There are another three kinds:
        1. Diagonal matrices: The non-zero elements are only in the diagonal. We like diagonal matrices most, also because they have nice properties.
        2. Upper triangular matrices: The non-zero elements are in/above the diagonal.
        3. Lower triangular matrices: The non-zero elements are in/under the diagonal.
2. Given a matrix $\mathbf{A}_{m\times n}$, we would like to consider its four subspaces:
    1. Column space $\mathcal{R}(\mathbf{A})$ (We also call column space as *range*).
    2. Row space $\mathcal{R}(\mathbf{A}^\top)$.
    3. Null space $\mathcal{N}(\mathbf{A})$: The subspace contains $\mathbf{x}$, where $\mathbf{Ax}=\mathbf{0}$.
    4. Left null space $\mathcal{N}(\mathbf{A}^\top)$.
    5. The Fundamental Theorem of Linear Algebra: It tells us three things:
        1. Dimensions of four subspaces:
            1. $\dim(\mathcal{R}(\mathbf{A}))=r$, where $r$ is the rank of $\mathbf{A}$.
            2. $\dim(\mathcal{R}(\mathbf{A}^\top))=r=\dim(\mathcal{R}(\mathbf{A}))$.
            3. $\dim(\mathcal{N}(\mathbf{A}))=n-r$.
            4. $\dim(\mathcal{N}(\mathbf{A}^\top))=m-r$.
        2. Relationship between subspaces:
            1. $\mathcal{R}(\mathbf{A})\bot\mathcal{N}(\mathbf{A}^\top)$ in $\mathbb{R}^m$.
            2. $\mathcal{R}(\mathbf{A}^\top)\bot\mathcal{N}(\mathbf{A})$ in $\mathbb{R}^n$.
        3. Orthonormal bases for four subspaces (Because we have subspaces, it is natural to think orthonormal bases of these subspaces): Suppose $(\sigma_i^2, \mathbf{v}_i)$'s are the eigenpairs of $\mathbf{A}^\top\mathbf{A}$, where $\mathbf{v}$'s are the orthonormal eigenvectors.
            1. There are $r$ orthonormal bases $\mathbf{v}$'s in $\mathcal{R}(\mathbf{A}^\top)$, where $\mathbf{Av}_i=\sigma_i\mathbf{u}_i$.
            2. There are $n-r$ orthonormal bases $\mathbf{v}$'s in $\mathcal{N}(\mathbf{A})$, where $\mathbf{Av}_i=\mathbf{0}$.
            3. The $r$ orthonormal bases of $\mathcal{R}(\mathbf{A})$ are $\mathbf{u}$'s, where $\mathbf{A}^+\mathbf{u}_i=\mathbf{v}_i/\sigma_i$. $\mathbf{A}^+$ is the pseudoinverse of $\mathbf{A}$.
            4. The $m-r$ orthonormal bases of $\mathcal{N}(\mathbf{A}^\top)$ are $\mathbf{u}$'s, where $\mathbf{A}^+\mathbf{u}_i=\mathbf{0}$.
        4. The orthonormal bases of four subspaces lead to sigular value decomposition (SVD). Let $\mathbf{V}=[\mathbf{v}_1,\mathbf{v}_2,\cdots,\mathbf{v}_n]$, $\mathbf{U}=[\mathbf{u}_1,\mathbf{u}_2,\cdots,\mathbf{u}_m]$, then we have $$\mathbf{AV}=\mathbf{U}\boldsymbol{\Sigma}$$ where $\boldsymbol{\Sigma}=\text{diag}(\sigma_1,\sigma_2,\cdots,\sigma_r,\cdots,0)$. In other words, $\mathbf{A}=\mathbf{U}\boldsymbol{\Sigma}\mathbf{V}^\top$, which is the SVD of $\mathbf{A}$.

3. **Subspace**: A subspace of $\mathbb{R}^n$ is a set $S$ satisfying conditions:
    1. $\vec{0}\in S$.
    2. $\vec{v}_1,\vec{v}_2\in S\Rightarrow \vec{v}_1+\vec{v}_2\in S$.
    3. $c\in\mathbb{R}, \vec{v}\in S\Rightarrow c\vec{v}\in S$.
    
    Note: $\mathbb{R}^n$ is a set with elements $\left(x_1,x_2,\cdots,x_n\right)^\top, x_i\in\mathbb{R}^n, 1\leq i \leq n$.
    
4. **Pseudoinverse**

5. Eigen problems
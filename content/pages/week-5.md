---
content_type: page
description: This section covers Lectures 12-14.
draft: false
learning_resource_types: []
ocw_type: CourseSection
title: Week 5
uid: a4d71ca2-18aa-0275-e844-5a9cbf900105
---
## Lecture 12: Cache-Oblivious Algorithms and Spatial Locality

### Summary

Introduced the concept of optimal cache-oblivious algorithms. Discussed cache-oblivious matrix multiplication in theory and in practice (see handout and {{% resource_link "875b6646-cee2-4ea1-acb4-52fb4dc65dbb" "Cache-Oblivious Algorithms" %}} by Matteo Frigo et al below).

Discussion of spatial locality and cache lines, with examples of dot products and matrix additions (both of which are "level 1 BLAS" operations with no temporal locality); you'll do more on this in Problem set 3.

- Lecture 12 handout: {{% resource_link "94f02a07-3e2e-6c15-27e2-4c71ba8741f4" "Experiments with Cache-Oblivious Matrix Multiplication (PDF)" %}}
- Lecture 12 notebook: {{% resource_link "e9941dde-dd4b-4975-a271-1a93f62789e9" "Experiments with Memory Access and Matrices" %}}

### Further Reading

- {{% resource_link "b37f1d7d-6f25-4a65-8574-8e26210b3ad4" "Automatically Tuned Linear Algebra Software (ATLAS)" %}}
- {{% resource_link "875b6646-cee2-4ea1-acb4-52fb4dc65dbb" "Cache-Oblivious Algorithms" %}} by Matteo Frigo, et al.
- {{% resource_link "5666685d-9f3c-4bbb-9bd2-645a8153de58" "Register Allocation in Kernel Generators (PDF)" %}} by Matteo Frigo
- {{% resource_link "9f0fbced-ccb6-4966-a6ac-91dba6961ef3" "Row- and column-major order" %}} on Wikipedia

## Lecture 13: LU Factorization and Partial Pivoting

### Summary

Review of Gaussian elimination. Reviewed the fact that this gives an A=LU factorization, and that we then solve Ax=b by solving Ly=b (doing the same steps to b that we did to A during elimination to get y) and then solving Ux=y (back substitution). Emphasized that you should almost never compute A{{< sup "\-1" >}} explicitly. It is just as cheap to keep L and U around, since triangular solves are essentially the same cost as a matrix-vector multiplication. Computing A{{< sup "\-1" >}} is usually a mistake: you can't do anything with A{{< sup "\-1" >}} that you couldn't do with L and U, and you are wasting both computations and accuracy in computing A{{< sup "\-1" >}}. A{{< sup "\-1" >}} is useful in abstract manipulations, but whenever you see "x=A{{< sup "\-1" >}}b" you should interpret it for computational purposes as solving Ax=b by LU or some other method.

Introduced partial pivoting, and pointed out (omitting bookkeeping details) that this can be expressed as a PA=LU factorization where P is a permutation. Began to discuss backwards stability of LU, and mentioned example where U matrix grows exponentially fast with m to point out that the backwards stability result is practically useless here, and that the (indisputable) practicality of Gaussian elimination is more a result of the types of matrices that arise in practice.

### Further Reading

- Read “Lectures 20–23” in the textbook *Numerical Linear Algebra*.

## Lecture 14: Cholesky Factorization and other Specialized Solvers. Eigenproblems and Schur Factorizations

### Summary

Briefly discussed Cholesky factorization, which is Gaussian elimination for the special case of Hermitian positive-definite matrices, where we can save a factor of two in time and memory. More generally, if the matrix A has a special form, one can sometimes take advantage of this to have a more efficient Ax=b solver, for example: Hermitian positive-definite (Cholesky), tridiagonal or banded (linear-time solvers), lower/upper triangular (forward/back substitution), sparse (mostly zero—sparse-direct and iterative solvers, to be discussed later; typically only worthwhile when the matrix is much bigger than 1000×1000).

New topic: eigenproblems. Reviewed the usual formulation of eigenproblems and the characteristic polynomial, mentioned extensions to generalized eigenproblems and SVDs. Discussed diagonalization, defective matrices, and the generalization of the Schur factorization.

Discussed diagonalization, defective matrices, and the generalization of the Schur factorization. Proved (by induction) that every (square) matrix has a Schur factorization, and that for Hermitian matrices the Schur form is real and diagonal.

### Further Reading

- Read “Lectures 20–23” in the textbook *Numerical Linear Algebra*.
- See all of the special cases of LAPACK's {{% resource_link "8300eb43-f687-497a-b964-02b0f4e79105" "Linear Equations" %}}.
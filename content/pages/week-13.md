---
content_type: page
description: This section covers Lectures 35-37.
draft: false
learning_resource_types: []
ocw_type: CourseSection
title: Week 13
uid: f0c2e826-9307-e9b8-dfff-15f04276fcac
---
## Lecture 35: Chebyshev Approximation

### Summary

Explained connection of Clenshaw-Curtis quadrature and cosine series to Chebyshev polynomials. This leads into the general topic of Chebyshev approximation, and how we can approximate any smooth function on a finite interval by a polynomial with exponential accuracy (in the degree of the polynomial) as long as we interpolate via Chebyshev points.

Using Chebyshev approximation, explained how lots of problems can be solved by first approximating a nasty function via a polynomial, at which point one can just use easy methods for polynomials. Showed examples of root finding, minimization, integration, and solving ODEs via the {{% resource_link "0163c0ec-a36a-4eb6-817a-24bd62d810e2" "ApproxFun" %}} package for Julia, which implements a modern version of these ideas (following in the tracks of the pioneering {{% resource_link "8cb01c4d-158a-49c2-b4e2-67817c5eed28" "Chebfun" %}} package for MATLAB).

### Further Reading

- {{% resource_link "5b3bb351-ed6c-4743-b2e8-223c92a0cada" "Chebyshev polynomials" %}} on Wikipedia.
- Online book {{% resource_link "7faf1654-a837-42c9-af21-712a60a143cb" "Chebyshev and Fourier Spectral Methods" %}} by John P. Boyd.

## Lecture 36: Integration with Weight Functions, and Gaussian Quadrature

### Summary

Discussed integration with weight functions: I = ∫w(x)f(x)dx ≈ I\\(_n\\) = ∑w\\(_i\\)f(x\\(_i\\)). Even if the "weight" w(x) is "nasty" (discontinuous, singular, highly oscillatory…), we can do some (possibly expensive) precomputations of w\\(_i\\) and x\\(_i\\) *once* and re-use them for integrating many "nice" (smooth) functions f(x) with only a few quadrature points.

One approach to this is weighted Clenshaw-Curtis quadrature: expand f(x) in Chebyshev polynomials, i.e. f(cosθ) in a cosine series, as before via a trapezoidal rule (DCT), and then compute the integrals ∫w(cosθ)cos(kθ)sin(θ)dθ in whatever way you can … possibly by a very slowly converging method, but you only need to compute these weight integrals *once* and can then re-use them for many different f(x).

An alternative approach (for real w ≥ 0, and w > 0 almost everywhere) is {{% resource_link "195da907-1ad3-4a69-9817-89eddb5e5f2b" "Gaussian quadrature" %}}: fit f(x) to a polynomial of degree n–1 by evaluating at n points consisting of the roots of an orthogonal polynomial q\\(<em>{n+1}\\) of degree n, where the polynomials {q\\(_1\\),q\\(_2\\),…} are formed via Gram-Schmidt orthogonalization of the basis {1,x,x\\(^2\\),…} with the inner product (p,q)=∫w(x)p(x)q(x)dx. There is a beautiful proof that this integrates polynomials exactly up to degree 2n–1, it takes w(x) into account analytically, and by a more complicated analysis it converges exponentially for analytic f. Moreover, it turns out that finding {q\\(_1\\),q\\(_2\\),…} is equivalent to performing the Lanczos iteration with the real-symmetric linear operator x, leading to a three-term recurrence. We already saw one such three-term recurrence for the Chebyshev polynomials T\\(_n\\)(x), corresponding to the weight \\(\text{w(x)}=1/\sqrt{1-\text{x}^2}\\), and other weight functions give rise to other orthogonal polynomials with their own 3-term recurrences: w=1 gives {{% resource_link "f90c8207-4443-42f7-a228-790f74b7f358" "Legendre polynomials" %}}, but there are also {{% resource_link "e72eff78-b00d-4ad2-ba80-46c8199d3d6a" "Gegenbauer polynomials" %}}, {{% resource_link "eac31ce5-f721-4704-abdc-50ce8cd423ba" "Laguerre polynomials" %}} for w=e\\(^{-x}\\) on 0…\\(\infty\\), {{% resource_link "3ff86b64-f87d-478b-bc18-33558d84d3bb" "Hermite polynomials" %}} for w=exp(-x\\(^2\\)) on -\\(\infty\\)…+\\(\infty\\), and others. Moreover, the Lanczos tridiagonal eigenvalues turn out to be precisely the roots of q\\(</em>{n+1}\\) that we want, while the eigenvectors turn out to give the weights, and for a long time this surprising(!) O(n\\(^2\\)) "Golub-Welsch" method was the method of choice for finding Gaussian quadrature nodes and weights.

### Further Reading

- {{% resource_link "d82e2947-8109-4783-bfb9-e5d4f35c4cea" "A Comparison of Some Methods for the Evaluation of Highly Oscillatory Integrals" %}} (by G.A. Evans and J.R.Webster) describes the weighted Clenshaw-Curtis approach to oscillatory integrals.
- {{% resource_link "a0472f2a-8f29-49ac-80cd-58030a9cba87" "Numerical Approximation of Highly Oscillatory Integrals (PDF)" %}} by Sheehan Olver.
- Read “Lecture 37” in the textbook *Numerical Linear Algebra*.
- O(n) methods have been discovered to find the Gaussian quadrature points and weights; see the references in the Julia {{% resource_link "30932fcd-9875-4419-a214-09b29e06e7ae" "FastGaussQuadrature" %}} package.
- An influential recent comparison of Clenshaw-Curtis and Gaussian quadrature is: Trefethen, Lloyd N. {{% resource_link "bc50003d-74b7-4429-8c3f-deb6fab7e1d1" "Is Gauss Quadrature Better Than Clenshaw-Curtis?" %}}, *SIAM Review* 50 (1), 67-87 (2008).

## Lecture 37: Adaptive and Multidimensional Quadrature

### Summary

Discussed the importance of nested quadrature rules for *a posteriori* error estimation (Clenshaw-Curtis, Gauss-Kronrod, Gauss-Patterson) and adaptive quadrature. Discussed p-adaptive vs. h-adaptive adaptive schemes. Talked about multidimensional integration and the curse of dimensionality.
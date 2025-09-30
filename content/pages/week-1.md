---
content_type: page
description: This section covers Lectures 1-2.
draft: false
learning_resource_types: []
ocw_type: CourseSection
title: Week 1
uid: 6950d4a0-73bc-0d04-aa63-962ae31c42a2
---
## Lecture 1: Course Overview, Newton's Method for Root-Finding

### Summary

Brief overview of the huge field of numerical methods and outline of the small portion that this course will cover. Key new concerns in numerical analysis, which don't appear in more abstract mathematics, are (i) performance (traditionally, arithmetic counts, but now memory access often dominates) and (ii) accuracy (both floating-point roundoff errors and also convergence of intrinsic approximations in the algorithms).

As a starting example, we considered the convergence of Newton's method (as applied to square roots); see the handout and Julia notebook below.

- Lecture 1 handout: {{% resource_link "0a734ecc-94b6-0a26-2134-88e68588bc8d" "Square Roots via Newton's Method (PDF)" %}}
- Lecture 1 notebook: {{% resource_link "bb8c23c1-e445-4efa-bcad-b12d14546cab" "Square Roots" %}}

### Assignment

- {{% resource_link "6e673088-5b20-bd04-6cbd-e805d15a4835" "Problem set 1 (PDF)" %}}
- Problem set 1 notebook: {{% resource_link "6ef8b983-dd83-43a6-a965-b1ba2038d987" "Problem set 1" %}}
- {{% resource_link "e03746c6-51f0-a76f-651d-918a0aa0dd10" "Problem set 1 solutions (PDF)" %}}
- Problem set 1 solutions notebook: {{% resource_link "ae93a1e3-8c06-4a3e-93c7-f7326af66a89" "Problem set 1 solutions" %}}

### Further Reading

- [Newton's method](https://en.wikipedia.org/wiki/Newton's_method) from Wikipedia is a reasonable starting point. Googling "Newton's method" can find lots of references.
- Beware that the terminology for the {{% resource_link "8445d0c7-75e6-446f-9c64-d5147b170b47" "rate of convergence" %}} (linear, quadratic, etc.) is somewhat different in this context from the terminology for discretization schemes (first-order, second-order, etc.); see e.g. the linked Wikipedia article.

## Lecture 2: Floating-Point Arithmetic

### Summary

The basic issue is that, for computer arithmetic to be fast, it has to be done in hardware, operating on numbers stored in a fixed, finite number of digits (bits). As a consequence, only a *finite subset* of the real numbers can be represented, and the question becomes *which subset* to store, how arithmetic on this subset is defined, and how to analyze the errors compared to theoretical exact arithmetic on real numbers.

In floating-point arithmetic, we store both an integer coefficient and an exponent in some base: essentially, scientific notation. This allows large dynamic range and fixed *relative* accuracy: if fl(*x*) is the closest floating-point number to any real *x*, then |fl(*x*)-*x*| \< ε|*x*| where ε is the *machine precision*. This makes error analysis much easier and makes algorithms mostly insensitive to overall scaling or units, but has the disadvantage that it requires specialized floating-point hardware to be fast. Nowadays, all general-purpose computers, and even many little computers like your cell phones, have floating-point units.

Went through some simple examples in Julia (see notebook below), illustrating basic syntax and a few interesting tidbits, in particular on the accuracy of summation algorithms, that we will investigate in more detail later.

Overview of floating-point representations, focusing on the IEEE 754 standard (see also handout from previous lecture). The key point is that the nearest floating-point number to *x*, denoted fl(*x*), has the property of *uniform relative precision* (for |*x*| and 1/|*x*| less than some *range*, ≈10308 for double precision) that |fl(*x*)−*x*| ≤ εmachine|*x*|, where εmachine is the relative "machine precision" (about 10−16 for double precision). There are also a few special values: ±Inf (e.g. for {{% resource_link "5823a443-6021-49a8-b568-7c40ca8f9646" "overflow" %}}), {{% resource_link "00d8d69d-2436-4d39-a94d-8381c433af18" "NaN" %}}, and ±0 (e.g. for {{% resource_link "31558313-34e7-477b-8d34-504788e514e4" "underflow" %}}).

- Lecture 2 handout:
- {{% resource_link "76b99473-7db1-4d72-b6e5-58f063c9e78c" "Floating-Point Arithmetic" %}}
- {{% resource_link "88129903-3165-275f-3b15-ae8b172e6de8" "Some Myths about Floating-Point Arithmetic (PDF)" %}}

### Further Reading

- {{% resource_link "43936ec1-adc1-45ef-959d-9e5f7eeef8d5" "What Every Computer Scientist Should Know About Floating Point Arithmetic" %}} by David Goldberg.
- {{% resource_link "fdd9f5c6-fbdf-4290-8c95-8d5aadff5824" "How Java’s Floating-Point Hurts Everyone Everywhere (PDF)" %}} by William Kahan and Joseph Darcy. This article contains a nice discussion of floating-point myths and misconceptions.
- Read “Lecture 13” in the textbook *Numerical Linear Algebra*.

## Julia Tutorial

We introduced {{% resource_link "9101ae10-24db-4814-9cdc-8c8b05d41f70" "the Julia Programming Language" %}} that we will use this term.

- {{% resource_link "fb66800c-466e-fd52-4aa5-d76ddf928bf5" "Julia & IJulia Cheat-Sheet (PDF)" %}}
- {{% resource_link "ff680e9d-d985-7804-f64e-6f3bf523f80e" "Introduction to Julia (PDF)" %}}
- {{% resource_link "e6fc46e4-e11c-4bb2-adac-7c554a15d07b" "Julia for Numerical Computation in MIT Courses" %}}
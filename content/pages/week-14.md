---
content_type: page
description: This section covers Lectures 38 and 39.
learning_resource_types: []
ocw_type: CourseSection
title: Week 14
uid: 91f42844-de39-df8a-3812-24c45f7815b4
---

Lecture 38: The Discrete Fourier Transform (DFT) and FFT Algorithms
-------------------------------------------------------------------

### Summary

Introduced the {{% resource_link "9fd65811-b6a2-460d-a418-330475235c31" "discrete Fourier transform (DFT)" %}}. Talked about its history (Gauss!), properties (unitarity, convolution theorem), aliasing, special case of the type-1 {{% resource_link "b1fddeff-9314-4bfb-90e2-23b599aa0eed" "discrete cosine transform (DCT)" %}}, and applications (Chebyshev and other spectral methods for integration, PDEs, etcetera; signal processing, {{% resource_link "8e02e480-e5c0-46df-a951-0fb59ad455f7" "Schönhage-Strassen algorithm" %}}), etc.

A {{% resource_link "262aa24f-1723-49d2-adac-c0976dd9671f" "fast Fourier transform (FFT)" %}} is an O(_N_ log _N_) algorithm to compute the discrete Fourier transform. There are many such algorithms, the most famous of which is the Cooley-Tukey algorithm (1965, though there were many precursors dating back to Gauss himself).

*   Lecture 38 handout: {{% resource_link edf5b798-bef2-f1cf-e687-a6bfcd32a03a "Fast Fourier Transform Algorithms (PDF)" %}}

Lecture 39: FFT Algorithms and FFTW
-----------------------------------

### Summary

Continued on fast Fourier transform (FFT). Talked about fast Fourier transform in the west (FFTW). The fast Fourier transform in the west is a software library for computing discrete Fourier transforms (DFTs) developed by Matteo Frigo and Steven G. Johnson at MIT. FFTW is known as the fastest free software implementation of the fast Fourier transform (FFT) (upheld by regular benchmarks). Like many other implementations, it can compute transforms of real and complex-valued arrays of arbitrary size and dimension in O(_N_ log _N_) time.

*   Lecture 39 handout: {{% resource_link f4e0fe09-545f-cf1a-9fa8-928385fcf412 "Fast Fourier Transform and Fast Fourier Transform in the West (PDF - 2.6MB)" %}}
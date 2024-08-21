+++
title = 'GSoC24 @Sagemath: Final Report'
date = 2024-08-21T22:25:22+07:00
draft = false
tags = ["tropical algebra", "GSoC"]
categories = ["mathematics"]
author = "verreld7"
showtoc = true
UseHugoToc = false
tocopen = true
+++

## Overview
This summer I participate in Google Summer of Code (GSoC) project: [Implementation of Tropical Polynomials and its Corresponding Tropical Hypersurfaces](https://summerofcode.withgoogle.com/myprojects/details/j1yAryTd).

My primary task was to implement tropical polynomials in Sagemath, where I focused on creating new classes that extend polynomial implementation to support coefficient from tropical semirings, along with several methods to manage various functionality.  Additionally, I implemented a class for tropical varieties, which facilitates the visualization of tropical hypersurfaces for multivariate tropical polynomials.

## Work Report

List of relevant issues and pull requests:
* [GSoC 2024: Meta-Ticket for implementing a tropical polynomials #37962](https://github.com/sagemath/sage/issues/37962)
* [Implement a custom class for tropical polynomials #38291](https://github.com/sagemath/sage/pull/38291)

### New classes for Tropical Polynomials :star:
Developed new element classes specifically designed to handle tropical polynomials, building on the existing tropical semiring implementation in SageMath. We've created a separate class for univariate and multivariate cases, along with a parent class that encapsulates the semiring structure. These classes support operations like (tropical) addition, multiplication, and exponentiation (with scalar).

### Univariate Tropical Polynomials 📈
We developed and implemented an algorithm to find the tropical roots of univariate tropical polynomials. These roots allow us to determine the tropical polynomial function, which is essentially a piecewise linear function. Using these result, we can then plot the graph of the tropical polynomial. A few examples of the graph:

|![](../images/polyplot1.png) | ![](../images/polyplot2.png)  |
|:-:|:-:|
| Figure 1. Graph of $0x^2 + -1x + 1$ (max-plus algebra) | Figure 2. Graph of $0x^2 + -1x + 1$ (min-plus algebra)|

|![](../images/polyplot3.png) | ![](../images/polyplot4.png)  |
|:-:|:-:|
| Figure 3. Graph of $-1x^5 + \frac{1}{3}x^4 + 1x^2 + \frac{1}{3}x$ (max-plus algebra) | Figure 4. Graph of $-1x^5 + \frac{1}{3}x^4 + 1x^2 + \frac{1}{3}x$  (min-plus algebra)|

The classes for univariate case can also handle interpolation of points, finding the split form, and determining the tropical factorization.

### Tropical Variety
A tropical variety is defined as the corner locus of a tropical polynomial function, consisting of all points in $\mathbb{R}^n$ where the minimum (or maximum) of the function is attained at least twice. We developed and implemented an algorithm to compute the tropical variety for any multivariate tropical polynomial, with the ability to visualize these varieties in the cases of two and three variables. For dimensions greater than three, the result is also referred to as tropical hypersurface.

#### Tropical Curve :two:
A tropical curve is a piecewise linear structure in $\mathbb{R}^2$ which can be seen as *tropical roots* of tropical polynomials in two variables.  For these polynomials, we can also plot their graph, which consist of multiple surfaces in three dimensions. Some examples of these are:

|![](../images/tcurve1.png)  | ![](../images/mpolyplot3d1.png)   |
|:-:|:-:|
|Figure 5. Tropical Curve of $-2x^2 + -1x + \frac{1}{2}y$| Figure 6. Graph of $-2x^2 + -1x + \frac{1}{2}y$ |

|![](../images/tcurve2.png)  |![](../images/mpolyplot3d2.png)   |
|:-:|:-:|
|Figure 7. Tropical Curve of $2x^2 + 0xy + 2y^2 + 0x + -1y + 3$ | Figure 8. Graph of $2x^2 + 0xy + 2y^2 + 0x + -1y + 3$ |

#### Tropical Surface :three:
A tropical surface is a piecewise linear structure in $\mathbb{R}^3$ which can be seen as *tropical roots* of tropical polynomials in three variables.  The tropical surface consists of planar regions and facets, referred to as cells. Some examples of these are:

|![](../images/tsurface1.png) | ![](../images/tsurface2.png) |
|:-:|:-:|
|Figure 9. Tropical Surface of $0x + 0y + 0z$|Figure 10. Tropical Surface of $0x^2 + 0xyz + 0x + 0y + 0z + 1$|

### Dual Subdivision 🔗
Dual subdivision is a subdivision of the Newton polygon of tropical polynomials. This subdivision is *dual* in the sense that each face of the subdivision corresponds to a vertex of the tropical curve, and each edge of the subdivision corresponds to an edge of the tropical curve. This analogy extends to tropical varieties in higher dimensions, where the dual subdivision similarly reflects the structure of the variety. Some examples of these are:

|![](../images/dual1.png) | ![](../images/dual2.png) |
|:-:|:-:|
|Figure 11. Dual Subdivision of $2x^2 + 0xy + 2y^2 + 0x + -1y + 3$|Figure 12. Dual Subdivion of $0x^2 + 0xyz + 0x + 0y + 0z + 1$|

### Weight Vectors ↗
As seen before, a tropical curve consists of line segments and half-lines, referred to as edges. These edges meet at a vertices, where the balancing condition is satisfied. This balancing condition ensures that the sum of the outgoing slopes at each vertex equals zero, reflecting the equilibrium. Continuing from that, we have successfully extended the concept to tropical surfaces, where the sum of the outgoing normal vectors with respect to a line equals zero. Some examples are:

## Potential Future Improvements
* Generalizing the concept of weight vectors to tropical varieties of dimension $n \geq 4$
* Refactor polynomial classes for the semiring polynomials
* Extending the tropical polynomial semiring to Laurent polynomial iring

## Afterword
Creating new classes and implementing the complex algorithms for various methods was quite challenging. However, the satisfaction of seeing the expected results and the intricate, fascinating graphs made the effort worthwhile.

I would like to express my deepest gratitude to my mentor, Travis Scrimshaw for helpful meetings and email exchanges. His support and guidance were important during my time on the project. I'm also thankful to Google for organizing this incredible event. Moving forward, I hope to continue contributing to Sagemath. Until next time!

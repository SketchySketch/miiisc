---
title: Geo - Compasses , Straightedges and Analytical Geometry
excerpt: >-
  When the most ancient geometry meets the (relatively) new geometry
date: '2020-11-27'
template: post
---

> All contents in this page is original.

# "Old" Geometry: Compasses and Straightedges

Compass-and-straightedge construction is one of the oldest branch of geometry. _Elements_, by Euclid in ancient Greece, is a perfect example. Most of the time if we want to construct a geometrical object we prove it by geometrical properties or by trailing. Have you ever thought of -- proving the probability by **analytical geometry**?

# A Bit "Younger"

**Analytical geometry**, created by Discartes, is relatively new. With it we can describe geometrical objects by pure algebraic expressions. Should say, it's a common but creative connection between algebra and geometry.

Before we dive in, let's learn some fundamentals.

## Quardatic Curves

The equation for quadratic curves (circles, ellipses, parabolas, hyperbolas) is generally

_C: Ax<sup>2</sup> + Bxy + Cy<sup>2</sup> + Dx + Ey + F = 0_.

### Circles
A **circle** C with its center _(h,k)_ and radius _r_ can be expressed as

_C: (x-h)<sup>2</sup> + (y-k)<sup>2</sup> = r<sup>2</sup>_.

The length of the tangent line which goes through _(a,b)_ and _C_ is

_d = (a-h)<sup>2</sup> + (b-k)<sup>2</sup>_.

### Ellipses
An **ellipse** C centered at the original with its major radius _a_ and minor radius _b_ is

_C: x<sup>2</sup>/a<sup>2</sup> + y<sup>2</sup>/b<sup>2</sup> = 1_ or

_C':x<sup>2</sup>/b<sup>2</sup> + y<sup>2</sup>/a<sup>2</sup> = 1_, which the major radius of _C_ lies on the x-axis, and y-axis for _C'_.

Focal length of _C_ is _sqrt(a<sup>2</sup> - b<sup>2</sup>)_.

### Parabolas
A **parabola** can be expressed as

_y<sup>2</sup> = 2px_ or

_x<sup>2</sup> = 2py_.

### Hyperbolas
A **hyperbola** can be expressed as

_x<sup>2</sup>/a<sup>2</sup> - y<sup>2</sup>/b<sup>2</sup> = 1_.

Carefully compare this to an ellipse.

### Transformations
Let _C_ be a curve _f(x,y) = 0_. Then, if we move it up _a_ and right _b_, we should get

_C': f(x-a, y-b) = 0_.

## Quite Subtle Relation
So what on earth is the relation between compass-and-straightedge construction and analytical geometry?

It begins with a surprising discovery by myself a few days ago.

**Proposition 1: Given the length of _1_, _n_ reals _a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>_ and a rational polynomial _f(a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>)_. With a compass and a ruler we can construct the length of _f(a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>)_, _sqrt(f(a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>)_) and _1 / f(a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>)_.**

It might be quite unbelievable. Some may find it odd because of some reasons about *units*: We should be only able to construct *lines*, or *1-degree polynomials*. What I want to say is, that's the use of the length of *1*: let *deg(f) = n*, then *f / 1<sup>n-1</sup>* is exactly linear.

Let's prove that proposition.

### A Possible Proof
**Proposition A<sub>0</sub>: Given a rectangle. We can construct a square with the same area.**

It's possible because of the *projection theorem*.

**Proposition A: Given _1_ and _a_. We can construct _sqrt(a)_.**

It's obvious for we can construct a rectangle with its sides *a* and *1*.

**Proposition B<sub>0</sub>: Given _1_ and _a_. We can construct _a<sup>2</sup>_.**

It's a reverse of **Proposition A<sub>0</sub>**.

**Proposition B: Given _1_, _a_ and _b_. We can construct _ab_.**

It's obvious for we can construct _sqrt(ab)_ by using *projection theorem*.

**Proposition C: Given _a_ and a positive integer _n_, we can construct _a / n_.**

It's possible because of *proportional segment theorem*.

**Proposition D: Given _1_ and _a_, we can construct _1 / a_.**

It's a reverse of **Proposition B**, for _(1 / a) * a = 1_.

By proposition A, B, C and D, we finally proved the **Proposition 1**.

> The next post will be also related to compass-and-straightedge construction and analytical geometry. In the next post, I'll find a few examples to shhow the way of using the proposition.

---
date: '2026-03-18T13:10:53+02:00'
draft: false
title: 'Fundamentals of Physics - Chapter 6 Sample Problem 6.03'
categories: ['Physics']
tags: ['Physics']
math: true
---

# Question
A raindrop with radius $R = 1.5 mm$ falls from a cloud that is at height $h = 1200m$ above the ground. The drag coefficient $C$ for the drop is $0.60$. Assume that the drop is spherical throughout its fall. The density of water $\rho_w$ is $1000 kg/m3$, and the density of air $\rho_a$ is $1.2 kg/m3$.

The raindrop reaches terminal speed after falling just a few meters. What is the terminal speed?

# Answer
First let's convert the radius to meters, the base qunatity we are working with.

$$
1\ mm = \frac{1}{1000}\ m
\Rightarrow R = 1.5 \cdot 10^{-3} = 0.0015\ m
$$

The terminal speed of an object is defined as the constant maximum speed that an object reaches when falling through a fluid or gas under the influence of gravity. It occures when the downward force of gravity is perfectly balanced by the upward force of drag.
Hence:

Let $\vec{D_b}$ be that drag force which balances the system perfectly with gravity setting $a = 0$.

* Let the positive direction be upward - up the horizontal axis:

$$
\vec{D_b} + \vec{F_g} = 0 \Rightarrow \vec{D_b} = -\vec{F_g}
$$

And in vector magnitude, as we are asked about speed and do not care about directions:

$$
|\vec{D_b}| = |\vec{F_g}|
$$

$$
|\vec{D_b}| = |\frac{1}{2} \cdot C \cdot \rho_a \cdot Area \cdot s^{2}|
$$

* Area of a circle (The area of the drop "hitting" the air on the way down) = $\pi R ^2$.
* Dropping the absolute at the end as $s^2 >= 0$

$$
|\vec{D_b}| = |\frac{1}{2} \cdot 0.6 \cdot 1.2 \cdot \pi \cdot (0.0015^2) \cdot s^{2}| = 2.5434 \cdot 10^{-6} \cdot s^2
$$


* As the volume of a sphere is formulated by $\frac{4}{3} \cdot \pi \cdot R^{3}$
* ${density} = \frac{mass}{volume} \Rightarrow {mass} = {density} \cdot {volume}$
$$
|-\vec{F_g}| = |-(m \cdot g = density \cdot volume \cdot g = \rho_w \cdot \frac{4}{3} \cdot \pi \cdot R^{3} \cdot 9.8)|
$$

$$
= |-(1000 \cdot \frac{4}{3} \cdot \pi \cdot (0.0015)^{3} \cdot 9.8)| = |-1.38474 \cdot 10^{-4}| = 1.38474 \cdot 10^{-4} N
$$

We find now that

$$
2.5434 \cdot 10^{-6} \cdot s^2 = 1.38474 \cdot 10^{-4} \Rightarrow s^2 = \frac{1.38474 \cdot 10^{-4}}{2.5434 \cdot 10^{-6}} = 54.444
$$

$$
s_{terminal} = \sqrt{54.444} = 7.378 \frac{m}{s}
$$

✔️
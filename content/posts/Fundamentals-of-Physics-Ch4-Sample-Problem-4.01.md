---
date: '2026-03-12'
draft: false
title: 'Fundamentals of Physics - Chapter 4 Sample Problem 4.01'
categories: ['Physics']
tags: ['Physics']
math: true
---

# Questions

A rabbit runs across a parking lot on which a set of coordinate axes has, strangely enough, been drawn. The coordinates (meters) of the rabbit’s position as functions of
time $t$ (seconds) are given by:

$$
x = -0.31t^2 + 7.2t + 28 \newline
y = 0.22t^2 -9.1t + 30
$$

(a) At $t = 15s$ what is the rabbit's position vector $\vec{r}$ in unit-vector notation and in magnitude-angle notation ?

(b) Graph the rabbit’s path for $t=0$ to $t = 25s$

# Answers
(a)
Substituting $t = 15$ within the given equations we get:

$$
x = -0.31 \cdot (15)^2 + 7.2 \cdot 15 + 28 = 66.25 \newline
y = 0.22 \cdot (15)^2 - 9.1 \cdot 15 + 30 = -57.0
$$

Therefore, the coordinates for $t = 15s$ are $(66.25, -57)$, which can be expressed in unit-vector notation for the vector $\vec{r}$ as:

$$
\vec{r} = (66.25m)\hat{i} -(57m)\hat{j}
$$

In terms of manitude-angle notation, if we look at the position vector drawing:

![](/img/r_vector.png)

we know that $r_x = 66.25$ and $r_y = -57$, now to find $\theta$ we can use simple trigonometry:

$$
\tan{\theta} = \frac{r_y}{r_x} = \frac{-57}{66.25} \Rightarrow \theta = -42.47917209\degree
$$

To calculate $\vec{r}$ magnitude we use pythogras theorem:

$$
r = \sqrt{r_x^2 + r_y^2} = \sqrt{66.25^2+(-57)^2} = 87.396
$$

and hence we get the magnitude-angle notation for $\vec{r}$ as :

$$
(87.396m, -42.4791\degree)
$$

(b)
I'll be skipping in 5s and checking the coordinates for $t = 1, 5, 10, .., 25$.
Writing a small python snippet to calculate the results:

```python
>> [(-0.31*(t**2)+7.2*t+28, 0.22*(t**2)-9.1*t+30) for t in range(0, 25+1, 5)]
[(28.0, 30.0), (56.25, -10.0), (69.0, -39.0), (66.25, -57.0), (48.0, -64.0), (14.25, -60.0)]
```

Result Graph (Rabbit's Path on the coordinate system):
![](/img/RabbitPath.png)

✔️

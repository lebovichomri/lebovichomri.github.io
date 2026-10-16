---
date: '2026-03-17T21:50:02+02:00'
draft: false
title: 'Fundamentals of Physics - Chapter 6 Sample Problem 6.02'
categories: ['Physics']
tags: ["Physics"]
math: true
---

# Questions

(a) How far does it take for a car with initial velocity of $10 m/s$ to slide to a stop on a horizontal road if the coefficient of kinetic friction is $\mu = 0.6$ ?

(b) What is the stopping distance if the road is covered with ice with $\mu = 0.10?$

(c) Now let’s have the car sliding down an icy hill with an inclination of $\theta = 5.00 \degree$.
# Answers
First, let us draw a FBD diagram:

![](/img/sliding_car_with_kinetic_friction_fbd.PNG)

(a)
$$
\vec{F_{net,x}} = -f_k = 0.6 \cdot m \cdot g = m \cdot a
$$

$$
\Rightarrow 0.6 \cdot g = a = 0.6 \cdot (-9.8) = -5.88 \frac{m}{s^2}
$$

Utilizing the constant acceleration equation from previous chapters:
$$
x - x_0 = \frac{v^2 - {v_0}^2}{2 \cdot a_x}
$$

$$
x - 0 = \frac{0^2 - {10}^2}{2 \cdot (-5.88)} = 8.5\ m
$$

(b)
Substituting the new $\mu$:
$$
a = 0.1 \cdot (-9.8) = -0.98 \frac{m}{s^2}
$$

$$
\Rightarrow x = \frac{-{10}^2}{2 \cdot {-0.98}} = \frac{-100}{-1.96} = 51.02\ m
$$

(c)
![](/img/sliding_car_with_kinetic_friction_fbd_c.PNG)

$$
F_{net,x} = \vec{f_k} + \vec{F_g,x} = m \cdot \vec{a_x}
$$

$$
\Rightarrow 0.1 \cdot \vec{F_N} + m \cdot 9.8 \cdot \sin (5) = m \cdot \vec{a_x} = 0.1 \cdot m \cdot (-9.8) \cdot \cos (5) + m \cdot 9.8 \cdot \sin (5) = m \cdot \vec{a_x}
$$

$$
\Rightarrow  0.1 \cdot \cancel{m} \cdot (-9.8) \cdot \cos (5) + \cancel{m} \cdot 9.8 \cdot \sin (5) = \cancel{m} \cdot \vec{a_x}
$$

$$
\Rightarrow a_x = -0.122 \frac{m}{s^2}
$$

And finding the distance traveled now that we have the acceleration:
$$
x = \frac{-(10)^2}{2 \cdot -0.122} = 409\ m
$$

✔️
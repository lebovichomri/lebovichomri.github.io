---
date: '2026-03-14T17:44:35+02:00'
draft: false
title: 'Fundamentals of Physics - Centripetal Acceleration'
categories: ['Physics']
tags: ['Physics']
math: true
---

# Introduction
In this article I will prove why for a particle in uniform circular motion it's acceleration is equal to $\frac{v2}{r}$.

# Proof

Let's have a look at the following uniform circular motion illustration:

![](/img/centripetal_particle_movement.png)

The particle is located at point $p$, it's centripetal acceleartion is directed towards the center of the circle while it's velocity is tangent to the circle.

$$
\vec{v} = -\vec{v_x} + \vec{v_y} = -v_x \cdot \hat{i} + v_y \cdot \hat{j}
$$

$$
\vec{v} = -(\cos \theta \cdot v) \cdot \hat{i} + (\sin \theta \cdot v) \cdot \hat{j} 
$$

$$
\vec{a} = \frac{d\vec{v}}{dt}
$$

$$
\vec{a} = \frac{d(-\cos \theta \cdot v \cdot \hat{i} )+ d(\sin \theta \cdot v\cdot \hat{j})}{dt}
$$

From looking at the inner right-angled triangle

$$
\sin (90 - \theta) = \frac{y_p}{r} = \cos \theta
$$

$$
\cos (90 - \theta) = \frac{x_p}{r} = \sin \theta
$$

Inserting our new findings into the equations above

$$
\vec{a} = \frac{d(-\frac{y_p \cdot v \cdot \hat{i}}{r}) + d(\frac{x_p \cdot v \cdot \hat{j}}{r})}{dt}
$$

As $v$, $r$, $\hat{i}$ and $\hat{j}$ do not change over time we can extract them outside:

$$
\vec{a} = \frac{v\hat{i}}{r} \cdot d(-y_p) + \frac{v\hat{j}}{r} \cdot d(x_p) \Rightarrow
\vec{a} = \frac{v}{r}(\hat{i} \cdot \frac{d(-y_p)}{dt} + \hat{j} \cdot \frac{d(x_p)}{dt})
$$

Now since $velocity = \frac{\Delta distance}{\Delta time}$ and $velocity$ is constant in uniform circular motion:

$$
\frac{d y_p}{dt} = v_y, \frac{d x_p}{dt} = v_x
$$

Substituting above:

$$
\vec{a} = \frac{v}{r}(\hat{i} \cdot -(v_y) + \hat{j} \cdot v_x)
$$

Additionaly we know that
$$
v_y = v \cdot \sin \theta
$$
and
$$
v_x = v \cdot \cos \theta
$$

We can insert and receive

$$
\vec{a} = \frac{v}{r}(\hat{i} \cdot - (\sin \theta \cdot v) + \hat{j} \cdot (\cos \theta \cdot v)) \Rightarrow \newline
\vec{a} = -\frac{v^2}{r} \cdot \sin \theta \cdot \hat{i} + \frac{v^2}{r} \cdot \cos \theta \cdot \hat{j}
$$

Now we know that

$$
\vec{a} = a_x \hat{i} + a_y {\hat{j}}
$$

Therefore

$$
a_x = -\frac{v^2}{r}\sin \theta 
$$
$$
a_y = \frac{v^2}{r}\cos \theta
$$

$\Rightarrow$

$$
a = \sqrt{a_x^2 + a_y^2} = \sqrt{(-\frac{v^2}{r}\sin \theta)^2 + (\frac{v^2}{r}\cos \theta)^2} = \sqrt{\frac{v^4 \sin^2 \theta}{r^2} + \frac{v^4 \cos ^2 \theta}{r^2}}
$$

$$
\Rightarrow
\sqrt{\frac{v^4}{r^2}(sin^2\theta+\cos^2\theta)} = \sqrt{\frac{v^4}{r^2}} = \frac{\sqrt{v^4}}{\sqrt{r^2}} = \frac{v^2}{r}
$$

![](/img/centripetal_particle_movement_acceleration_vector_included.png)

✔️
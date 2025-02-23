---
title: "MA1521 Calculus for Computing"
date: "2024-11-19"
summary: "Differentiation and integration formulas aren't particularly useful, as more comprehensive lists are provided in the paper."
toc: true
readTime: true
autonumber: false
math: true
tags: ["Cheatsheet"]
showTags: true
---

**Note**: Taken in AY2024/25 Semester 1

## Squeeze Theorem

If $h(x)\leq g(x)\leq f(x)$ when $x$ is near $a$, except possibly at $a$, and $\displaystyle\lim_{x\to a}f(x)=\lim_{x\to a}h(x)=L$, then $\displaystyle\lim_{x\to a}g(x)=L$.

---

## Definite Integral and FTC

$\displaystyle\int_a^bf(x)dx=\lim_{n\to\infty}\left(\sum_{i=1}^n\left(\frac{b-a}{n}\right)f\left(a+k\left(\frac{b-a}{n}\right)\right) \right)=F(b)-F(a)$ given that $F$ is an anti-derivative of $f$. Alternatively, $f(x)=\displaystyle\frac{d}{dx}\int_a^x f(t)dt$.

---

## Tests for Convergence/Divergence

### n-th Term Test

For the series $\sum_{n=1}^\infty a_n$:

- If $\lim_{n \to \infty} a_n \neq 0$, then $\sum_{n=1}^\infty a_n$ diverges.
- If $\lim_{n \to \infty} a_n = 0$, the test is inconclusive.

### Integral Test

For $\sum_{n=1}^\infty a_n$ where $f(n) = a_n \geq 0$:

- If $\int_1^\infty f(x) \, dx$ converges, then $\sum_{n=1}^\infty a_n$ converges.
- If $\int_1^\infty f(x) \, dx$ diverges, then $\sum_{n=1}^\infty a_n$ diverges.

### Comparison Test

For $\sum_{n=1}^\infty a_n$ and $\sum_{n=1}^\infty b_n$ where $0 \leq a_n \leq b_n$:

- If $\sum_{n=1}^\infty b_n$ converges, then $\sum_{n=1}^\infty a_n$ converges.
- If $\sum_{n=1}^\infty a_n$ diverges, then $\sum_{n=1}^\infty b_n$ diverges.

### Useful Series for Comparison:

1. **Geometric Series**: $\sum_{n=1}^\infty ar^{n-1}$ converges if and only if $\vert r\vert < 1$.

2. **p-Series**: $\sum_{n=1}^\infty \frac{1}{n^p}$ converges if and only if $p > 1$.

### Ratio Test

For the series $\sum_{n=1}^\infty \vert a_n\vert$, let $\displaystyle L = \lim_{n \to \infty} \lvert \frac{a_{n+1}}{a_n} \rvert$:

- If $L < 1$, then $\sum_{n=1}^\infty \vert a_n\vert$ converges.
- If $L > 1$, then $\sum_{n=1}^\infty a_n$ diverges.
- If $L = 1$, the test is inconclusive.

### Root Test

For the series $\sum_{n=1}^\infty \vert a_n\vert$, let $L = \lim_{n \to \infty} \sqrt[n]{\vert a_n\vert}$:

- If $L < 1$, then $\sum_{n=1}^\infty \vert a_n\vert$ converges.
- If $L > 1$, then $\sum_{n=1}^\infty a_n$ diverges.
- If $L = 1$, the test is inconclusive.

### Alternating Series Test

For $\sum_{n=1}^\infty (-1)^{n-1} b_n$ where: $b_n \geq 0$, $b_n \geq b_{n+1}$, and $\lim_{n \to \infty} b_n = 0$, then $\sum_{n=1}^\infty (-1)^{n-1} b_n$ converges.

### Power Series

For the power series $\sum_{n=0}^\infty c_n (x - a)^n$:

- The **radius of convergence** $R$ is given by  
  $\displaystyle\lim_{n \to \infty} \left| \frac{c_{n+1}}{c_n} \right| = \frac{1}{R}$.
- The series converges if $\vert x - a\vert < R$ and diverges if $\vert x - a\vert > R$.

### Special Cases for Power Series

For $\sum_{n=0}^\infty c_n (x - a)^{2n}$ or $\sum_{n=0}^\infty c_n (x - a)^{2n+1}$:

- Let $u_n = c_n (x - a)^{2n}$ or $u_n = c_n (x - a)^{2n+1}$.
- Apply the ratio test: $\displaystyle \lvert \frac{u_{n+1}}{u_n} \rvert = \lim_{n \to \infty} \lvert \frac{c_{n+1}}{c_n} \rvert \lvert x - a\rvert^2 = L \lvert x - a\rvert^2$.
- Converges if $L \lvert x - a\rvert^2 < 1 \iff \lvert x - a\rvert < 1/\sqrt{L}$.
- Diverges if $\lvert x - a\rvert > \frac{1}{\sqrt{L}}$. So, $R = 1/\sqrt{L}$.

## Taylor Series

The Taylor series of $f(x)$ at $x = a$ is: $\displaystyle f(x) = \sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!} (x - a)^n$.

### Examples of Taylor Series

1. $\displaystyle\frac{1}{1 - x} = \sum_{n=0}^\infty x^n, \ \lvert x\rvert < 1$
2. $e^x = \sum_{n=0}^\infty \displaystyle\frac{x^n}{n!}$
3. $\sin x = \sum_{n=0}^\infty \displaystyle\frac{(-1)^n x^{2n+1}}{(2n+1)!}$
4. $\cos x = \sum_{n=0}^\infty \displaystyle\frac{(-1)^n x^{2n}}{(2n)!}$
5. $\tan^{-1} x = \sum_{n=0}^\infty \displaystyle\frac{(-1)^n x^{2n+1}}{2n+1}$
6. $\ln(1 - x) = -\sum_{n=0}^\infty \displaystyle\frac{x^{n+1}}{n+1}, \ \lvert x\rvert < 1$

---

## 3D Vector Geometry

- **Distance** from $(x_0,y_0,z_0)$ to a plane $ax+by+cz+d=0$ is $\displaystyle\lvert\frac{ax_0+by_0+cz_0+d}{\sqrt{a^2+b^2+c^2}}\rvert$.
- **Tangent Vector**: $\mathbf{r}'(t)=\langle x'(t),y'(t),z'(t)\rangle$
- **Arc length**: $\displaystyle\int_a^b\sqrt{x'(t)^2+y'(t)^2+z'(t)^2}dt=\int_{x_1}^{x_2}\sqrt{1+f'(x)^2}dx=\int_{y_1}^{y_2}\sqrt{1+f'(y)^2}dy$.

---

## Multivariable Calculus

### Useful Formula

- **Gradient**: $\displaystyle \nabla f=\langle \frac{\partial f}{\partial x},\frac{\partial f}{\partial y}\rangle$ is the steepest ascent and normal to the curve $f(x,y)=C$.
- **Directional Derivative**: $D_{\hat{\mathbf{u}}}=\nabla f\cdot\hat{\mathbf{u}}$ where $\hat{\mathbf{u}}$ is a unit vector.
- **Tangent Plane**: If we have $z=f(x,y)$, then we can use $z=f(a,b)+f_x(a,b)(x-a)+f_y(a,b)(y-b)$. However, if we have $f(x,y,z)=0$, we can use $\nabla f(a,b,c)\cdot \langle x-a,y-b,z-c\rangle=0$.
- **Chain Rule**: If $z=f(x,y),x=x(s,t),y=y(s,t)$, then we have the equation: $\displaystyle\frac{\partial z}{\partial s}=\frac{\partial f}{\partial x}\frac{\partial x}{\partial s}+\frac{\partial f}{\partial y}\frac{\partial y}{\partial s}$, where we can replace $s$ with $t$.
- **Implicit Differentiation**: For $F(x,y,z)=0$, we have $\displaystyle\frac{\partial z}{\partial x}=-\frac{F_x(x,y,z)}{F_z(x,y,z)}$, where we can replace $x$ with $y$.

### Second Derivative Test

Suppose $f_x(a, b) = f_y(a, b) = 0$. Define the discriminant $D$ for the point $(a, b)$ by: $D = D(a, b) = f_{xx}(a, b)f_{yy}(a, b) - [f_{xy}(a, b)]^2.$

1. **If $D > 0$ and $f_{xx}(a, b) > 0$**, then $f$ has a local minimum at $(a, b)$.
2. **If $D > 0$ and $f_{xx}(a, b) < 0$**, then $f$ has a local maximum at $(a, b)$.
3. **If $D < 0$**, then $(a, b)$ is a saddle point of $f$.
4. **If $D = 0$**, then no conclusion can be drawn.

### Double Integrals as Volume

- **Type I Region** ($D = \\{(x, y) : a \leq x \leq b, \, g_1(x) \leq y \leq g_2(x)\\}$): $\displaystyle\iint_D f(x, y) \, dA = \int_a^b \int_{g_1(x)}^{g_2(x)} f(x, y) \, dy \, dx$.
- **Type II Region** ($D = \\{(x, y) : c \leq y \leq d, \, h_1(y) \leq y \leq h_2(y)\\}$): $\displaystyle\iint_D f(x, y) \, dA = \int_c^d \int_{h_1(y)}^{h_2(y)} f(x, y) \, dx \, dy$.
- **Polar Region** ($R = \\{(r, \theta) : 0 \leq a \leq r \leq b, \, \alpha \leq \theta \leq \beta\\}$
  ): $\displaystyle\iint_R f(x, y) \, dA = \int_\alpha^\beta \int_a^b f(r \cos \theta, r \sin \theta) \, r \, dr \, d\theta.$
- **Application on Surface Area**: $\displaystyle \iint_D dS = \iint_D \sqrt{f_x^2 + f_y^2 + 1} \, dA$.

---

## First Order ODE

- A **separable differential equation** has the form: $\displaystyle\frac{dy}{dx} = f(x)g(y)$. The solution can be obtained by integrating: $\displaystyle\int \frac{1}{g(y)} \, dy = \int f(x) \, dx + C$.
- For a **homogeneous differential equation** of the form: $\displaystyle y' = g\left(\frac{y}{x}\right),$  
  use the substitution $y = vx$. This leads to: $\displaystyle \int \frac{dv}{g(v) - v} = \int \frac{dx}{x} + C.$
- A **linear differential equation** has the form $\displaystyle \frac{dy}{dx} + P(x)y = Q(x)$:

  1. The integrating factor is:  
     $I(x) = e^{\int P(x) \, dx}.$

  2. The equation becomes:  
     $(I(x)y)' = I(x)Q(x).$

  3. The solution is:  
     $y = I(x)^{-1} \left[\int I(x) \cdot Q(x) \, dx + C\right].$

- A **Bernoulli equation** is of the form: $y' + p(x)y = q(x)y^n$. Using the substitution $u = y^{1-n},$ the equation transforms into: $u' + (1-n)p(x)u = (1-n)q(x)$.

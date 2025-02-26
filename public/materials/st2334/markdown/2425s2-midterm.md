class: middle

# ST2334 Midterm Cheat Sheet

## Chapter 1

- **Independent Events**: $P(A \cap B) = P(A) \times P(B)$.
- **Mutually Exclusive Events**: $A\cap B=\emptyset$. The definition also implies $P(A\cap B)=0$ but not vice versa.
- **Complement Probabilities**: $\boxed{P(A \cap B) + P(A \cap B^\prime)=P(A)}$
- **Absorption Law**: $\boxed{A\cup (A\cap B)=A\cap (A\cup B)=A}$.

---

class: middle

## Chapter 2

- **Variance**: $V(X)=E((X-\mu_X)^2=\boxed{E(X^2)-(E(X))^2}$.
- **PMF**: $f(x)=P(X=x)$ for discrete $X$.
- **PDF**: $\int_a^b f(x)dx=P(a\leq X \leq b)$ for continuous $X$.
- **Non-Existence of $E(X)$**: Consider $f(x)=\frac{1}{2x^2}$ for $\lvert x\rvert \geq 1$ and $0$ elsewhere.

$$E(X)=\int_{-\infty}^1x\cdot\frac{1}{2x^2}dx+\int_1^{\infty}x\cdot\frac{1}{2x^2}dx=-\infty+\infty$$

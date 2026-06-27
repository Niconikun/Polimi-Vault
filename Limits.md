---
title: Limits
tags:
  - calculus
  - analysis
  - mathematics
  - foundations
---

# Limits

## Formal Definition

A **limit** is a fundamental concept in calculus and analysis that describes the value that a function or sequence approaches as the input or index approaches some value. Formally, the limit of a function $f(x)$ as $x$ approaches $a$ is $L$, denoted $\lim_{x \to a} f(x) = L$, if for every $\epsilon > 0$, there exists a $\delta > 0$ such that:

$$
|x - a| < \delta \implies |f(x) - L| < \epsilon
$$

Limits are the rigorous foundation underlying [[Differential Equations|derivatives]], [[Fundamental Theorem of Calculus|integrals]], and continuity, making them essential to all of calculus and analysis.

## Historical Development

### Key Milestones
- **1600s:** Isaac Newton and Gottfried Leibniz develop calculus using informal notion of limits
- **1750s:** Jean le Rond d'Alembert attempts rigorous formulation ("limit" terminology introduced)
- **1821:** Augustin-Louis Cauchy develops rigorous $\epsilon$-$\delta$ definition
- **1872:** Karl Weierstrass formalizes analysis with precise limit theory
- **1872+:** Rigorous foundations enable complex analysis, functional analysis, topology

### Foundational Contributors
1. **Augustin-Louis Cauchy (1789–1857):** Rigorous formulation and $\epsilon$-$\delta$ definition
2. **Karl Weierstrass (1815–1897):** Formalized analysis; independent definition of limit
3. **Georg Cantor (1845–1918):** Developed set theory enabling abstract limits
4. **David Hilbert (1862–1943):** Extended limits to infinite-dimensional spaces

## Mathematical Formulation

### Limit of a Function at a Point

**Definition ($\epsilon$-$\delta$):**

$$
\lim_{x \to a} f(x) = L \iff \forall \epsilon > 0, \exists \delta > 0: |x - a| < \delta \Rightarrow |f(x) - L| < \epsilon
$$

**Intuitive Meaning:** Values of $f(x)$ get arbitrarily close to $L$ as $x$ gets arbitrarily close to $a$.

### Limit of a Sequence

For sequence $\{a_n\}_{n=1}^\infty$:

$$
\lim_{n \to \infty} a_n = L \iff \forall \epsilon > 0, \exists N \in \mathbb{N}: n > N \Rightarrow |a_n - L| < \epsilon
$$

### One-Sided Limits

**Right Limit (Limit from above):**
$$
\lim_{x \to a^+} f(x) = L \iff \forall \epsilon > 0, \exists \delta > 0: 0 < x - a < \delta \Rightarrow |f(x) - L| < \epsilon
$$

**Left Limit (Limit from below):**
$$
\lim_{x \to a^-} f(x) = L \iff \forall \epsilon > 0, \exists \delta > 0: 0 < a - x < \delta \Rightarrow |f(x) - L| < \epsilon
$$

Two-sided limit exists if and only if both one-sided limits exist and are equal.

### Special Cases

1. **Limit at Infinity:**
   $$
   \lim_{x \to \infty} f(x) = L \iff \forall \epsilon > 0, \exists M > 0: x > M \Rightarrow |f(x) - L| < \epsilon
   $$

2. **Infinite Limits:**
   $$
   \lim_{x \to a} f(x) = \infty \iff \forall M > 0, \exists \delta > 0: 0 < |x - a| < \delta \Rightarrow f(x) > M
   $$

3. **Limit of Constant Function:**
   $$
   \lim_{x \to a} c = c
   $$

## Fundamental Principles

### Properties of Limits (Limit Laws)

If $\lim_{x \to a} f(x) = L$ and $\lim_{x \to a} g(x) = M$, then:

**Sum Rule:**
$$
\lim_{x \to a} [f(x) + g(x)] = L + M
$$

**Product Rule:**
$$
\lim_{x \to a} [f(x) \cdot g(x)] = L \cdot M
$$

**Quotient Rule** (if $M \neq 0$):
$$
\lim_{x \to a} \frac{f(x)}{g(x)} = \frac{L}{M}
$$

**Power Rule:**
$$
\lim_{x \to a} [f(x)]^n = L^n
$$

**Scalar Multiple:**
$$
\lim_{x \to a} [c \cdot f(x)] = c \cdot L
$$

### Squeeze Theorem (Sandwich Theorem)

If $f(x) \leq g(x) \leq h(x)$ near $a$ and:
$$
\lim_{x \to a} f(x) = \lim_{x \to a} h(x) = L
$$

Then:
$$
\lim_{x \to a} g(x) = L
$$

**Application:** $\lim_{x \to 0} x \sin(1/x) = 0$ (using $|x \sin(1/x)| \leq |x|$)

## Theoretical Framework

### Continuity

Function $f$ is continuous at point $a$ if:
$$
\lim_{x \to a} f(x) = f(a)
$$

All three conditions must hold:
1. $\lim_{x \to a} f(x)$ exists
2. $f(a)$ is defined
3. The limit equals the function value

### Convergence of Sequences

**Convergent Sequence:** $\lim_{n \to \infty} a_n = L$ (often written $a_n \to L$)

**Divergent Sequence:** Limit does not exist (either infinite or oscillates)

**Bounded Sequence:** Remains within some interval; necessary but not sufficient for convergence

### Types of Convergence

1. **Pointwise Convergence:** Sequence of functions $f_n(x) \to f(x)$ for each $x$

2. **Uniform Convergence:** Sequence of functions converges uniformly if:
   $$
   \lim_{n \to \infty} \sup_x |f_n(x) - f(x)| = 0
   $$
   (stronger than pointwise; preserves continuity)

## Computational Methods

### Finding Limits Analytically

1. **Direct Substitution:** Evaluate $f(a)$ if continuous at $a$

2. **Factoring:** Remove common factors causing $0/0$ indeterminacy

3. **Rationalization:** Multiply by conjugate to resolve $0/0$ or $\infty - \infty$

4. **L'Hôpital's Rule:** For indeterminate forms:
   $$
   \lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{x \to a} \frac{f'(x)}{g'(x)}
   $$
   (if right-hand limit exists; valid when $0/0$ or $\infty/\infty$)

5. **Taylor Series:** Expand near point of interest:
   $$
   f(x) = f(a) + f'(a)(x-a) + \frac{f''(a)}{2}(x-a)^2 + \ldots
   $$

### Common Indeterminate Forms

1. $\frac{0}{0}$: Direct factoring or L'Hôpital's rule
2. $\frac{\infty}{\infty}$: L'Hôpital's rule or divide by highest power
3. $0 \cdot \infty$: Rewrite as $\frac{0}{1/\infty}$ or $\frac{\infty}{1/0}$
4. $\infty - \infty$: Find common denominator or rationalize
5. $0^0, 1^\infty, \infty^0$: Use logarithms

## Relationship to Other Concepts

1. **Connection to [[Derivative]]:**
   - Definition: $f'(a) = \lim_{h \to 0} \frac{f(a+h) - f(a)}{h}$
   - Limits are prerequisite concept

2. **Connection to [[Fundamental Theorem of Calculus]]:**
   - Integrals defined as limit of Riemann sums
   - Derivative-integral relationship via limits

3. **Connection to [[Taylor Series Expansion]]:**
   - Taylor series represents function as limit of polynomial approximations
   - Error term goes to zero in limit

4. **Connection to [[Convergence]]:**
   - Limits formalize notion of convergence
   - Essential for analysis, [[Numerical Analysis]], approximation theory

## Classification and Variants

### By Domain Type

1. **Real Functions:** $f: \mathbb{R} \to \mathbb{R}$
2. **Complex Functions:** $f: \mathbb{C} \to \mathbb{C}$
3. **Multivariable Functions:** $f: \mathbb{R}^n \to \mathbb{R}^m$
4. **Functional Limits:** Limits in infinite-dimensional spaces (functional analysis)

### By Behavior

1. **Finite Limits:** Limit is finite real number
2. **Infinite Limits:** Function grows unbounded
3. **Oscillating Limits:** No limit exists (oscillation)
4. **Removable Discontinuity:** Limit exists but $f(a)$ undefined or different

## Important Limits

### Standard Limits

$$
\lim_{x \to 0} \frac{\sin x}{x} = 1
$$

$$
\lim_{x \to \infty} \left(1 + \frac{1}{x}\right)^x = e
$$

$$
\lim_{n \to \infty} \left(1 + \frac{1}{n}\right)^n = e
$$

$$
\lim_{x \to 0} \frac{e^x - 1}{x} = 1
$$

$$
\lim_{x \to \infty} \frac{e^x}{x^n} = \infty \text{ for any } n
$$

### Asymptotics (Limit Behavior)

Big-O notation: $f(x) = O(g(x))$ means $|f(x)| \leq C|g(x)|$ for large $x$.

Little-o notation: $f(x) = o(g(x))$ means $\lim_{x \to \infty} \frac{f(x)}{g(x)} = 0$.

## Applications

### Calculus and Analysis

- **Continuity:** Functions must satisfy limit conditions
- **Differentiability:** Derivatives defined as limits
- **Integrability:** Integrals defined as limits of Riemann sums
- **[[Asymptotic Analysis]]:** Behavior of functions for large arguments

### Numerical Methods

- **Convergence Analysis:** [[Euler Method|Numerical methods]] converge as step size $h \to 0$
- **Error Bounds:** Truncation and round-off errors approach zero with refinement
- **Approximation Theory:** Polynomial approximations improve in limit

### Engineering and Physics

- **Steady-State Response:** System behavior as $t \to \infty$
- **Perturbation Analysis:** Expansion parameters approach zero
- **Signal Processing:** [[Signal Processing|Nyquist]] and [[Shannon Theorem|Shannon]] limits

## See Also

- [[Continuity]]
- [[Derivative]]
- [[Fundamental Theorem of Calculus]]
- [[Taylor Series Expansion]]
- [[Convergence]]
- [[Asymptotic Analysis]]
- [[Differential Equations]]
- [[Numerical Analysis]]
- [[L'Hôpital's Rule]]

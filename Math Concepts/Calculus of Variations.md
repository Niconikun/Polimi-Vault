## Formal Definition

**Calculus of Variations** is a branch of mathematical analysis that deals with optimizing functionals—mappings from a space of functions to real numbers—rather than functions of finite-dimensional variables. It provides methods to find functions that extremize (minimize, maximize, or make stationary) quantities expressed as integrals, leading to Euler-Lagrange differential equations as necessary conditions for extrema. This field forms the mathematical foundation for variational principles in physics and engineering, including mechanics, optics, and optimal control.

## Historical Development

### Foundational Problems
- **1696:** Johann Bernoulli's **brachistochrone problem** (curve of fastest descent)
- **1697:** Solutions by Newton, Leibniz, L'Hôpital, and the Bernoulli brothers
- **1744:** Leonhard Euler's general method using finite differences
- **1755:** Joseph-Louis Lagrange's analytical formulation using variations
- **19th century:** Further development by Legendre, Jacobi, Weierstrass, and Hilbert
- **20th century:** Extension to infinite dimensions, optimal control, and modern applications

## Mathematical Framework

### Basic Problem Formulation

The fundamental problem in calculus of variations is to find a function $y(x)$ that extremizes a functional of the form:

$$
J[y] = \int_{a}^{b} F(x, y(x), y'(x)) \, dx
$$

subject to boundary conditions:
$$
y(a) = y_a, \quad y(b) = y_b
$$

where:
- $F: \mathbb{R}^3 \to \mathbb{R}$ is a given function (the Lagrangian density)
- $y \in C^1([a,b])$ or in an appropriate function space
- $y' = dy/dx$

### First Variation and Euler-Lagrange Equation

The necessary condition for $J[y]$ to have an extremum is that its **first variation** vanishes:

$$
\delta J[y; \eta] = 0 \quad \text{for all admissible variations } \eta
$$

This leads to the **Euler-Lagrange equation**:

$$
\frac{\partial F}{\partial y} - \frac{d}{dx} \left( \frac{\partial F}{\partial y'} \right) = 0
$$

with boundary conditions $y(a) = y_a$, $y(b) = y_b$.

### Derivation via Variations

Consider a perturbed function $y_\epsilon(x) = y(x) + \epsilon \eta(x)$, where $\eta(a) = \eta(b) = 0$. Then:

$$
\delta J = \left. \frac{d}{d\epsilon} J[y_\epsilon] \right|_{\epsilon=0} = \int_a^b \left( \frac{\partial F}{\partial y} \eta + \frac{\partial F}{\partial y'} \eta' \right) dx
$$

Integration by parts of the second term yields:

$$
\delta J = \int_a^b \left[ \frac{\partial F}{\partial y} - \frac{d}{dx} \left( \frac{\partial F}{\partial y'} \right) \right] \eta \, dx + \left. \frac{\partial F}{\partial y'} \eta \right|_a^b
$$

The boundary term vanishes due to $\eta(a) = \eta(b) = 0$, and since $\eta$ is arbitrary, the [[Fundamental Lemma of Calculus of Variations]] gives the Euler-Lagrange equation.

## Generalized Formulations

### Multiple Dependent Variables

For $n$ unknown functions $y_1(x), \ldots, y_n(x)$:

$$
J[\mathbf{y}] = \int_a^b F(x, y_1, \ldots, y_n, y_1', \ldots, y_n') dx
$$

We obtain a system of $n$ [[Euler-Lagrange Equations]]:

$$
\frac{\partial F}{\partial y_i} - \frac{d}{dx} \left( \frac{\partial F}{\partial y_i'} \right) = 0, \quad i = 1, \ldots, n
$$

### Higher-Order Derivatives

For functionals involving derivatives up to order $n$:

$$
J[y] = \int_a^b F(x, y, y', y'', \ldots, y^{(n)}) dx
$$

The Euler-Lagrange equation generalizes to:

$$
\sum_{k=0}^n (-1)^k \frac{d^k}{dx^k} \left( \frac{\partial F}{\partial y^{(k)}} \right) = 0
$$

where $y^{(0)} = y$, $y^{(1)} = y'$, etc.

### Multiple Independent Variables

For functions of several variables, e.g., $u(x,y)$:

$$
J[u] = \iint_\Omega F(x, y, u, u_x, u_y) dx\,dy
$$

The Euler-Lagrange equation becomes a partial differential equation:

$$
\frac{\partial F}{\partial u} - \frac{\partial}{\partial x} \left( \frac{\partial F}{\partial u_x} \right) - \frac{\partial}{\partial y} \left( \frac{\partial F}{\partial u_y} \right) = 0
$$

For $n$ independent variables $x_1, \ldots, x_n$:

$$
\frac{\partial F}{\partial u} - \sum_{i=1}^n \frac{\partial}{\partial x_i} \left( \frac{\partial F}{\partial u_{x_i}} \right) = 0
$$

## Special Cases and Techniques

### Beltrami Identity (First Integral)

When $F$ does not depend explicitly on $x$, i.e., $F = F(y, y')$, then:

$$
\frac{d}{dx} \left( F - y' \frac{\partial F}{\partial y'} \right) = 0
$$

which implies:

$$
F - y' \frac{\partial F}{\partial y'} = \text{constant}
$$

This provides a first integral that often simplifies solution.

### [[Natural Boundary Conditions]]

When endpoint values are not prescribed, the **[[Natural Boundary Conditions]]** arise:

$$
\left. \frac{\partial F}{\partial y'} \right|_{x=a} = 0 \quad \text{and/or} \quad \left. \frac{\partial F}{\partial y'} \right|_{x=b} = 0
$$

### Transversality Conditions

For problems with variable endpoints or free boundary conditions, more general conditions apply, relating the Lagrangian to the geometry of the endpoint constraints.

### Isoperimetric Problems

Constrained problems of the form:

$$
\begin{aligned}
&\text{Minimize } J[y] = \int_a^b F(x, y, y') dx \\
&\text{subject to } K[y] = \int_a^b G(x, y, y') dx = C
\end{aligned}
$$

Solved using Lagrange multipliers: extremize $J + \lambda K$.

## Existence and Regularity Theory

### Direct Method

Developed by Hilbert and Lebesgue, the direct method establishes existence of minimizers by:
1. Taking a minimizing sequence
2. Proving compactness in an appropriate topology
3. Showing lower semicontinuity of the functional

### Tonelli's Theorem

Under conditions of **coercivity** and **lower semicontinuity**, existence of a minimizer is guaranteed.

### Regularity

Minimizers often have higher regularity than initially assumed:
- For convex Lagrangians, minimizers are typically $C^1$ or smoother
- Elliptic regularity theory applies to [[Euler-Lagrange Equations]]

## Applications in Mechanics and Physics

### Lagrangian Mechanics

The [[Action]] integral $S = \int L(q, \dot{q}, t) dt$ leads via Euler-Lagrange to Lagrange's equations:

$$
\frac{d}{dt} \left( \frac{\partial L}{\partial \dot{q}_i} \right) - \frac{\partial L}{\partial q_i} = 0
$$

### [[Continuum Mechanics]]

Field theories use Lagrangian densities $\mathcal{L}(\phi, \partial_\mu \phi)$:

$$
S = \int \mathcal{L}(\phi, \partial_\mu \phi) d^4x
$$

[[Euler-Lagrange Equations]] yield field equations, e.g., Maxwell's equations from electromagnetic Lagrangian.

### Geometric Optics

Fermat's principle (least time) leads to the eikonal equation governing light rays.

### Elasticity

The [[Principle of Minimum Potential Energy]] leads to [[Equilibrium Equations]] via Euler-Lagrange.

## Modern Developments and Extensions

### Optimal [[Control Theory]]

The calculus of variations extends to control problems via Pontryagin's maximum principle:

Minimize $J = \int_0^T L(x, u, t) dt$ subject to $\dot{x} = f(x, u, t)$.

### Shape Optimization

Optimizing domain shapes for desired properties leads to shape derivatives and sensitivity analysis.

### Numerical Methods

1. **Ritz method:** Approximate solution by finite linear combination of basis functions
2. **[[Finite Element Method]]:** Discretization of weak form derived from [[Variational Principle]]
3. **Direct methods:** Discretize then optimize (e.g., using nonlinear programming)

### Stochastic Calculus of Variations

Extensions to functionals of stochastic processes (Malliavin calculus).

## Key Theorems and Results

### [[Noether's Theorem]]

For every continuous symmetry of the Lagrangian, there exists a conserved quantity. If $F$ is invariant under $x \to x + \epsilon \xi$, $y \to y + \epsilon \eta$, then:

$$
\frac{d}{dx} \left( F\xi + (\eta - y'\xi)\frac{\partial F}{\partial y'} \right) = 0
$$

### Legendre Condition (Second Variation)

For a minimizer, the **Legendre condition** must hold:

$$
\frac{\partial^2 F}{\partial y'^2} \geq 0 \quad \text{(necessary condition for minimum)}
$$

### Jacobi Condition

Absence of conjugate points along the extremal is necessary for a weak minimum.

### Weierstrass Excess Function

For strong minima, the Weierstrass excess function must be nonnegative.

## Computational Approaches

### [[Finite Element Method]]

The weak form of [[Euler-Lagrange Equations]]:

$$
\int_\Omega \left( \frac{\partial F}{\partial u} v + \frac{\partial F}{\partial \nabla u} \cdot \nabla v \right) d\Omega = 0 \quad \forall v \in V_0
$$

is discretized as $\mathbf{Ku} = \mathbf{F}$.

### Direct Numerical Methods

1. **Shooting methods:** Solve boundary value problem via [[initial value problems]]
2. **Galerkin methods:** Project onto finite-dimensional subspaces
3. **Collocation methods:** Enforce equation at discrete points

## Relationship to Other Fields

### Differential Geometry

Variational problems on manifolds lead to geodesic equations and minimal surfaces.

### Partial Differential Equations

Many PDEs arise as [[Euler-Lagrange Equations]] of energy functionals.

### Functional Analysis

The calculus of variations operates in infinite-dimensional function spaces, requiring concepts from functional analysis.

### Convex Analysis

For convex functionals, minimization problems are well-posed and have unique solutions.

## Limitations and Challenges

### Non-Convex Problems

Non-convex functionals may have multiple local minima, and global minimization is challenging.

### Lack of Regularity

Minimizers may develop singularities (e.g., cracks in fracture mechanics).

### Computational Complexity

High-dimensional problems (e.g., in quantum field theory) are computationally intensive.

### Constraints Handling

Inequality constraints and non-holonomic constraints require specialized techniques.

## See Also

- [[Euler-Lagrange Equations]]
- [[Variational Principle]]
- [[Principle of Minimum Potential Energy]]
- [[Lagrangian Mechanics]]
- [[Finite Element Method]]
- [[Optimal Control Theory]]
- [[Partial Differential Equations (PDEs)]]
- [[Functional Analysis]]
- [[Noether's Theorem]]
- [[Direct Methods in Calculus of Variations]]
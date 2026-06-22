## Formal Definition

The **Euler-Lagrange Equations** are a system of second-order [[Ordinary Differential Equations (ODEs)]] that provide the necessary condition for a [[Functional]] to be stationary (i.e., to have an extremum) in the [[Calculus of Variations]]. They serve as the fundamental mathematical tool for deriving the governing equations of motion or equilibrium from variational principles, forming the bridge between energy-based formulations and differential equations in mechanics, physics, and engineering.

## Mathematical Formulation

### General Form for Single Dependent Variable

For a functional of the form:

$$
J[y] = \int_{a}^{b} F(x, y(x), y'(x)) \, dx
$$

where:
- $F$ is a given function (the Lagrangian density) that is continuously differentiable with respect to all its arguments
- $y(x)$ is the unknown function to be determined
- $y'(x) = \frac{dy}{dx}$
- Boundary conditions: $y(a) = y_a$, $y(b) = y_b$

The necessary condition for $J[y]$ to have an extremum (minimum, maximum, or saddle point) is that $y(x)$ satisfies the **Euler-Lagrange equation**:

$$
\frac{\partial F}{\partial y} - \frac{d}{dx} \left( \frac{\partial F}{\partial y'} \right) = 0
$$

### Derivation via [[Calculus of Variations]]

Consider a small perturbation $\eta(x)$ about the extremal function $y(x)$, with $\eta(a) = \eta(b) = 0$:
$$
y_\epsilon(x) = y(x) + \epsilon \eta(x)
$$

The first variation of the functional is:
$$
\delta J = \left. \frac{d}{d\epsilon} J[y_\epsilon] \right|_{\epsilon=0} = \int_a^b \left( \frac{\partial F}{\partial y} \eta + \frac{\partial F}{\partial y'} \eta' \right) dx
$$

Integrating the second term by parts:
$$
\int_a^b \frac{\partial F}{\partial y'} \eta' dx = \left. \frac{\partial F}{\partial y'} \eta \right|_a^b - \int_a^b \frac{d}{dx} \left( \frac{\partial F}{\partial y'} \right) \eta dx
$$

Using the boundary conditions $\eta(a) = \eta(b) = 0$, we obtain:
$$
\delta J = \int_a^b \left[ \frac{\partial F}{\partial y} - \frac{d}{dx} \left( \frac{\partial F}{\partial y'} \right) \right] \eta dx = 0
$$

Since $\eta(x)$ is arbitrary, the [[Fundamental Lemma of Calculus of Variations]] gives the Euler-Lagrange equation.

## Extended Forms

### Multiple Dependent Variables

For a functional depending on $n$ functions $y_1(x), \ldots, y_n(x)$:

$$
J[\mathbf{y}] = \int_a^b F(x, y_1, \ldots, y_n, y_1', \ldots, y_n') dx
$$

We obtain a system of $n$ Euler-Lagrange equations:

$$
\frac{\partial F}{\partial y_i} - \frac{d}{dx} \left( \frac{\partial F}{\partial y_i'} \right) = 0, \quad i = 1, \ldots, n
$$

### Higher-Order Derivatives

For functionals involving higher derivatives, e.g.:

$$
J[y] = \int_a^b F(x, y, y', y'', \ldots, y^{(n)}) dx
$$

The Euler-Lagrange equation generalizes to:

$$
\frac{\partial F}{\partial y} - \frac{d}{dx} \left( \frac{\partial F}{\partial y'} \right) + \frac{d^2}{dx^2} \left( \frac{\partial F}{\partial y''} \right) - \cdots + (-1)^n \frac{d^n}{dx^n} \left( \frac{\partial F}{\partial y^{(n)}} \right) = 0
$$

### Multiple Independent Variables

For functionals of functions of several variables, e.g., $u(x,y)$:

$$
J[u] = \iint_\Omega F(x, y, u, u_x, u_y) dx dy
$$

The Euler-Lagrange equation becomes a partial differential equation:

$$
\frac{\partial F}{\partial u} - \frac{\partial}{\partial x} \left( \frac{\partial F}{\partial u_x} \right) - \frac{\partial}{\partial y} \left( \frac{\partial F}{\partial u_y} \right) = 0
$$

## Special Cases and Simplifications

### Beltrami Identity (First Integral)

When $F$ does not depend explicitly on $x$, i.e., $F = F(y, y')$, then:

$$
\frac{d}{dx} \left( F - y' \frac{\partial F}{\partial y'} \right) = 0
$$

which implies:

$$
F - y' \frac{\partial F}{\partial y'} = \text{constant}
$$

This provides a first integral that often simplifies the solution.

### [[Natural Boundary Conditions]]

When boundary values are not prescribed, the [[Natural Boundary Conditions]] arise:

$$
\left. \frac{\partial F}{\partial y'} \right|_{x=a} = 0 \quad \text{and/or} \quad \left. \frac{\partial F}{\partial y'} \right|_{x=b} = 0
$$

These are also called **transversality conditions**.

## Applications in Mechanics

### Lagrangian Mechanics

In classical mechanics, the [[Action]] $S$ is defined as:

$$
S = \int_{t_1}^{t_2} L(q, \dot{q}, t) dt
$$

where $L = T - V$ is the Lagrangian (kinetic minus potential energy), and $q_i$ are [[Generalized Coordinates]]. The Euler-Lagrange equations yield **Lagrange's equations**:

$$
\frac{d}{dt} \left( \frac{\partial L}{\partial \dot{q}_i} \right) - \frac{\partial L}{\partial q_i} = 0, \quad i = 1, \ldots, n
$$

### [[Continuum Mechanics]]

For continuous systems, the Lagrangian density $\mathcal{L}$ depends on field variables and their derivatives:

$$
S = \int_{t_1}^{t_2} \int_\Omega \mathcal{L}(\phi, \partial_\mu \phi, x^\mu) d^3x dt
$$

The Euler-Lagrange equations give the field equations:

$$
\frac{\partial \mathcal{L}}{\partial \phi} - \partial_\mu \left( \frac{\partial \mathcal{L}}{\partial (\partial_\mu \phi)} \right) = 0
$$

### Examples from [[Solid Mechanics]]

**Bernoulli-Euler beam:**
For beam bending with Lagrangian density $\mathcal{L} = \frac{1}{2}EI(w'')^2 - qw$:
$$
\frac{d^2}{dx^2} \left( EI \frac{d^2 w}{dx^2} \right) = q
$$

**Stretched string:**
For small vibrations with $\mathcal{L} = \frac{1}{2}\rho u_t^2 - \frac{1}{2}T u_x^2$:
$$
\rho u_{tt} - T u_{xx} = 0
$$

**Linear elasticity:**
From the Lagrangian density $\mathcal{L} = \frac{1}{2}\rho \dot{u}_i \dot{u}_i - \frac{1}{2}C_{ijkl} \varepsilon_{ij} \varepsilon_{kl}$:
$$
\rho \ddot{u}_i - \frac{\partial}{\partial x_j} \left( C_{ijkl} \frac{\partial u_k}{\partial x_l} \right) = 0
$$

## Relationship to Other Principles

### [[Principle of Least Action]]

The Euler-Lagrange equations are the differential expression of the **principle of stationary action** (or [[Hamilton's Principle]]), which states that the actual path of a system is such that the [[Action]] integral is stationary.

### [[Principle of Virtual Work]]

For static problems, the Euler-Lagrange equations reduce to the [[Equilibrium Equations]] derived from the [[Principle of Virtual Work]].

### [[Principle of Minimum Potential Energy]]

In elastostatics, the Euler-Lagrange equations obtained from minimizing the total potential energy yield the [[Equilibrium Equations]] and [[Natural Boundary Conditions]].

## Mathematical Properties

### Existence and Uniqueness

The existence of solutions to the Euler-Lagrange equations is not guaranteed in general and depends on:
- Convexity of $F$ with respect to $y'$ (Tonelli conditions)
- Growth conditions (coercivity)
- Regularity of boundary data

Uniqueness typically requires strict convexity of $F$.

### Regularity

Solutions of the Euler-Lagrange equations generally inherit the smoothness of the Lagrangian $F$. For $F \in C^k$, solutions are typically $C^{k+1}$.

### [[Noether's Theorem]]

If the functional $J$ is invariant under a continuous family of transformations, then there exists a corresponding conserved quantity (first integral). For example, if $F$ is independent of $x$, then $F - y' \frac{\partial F}{\partial y'}$ is constant.

## Numerical Implications

### [[Finite Element Method]]

The weak form of the Euler-Lagrange equations provides the basis for finite element discretization. For a functional $J[u]$, the condition $\delta J = 0$ leads to:

$$
\int_\Omega \left( \frac{\partial F}{\partial u} v + \frac{\partial F}{\partial \nabla u} \cdot \nabla v \right) d\Omega = 0 \quad \forall v \in V_0
$$

which is discretized as $\mathbf{Ku} = \mathbf{F}$.

### Direct Methods in [[Calculus of Variations]]

Numerical methods for solving variational problems directly, such as the Ritz method, approximate the solution as:

$$
y_n(x) = \sum_{i=1}^n c_i \phi_i(x)
$$

and determine coefficients $c_i$ by solving $\frac{\partial J[y_n]}{\partial c_i} = 0$.

## Limitations and Extensions

### Non-differentiable Functions

The classical Euler-Lagrange equations require $F$ to be differentiable. For non-smooth problems (e.g., involving constraints or non-differentiable functions), generalizations include:
- Subdifferential calculus for convex functions
- Lagrange multipliers for constraints
- Nonsmooth analysis

### Constraints

For problems with constraints, the method of Lagrange multipliers extends the Euler-Lagrange equations. For isoperimetric constraints $\int_a^b G(x,y,y')dx = C$, we solve:

$$
\frac{\partial}{\partial y} (F + \lambda G) - \frac{d}{dx} \left( \frac{\partial}{\partial y'} (F + \lambda G) \right) = 0
$$

### Infinite-Dimensional Spaces

For problems in infinite-dimensional function spaces, the Euler-Lagrange equations generalize to Gateaux or Fréchet derivative conditions:

$$
DJ[y] = 0
$$

where $DJ$ is the functional derivative.

## Historical Context

### Development Timeline

- **1696:** Johann Bernoulli poses the brachistochrone problem
- **1744:** Leonhard Euler publishes first general treatment
- **1755:** Joseph-Louis Lagrange develops the [[Calculus of Variations]] formalism
- **1834-35:** William Rowan Hamilton formulates [[Hamilton's Principle]]
- **20th century:** Extension to infinite dimensions, optimal control, and field theories

### Key Contributors

1. **Johann Bernoulli (1667-1748):** Brachistochrone problem
2. **Leonhard Euler (1707-1783):** First general equations
3. **Joseph-Louis Lagrange (1736-1813):** Systematic formulation
4. **Carl Gustav Jacobi (1804-1851):** Second variation and conjugate points
5. **David Hilbert (1862-1943):** Direct method in [[Calculus of Variations]]

## See Also

- [[Calculus of Variations]]
- [[Lagrangian Mechanics]]
- [[Hamilton's Principle]]
- [[Variational Principle]]
- [[Weak Form (Variational Form)]]
- [[Finite Element Method]]
- [[Noether's Theorem]]
- [[Principle of Minimum Potential Energy]]
- [[Partial Differential Equations]]
- [[Optimal Control Theory]]
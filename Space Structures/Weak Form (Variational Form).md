## Formal Definition

The **Weak Form**, also known as the **Variational Form**, is an integral reformulation of a [[Boundary Value Problems]] (BVP) obtained by multiplying the governing differential equation by a **test function**, integrating over the domain, and applying integration by parts to reduce the order of derivatives. This formulation relaxes the continuity requirements on the solution, transforming the problem from seeking a function that satisfies the differential equation pointwise ([[Strong Form (Pointwise Form)]]) to seeking a function that satisfies an integral identity for a class of test functions.

## Mathematical Formulation

### [[Strong Form (Pointwise Form)]] to Weak Form Transformation

Given a boundary value problem in **[[Strong Form (Pointwise Form)]]**:

$$
\begin{aligned}
\mathcal{L}u &= f \quad \text{in } \Omega \\
\mathcal{B}u &= g \quad \text{on } \Gamma = \partial\Omega
\end{aligned}
$$

where:
- \( \mathcal{L} \) is a linear differential operator of order \( 2m \)
- \( \mathcal{B} \) represents boundary operators
- \( \Omega \) is the problem domain
- \( \Gamma \) is the boundary

The **weak form** is obtained through the following procedure:

#### Step 1: Weighted Residual Statement
Multiply the differential equation by a test function \( v \) and integrate over \( \Omega \):

$$
\int_\Omega v (\mathcal{L}u - f) \, d\Omega = 0
$$

#### Step 2: Integration by Parts
Apply integration by parts (Green's theorem, divergence theorem) to transfer derivatives from \( u \) to \( v \):

$$
\int_\Omega v \mathcal{L}u \, d\Omega = \text{boundary terms} + \int_\Omega a(u, v) \, d\Omega
$$

where \( a(\cdot, \cdot) \) is a bilinear form containing derivatives of lower order.

#### Step 3: Incorporation of Boundary Conditions
- **Essential (Dirichlet) boundary conditions:** Incorporated by restricting the solution and test function spaces
- **Natural (Neumann/Robin) boundary conditions:** Emerge naturally from the integration by parts

#### Resulting Weak Form
Find \( u \in V \) such that:

$$
a(u, v) = l(v) \quad \forall v \in \hat{V}
$$

where:
- \( a(u, v) \) is a bilinear (or sesquilinear) form
- \( l(v) \) is a linear (or antilinear) functional
- \( V \) is the trial function space
- \( \hat{V} \) is the test function space (often \( V_0 \), the space of functions vanishing on Dirichlet boundaries)

## Fundamental Concepts

### Function Spaces

#### Sobolev Spaces
The natural setting for weak formulations is **Sobolev spaces**:

- \( H^m(\Omega) = \{ u \in L^2(\Omega) : D^\alpha u \in L^2(\Omega), |\alpha| \leq m \} \)
- \( H_0^m(\Omega) = \{ u \in H^m(\Omega) : u = \partial_n u = \cdots = \partial_n^{m-1} u = 0 \text{ on } \partial\Omega \} \)

where derivatives are understood in the weak sense.

#### Trial and Test Spaces
- **Trial space \( V \):** Functions satisfying [[Essential Boundary Conditions]]
- **Test space \( \hat{V} \):** Functions vanishing on essential boundaries (often \( \hat{V} = V_0 \))

### Bilinear Forms and Continuity

A bilinear form \( a: V \times V \rightarrow \mathbb{R} \) is:
- **Continuous (bounded):** \( \exists M > 0 : |a(u, v)| \leq M \|u\|_V \|v\|_V \)
- **Coercive (V-elliptic):** \( \exists \alpha > 0 : a(v, v) \geq \alpha \|v\|_V^2 \)

These properties ensure well-posedness via the Lax-Milgram theorem.

## Examples of Weak Forms

### Poisson Equation

**[[Strong Form (Pointwise Form)]]:**
$$
\begin{aligned}
-\nabla^2 u &= f \quad \text{in } \Omega \\
u &= 0 \quad \text{on } \Gamma_D \\
\frac{\partial u}{\partial n} &= g \quad \text{on } \Gamma_N
\end{aligned}
$$

**Weak form:**
Find \( u \in H_0^1(\Omega) \) such that:
$$
\int_\Omega \nabla u \cdot \nabla v \, d\Omega = \int_\Omega f v \, d\Omega + \int_{\Gamma_N} g v \, d\Gamma \quad \forall v \in H_0^1(\Omega)
$$

### Linear Elasticity

**[[Strong Form (Pointwise Form)]]:**
$$
\begin{aligned}
\nabla \cdot \boldsymbol{\sigma} + \mathbf{b} &= \mathbf{0} \quad \text{in } \Omega \\
\boldsymbol{\sigma} &= \mathbf{C} : \boldsymbol{\varepsilon} \\
\boldsymbol{\varepsilon} &= \frac{1}{2}(\nabla \mathbf{u} + \nabla \mathbf{u}^T)
\end{aligned}
$$

**Weak form ([[Principle of Virtual Work]]):**
Find \( \mathbf{u} \in V \) such that:
$$
\int_\Omega \boldsymbol{\sigma}(\mathbf{u}) : \boldsymbol{\varepsilon}(\mathbf{v}) \, d\Omega = \int_\Omega \mathbf{b} \cdot \mathbf{v} \, d\Omega + \int_{\Gamma_N} \mathbf{t} \cdot \mathbf{v} \, d\Gamma \quad \forall \mathbf{v} \in V_0
$$

### Heat Equation (Transient)

**[[Strong Form (Pointwise Form)]]:**
$$
\rho c_p \frac{\partial T}{\partial t} - \nabla \cdot (k \nabla T) = Q
$$

**Weak form:**
Find \( T \in V \) such that:
$$
\int_\Omega \rho c_p \frac{\partial T}{\partial t} v \, d\Omega + \int_\Omega k \nabla T \cdot \nabla v \, d\Omega = \int_\Omega Q v \, d\Omega + \text{boundary terms} \quad \forall v \in \hat{V}
$$

## Theoretical Foundations

### Variational Principles

For self-adjoint positive-definite operators, the weak form corresponds to the [[Stationarity]] condition of a [[Functional]]:

**Minimization problem:**
$$
u = \arg\min_{v \in V} J(v), \quad J(v) = \frac{1}{2} a(v, v) - l(v)
$$

**Euler-Lagrange equation:**
$$
\delta J(u; v) = a(u, v) - l(v) = 0 \quad \forall v \in V_0
$$

### Existence and Uniqueness

#### Lax-Milgram Theorem
If \( a(\cdot, \cdot) \) is:
1. Continuous: \( |a(u, v)| \leq M \|u\| \|v\| \)
2. Coercive: \( a(v, v) \geq \alpha \|v\|^2 \)

and \( l(\cdot) \) is continuous, then the weak formulation has a unique solution.

#### Babuška-Lax-Milgram Theorem (Generalized)
For mixed formulations or non-symmetric problems, replaces coercivity with an inf-sup condition.

## Advantages over [[Strong Form (Pointwise Form)]]

### Reduced Continuity Requirements
- [[Strong Form (Pointwise Form)]] requires \( u \in C^{2m}(\Omega) \)
- Weak form requires \( u \in H^m(\Omega) \) (derivatives exist in a weaker sense)

### Natural Treatment of Boundary Conditions
- Neumann/Robin conditions emerge naturally
- Easier handling of mixed boundary conditions

### Foundation for Numerical Methods
- Direct discretization leads to Galerkin methods
- Enables finite element, finite volume, and spectral methods

### Mathematical Robustness
- Well-defined for problems with discontinuous coefficients
- Handles singularities and irregular domains better

## Finite Element Implementation

### Galerkin Approximation

Given the weak form:
Find \( u \in V \) such that \( a(u, v) = l(v) \ \forall v \in \hat{V} \)

Approximate \( V \) by a finite-dimensional subspace \( V_h \subset V \):

**Discrete problem:**
Find \( u_h \in V_h \) such that:
$$
a(u_h, v_h) = l(v_h) \quad \forall v_h \in \hat{V}_h
$$

### Matrix Formulation

Let \( \{\phi_i\}_{i=1}^n \) be a basis for \( V_h \). Then:
$$
u_h = \sum_{j=1}^n u_j \phi_j
$$

The discrete problem becomes:
$$
\sum_{j=1}^n a(\phi_j, \phi_i) u_j = l(\phi_i), \quad i = 1, \dots, n
$$

Or in matrix form:
$$
\mathbf{K} \mathbf{u} = \mathbf{F}
$$
where:
- \( K_{ij} = a(\phi_j, \phi_i) \) (stiffness matrix)
- \( F_i = l(\phi_i) \) (load [[Vector]])
- \( \mathbf{u} = [u_1, \dots, u_n]^T \)

## Special Considerations

### Non-Conforming Methods
When \( V_h \not\subset V \), additional terms are needed to ensure [[consistency]] (e.g., discontinuous Galerkin methods).

### Stabilization
For problems lacking coercivity or satisfying inf-sup condition (e.g., advection-dominated, incompressible flow), stabilization terms are added:
$$
a_h(u_h, v_h) + s_h(u_h, v_h) = l_h(v_h)
$$

### Nonlinear Problems
For nonlinear operators \( \mathcal{N}(u) = f \), the weak form becomes:
Find \( u \in V \) such that:
$$
\langle \mathcal{N}(u), v \rangle = \langle f, v \rangle \quad \forall v \in \hat{V}
$$

Linearization leads to sequence of linear problems.

## Error Analysis

### Céa's Lemma
For coercive problems, the Galerkin approximation is quasi-optimal:
$$
\|u - u_h\|_V \leq \frac{M}{\alpha} \inf_{v_h \in V_h} \|u - v_h\|_V
$$

### Strang's Lemmas
For non-conforming or stabilized methods, provide error estimates accounting for consistency errors.

### A Priori Estimates
$$
\|u - u_h\| \leq C h^p \|u\|_{H^{p+1}}
$$
where \( p \) is the polynomial degree of approximation.

## Applications Across Disciplines

### [[Solid Mechanics]]
- Linear and nonlinear elasticity
- Plasticity, viscoelasticity
- Contact mechanics

### Fluid Dynamics
- Stokes and Navier-Stokes equations
- Potential flow
- Boundary layer theory

### Electromagnetics
- Maxwell's equations
- Wave propagation
- Electrostatics and magnetostatics

### Multiphysics Problems
- Thermo-mechanics
- Piezoelectricity
- Fluid-structure interaction

## Advanced Topics

### Mixed Formulations
For problems with constraints (e.g., incompressibility), introduce additional variables:
Find \( (u, p) \in V \times Q \) such that:
$$
\begin{aligned}
a(u, v) + b(p, v) &= l(v) \quad \forall v \in V \\
b(q, u) &= 0 \quad \forall q \in Q
\end{aligned}
$$

### Discontinuous Galerkin Methods
Allow completely discontinuous approximations with penalty terms for inter-element continuity.

### Isogeometric Analysis
Use same basis functions for geometry and solution, often with higher continuity.

## See Also

- [[Strong Form of Differential Equations]]
- [[Galerkin Method]]
- [[Finite Element Method Fundamentals]]
- [[Sobolev Spaces]]
- [[Variational Principles]]
- [[Lax-Milgram Theorem]]
- [[Mixed Finite Element Methods]]
- [[Discontinuous Galerkin Methods]]
- [[Integration by Parts in Multiple Dimensions]]
- [[Boundary Conditions in Weak Formulations]]
## Formal Definition

**Weighted Residual Methods** (WRM) constitute a broad class of numerical techniques for solving [[differential equations]] by requiring that the **residual**—the error obtained when substituting an approximate solution into the governing equation—be orthogonal to a set of carefully chosen **weighting functions** over the problem domain. These methods transform the original differential equation into an integral form that can be discretized and solved numerically, providing the theoretical foundation for many computational techniques including finite element, finite volume, and spectral methods.

## Mathematical Formulation

### General Problem Statement

Consider a boundary value problem defined by:

1. **Differential equation** in domain Ω:
   $$
   \mathcal{L}u = f \quad \text{in } \Omega
   $$
   where:
   - $\mathcal{L}$ = linear differential operator of order $2m$
   - $u$ = unknown field variable
   - $f$ = known source function

2. **Boundary conditions** on boundary Γ = ∂Ω:
   $$
   \mathcal{B}u = g \quad \text{on } \Gamma
   $$

### Approximate Solution Construction

The exact solution $u$ is approximated by a trial function $u_N$ expressed as a linear combination of **basis functions** $\phi_j$:

$$
u_N(\mathbf{x}) = \sum_{j=1}^N c_j \phi_j(\mathbf{x})
$$

where:
- $c_j$ = unknown coefficients to be determined
- $\phi_j(\mathbf{x})$ = prescribed basis functions (must satisfy [[Essential Boundary Conditions]])
- $N$ = number of terms in the approximation

### Residual Definition

The **residual** $R_N$ is the error introduced by the approximation:

$$
R_N(\mathbf{x}) = \mathcal{L}u_N - f
$$

In weighted residual methods, we do not require $R_N(\mathbf{x}) = 0$ pointwise (which would give the exact solution), but rather enforce that the weighted average of the residual vanishes.

### Weighted Residual Statement

The fundamental condition of weighted residual methods is:

$$
\int_\Omega w_i(\mathbf{x}) R_N(\mathbf{x}) \, d\Omega = 0 \quad \text{for } i = 1, 2, \ldots, N
$$

where $w_i(\mathbf{x})$ are **weighting functions** (also called **test functions**). This yields a system of $N$ equations to determine the $N$ unknown coefficients $c_j$.

## Classification of Weighted Residual Methods

The specific choice of weighting functions distinguishes different weighted residual methods:

### 1. Collocation Method
**Weighting functions:** Dirac delta functions at selected points
$$
w_i(\mathbf{x}) = \delta(\mathbf{x} - \mathbf{x}_i)
$$
**Resulting condition:** $R_N(\mathbf{x}_i) = 0$ at collocation points $\mathbf{x}_i$
**Advantages:** Simple implementation, no integration required
**Disadvantages:** Accuracy depends heavily on point selection

### 2. Subdomain Method
**Weighting functions:** Characteristic functions of subdomains
$$
w_i(\mathbf{x}) = 
\begin{cases}
1 & \text{if } \mathbf{x} \in \Omega_i \\
0 & \text{otherwise}
\end{cases}
$$
where $\Omega = \bigcup_{i=1}^N \Omega_i$
**Resulting condition:** Average residual over each subdomain is zero
**Advantages:** Conservative, leads to finite volume methods

### 3. [[Least Squares Method]]
**Weighting functions:** Derivatives of residual with respect to coefficients
$$
w_i = \frac{\partial R_N}{\partial c_i}
$$
**Resulting condition:** Minimizes $\int_\Omega R_N^2 d\Omega$
**Advantages:** Always yields symmetric positive definite matrices
**Disadvantages:** Requires higher differentiability, computationally intensive

### 4. [[Galerkin Method]]
**Weighting functions:** Same as basis functions (Bubnov-Galerkin)
$$
w_i = \phi_i
$$
**Resulting condition:** Residual orthogonal to basis function space
**Advantages:** Optimal approximation properties for self-adjoint operators, leads to symmetric matrices
**Disadvantages:** May not be optimal for non-self-adjoint problems

### 5. [[Petrov-Galerkin Method]]
**Weighting functions:** Different from basis functions
$$
w_i \neq \phi_i
$$
**Resulting condition:** Residual orthogonal to a different function space
**Advantages:** Can stabilize convection-dominated problems
**Disadvantages:** Loss of symmetry, more complex analysis

### 6. Method of Moments
**Weighting functions:** Members of a complete set (e.g., polynomials, trigonometric functions)
**Resulting condition:** Successive moments of residual vanish
**Advantages:** Systematic approach, good for infinite domains
**Disadvantages:** Choice of moment functions critical

## Theoretical Foundations

### Completeness and Convergence

For convergence as $N \to \infty$, the basis functions $\{\phi_j\}$ must form a **complete set** in the appropriate function space (e.g., $H^m(\Omega)$ for $2m$-order operators). Common choices include:

1. **Polynomials:** Power series, [[Legendre polynomials]], Chebyshev polynomials
2. **Trigonometric functions:** [[Fourier series]]
3. **Piecewise polynomials:** Finite element basis functions
4. **Wavelets:** Multi-resolution analysis
5. **Radial basis functions:** For meshless methods

### Error Analysis

The error $e_N = u - u_N$ satisfies an **orthogonality condition**:

$$
\int_\Omega w_i \mathcal{L} e_N \, d\Omega = 0 \quad \text{for } i = 1, \ldots, N
$$

For [[Galerkin Method]] with self-adjoint positive definite $\mathcal{L}$, we have the **best approximation property** in the energy norm:

$$
\|u - u_N\|_E \leq \|u - v\|_E \quad \forall v \in V_N
$$

where $V_N = \text{span}\{\phi_1, \ldots, \phi_N\}$.

## Implementation Procedure

### Step-by-Step Algorithm

1. **Select basis functions** $\phi_j$ that satisfy [[Essential Boundary Conditions]]
2. **Choose weighting functions** $w_i$ according to the desired method
3. **Form approximate solution:** $u_N = \sum_{j=1}^N c_j \phi_j$
4. **Compute residual:** $R_N = \mathcal{L}u_N - f$
5. **Form weighted residual equations:**
   $$
   \int_\Omega w_i R_N \, d\Omega = 0 \quad \Rightarrow \quad \sum_{j=1}^N A_{ij} c_j = b_i
   $$
   where:
   - $A_{ij} = \int_\Omega w_i \mathcal{L}\phi_j \, d\Omega$
   - $b_i = \int_\Omega w_i f \, d\Omega$
6. **Solve linear system** $\mathbf{A}\mathbf{c} = \mathbf{b}$ for coefficients $c_j$
7. **Construct approximate solution** $u_N$

### Treatment of Boundary Conditions

**Essential (Dirichlet) conditions:** Built into basis functions
**Natural (Neumann) conditions:** Incorporated through integration by parts or included in the weighted residual statement

## Relationship to Other Numerical Methods

### [[Finite Element Method]] (FEM)
- [[Galerkin Method]] with piecewise polynomial basis functions
- Local support basis functions lead to sparse matrices
- Natural handling of complex geometries

### Finite Volume Method (FVM)
- Subdomain method with control volumes
- Conservative by construction
- Popular in fluid dynamics

### Spectral Methods
- Galerkin or collocation methods with global basis functions (Fourier, Chebyshev)
- Exponential convergence for smooth solutions
- Limited to simple geometries

### Boundary Element Method (BEM)
- Weighted residual method applied to boundary integral equations
- Reduces dimensionality by one
- Effective for infinite domains

## Advanced Formulations

### Weak Form Formulation

For second-order problems, integration by parts yields the **weak form**:

$$
\int_\Omega \nabla w_i \cdot \mathbf{D} \nabla u_N \, d\Omega = \int_\Omega w_i f \, d\Omega + \text{boundary terms}
$$

which:
- Reduces differentiability requirements
- Incorporates [[Natural Boundary Conditions]] automatically
- Forms the basis for finite element methods

### Variational Framework

For self-adjoint positive definite operators, the [[Galerkin Method]] is equivalent to minimizing the [[Functional]]:

$$
J[u] = \frac{1}{2} a(u,u) - (f,u)
$$

where $a(\cdot,\cdot)$ is the bilinear form associated with $\mathcal{L}$.

### Stabilized Methods

For problems lacking coercivity or satisfying inf-sup conditions (e.g., convection-dominated, incompressible flow):

**Streamline-Upwind/Petrov-Galerkin (SUPG):**
$$
w_i = \phi_i + \tau \mathbf{b} \cdot \nabla \phi_i
$$
where $\mathbf{b}$ is the [[velocity field]], $\tau$ is stabilization parameter.

**Galerkin/Least-Squares (GLS):**
$$
w_i = \phi_i + \tau \mathcal{L}\phi_i
$$

## Applications Across Engineering Disciplines

### Structural Mechanics
- Stress analysis using [[Principle of Virtual Work]] ([[Galerkin Method]])
- Plate and shell bending
- Contact problems

### Fluid Dynamics
- Navier-Stokes equations (Petrov-Galerkin for convection)
- Potential flow (boundary element methods)
- Turbulence modeling

### [[Heat Transfer]]
- Conduction, convection, radiation problems
- Phase change (Stefan problems)

### Electromagnetics
- Maxwell's equations
- Wave propagation
- Antenna design

### Geomechanics
- Soil consolidation
- Groundwater flow
- Rock mechanics

## Error Estimation and Adaptivity

### A Priori Error Estimates
Depend on solution regularity and approximation properties:
$$
\|u - u_N\| \leq C h^p \|u\|_{H^{p+1}}
$$
where $h$ is mesh size, $p$ is polynomial degree.

### A Posteriori Error Estimates
Based on computed solution:
- **Residual-based estimators:** $\eta^2 = \sum_K h_K^2 \|R\|_{L^2(K)}^2 + \sum_E h_E \|J\|_{L^2(E)}^2$
- **Recovery-based estimators:** Zienkiewicz-Zhu estimator
- **Goal-oriented estimators:** For specific quantities of interest

### Adaptive Refinement Strategies
1. **h-adaptivity:** Mesh refinement/coarsening
2. **p-adaptivity:** Changing polynomial order
3. **hp-adaptivity:** Combined h- and p-refinement
4. **r-adaptivity:** Mesh movement

## Specialized Weighted Residual Methods

### Discontinuous Galerkin Method
Allows discontinuities across element boundaries with penalty terms:
$$
\sum_K \int_K (\mathcal{L}u_N - f) w \, d\Omega + \sum_E \int_E \text{penalty terms} \, dS = 0
$$

### Spectral Element Method
Combines spectral accuracy with geometric flexibility of finite elements.

### Meshfree Methods
- **Element-free Galerkin:** Moving least squares approximation
- **Smoothed Particle Hydrodynamics:** Kernel-based approximation
- **Reproducing Kernel Particle Method:** Higher-order [[consistency]]

## Convergence Analysis

### [[Consistency]]
The method is **consistent** if the exact solution satisfies the discrete equations:
$$
\int_\Omega w_i (\mathcal{L}u - f) \, d\Omega = 0
$$

### Stability
The discrete problem is **stable** if:
$$
\|u_N\| \leq C \|f\|
$$
independent of $N$.

### Lax Equivalence Theorem
For linear problems: **[[Consistency]] + Stability ⇔ Convergence**

## Computational Aspects

### Matrix Properties

**Galerkin method for symmetric $\mathcal{L}$:**
- Symmetric positive definite matrices
- Banded structure for local basis functions
- Condition number $O(h^{-2})$ for second-order problems

**Collocation method:**
- Non-symmetric matrices
- Full or structured depending on basis

**[[Least squares method]]:**
- Symmetric positive definite normal equations
- Squared condition number

### Numerical Integration

Most weighted residual methods require numerical integration:
- **Gauss quadrature:** Optimal for polynomials
- **Adaptive quadrature:** For singular or oscillatory integrands
- **Integration by lookup:** For complex basis functions

## Limitations and Challenges

### Method Selection Trade-offs
- **Accuracy vs. efficiency:** Higher accuracy often requires more computational effort
- **Generality vs. specialization:** General methods may be less efficient for specific problems
- **Implementation complexity:** Some methods are significantly harder to implement

### Common Difficulties
1. **Choice of basis/weighting functions:** Critical for accuracy and stability
2. **Treatment of singularities:** Requires special functions or adaptive refinement
3. **Nonlinear problems:** Require linearization and iterative solution
4. **Time-dependent problems:** Need appropriate time discretization coupled with spatial discretization

## Historical Development

### Early Developments
- **1915:** Boris Galerkin introduces [[Galerkin Method]]
- **1930s:** Collocation methods developed
- **1940s:** Least squares methods formalized
- **1950s:** [[Finite Element Method]] emerges from structural analysis
- **1960s:** Mathematical analysis of weighted residual methods
- **1970s:** Stabilized methods for convection-dominated problems
- **1980s:** hp-adaptive methods
- **1990s:** Discontinuous Galerkin methods gain popularity
- **2000s:** Isogeometric analysis

### Key Contributors
1. **Boris Galerkin (1871-1945):** Galerkin method
2. **Richard Courant (1888-1972):** Early finite element concepts
3. **Raymond Mindlin (1906-1987):** Applications in elasticity
4. **Olga Ladyzhenskaya (1922-2004):** Mathematical analysis
5. **Ivo Babuška (1926-2023):** Finite element error analysis
6. **Thomas Hughes (1943-2020):** Stabilized and isogeometric methods

## See Also

- [[Galerkin Method]]
- [[Finite Element Method]]
- [[Collocation Methods]]
- [[Least Squares Method]]
- [[Method of Moments]]
- [[Weak Form (Variational Form)]]
- [[Variational Methods]]
- [[Spectral Methods]]
- [[Discontinuous Galerkin Methods]]
- [[Error Estimation in Numerical Methods]]
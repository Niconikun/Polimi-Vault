## Formal Definition

The **Petrov-[[Galerkin Method]]** is a weighted residual numerical technique for solving differential equations where the test (weighting) functions are chosen from a different function space than the trial (approximation) functions. This approach generalizes the standard [[Galerkin Method]] by allowing asymmetric formulations, which is particularly advantageous for problems with non-self-adjoint operators, convection-dominated phenomena, or when specific stabilization is required.

## Mathematical Formulation

### General Boundary Value Problem

Consider a linear boundary value problem:

1. **Governing equation:**
   $$ \mathcal{L}u = f \quad \text{in } \Omega $$
   where:
   - $\mathcal{L}$ = linear differential operator (potentially non-self-adjoint)
   - $u$ = unknown field variable
   - $f$ = known source function

2. **Boundary conditions:**
   $$ \mathcal{B}u = g \quad \text{on } \Gamma = \partial\Omega $$

### Petrov-Galerkin Approximation

1. **Function Space Selection:**
   - **Trial space:** $V_n = \text{span}\{\phi_1, \phi_2, \ldots, \phi_n\} \subset V$
     where $\phi_i$ satisfy [[Essential Boundary Conditions]]
   - **Test space:** $W_n = \text{span}\{\psi_1, \psi_2, \ldots, \psi_n\} \subset W$
     where $\psi_i$ may be chosen from a different space than $\phi_i$

2. **Approximate Solution:**
   $$ u_n(\mathbf{x}) = \sum_{j=1}^n c_j \phi_j(\mathbf{x}) $$

3. **Weighted Residual Statement:**
   Find $u_n \in V_n$ such that:
   $$ \int_\Omega \psi_i (\mathcal{L}u_n - f) \, d\Omega = 0 \quad \forall \psi_i \in W_n, \ i = 1, \ldots, n $$

4. **Resulting Linear System:**
   $$ \sum_{j=1}^n \left[ \int_\Omega \psi_i \mathcal{L}\phi_j \, d\Omega \right] c_j = \int_\Omega \psi_i f \, d\Omega $$
   Or in matrix form:
   $$ \mathbf{K} \mathbf{c} = \mathbf{F} $$
   where:
   - $K_{ij} = \int_\Omega \psi_i \mathcal{L}\phi_j \, d\Omega$ (generally non-symmetric)
   - $F_i = \int_\Omega \psi_i f \, d\Omega$

## Theoretical Foundations

### Variational Formulation

For the Petrov-[[Galerkin Method]], we seek $u_n \in V_n$ such that:
$$ a(u_n, v) = l(v) \quad \forall v \in W_n $$
where:
- $a(u, v) = \int_\Omega v \mathcal{L}u \, d\Omega$ = bilinear form (not necessarily symmetric)
- $l(v) = \int_\Omega v f \, d\Omega$ = linear [[Functional]]

### Inf-Sup (Babuska-Brezzi) Condition

For stability and uniqueness, the following condition must be satisfied:
$$ \exists \beta > 0 : \sup_{v \in W_n} \frac{a(u, v)}{\|v\|_W} \geq \beta \|u\|_V \quad \forall u \in V_n $$
This ensures that the discrete problem is well-posed even when $a(\cdot, \cdot)$ is not coercive.

## Motivation and Rationale

The Petrov-[[Galerkin Method]] is employed when:

1. **Operator Non-Symmetry:** $\mathcal{L}$ is non-self-adjoint ($\mathcal{L} \neq \mathcal{L}^*$)
2. **Physical Asymmetry:** The problem has directional preferences (e.g., convection-diffusion)
3. **Stabilization Needs:** Standard Galerkin produces spurious oscillations
4. **Accuracy Enhancement:** Better approximation properties for specific problem types

## Key Variants and Applications

### 1. Streamline-Upwind/Petrov-Galerkin (SUPG)
For convection-dominated problems ($\epsilon \nabla^2 u + \mathbf{b} \cdot \nabla u = f$):
- **Test functions:** $\psi_i = \phi_i + \tau \mathbf{b} \cdot \nabla \phi_i$
- **Stabilization parameter:** $\tau$ based on local mesh size and flow field
- **Purpose:** Adds streamline diffusion to suppress crosswind oscillations

### 2. Galerkin/Least-Squares (GLS)
General stabilization approach:
- **Test functions:** $\psi_i = \phi_i + \tau \mathcal{L}\phi_i$
- **Unifies** SUPG and other stabilization methods
- **Provides** consistent stabilization for various problem types

### 3. Discontinuous Petrov-Galerkin (DPG)
- Uses **optimal test functions** computed element-by-element
- Achieves **ultraweak formulation** with broken test spaces
- Provides **automatic stability** and built-in error estimators

### 4. Subgrid Scale (SGS) Methods
- Decompose solution into **resolved** and **unresolved** (subgrid) scales
- Model effect of unresolved scales on resolved scales
- Test functions modified to account for subgrid interactions

## Implementation Considerations

### Matrix Properties
- **Non-symmetric:** $\mathbf{K}^T \neq \mathbf{K}$ generally
- **Solvers required:** Need algorithms for non-symmetric systems (GMRES, BiCGSTAB)
- **Storage:** May require full matrix storage rather than symmetric storage

### Test Function Construction
Methods for selecting $\psi_i$:

1. **Analytical approach:** Based on adjoint operator or physical insight
2. **Parameterized modification:** $\psi_i = \phi_i + \text{stabilization term}$
3. **Optimal test functions:** Solve local problems for best approximation
4. **Empirical selection:** Based on numerical experiments

## Advantages

1. **Stabilization Capability:** Effectively handles convection-dominated and other unstable problems
2. **Flexibility:** Can tailor test functions to specific problem characteristics
3. **Improved Accuracy:** Often provides better solutions than standard Galerkin for non-symmetric problems
4. **Broader Applicability:** Can solve problems where [[Galerkin Method]] fails or performs poorly
5. **Physical Interpretation:** Test functions can incorporate directional or physical preferences

## Limitations

1. **Increased Complexity:** More difficult to implement than standard Galerkin
2. **Parameter Sensitivity:** Many variants require problem-dependent stabilization parameters
3. **Theoretical Challenges:** Analysis more complex due to non-symmetric formulations
4. **Computational Cost:** Non-symmetric matrices require more storage and computational effort
5. **Lack of Variational Structure:** Not derived from minimization principle for non-self-adjoint problems

## Error Analysis

### Convergence Properties
- **Optimal convergence:** Achieved with appropriate test function selection
- **Consistency:** Method is consistent if exact solution satisfies discrete equations
- **Stability:** Governed by inf-sup condition rather than coercivity

### A Priori Estimates
For properly stabilized methods:
$$ \|u - u_n\| \leq C h^k \|u\|_{k+1} $$
where $k$ depends on polynomial degree and stabilization effectiveness

## Relationship to Other Methods

1. **[[Galerkin Method]]:** Special case when $W_n = V_n$ (Bubnov-Galerkin)
2. **Least-Squares FEM:** Can be viewed as Petrov-Galerkin with $\psi_i = \mathcal{L}\phi_i$
3. **Collocation Method:** Limit case with Dirac delta test functions
4. **Finite Volume Method:** Some FVM formulations can be interpreted as Petrov-Galerkin

## Practical Applications

1. **Fluid Dynamics:** Navier-Stokes equations, especially high Reynolds number flows
2. **Convection-Diffusion-Reaction:** Chemical transport, pollutant dispersion
3. **Wave Propagation:** Helmholtz equation, acoustics, electromagnetics
4. **Plasma Physics:** Magnetohydrodynamics (MHD) equations
5. **Multiscale Problems:** Problems with dominant directional features

## See Also

- [[Galerkin Method]]
- Streamline-Upwind/Petrov-Galerkin (SUPG)
- Galerkin/Least-Squares (GLS) Method
- Discontinuous Petrov-Galerkin Method
- Stabilized Finite Element Methods
- Babuska-Brezzi Condition
- [[Weighted Residual Methods]]
- Non-Self-Adjoint Problems
- Convection-Dominated Problems

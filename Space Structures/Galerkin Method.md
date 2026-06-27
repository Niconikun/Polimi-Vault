## Formal Definition

The **Galerkin Method** is a weighted residual numerical technique for solving [[differential equations]] by projecting the residual onto a finite-dimensional subspace of test functions. As a member of the broader class of **Method of Weighted Residuals (MWR)**, it transforms continuous differential equations into discrete algebraic systems by enforcing orthogonality between the residual and a set of weighting functions. In its most common form, the **Bubnov-Galerkin** method, the weighting functions are chosen to be identical to the trial functions used to approximate the solution.

## Mathematical Formulation

### General Boundary Value Problem

Consider a linear boundary value problem defined by:

1. **Governing differential equation** in domain Ω:
   $$ \mathcal{L}u = f \quad \text{in } \Omega $$
   where:
   - $\mathcal{L}$ = linear differential operator
   - $u$ = unknown field variable
   - $f$ = known source function

2. **Boundary conditions** on boundary Γ = ∂Ω:
   $$ \mathcal{B}u = g \quad \text{on } \Gamma $$

### Galerkin Approximation Procedure

1. **Trial Function Selection:**
   Choose a finite set of $n$ linearly independent **trial functions** $\phi_i(\mathbf{x})$ that:
   - Satisfy all essential (Dirichlet) boundary conditions
   - Form a basis for the approximation space $V_n \subset V$

2. **Solution Approximation:**
   Express the approximate solution as:
   $$ u_n(\mathbf{x}) = \sum_{j=1}^n c_j \phi_j(\mathbf{x}) $$
   where $c_j$ are unknown coefficients to be determined.

3. **Residual Definition:**
   The residual $R_n$ is the error in satisfying the differential equation:
   $$ R_n(\mathbf{x}) = \mathcal{L}u_n - f = \sum_{j=1}^n c_j \mathcal{L}\phi_j - f $$

4. **Weighted Residual Statement:**
   Require the residual to be orthogonal to each weighting function $w_i$ in the inner product sense:
   $$ \int_\Omega w_i(\mathbf{x}) R_n(\mathbf{x}) \, d\Omega = 0 \quad \text{for } i = 1, 2, \ldots, n $$

5. **Bubnov-Galerkin Specific Choice:**
   Select weighting functions identical to trial functions:
   $$ w_i(\mathbf{x}) = \phi_i(\mathbf{x}) $$

6. **Resulting Linear System:**
   The orthogonality condition yields:
   $$ \int_\Omega \phi_i \left( \sum_{j=1}^n c_j \mathcal{L}\phi_j - f \right) d\Omega = 0 $$
   Rearranging gives the linear system:
   $$ \sum_{j=1}^n \left[ \int_\Omega \phi_i \mathcal{L}\phi_j \, d\Omega \right] c_j = \int_\Omega \phi_i f \, d\Omega $$
   Or in matrix form:
   $$ \mathbf{K} \mathbf{c} = \mathbf{F} $$
   where:
   - $K_{ij} = \int_\Omega \phi_i \mathcal{L}\phi_j \, d\Omega$ = stiffness matrix coefficient
   - $F_i = \int_\Omega \phi_i f \, d\Omega$ = load vector component
   - $\mathbf{c} = [c_1, c_2, \ldots, c_n]^T$ = unknown coefficient vector

## Theoretical Foundation

### Variational Basis

For symmetric, positive-definite operators $\mathcal{L}$, the Galerkin method is equivalent to minimizing the quadratic functional:
$$ \Pi(u) = \frac{1}{2} a(u, u) - (f, u) $$
where:
- $a(u, v) = \int_\Omega u \mathcal{L}v \, d\Omega$ = symmetric bilinear form
- $(f, u) = \int_\Omega f u \, d\Omega$ = linear [[Functional]]

The Galerkin formulation then corresponds to:
$$ a(u_n, v) = (f, v) \quad \forall v \in V_n $$

### Error Analysis

The Galerkin solution $u_n$ satisfies the **best approximation property** in the energy norm:
$$ \| u - u_n \|_E \leq \| u - v \|_E \quad \forall v \in V_n $$
where the energy norm is defined as $\| v \|_E = \sqrt{a(v, v)}$.

## Classification of Galerkin Methods

1. **Bubnov-Galerkin Method:** $w_i = \phi_i$ (most common in structural mechanics)
2. **[[Petrov-Galerkin Method]]:** $w_i \neq \phi_i$ (used for convection-dominated problems)
3. **Continuous Galerkin (CG):** Trial and test functions are continuous across element boundaries
4. **Discontinuous Galerkin (DG):** Functions may be discontinuous at element boundaries

## Key Properties

1. **Variational Consistency:** For self-adjoint problems, yields symmetric positive-definite matrices.
2. **Optimal Approximation:** Provides the best approximation in the energy norm.
3. **Orthogonality of Error:** The error $e = u - u_n$ satisfies $a(e, v) = 0$ for all $v \in V_n$.
4. **Convergence:** As the approximation space is enriched ($n \to \infty$), $u_n$ converges to $u$ under appropriate conditions.

## Finite Element Implementation

In the [[Finite Element Method]] (FEM), the Galerkin method is applied with:

1. **Local Basis Functions:** Trial functions $\phi_i$ are piecewise polynomials defined over elements.
2. **Assembly Procedure:** Global matrices assembled from element contributions:
   $$ K_{ij} = \sum_{e=1}^{N_e} \int_{\Omega_e} \nabla \phi_i \cdot \mathbf{D} \nabla \phi_j \, d\Omega $$
   for diffusion-type problems with material tensor $\mathbf{D}$.

## Applications

1. **Structural Mechanics:** Stress analysis, vibration, buckling
2. **Fluid Dynamics:** Navier-Stokes equations (often with Petrov-Galerkin stabilization)
3. **[[Heat Transfer]]:** Conduction, convection, radiation problems
4. **Electromagnetics:** Maxwell's equations
5. **Multiphysics Problems:** Coupled field analyses

## Relationship to Other Methods

1. **Ritz Method:** For self-adjoint problems, Galerkin method yields identical results to Ritz method when using same trial functions.
2. **Finite Difference Method:** Galerkin FEM can be interpreted as a generalized finite difference scheme.
3. **Collocation Method:** Special case where weighting functions are Dirac delta functions at collocation points.
4. **[[Least Squares Method]]:** Different weighting strategy minimizing squared residual.

## Advantages

1. **Mathematical Rigor:** Strong theoretical foundation with convergence proofs.
2. **Flexibility:** Applicable to a wide range of [[differential equations]].
3. **Systematic Procedure:** Well-defined steps for implementation.
4. **[[Natural Boundary Conditions]]:** Neumann/Robin conditions incorporated automatically.
5. **Energy Conservation:** For conservative systems, preserves fundamental physical principles.

## Limitations

1. **Symmetric Operator Requirement:** For optimal properties, requires symmetric positive-definite operators.
2. **Convection-Dominated Problems:** Standard Galerkin suffers from numerical oscillations (requires stabilization).
3. **Boundary Layer Resolution:** May require adaptive refinement or special functions.
4. **Computational Cost:** Integration and assembly can be expensive for complex problems.

## Stabilization Techniques (for non-ideal problems)

1. **Streamline-Upwind/Petrov-Galerkin (SUPG):** Modified weighting functions for convection-dominated flows.
2. **Galerkin/Least-Squares (GLS):** Adds least-squares stabilization term.
3. **Discontinuous Galerkin:** Allows discontinuities with flux terms to handle steep gradients.
4. **Subgrid Scale Methods:** Resolve fine-scale features not captured by coarse mesh.

## Error Estimation and Adaptivity

1. **A Posteriori Error Estimates:** Use computed solution to estimate error distribution.
2. **h-Adaptivity:** Refine mesh based on error indicators.
3. **p-Adaptivity:** Increase polynomial order in high-error regions.
4. **hp-Adaptivity:** Combine h- and p-refinement for optimal convergence.

## See Also

- [[Weighted Residual Methods]]
- [[Finite Element Method]]
- [[Ritz Method (Rayleigh-Ritz Method)]]
- [[Variational Formulation]]
- [[Weak Form (Variational Form)]]
- [[Petrov-Galerkin Method]]
- [[Bubnov-Galerkin Method]]
- [[Discontinuous Galerkin Method]]
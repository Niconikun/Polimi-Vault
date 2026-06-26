#Space-Structures #TBD 
## Formal Definition

The **Finite Element Method (FEM)** is a numerical technique for obtaining approximate solutions to [[Boundary Value Problems]] governed by [[partial differential equations (PDEs)]] or integral equations. By discretizing a continuous domain into a finite number of interconnected simple geometric subdomains called **elements**, FEM transforms complex continuum problems into discrete systems of algebraic equations that can be solved computationally. The method is characterized by its variational foundation, piecewise polynomial approximations, and systematic assembly procedures.

## Historical and Theoretical Foundations

### Historical Development
- **Origins:** Developed in the 1950s for structural analysis in aerospace engineering
- **Pioneers:** Argyris, Clough, Turner, Zienkiewicz, O.C.
- **Theoretical Basis:** Combines principles from variational calculus, [[Weighted Residual Methods]], and structural mechanics

### Mathematical Framework
FEM is founded on three equivalent formulations:
1. **Variational Formulation:** Based on minimization of energy functionals (for self-adjoint operators)
2. **Weak Formulation:** Integral form obtained through integration by parts
3. **Weighted Residual Formulation:** Direct approximation of differential equations

## Core Components and Terminology

### 1. Domain Discretization
- **Mesh:** Collection of finite elements covering the domain Ω
- **Elements:** Basic building blocks (triangles, quadrilaterals, tetrahedra, hexahedra)
- **Nodes:** Discrete points where [[degrees of freedom]] are defined
- **Element Connectivity:** Mapping between local and global numbering

### 2. Approximation Spaces
- **Trial Functions:** Basis functions for approximating the solution field
- **Test Functions:** Weighting functions for residual minimization
- **Shape Functions:** Local polynomial functions defined per element
- **Global Approximation:** $u^h(\mathbf{x}) = \sum_{i=1}^{N} N_i(\mathbf{x}) u_i$

### 3. Governing Equations
The general boundary value problem:
$$
\begin{aligned}
\mathcal{L}u &= f \quad \text{in } \Omega \\
\mathcal{B}u &= g \quad \text{on } \Gamma
\end{aligned}
$$
where \(\mathcal{L}\) is a differential operator and \(\mathcal{B}\) defines boundary conditions.

## Methodological Procedure

### Step 1: Problem Formulation
1. **[[Strong Form (Pointwise Form)]]:** Original PDE with boundary conditions
2. **[[Weak Form (Variational Form)]]:** Multiply by test function \(v\) and integrate:
   $$ \int_\Omega v\mathcal{L}u\,d\Omega = \int_\Omega vf\,d\Omega $$
3. **Integration by Parts:** Reduces derivative order, introduces [[Natural Boundary Conditions]]

### Step 2: Domain Discretization
1. **Mesh Generation:** Subdivide Ω into elements Ωₑ
2. **Node Numbering:** Global and local numbering schemes
3. **Element Selection:** Choose appropriate element types based on physics

### Step 3: Element Formulation
1. **Shape Function Definition:** $\mathbf{N}^e(\mathbf{x})$ for element e
2. **Field Approximation:** $u^e(\mathbf{x}) = \mathbf{N}^e(\mathbf{x})\mathbf{u}^e$
3. **[[Strain]]-Displacement:** $\varepsilon^e = \mathbf{B}^e\mathbf{u}^e$
4. **Constitutive Relation:** $\sigma^e = \mathbf{D}^e\varepsilon^e$

### Step 4: Assembly Process
1. **Element Matrices:** Compute local stiffness \(\mathbf{k}^e\) and load \(\mathbf{f}^e\)
2. **Global Assembly:** $\mathbf{K} = \bigwedge_{e=1}^{N_e} \mathbf{k}^e, \quad \mathbf{F} = \bigwedge_{e=1}^{N_e} \mathbf{f}^e$
3. **Boundary Conditions:** Apply essential and [[Natural Boundary Conditions]]

### Step 5: Solution
1. **Linear System:** $\mathbf{K}\mathbf{u} = \mathbf{F}$
2. **Solvers:** Direct (Gaussian elimination) or iterative (CG, GMRES) methods
3. **Post-processing:** Compute derived quantities (stresses, fluxes, etc.)

## Mathematical Formulations

### [[Weak Form (Variational Form)]] Derivation
For Poisson's equation \(-\nabla^2 u = f\):
$$
\int_\Omega \nabla v \cdot \nabla u \, d\Omega = \int_\Omega vf \, d\Omega + \int_\Gamma v\frac{\partial u}{\partial n} \, d\Gamma
$$

### Galerkin Approximation
$$ \int_\Omega \nabla N_i \cdot \nabla N_j \, d\Omega \, u_j = \int_\Omega N_i f \, d\Omega $$

### Element Stiffness Matrix
$$ \mathbf{k}^e = \int_{\Omega^e} \mathbf{B}^{eT} \mathbf{D}^e \mathbf{B}^e \, d\Omega $$

## Key Theoretical Concepts

### 1. Approximation Theory
- **Interpolation Error:** $\|u - u^h\| \leq Ch^{p+1}|u|_{p+1}$
- **Convergence:** $h$-refinement (mesh size) and $p$-refinement (polynomial order)
- **A Priori Estimates:** Theoretical error bounds

### 2. Variational Principles
- **Minimum Potential Energy:** For elastic systems
- **[[Principle of Virtual Work]]:** General [[Continuum Mechanics]]
- **[[Hamilton's Principle]]:** Dynamic systems

### 3. Numerical Integration
- **Gauss Quadrature:** Optimal integration points and weights
- **Jacobian Transformation:** Mapping to reference elements
- **Integration Order:** Balancing accuracy and efficiency

## Element Families and Characteristics

### 1. Lagrangian Elements
- **Basis:** Lagrange polynomials
- **Continuity:** C⁰ continuous
- **Applications:** [[Heat transfer]], potential flow

### 2. Hermitian Elements
- **Basis:** Hermite polynomials
- **Continuity:** C¹ continuous
- **Applications:** Beam bending, plate bending

### 3. Hierarchical Elements
- **Basis:** Nested polynomial spaces
- **Advantages:** Efficient $p$-refinement

### 4. Isoparametric Elements
- **Geometry:** Same shape functions for geometry and field variables
- **Mapping:** Reference to physical coordinates via $\mathbf{x} = \sum N_i \mathbf{x}_i$

## Convergence and Error Analysis

### Convergence Criteria
1. **Completeness:** Shape functions can represent constant [[strain]]/stress states
2. **Compatibility:** Field continuity across element boundaries
3. **Stability:** Satisfying inf-sup conditions for mixed formulations

### Error Estimation
1. **A Priori:** Theoretical bounds based on mesh size and polynomial degree
2. **A Posteriori:** Computable from numerical solution
   - Residual-based estimators
   - Recovery-based estimators (Zienkiewicz-Zhu)
1. **Adaptive Refinement:** $h$, $p$, and $hp$ strategies

## Implementation Aspects

### Data Structures
- **Nodal Coordinates:** Geometry representation
- **Element Connectivity:** Topology information
- **Material Properties:** Element-specific parameters
- **Boundary Conditions:** Essential and natural constraints

### Matrix Properties
- **Sparsity:** Banded structure from local connectivity
- **Symmetry:** For self-adjoint problems
- **Positive Definiteness:** For well-posed elliptic problems

### Computational Considerations
1. **Condition Number:** Affects solver performance
2. **Mesh Quality:** Aspect ratio, skewness, Jacobian positivity
3. **Locking:** Numerical stiffening (shear, volumetric, membrane)

## Applications Spectrum

### Structural Mechanics
- Stress analysis, vibration, buckling, contact

### Field Problems
- [[Heat transfer]], fluid dynamics, electromagnetics

### Multiphysics
- Thermo-mechanical, fluid-structure interaction, piezoelectric

### Specialized Formulations
- Non-linear materials, large deformations, fracture mechanics

## Advantages and Limitations

### Advantages
1. **Geometric Flexibility:** Complex domains via meshing
2. **Systematic Procedure:** General framework for diverse problems
3. **Mathematical Rigor:** Strong theoretical foundation
4. **Adaptability:** Local refinement and error control
5. **Commercial Maturity:** Extensive software ecosystem

### Limitations
1. **Mesh Dependency:** Solution quality tied to discretization
2. **Computational Cost:** Large systems require significant resources
3. **Numerical Artifacts:** Locking, hourglassing, shear checking
4. **Mesh Generation:** Non-trivial for complex 3D geometries

## Advanced Topics

### Nonlinear Analysis
1. **Material Nonlinearity:** Plasticity, viscoelasticity, damage
2. **Geometric Nonlinearity:** Large deformations, buckling
3. **Contact Nonlinearity:** Changing boundary conditions

### Time-Dependent Problems
1. **Semi-discretization:** Method of lines
2. **Time Integration:** Newmark, [[Runge-Kutta Methods]], generalized-α

### Special Techniques
1. **Mixed Formulations:** Independent approximation of multiple fields
2. **Stabilized Methods:** SUPG, GLS for convection-dominated problems
3. **Discontinuous Galerkin:** Higher-order continuity not required
4. **Extended FEM (XFEM):** Modeling discontinuities and singularities

## Relationship to Other Methods

### Complementary Methods
- **Boundary Element Method (BEM):** Discretizes boundaries only
- **Finite Difference Method (FDM):** Regular grids, [[Strong Form (Pointwise Form)]]
- **Finite Volume Method (FVM):** Conservation laws, integral balance

### Hybrid Approaches
- **FEM-BEM Coupling:** Interior and exterior problems
- **FEM-FVM:** Fluid-structure interaction
- **Isogeometric Analysis (IGA):** CAD-integrated FEM

## See Also

- [[Weak Form (Variational Form)]]
- [[Galerkin Method]]
- Shape Functions]]
- [[Isoparametric Formulation]]
- [[Stiffness Matrix Assembly]]
- Error Estimation and Adaptivity]]
- [[Nonlinear Finite Element Analysis]]
- [[Computational Mechanics]]
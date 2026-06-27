## Formal Definition

**Shell Theory** is a collection of mathematical models and mechanical theories that describe the behavior of curved structural elements with one dimension (thickness) significantly smaller than the other two (in-plane dimensions). These theories extend plate theories to curved surfaces, capturing the complex coupling between bending and membrane actions that arises from initial curvature, enabling analysis of diverse structures from pressure vessels to aircraft fuselages.

## Historical Development

### Evolution of Shell Theories
- **1814:** Germain's work on curved elastic surfaces
- **1888:** Love's extension of plate theory to curved surfaces
- **1910s:** Reissner's work on axisymmetric shells
- **1920s:** von Kármán and Tsien's contributions to nonlinear shell theory
- **1930s-40s:** Donnell, Mushtari, Vlasov, and Sanders developed simplified theories
- **1944:** Flügge's comprehensive shell theory
- **1950s:** Naghdi, Koiter's refined theories and stability analyses
- **1960s:** Development of finite elements for shells

## Geometric Foundations

### Surface Description

A shell is defined by its **mid-surface** and constant **thickness** h. The mid-surface is a two-dimensional manifold embedded in ℝ³, described parametrically:
$$
\mathbf{r}(\theta^1, \theta^2) = [x(\theta^1, \theta^2), y(\theta^1, \theta^2), z(\theta^1, \theta^2)]^T
$$
where θ¹, θ² are curvilinear coordinates (often called α, β or ξ, η).

### Fundamental Tensors

**First fundamental form (metric tensor):**
$$
a_{\alpha\beta} = \mathbf{r}_{,\alpha} \cdot \mathbf{r}_{,\beta}
$$
where $\mathbf{r}_{,\alpha} = \partial \mathbf{r}/\partial \theta^\alpha$

**Second fundamental form (curvature tensor):**
$$
b_{\alpha\beta} = \mathbf{n} \cdot \mathbf{r}_{,\alpha\beta} = -\mathbf{n}_{,\alpha} \cdot \mathbf{r}_{,\beta}
$$
where $\mathbf{n} = (\mathbf{r}_{,1} \times \mathbf{r}_{,2})/|\mathbf{r}_{,1} \times \mathbf{r}_{,2}|$ is the unit normal.

**Third fundamental form:**
$$
c_{\alpha\beta} = \mathbf{n}_{,\alpha} \cdot \mathbf{n}_{,\beta}
$$

### Principal Curvatures

The principal curvatures κ₁, κ₂ are eigenvalues of the mixed curvature tensor:
$$
b^\alpha_\beta = a^{\alpha\gamma} b_{\gamma\beta}
$$
The **Gaussian curvature** $K = \kappa_1 \kappa_2$ and **mean curvature** $H = (\kappa_1 + \kappa_2)/2$ classify surfaces:
- K > 0: Elliptic (dome-like)
- K = 0: Parabolic (cylindrical)
- K < 0: Hyperbolic (saddle-shaped)

## Classification of Shell Theories

### By Kinematic Assumptions

1. **Kirchhoff-Love Shell Theory:**
   - Extends Kirchhoff plate hypotheses to curved surfaces
   - Neglects transverse shear and normal strains
   - Requires C¹ continuity in finite element implementation

2. **Reissner-Mindlin Shell Theory (First-Order Shear Deformation):**
   - Includes transverse shear deformation
   - Maintains C⁰ continuity requirement
   - More suitable for moderately thick shells

3. **Higher-Order Shear Deformation Theories:**
   - Parabolic or higher-order through-thickness displacement expansion
   - Eliminates need for shear correction factors

### By Strain Magnitude

1. **Linear Shell Theory:** Small displacements and rotations
2. **Moderate Rotation Theory:** von Kármán-type assumptions
3. **Large Rotation/Finite Strain Theory:** Fully nonlinear kinematics

### By Complexity

1. **Membrane Theory:** Assumes no bending resistance (moment-free state)
2. **Bending Theory:** Includes bending but neglects membrane-bending coupling
3. **General Theory:** Full coupling between membrane and bending actions

## Kinematic Relations

### General [[Displacement Field]]

For a point at distance ζ from the mid-surface along the normal:
$$
\mathbf{u}(\theta^1, \theta^2, \zeta) = \mathbf{u}^0(\theta^1, \theta^2) + \zeta \boldsymbol{\phi}(\theta^1, \theta^2) + \zeta^2 \boldsymbol{\psi}(\theta^1, \theta^2) + \cdots
$$
where:
- $\mathbf{u}^0$ = mid-surface displacement
- $\boldsymbol{\phi}$ = rotation vector (first-order term)
- $\boldsymbol{\psi}$ = higher-order terms

### Kirchhoff-Love Kinematics

**Assumptions:**
1. Straight normals remain straight and normal to deformed mid-surface
2. Thickness unchanged
3. Transverse normal strain ε₃₃ = 0

**[[Displacement Field]]:**
$$
\mathbf{u}(\theta^1, \theta^2, \zeta) = \mathbf{u}^0(\theta^1, \theta^2) - \zeta [\mathbf{n} \cdot (\nabla \mathbf{u}^0)] \mathbf{n} + \zeta \mathbf{w}(\theta^1, \theta^2)
$$
where $\mathbf{w}$ accounts for thickness change.

### Reissner-Mindlin Kinematics

**[[Displacement Field]]:**
$$
\mathbf{u}(\theta^1, \theta^2, \zeta) = \mathbf{u}^0(\theta^1, \theta^2) + \zeta \boldsymbol{\phi}(\theta^1, \theta^2)
$$
where $\boldsymbol{\phi}$ are independent rotations, not necessarily equal to mid-surface slope.

## Strain Measures

### Green-Lagrange Strain Tensor

In curvilinear coordinates:
$$
E_{\alpha\beta} = \frac{1}{2}(u_{\alpha|\beta} + u_{\beta|\alpha} + u^\gamma_{|\alpha} u_{\gamma|\beta})
$$
where $|$ denotes covariant differentiation.

### Linearized Strain Components

**Membrane strains:**
$$
\varepsilon_{\alpha\beta} = \frac{1}{2}(u_{\alpha|\beta} + u_{\beta|\alpha}) - b_{\alpha\beta} w
$$

**Bending strains (changes in curvature):**
$$
\kappa_{\alpha\beta} = -\phi_{\alpha|\beta} - \phi_{\beta|\alpha} + c_{\alpha\beta} w + b^\gamma_\alpha \phi_{\gamma|\beta} + b^\gamma_\beta \phi_{\gamma|\alpha}
$$

**Transverse shear strains (for shear-deformable theories):**
$$
\gamma_\alpha = \phi_\alpha + w_{,\alpha} - b^\beta_\alpha u_\beta
$$

## Stress Resultants

### Force and Moment Definitions

**Membrane forces:**
$$
N^{\alpha\beta} = \int_{-h/2}^{h/2} \sigma^{\alpha\beta} (1 + \zeta \kappa_\gamma^\gamma) \, d\zeta
$$

**Bending moments:**
$$
M^{\alpha\beta} = \int_{-h/2}^{h/2} \sigma^{\alpha\beta} \zeta (1 + \zeta \kappa_\gamma^\gamma) \, d\zeta
$$

**Transverse shear forces:**
$$
Q^\alpha = \int_{-h/2}^{h/2} \sigma^{\alpha 3} (1 + \zeta \kappa_\gamma^\gamma) \, d\zeta
$$

## [[Constitutive Equations]]

### General Anisotropic Material

$$
\begin{bmatrix}
\mathbf{N} \\
\mathbf{M}
\end{bmatrix}
=
\begin{bmatrix}
\mathbf{A} & \mathbf{B} \\
\mathbf{B} & \mathbf{D}
\end{bmatrix}
\begin{bmatrix}
\boldsymbol{\varepsilon} \\
\boldsymbol{\kappa}
\end{bmatrix}
$$

where:
- $\mathbf{A}$ = extensional stiffness matrix
- $\mathbf{B}$ = extensional-bending coupling matrix
- $\mathbf{D}$ = bending stiffness matrix

**For [[isotropic material]]:**
$$
A^{\alpha\beta\gamma\delta} = \frac{Eh}{1-\nu^2} [a^{\alpha\gamma} a^{\beta\delta} + a^{\alpha\delta} a^{\beta\gamma} + \frac{2\nu}{1-\nu} a^{\alpha\beta} a^{\gamma\delta}]
$$
$$
D^{\alpha\beta\gamma\delta} = \frac{h^2}{12} A^{\alpha\beta\gamma\delta}
$$

**Transverse shear stiffness:**
$$
A_s^{\alpha\beta} = \kappa G h a^{\alpha\beta}
$$
with shear correction factor κ (typically 5/6).

## Governing Equations

### [[Equilibrium Equations]]

**Force equilibrium:**
$$
N^{\alpha\beta}_{|\alpha} - b^\alpha_\beta Q_\alpha + p^\beta = 0
$$
$$
Q^\alpha_{|\alpha} + b_{\alpha\beta} N^{\alpha\beta} + p^3 = 0
$$

**Moment equilibrium:**
$$
M^{\alpha\beta}_{|\alpha} - Q^\beta = 0
$$

### Combined Equations

For isotropic Kirchhoff-Love shells (Love's equations):
$$
D \nabla^4 w + \frac{Eh}{R^2} w = q - \frac{h}{R} \nabla^2 \Phi
$$
$$
\frac{1}{Eh} \nabla^4 \Phi + \frac{1}{R} \nabla^2 w = 0
$$
where Φ is the stress function and R is the radius of curvature.

## Special Shell Theories

### Membrane Theory
Assumes bending moments are negligible:
$$
N^{\alpha\beta}_{|\alpha} + p^\beta = 0
$$
$$
b_{\alpha\beta} N^{\alpha\beta} + p^3 = 0
$$
Only applicable when:
1. Shell is smoothly curved
2. Loads are smoothly distributed
3. Boundaries are free to move in normal direction

### Donnell-Mushtari-Vlasov Theory
For shallow shells (|w| ≪ R):
Simplifies curvature terms, valid when:
$$
\left(\frac{a}{R}\right)^2 \ll 1
$$
where a is characteristic planform dimension.

### Sanders-Koiter Theory
Consistently linearized theory with improved accuracy for thin shells, properly accounts for rotation about normal.

## Boundary Conditions

### Common Edge Conditions

1. **Clamped:**
   - Displacements: u = v = w = 0
   - Rotations: φ₁ = φ₂ = 0 (or ∂w/∂n = 0 for Kirchhoff)

2. **Simply Supported:**
   - Hard: uₜ = w = 0, Mₙ = 0
   - Soft: w = 0, Mₙ = 0, Nₙₜ = 0

3. **Free Edge:**
   - Nₙ = Nₙₜ = Mₙ = Mₙₜ = Qₙ = 0
   - For Kirchhoff: Mₙ = 0, Vₙ = Qₙ + ∂Mₙₜ/∂s = 0

4. **Symmetry/Antisymmetry:**
   - Appropriate combinations of zero displacements/rotations

## Analytical Solutions

### Methods of Solution

1. **Series Solutions:**
   - [[Fourier series]] for shells of rectangular planform
   - Trigonometric-hyperbolic functions for cylindrical shells

2. **Separation of Variables:**
   - For shells of revolution under axisymmetric loading

3. **Asymptotic Methods:**
   - Boundary layer theory for edge effects
   - Saint-Venant's principle for localized loads

4. **Complex Variable Methods:**
   - For shallow shells with complex boundary conditions

### Benchmark Solutions

1. **Cylindrical Shell:**
   - Donnell's equations for circular cylinders
   - Flügge's exact solution for bending

2. **Spherical Shell:**
   - Axisymmetric loading (Reissner-Meissner theory)
   - Point load solution (Reissner-Sagoci problem)

3. **Conical Shell:**
   - Bessel function solutions

## Stability Considerations

### Buckling Phenomena

1. **General Instability:**
   - Overall buckling of shell
   - Critical load highly sensitive to imperfections

2. **Local Buckling:**
   - Wrinkling or dimpling
   - Characteristic wavelength ~ √(Rh)

3. **Koiter's Imperfection Sensitivity Theory:**
   - Explains drastic reduction in buckling load
   - Post-buckling behavior classification

### Buckling Loads

**Cylindrical shell under axial [[compression]]:**
$$
P_{cr} = \frac{2\pi E h^2}{\sqrt{3(1-\nu^2)}} \quad \text{(classical)}
$$
Actual values are 20-60% lower due to imperfections.

**Spherical shell under external pressure:**
$$
p_{cr} = \frac{2E}{\sqrt{3(1-\nu^2)}} \left(\frac{h}{R}\right)^2
$$

## Finite Element Implementation

### Special Challenges

1. **Locking Phenomena:**
   - Membrane locking: Inextensional bending modes
   - Shear locking: Especially in thin shells
   - Curvature thickness locking: For very thick curved shells

2. **Continuity Requirements:**
   - Kirchhoff elements require C¹ continuity
   - Mindlin elements require C⁰ but suffer from locking

3. **Parametrization Issues:**
   - Choice of curvilinear coordinates
   - Singularities at poles of revolution

### Element Types

1. **Flat Shell Elements:**
   - Superposition of plate bending and membrane elements
   - Limited to small curvature

2. **Curved Shell Elements:**
   - Isoparametric formulation
   - Degenerated solid elements

3. **Discrete Kirchhoff Elements:**
   - Constrain shear strains to zero at discrete points

4. **Mixed/Enhanced Strain Elements:**
   - EAS, ANS methods to alleviate locking

## Applications

### Engineering Domains

1. **Aerospace:**
   - Aircraft fuselages, wings, rocket bodies
   - Reentry vehicle heat shields

2. **Civil Engineering:**
   - Domes, hyperbolic paraboloids, barrel vaults
   - Silos, tanks, pressure vessels

3. **Marine:**
   - Ship hulls, submarine pressure hulls
   - Offshore platform components

4. **Biomechanics:**
   - Skull, rib cage, arterial walls

5. **Micro/Nanosystems:**
   - MEMS membranes, CNT-based structures

## Advanced Topics

### Nonlinear Shell Theory

1. **Geometric Nonlinearity:**
   - Large rotations (finite rotation tensor)
   - Moderate rotation theory (von Kármán type)

2. **Material Nonlinearity:**
   - Plasticity, viscoelasticity, damage
   - Composite material failure criteria

3. **Contact and Impact:**
   - Shell-to-shell contact
   - Dynamic crushing

### Dynamics and Vibrations

1. **Free Vibration:**
   - Natural frequencies and mode shapes
   - Influence of curvature on spectra

2. **Wave Propagation:**
   - High-[[Frequency Response Function (FRF)]]
   - Dispersion relations

3. **Fluid-Structure Interaction:**
   - Shells conveying or immersed in fluid
   - Added mass effects

### Composite and Sandwich Shells

1. **Laminated Shells:**
   - Classical and shear deformation lamination theories
   - Layer-wise and zig-zag theories

2. **Functionally Graded Shells:**
   - Continuous property variation
   - Thermoelastic analysis

3. **Sandwich Shells:**
   - Soft core effects
   - Face sheet wrinkling

## See Also

- [[Plate Theory Fundamentals]]
- [[Kirchhoff-Love Shell Element]]
- [[Mindlin-Reissner Shell Element]]
- [[Curvilinear Coordinates in Continuum Mechanics]]
- Shell Buckling and Stability]]
- Finite Element Analysis of Shells]]
- Composite Shell Structures]]
- Nonlinear Shell Analysis]]
- [[Thin-Walled Structures]]
- Differential Geometry for Engineers]]
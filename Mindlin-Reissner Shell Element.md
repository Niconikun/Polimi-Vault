---
title: Mindlin-Reissner Shell Element
tags:
  - finite element analysis
  - structural mechanics
  - shell theory
  - numerical methods
---

# Mindlin-Reissner Shell Element

## Formal Definition

The **Mindlin-Reissner shell element** is a finite element formulation for analyzing thin to moderately thick shells, accounting for transverse shear deformation in addition to bending. Unlike Kirchhoff-Love shell theory (which assumes zero transverse shear strain), the Mindlin-Reissner theory allows shear strain, making it accurate for thicker shells and lower-order finite elements. The Mindlin-Reissner formulation is fundamental to [[Finite Element Analysis (FEA)]], structural analysis, aerospace shell buckling studies, and general stress analysis in [[Control Systems|structural control]] applications.

## Historical Development

### Key Milestones
- **1951:** Eric Reissner develops plate theory accounting for shear deformation
- **1951:** Raymond Mindlin independently publishes similar plate theory
- **1960s:** Extension to shell structures (Naghdi, Sanders)
- **1970s:** Finite element implementations (Kraus, Pawlik, Ahmad)
- **1980s–1990s:** Locking mitigation techniques; reduced integration
- **2000s–Present:** Layered composite shells; nonlinear dynamics

### Foundational Contributors
1. **Eric Reissner (1913–1996):** Plate theory with shear deformation
2. **Raymond D. Mindlin (1906–1987):** Independent plate theory development
3. **Pál Naghdi (1924–1994):** Shell theory generalization
4. **Suresh R. Narayanan:** Shell finite elements
5. **Magdi Mohareb:** Modern shell element implementations

## Mathematical Formulation

### Shell Geometry and Coordinate System

**Shell reference surface:** Mid-surface with curvature

**Coordinates:**
- $(x_1, x_2)$: Curvilinear surface coordinates
- $x_3$: Thickness direction (normal)
- $h$: Shell thickness

**Radius of curvature:** $R_1, R_2$ in principal directions

### Displacement Field (Mindlin-Reissner)

**Definition:**
$$
\mathbf{u}(\mathbf{x}) = u_1(x_1, x_2) - x_3 \theta_1(x_1, x_2)
$$
$$
\mathbf{v}(\mathbf{x}) = u_2(x_1, x_2) - x_3 \theta_2(x_1, x_2)
$$
$$
\mathbf{w}(\mathbf{x}) = w(x_1, x_2)
$$

Where:
- $u_1, u_2$: In-plane displacements (reference surface)
- $w$: Transverse (normal) displacement
- $\theta_1, \theta_2$: Rotations about axes 2 and 1
- **Key assumption:** Rotation angles independent of $x_3$ (constant through thickness)

### Strain Components

**In-plane strains:**
$$
\varepsilon_1 = \frac{\partial u_1}{\partial x_1} + \frac{u_2}{R_1} - x_3 \frac{\partial \theta_1}{\partial x_1}
$$

**Transverse shear strains** (non-zero in Mindlin theory):
$$
\gamma_{13} = \frac{\partial w}{\partial x_1} - \theta_1 + \frac{u_1}{R_1}
$$
$$
\gamma_{23} = \frac{\partial w}{\partial x_2} - \theta_2 + \frac{u_2}{R_2}
$$

**Thick plate limit:** Shear strains significant

**Thin shell limit:** Shear strains → 0 (recovers Kirchhoff-Love theory)

### Stress-Strain Relationship

**Constitutive law (isotropic material):**
$$
\begin{pmatrix} \sigma_1 \\ \sigma_2 \\ \tau_{12} \end{pmatrix} = \frac{E}{1-\nu^2} \begin{pmatrix} 1 & \nu & 0 \\ \nu & 1 & 0 \\ 0 & 0 & (1-\nu)/2 \end{pmatrix} \begin{pmatrix} \varepsilon_1 \\ \varepsilon_2 \\ \gamma_{12} \end{pmatrix}
$$

**Transverse shear:**
$$
\tau_{13} = G \gamma_{13}, \quad \tau_{23} = G \gamma_{23}
$$

Where $G = E/(2(1+\nu))$ is shear modulus; correction factor $\kappa$ often applied (shear locking mitigation).

## Finite Element Discretization

### Element Degrees of Freedom

**Per node (typically 5 DOF):**
- 2 in-plane displacements: $u_1, u_2$
- 1 transverse displacement: $w$
- 2 rotations: $\theta_1, \theta_2$

**Total element DOF:** $5 \times \text{(number of nodes)}$

### Shape Functions

**Displacement interpolation:**
$$
u_1 = \sum_i N_i(\xi, \eta) u_{1,i}, \quad w = \sum_i N_i(\xi, \eta) w_i, \quad \theta_1 = \sum_i N_i(\xi, \eta) \theta_{1,i}
$$

Where $N_i$ are standard Lagrange shape functions in parent element coordinates $(\xi, \eta)$.

**Common elements:**
- **Bilinear (Q4):** 4 nodes, 20 DOF; prone to shear locking
- **Biquadratic (Q8/Q9):** 8–9 nodes, 40–45 DOF; improved accuracy
- **Triangular (T3/T6):** 3–6 nodes; mesh flexibility

### Strain-Displacement Matrix

**Strain vector:**
$$
\boldsymbol{\varepsilon} = \mathbf{B} \mathbf{d}
$$

Where $\mathbf{d}$ is nodal displacement vector; $\mathbf{B}$ contains derivatives of shape functions.

**Components:**
$$
\mathbf{B} = \begin{pmatrix} \mathbf{B}_m \\ \mathbf{B}_b \\ \mathbf{B}_s \end{pmatrix}
$$

- $\mathbf{B}_m$: Membrane (in-plane) strains
- $\mathbf{B}_b$: Bending strains
- $\mathbf{B}_s$: Transverse shear strains

## Stiffness Matrix and Assembly

### Element Stiffness Matrix

**Definition:**
$$
\mathbf{K}^e = \int_V \mathbf{B}^T \mathbf{D} \mathbf{B} \, dV
$$

Where $\mathbf{D}$ is constitutive matrix; integration over element volume.

**Numerical integration (Gauss quadrature):**

Typically 2×2 or 3×3 Gauss points for bilinear shells.

### Global Stiffness Assembly

**Standard FEA procedure:**
$$
\mathbf{K} = \bigcup_e \mathbf{K}^e
$$

Direct assembly at shared nodes.

### System Equations

**Static case:**
$$
\mathbf{K} \mathbf{d} = \mathbf{f}
$$

**Dynamic case:**
$$
\mathbf{M}\ddot{\mathbf{d}} + \mathbf{C}\dot{\mathbf{d}} + \mathbf{K}\mathbf{d} = \mathbf{f}(t)
$$

Where $\mathbf{M}$ is [[Mass Matrix|mass matrix]], $\mathbf{C}$ is damping.

## Locking Phenomena and Remedies

### Shear Locking

**Problem:** Bilinear elements underestimate flexibility; overpredicts stiffness

**Physical cause:** Shear strain term $\gamma_{13} = \partial w/\partial x_1 - \theta_1$ → 0 in thin limit, incompatible with displacement field

**Result:** Nonphysical stiffening as thickness → 0; poor accuracy for thin shells

### Membrane Locking

**Problem:** In-plane strains over-constrained by element geometry

**Occurs:** Highly curved surfaces with low-order elements

### Remedies

**1. Reduced Integration:**
- Use fewer Gauss points for shear terms (selective reduced integration)
- Example: 1-point integration for shear, full integration for bending

**2. Assumed Strain Methods:**
- Independently assume shear strain field; not derived from displacement interpolation
- Example: Assumed Natural Strain (ANS) formulation (Bathe-Dvorkin)

**3. Mixed Formulation:**
- Include shear strain as independent variable
- Increases DOF but eliminates locking

**4. Thick Elements:**
- Use multilayered elements for thick shells; less susceptible to locking

## Applications in Structural Analysis

### Shell Buckling Analysis

**Eigenvalue problem:**
$$
(\mathbf{K} + \lambda_i \mathbf{K}_{\text{geom}}) \boldsymbol{\phi}_i = 0
$$

Where $\mathbf{K}_{\text{geom}}$ is geometric stiffness from membrane stress state.

**Application:** Pressure vessel buckling, spacecraft shell buckling, composite panels

### Dynamic Response (Natural Frequencies)

**Eigenvalue problem:**
$$
(\mathbf{K} - \omega_n^2 \mathbf{M}) \boldsymbol{\phi}_n = 0
$$

**Solutions:** Natural frequencies $\omega_n$, mode shapes $\boldsymbol{\phi}_n$

**Application:** [[Vibration Analysis|vibration control]], seismic design, modal damping

### Stress Analysis Under Complex Loading

**Combined loadings:**
- External pressure (uniform, concentrated)
- Temperature gradients (thermal stresses)
- Dynamic loads (impact, vibration)

**Output:** Stress distribution, principal stresses, failure indices (Von Mises)

## Composite and Layered Shells

### Laminated Shell Theory

**Extension to composite materials:**

Each layer has orientation-dependent stiffness; through-thickness variation.

**Laminate stiffness matrix:**
$$
[\mathbf{A}, \mathbf{B}, \mathbf{D}] = \int_0^h [\mathbf{Q}(\theta), \mathbf{Q}(\theta)x_3, \mathbf{Q}(\theta)x_3^2] \, dx_3
$$

Where $\mathbf{Q}(\theta)$ is rotated material stiffness matrix for ply at angle $\theta$.

### Failure Criteria

**Tsai-Hill criterion:**
$$
\frac{\sigma_1^2}{X^2} + \frac{\sigma_2^2}{Y^2} - \frac{\sigma_1\sigma_2}{X^2} + \frac{\tau_{12}^2}{S^2} = 1
$$

Where $X, Y, S$ are strength values; predicts failure envelope.

**Progressive ply failure:** Degrade stiffness of failed plies; continue analysis.

## Nonlinear Analysis

### Geometric Nonlinearity

**Large displacement effects:**
$$
\mathbf{K}_{\text{total}} = \mathbf{K} + \mathbf{K}_{\text{geom}}(\mathbf{d})
$$

**Nonlinear solution:** Newton-Raphson iteration

**Application:** Snap-through, post-buckling behavior

### Material Nonlinearity

**Plasticity, damage:** Constitutive law nonlinear

**Integration:** Updated Lagrangian or Total Lagrangian formulation

## Computational Implementation

### Finite Element Software

**Common implementations:**
- **ANSYS:** SHELL181, SHELL281 elements
- **ABAQUS:** S4, S9R5 shell elements
- **COMSOL:** Shell interface physics
- **Open-source:** Code_Aster, Elmer

### Preprocessing

1. **CAD import:** Geometry import/cleanup
2. **Meshing:** Shell surface mesh generation; quad/triangular options
3. **Material definition:** Isotropic/orthotropic properties
4. **Boundary conditions:** Fixed supports, symmetry, periodic

### Postprocessing

**Results visualization:**
- Deformed shape (with scaling)
- Stress contours (Von Mises, principal)
- Displacement vectors
- Mode shape animations
- Frequency response functions (FRF)

## Comparison with Other Shell Elements

| Element Type | Shear Deformation | Thickness | Computational Cost | Accuracy |
|---|---|---|---|---|
| Kirchhoff-Love | No | Thin only | Low | Good (thin) |
| Mindlin-Reissner | Yes | Thin–Moderate | Medium | Excellent |
| 3D Solid Elements | Yes | Any | High | Excellent |
| SHELL181 (ANSYS) | Yes | Thin–Thick | Medium | Excellent |

## Connection to Other Concepts

1. **Connection to [[Finite Element Analysis (FEA)]]:**
   - Fundamental element type in structural FEA
   - Standard in commercial software

2. **Connection to [[Vibration Analysis]]:**
   - Natural frequency and damping analysis
   - [[Modal Damping]] application

3. **Connection to [[Stress Tensor]]:**
   - Stress distribution from finite element solution

4. **Connection to [[Structural Mechanics]]:**
   - Bending, membrane, and shear coupling

5. **Connection to [[Control Systems]]:**
   - Basis for structural control design
   - Modal models for control

## Advanced Topics

### Thickness Stretching

**Transverse normal stress** $\sigma_3$ (typically neglected):

For very thick shells or composite laminates, may require inclusion.

**Enhanced formulation:** Include transverse normal strain as additional variable.

### Dynamic Analysis with Damping

**Proportional damping (Rayleigh):**
$$
\mathbf{C} = \alpha \mathbf{M} + \beta \mathbf{K}
$$

**Modal damping:** Specify damping ratio per mode (realistic for composite shells).

### Adaptive Mesh Refinement

**Error estimation:** Estimate error in stress concentration regions

**Refinement:** Automatically refine mesh; re-solve; iterate until convergence

**Application:** Stress singularities, sharp geometry changes

## See Also

- [[Finite Element Analysis (FEA)]]
- [[Shell Theory]]
- [[Kirchhoff-Love Shell]]
- [[Vibration Analysis]]
- [[Modal Damping]]
- [[Stress Tensor]]
- [[Structural Mechanics]]
- [[Composite Materials]]
- [[Numerical Methods]]

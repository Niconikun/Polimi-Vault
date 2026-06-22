# Saint-Venant [[Compatibility Equations]]

## Formal Definition

The **Saint-Venant [[Compatibility Equations]]** are a set of six independent second-order partial differential equations that must be satisfied by a linear strain tensor field in order for it to be derivable from a single-valued, continuous [[Displacement Field]] in a simply connected three-dimensional body. Named after the French mathematician and mechanician **Adhémar Jean Claude Barré de Saint-Venant** (1797-1886), these equations ensure that when a strain field is integrated to obtain displacements, the resulting [[Displacement Field]] is physically admissible—free from gaps, overlaps, or discontinuities.

## Mathematical Formulation

### Tensor Notation

In modern [[Continuum Mechanics]] notation, the compatibility condition can be expressed compactly as:

$$
\nabla \times (\nabla \times \boldsymbol{\varepsilon})^T = \mathbf{0}
$$

where:
- $\boldsymbol{\varepsilon}$ is the infinitesimal strain tensor
- $\nabla \times$ denotes the curl operator
- $(\cdot)^T$ denotes the transpose
- $\mathbf{0}$ is the zero tensor

### Index Notation with [[Levi-Civita Symbol]]

Using index notation and the Levi-Civita permutation symbol $\epsilon_{ijk}$, the [[Compatibility Equations]] become:

$$
\epsilon_{ikl} \epsilon_{jmn} \frac{\partial^2 \varepsilon_{ln}}{\partial x_k \partial x_m} = 0
$$

where:
- $i,j,k,l,m,n$ range from 1 to 3
- $\varepsilon_{ln}$ are the components of the strain tensor
- $x_k$ denote Cartesian coordinates

### Expanded Form in Cartesian Coordinates

In three-dimensional Cartesian coordinates $(x, y, z)$, the six independent Saint-Venant [[Compatibility Equations]] are:

1. **In-plane normal-shear relation:**
   $$
   \frac{\partial^2 \varepsilon_{xx}}{\partial y^2} + \frac{\partial^2 \varepsilon_{yy}}{\partial x^2} = 2\frac{\partial^2 \varepsilon_{xy}}{\partial x \partial y}
   $$

2. **Out-of-plane normal-shear relation (y-z plane):**
   $$
   \frac{\partial^2 \varepsilon_{yy}}{\partial z^2} + \frac{\partial^2 \varepsilon_{zz}}{\partial y^2} = 2\frac{\partial^2 \varepsilon_{yz}}{\partial y \partial z}
   $$

3. **Out-of-plane normal-shear relation (z-x plane):**
   $$
   \frac{\partial^2 \varepsilon_{zz}}{\partial x^2} + \frac{\partial^2 \varepsilon_{xx}}{\partial z^2} = 2\frac{\partial^2 \varepsilon_{zx}}{\partial z \partial x}
   $$

4. **Mixed derivative relation (x-component):**
   $$
   \frac{\partial}{\partial x} \left( -\frac{\partial \varepsilon_{yz}}{\partial x} + \frac{\partial \varepsilon_{zx}}{\partial y} + \frac{\partial \varepsilon_{xy}}{\partial z} \right) = \frac{\partial^2 \varepsilon_{xx}}{\partial y \partial z}
   $$

5. **Mixed derivative relation (y-component):**
   $$
   \frac{\partial}{\partial y} \left( \frac{\partial \varepsilon_{yz}}{\partial x} - \frac{\partial \varepsilon_{zx}}{\partial y} + \frac{\partial \varepsilon_{xy}}{\partial z} \right) = \frac{\partial^2 \varepsilon_{yy}}{\partial z \partial x}
   $$

6. **Mixed derivative relation (z-component):**
   $$
   \frac{\partial}{\partial z} \left( \frac{\partial \varepsilon_{yz}}{\partial x} + \frac{\partial \varepsilon_{zx}}{\partial y} - \frac{\partial \varepsilon_{xy}}{\partial z} \right) = \frac{\partial^2 \varepsilon_{zz}}{\partial x \partial y}
   $$

## Physical Interpretation

### Geometric Necessity

The [[Compatibility Equations]] arise from the fact that six strain components are derived from only three displacement components. If arbitrary functions are chosen for the six strain components, they will generally not correspond to a physically possible deformation. The equations ensure that the strain field can be "integrated" to yield a continuous [[Displacement Field]] without inconsistencies.

### Simply vs. Multiply Connected Domains

- **Simply connected domains:** The Saint-Venant equations are both necessary and sufficient for the existence of a single-valued [[Displacement Field]].
- **Multiply connected domains:** Additional conditions (cyclic integrals around holes) are required beyond the Saint-Venant equations to ensure single-valued displacements.

### Relationship to Defects

When the [[Compatibility Equations]] are not satisfied, the strain field is **incompatible**, indicating the presence of defects:

- **Dislocations:** Line defects where the [[Displacement Field]] is multi-valued
- **Disclinations:** Rotational defects
- **Point defects:** Vacancies or interstitials that cause lattice distortion

The **incompatibility tensor** $\boldsymbol{\eta}$ is defined as:
$$
\boldsymbol{\eta} = \nabla \times (\nabla \times \boldsymbol{\varepsilon})^T
$$
and is directly related to the density of geometrically necessary dislocations.

## Special Cases

### Two-Dimensional Problems

For **plane strain** ($\varepsilon_{zz} = \varepsilon_{xz} = \varepsilon_{yz} = 0$, all strains independent of $z$), the only non-trivial compatibility equation reduces to:

$$
\frac{\partial^2 \varepsilon_{xx}}{\partial y^2} + \frac{\partial^2 \varepsilon_{yy}}{\partial x^2} = 2\frac{\partial^2 \varepsilon_{xy}}{\partial x \partial y}
$$

For isotropic linear elasticity, this can be expressed in terms of stresses or the Airy stress function.

### Airy Stress Function Formulation

In two-dimensional linear elasticity with no body forces, introducing the **Airy stress function** $\Phi(x,y)$ such that:

$$
\sigma_{xx} = \frac{\partial^2 \Phi}{\partial y^2}, \quad \sigma_{yy} = \frac{\partial^2 \Phi}{\partial x^2}, \quad \sigma_{xy} = -\frac{\partial^2 \Phi}{\partial x \partial y}
$$

the compatibility equation becomes the **biharmonic equation**:

$$
\nabla^4 \Phi = \frac{\partial^4 \Phi}{\partial x^4} + 2\frac{\partial^4 \Phi}{\partial x^2 \partial y^2} + \frac{\partial^4 \Phi}{\partial y^4} = 0
$$

### Beltrami-Michell Equations

Combining the [[Compatibility Equations]] with the [[Equilibrium Equations]] and constitutive relations yields the **Beltrami-Michell equations**—a set of equations expressed entirely in terms of stresses:

For isotropic linear elasticity:
$$
\nabla^2 \sigma_{ij} + \frac{1}{1+\nu} \frac{\partial^2 \sigma_{kk}}{\partial x_i \partial x_j} + \frac{\nu}{1-\nu} \delta_{ij} \nabla \cdot \mathbf{b} + \left( \frac{\partial b_i}{\partial x_j} + \frac{\partial b_j}{\partial x_i} \right) = 0
$$

where $\mathbf{b}$ are body forces, $\nu$ is [[Poisson's ratio]], and $\delta_{ij}$ is the [[Kronecker delta]].

## Applications

### Analytical Elasticity

1. **Solution of elasticity problems:** The [[Compatibility Equations]], together with equilibrium and constitutive relations, form a complete system for solving [[Boundary Value Problems]] in linear elasticity.

2. **Stress function methods:** In two dimensions, the Airy stress function approach reduces the problem to solving the biharmonic equation.

3. **[[Torsion]] of prismatic bars:** Using the Prandtl stress function, the compatibility condition leads to Poisson's equation for the stress function.

### Experimental Mechanics

1. **Strain field validation:** In techniques like digital image correlation (DIC) or moiré interferometry, measured strain fields are checked for compatibility to validate measurements and detect errors.

2. **Defect detection:** Incompatibility in measured strain fields can indicate the presence of defects or damage in materials.

### Computational Mechanics

1. **[[Finite Element Analysis (FEA)]]:**
   - **Displacement-based FEM:** Compatibility is automatically satisfied as strains are derived from continuous displacement fields.
   - **Mixed/hybrid FEM:** Compatibility conditions may need to be enforced explicitly through constraints or special element formulations.
   - **Stress-based FEM:** The [[Compatibility Equations]] are used to formulate the finite element equations.

2. **Error estimation:** Compatibility conditions are used in a posteriori error estimation for finite element solutions.

## Theoretical Foundations

### Differential Geometry Interpretation

In the language of differential geometry, the [[Compatibility Equations]] express the condition that the Riemann-Christoffel curvature tensor formed from the strain tensor vanishes. For a simply connected body, this ensures that the strain field corresponds to a deformation of a Euclidean body without intrinsic curvature.

### Mathematical Rigor

The existence of a [[Displacement Field]] given a compatible strain field is guaranteed by the **Cesàro-Volterra formula**:

$$
u_i(\mathbf{x}) = u_i(\mathbf{x}_0) + \omega_{ij}(\mathbf{x}_0)(x_j - x_{0j}) + \int_{\mathbf{x}_0}^{\mathbf{x}} \varepsilon_{ij}(\mathbf{x}') \, dx'_j
$$

where $\omega_{ij}$ is the rotation tensor. The path independence of this integral requires the compatibility conditions.

## Limitations and Extensions

### Finite Deformations

For finite deformations, the compatibility conditions become more complex. They involve the requirement that the Riemann curvature tensor computed from the metric tensor (right Cauchy-Green tensor) vanishes:

$$
R_{ijkl} = 0
$$

where $R_{ijkl}$ is the Riemann curvature tensor with components derived from the metric $g_{ij} = \delta_{ij} + 2\varepsilon_{ij}$ in the linearized case.

### Incompatible Elasticity

Modern theories of defects relax the compatibility conditions:

1. **Dislocation theory:** The incompatibility tensor is proportional to the dislocation density tensor.
2. **Strain-gradient elasticity:** Higher-order gradients of strain are included, modifying the compatibility conditions.
3. **Geometrically necessary dislocations:** The incompatibility tensor quantifies the density of dislocations required to accommodate curvature in the crystal lattice.

### Multiply Connected Domains

For bodies with holes, the Saint-Venant equations are necessary but not sufficient. Additional conditions must be imposed:

$$
\oint_C \left( \varepsilon_{ij} - \frac{1}{2} \epsilon_{ijk} \omega_k x_l \right) dx_j = 0
$$

for all closed curves $C$ encircling holes, where $\omega_k$ are [[Rigid Body]] rotations.

## Historical Context

### Saint-Venant's Contribution

Adhémar Jean Claude Barré de Saint-Venant first derived these equations in 1864 while working on the [[torsion]] of prismatic bars. His work extended Cauchy's theory of elasticity and provided a rigorous foundation for stress-based formulations.

### Related Developments

- **Beltrami (1892):** Derived the stress [[Compatibility Equations]] for isotropic elasticity.
- **Michell (1900):** Extended Beltrami's work to include body forces.
- **Love (1927):** Presented the equations in their modern tensor form.

## See Also

- [[Compatibility Equations]]
- [[Beltrami-Michell Equations]]
- [[Airy Stress Function]]
- [[Strain-Displacement Relations]]
- [[Linear Elasticity Theory]]
- [[Incompatibility Tensor]]
- [[Finite Element Method]]
- [[Continuum Mechanics]]
- [[Differential Geometry in Mechanics]]
- [[Dislocation Theory]]
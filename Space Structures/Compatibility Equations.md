## Formal Definition

**Compatibility Equations** are a set of differential conditions that ensure the existence of a single-valued, continuous [[Displacement Field]] for a given strain field in a continuum body. These equations guarantee that when a strain field is integrated to obtain displacements, the resulting [[Displacement Field]] is physically admissible—meaning it does not lead to gaps, overlaps, or discontinuities in the material. In essence, they are the integrability conditions for the [[Strain-Displacement Relations]].

## Mathematical Formulation

### [[Strain-Displacement Relations]]

For small deformation theory, the linear strain tensor is defined as:

$$
\boldsymbol{\varepsilon} = \frac{1}{2}(\nabla \mathbf{u} + (\nabla \mathbf{u})^T)
$$

or in component form (in Cartesian coordinates):

$$
\varepsilon_{ij} = \frac{1}{2}\left( \frac{\partial u_i}{\partial x_j} + \frac{\partial u_j}{\partial x_i} \right)
$$

Given a [[Displacement Field]] $\mathbf{u}$, the strains are uniquely determined. However, the inverse problem—finding displacements from strains—requires that the strain field satisfies certain conditions to ensure a single-valued continuous [[Displacement Field]].

### Compatibility Conditions for Linear Elasticity

For a simply connected region, the compatibility equations are given by the **[[Saint-Venant Compatibility Equations]]** (in [[tensor]] notation):

$$
\nabla \times (\nabla \times \boldsymbol{\varepsilon})^T = \mathbf{0}
$$

or equivalently,

$$
\varepsilon_{ik,jl} + \varepsilon_{jl,ik} - \varepsilon_{il,jk} - \varepsilon_{jk,il} = 0
$$

where indices after a comma denote partial differentiation.

In three dimensions, these represent 81 equations, but due to symmetries only 6 are independent. In engineering notation, for Cartesian coordinates $(x, y, z)$, the six independent compatibility equations are:

1. $$
   \frac{\partial^2 \varepsilon_{xx}}{\partial y^2} + \frac{\partial^2 \varepsilon_{yy}}{\partial x^2} = 2 \frac{\partial^2 \varepsilon_{xy}}{\partial x \partial y}
   $$

2. $$
   \frac{\partial^2 \varepsilon_{yy}}{\partial z^2} + \frac{\partial^2 \varepsilon_{zz}}{\partial y^2} = 2 \frac{\partial^2 \varepsilon_{yz}}{\partial y \partial z}
   $$

3. $$
   \frac{\partial^2 \varepsilon_{zz}}{\partial x^2} + \frac{\partial^2 \varepsilon_{xx}}{\partial z^2} = 2 \frac{\partial^2 \varepsilon_{zx}}{\partial z \partial x}
   $$

4. $$
   \frac{\partial}{\partial x} \left( -\frac{\partial \varepsilon_{yz}}{\partial x} + \frac{\partial \varepsilon_{zx}}{\partial y} + \frac{\partial \varepsilon_{xy}}{\partial z} \right) = \frac{\partial^2 \varepsilon_{xx}}{\partial y \partial z}
   $$

5. $$
   \frac{\partial}{\partial y} \left( \frac{\partial \varepsilon_{yz}}{\partial x} - \frac{\partial \varepsilon_{zx}}{\partial y} + \frac{\partial \varepsilon_{xy}}{\partial z} \right) = \frac{\partial^2 \varepsilon_{yy}}{\partial z \partial x}
   $$

6. $$
   \frac{\partial}{\partial z} \left( \frac{\partial \varepsilon_{yz}}{\partial x} + \frac{\partial \varepsilon_{zx}}{\partial y} - \frac{\partial \varepsilon_{xy}}{\partial z} \right) = \frac{\partial^2 \varepsilon_{zz}}{\partial x \partial y}
   $$

### Two-Dimensional Case (Plane Strain)

For plane strain ($\varepsilon_{zz} = \varepsilon_{xz} = \varepsilon_{yz} = 0$ and all strains independent of $z$), the only non-trivial compatibility equation reduces to:

$$
\frac{\partial^2 \varepsilon_{xx}}{\partial y^2} + \frac{\partial^2 \varepsilon_{yy}}{\partial x^2} = 2 \frac{\partial^2 \varepsilon_{xy}}{\partial x \partial y}
$$

This is often written in terms of the Airy stress function $\Phi$ for isotropic linear elasticity, where the compatibility equation becomes the biharmonic equation:

$$
\nabla^4 \Phi = 0
$$

## Physical Interpretation

### Geometric Necessity

The compatibility conditions arise because the strain components are not independent; they are derived from only three displacement components. If arbitrary functions are chosen for the six strain components, they will generally not correspond to a valid [[Displacement Field]]. The compatibility equations are the conditions that allow the strain field to be "integrated" to yield a continuous [[Displacement Field]].

### Analogy with Differential Geometry

In differential geometry, the compatibility equations are analogous to the condition that the Riemann curvature tensor vanishes (i.e., the body is simply connected and without defects). When the compatibility equations are not satisfied, the body contains defects such as dislocations or disclinations.

## Relationship with Other Concepts

### Simply vs. Multiply Connected Domains

- **Simply connected domains:** The [[Saint-Venant Compatibility Equations]] are both necessary and sufficient for the existence of a single-valued [[Displacement Field]].
- **Multiply connected domains:** Additional conditions (cyclic integrals) are required to ensure single-valued displacements around holes or inclusions.

### Incompatibility and Defects

When the compatibility equations are not satisfied, the incompatibility tensor $\boldsymbol{\eta}$ is defined as:

$$
\boldsymbol{\eta} = \nabla \times (\nabla \times \boldsymbol{\varepsilon})^T
$$

This tensor is related to the density of geometrically necessary dislocations in crystal plasticity.

## Applications

### Linear Elasticity

In stress-based formulations of elasticity, the compatibility equations are used in conjunction with the [[Equilibrium Equations]] and constitutive relations to solve [[Boundary Value Problems]]. For example, in the Beltrami-Michell equations, the compatibility conditions are expressed in terms of stresses.

### Experimental Mechanics

In strain measurement techniques (e.g., digital image correlation, moiré interferometry), the measured strain fields must be checked for compatibility to ensure [[consistency]] and to detect measurement errors.

### [[Finite Element Analysis (FEA)]]

In displacement-based finite element methods, the compatibility conditions are automatically satisfied because the [[Displacement Field]] is assumed to be continuous and is used to compute strains. However, in mixed or stress-based finite element formulations, the compatibility conditions may need to be enforced explicitly.

### Plasticity and Damage

In plasticity, the total strain is decomposed into elastic and plastic parts. The compatibility condition applies to the total strain, but the plastic strain may be incompatible, leading to residual stresses and distortion.

## Special Cases and Extensions

### Finite Deformation Compatibility

For finite deformations, the compatibility conditions become more complex. The condition for the existence of a deformation map $\boldsymbol{\phi}$ such that the deformation gradient $\mathbf{F} = \nabla \boldsymbol{\phi}$ is given by the vanishing of the Riemann-Christoffel curvature tensor formed from the metric tensor (the right Cauchy-Green tensor $\mathbf{C} = \mathbf{F}^T\mathbf{F}$). In components:

$$
R_{ijkl} = 0
$$

where $R_{ijkl}$ is the Riemann curvature tensor computed from the metric $C_{ij}$.

### Incompatible Elasticity

In some theories (e.g., strain-gradient elasticity, theories of dislocations), the compatibility conditions are relaxed to allow for defects. The incompatibility tensor then becomes a fundamental field describing the defect density.

## Solution Techniques

### Direct Integration

In some simple cases, displacements can be obtained by directly integrating the [[Strain-Displacement Relations]]. The compatibility conditions ensure that the integration path does not affect the result.

### Stress Functions

In two-dimensional linear elasticity, the Airy stress function automatically satisfies the [[Equilibrium Equations]], and the compatibility condition leads to the biharmonic equation, which can be solved using various analytical or numerical methods.

### Numerical Methods

In computational mechanics, the compatibility conditions are often enforced weakly or through the choice of appropriate function spaces. For example, in mixed finite element methods, careful selection of strain and displacement spaces ensures that the discrete compatibility conditions are satisfied.

## Limitations and Considerations

### Material Nonlinearity

For nonlinear material behavior, the compatibility equations still apply to the total strain, but the decomposition into elastic and inelastic parts may require additional considerations.

### Geometric Nonlinearity

For large deformations, the compatibility conditions must be expressed in terms of appropriate strain measures and may involve the curvature of the deformed configuration.

### Multiply Connected Domains

In domains with holes, additional conditions (such as the Cesàro integrals) are required to ensure single-valued displacements.

## See Also

- [[Strain-Displacement Relations]]
- [[Saint-Venant Compatibility Equations]]
- [[Airy Stress Function]]
- [[Beltrami-Michell Equations]]
- [[Finite Element Method]]
- [[Continuum Mechanics]]
- [[Elasticity Theory]]
- [[Dislocation Theory]]
- [[Differential Geometry in Mechanics]]
- [[Residual Stresses]]
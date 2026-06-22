## Formal Definition

**Strain-Displacement Relations** are a set of kinematic equations that express the strain tensor components in terms of spatial derivatives of the [[Displacement Field]]. These fundamental relations in [[Continuum Mechanics]] bridge the kinematic description of deformation (displacements) with the measure of deformation (strain), providing the mathematical framework to compute strains from known displacements or, conversely, to determine the integrability conditions for obtaining displacements from strains.

## Mathematical Formulation

### Infinitesimal (Linear) Strain Theory

For small deformations where displacement gradients are much less than unity ($|\nabla \mathbf{u}| \ll 1$), the linearized strain-displacement relations are:

#### Tensor Form
$$
\boldsymbol{\varepsilon} = \frac{1}{2}(\nabla \mathbf{u} + (\nabla \mathbf{u})^T)
$$

where:
- $\boldsymbol{\varepsilon}$ is the infinitesimal (Cauchy) strain tensor (symmetric second-order tensor)
- $\mathbf{u}$ is the displacement vector field
- $\nabla \mathbf{u}$ is the displacement gradient tensor
- $(\cdot)^T$ denotes the transpose

#### Component Form in Cartesian Coordinates

In Cartesian coordinates $(x, y, z)$ with displacement components $u, v, w$:

**Normal strains:**
$$
\begin{aligned}
\varepsilon_{xx} &= \frac{\partial u}{\partial x} \\
\varepsilon_{yy} &= \frac{\partial v}{\partial y} \\
\varepsilon_{zz} &= \frac{\partial w}{\partial z}
\end{aligned}
$$

**Shear strains (tensor components):**
$$
\begin{aligned}
\varepsilon_{xy} &= \frac{1}{2}\left( \frac{\partial u}{\partial y} + \frac{\partial v}{\partial x} \right) \\
\varepsilon_{yz} &= \frac{1}{2}\left( \frac{\partial v}{\partial z} + \frac{\partial w}{\partial y} \right) \\
\varepsilon_{zx} &= \frac{1}{2}\left( \frac{\partial w}{\partial x} + \frac{\partial u}{\partial z} \right)
\end{aligned}
$$

**Engineering shear strains:**
$$
\begin{aligned}
\gamma_{xy} &= 2\varepsilon_{xy} = \frac{\partial u}{\partial y} + \frac{\partial v}{\partial x} \\
\gamma_{yz} &= 2\varepsilon_{yz} = \frac{\partial v}{\partial z} + \frac{\partial w}{\partial y} \\
\gamma_{zx} &= 2\varepsilon_{zx} = \frac{\partial w}{\partial x} + \frac{\partial u}{\partial z}
\end{aligned}
$$

### Finite Strain Theory

For large deformations, several strain measures are used, each with different strain-displacement relations:

#### Deformation Gradient
$$
\mathbf{F} = \mathbf{I} + \nabla \mathbf{u} = \frac{\partial \mathbf{x}}{\partial \mathbf{X}}
$$
where $\mathbf{x} = \mathbf{X} + \mathbf{u}$ is the current position, $\mathbf{X}$ is the reference position.

#### Green-Lagrange Strain Tensor
$$
\mathbf{E} = \frac{1}{2}(\mathbf{F}^T\mathbf{F} - \mathbf{I}) = \frac{1}{2}(\nabla \mathbf{u} + (\nabla \mathbf{u})^T + (\nabla \mathbf{u})^T \nabla \mathbf{u})
$$

In component form:
$$
E_{ij} = \frac{1}{2}\left( \frac{\partial u_i}{\partial X_j} + \frac{\partial u_j}{\partial X_i} + \frac{\partial u_k}{\partial X_i} \frac{\partial u_k}{\partial X_j} \right)
$$

#### Almansi-Euler Strain Tensor
$$
\mathbf{e} = \frac{1}{2}(\mathbf{I} - \mathbf{F}^{-T}\mathbf{F}^{-1})
$$

## Special Coordinate Systems

### Cylindrical Coordinates $(r, \theta, z)$

With displacements $(u_r, u_\theta, u_z)$:

$$
\begin{aligned}
\varepsilon_{rr} &= \frac{\partial u_r}{\partial r} \\
\varepsilon_{\theta\theta} &= \frac{1}{r}\frac{\partial u_\theta}{\partial \theta} + \frac{u_r}{r} \\
\varepsilon_{zz} &= \frac{\partial u_z}{\partial z} \\
\varepsilon_{r\theta} &= \frac{1}{2}\left( \frac{1}{r}\frac{\partial u_r}{\partial \theta} + \frac{\partial u_\theta}{\partial r} - \frac{u_\theta}{r} \right) \\
\varepsilon_{\theta z} &= \frac{1}{2}\left( \frac{\partial u_\theta}{\partial z} + \frac{1}{r}\frac{\partial u_z}{\partial \theta} \right) \\
\varepsilon_{zr} &= \frac{1}{2}\left( \frac{\partial u_z}{\partial r} + \frac{\partial u_r}{\partial z} \right)
\end{aligned}
$$

### Spherical Coordinates $(r, \theta, \phi)$

With displacements $(u_r, u_\theta, u_\phi)$:

$$
\begin{aligned}
\varepsilon_{rr} &= \frac{\partial u_r}{\partial r} \\
\varepsilon_{\theta\theta} &= \frac{1}{r}\frac{\partial u_\theta}{\partial \theta} + \frac{u_r}{r} \\
\varepsilon_{\phi\phi} &= \frac{1}{r\sin\theta}\frac{\partial u_\phi}{\partial \phi} + \frac{u_r}{r} + \frac{u_\theta\cot\theta}{r} \\
\varepsilon_{r\theta} &= \frac{1}{2}\left( \frac{1}{r}\frac{\partial u_r}{\partial \theta} + \frac{\partial u_\theta}{\partial r} - \frac{u_\theta}{r} \right) \\
\varepsilon_{\theta\phi} &= \frac{1}{2}\left( \frac{1}{r\sin\theta}\frac{\partial u_\theta}{\partial \phi} + \frac{1}{r}\frac{\partial u_\phi}{\partial \theta} - \frac{u_\phi\cot\theta}{r} \right) \\
\varepsilon_{\phi r} &= \frac{1}{2}\left( \frac{1}{r\sin\theta}\frac{\partial u_r}{\partial \phi} + \frac{\partial u_\phi}{\partial r} - \frac{u_\phi}{r} \right)
\end{aligned}
$$

## Physical Interpretation

### Geometric Meaning

- **Normal strains:** Represent elongation or contraction of material fibers along coordinate directions
- **Shear strains:** Represent angular distortion between initially perpendicular material fibers

### Volumetric and Deviatoric Components

**Volumetric strain (dilatation):**
$$
\varepsilon_v = \varepsilon_{xx} + \varepsilon_{yy} + \varepsilon_{zz} = \nabla \cdot \mathbf{u}
$$

**Deviatoric strain (distortional part):**
$$
\boldsymbol{\varepsilon}' = \boldsymbol{\varepsilon} - \frac{1}{3}\varepsilon_v\mathbf{I}
$$

## Inverse Problem: Displacements from Strains

### Compatibility Conditions

Given a strain field $\boldsymbol{\varepsilon}$, a single-valued continuous [[Displacement Field]] $\mathbf{u}$ exists if and only if the strain field satisfies the **Saint-Venant [[Compatibility Equations]]**:

$$
\nabla \times (\nabla \times \boldsymbol{\varepsilon})^T = \mathbf{0}
$$

In 2D, this reduces to:
$$
\frac{\partial^2 \varepsilon_{xx}}{\partial y^2} + \frac{\partial^2 \varepsilon_{yy}}{\partial x^2} = 2\frac{\partial^2 \varepsilon_{xy}}{\partial x \partial y}
$$

### Cesàro-Volterra Formula

For simply connected domains, displacements can be recovered from strains by path integration:

$$
u_i(\mathbf{x}) = u_i(\mathbf{x}_0) + \omega_{ij}(\mathbf{x}_0)(x_j - x_{0j}) + \int_{\mathbf{x}_0}^{\mathbf{x}} \varepsilon_{ij}(\mathbf{x}') \, dx'_j
$$

where $\omega_{ij}$ is the rotation tensor.

## Special Cases and Reduced Theories

### One-Dimensional Case

For uniaxial deformation:
$$
\varepsilon = \frac{du}{dx}
$$

### Plane Strain

Assumptions: $\varepsilon_{zz} = \varepsilon_{xz} = \varepsilon_{yz} = 0$, $w = 0$:

$$
\begin{aligned}
\varepsilon_{xx} &= \frac{\partial u}{\partial x} \\
\varepsilon_{yy} &= \frac{\partial v}{\partial y} \\
\varepsilon_{xy} &= \frac{1}{2}\left( \frac{\partial u}{\partial y} + \frac{\partial v}{\partial x} \right)
\end{aligned}
$$

### Plane Stress

Assumptions: $\sigma_{zz} = \sigma_{xz} = \sigma_{yz} = 0$, but $\varepsilon_{zz} \neq 0$:

Strain-displacement relations remain the full 2D form, but with $\varepsilon_{zz}$ determined from [[Constitutive Equations]].

### Axisymmetric Problems (Cylindrical Coordinates)

For axisymmetric deformation ($\partial/\partial\theta = 0$, $u_\theta = 0$):

$$
\begin{aligned}
\varepsilon_{rr} &= \frac{\partial u_r}{\partial r} \\
\varepsilon_{\theta\theta} &= \frac{u_r}{r} \\
\varepsilon_{zz} &= \frac{\partial u_z}{\partial z} \\
\varepsilon_{rz} &= \frac{1}{2}\left( \frac{\partial u_r}{\partial z} + \frac{\partial u_z}{\partial r} \right)
\end{aligned}
$$

## Applications in [[Finite Element Analysis (FEA)]]

### Strain-Displacement Matrix ($\mathbf{B}$-matrix)

In displacement-based finite element formulations, strains are expressed in terms of nodal displacements:

$$
\boldsymbol{\varepsilon} = \mathbf{B} \mathbf{u}^e
$$

where:
- $\mathbf{B}$ is the strain-displacement matrix (contains derivatives of shape functions)
- $\mathbf{u}^e$ is the vector of element nodal displacements

#### For 2D Linear Elasticity

For a 2D element with shape functions $N_i(x,y)$:

$$
\mathbf{B}_i = 
\begin{bmatrix}
\frac{\partial N_i}{\partial x} & 0 \\
0 & \frac{\partial N_i}{\partial y} \\
\frac{\partial N_i}{\partial y} & \frac{\partial N_i}{\partial x}
\end{bmatrix}
$$

#### For 3D Solid Elements

$$
\mathbf{B}_i = 
\begin{bmatrix}
\frac{\partial N_i}{\partial x} & 0 & 0 \\
0 & \frac{\partial N_i}{\partial y} & 0 \\
0 & 0 & \frac{\partial N_i}{\partial z} \\
\frac{\partial N_i}{\partial y} & \frac{\partial N_i}{\partial x} & 0 \\
0 & \frac{\partial N_i}{\partial z} & \frac{\partial N_i}{\partial y} \\
\frac{\partial N_i}{\partial z} & 0 & \frac{\partial N_i}{\partial x}
\end{bmatrix}
$$

### Isoparametric Formulation

For elements with curved geometry, derivatives are computed in natural coordinates $(\xi, \eta, \zeta)$ and transformed using the Jacobian:

$$
\frac{\partial N_i}{\partial \mathbf{x}} = \mathbf{J}^{-1} \frac{\partial N_i}{\partial \boldsymbol{\xi}}
$$

where $\mathbf{J} = \frac{\partial \mathbf{x}}{\partial \boldsymbol{\xi}}$ is the [[Jacobian Matrix]].

## Higher-Order Strain Measures

### Strain Gradients

For strain-gradient theories or higher-order continua:

$$
\eta_{ijk} = \frac{\partial \varepsilon_{ij}}{\partial x_k}
$$

### Rotation-Displacement Relations

The rotation vector $\boldsymbol{\omega}$ (for infinitesimal rotations):

$$
\boldsymbol{\omega} = \frac{1}{2} \nabla \times \mathbf{u}
$$

In component form:
$$
\omega_x = \frac{1}{2}\left( \frac{\partial w}{\partial y} - \frac{\partial v}{\partial z} \right), \quad
\omega_y = \frac{1}{2}\left( \frac{\partial u}{\partial z} - \frac{\partial w}{\partial x} \right), \quad
\omega_z = \frac{1}{2}\left( \frac{\partial v}{\partial x} - \frac{\partial u}{\partial y} \right)
$$

## Limitations and Approximations

### Small Strain Assumption Validity

The linear strain-displacement relations are valid when:
- Displacement gradients are small: $|\partial u_i / \partial x_j| \ll 1$
- Rotations are small: $|\omega_{ij}| \ll 1$
- Typical limit: Strains less than 5%

### Large Deformation Formulations

For finite strains, must use:
- Proper finite strain measures (Green-Lagrange, Almansi-Euler)
- Objective stress rates in [[Constitutive Equations]]
- Updated or total Lagrangian formulations in FEM

## Relationship to Other Kinematic Quantities

### [[Velocity]]-Strain Relations

For rate-dependent materials:

$$
\mathbf{D} = \frac{1}{2}(\nabla \mathbf{v} + (\nabla \mathbf{v})^T)
$$

where $\mathbf{D}$ is the rate of deformation tensor, $\mathbf{v} = \dot{\mathbf{u}}$ is the velocity.

### Compatibility with Displacement Boundary Conditions

Essential (Dirichlet) boundary conditions are prescribed on displacements:

$$
\mathbf{u} = \mathbf{u}_0 \quad \text{on } \Gamma_u
$$

which directly affect the strain field through the strain-displacement relations.

## Applications Across Mechanics

### Structural Mechanics
- Beam bending: $\varepsilon_{xx} = -z \frac{d^2 w}{dx^2}$ (Euler-Bernoulli)
- Plate bending: $\varepsilon_{\alpha\beta} = -z \frac{\partial^2 w}{\partial x_\alpha \partial x_\beta}$ (Kirchhoff-Love)

### Geomechanics
- Soil and rock deformation analysis
- Settlement calculations

### Biomechanics
- Tissue deformation analysis
- Bone strain computation

### Experimental Mechanics
- Converting measured displacements to strains in DIC
- Strain computation from displacement gauges

## See Also

- [[Strain]]
- [[Displacement Field]]
- [[Compatibility Equations]]
- [[Deformation Gradient]]
- [[Finite Element Method]]
- [[Linear Elasticity]]
- [[Continuum Mechanics]]
- [[Tensor Calculus]]
- [[Jacobian Matrix]]
- [[Isoparametric Elements]]
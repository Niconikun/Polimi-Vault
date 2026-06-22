#Space-Structures #TBD 
## Formal Definition

**Equilibrium Equations** are a set of partial differential equations that express the balance of forces and moments within a continuum body or structural system. These equations ensure that at every point in the domain, the internal stresses are in equilibrium with the applied body forces, and that the net force and moment on any subdomain are zero. They are fundamental to [[Continuum Mechanics]] and structural analysis, providing the governing equations for stress and deformation fields.

## Mathematical Formulation

### General Three-Dimensional Equilibrium

For a continuum body in static equilibrium, the following equations must be satisfied:

#### Force Equilibrium ([[Linear Momentum]] Balance)

In the absence of inertial effects, the equilibrium of forces per unit volume is expressed as:

$$
\nabla \cdot \boldsymbol{\sigma} + \mathbf{b} = \mathbf{0} \quad \text{in } \Omega
$$

where:
- \( \boldsymbol{\sigma} \) is the Cauchy [[stress tensor]] (second-order, symmetric)
- \( \mathbf{b} \) is the body force vector per unit volume (e.g., gravity)
- \( \nabla \cdot \) denotes the divergence operator

In index notation (using Einstein summation convention):

$$
\sigma_{ij,j} + b_i = 0, \quad i = 1,2,3
$$

where \( \sigma_{ij,j} = \partial \sigma_{ij} / \partial x_j \).

#### Moment Equilibrium ([[Angular Momentum]] Balance)

The balance of moments (about any point) requires the [[stress tensor]] to be symmetric:

$$
\boldsymbol{\sigma} = \boldsymbol{\sigma}^T \quad \text{or} \quad \sigma_{ij} = \sigma_{ji}
$$

This condition ensures that there are no net internal couples.

### Component Form in Cartesian Coordinates

Expanding the force equilibrium equations in Cartesian coordinates \((x, y, z)\):

$$
\begin{aligned}
\frac{\partial \sigma_{xx}}{\partial x} + \frac{\partial \sigma_{xy}}{\partial y} + \frac{\partial \sigma_{xz}}{\partial z} + b_x &= 0 \\
\frac{\partial \sigma_{xy}}{\partial x} + \frac{\partial \sigma_{yy}}{\partial y} + \frac{\partial \sigma_{yz}}{\partial z} + b_y &= 0 \\
\frac{\partial \sigma_{xz}}{\partial x} + \frac{\partial \sigma_{yz}}{\partial y} + \frac{\partial \sigma_{zz}}{\partial z} + b_z &= 0
\end{aligned}
$$

### Two-Dimensional Cases

#### Plane Stress
For thin plates with stresses assumed to be in-plane only (\(\sigma_{zz} = \sigma_{xz} = \sigma_{yz} = 0\)):

$$
\begin{aligned}
\frac{\partial \sigma_{xx}}{\partial x} + \frac{\partial \sigma_{xy}}{\partial y} + b_x &= 0 \\
\frac{\partial \sigma_{xy}}{\partial x} + \frac{\partial \sigma_{yy}}{\partial y} + b_y &= 0
\end{aligned}
$$

#### Plane [[Strain]]
For long bodies with strain confined to a plane (\(\varepsilon_{zz} = \varepsilon_{xz} = \varepsilon_{yz} = 0\)):

$$
\begin{aligned}
\frac{\partial \sigma_{xx}}{\partial x} + \frac{\partial \sigma_{xy}}{\partial y} + b_x &= 0 \\
\frac{\partial \sigma_{xy}}{\partial x} + \frac{\partial \sigma_{yy}}{\partial y} + b_y &= 0
\end{aligned}
$$

Note: \(\sigma_{zz}\) is non-zero but does not appear in the equilibrium equations as it is not a function of \(x\) and \(y\).

## Boundary Conditions

The equilibrium equations are supplemented by boundary conditions:

### Traction Boundary Conditions
On a portion of the boundary \(\Gamma_t\) with prescribed traction \(\mathbf{t}\):

$$
\boldsymbol{\sigma} \mathbf{n} = \mathbf{t} \quad \text{on } \Gamma_t
$$

where \(\mathbf{n}\) is the unit outward normal vector. In component form:

$$
\begin{aligned}
\sigma_{xx} n_x + \sigma_{xy} n_y + \sigma_{xz} n_z &= t_x \\
\sigma_{xy} n_x + \sigma_{yy} n_y + \sigma_{yz} n_z &= t_y \\
\sigma_{xz} n_x + \sigma_{yz} n_y + \sigma_{zz} n_z &= t_z
\end{aligned}
$$

### [[Displacement]] Boundary Conditions
On a portion of the boundary \(\Gamma_u\):

$$
\mathbf{u} = \mathbf{u}_0 \quad \text{on } \Gamma_u
$$

where \(\mathbf{u}_0\) is a prescribed displacement.

## Derivation Principles

### Principle of [[Conservation of Linear Momentum]]
For a static system, the sum of forces on any subdomain \(V\) must vanish:

$$
\int_{\partial V} \mathbf{t} \, dS + \int_V \mathbf{b} \, dV = \mathbf{0}
$$

Applying the divergence theorem to the surface integral yields the local equilibrium equations.

### [[Virtual Work]] Principle (Weak Form)
An equivalent integral form of equilibrium is the [[Principle of Virtual Work]]:

$$
\int_\Omega \boldsymbol{\sigma} : \delta\boldsymbol{\varepsilon} \, dV = \int_\Omega \mathbf{b} \cdot \delta\mathbf{u} \, dV + \int_{\Gamma_t} \mathbf{t} \cdot \delta\mathbf{u} \, dS
$$

for all admissible virtual displacements \(\delta\mathbf{u}\) and corresponding virtual strains \(\delta\boldsymbol{\varepsilon}\). This weak form is the basis for finite element formulations.

## Specialized Equilibrium Equations

### Beam Bending Equilibrium

For Euler-Bernoulli beams under transverse loading:

$$
\begin{aligned}
\frac{dV}{dx} + q(x) &= 0 \\
\frac{dM}{dx} - V &= 0
\end{aligned}
$$

where:
- \(V\) = shear force
- \(M\) = bending moment
- \(q(x)\) = distributed transverse load

Combining gives:

$$
\frac{d^2 M}{dx^2} + q(x) = 0
$$

### Plate Bending Equilibrium

For Kirchhoff plates:

$$
\begin{aligned}
\frac{\partial Q_x}{\partial x} + \frac{\partial Q_y}{\partial y} + q &= 0 \\
\frac{\partial M_{xx}}{\partial x} + \frac{\partial M_{xy}}{\partial y} - Q_x &= 0 \\
\frac{\partial M_{xy}}{\partial x} + \frac{\partial M_{yy}}{\partial y} - Q_y &= 0
\end{aligned}
$$

where \(Q_x, Q_y\) are transverse shear forces, \(M_{xx}, M_{yy}, M_{xy}\) are bending and twisting moments, and \(q\) is the distributed transverse load.

Eliminating shear forces yields:

$$
\frac{\partial^2 M_{xx}}{\partial x^2} + 2\frac{\partial^2 M_{xy}}{\partial x \partial y} + \frac{\partial^2 M_{yy}}{\partial y^2} + q = 0
$$

## Equilibrium in Terms of Displacements

### Navier Equations (Linear Elasticity)

Substituting the strain-displacement and constitutive relations into the equilibrium equations yields the Navier equations for isotropic linear elasticity:

$$
(\lambda + \mu) \nabla (\nabla \cdot \mathbf{u}) + \mu \nabla^2 \mathbf{u} + \mathbf{b} = \mathbf{0}
$$

where \(\lambda\) and \(\mu\) are [[Lamé constants]], and \(\mathbf{u}\) is the displacement vector.

In component form:

$$
\begin{aligned}
(\lambda + \mu) \frac{\partial}{\partial x} \left( \frac{\partial u}{\partial x} + \frac{\partial v}{\partial y} + \frac{\partial w}{\partial z} \right) + \mu \nabla^2 u + b_x &= 0 \\
(\lambda + \mu) \frac{\partial}{\partial y} \left( \frac{\partial u}{\partial x} + \frac{\partial v}{\partial y} + \frac{\partial w}{\partial z} \right) + \mu \nabla^2 v + b_y &= 0 \\
(\lambda + \mu) \frac{\partial}{\partial z} \left( \frac{\partial u}{\partial x} + \frac{\partial v}{\partial y} + \frac{\partial w}{\partial z} \right) + \mu \nabla^2 w + b_z &= 0
\end{aligned}
$$

## Dynamic Equilibrium

When inertial effects are significant, the equilibrium equations generalize to the equations of motion:

$$
\nabla \cdot \boldsymbol{\sigma} + \mathbf{b} = \rho \ddot{\mathbf{u}}
$$

where \(\rho\) is the density and \(\ddot{\mathbf{u}}\) is the acceleration.

## Stress Functions

For two-dimensional problems, the equilibrium equations can be satisfied automatically by introducing a stress function:

### Airy Stress Function (Plane Problems)

For plane stress or plane strain with no body forces, a scalar Airy stress function \(\Phi(x,y)\) is defined such that:

$$
\sigma_{xx} = \frac{\partial^2 \Phi}{\partial y^2}, \quad \sigma_{yy} = \frac{\partial^2 \Phi}{\partial x^2}, \quad \sigma_{xy} = -\frac{\partial^2 \Phi}{\partial x \partial y}
$$

These definitions satisfy the equilibrium equations identically.

### Prandtl Stress Function ([[Torsion]])

For [[torsion]] of prismatic bars, the shear stresses are derived from Prandtl's stress function \(\Psi(x,y)\):

$$
\sigma_{xz} = \frac{\partial \Psi}{\partial y}, \quad \sigma_{yz} = -\frac{\partial \Psi}{\partial x}
$$

which satisfy equilibrium when body forces are absent.

## Applications and Significance

### Structural Analysis
- Determining internal forces and stresses in beams, frames, trusses, plates, and shells.
- Design and safety assessment of structures.

### Material Science
- Analysis of residual stresses.
- Study of deformation mechanisms.

### Geomechanics
- Stress distribution in soil and rock masses.
- Analysis of foundations and underground structures.

### Biomechanics
- Stress analysis in bones and tissues.
- Design of prosthetic devices.

## Solution Methods

### Analytical Solutions
- Direct integration for simple geometries and loading.
- Use of stress functions for two-dimensional problems.
- Transform methods for complex boundaries.

### Numerical Methods
- [[Finite Element Method]] (FEM): Solves the weak form of equilibrium equations.
- Finite Difference Method (FDM): Direct discretization of the PDEs.
- Boundary Element Method (BEM): Reduces problem to boundary integrals.

## Limitations and Assumptions

### Linearity Assumptions
- Most formulations assume small deformations and linear material behavior.
- Geometric nonlinearity requires updated equilibrium equations.

### Material Homogeneity
- Derived for homogeneous materials; heterogeneous materials require modification.

### Continuum Assumption
- Assumes material is a continuum; not valid at atomic or granular scales.

## See Also

- [[Stress Tensor]]
- [[Strain-Displacement Relations]]
- [[Constitutive Equations]]
- [[Virtual Work Principle]]
- [[Navier Equations]]
- [[Airy Stress Function]]
- [[Finite Element Method]]
- [[Beam Theory]]
- [[Plate Theory]]
- [[Continuum Mechanics]]
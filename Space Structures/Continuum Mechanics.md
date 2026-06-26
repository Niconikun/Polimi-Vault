## Formal Definition

**Continuum Mechanics** is a branch of mechanics that models materials as continuous masses rather than discrete particles, employing field quantities (density, velocity, stress, etc.) that vary smoothly over the material domain. It provides a macroscopic framework for analyzing deformation and flow of materials under external influences, abstracting away atomic and molecular details to describe material behavior at length scales much larger than inter-atomic distances. The theory rests on the fundamental assumption that matter is continuously distributed throughout space, filling the region it occupies.

## Historical Development

### Foundational Contributions
- **17th century:** Newton's laws of motion and Euler's fluid equations
- **18th century:** Bernoulli's work on hydrodynamics, Cauchy's stress principle
- **1822:** Navier's equations of elasticity
- **1827-1845:** Cauchy's development of stress tensor and continuum theory
- **1850s:** Stokes' formulation of viscous fluid flow
- **20th century:** Truesdell, Noll's axiomatic formulation, Coleman's thermodynamics

## Fundamental Concepts

### Continuum Hypothesis

The central assumption that matter is continuously distributed, allowing definition of field quantities at every point:

$$
\rho(\mathbf{x}, t) = \lim_{\Delta V \to V_0} \frac{\Delta m}{\Delta V}
$$

where $V_0$ is the representative elementary volume—small enough to be considered a point macroscopically but large enough to contain sufficient particles for statistical averaging.

### Motion and Deformation

#### Material vs. Spatial Descriptions

**Material (Lagrangian) description:** Follows individual material particles:
$$
\mathbf{x} = \boldsymbol{\chi}(\mathbf{X}, t)
$$
where $\mathbf{X}$ is material coordinate, $\mathbf{x}$ is spatial position.

**Spatial (Eulerian) description:** Observes fixed points in space:
$$
\mathbf{v} = \mathbf{v}(\mathbf{x}, t)
$$

#### Deformation Measures

**Deformation gradient:**
$$
\mathbf{F} = \frac{\partial \boldsymbol{\chi}}{\partial \mathbf{X}} = \nabla_0 \boldsymbol{\chi}
$$

**Right Cauchy-Green tensor:**
$$
\mathbf{C} = \mathbf{F}^T \mathbf{F}
$$

**Green-Lagrange [[strain]] tensor:**
$$
\mathbf{E} = \frac{1}{2}(\mathbf{C} - \mathbf{I})
$$

### Kinematics

#### Velocity and [[Acceleration]]

**Material time derivative:**
$$
\dot{\mathbf{v}} = \frac{\partial \mathbf{v}}{\partial t} + (\nabla \mathbf{v})\mathbf{v}
$$

**Rate of deformation tensor:**
$$
\mathbf{D} = \frac{1}{2}(\nabla \mathbf{v} + (\nabla \mathbf{v})^T)
$$

**Spin tensor:**
$$
\mathbf{W} = \frac{1}{2}(\nabla \mathbf{v} - (\nabla \mathbf{v})^T)
$$

## Conservation Laws

### Mass Conservation (Continuity Equation)

**Spatial form:**
$$
\frac{\partial \rho}{\partial t} + \nabla \cdot (\rho \mathbf{v}) = 0
$$

**Material form:**
$$
\rho J = \rho_0
$$
where $J = \det(\mathbf{F})$.

### [[Linear Momentum]] Balance

**Cauchy's first law:**
$$
\nabla \cdot \boldsymbol{\sigma} + \rho \mathbf{b} = \rho \dot{\mathbf{v}}
$$
where $\boldsymbol{\sigma}$ is Cauchy stress tensor, $\mathbf{b}$ is body force per unit mass.

### [[Angular Momentum]] Balance

**Cauchy's second law:**
$$
\boldsymbol{\sigma} = \boldsymbol{\sigma}^T
$$
Stress tensor symmetry (in absence of body couples).

### Energy Conservation (First Law)

**Spatial form:**
$$
\rho \dot{e} = \boldsymbol{\sigma} : \mathbf{D} - \nabla \cdot \mathbf{q} + \rho r
$$
where $e$ is specific [[internal energy]], $\mathbf{q}$ is heat flux, $r$ is heat supply.

## Constitutive Theory

### General Principles

1. **Determinism:** Stress depends on past history of motion and [[Temperature]]
2. **Local action:** Stress at point depends only on neighborhood
3. **Material frame indifference (Objectivity):** [[Constitutive Equations]] invariant under observer changes
4. **Material symmetry:** [[Invariance]] under symmetry transformations
5. **Thermodynamic consistency:** Must satisfy second law

### Material Classifications

#### Elastic Materials
Stress depends only on current deformation:
$$
\boldsymbol{\sigma} = \hat{\boldsymbol{\sigma}}(\mathbf{F})
$$

**[[Hyperelastic materials]]:**
$$
\boldsymbol{\sigma} = \frac{1}{J} \frac{\partial W}{\partial \mathbf{F}} \mathbf{F}^T
$$
with [[Strain Energy]] $W(\mathbf{F})$.

#### Viscous Fluids
Stress depends on rate of deformation:
$$
\boldsymbol{\sigma} = -p\mathbf{I} + \mathbf{f}(\mathbf{D})
$$

**Newtonian fluids:**
$$
\boldsymbol{\sigma} = -p\mathbf{I} + 2\mu\mathbf{D} + \lambda(\text{tr}\mathbf{D})\mathbf{I}
$$

#### Plastic Materials
Exhibit permanent deformation beyond yield [[surface]]:
$$
f(\boldsymbol{\sigma}, \mathbf{q}) \leq 0
$$
with flow rule and hardening laws.

#### Viscoelastic Materials
Combine elastic and viscous response:
$$
\boldsymbol{\sigma} = \int_0^t \mathbf{G}(t-s) : \dot{\boldsymbol{\varepsilon}}(s) ds
$$

## Field Equations

### Navier-Stokes Equations (Newtonian Fluids)

$$
\rho\left(\frac{\partial \mathbf{v}}{\partial t} + \mathbf{v} \cdot \nabla \mathbf{v}\right) = -\nabla p + \mu\nabla^2\mathbf{v} + \rho\mathbf{b}
$$

with incompressibility constraint $\nabla \cdot \mathbf{v} = 0$.

### Navier Equations (Linear Elasticity)

For isotropic linear elasticity:
$$
(\lambda + \mu)\nabla(\nabla \cdot \mathbf{u}) + \mu\nabla^2\mathbf{u} + \rho\mathbf{b} = \rho\ddot{\mathbf{u}}
$$

where $\mathbf{u}$ is [[Displacement]], $\lambda, \mu$ are [[Lamé constants]].

### [[Heat Conduction]] Equation

$$
\rho c_p \dot{\theta} = \nabla \cdot (k\nabla\theta) + \boldsymbol{\sigma} : \mathbf{D} + \rho r
$$

## Thermodynamic Foundations

### Second Law (Clausius-Duhem Inequality)

$$
-\rho(\dot{\psi} + \eta\dot{\theta}) + \boldsymbol{\sigma} : \mathbf{D} - \frac{1}{\theta}\mathbf{q} \cdot \nabla\theta \geq 0
$$

where $\psi = e - \theta\eta$ is Helmholtz free energy, $\eta$ is entropy.

### Coleman-Noll Procedure

Systematic derivation of [[Constitutive Equations]] from thermodynamic principles:

1. Postulate form of free energy $\psi$
2. Compute its material time derivative
3. Substitute into Clausius-Duhem inequality
4. Derive restrictions on constitutive functions

## Specialized Theories

### Linear Elasticity (Small Deformations)

**Strain-displacement:**
$$
\boldsymbol{\varepsilon} = \frac{1}{2}(\nabla\mathbf{u} + \nabla\mathbf{u}^T)
$$

**[[Hooke's Law]]:**
$$
\boldsymbol{\sigma} = \mathbf{C} : \boldsymbol{\varepsilon}
$$

For isotropy:
$$
\boldsymbol{\sigma} = \lambda\text{tr}(\boldsymbol{\varepsilon})\mathbf{I} + 2\mu\boldsymbol{\varepsilon}
$$

### Finite Elasticity

**Stress measures:**
- First Piola-Kirchhoff: $\mathbf{P} = J\boldsymbol{\sigma}\mathbf{F}^{-T}$
- Second Piola-Kirchhoff: $\mathbf{S} = J\mathbf{F}^{-1}\boldsymbol{\sigma}\mathbf{F}^{-T}$

**Balance laws in material form:**
$$
\nabla_0 \cdot \mathbf{P} + \rho_0\mathbf{b} = \rho_0\ddot{\mathbf{u}}
$$

### Plasticity

**Yield criterion:**
$$
f(\boldsymbol{\sigma}, \mathbf{q}) = 0
$$

**Flow rule:**
$$
\dot{\boldsymbol{\varepsilon}}^p = \dot{\lambda}\frac{\partial g}{\partial \boldsymbol{\sigma}}
$$

**Hardening laws:**
Evolution equations for internal variables $\mathbf{q}$.

## Mathematical Framework

### Function Spaces

**Sobolev spaces:** $H^m(\Omega)$ for displacement fields
**Lebesgue spaces:** $L^p(\Omega)$ for stresses, strains
**[[Tensor]] spaces:** Appropriate spaces for stress and strain tensors

### [[Boundary Value Problems]]

General form:
$$
\begin{aligned}
\mathcal{L}(\mathbf{u}) &= \mathbf{f} \quad \text{in } \Omega \\
\mathcal{B}(\mathbf{u}) &= \mathbf{g} \quad \text{on } \partial\Omega
\end{aligned}
$$

with existence, uniqueness, and regularity theorems.

### Variational Formulations

**[[Principle of Virtual Work]]:**
$$
\int_\Omega \boldsymbol{\sigma} : \delta\boldsymbol{\varepsilon} \, dV = \int_\Omega \rho\mathbf{b} \cdot \delta\mathbf{u} \, dV + \int_{\partial\Omega} \mathbf{t} \cdot \delta\mathbf{u} \, dS
$$

**[[Hamilton's Principle]]:**
$$
\delta\int_{t_1}^{t_2} (T - U) dt = 0
$$

## Applications

### [[Solid Mechanics]]
- Stress analysis in structures
- Fracture and damage mechanics
- Soil and rock mechanics
- Biomechanics (bone, tissue mechanics)

### Fluid Mechanics
- Aerodynamics and hydrodynamics
- Turbulence modeling
- Non-Newtonian fluid flow
- Microfluidics

### Multi-physics Problems
- Thermo-mechanics (thermal stresses)
- Electro-mechanics (piezoelectricity)
- Fluid-structure interaction
- Poromechanics (porous media flow)

### Manufacturing Processes
- Metal forming and plasticity
- Polymer processing
- Composite material fabrication
- Additive manufacturing

## Computational Continuum Mechanics

### [[Finite Element Method]] (FEM)
- Displacement-based formulations
- Mixed formulations for incompressibility
- Large deformation analysis (updated Lagrangian, total Lagrangian)
- Contact and interface problems

### Finite Volume Method (FVM)
- Primarily for fluid dynamics
- Conservative discretization of balance laws
- Complex geometries and multiphase flows

### Boundary Element Method (BEM)
- Reduced dimensionality for linear problems
- Effective for infinite domains
- Fracture mechanics applications

### Meshfree Methods
- Smoothed particle hydrodynamics (SPH)
- Element-free Galerkin (EFG) methods
- Peridynamics for fracture

## Advanced Topics

### Nonlinear Material Behavior
- Finite [[strain]] plasticity
- Viscoplasticity and creep
- Damage and fracture mechanics
- Phase transformations

### Instabilities and Bifurcation
- Buckling of structures
- Shear band formation
- Material instability (loss of ellipticity)
- Pattern formation

### Multi-scale Methods
- Homogenization theory
- Computational homogenization (FE²)
- Atomistic-to-continuum coupling

### Non-classical Continua
- Cosserat (micropolar) continua
- Strain-gradient theories
- Non-local continua
- Porous media theories

## Limitations and Extensions

### Breakdown of Continuum Assumption
- Nanoscale phenomena (length scales ~1-100 nm)
- Rarefied gas dynamics (Knudsen number > 0.1)
- Discrete fracture propagation

### Extended Theories
- Peridynamics: Non-local formulation for fracture
- [[Molecular dynamics]]: Atomistic simulation
- Discrete element methods: Granular materials
- [[Quantum mechanics]]: Electronic structure effects

## Current Research Directions

### Advanced Materials
- Metamaterials with tailored properties
- Active and smart materials
- Biological and bio-inspired materials
- 2D materials and nanocomposites

### Computational Advances
- Isogeometric analysis
- [[Machine learning]] in constitutive modeling
- High-performance computing for multiscale problems
- Uncertainty quantification

### Emerging Applications
- Soft robotics and flexible electronics
- Tissue engineering and regenerative medicine
- Energy harvesting materials
- Space exploration materials

## See Also

- [[Solid Mechanics]]
- [[Fluid Mechanics]]
- [[Constitutive Equations]]
- [[Continuum Thermodynamics]]
- [[Finite Element Method]]
- [[Tensor Calculus]]
- [[Nonlinear Mechanics]]
- [[Multi-scale Modeling]]
- [[Continuum Damage Mechanics]]
- [[Peridynamics]]
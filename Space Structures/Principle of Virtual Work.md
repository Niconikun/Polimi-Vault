# Principle of Virtual Work

## Formal Definition

The **Principle of Virtual Work** (PVW) is a fundamental [[Variational Principle]] in mechanics that states: *For a body in equilibrium, the total [[virtual work]] done by all internal and external forces during any kinematically admissible [[virtual displacement]] is zero.* This principle provides a weak (integral) form of the [[Equilibrium Equations]] and serves as the foundation for many numerical methods in structural analysis, including the [[Finite Element Method]].

## Mathematical Formulation

### General Statement

For a deformable body in static equilibrium under the action of body forces $\mathbf{b}$ and surface tractions $\mathbf{t}$, the principle states:

$$
\delta W_{\text{int}} = \delta W_{\text{ext}}
$$

or more explicitly:

$$
\int_\Omega \boldsymbol{\sigma} : \delta\boldsymbol{\varepsilon} \, d\Omega = \int_\Omega \mathbf{b} \cdot \delta\mathbf{u} \, d\Omega + \int_{\Gamma_t} \mathbf{t} \cdot \delta\mathbf{u} \, dS
$$

where:
- $\boldsymbol{\sigma}$ = Cauchy stress tensor (current stresses in equilibrium)
- $\delta\boldsymbol{\varepsilon}$ = virtual strain tensor (symmetric part of gradient of [[virtual displacement]])
- $\mathbf{b}$ = body force vector per unit volume
- $\mathbf{t}$ = prescribed traction vector on boundary $\Gamma_t$
- $\delta\mathbf{u}$ = virtual [[Displacement Field]] (kinematically admissible)
- $\Omega$ = domain occupied by the body
- $\Gamma_t$ = portion of boundary with prescribed tractions

### Virtual Quantities

**[[Virtual displacement]]** $\delta\mathbf{u}$:
- An infinitesimal, arbitrary [[Displacement Field]]
- Must be **kinematically admissible**: satisfies homogeneous [[Essential Boundary Conditions]]
- Must be **continuous** and sufficiently smooth
- Independent of actual displacements and time

**Virtual strain** $\delta\boldsymbol{\varepsilon}$:
Derived from [[virtual displacement]] via the strain-displacement relation:
$$
\delta\boldsymbol{\varepsilon} = \frac{1}{2}(\nabla \delta\mathbf{u} + (\nabla \delta\mathbf{u})^T)
$$

## Theoretical Foundations

### Equilibrium Statement

The Principle of Virtual Work is equivalent to the [[Strong Form (Pointwise Form)]] [[Equilibrium Equations]]:

**[[Strong Form (Pointwise Form)]] (local equilibrium):**
$$
\begin{aligned}
\nabla \cdot \boldsymbol{\sigma} + \mathbf{b} &= \mathbf{0} \quad \text{in } \Omega \\
\boldsymbol{\sigma}\mathbf{n} &= \mathbf{t} \quad \text{on } \Gamma_t
\end{aligned}
$$

**Weak form ([[virtual work]]):**
$$
\int_\Omega \boldsymbol{\sigma} : \delta\boldsymbol{\varepsilon} \, d\Omega - \int_\Omega \mathbf{b} \cdot \delta\mathbf{u} \, d\Omega - \int_{\Gamma_t} \mathbf{t} \cdot \delta\mathbf{u} \, dS = 0
$$

for all virtual displacements $\delta\mathbf{u}$ that vanish on $\Gamma_u$ (where displacements are prescribed).

### Derivation from Equilibrium

Starting from the equilibrium equation $\nabla \cdot \boldsymbol{\sigma} + \mathbf{b} = \mathbf{0}$:
1. Multiply by [[virtual displacement]] $\delta\mathbf{u}$
2. Integrate over domain $\Omega$
3. Apply divergence theorem
4. Use boundary conditions

This yields the virtual work equation, demonstrating equivalence.

## Variants and Special Cases

### [[Principle of Virtual Displacements]]

The standard form presented above, emphasizing virtual displacements as the primary variable.

### Principle of Virtual Forces (Dual Principle)

For a compatible strain field, the total complementary virtual work is zero:

$$
\int_\Omega \delta\boldsymbol{\sigma} : \boldsymbol{\varepsilon} \, d\Omega - \int_{\Gamma_u} \delta\mathbf{t} \cdot \mathbf{u} \, dS = 0
$$

where $\delta\boldsymbol{\sigma}$ is a virtual stress field satisfying equilibrium.

### Extended Principles

**With inertia forces (D'Alembert's principle):**
$$
\int_\Omega \boldsymbol{\sigma} : \delta\boldsymbol{\varepsilon} \, d\Omega = \int_\Omega (\mathbf{b} - \rho\ddot{\mathbf{u}}) \cdot \delta\mathbf{u} \, d\Omega + \int_{\Gamma_t} \mathbf{t} \cdot \delta\mathbf{u} \, dS
$$

**With conservative forces:**
If forces are conservative, PVW is equivalent to the Principle of Stationary Potential Energy.

## Applications in [[Finite Element Method]]

### Weak Form Discretization

The PVW provides the foundation for finite element formulation:

1. **Approximation:** $\mathbf{u}^h = \sum N_i \mathbf{u}_i$, $\delta\mathbf{u}^h = \sum N_i \delta\mathbf{u}_i$
2. **Strain-displacement:** $\boldsymbol{\varepsilon}^h = \mathbf{B}\mathbf{u}$, $\delta\boldsymbol{\varepsilon}^h = \mathbf{B}\delta\mathbf{u}$
3. **Discretized virtual work:** $\delta\mathbf{u}^T \left( \int_\Omega \mathbf{B}^T \boldsymbol{\sigma} \, d\Omega - \mathbf{f} \right) = 0$
4. **Since $\delta\mathbf{u}$ is arbitrary:** $\int_\Omega \mathbf{B}^T \boldsymbol{\sigma} \, d\Omega = \mathbf{f}$

### Linear Elasticity

For linear elastic materials $\boldsymbol{\sigma} = \mathbf{D}\boldsymbol{\varepsilon}$:

$$
\left( \int_\Omega \mathbf{B}^T \mathbf{D} \mathbf{B} \, d\Omega \right) \mathbf{u} = \mathbf{f}
$$

or $\mathbf{K}\mathbf{u} = \mathbf{f}$, where $\mathbf{K}$ is the stiffness matrix.

### Nonlinear Analysis

**Updated Lagrangian formulation:**
$$
\int_{\Omega} \mathbf{S} : \delta\mathbf{E} \, d\Omega = \int_{\Omega} \mathbf{b} \cdot \delta\mathbf{u} \, d\Omega + \int_{\Gamma_t} \mathbf{t} \cdot \delta\mathbf{u} \, dS
$$

where $\mathbf{S}$ is the second Piola-Kirchhoff stress and $\mathbf{E}$ is the Green-Lagrange strain.

## Physical Interpretation

### Virtual Work Concept

- **Internal virtual work:** $\delta W_{\text{int}} = \int_\Omega \boldsymbol{\sigma} : \delta\boldsymbol{\varepsilon} \, d\Omega$
  - Work done by actual stresses through virtual strains
  - Represents [[Strain Energy]] variation

- **External virtual work:** $\delta W_{\text{ext}} = \int_\Omega \mathbf{b} \cdot \delta\mathbf{u} \, d\Omega + \int_{\Gamma_t} \mathbf{t} \cdot \delta\mathbf{u} \, dS$
  - Work done by external forces through virtual displacements

### Energy Interpretation

For conservative systems, PVW is equivalent to:
$$
\delta\Pi = 0
$$
where $\Pi$ is the total potential energy. This is the Principle of Stationary Potential Energy.

## Advantages Over [[Strong Form (Pointwise Form)]]

### Reduced Continuity Requirements

- [[Strong Form (Pointwise Form)]] requires stresses differentiable (typically $C^1$)
- Weak form only requires integrals to exist (typically $H^1$ for displacements)
- Enables handling of discontinuous material properties

### [[Natural Boundary Conditions]]

Traction boundary conditions are incorporated naturally in the surface integral term, while essential (displacement) conditions are enforced on the virtual displacements.

### Foundation for Numerical Methods

Provides systematic approach for:
- [[Finite Element Method]]
- Boundary element method
- Meshfree methods

## Special Considerations

### Kinematic Admissibility

Virtual displacements must satisfy:
1. **Continuity:** Typically $\delta\mathbf{u} \in H^1(\Omega)$
2. **Boundary conditions:** $\delta\mathbf{u} = \mathbf{0}$ on $\Gamma_u$
3. **Infinitesimal:** Small enough to not alter geometry or boundary conditions

### Static Admissibility (for virtual forces)

Virtual stresses must satisfy:
1. **Equilibrium:** $\nabla \cdot \delta\boldsymbol{\sigma} = \mathbf{0}$ in $\Omega$
2. **Traction conditions:** $\delta\boldsymbol{\sigma}\mathbf{n} = \delta\mathbf{t}$ on $\Gamma_t$

## Extended Applications

### Nonlinear Materials

**Plasticity:** Virtual work principle with yield condition and flow rule
**Viscoelasticity:** Time-dependent constitutive relations
**Hyperelasticity:** [[Strain Energy]] density functions

### Contact Problems

Virtual work formulation with contact constraints:
$$
\delta W_{\text{contact}} = \int_{\Gamma_c} \mathbf{t}_c \cdot \delta\mathbf{g} \, dS
$$
where $\mathbf{g}$ is gap function and $\mathbf{t}_c$ is contact traction.

### Multiphysics Problems

**Thermoelasticity:**
$$
\int_\Omega \boldsymbol{\sigma} : \delta\boldsymbol{\varepsilon} \, d\Omega = \int_\Omega (\mathbf{b} - \beta\nabla T) \cdot \delta\mathbf{u} \, d\Omega + \int_{\Gamma_t} \mathbf{t} \cdot \delta\mathbf{u} \, dS
$$

**Piezoelectricity:** Coupled mechanical and electrical virtual work.

## Historical Development

### Origins

- **Ancient:** Aristotle's concept of virtual velocities
- **16th century:** Galileo's work on simple machines
- **1717:** Johann Bernoulli introduces principle of virtual velocities
- **1743:** D'Alembert extends to dynamic systems
- **19th century:** Lagrange formalizes for analytical mechanics

### Modern Formulation

- **20th century:** Extension to [[Continuum Mechanics]]
- **1950s:** Foundation for finite element method development
- **1970s:** Mathematical formalization in Sobolev spaces

## Limitations and Extensions

### Non-conservative Forces

For follower forces, [[Damping]], or friction, additional terms are needed:
$$
\delta W_{\text{non-conservative}} = \int_\Omega \mathbf{f}_{\text{nc}} \cdot \delta\mathbf{u} \, d\Omega
$$

### Large Deformations

For finite strains, must use appropriate stress and strain measures:
- First Piola-Kirchhoff stress and deformation gradient
- Second Piola-Kirchhoff stress and Green-Lagrange strain

### Dynamic Problems

D'Alembert's principle includes inertia forces:
$$
\int_\Omega \boldsymbol{\sigma} : \delta\boldsymbol{\varepsilon} \, d\Omega = \int_\Omega (\mathbf{b} - \rho\ddot{\mathbf{u}}) \cdot \delta\mathbf{u} \, d\Omega + \int_{\Gamma_t} \mathbf{t} \cdot \delta\mathbf{u} \, dS
$$

## Relationship to Other Principles

### Minimum [[Potential Energy]]

For conservative systems, PVW is equivalent to $\delta\Pi = 0$.

### [[Hamilton's Principle]]

For dynamic systems, the time integral of virtual work leads to [[Hamilton's Principle]].

### [[Weighted Residual Methods]]

PVW can be viewed as a [[Galerkin Method]] where weighting functions are virtual displacements.

## Computational Implementation

### Finite Element Procedure

1. **Domain discretization:** $\Omega = \bigcup_e \Omega_e$
2. **Shape functions:** $\mathbf{u}^h = \mathbf{N}\mathbf{u}_e$, $\delta\mathbf{u}^h = \mathbf{N}\delta\mathbf{u}_e$
3. **Strain-displacement:** $\boldsymbol{\varepsilon}^h = \mathbf{B}\mathbf{u}_e$, $\delta\boldsymbol{\varepsilon}^h = \mathbf{B}\delta\mathbf{u}_e$
4. **Element matrices:** $\mathbf{K}_e = \int_{\Omega_e} \mathbf{B}^T \mathbf{D} \mathbf{B} \, d\Omega$
5. **Assembly:** $\mathbf{K} = \bigwedge_e \mathbf{K}_e$, $\mathbf{f} = \bigwedge_e \mathbf{f}_e$
6. **Solution:** $\mathbf{K}\mathbf{u} = \mathbf{f}$

### Nonlinear Analysis

**[[Newton-Raphson Method]] iteration:**
$$
\mathbf{K}_T^{(i)} \Delta\mathbf{u}^{(i)} = \mathbf{f}_{\text{ext}} - \mathbf{f}_{\text{int}}^{(i)}
$$
where:
- $\mathbf{K}_T$ = tangent stiffness matrix
- $\mathbf{f}_{\text{int}} = \int_\Omega \mathbf{B}^T \boldsymbol{\sigma} \, d\Omega$

## See Also

- [[Variational Principle]]
- [[Principle of Minimum Potential Energy]]
- [[Finite Element Method]]
- [[Weak Form (Variational Form)]]
- [[Virtual Displacement]]
- [[D'Alembert's Principle]]
- [[Hamilton's Principle]]
- [[Weighted Residual Methods]]
- [[Nonlinear Finite Element Analysis]]
- [[Continuum Mechanics]]
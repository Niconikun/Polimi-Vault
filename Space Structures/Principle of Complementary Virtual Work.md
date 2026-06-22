## Formal Definition

The **Principle of Complementary Virtual Work** (also known as the **Principle of Virtual Forces** or **Dual [[Principle of Virtual Work]]**) is a [[Variational Principle]] in [[solid mechanics]] that states: *For a body with compatible deformation (satisfying [[Strain-Displacement Relations]] and displacement boundary conditions), the total complementary virtual work done by a system of virtual stresses (or forces) in equilibrium through the actual strains (or displacements) is zero.* This principle provides the dual formulation to the [[Principle of Virtual Work]], with virtual forces/stresses as the varying quantities rather than virtual displacements.

## Mathematical Formulation

### General Statement

For a deformable body with actual strains $\boldsymbol{\varepsilon}$ and actual displacements $\mathbf{u}$, and subject to virtual stresses $\delta\boldsymbol{\sigma}$ that satisfy equilibrium, the principle states:

$$
\int_\Omega \delta\boldsymbol{\sigma} : \boldsymbol{\varepsilon} \, d\Omega - \int_{\Gamma_u} \delta\mathbf{t} \cdot \mathbf{u} \, dS = 0
$$

where:
- $\delta\boldsymbol{\sigma}$ = virtual stress tensor (symmetric, satisfies equilibrium)
- $\boldsymbol{\varepsilon}$ = actual strain tensor (compatible with displacements)
- $\delta\mathbf{t} = \delta\boldsymbol{\sigma}\mathbf{n}$ = virtual traction on the boundary
- $\mathbf{u}$ = actual [[Displacement Field]]
- $\Gamma_u$ = portion of boundary where displacements are prescribed
- $\Omega$ = domain occupied by the body

### Admissibility Conditions

**Virtual stresses $\delta\boldsymbol{\sigma}$ must be:**
1. **Statically admissible:**
   - Satisfy equilibrium: $\nabla \cdot \delta\boldsymbol{\sigma} = \mathbf{0}$ in $\Omega$
   - Satisfy homogeneous traction conditions on $\Gamma_t$: $\delta\boldsymbol{\sigma}\mathbf{n} = \mathbf{0}$ on $\Gamma_t$
2. **Symmetric:** $\delta\boldsymbol{\sigma} = \delta\boldsymbol{\sigma}^T$

**Actual strains $\boldsymbol{\varepsilon}$ and displacements $\mathbf{u}$ must be:**
1. **Kinematically admissible:**
   - Compatible: $\boldsymbol{\varepsilon} = \frac{1}{2}(\nabla\mathbf{u} + \nabla\mathbf{u}^T)$ in $\Omega$
   - Satisfy displacement boundary conditions: $\mathbf{u} = \mathbf{u}_0$ on $\Gamma_u$

## Derivation and Equivalence

### Relationship to Virtual Work Principle

The Principle of Complementary Virtual Work (PCVW) is mathematically dual to the [[Principle of Virtual Work]] (PVW):

| **[[Principle of Virtual Work]]** | **Principle of Complementary Virtual Work** |
|-------------------------------|---------------------------------------------|
| Virtual displacements $\delta\mathbf{u}$ | Virtual stresses $\delta\boldsymbol{\sigma}$ |
| Actual stresses $\boldsymbol{\sigma}$ | Actual strains $\boldsymbol{\varepsilon}$ |
| Satisfies compatibility | Satisfies equilibrium |
| Tests equilibrium | Tests compatibility |

### Derivation from Weighted Residual

Starting from the strain-displacement compatibility equation:
$$
\boldsymbol{\varepsilon} - \frac{1}{2}(\nabla\mathbf{u} + \nabla\mathbf{u}^T) = \mathbf{0} \quad \text{in } \Omega
$$

Multiply by virtual stress $\delta\boldsymbol{\sigma}$ and integrate:
$$
\int_\Omega \delta\boldsymbol{\sigma} : \left[\boldsymbol{\varepsilon} - \frac{1}{2}(\nabla\mathbf{u} + \nabla\mathbf{u}^T)\right] d\Omega = 0
$$

Integration by parts and applying divergence theorem yields the PCVW statement.

## Formulations for Different Problems

### Linear Elasticity

For linear elastic materials with constitutive relation $\boldsymbol{\varepsilon} = \mathbf{S} : \boldsymbol{\sigma}$, where $\mathbf{S} = \mathbf{C}^{-1}$ is the compliance tensor:

$$
\int_\Omega \delta\boldsymbol{\sigma} : \mathbf{S} : \boldsymbol{\sigma} \, d\Omega - \int_{\Gamma_u} \delta\mathbf{t} \cdot \mathbf{u} \, dS = 0
$$

### Structural Elements

#### Truss Members
For a [[Truss Element]] with axial force $N$ and axial strain $\varepsilon$:

$$
\sum_i \delta N_i \cdot \Delta_i = 0
$$

where $\Delta_i$ is the actual elongation of member $i$, and $\delta N_i$ are virtual axial forces in equilibrium.

#### Beams
For Euler-Bernoulli beams:

$$
\int_0^L \delta M \cdot \kappa \, dx - \sum \delta P_i \cdot w_i - \sum \delta M_i \cdot \theta_i = 0
$$

where:
- $\delta M$ = virtual bending moment (satisfying equilibrium)
- $\kappa$ = actual curvature
- $\delta P_i, \delta M_i$ = virtual forces and moments at supports
- $w_i, \theta_i$ = actual displacements and rotations

### Matrix Form for Discrete Systems

For discrete structural systems:

$$
\{\delta\mathbf{F}\}^T \{\mathbf{\Delta}\} = 0
$$

where:
- $\{\delta\mathbf{F}\}$ = vector of virtual forces in equilibrium
- $\{\mathbf{\Delta}\}$ = vector of actual displacements

## Applications

### Flexibility Method (Force Method)

The PCVW forms the basis for the flexibility method in structural analysis:

1. Choose redundant forces/moments
2. Apply virtual forces corresponding to redundants
3. Use PCVW to obtain [[Compatibility Equations]]
4. Solve for redundant forces

### Computation of Displacements

To compute a specific displacement component $\Delta$ at a point:

1. Apply a unit virtual force (or moment) at the point in the direction of $\Delta$
2. Ensure the virtual force system is in equilibrium
3. Apply PCVW:

$$
1 \cdot \Delta = \int_\Omega \delta\boldsymbol{\sigma} : \boldsymbol{\varepsilon} \, d\Omega
$$

For linear elasticity:
$$
\Delta = \int_\Omega \delta\boldsymbol{\sigma} : \mathbf{S} : \boldsymbol{\sigma} \, d\Omega
$$

### Example: Beam Deflection

To find deflection at mid-span of a simply supported beam with actual moment $M(x)$:
1. Apply unit virtual force at mid-span
2. Compute virtual moment $\delta M(x)$
3. Apply:

$$
\Delta = \int_0^L \frac{\delta M(x) M(x)}{EI} dx
$$

### Stress Concentration Analysis

Using virtual stress fields to determine displacement fields around stress concentrations.

## Theoretical Foundations

### Duality with Virtual Work Principle

The two principles are related through **Legendre transformation**:

**Virtual Work Principle:**
$$
\delta W_{\text{int}} - \delta W_{\text{ext}} = 0 \quad \text{with } \delta\boldsymbol{\varepsilon} = \frac{1}{2}(\nabla\delta\mathbf{u} + \nabla\delta\mathbf{u}^T)
$$

**Complementary Virtual Work Principle:**
$$
\delta W^*_{\text{int}} - \delta W^*_{\text{ext}} = 0 \quad \text{with } \nabla \cdot \delta\boldsymbol{\sigma} = \mathbf{0}
$$

where $W^*$ denotes complementary work.

### Complementary Energy Principle

For conservative systems, PCVW is equivalent to the [[Stationarity]] of complementary energy:

$$
\delta \Pi_c[\boldsymbol{\sigma}] = 0
$$

where:
$$
\Pi_c[\boldsymbol{\sigma}] = \frac{1}{2} \int_\Omega \boldsymbol{\sigma} : \mathbf{S} : \boldsymbol{\sigma} \, d\Omega - \int_{\Gamma_u} \mathbf{u}_0 \cdot (\boldsymbol{\sigma}\mathbf{n}) \, dS
$$

### Betti's Reciprocal Theorem

A special case of PCVW that relates two different equilibrium states of the same linear elastic body:

$$
\int_\Omega \boldsymbol{\sigma}^{(1)} : \boldsymbol{\varepsilon}^{(2)} \, d\Omega = \int_\Omega \boldsymbol{\sigma}^{(2)} : \boldsymbol{\varepsilon}^{(1)} \, d\Omega
$$

## Finite Element Implementation

### Hybrid Finite Elements

Elements based on PCVW have independent approximations for:
- Stresses within elements
- Displacements on element boundaries

**Variational statement:**
Find $(\boldsymbol{\sigma}^h, \mathbf{u}^h)$ such that:

$$
\begin{aligned}
\int_{\Omega_e} \delta\boldsymbol{\sigma}^h : (\mathbf{S}\boldsymbol{\sigma}^h - \boldsymbol{\varepsilon}(\mathbf{u}^h)) \, d\Omega &= 0 \\
\int_{\Gamma_e} \delta\mathbf{u}^h \cdot (\mathbf{t}^h - \bar{\mathbf{t}}) \, dS &= 0
\end{aligned}
$$

for all admissible $(\delta\boldsymbol{\sigma}^h, \delta\mathbf{u}^h)$.

### Mixed Finite Elements

For problems where both displacement and stress are primary variables, PCVW provides one of the governing equations.

## Advantages and Limitations

### Advantages

1. **Natural for force method:** Directly provides [[Compatibility Equations]]
2. **Efficient for certain problems:** Particularly when number of redundants is small
3. **Physical insight:** Clear interpretation in terms of force paths
4. **Accurate stress computation:** Can yield better stress approximations than displacement-based methods

### Limitations

1. **Equilibrium satisfaction:** Constructing admissible virtual stress fields can be difficult for complex geometries
2. **Less general:** Not as widely applicable as displacement-based methods
3. **Implementation complexity:** More challenging to automate
4. **Singularities:** Problems with [[Rigid Body]] modes require special treatment

## Special Considerations

### Inelastic Materials

For nonlinear materials, the principle extends to:

$$
\int_\Omega \delta\boldsymbol{\sigma} : \boldsymbol{\varepsilon}_{\text{total}} \, d\Omega - \int_{\Gamma_u} \delta\mathbf{t} \cdot \mathbf{u} \, dS = 0
$$

where $\boldsymbol{\varepsilon}_{\text{total}}$ includes elastic, plastic, and thermal components.

### Geometric Nonlinearity

For large deformations, appropriate stress and strain measures must be used:
- Virtual stress: Variation of second Piola-Kirchhoff stress $\delta\mathbf{S}$
- Actual strain: Green-Lagrange strain $\mathbf{E}$

### Dynamic Problems

For dynamic systems with d'Alembert forces:

$$
\int_\Omega \delta\boldsymbol{\sigma} : \boldsymbol{\varepsilon} \, d\Omega - \int_{\Gamma_u} \delta\mathbf{t} \cdot \mathbf{u} \, dS - \int_\Omega \delta\mathbf{b} \cdot \mathbf{u} \, d\Omega = 0
$$

where $\delta\mathbf{b}$ are virtual body forces including inertial effects.

## Historical Development

### Origins

- **1864:** Maxwell's reciprocal theorem for trusses
- **1872:** Castigliano's theorem (special case of PCVW)
- **1875:** Betti's reciprocal theorem for continua
- **20th century:** Formalization as dual to virtual work principle

### Key Contributors

1. **James Clerk Maxwell (1831-1879):** Reciprocal relations in trusses
2. **Carlo Alberto Castigliano (1847-1884):** Theorem on displacements
3. **Enrico Betti (1823-1892):** Reciprocal theorem for elastic bodies
4. **Richard von Mises (1883-1953):** Generalization to continua

## Practical Applications

### Structural Analysis

1. **Indeterminate structures:** Force method for beams, frames, trusses
2. **Influence lines:** Using unit virtual loads
3. **Settlement analysis:** Computing forces due to support movements

### Design Calculations

1. **Deflection computations:** For serviceability checks
2. **Redundant force determination:** In statically indeterminate systems
3. **Stress resultant diagrams:** From virtual force distributions

### Experimental Mechanics

1. **Load path visualization:** Using photoelasticity with virtual loads
2. **Strain gauge analysis:** Interpreting measurements via virtual work concepts

## Relationship to Other Principles

### Castigliano's Theorems

**First theorem (Part 2):** The partial derivative of complementary energy with respect to a force gives the displacement in the direction of that force:

$$
\Delta_i = \frac{\partial \Pi_c}{\partial P_i}
$$

**Second theorem:** A special case of PCVW for linear elastic systems.

### Unit Load Method

A direct application of PCVW for computing displacements:

$$
\Delta = \int \frac{\delta M \cdot M}{EI} dx + \int \frac{\delta N \cdot N}{EA} dx + \int \frac{\delta V \cdot V}{GA} \kappa dx
$$

### Principle of Stationary Complementary Energy

For linear elastic systems, PCVW is equivalent to $\delta\Pi_c = 0$, where $\Pi_c$ is the total complementary energy.

## See Also

- [[Principle of Virtual Work]]
- [[Complementary Energy Principle]]
- [[Castigliano's Theorems]]
- Flexibility Method]]
- Unit Load Method]]
- Betti's Reciprocal Theorem]]
- Mixed Finite Element Methods]]
- Stress-Based Finite Elements]]
- Duality in Mechanics]]
- Energy Methods in Structural Analysis]]
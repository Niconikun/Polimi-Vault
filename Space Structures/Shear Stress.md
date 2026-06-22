#Space-Structures #TBD 
# Shear Stress

## Formal Definition

**Shear Stress** is a component of the stress tensor that acts parallel or tangential to the surface of a material element, representing the intensity of internal forces that tend to cause adjacent material layers to slide relative to each other. Unlike normal stress, which acts perpendicular to a surface and tends to elongate or compress the material, shear stress induces angular deformation and is responsible for phenomena such as cutting, twisting, and sliding failures in materials.

## Mathematical Formulation

### Stress Tensor Representation

In [[Continuum Mechanics]], the state of stress at a point is described by the Cauchy stress tensor $\boldsymbol{\sigma}$:

$$
\boldsymbol{\sigma} = 
\begin{bmatrix}
\sigma_{xx} & \sigma_{xy} & \sigma_{xz} \\
\sigma_{yx} & \sigma_{yy} & \sigma_{yz} \\
\sigma_{zx} & \sigma_{zy} & \sigma_{zz}
\end{bmatrix}
$$

where:
- Diagonal components ($\sigma_{xx}, \sigma_{yy}, \sigma_{zz}$) are **normal stresses**
- Off-diagonal components ($\sigma_{xy}, \sigma_{xz}, \sigma_{yz}$, etc.) are **shear stresses**

Due to the balance of [[Angular Momentum]] (in the absence of body couples), the stress tensor is symmetric:

$$
\sigma_{ij} = \sigma_{ji}
$$

Thus, there are only three independent shear stress components: $\sigma_{xy} = \sigma_{yx}$, $\sigma_{xz} = \sigma_{zx}$, and $\sigma_{yz} = \sigma_{zy}$.

### Definition

The shear stress $\tau$ (often denoted as $\sigma_{s}$ or $\tau$) on a plane with unit normal $\mathbf{n}$ in the direction of a unit vector $\mathbf{m}$ (lying in the plane, so $\mathbf{m} \cdot \mathbf{n} = 0$) is given by:

$$
\tau = \mathbf{m} \cdot \boldsymbol{\sigma} \mathbf{n}
$$

In terms of the stress tensor components, if the plane is perpendicular to the $x$-axis ($\mathbf{n} = \mathbf{e}_x$), then the shear stress in the $y$ direction is $\sigma_{xy}$ and in the $z$ direction is $\sigma_{xz}$.

### Engineering Notation

In engineering contexts, shear stress is often denoted by $\tau$ with subscripts indicating the plane and direction:

- $\tau_{xy}$: Shear stress on a plane perpendicular to the x-axis, acting in the y-direction.
- $\tau_{yx}$: Shear stress on a plane perpendicular to the y-axis, acting in the x-direction (equal to $\tau_{xy}$ by symmetry).

## Physical Interpretation

### Microscopic Origin

At the atomic/molecular level, shear stress arises from interatomic forces that resist relative sliding between adjacent layers. In crystalline materials, this involves the overcoming of atomic bonds and the motion of dislocations.

### Macroscopic Behavior

Shear stress causes **angular distortion** of a material element. Consider a small rectangular element in the xy-plane: a positive shear stress $\sigma_{xy}$ causes the element to deform into a parallelogram, with the right angles changing by the shear strain $\gamma_{xy}$.

## Shear Stress in Different Materials

### Solids

In solids, shear stress is related to shear strain through constitutive laws:

**Linear elastic (Hookean) solids:**
$$
\sigma_{xy} = G \gamma_{xy}
$$
where $G$ is the [[Shear Modulus]] (modulus of rigidity), related to [[Young's Modulus]] $E$ and [[Poisson's ratio]] $\nu$ by:
$$
G = \frac{E}{2(1+\nu)}
$$

**Plastic solids:** Once the shear stress reaches a critical value (yield stress in shear), permanent deformation occurs.

### Fluids

For fluids, shear stress is related to the rate of shear strain (velocity gradient):

**Newtonian fluids:**
$$
\tau = \mu \frac{du}{dy}
$$
where $\mu$ is the dynamic viscosity and $du/dy$ is the velocity gradient perpendicular to the flow direction.

**Non-Newtonian fluids:** The relationship may be nonlinear, time-dependent, or have a yield stress.

## Transformation of Stresses

### Plane Stress Transformation

For a state of plane stress ($\sigma_{zz}=\sigma_{xz}=\sigma_{yz}=0$), the shear stress on an inclined plane (angle $\theta$ from the x-axis) is given by:

$$
\tau_{\theta} = -\frac{\sigma_{xx} - \sigma_{yy}}{2} \sin 2\theta + \sigma_{xy} \cos 2\theta
$$

### Principal Stresses

At every point, there exist three mutually perpendicular planes on which the shear stress is zero. These are called **principal planes**, and the normal stresses on them are the **principal stresses**. The maximum shear stress at a point is given by:

$$
\tau_{\text{max}} = \frac{\sigma_1 - \sigma_3}{2}
$$

where $\sigma_1$ and $\sigma_3$ are the maximum and minimum principal stresses, respectively. The planes of maximum shear stress are oriented at $45^\circ$ to the principal planes.

## Measurement and Calculation

### Experimental Techniques

1. **Strain gauges:** Using rosettes to measure strains and converting to shear stress via [[Constitutive Equations]].
2. **Photoelasticity:** Using birefringent materials to visualize stress fringes, including shear stress.
3. **Shear-sensitive coatings:** Coatings that change appearance under shear.
4. **Direct shear tests:** In geotechnical and material testing.

### Analytical Calculation

From [[Equilibrium Equations]] and boundary conditions, shear stress distributions can be derived for simple geometries:

**Example: Shear stress in a beam** (from [[Euler-Bernoulli Beam Element]]):

For a beam with bending moment $M(x)$ and shear force $V(x)$, the shear stress at a distance $y$ from the neutral axis is:

$$
\tau_{xy} = \frac{VQ}{Ib}
$$

where:
- $Q$ is the first moment of area of the cross-section above $y$,
- $I$ is the second moment of area of the entire cross-section,
- $b$ is the width at the level $y$.

## Failure Criteria Involving Shear Stress

### Ductile Materials (Metals)

**Maximum shear stress criterion (Tresca):** Yielding occurs when the maximum shear stress reaches a critical value:

$$
\tau_{\text{max}} = \frac{\sigma_y}{2}
$$

where $\sigma_y$ is the yield stress in uniaxial tension.

**Von Mises criterion:** Uses the distortional energy, which includes shear stress components:

$$
\frac{1}{2}[(\sigma_{xx}-\sigma_{yy})^2 + (\sigma_{yy}-\sigma_{zz})^2 + (\sigma_{zz}-\sigma_{xx})^2 + 6(\sigma_{xy}^2+\sigma_{yz}^2+\sigma_{zx}^2)] = \sigma_y^2
$$

### Brittle Materials

**Mohr-Coulomb criterion:** Used for soils, rocks, and concrete:

$$
\tau = c + \sigma_n \tan \phi
$$

where $c$ is the cohesion, $\sigma_n$ is the normal stress on the failure plane, and $\phi$ is the angle of internal friction.

## Applications

### Structural Engineering

- Design of bolts, rivets, and welds subjected to shear.
- Analysis of beams and shafts under transverse loads.
- Stability of structures against sliding.

### Geotechnical Engineering

- Slope stability analysis (shear strength of soil).
- Foundation design (bearing capacity and shear failure).

### Manufacturing and Materials Processing

- Metal forming (shearing, punching).
- Machining (cutting forces involve shear).

### Biomechanics

- Shear stresses in blood flow (arterial walls).
- Bone and tissue mechanics.

## Special Cases and Advanced Topics

### Pure Shear

A state of stress where the normal stresses are zero and only shear stresses exist. For example, in the xy-plane:

$$
\boldsymbol{\sigma} = 
\begin{bmatrix}
0 & \tau & 0 \\
\tau & 0 & 0 \\
0 & 0 & 0
\end{bmatrix}
$$

The principal stresses are $\sigma_1 = \tau$, $\sigma_2 = 0$, $\sigma_3 = -\tau$, with principal planes at $45^\circ$.

### Shear in Thin-Walled Structures

**Thin-walled tubes under [[torsion]]:** Shear stress is given by the Bredt-Batho formula:

$$
\tau = \frac{T}{2A t}
$$

where $T$ is the torque, $A$ is the area enclosed by the midline of the tube, and $t$ is the wall thickness.

**Shear flow in beams:** In thin-walled beams, shear flow $q = \tau t$ is often used for analysis.

### Shear Center

For thin-walled open sections (like channels), the shear center is the point where a transverse load must be applied to avoid twisting. Shear stress distribution is non-uniform and must be computed accordingly.

## Limitations and Considerations

### Shear Stress Distribution

In many cases, shear stress is not uniform across a section. For example, in rectangular beams, shear stress varies parabolically with maximum at the neutral axis.

### Size Effects

In very small structures (micro/nano-scale), shear stress may exhibit size-dependent behavior due to strain gradient effects or surface stresses.

### Anisotropic Materials

For anisotropic materials (composites, crystals), shear stress-shear strain relationships are more complex and involve coupling between different stress components.

## Computational Methods

In [[Finite Element Analysis (FEA)]], shear stress is computed from the [[Displacement Field]] via the [[Strain-Displacement Relations]] and [[Constitutive Equations]]. Special care is needed for:

- **Shear locking:** In bending elements, overly stiff response due to poor shear strain representation.
- **Shear correction factors:** In Timoshenko beams and Mindlin plates, a factor is used to account for non-uniform shear stress distribution.

## See Also

- [[Normal Stress]]
- [[Stress Tensor]]
- [[Shear Strain]]
- [[Mohr's Circle]]
- [[Torsion]]
- [[Beam Shear Stress]]
- [[Yield Criteria]]
- [[Viscosity]]
- [[Finite Element Method]]
- [[Continuum Mechanics]]
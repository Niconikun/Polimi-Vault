# Shear Strain

## Formal Definition

**Shear Strain** is a dimensionless measure of angular distortion within a material, quantifying the change in angle between two initially perpendicular material line elements. It represents the tangent of the angle change caused by deformation and is a fundamental component of the strain tensor that characterizes the sliding of adjacent material layers relative to each other without volume change. Unlike normal strain, which measures elongation or contraction, shear strain captures shape distortion at constant area (2D) or volume (3D).

## Mathematical Formulation

### Tensor Definition

In [[Continuum Mechanics]], shear strain appears as the off-diagonal components of the strain tensor. For infinitesimal (small) deformations, the linearized strain tensor is:

$$
\boldsymbol{\varepsilon} = \frac{1}{2}(\nabla \mathbf{u} + (\nabla \mathbf{u})^T)
$$

where $\mathbf{u}$ is the [[Displacement Field]]. The shear strain components are:

$$
\varepsilon_{ij} = \frac{1}{2}\left( \frac{\partial u_i}{\partial x_j} + \frac{\partial u_j}{\partial x_i} \right) \quad \text{for } i \neq j
$$

### Engineering Shear Strain vs. Tensor Shear Strain

There are two common conventions for shear strain:

1. **Tensor shear strain** ($\varepsilon_{ij}$ for $i \neq j$):
   - Half the total angle change
   - Appears naturally in [[tensor]] formulations
   - Symmetric: $\varepsilon_{ij} = \varepsilon_{ji}$

2. **Engineering shear strain** ($\gamma_{ij}$):
   - Full angle change between initially perpendicular lines
   - Related by: $\gamma_{ij} = 2\varepsilon_{ij}$
   - Commonly used in engineering practice

Thus:
$$
\gamma_{xy} = \frac{\partial u}{\partial y} + \frac{\partial v}{\partial x} = 2\varepsilon_{xy}
$$

### Complete Set in 3D Cartesian Coordinates

For Cartesian coordinates $(x, y, z)$ with displacements $(u, v, w)$:

**[[Tensor]] components:**
$$
\begin{aligned}
\varepsilon_{xy} &= \frac{1}{2}\left( \frac{\partial u}{\partial y} + \frac{\partial v}{\partial x} \right) \\
\varepsilon_{yz} &= \frac{1}{2}\left( \frac{\partial v}{\partial z} + \frac{\partial w}{\partial y} \right) \\
\varepsilon_{zx} &= \frac{1}{2}\left( \frac{\partial w}{\partial x} + \frac{\partial u}{\partial z} \right)
\end{aligned}
$$

**Engineering components:**
$$
\begin{aligned}
\gamma_{xy} &= \frac{\partial u}{\partial y} + \frac{\partial v}{\partial x} \\
\gamma_{yz} &= \frac{\partial v}{\partial z} + \frac{\partial w}{\partial y} \\
\gamma_{zx} &= \frac{\partial w}{\partial x} + \frac{\partial u}{\partial z}
\end{aligned}
$$

## Physical Interpretation

### Geometric Meaning

Consider two initially perpendicular material line elements $dx$ and $dy$ in the undeformed configuration. After deformation:

- The angle between them becomes $\theta_{xy} = \frac{\pi}{2} - \gamma_{xy}$ (for small strains)
- The engineering shear strain $\gamma_{xy}$ represents the total change from a right angle
- Positive shear strain typically means the angle decreases (becomes acute)
- Negative shear strain means the angle increases (becomes obtuse)

Mathematically:
$$
\gamma_{xy} = \tan(\alpha) + \tan(\beta)
$$
where $\alpha$ and $\beta$ are the angles each line rotates toward the other.

### Visual Representation

For a small rectangular element in the xy-plane:
- Under pure shear, the rectangle deforms into a parallelogram
- The right angle changes by $\gamma_{xy}$ radians
- The diagonal lengths change, but area remains approximately constant for small strains

## Shear Strain in Different Coordinate Systems

### Cylindrical Coordinates $(r, \theta, z)$

With displacements $(u_r, u_\theta, u_z)$:

**[[Tensor]] components:**
$$
\begin{aligned}
\varepsilon_{r\theta} &= \frac{1}{2}\left( \frac{1}{r}\frac{\partial u_r}{\partial \theta} + \frac{\partial u_\theta}{\partial r} - \frac{u_\theta}{r} \right) \\
\varepsilon_{\theta z} &= \frac{1}{2}\left( \frac{\partial u_\theta}{\partial z} + \frac{1}{r}\frac{\partial u_z}{\partial \theta} \right) \\
\varepsilon_{zr} &= \frac{1}{2}\left( \frac{\partial u_z}{\partial r} + \frac{\partial u_r}{\partial z} \right)
\end{aligned}
$$

### Spherical Coordinates $(r, \theta, \phi)$

With displacements $(u_r, u_\theta, u_\phi)$:

**[[Tensor]] components:**
$$
\begin{aligned}
\varepsilon_{r\theta} &= \frac{1}{2}\left( \frac{1}{r}\frac{\partial u_r}{\partial \theta} + \frac{\partial u_\theta}{\partial r} - \frac{u_\theta}{r} \right) \\
\varepsilon_{\theta\phi} &= \frac{1}{2}\left( \frac{1}{r\sin\theta}\frac{\partial u_\theta}{\partial \phi} + \frac{1}{r}\frac{\partial u_\phi}{\partial \theta} - \frac{u_\phi\cot\theta}{r} \right) \\
\varepsilon_{\phi r} &= \frac{1}{2}\left( \frac{1}{r\sin\theta}\frac{\partial u_r}{\partial \phi} + \frac{\partial u_\phi}{\partial r} - \frac{u_\phi}{r} \right)
\end{aligned}
$$

## Relationship to [[Shear Stress]]

### Constitutive Laws

**Linear Elastic (Hookean) Solids:**
For isotropic materials:
$$
\sigma_{ij} = 2G\varepsilon_{ij} \quad \text{for } i \neq j
$$
or equivalently:
$$
\tau_{ij} = G\gamma_{ij}
$$
where $G$ is the [[Shear Modulus]] (modulus of rigidity), related to [[Young's Modulus]] $E$ and [[Poisson's ratio]] $\nu$ by:
$$
G = \frac{E}{2(1+\nu)}
$$

**Newtonian Fluids:**
Shear strain rate (not strain itself) relates to [[Shear Stress]]:
$$
\tau = \mu\dot{\gamma}
$$
where $\mu$ is the dynamic viscosity and $\dot{\gamma} = d\gamma/dt$ is the shear strain rate.

**Plastic Materials:**
Once yield criteria are met (e.g., Tresca: $\tau_{\text{max}} = \sigma_y/2$), plastic shear strain accumulates according to flow rules.

### [[Shear Modulus]] ($G$) Significance

The [[Shear Modulus]] quantifies a material's resistance to shear deformation:
- High $G$: Material resists shape distortion (e.g., steel: ~79 GPa)
- Low $G$: Material easily deforms in shear (e.g., rubber: ~0.0003 GPa)

## Strain Transformation

### Transformation Laws

For rotation of coordinate axes in 2D (angle $\theta$ from x-axis):

**Engineering shear strain transformation:**
$$
\gamma_{x'y'} = -(\varepsilon_{xx} - \varepsilon_{yy})\sin 2\theta + \gamma_{xy}\cos 2\theta
$$

**Tensor shear strain transformation:**
$$
\varepsilon_{x'y'} = -\frac{1}{2}(\varepsilon_{xx} - \varepsilon_{yy})\sin 2\theta + \varepsilon_{xy}\cos 2\theta
$$

### Principal Strains

At every point, there exist orientations where shear strain is zero. These are the **principal strain directions**. The principal strains $\varepsilon_1, \varepsilon_2, \varepsilon_3$ are the eigenvalues of the strain tensor.

**Maximum shear strain:**
$$
\gamma_{\text{max}} = \varepsilon_{\text{max}} - \varepsilon_{\text{min}}
$$
Occurs at 45° to the principal directions.

## Measurement Techniques

### Experimental Methods

1. **Strain Gauges:**
   - Rosette configurations (45° or 60° rosettes) to determine shear strain
   - Shear strain calculated from multiple normal strain measurements
   - For 45° rosette: $\gamma_{xy} = 2\varepsilon_{45} - (\varepsilon_0 + \varepsilon_{90})$

2. **Digital Image Correlation (DIC):**
   - Tracks [[Displacement Field]] by correlating speckle patterns
   - Computes full strain tensor, including shear components
   - High spatial resolution

3. **Photoelasticity:**
   - Uses birefringent materials
   - Shear strain affects fringe patterns
   - Particularly useful for stress concentration visualization

4. **Moiré Interferometry:**
   - Measures in-plane displacements
   - Shear strain obtained by differentiating displacement fields

5. **Shearography:**
   - Direct measurement of surface strain gradients
   - Sensitive to shear strains

### Calculation from Displacements

In [[Finite Element Analysis (FEA)]], shear strain is computed from nodal displacements:
$$
\boldsymbol{\varepsilon} = \mathbf{B}\mathbf{u}^e
$$
where $\mathbf{B}$ is the strain-displacement matrix containing derivatives of shape functions.

## Special Cases and Applications

### Pure Shear

A deformation state where:
- Normal strains are zero: $\varepsilon_{xx} = \varepsilon_{yy} = 0$
- Only shear strain exists: $\varepsilon_{xy} \neq 0$
- Area/volume remains constant for small strains

### Simple Shear

A special case of pure shear with additional constraint of no rotation in the average sense. The [[Displacement Field]] is:
$$
u = \gamma y, \quad v = 0, \quad w = 0
$$
giving $\gamma_{xy} = \gamma$.

### Beam Bending (Timoshenko Beam Theory)

Includes shear deformation effects:
$$
\gamma_{xz} = \frac{\partial w}{\partial x} - \theta_y
$$
where $w$ is transverse deflection and $\theta_y$ is rotation of cross-section.

### Plate and Shell Theories

**Kirchhoff-Love theory:** Assumes zero transverse shear strain ($\gamma_{xz} = \gamma_{yz} = 0$)

**Mindlin-Reissner theory:** Includes transverse shear strains:
$$
\gamma_{xz} = \frac{\partial w}{\partial x} - \theta_y, \quad \gamma_{yz} = \frac{\partial w}{\partial y} + \theta_x
$$

### [[Torsion]] of Shafts

For circular shafts under torque $T$:
$$
\gamma_{\theta z} = r\frac{d\phi}{dz}
$$
where $r$ is radial coordinate and $\phi$ is angle of twist per unit length.

## Compatibility Conditions

For a strain field to be physically admissible (derivable from a continuous [[Displacement Field]]), shear strains must satisfy [[Compatibility Equations]] with normal strains.

**2D compatibility:**
$$
\frac{\partial^2 \gamma_{xy}}{\partial x \partial y} = \frac{\partial^2 \varepsilon_{xx}}{\partial y^2} + \frac{\partial^2 \varepsilon_{yy}}{\partial x^2}
$$

**3D Saint-Venant [[Compatibility Equations]]** provide additional constraints involving shear strains.

## Material Behavior

### Elastic Range

For isotropic linear elasticity, [[Shear Stress]] and shear strain are proportional ([[Hooke's Law]] in shear).

### Yield Criteria Involving Shear Strain

**Tresca criterion:** Yielding when maximum shear strain reaches a critical value.

**Von Mises criterion:** Uses effective strain $\bar{\varepsilon}$ which includes shear contributions:
$$
\bar{\varepsilon} = \sqrt{\frac{2}{3}\boldsymbol{\varepsilon}' : \boldsymbol{\varepsilon}'}
$$
where $\boldsymbol{\varepsilon}'$ is the deviatoric strain tensor.

### Viscoelastic Materials

Shear strain may exhibit time-dependent behavior:
- Creep under constant [[Shear Stress]]
- Stress relaxation under constant shear strain
- Frequency-dependent [[Shear Modulus]] in dynamic loading

## Limitations and Considerations

### Small Strain Assumption

Linear shear strain definitions assume:
- Small displacement gradients ($|\partial u_i/\partial x_j| \ll 1$)
- Valid for $\gamma_{ij} \lesssim 0.05$ (5% shear strain)

### Finite Shear Strain

For large deformations, proper finite strain measures must be used:
- Green-Lagrange tensor: $E_{xy} = \frac{1}{2}\left( \frac{\partial u}{\partial Y} + \frac{\partial v}{\partial X} + \frac{\partial u}{\partial X}\frac{\partial u}{\partial Y} + \frac{\partial v}{\partial X}\frac{\partial v}{\partial Y} \right)$
- Almansi-Euler tensor
- Logarithmic (Hencky) strain

### Shear Locking in FEM

A numerical pathology where certain finite elements exhibit overly stiff behavior in bending due to spurious shear [[Strain Energy]]. Remedies include:
- Reduced integration
- Selective reduced integration
- Assumed natural strain (ANS) methods
- Discrete shear gap (DSG) technique

## Practical Applications

### Structural Engineering
- Analysis of shear walls and diaphragms
- Design of connections (bolts, welds) under shear
- Shear deformation in deep beams

### Geotechnical Engineering
- Shear strength of soils (Mohr-Coulomb criterion)
- Slope stability analysis
- Soil-structure interaction

### Manufacturing
- Metal forming processes (shearing, punching)
- Machining (chip formation involves shear)
- Composite material processing (shear between layers)

### Biomechanics
- Shear deformation in soft tissues
- Blood flow shear effects on vessel walls
- Bone response to shear loading

## Advanced Topics

### Micropolar (Cosserat) Continuum

Includes micro-rotations and couple stresses, with additional rotational [[degrees of freedom]] affecting shear strain interpretation.

### Strain Gradient Theories

Account for higher gradients of displacement, important at small scales where shear strain gradients influence material behavior.

### Shear Band Formation

Localization of shear strain into narrow bands, precursor to failure in many materials:
- Metals: [[Adiabatic Process]] shear bands
- Soils: shear bands in triaxial tests
- Polymers: shear yielding

## See Also

- [[Normal Strain]]
- [[Strain]]
- [[Shear Stress]]
- [[Shear Modulus]]
- [[Compatibility Equations]]
- [[Finite Element Method]]
- [[Timoshenko Beam Element]]
- [[Mohr's Circle for Strain]]
- [[Elasticity Theory]]
- [[Plasticity Theory]]
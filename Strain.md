#Space-Structures #Physics-Concept #TBD  
## Formal Definition

**Strain** is a dimensionless measure of deformation representing the relative displacement between material points in a continuum body. It quantifies how much a body deforms under applied forces, expressed as the ratio of change in length (for normal strain) or change in angle (for shear strain) to the original dimension. Strain is a fundamental kinematic quantity in [[Continuum Mechanics]] that characterizes the local geometric changes within a material, serving as the primary input to [[Constitutive Equations]] that relate deformation to stress.

## Mathematical Formulation

### Infinitesimal (Linear) Strain

For small deformations, the **infinitesimal strain tensor** $\boldsymbol{\varepsilon}$ is defined as the symmetric part of the displacement gradient:

$$
\boldsymbol{\varepsilon} = \frac{1}{2}(\nabla \mathbf{u} + (\nabla \mathbf{u})^T)
$$

In component form (Cartesian coordinates):

$$
\varepsilon_{ij} = \frac{1}{2}\left( \frac{\partial u_i}{\partial x_j} + \frac{\partial u_j}{\partial x_i} \right), \quad i,j = 1,2,3
$$

### Normal Strain

Normal strain measures elongation or contraction along coordinate axes:

$$
\varepsilon_{xx} = \frac{\partial u}{\partial x}, \quad \varepsilon_{yy} = \frac{\partial v}{\partial y}, \quad \varepsilon_{zz} = \frac{\partial w}{\partial z}
$$

**Engineering normal strain:** $e = \frac{\Delta L}{L_0}$ (change in length per original length)

### Shear Strain

Shear strain measures angular distortion:

$$
\gamma_{xy} = \frac{\partial u}{\partial y} + \frac{\partial v}{\partial x} = 2\varepsilon_{xy}
$$

(Note: Engineering shear strain $\gamma$ is twice the tensor component $\varepsilon_{xy}$)

## Finite Strain Measures

For large deformations, several strain measures are used:

### Green-Lagrange Strain Tensor

$$
\mathbf{E} = \frac{1}{2}(\mathbf{F}^T\mathbf{F} - \mathbf{I})
$$

where $\mathbf{F} = \frac{\partial \mathbf{x}}{\partial \mathbf{X}}$ is the deformation gradient, $\mathbf{x}$ is current position, $\mathbf{X}$ is reference position.

In component form:

$$
E_{ij} = \frac{1}{2}\left( \frac{\partial u_i}{\partial X_j} + \frac{\partial u_j}{\partial X_i} + \frac{\partial u_k}{\partial X_i} \frac{\partial u_k}{\partial X_j} \right)
$$

### Almansi-Euler Strain Tensor

$$
\mathbf{e} = \frac{1}{2}(\mathbf{I} - \mathbf{F}^{-T}\mathbf{F}^{-1})
$$

### Logarithmic (Hencky) Strain

For uniaxial deformation:

$$
\varepsilon_{\text{true}} = \ln\left(\frac{L}{L_0}\right)
$$

General 3D form via spectral decomposition of $\mathbf{F}$.

## Physical Interpretation

### Geometric Meaning

- **Normal strain:** Fractional change in length of a material fiber
  - Positive: Extension (tension)
  - Negative: Contraction ([[compression]])

- **Shear strain:** Change in angle between initially perpendicular material fibers
  - Positive: Angle decreases (typically < 90°)
  - Negative: Angle increases (typically > 90°)

### Volume Change

**Volumetric strain:** $\varepsilon_v = \varepsilon_{xx} + \varepsilon_{yy} + \varepsilon_{zz} = \text{tr}(\boldsymbol{\varepsilon})$

For incompressible materials: $\varepsilon_v = 0$

### Distortional (Deviatoric) Strain

The strain deviator representing shape change without volume change:

$$
\boldsymbol{\varepsilon}' = \boldsymbol{\varepsilon} - \frac{1}{3}\varepsilon_v\mathbf{I}
$$

## Strain Components in Different Coordinate Systems

### Cylindrical Coordinates $(r, \theta, z)$

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

## Strain Transformation Rules

### Coordinate Transformation

For rotation defined by transformation matrix $[a_{ij}]$:

$$
\varepsilon'_{ij} = a_{ik}a_{jl}\varepsilon_{kl}
$$

### Principal Strains

Eigenvalues of the strain tensor satisfy:

$$
\det(\boldsymbol{\varepsilon} - \varepsilon\mathbf{I}) = 0
$$

**[[Characteristic equation]]:**
$$
\varepsilon^3 - I_1\varepsilon^2 + I_2\varepsilon - I_3 = 0
$$

**Strain invariants:**
$$
\begin{aligned}
I_1 &= \varepsilon_{xx} + \varepsilon_{yy} + \varepsilon_{zz} \\
I_2 &= \varepsilon_{xx}\varepsilon_{yy} + \varepsilon_{yy}\varepsilon_{zz} + \varepsilon_{zz}\varepsilon_{xx} - \varepsilon_{xy}^2 - \varepsilon_{yz}^2 - \varepsilon_{zx}^2 \\
I_3 &= \det(\boldsymbol{\varepsilon})
\end{aligned}
$$

### Maximum Shear Strain

$$
\gamma_{\text{max}} = \varepsilon_{\text{max}} - \varepsilon_{\text{min}}
$$

Occurs at 45° to principal directions.

## Compatibility Conditions

For a strain field to be physically admissible (derivable from a continuous [[Displacement Field]]), it must satisfy the **Saint-Venant [[Compatibility Equations]]**:

$$
\nabla \times (\nabla \times \boldsymbol{\varepsilon})^T = \mathbf{0}
$$

In 2D, the single compatibility equation is:

$$
\frac{\partial^2 \varepsilon_{xx}}{\partial y^2} + \frac{\partial^2 \varepsilon_{yy}}{\partial x^2} = 2\frac{\partial^2 \varepsilon_{xy}}{\partial x \partial y}
$$

## Strain Rate and Deformation Rate

### [[Velocity]] Gradient

$$
\mathbf{L} = \nabla \mathbf{v} = \frac{\partial \mathbf{v}}{\partial \mathbf{x}}
$$

### Rate of Deformation Tensor

$$
\mathbf{D} = \frac{1}{2}(\mathbf{L} + \mathbf{L}^T)
$$

### Spin Tensor

$$
\mathbf{W} = \frac{1}{2}(\mathbf{L} - \mathbf{L}^T)
$$

## Measurement Techniques

### Experimental Methods

1. **Strain gauges:** Electrical resistance change with strain
   - Gauge factor: $GF = \frac{\Delta R/R}{\varepsilon}$
   - Rosette configurations for multi-axial strain

2. **Digital Image Correlation (DIC):** Optical measurement using pattern tracking

3. **Moiré interferometry:** Optical interference patterns

4. **Photoelasticity:** Birefringence in transparent materials

5. **Extensometers:** Mechanical displacement measurement

### Strain Calculation from Displacements

In [[Finite Element Analysis (FEA)]], strain is computed from nodal displacements:

$$
\boldsymbol{\varepsilon} = \mathbf{B} \mathbf{u}
$$

where $\mathbf{B}$ is the strain-displacement matrix.

## Applications

### Structural Analysis

- Stress calculation via constitutive laws
- Deflection and deformation analysis
- Buckling and stability calculations
- Fatigue life prediction

### Material Characterization

- Determination of elastic moduli
- Yield point identification
- Ductility measurement
- Creep and relaxation studies

### Geotechnical Engineering

- Settlement analysis
- Soil deformation under loads
- Rock mass behavior

### Biomechanics

- Bone and tissue deformation
- Implant design
- Injury mechanics

## Special Strain Measures

### Effective (Equivalent) Strain

**Von Mises effective strain (for plasticity):**
$$
\bar{\varepsilon} = \sqrt{\frac{2}{3}\boldsymbol{\varepsilon}' : \boldsymbol{\varepsilon}'}
$$

**Tresca effective strain:**
$$
\bar{\varepsilon} = \varepsilon_{\text{max}} - \varepsilon_{\text{min}}
$$

### Plastic Strain

In elastoplasticity, total strain is decomposed:

$$
\boldsymbol{\varepsilon} = \boldsymbol{\varepsilon}^e + \boldsymbol{\varepsilon}^p
$$

where $\boldsymbol{\varepsilon}^e$ is elastic (recoverable) and $\boldsymbol{\varepsilon}^p$ is plastic (permanent) strain.

### Thermal Strain

Due to temperature change $\Delta T$:

$$
\boldsymbol{\varepsilon}^{th} = \alpha \Delta T \mathbf{I}
$$

where $\alpha$ is coefficient of thermal expansion.

## Limitations and Approximations

### Small Strain Assumption

Infinitesimal strain theory assumes:
- Displacement gradients are small ($|\nabla \mathbf{u}| \ll 1$)
- Valid for strains typically < 5%
- Neglects geometric nonlinearity

### Large Strain Formulations

Required when:
- Large rotations or displacements
- Rubber-like materials (elastomers)
- Metal forming processes
- Biological tissues

### Objective Strain Rates

In large deformation, must use objective rates (Jaumann, Truesdell, Green-Naghdi) for [[Constitutive Equations]].

## Advanced Topics

### Strain Localization

- Shear bands in metals
- Necking in tension
- Localized deformation in soils

### Multi-scale Strain

- Microstructural strain heterogeneity
- Grain-level strains in polycrystals
- Atomic lattice strains

### Residual Strain

Strain remaining after external loads removed:
- Due to plastic deformation
- Manufacturing processes
- Thermal mismatch in composites

## See Also

- [[Stress Tensor]]
- [[Displacement Field]]
- [[Deformation Gradient]]
- [[Strain-Displacement Relations]]
- [[Compatibility Equations]]
- [[Constitutive Equations]]
- [[Finite Element Method]]
- [[Experimental Mechanics]]
- [[Elasticity Theory]]
- [[Plasticity Theory]]
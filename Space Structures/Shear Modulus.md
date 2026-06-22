## Formal Definition

The **Shear Modulus** (denoted as $G$, also known as the **modulus of rigidity**, **torsional modulus**, or **second Lamé constant** $\mu$) is a material property that quantifies the resistance to shear deformation. It represents the ratio of [[Shear Stress]] ($\tau$) to engineering shear strain ($\gamma$) in the linear elastic regime, defining the slope of the [[Shear Stress]]-shear strain curve in the elastic region. As one of the fundamental elastic constants, it characterizes a material's stiffness under shear loading and is a critical parameter in analyzing [[torsion]], transverse loading, and other shear-dominated deformation modes.

## Mathematical Formulation

### Definition

For a material in the linear elastic range subjected to pure shear:

$$
G = \frac{\tau}{\gamma}
$$

where:
- $G$ = shear modulus (Pa or psi)
- $\tau$ = [[Shear Stress]] (Pa or psi)
- $\gamma$ = engineering shear strain (dimensionless)

### [[Tensor]] Formulation

In three-dimensional linear elasticity, the shear modulus relates the deviatoric stress to the deviatoric strain. For an [[isotropic material]]:

$$
\sigma_{ij} = \lambda \varepsilon_{kk} \delta_{ij} + 2\mu \varepsilon_{ij}
$$

where:
- $\mu = G$ = shear modulus (second Lamé constant)
- $\lambda$ = first Lamé constant
- $\varepsilon_{kk}$ = volumetric strain (sum of diagonal strain components)
- $\delta_{ij}$ = [[Kronecker delta]]

Specifically for shear components ($i \neq j$):

$$
\sigma_{ij} = 2G \varepsilon_{ij} \quad \text{or} \quad \tau_{ij} = G \gamma_{ij}
$$

### Relationship to Other Elastic Constants

For isotropic linear elastic materials, the shear modulus is related to other fundamental elastic constants through the following equations:

**With [[Young's Modulus]] $E$ and [[Poisson's ratio]] $\nu$:**
$$
G = \frac{E}{2(1 + \nu)}
$$

**With bulk modulus $K$:**
$$
G = \frac{3K(1 - 2\nu)}{2(1 + \nu)} = \frac{3KE}{9K - E}
$$

**With [[Lamé constants]] $\lambda$ and $\mu$:**
$$
G = \mu
$$

**Inverse relations:**
$$
E = 2G(1 + \nu), \quad K = \frac{2G(1 + \nu)}{3(1 - 2\nu)}, \quad \nu = \frac{E}{2G} - 1
$$

### Range of Values

The shear modulus is always positive ($G > 0$) for stable materials. Thermodynamic stability requires:

$$
3K + 4G > 0 \quad \text{and} \quad G > 0
$$

which implies $-1 < \nu < 0.5$ for isotropic materials.

## Physical Interpretation

### Microscopic Basis

At the atomic/molecular level, the shear modulus represents the resistance to sliding of atomic planes or the distortion of molecular arrangements. It arises from:
- Interatomic bonding forces in crystalline solids
- Entropic resistance in polymer chains
- Microstructural constraints in composite materials

### Material Classification by Shear Modulus

**High Shear Modulus Materials ($G > 40 \, \text{GPa}$):**
- Diamond: ~478 GPa
- Tungsten: ~160 GPa
- Steel: ~79 GPa
- Titanium: ~41 GPa

**Moderate Shear Modulus Materials ($10 < G < 40 \, \text{GPa}$):**
- Aluminum: ~26 GPa
- Copper: ~44 GPa
- Glass: ~26 GPa
- Concrete: ~12 GPa

**Low Shear Modulus Materials ($G < 10 \, \text{GPa}$):**
- Wood (parallel to grain): ~0.5-10 GPa
- Plastics: ~0.5-3 GPa
- Rubber: ~0.0003-0.001 GPa
- Soft biological tissues: ~0.000001-0.00001 GPa

## Measurement Techniques

### Direct Methods

1. **[[Torsion]] Testing:**
   - Most direct measurement of $G$
   - Applying torque $T$ to cylindrical specimen
   - Measuring angle of twist $\phi$
   - For solid circular shaft: $G = \frac{2TL}{\pi R^4 \phi}$

2. **Simple Shear Testing:**
   - Applying pure shear load to thin-walled tube or rectangular specimen
   - Direct measurement of $\tau$ and $\gamma$

3. **Ultrasonic Methods:**
   - Measuring shear wave velocity $v_s$
   - $G = \rho v_s^2$, where $\rho$ is density
   - Non-destructive and applicable to small samples

### Indirect Methods

1. **From Other Elastic Constants:**
   - If $E$ and $\nu$ are known: $G = E/[2(1+\nu)]$
   - Requires separate measurement of [[Young's Modulus]] and [[Poisson's ratio]]

2. **Resonant Ultrasound Spectroscopy (RUS):**
   - Measuring natural frequencies of vibration
   - Solving inverse problem for elastic constants

3. **Nanoindentation:**
   - Measuring load-displacement curves
   - Extracting shear modulus from contact mechanics models

## Temperature and Strain Rate Dependence

### Temperature Effects

For most materials, shear modulus decreases with increasing temperature:

**Metals:**
$$
G(T) = G_0 \left[ 1 - \alpha_G (T - T_0) \right]
$$
where $\alpha_G$ is the temperature coefficient (typically 10⁻⁴ to 10⁻³ K⁻¹).

**Polymers:**
Exhibit significant temperature dependence near glass transition temperature $T_g$.

**Empirical Relation (Wachtman et al. for ceramics):**
$$
G(T) = G_0 - BT \exp(-T_0/T)
$$

### Strain Rate Dependence

- **Metals:** Relatively rate-independent at low temperatures
- **Polymers and soft materials:** Strong rate dependence (viscoelastic behavior)
- **High strain rates:** Can lead to apparent increase in shear modulus

## Applications in Engineering Analysis

### [[Torsion]] of Shafts

For circular shafts under torque $T$:

**[[Shear Stress]] distribution:**
$$
\tau(r) = \frac{Tr}{J}
$$

**Angle of twist:**
$$
\phi = \frac{TL}{GJ}
$$
where $J$ is polar moment of inertia.

### Beam Shear Deformation

**Timoshenko beam theory** includes shear deformation effects:

**Shear strain:**
$$
\gamma_{xz} = \frac{\partial w}{\partial x} - \theta_y
$$

**Shear force-shear strain relation:**
$$
V = kGA\gamma_{xz}
$$
where $k$ is shear correction factor (typically 5/6 for rectangular sections).

### Plate and Shell Analysis

**Mindlin-Reissner plate theory** includes transverse shear deformation:

**[[Shear Stress]] resultants:**
$$
Q_\alpha = \kappa G h \gamma_{\alpha 3}
$$
where $\kappa$ is shear correction factor, $h$ is thickness.

### Elastic Wave Propagation

**Shear wave velocity:**
$$
v_s = \sqrt{\frac{G}{\rho}}
$$

**Relation to seismic properties:**
- S-waves (secondary waves) are shear waves
- Used in geophysics to determine Earth's interior structure

## Anisotropic Materials

### General Anisotropy

For anisotropic materials, the shear modulus depends on direction and plane of shear:

**Generalized [[Hooke's Law]]:**
$$
\sigma_{ij} = C_{ijkl} \varepsilon_{kl}
$$

**Shear moduli** appear as components $C_{ijij}$ (no sum) for $i \neq j$.

### Orthotropic Materials

Three independent shear moduli:
- $G_{12}$: Shear in 1-2 plane
- $G_{23}$: Shear in 2-3 plane
- $G_{31}$: Shear in 3-1 plane

### Transversely Isotropic Materials

Two independent shear moduli:
- $G_{12}$: In-plane shear modulus
- $G_{23} = G_{31}$: Transverse shear modulus

## Limitations and Special Considerations

### Validity Range

1. **Linear Elastic Assumption:**
   - Valid only in elastic region (before yielding)
   - For metals, typically up to 0.2% offset strain

2. **Small Strain Assumption:**
   - Valid for engineering shear strains < 5%
   - Large deformations require finite strain measures

3. **Isotropic Assumption:**
   - Many materials are anisotropic (composites, crystals)
   - Direction-dependent shear moduli must be considered

### Temperature and Pressure Effects

**Pressure dependence:**
$$
\frac{dG}{dP} > 0 \quad \text{for most materials}
$$

**Pressure derivative:**
$$
G' = \frac{d \ln G}{d \ln \rho} \quad \text{typically 1-3}
$$

### Viscoelastic Materials

For time-dependent materials, the shear modulus becomes complex:

**Complex shear modulus:**
$$
G^*(\omega) = G'(\omega) + iG''(\omega)
$$
where:
- $G'$ = storage modulus (elastic response)
- $G''$ = loss modulus (viscous response)

## Special Cases

### Incompressible Materials ($\nu = 0.5$)

For incompressible materials (rubber, soft tissues):

$$
G = \frac{E}{3} \quad \text{and} \quad K \to \infty
$$

### Auxetic Materials ($\nu < 0$)

Materials with negative [[Poisson's ratio]] have unusual shear modulus relationships:

$$
G = \frac{E}{2(1+\nu)} > \frac{E}{2} \quad \text{for } \nu < 0
$$

### Porous Materials

Effective shear modulus depends on porosity $\phi$:

**Self-consistent approximation:**
$$
G_{\text{eff}} = G_0 \left(1 - \frac{15(1-\nu_0)}{7-5\nu_0} \phi\right)
$$

## Relationship to Material Strength

### Yield Criterion in Shear

**Tresca criterion:**
$$
\tau_{\text{yield}} = \frac{\sigma_y}{2}
$$

**Von Mises criterion:**
$$
\tau_{\text{yield}} = \frac{\sigma_y}{\sqrt{3}} \approx 0.577\sigma_y
$$

### Shear Strength vs. Shear Modulus

- **Shear modulus** measures stiffness (resistance to deformation)
- **Shear strength** measures load-bearing capacity before failure
- No direct proportionality between them
- Brittle materials can have high $G$ but low shear strength

## Advanced Topics

### Strain Gradient Elasticity

For very small scales (micron/nano), additional length-scale parameters modify shear response:

$$
\tau_{ij} = G\gamma_{ij} + l^2 \nabla^2 \gamma_{ij}
$$
where $l$ is material length scale parameter.

### Pressure-Dependent Shear Modulus

For soils and granular materials, shear modulus depends on confining pressure:

**Hardin-Black equation:**
$$
G = G_0 \left( \frac{\sigma_m'}{\sigma_0'} \right)^n
$$
where $\sigma_m'$ is mean effective stress, $\sigma_0'$ is reference stress, $n$ is exponent (typically 0.5).

### Shear Modulus Degradation

Under cyclic loading, shear modulus can degrade:

**Strain-dependent shear modulus:**
$$
\frac{G}{G_{\text{max}}} = \frac{1}{1 + \gamma/\gamma_r}
$$
where $\gamma_r$ is reference shear strain.

## Practical Applications

### Design Calculations

1. **Shaft Design:**
   - Determining torsional stiffness
   - Calculating critical speeds

2. **Vibration Isolation:**
   - Designing rubber mounts and bearings
   - [[Natural Frequency]] calculations

3. **Earthquake Engineering:**
   - Soil-structure interaction analysis
   - Site response studies

4. **Composite Material Design:**
   - Optimizing fiber orientation for shear resistance
   - Interlaminar shear strength calculations

### Material Selection

Criteria for selecting materials based on shear modulus:
- **High G:** Precision instruments, machine tools, structural elements
- **Moderate G:** General structural applications
- **Low G:** Vibration isolation, flexible couplings, seals

## See Also

- [[Young's Modulus]]
- [[Poisson's Ratio]]
- [[Bulk Modulus]]
- [[Torsion]]
- [[Shear Stress]]
- [[Shear Strain]]
- [[Linear Elasticity]]
- [[Material Properties]]
- [[Anisotropic Elasticity]]
- [[Viscoelasticity]]
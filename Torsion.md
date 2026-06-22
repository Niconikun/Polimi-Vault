#Space-Structures #DONE
## Formal Definition

**Torsion** is a mode of structural deformation in which a structural member is subjected to a twisting moment (torque) about its longitudinal axis, resulting in shear stresses and angular displacement along the member. This loading condition induces a rotational deformation where each cross-section rotates relative to adjacent cross-sections, producing shear strains that vary linearly from the center (neutral axis) in prismatic members with circular cross-sections, and more complex distributions in non-circular sections.

## Mathematical Formulation

### Fundamental Relationships

For a prismatic shaft of circular cross-section subjected to a torque $T$:

#### [[Shear Stress]] Distribution

The [[Shear Stress]] $\tau$ at a radial distance $r$ from the center is given by:

$$
\tau(r) = \frac{Tr}{J}
$$

where:
- $T$ = applied torque (N·m or lb·in)
- $r$ = radial distance from the center (m or in)
- $J$ = polar moment of inertia of the cross-section (m⁴ or in⁴)

For a solid circular shaft of radius $R$:
$$
J = \frac{\pi R^4}{2} = \frac{\pi D^4}{32}
$$

For a hollow circular shaft with outer radius $R_o$ and inner radius $R_i$:
$$
J = \frac{\pi}{2}(R_o^4 - R_i^4) = \frac{\pi}{32}(D_o^4 - D_i^4)
$$

#### Angle of Twist

The relative angle of twist $\phi$ between two cross-sections separated by distance $L$ is:

$$
\phi = \frac{TL}{GJ}
$$

where:
- $\phi$ = angle of twist (radians)
- $L$ = length of shaft between cross-sections (m or in)
- $G$ = [[Shear Modulus]] of the material (Pa or psi)
- $J$ = polar moment of inertia

For a shaft with varying torque, cross-section, or material properties along its length:

$$
\phi = \int_0^L \frac{T(x)}{G(x)J(x)} dx
$$

### Shear Strain Relationship

The shear strain $\gamma$ at a point is related to the angle of twist per unit length $\theta = \frac{d\phi}{dx}$:

$$
\gamma(r) = r \frac{d\phi}{dx} = r\theta
$$

Using [[Hooke's Law]] in shear ($\tau = G\gamma$), we recover the [[Shear Stress]] formula.

## Torsion of Non-Circular Sections

### General Torsion Theory (Saint-Venant)

For non-circular prismatic bars, the torsion problem is governed by the Poisson equation:

$$
\nabla^2 \psi = -2G\theta \quad \text{in the cross-section } \Omega
$$

with boundary condition $\psi = 0$ on $\partial\Omega$, where $\psi(x,y)$ is the Prandtl stress function.

The torque is given by:

$$
T = 2\int_\Omega \psi \, dA
$$

and the shear stresses are:

$$
\tau_{zx} = \frac{\partial \psi}{\partial y}, \quad \tau_{zy} = -\frac{\partial \psi}{\partial x}
$$

### Torsion Constant

For any cross-section, we define the torsion constant $J_t$ (not to be confused with polar moment of inertia) such that:

$$
\phi = \frac{TL}{GJ_t}
$$

where $J_t$ depends on the cross-section geometry.

### Common Non-Circular Sections

#### Elliptical Cross-Section

For an ellipse with semi-axes $a$ and $b$ ($a \geq b$):

- Torsion constant: $J_t = \frac{\pi a^3 b^3}{a^2 + b^2}$
- Maximum [[Shear Stress]] (at ends of minor axis): $\tau_{\text{max}} = \frac{2T}{\pi ab^2}$

#### Rectangular Cross-Section

For a rectangle with width $b$ and depth $h$ ($h \geq b$):

- Torsion constant: $J_t = \beta h b^3$
- Maximum [[Shear Stress]]: $\tau_{\text{max}} = \frac{T}{\alpha h b^2}$

where $\alpha$ and $\beta$ are dimensionless coefficients depending on $h/b$:

| $h/b$ | $\alpha$ | $\beta$ |
|----------|-------------|------------|
| 1.0      | 0.208       | 0.141      |
| 1.5      | 0.231       | 0.196      |
| 2.0      | 0.246       | 0.229      |
| 3.0      | 0.267       | 0.263      |
| 5.0      | 0.291       | 0.291      |
| 10.0     | 0.312       | 0.312      |
| ∞        | 0.333       | 0.333      |

#### Thin-Walled Sections

**Closed Thin-Walled Sections** (e.g., tubes):
- Shear flow: $q = \tau t = \text{constant}$
- Bredt-Batho formula: $\tau = \frac{T}{2A_e t}$
- Angle of twist: $\phi = \frac{TL}{4A_e^2 G} \oint \frac{ds}{t}$
where $A_e$ is the area enclosed by the median line, $t$ is wall thickness, and the integral is around the perimeter.

**Open Thin-Walled Sections** (e.g., I-beams, channels):
- Torsion constant: $J_t \approx \frac{1}{3} \sum h_i t_i^3$ for sections composed of thin rectangles
- Maximum [[Shear Stress]]: $\tau_{\text{max}} = \frac{T t_{\text{max}}}{J_t}$

## Warping in Non-Circular Torsion

### Warping Displacement

For non-circular sections, plane sections do not remain plane (Saint-Venant's warping). The out-of-plane displacement $w(x,y)$ (warping function) satisfies:

$$
\nabla^2 w = 0 \quad \text{in } \Omega
$$

with boundary condition $\frac{\partial w}{\partial n} = y n_x - x n_y$ on $\partial\Omega$, where $(n_x, n_y)$ is the unit outward normal.

The warping displacement is given by:

$$
w(x,y) = \theta \omega(x,y)
$$

where $\omega(x,y)$ is the normalized warping function.

### Constrained Warping (Non-uniform Torsion)

When warping is restrained (e.g., fixed ends, non-uniform torque), additional normal stresses $\sigma_w$ and shear stresses $\tau_w$ develop. This is described by the **Vlasov theory of thin-walled beams**:

**Warping normal stress:**
$$
\sigma_w = E \omega_n \frac{d^2 \phi}{dx^2}
$$

**Warping [[Shear Stress]]:**
$$
\tau_w = -\frac{E S_\omega}{t} \frac{d^3 \phi}{dx^3}
$$

where:
- $\omega_n$ is the normalized unit warping function
- $S_\omega$ is the warping statical moment
- $E$ is [[Young's Modulus]]

The governing equation becomes:
$$
E \Gamma \frac{d^4 \phi}{dx^4} - G J_t \frac{d^2 \phi}{dx^2} = m(x)
$$

where:
- $\Gamma$ is the warping constant (warping moment of inertia)
- $m(x)$ is distributed torque along the member

## Energy Considerations

### [[Strain Energy]] in Torsion

For uniform torsion (Saint-Venant torsion):

**[[Strain Energy]] per unit length:**
$$
U = \frac{1}{2} G J_t \left( \frac{d\phi}{dx} \right)^2 = \frac{T^2}{2GJ_t}
$$

**Total [[Strain Energy]] for length $L$:**
$$
U_{\text{total}} = \int_0^L \frac{T(x)^2}{2GJ_t(x)} dx
$$

For non-uniform torsion (including warping):

$$
U = \frac{1}{2} \int_0^L \left[ E \Gamma \left( \frac{d^2 \phi}{dx^2} \right)^2 + G J_t \left( \frac{d\phi}{dx} \right)^2 \right] dx
$$

## Failure Theories for Torsion

### Ductile Materials

**Maximum [[Shear Stress]] criterion (Tresca):**
$$
\tau_{\text{max}} = \frac{\sigma_y}{2}
$$
where $\sigma_y$ is yield strength in tension.

**Distortion energy criterion (Von Mises):**
$$
\tau_{\text{max}} = \frac{\sigma_y}{\sqrt{3}} \approx 0.577\sigma_y
$$

### Brittle Materials

**Maximum normal stress criterion:**
Failure occurs when maximum principal stress reaches ultimate tensile strength.

**Mohr's theory:** Accounts for different strengths in tension and [[compression]].

## Design Considerations

### Shaft Design

**Power transmission shafts:**
Power $P$ (in watts) transmitted by a shaft rotating at angular speed $\omega$ (rad/s) or $N$ (rpm):

$$
P = T\omega = \frac{2\pi NT}{60}
$$

Design torque: $T_{\text{design}} = K \cdot T_{\text{nominal}}$, where $K$ is a service factor accounting for shock, fatigue, etc.

**Allowable [[Shear Stress]]:**
$$
\tau_{\text{allow}} = \frac{\tau_y}{n} \quad \text{or} \quad \tau_{\text{allow}} = \frac{\tau_u}{n}
$$
where $n$ is factor of safety.

**Shaft diameter (solid circular shaft):**
$$
d = \left( \frac{16T}{\pi \tau_{\text{allow}}} \right)^{1/3}
$$

### Combined Loading

Shafts often experience combined torsion and bending:

**Equivalent torque** (for design based on maximum [[Shear Stress]] theory):
$$
T_e = \sqrt{M^2 + T^2}
$$

**Equivalent bending moment:**
$$
M_e = \frac{1}{2} \left( M + \sqrt{M^2 + T^2} \right)
$$

where $M$ is bending moment and $T$ is torque.

## Experimental Methods

### Torque Measurement

1. **Torque sensors:** Strain gauge-based, optical, or magnetic.
2. **Reaction torque:** Measure reaction at support bearings.
3. **Twist measurement:** Optical encoders, proximity sensors.

### Material Property Determination

**Torsion tests** are used to determine [[Shear Modulus]] $G$ and shear strength:

1. **[[Shear Modulus]]:**
   $$
   G = \frac{TL}{J\phi}
   $$
   from measured torque and angle of twist.

2. **Shear yield strength:** From torque at onset of yielding.

3. **[[Shear Stress]]-strain curve:** Obtained from torsion test.

## Applications

### Mechanical Systems
- Power transmission shafts in vehicles, machinery
- Drive shafts, propeller shafts
- Tool shanks, spindles

### Structural Engineering
- Torsional bracing in buildings
- Curved bridge girders
- Helical staircases

### Aerospace
- Aircraft wing torsion boxes
- Helicopter rotor shafts
- Control surface linkages

### Biomechanics
- Torsional loading of bones
- Prosthetic joint design
- Dental implant analysis

## Advanced Topics

### Elastic-Plastic Torsion

For materials exhibiting plastic behavior under torsion:

**Elastic core radius** $r_c$ when yielding begins at outer radius:
$$
r_c = \frac{\tau_y J}{T} \quad \text{(for circular shafts)}
$$

**Fully plastic torque:**
$$
T_p = \frac{2\pi R^3}{3} \tau_y \quad \text{(solid circular shaft)}
$$

### Anisotropic Materials

For materials with different properties in different directions (composites, crystals), the torsion response depends on material orientation. The governing equations become more complex, involving multiple material constants.

### Dynamic Torsion

**Torsional vibrations:**
Governing equation for a uniform shaft:
$$
\frac{\partial^2 \phi}{\partial t^2} = c^2 \frac{\partial^2 \phi}{\partial x^2}, \quad c = \sqrt{\frac{G}{\rho}}
$$
where $\rho$ is density, $c$ is wave speed.

**Natural frequencies** for a shaft with boundary conditions (fixed-free, fixed-fixed, etc.).

### Thermal Effects

Temperature changes can induce thermal stresses in constrained torsional members. For a shaft constrained against rotation, a temperature change $\Delta T$ induces torque:
$$
T = G J_t \alpha \Delta T \frac{L}{L} = G J_t \alpha \Delta T
$$
where $\alpha$ is coefficient of thermal expansion.

## See Also

- [[Shear Stress]]
- [[Shear Strain]]
- [[Polar Moment of Inertia]]
- [[Saint-Venant Principle]]
- [[Elasticity Theory]]
- [[Structural Dynamics]]
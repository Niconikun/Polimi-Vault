## Formal Definition

**Plate Theory** encompasses a collection of mathematical models and analytical frameworks developed to describe the mechanical behavior of thin, flat structural elements subjected to transverse and in-plane loads. These theories simplify the three-dimensional [[Continuum Mechanics]] problem to two dimensions by making specific kinematic assumptions about the deformation through the thickness, enabling efficient analysis of bending, vibration, buckling, and stress distribution in plate structures.

## Historical Development

### Chronological Evolution
- **1788:** Euler's early work on elastic surfaces
- **1811:** Sophie Germain's derivation of plate equation (won French Academy prize)
- **1850:** Kirchhoff's rigorous formulation of thin plate theory
- **1888:** Love's extension to include in-plane forces
- **1945:** Reissner's inclusion of transverse shear deformation
- **1951:** Mindlin's independent development of shear-deformable plate theory
- **1960s:** Development of finite plate elements based on these theories

## Fundamental Concepts

### Geometric Definition
A plate is a three-dimensional body characterized by:
- **Mid-surface:** Plane equidistant from top and bottom surfaces
- **Thickness (h):** Small compared to in-plane dimensions (typically h/L < 1/20 for thin plates)
- **Planar Domain (Ω):** Area of the mid-surface
- **Boundary (Γ):** Edge of the plate with prescribed boundary conditions

### Classification Criteria
1. **Thickness Ratio:** 
   - Thin plates: h/L < 1/20 (Kirchhoff-Love theory)
   - Moderately thick: 1/20 < h/L < 1/5 (Mindlin-Reissner theory)
   - Thick plates: h/L > 1/5 (require 3D elasticity or higher-order theories)

2. **Deformation Magnitude:**
   - Small deflection theory (linear)
   - Large deflection theory (geometrically nonlinear)

3. **Material Behavior:**
   - Isotropic, homogeneous
   - Orthotropic, anisotropic
   - Composite, layered

## Kinematic Foundations

### Kirchhoff-Love Plate Theory (Classical Plate Theory)

#### Fundamental Hypotheses
1. **Straight Normal Hypothesis:** Lines initially straight and perpendicular to the mid-surface remain straight and perpendicular to the deformed mid-surface.
2. **Constant Thickness:** The plate thickness remains unchanged during deformation.
3. **Negligible Transverse Effects:**
   - Transverse [[normal stress]]: σₓₓ ≈ 0
   - Transverse shear strains: γₓz = γᵧz = 0

#### [[Displacement Field]]
$$
\begin{aligned}
u(x,y,z) &= u_0(x,y) - z \frac{\partial w}{\partial x} \\
v(x,y,z) &= v_0(x,y) - z \frac{\partial w}{\partial y} \\
w(x,y,z) &= w_0(x,y)
\end{aligned}
$$

#### Strain Components
**Membrane strains:**
$$
\boldsymbol{\varepsilon}_m = 
\begin{Bmatrix}
\varepsilon_x^0 \\ \varepsilon_y^0 \\ \gamma_{xy}^0
\end{Bmatrix}
= 
\begin{Bmatrix}
\frac{\partial u_0}{\partial x} \\
\frac{\partial v_0}{\partial y} \\
\frac{\partial u_0}{\partial y} + \frac{\partial v_0}{\partial x}
\end{Bmatrix}
$$

**[[Bending]] curvatures:**
$$
\boldsymbol{\kappa} = 
\begin{Bmatrix}
\kappa_x \\ \kappa_y \\ \kappa_{xy}
\end{Bmatrix}
= 
\begin{Bmatrix}
-\frac{\partial^2 w}{\partial x^2} \\
-\frac{\partial^2 w}{\partial y^2} \\
-2\frac{\partial^2 w}{\partial x \partial y}
\end{Bmatrix}
$$

**Total strains:**
$$
\boldsymbol{\varepsilon} = \boldsymbol{\varepsilon}_m + z\boldsymbol{\kappa}
$$

### Mindlin-Reissner Plate Theory (First-Order Shear Deformation Theory)

#### Modified Hypotheses
1. **Straight but Not Normal:** Lines initially straight and perpendicular to the mid-surface remain straight but not necessarily perpendicular to the deformed mid-surface.
2. **Included Shear Deformation:** Transverse shear strains are constant through thickness.
3. **Shear Correction:** Requires shear correction factor κ to account for non-uniform shear distribution.

#### [[Displacement Field]]
$$
\begin{aligned}
u(x,y,z) &= u_0(x,y) + z\theta_y(x,y) \\
v(x,y,z) &= v_0(x,y) - z\theta_x(x,y) \\
w(x,y,z) &= w_0(x,y)
\end{aligned}
$$
where θₓ and θᵧ are independent rotations.

#### Strain Components
**[[Bending]] curvatures:**
$$
\boldsymbol{\kappa} = 
\begin{Bmatrix}
\frac{\partial \theta_y}{\partial x} \\
-\frac{\partial \theta_x}{\partial y} \\
\frac{\partial \theta_y}{\partial y} - \frac{\partial \theta_x}{\partial x}
\end{Bmatrix}
$$

**Transverse shear strains:**
$$
\boldsymbol{\gamma} = 
\begin{Bmatrix}
\gamma_{xz} \\ \gamma_{yz}
\end{Bmatrix}
= 
\begin{Bmatrix}
\frac{\partial w}{\partial x} + \theta_y \\
\frac{\partial w}{\partial y} - \theta_x
\end{Bmatrix}
$$

## Constitutive Relations

### Stress Resultants

#### Force and Moment Definitions
**Membrane forces (per unit length):**
$$
\begin{aligned}
N_x &= \int_{-h/2}^{h/2} \sigma_x \, dz \\
N_y &= \int_{-h/2}^{h/2} \sigma_y \, dz \\
N_{xy} &= \int_{-h/2}^{h/2} \tau_{xy} \, dz
\end{aligned}
$$

**Bending moments (per unit length):**
$$
\begin{aligned}
M_x &= \int_{-h/2}^{h/2} \sigma_x z \, dz \\
M_y &= \int_{-h/2}^{h/2} \sigma_y z \, dz \\
M_{xy} &= \int_{-h/2}^{h/2} \tau_{xy} z \, dz
\end{aligned}
$$

**Transverse shear forces (per unit length):**
$$
\begin{aligned}
Q_x &= \int_{-h/2}^{h/2} \tau_{xz} \, dz \\
Q_y &= \int_{-h/2}^{h/2} \tau_{yz} \, dz
\end{aligned}
$$

### [[Isotropic Material]] Relations

#### For Kirchhoff-Love Theory
$$
\begin{Bmatrix}
N \\ M
\end{Bmatrix}
= 
\begin{bmatrix}
\mathbf{A} & \mathbf{0} \\
\mathbf{0} & \mathbf{D}
\end{bmatrix}
\begin{Bmatrix}
\boldsymbol{\varepsilon}_m \\ \boldsymbol{\kappa}
\end{Bmatrix}
$$

where:
- **Extensional stiffness:** 
$$
\mathbf{A} = \frac{Eh}{1-\nu^2}
\begin{bmatrix}
1 & \nu & 0 \\
\nu & 1 & 0 \\
0 & 0 & \frac{1-\nu}{2}
\end{bmatrix}$$
- **Bending stiffness:** 
$$
\mathbf{D} = \frac{Eh^3}{12(1-\nu^2)}
\begin{bmatrix}
1 & \nu & 0 \\
\nu & 1 & 0 \\
0 & 0 & \frac{1-\nu}{2}
\end{bmatrix}$$

#### For Mindlin-Reissner Theory
$$
\begin{Bmatrix}
N \\ M \\ Q
\end{Bmatrix}
= 
\begin{bmatrix}
\mathbf{A} & \mathbf{0} & \mathbf{0} \\
\mathbf{0} & \mathbf{D} & \mathbf{0} \\
\mathbf{0} & \mathbf{0} & \mathbf{A}_s
\end{bmatrix}
\begin{Bmatrix}
\boldsymbol{\varepsilon}_m \\ \boldsymbol{\kappa} \\ \boldsymbol{\gamma}
\end{Bmatrix}
$$

where:
- **Shear stiffness:** $$\mathbf{A}_s = \kappa Gh 
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix} = \frac{\kappa Eh}{2(1+\nu)} 
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}$$
- **Shear correction factor:** Typically κ = 5/6 for homogeneous sections

## Governing Equations

### [[Equilibrium Equations]]

#### For Kirchhoff-Love Plates
**Force equilibrium:**
$$
\begin{aligned}
\frac{\partial N_x}{\partial x} + \frac{\partial N_{xy}}{\partial y} + p_x &= 0 \\
\frac{\partial N_{xy}}{\partial x} + \frac{\partial N_y}{\partial y} + p_y &= 0 \\
\frac{\partial Q_x}{\partial x} + \frac{\partial Q_y}{\partial y} + q &= 0
\end{aligned}
$$

**Moment equilibrium:**
$$
\begin{aligned}
\frac{\partial M_x}{\partial x} + \frac{\partial M_{xy}}{\partial y} - Q_x &= 0 \\
\frac{\partial M_{xy}}{\partial x} + \frac{\partial M_y}{\partial y} - Q_y &= 0
\end{aligned}
$$

**Combined governing equation for bending (for constant D):**
$$
D\nabla^4 w = q - \left(N_x \frac{\partial^2 w}{\partial x^2} + 2N_{xy} \frac{\partial^2 w}{\partial x \partial y} + N_y \frac{\partial^2 w}{\partial y^2}\right)
$$
where $\nabla^4 = \frac{\partial^4}{\partial x^4} + 2\frac{\partial^4}{\partial x^2 \partial y^2} + \frac{\partial^4}{\partial y^4}$ is the biharmonic operator.

#### For Mindlin-Reissner Plates
Three coupled partial differential equations:
$$
\begin{aligned}
D\left(\frac{\partial^2 \theta_x}{\partial x^2} + \frac{1-\nu}{2}\frac{\partial^2 \theta_x}{\partial y^2} + \frac{1+\nu}{2}\frac{\partial^2 \theta_y}{\partial x \partial y}\right) - \kappa Gh\left(\theta_x + \frac{\partial w}{\partial y}\right) &= 0 \\
D\left(\frac{\partial^2 \theta_y}{\partial y^2} + \frac{1-\nu}{2}\frac{\partial^2 \theta_y}{\partial x^2} + \frac{1+\nu}{2}\frac{\partial^2 \theta_x}{\partial x \partial y}\right) - \kappa Gh\left(\theta_y - \frac{\partial w}{\partial x}\right) &= 0 \\
\kappa Gh\left(\nabla^2 w + \frac{\partial \theta_y}{\partial x} - \frac{\partial \theta_x}{\partial y}\right) + q &= 0
\end{aligned}
$$

## Boundary Conditions

### Common Support Conditions

1. **Clamped (Fixed) Edge:**
   - Kirchhoff: $w = 0$, $\frac{\partial w}{\partial n} = 0$
   - Mindlin: $w = 0$, $\theta_n = 0$, $\theta_s = 0$

2. **Simply Supported Edge:**
   - Hard support: $w = 0$, $M_n = 0$
   - Soft support: $w = 0$, $\theta_s = 0$, $M_n = 0$

3. **Free Edge:**
   - Kirchhoff: $M_n = 0$, $V_n = Q_n + \frac{\partial M_{ns}}{\partial s} = 0$
   - Mindlin: $M_n = 0$, $M_{ns} = 0$, $Q_n = 0$

4. **Elastically Supported:**
   - Translational spring: $V_n = -k_t w$
   - Rotational spring: $M_n = -k_r \theta_n$

## Specialized Theories and Extensions

### Higher-Order Shear Deformation Theories
1. **Third-Order Theory (Reddy):** Parabolic [[Shear Stress]] distribution
2. **Layerwise Theory:** Independent displacement fields per layer
3. **Zig-Zag Theory:** Accounts for slope discontinuity at layer interfaces

### Composite Plate Theories
1. **Classical Lamination Theory (CLT):** Extension of Kirchhoff to laminates
2. **First-Order Shear Deformation Theory (FSDT):** Extension of Mindlin to laminates
3. **Higher-Order Lamination Theories:** More accurate through-thickness variation

### Geometrically Nonlinear Theories
1. **Von Kármán Plate Theory:** Moderately large deflections
2. **Donnell-Mushtari-Vlasov Theory:** For shallow shells
3. **Large Rotation Theories:** Including finite rotations

## Analytical Solution Methods

### Exact Solutions
1. **Navier Solution:** Double sine series for simply supported rectangular plates
2. **Levy Solution:** Single series for two opposite edges simply supported
3. **Bessel Functions:** For circular and annular plates

### Approximate Methods
1. **Ritz Method:** Energy-based approximation
2. **[[Galerkin Method]]:** Weighted residual approach
3. **Finite Difference Method:** Direct discretization of PDEs
4. **[[Finite Element Method]]:** Numerical discretization

## Dimensionless Parameters

### Key Ratios
1. **Aspect Ratio:** $a/b$ (length/width)
2. **Thickness Ratio:** $h/a$ or $h/b$
3. **Loading Parameter:** $qa^4/(Eh^4)$
4. **Shear Parameter:** For Mindlin plates, $\frac{D}{\kappa Gha^2}$

### Regime Classification
1. **Thin Plate Regime:** $h/L < 1/20$, Kirchhoff theory applicable
2. **Moderate Thickness:** $1/20 < h/L < 1/5$, Mindlin theory required
3. **Thick Plate:** $h/L > 1/5$, higher-order or 3D theory needed

## Applications and Limitations

### Practical Applications
1. **Structural Engineering:** Floor slabs, bridge decks, shear walls
2. **Aerospace:** Aircraft skin panels, wing sections
3. **Marine:** Ship hull plating, bulkheads
4. **Mechanical:** Machine bases, covers, heat exchangers
5. **Microsystems:** MEMS devices, semiconductor wafers

### Theory Limitations
1. **Kirchhoff-Love Theory:**
   - Neglects shear deformation (inaccurate for thick plates)
   - Overpredicts natural frequencies
   - C¹ continuity requirement in FEM
   - Cannot capture thickness-stretch modes

2. **Mindlin-Reissner Theory:**
   - Requires shear correction factor
   - Assumes constant shear strain (violates traction-free conditions)
   - Shear locking in thin plate limit
   - May overestimate deflections for very thick plates

## Advanced Topics

### Dynamic Behavior
1. **Free Vibration:** Natural frequencies and mode shapes
2. **Forced Vibration:** Response to dynamic loading
3. **Wave Propagation:** High-frequency behavior

### Stability Analysis
1. **Buckling:** Critical loads under in-plane [[compression]]
2. **Post-Buckling:** Behavior beyond critical load
3. **Vibration-Buckling Interaction:** Dynamic stability

### Fracture and Damage
1. **Stress Concentration:** Around holes and cutouts
2. **Crack Propagation:** Fracture mechanics of plates
3. **Damage Tolerance:** Progressive damage analysis

## See Also

- [[Kirchhoff Plate Element (Kirchhoff-Love)]]
- [[Mindlin Plate Element (Mindlin-Reissner)]]
- [[Shell Theory Fundamentals]]
- [[Elasticity Theory]]
- [[Finite Element Method]]
- [[Composite Materials]]
- [[Structural Mechanics]]
- [[Variational Methods in Mechanics]]
- [[Plate and Shell Vibrations]]
- [[Buckling of Plates and Shells]]
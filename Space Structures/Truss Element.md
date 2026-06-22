## Formal Definition

A **Truss Element** is a one-dimensional, two-node finite element used to model slender structural members that transmit axial loads only. It is based on the assumption that the element can sustain solely tensile and compressive forces along its longitudinal axis, with no resistance to bending, shear, or [[torsion]]. The element is characterized by its cross-sectional area, material properties ([[Young's Modulus]]), and initial length, and it is capable of large displacements but small strains.

## Mathematical Formulation

### Kinematic Assumptions

1. **Uniaxial [[Stress Tensor]] State:** Only the axial [[Stress Tensor]] component is non-zero.
2. **Constant [[Strain]]:** For a linear truss element, the axial [[strain]] is assumed constant over the element length.
3. **Small Strains:** The element undergoes small axial strains, though finite displacements may be considered in geometric nonlinear formulations.
4. **Pin-Jointed Connections:** Moments are not transmitted between elements; only axial forces are transferred at the nodes.

### Nodal [[Degrees of Freedom]]

In the local coordinate system (along the element axis), each node has one axial displacement degree of freedom (DOF). For a two-node truss element in 1D:
- **Local DOFs:** \( \mathbf{a}^e = [u_1, u_2]^T \)

In global coordinates (2D or 3D), each node has two or three translational DOFs. A 2D truss element has:
- **Global DOFs:** \( \mathbf{a}^e = [u_1, v_1, u_2, v_2]^T \)

### Strain-Displacement Relationship

The axial (engineering) strain is given by:
$$ \varepsilon = \frac{du}{dx} $$
For the linear [[Displacement Field]] \( u(x) = N_1 u_1 + N_2 u_2 \), where \( N_1 = 1 - \frac{x}{L} \) and \( N_2 = \frac{x}{L} \), the strain is constant:
$$ \varepsilon = \frac{u_2 - u_1}{L} = \mathbf{B} \mathbf{a}^e $$
where \( \mathbf{B} = \left[ -\frac{1}{L}, \frac{1}{L} \right] \) in local coordinates.

### [[Stress Tensor]]-Strain Relationship

Assuming linear elastic material behavior ([[Hooke's Law]]):
$$ \sigma = E \varepsilon $$
where \( E \) is [[Young's Modulus]].

### Element Stiffness Matrix

#### Local Stiffness Matrix (1D)
Derived from the [[Principle of Virtual Work]] or minimum potential energy:
$$ \mathbf{k}^e = \int_0^L \mathbf{B}^T E A \, \mathbf{B} \, dx = \frac{EA}{L} \begin{bmatrix} 1 & -1 \\ -1 & 1 \end{bmatrix} $$
where \( A \) is the cross-sectional area.

#### Global Stiffness Matrix (2D/3D)
Transformation from local to global coordinates via a rotation matrix \( \mathbf{T} \):
$$ \mathbf{K}^e = \mathbf{T}^T \mathbf{k}^e \mathbf{T} $$
For a 2D truss element oriented at an angle \( \theta \) from the global x-axis:
$$ \mathbf{T} = \begin{bmatrix} \cos\theta & \sin\theta & 0 & 0 \\ 0 & 0 & \cos\theta & \sin\theta \end{bmatrix} $$
The 2D global stiffness matrix becomes:
$$ \mathbf{K}^e = \frac{EA}{L} \begin{bmatrix} c^2 & cs & -c^2 & -cs \\ cs & s^2 & -cs & -s^2 \\ -c^2 & -cs & c^2 & cs \\ -cs & -s^2 & cs & s^2 \end{bmatrix} $$
where \( c = \cos\theta \) and \( s = \sin\theta \).

### Element Force Vector

For constant distributed [[axial load]] \( q \) (force per unit length):
$$ \mathbf{f}^e = \int_0^L \mathbf{N}^T q \, dx = \frac{qL}{2} \begin{bmatrix} 1 \\ 1 \end{bmatrix} $$
in local coordinates. Thermal loads due to temperature change \( \Delta T \) and coefficient of thermal expansion \( \alpha \) are:
$$ \mathbf{f}_{th}^e = EA \alpha \Delta T \begin{bmatrix} -1 \\ 1 \end{bmatrix} $$

## Key Properties

1. **Uniaxial Load Carrying:** Only axial forces (tension/[[compression]]) are developed.
2. **Geometric Stiffness:** In geometric nonlinear analysis (e.g., buckling), an additional geometric stiffness matrix accounts for the effect of axial force on bending stiffness.
3. **Material Nonlinearity:** Can be extended to nonlinear material behavior (plasticity, hyperelasticity).
4. **Isoparametric Formulation:** Higher-order truss elements with more nodes and quadratic/cubic displacement fields can be formulated using isoparametric mapping.

## Applications

1. **Planar and Space Trusses:** Roof trusses, bridges, transmission towers.
2. **Component in Frame Structures:** Combined with beam elements to model frames with axial-bending interaction.
3. **Cable Structures:** As an approximation for cables under tension (no [[compression]] allowed).
4. **Supporting Members:** Bracing elements in buildings and mechanical systems.

## Limitations

1. **No Bending or Shear:** Cannot model moments or transverse shear forces; additional elements (beams, frames) are required for such effects.
2. **Pin-Jointed Assumption:** Real connections often transmit some moment, leading to secondary bending stresses.
3. **Buckling:** Linear truss elements do not account for buckling; eigenvalue analysis or nonlinear analysis is required.
4. **Large Displacements:** Linear formulation is limited to small displacements; corotational or total Lagrangian formulations are needed for large rotations.

## Advanced Formulations

1. **Nonlinear Geometric Analysis:** Using the corotational formulation or total Lagrangian formulation to account for large displacements and rotations.
2. **Elastoplastic Behavior:** Incorporating material nonlinearity via plastic hinges or distributed plasticity.
3. **Dynamic Analysis:** Consistent and lumped mass matrices for transient and vibration analysis.
4. **Thermal Effects:** Including thermal expansion and temperature-dependent material properties.

## Consistent Mass Matrix

For dynamic analysis, the consistent mass matrix in local coordinates is:
$$ \mathbf{m}^e = \frac{\rho A L}{6} \begin{bmatrix} 2 & 1 \\ 1 & 2 \end{bmatrix} $$
where \( \rho \) is the [[density]].

## Geometric Stiffness Matrix

For stability analysis under axial force \( P \), the geometric stiffness matrix in local coordinates is:
$$ \mathbf{k}_g^e = \frac{P}{L} \begin{bmatrix} 1 & -1 \\ -1 & 1 \end{bmatrix} $$

## See Also

- [[Finite Element Method]]
- [[Direct Stiffness Method]]
- [[Beam Element]]
- [[Frame Element]]
- [[Isoparametric Formulation]]
- [[Structural Stability and Buckling]]
- [[Nonlinear Finite Element Analysis]]
- [[Space Truss Structures]]
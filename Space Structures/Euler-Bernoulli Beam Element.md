## Formal Definition

The **Euler-Bernoulli Beam Element** is a one-dimensional, displacement-based finite element formulation used for the linear static and dynamic analysis of slender beams and frames. It is derived from the classical **Euler-Bernoulli Beam Theory**, which describes the relationship between the deflection of a beam and the applied load, governed by the following fourth-order partial differential equation:

$$
\frac{d^2}{dx^2}\left(EI \frac{d^2 w}{dx^2}\right) = q(x)
$$

Where:
*   $w(x)$ = transverse deflection of the beam neutral axis
*   $E$ = modulus of elasticity of the beam material
*   $I$ = second moment of area (area moment of inertia) of the beam cross-section
*   $q(x)$ = distributed transverse load
*   $x$ = coordinate along the beam's longitudinal axis

## Core Assumptions

The theory and its finite element implementation rely on the following kinematic assumptions:

1.  **Plane Sections Remain Plane:** Cross-sections perpendicular to the neutral axis before deformation remain plane and perpendicular to the deformed neutral axis after bending.
2.  **Negligible Shear Deformation:** The effect of transverse shear strains on the beam's deflection is considered insignificant. This is valid for slender beams (length >> depth).
3.  **Small Deformations and Rotations:** Deflections and slopes are assumed to be small relative to the beam's dimensions.
4.  **Linearly Elastic Material:** The beam material obeys [[Hooke's Law]].

## Finite Element Formulation

In the [[Finite Element Method]] (FEM), a beam structure is discretized into a series of **Euler-Bernoulli Beam Elements** connected at nodes. For the standard two-node, one-dimensional element:

*   **Nodal [[Degrees of Freedom]] (DOFs):** Each node $i$ possesses two DOFs:
    1.  Transverse displacement ($w_i$)
    2.  Rotation (slope, $\theta_i = \frac{dw}{dx}\big|_i$)

Thus, a single element has a total of **four DOFs**: $[w_1, \theta_1, w_2, \theta_2]^T$.

*   **Shape Functions:** The deflection within an element is interpolated from the nodal DOFs using **Hermitian cubic shape functions** ($N_1, N_2, N_3, N_4$). These functions are $C^1$ continuous, ensuring continuity of both deflection and slope across element boundaries.
    $$
    w(x) = N_1 w_1 + N_2 \theta_1 + N_3 w_2 + N_4 \theta_2 = \mathbf{N} \mathbf{a}^e
    $$

*   **Element Stiffness Matrix ($\mathbf{k}^e$):** Derived from the [[Principle of Minimum Potential Energy]] or [[virtual work]]. It relates nodal forces and moments to nodal displacements and rotations.
    $$
    \mathbf{k}^e = \int_{0}^{L} EI \left(\frac{d^2 \mathbf{N}}{dx^2}\right)^T \left(\frac{d^2 \mathbf{N}}{dx^2}\right) dx
    $$
    For a prismatic element (constant $E, I$), the classic stiffness matrix in local coordinates is:
    $$
    \mathbf{k}^e = \frac{EI}{L^3}
    \begin{bmatrix}
    12 & 6L & -12 & 6L \\
    6L & 4L^2 & -6L & 2L^2 \\
    -12 & -6L & 12 & -6L \\
    6L & 2L^2 & -6L & 4L^2
    \end{bmatrix}
    $$

*   **Consistent Load Vector:** Distributed loads $q(x)$ are converted to equivalent nodal forces and moments.

## Governing Equation for an Element

The elemental equation in local coordinates is:
$$
\mathbf{k}^e \mathbf{a}^e = \mathbf{f}^e
$$
where $\mathbf{f}^e = [F_1, M_1, F_2, M_2]^T$ is the vector of nodal forces and moments.

## Typical Applications

*   Analysis of slender beams under bending (e.g., building floor joists, bridge girders).
*   Frame analysis (combined with axial bar elements to form **beam-column elements**).
*   Determination of natural frequencies and mode shapes in beam dynamics (when combined with a consistent or lumped mass matrix).

## Limitations

*   **Not suitable for thick/deep beams** where shear deformation is significant (requires [[Timoshenko Beam Element]]).
*   **Inaccurate for very short beams** or at high frequencies where shear and rotational inertia dominate.
*   Assumes linear elastic material behavior.

## See Also

*   [[Timoshenko Beam Element]]
*   [[Finite Element Method]]
*   [[Hermitian Shape Functions]]
*   [[Direct Stiffness Method]]
*   [[Classical Beam Theory]]
[[Vector]]
[[Tensor]]

The symmetry express in a stress tensor is a consecuense of the [[Conservation of Angular Momentum]]
#Physics-Concept #Space-Structures #TBD 

### Formal Definition of Stress

**Stress** is a measure of the [[Internal Forces]] acting within a deformable body per unit area. Unlike [[Force]] which is a vector, stress is a second-order tensor quantity that describes both the magnitude and direction of these internal forces and the orientation of the surface they act upon.

---

### 1. The Cauchy Stress Tensor

The complete state of stress at a point within a material is described by the **[[Cauchy stress tensor]]** $\boldsymbol{\sigma}$. For an infinitesimal surface element with unit normal vector $\mathbf{n}$, the traction vector $\mathbf{T}$ (force per unit area) acting on that surface is given by:

$$
\mathbf{T} = \boldsymbol{\sigma} \cdot \mathbf{n}
$$

In component form using Einstein notation, this becomes:

$$
\boxed{T^i = \sigma^{ij} n_j}
$$

**Explanation of the Notation:**

*   $T^i$: The $i$-th component of the traction vector (force per unit area).
*   $\sigma^{ij}$: The components of the Cauchy stress tensor.
*   $n_j$: The components of the unit normal vector to the surface.
*   **The Rule Applied:** The repeated index $j$ in $\sigma^{ij} n_j$ implies summation over $j=1..3$.

---

### 2. Physical Interpretation of Stress Components

The stress tensor $\sigma^{ij}$ can be represented as a 3×3 matrix:

$$
\sigma^{ij} = \begin{pmatrix}
\sigma^{11} & \sigma^{12} & \sigma^{13} \\
\sigma^{21} & \sigma^{22} & \sigma^{23} \\
\sigma^{31} & \sigma^{32} & \sigma^{33}
\end{pmatrix}
$$

The physical meaning of the components is:
*   **[[Normal stress]]es** ($\sigma^{11}, \sigma^{22}, \sigma^{33}$): Stress components perpendicular to the coordinate planes.
*   **[[Shear Stress]]es** ($\sigma^{12}, \sigma^{13}, \sigma^{21}, \sigma^{23}, \sigma^{31}, \sigma^{32}$): Stress components parallel to the coordinate planes.

The first index indicates the direction of the surface normal, and the second index indicates the direction of the force component.

---

### 3. Force-Stress Relationship

The total force $\Delta F^i$ acting on a surface element with area $\Delta A$ and normal $n_j$ is:

$$
\Delta F^i = \sigma^{ij} n_j \Delta A
$$

For a finite [[Surface]] $S$, the total [[Force]] is obtained by integration:

$$
F^i = \int_S \sigma^{ij} n_j dA
$$

---

### 4. [[Equilibrium Equations]]

For a body in static equilibrium, the balance of [[Linear Momentum]] leads to the [[Equilibrium Equations]]. In the absence of body forces:

$$
\frac{\partial \sigma^{ij}}{\partial x^j} = 0
$$

When body forces (e.g., gravity) are present, with body force per unit volume $f^i$:

$$
\boxed{\frac{\partial \sigma^{ij}}{\partial x^j} + f^i = 0}
$$

**Explanation:**
*   $\frac{\partial \sigma^{ij}}{\partial x^j}$: The [[divergence]] of the stress tensor.
*   $f^i$: The body force components per unit volume.
*   The repeated index $j$ implies summation over spatial dimensions.

---

### 5. Symmetry of the Stress Tensor

The balance of [[Angular Momentum]] requires that the stress tensor be symmetric:

$$
\boxed{\sigma^{ij} = \sigma^{ji}}
$$

This symmetry reduces the number of independent stress components from 9 to 6.

---

### 6. Transformation Law

Under coordinate transformation, stress components transform as a second-order tensor:

$$
\sigma^{'ij} = a^i_k a^j_l \sigma^{kl}
$$

where $a^i_k = \frac{\partial x^{'i}}{\partial x^k}$ are the direction cosines of the transformation.

---

### 7. Principal Stresses

The principal stresses are the [[Eigenvalues & Eigenvectors]] of the stress tensor, found by solving:

$$
\sigma^{ij} n_j = \sigma n^i
$$

or equivalently:

$$
(\sigma^{ij} - \sigma g^{ij}) n_j = 0
$$

where $\sigma$ are the principal stresses and $n_j$ are the principal directions.

---

### 8. Invariants of the Stress Tensor

The [[principal invariants]] of the stress tensor are:
- First invariant (hydrostatic pressure): $I_1 = \sigma^{ii} = \sigma^{11} + \sigma^{22} + \sigma^{33}$
- Second invariant: $I_2 = \frac{1}{2}(\sigma^{ii}\sigma^{jj} - \sigma^{ij}\sigma^{ji})$
- Third invariant: $I_3 = \det(\sigma^{ij})$

---

### 9. Decomposition into Hydrostatic and Deviatoric Parts

The stress tensor can be decomposed into hydrostatic (volumetric) and deviatoric (distortional) parts:

$$
\sigma^{ij} = -p g^{ij} + s^{ij}
$$

where:
*   **Hydrostatic stress**: $-p = \frac{1}{3}\sigma^{kk}$ (pressure)
*   **Deviatoric stress**: $s^{ij} = \sigma^{ij} + p g^{ij}$

In Einstein notation, the pressure is:

$$
p = -\frac{1}{3}\sigma^{kk}
$$

---

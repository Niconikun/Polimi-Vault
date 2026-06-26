#Physics-Concept #DONE 
### Formal Definition of Kinetic Energy

The **kinetic energy** ($T$ or $K$) of an object is the energy it possesses due to its motion. For a single particle, it is defined as the [[Work]] required to accelerate the object from rest to its current velocity.

---

### 1. Classical Definition using Einstein Notation

In Newtonian mechanics, for a single particle of mass $m$ moving with [[Velocity]] $\mathbf{v}$, the kinetic energy is:

$$
T = \frac{1}{2} m v^2
$$

where $v^2 = \mathbf{v} \cdot \mathbf{v}$ is the square of the magnitude of the velocity vector.

To express this in Einstein notation, we write the velocity vector as $\mathbf{v} = v^i \mathbf{e}_i$. The dot product $\mathbf{v} \cdot \mathbf{v}$ is:

$$
\mathbf{v} \cdot \mathbf{v} = (v^i \mathbf{e}_i) \cdot (v^j \mathbf{e}_j) = v^i v^j (\mathbf{e}_i \cdot \mathbf{e}_j)
$$

In Cartesian coordinates, the basis is orthonormal: $\mathbf{e}_i \cdot \mathbf{e}_j = \delta_{ij}$, where $\delta_{ij}$ is the [[Kronecker delta]]. Therefore:

$$
\mathbf{v} \cdot \mathbf{v} = v^i v^j \delta_{ij} = v^i v^i
$$

Thus, the classical kinetic energy in Einstein notation is:

$$
\boxed{T = \frac{1}{2} m v^i v^i}
$$

**Explanation of the Notation:**

*   $T$: The scalar kinetic energy.
*   $m$: The mass of the particle.
*   $v^i$: The $i$-th component of the velocity vector.
*   **The Rule Applied:** The repeated index $i$ in $v^i v^i$ implies summation over all spatial dimensions: $v^1 v^1 + v^2 v^2 + v^3 v^3 = v_x^2 + v_y^2 + v_z^2 = v^2$.

---

### 2. General Coordinate Systems

In general curvilinear coordinates, the dot product requires the [[Metric Tensor]] $g_{ij} = \mathbf{e}_i \cdot \mathbf{e}_j$. The kinetic energy becomes:

$$
T = \frac{1}{2} m (\mathbf{v} \cdot \mathbf{v}) = \frac{1}{2} m (v^i \mathbf{e}_i \cdot v^j \mathbf{e}_j) = \frac{1}{2} m g_{ij} v^i v^j
$$

This is the most general form of the classical kinetic energy in Einstein notation:

$$
\boxed{T = \frac{1}{2} m g_{ij} v^i v^j}
$$

For example, in spherical coordinates, $g_{ij}$ is not the identity matrix, and this expression correctly accounts for the contributions from all velocity components.

---

### 3. Relativistic Definition using Einstein Notation

In [[special relativity]], the kinetic energy is defined as the total energy minus the rest energy:

$$
T = E - E_0 = \gamma m_0 c^2 - m_0 c^2
$$

where $m_0$ is the rest mass, $c$ is the speed of light, and $\gamma$ is the Lorentz factor:

$$
\gamma = (1 - v^2/c^2)^{-1/2}
$$

To express this in Einstein notation, we again note that $v^2 = \delta_{ij} v^i v^j$ in Cartesian coordinates. Therefore, the relativistic kinetic energy is:

$$
\boxed{T = m_0 c^2 \left( \frac{1}{\sqrt{1 - \frac{\delta_{ij} v^i v^j}{c^2}}} - 1 \right)}
$$

---

### 4. Kinetic Energy for a System of Particles

For a system of $N$ particles, the total classical kinetic energy is the sum of the kinetic energies of all particles:

$$
T = \sum_{n=1}^N \frac{1}{2} m_n v_n^2
$$

In Einstein notation, introducing a particle index $n$:

$$
\boxed{T = \sum_{n=1}^N \frac{1}{2} m_n v_n^i v_n^i}
$$

where $v_n^i$ is the $i$-th component of the velocity of the $n$-th particle.

---

### 5. Kinetic Energy in [[Rigid Body]] [[Rotation]]

For [[Rigid-Body Dynamics]] rotating with [[Angular Velocity]] $\boldsymbol{\omega}$, the kinetic energy can be expressed in terms of the [[inertia tensor]] $I^{ij}$. The general form is:

$$
T = \frac{1}{2} I^{ij} \omega_i \omega_j
$$

This expression uses Einstein notation with two repeated indices, implying a double sum:

$$
\boxed{T = \frac{1}{2} I^{ij} \omega_i \omega_j}
$$

This is the rotational analogue of $T = \frac{1}{2} m v^2$.

---

### 6. Relationship to Momentum

Kinetic energy can also be expressed in terms of [[Linear Momentum]] $\mathbf{p}$. Since $p^i = m v^i$, we have $v^i = p^i/m$. Substituting into the classical kinetic energy formula:

$$
T = \frac{1}{2} m v^i v^i = \frac{1}{2} m \left(\frac{p^i}{m}\right) \left(\frac{p^i}{m}\right) = \frac{p^i p^i}{2m}
$$

In general coordinates, using the inverse [[Metric Tensor]] $g^{ij}$:

$$
T = \frac{1}{2m} g^{ij} p_i p_j
$$

---

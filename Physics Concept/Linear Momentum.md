#Physics-Concept #DONE 
### Formal Definition of Linear Momentum

The **linear momentum** (often simply called **momentum**) of a particle is a [[Vector]] quantity defined as the product of the particle's mass and its [[Velocity]]. It is a measure of the quantity of motion possessed by the particle and is a conserved quantity in isolated systems.

For a single particle, the linear momentum $\mathbf{p}$ is given by:

$$
\mathbf{p} = m \mathbf{v}
$$

where $m$ is the mass of the particle and $\mathbf{v}$ is its velocity vector.

---

### Definition using Einstein Notation

We begin with the velocity vector expressed in Einstein notation: $\mathbf{v} = v^i \mathbf{e}_i$. Substituting this into the definition of momentum:

$$
\mathbf{p} = m (v^i \mathbf{e}_i)
$$

Since mass $m$ is a scalar, it can be distributed inside the sum. We define the component of the momentum vector as $p^i \equiv m v^i$. Therefore, the formal definition of the linear momentum vector in Einstein notation is:

$$
\boxed{\mathbf{p} = p^i \mathbf{e}_i} \quad \text{where} \quad \boxed{p^i = m v^i}
$$

**Explanation of the Notation:**

*   $\mathbf{p}$: The linear momentum vector.
*   $p^i$: The $i$-th **contravariant component** of the momentum vector. In 3D Cartesian coordinates, $(p^1, p^2, p^3) = (p_x, p_y, p_z)$.
*   $m$: The inertial mass of the particle (assumed constant in Newtonian mechanics for this definition).
*   $v^i$: The $i$-th component of the velocity vector.
*   $\mathbf{e}_i$: The $i$-th basis vector.
*   **The Rule Applied:** The repeated index $i$ in $p^i \mathbf{e}_i$ implies summation over all spatial dimensions.

---

### Relativistic Definition using Einstein Notation

In special relativity, the definition of momentum is modified to be consistent with the [[Lorentz Transformations]]. The relativistic momentum is given by:

$$
\mathbf{p} = \gamma m_0 \mathbf{v}
$$

where $m_0$ is the **rest mass** of the particle and $\gamma$ is the Lorentz factor, $\gamma = (1 - v^2/c^2)^{-1/2}$.

Expressing this in Einstein notation requires careful consideration of the Lorentz factor, which depends on the magnitude of velocity. The magnitude squared of the velocity is $v^2 = \delta_{ij} v^i v^j$, where $\delta_{ij}$ is the [[Kronecker delta]] (the [[Metric Tensor]] for Cartesian coordinates).

Therefore, the relativistic momentum in component form is:

$$
\boxed{p^i = \gamma m_0 v^i} \quad \text{where} \quad \boxed{\gamma = \left(1 - \frac{\delta_{jk} v^j v^k}{c^2}\right)^{-1/2}}
$$

The full momentum vector is still $\mathbf{p} = p^i \mathbf{e}_i$.

---

### Momentum as the Conjugate of Position (Analytical Mechanics)

In [[Lagrangian mechanics]], momentum takes on a more fundamental role as the **conjugate momentum** (or canonical momentum) to a generalized coordinate. For a generalized coordinate $q^j$, the conjugate momentum $p_j$ is defined as:

$$
p_j = \frac{\partial \mathcal{L}}{\partial \dot{q}^j}
$$

where $\mathcal{L}(q^j, \dot{q}^j, t)$ is the Lagrangian of the system, typically $\mathcal{L} = T - U$ ([[Kinetic Energy]] minus Potential energy), and $\dot{q}^j$ is the generalized velocity.

In Einstein notation, if the [[Kinetic Energy]] $T$ is expressed as a quadratic form, this definition becomes very powerful. For a system of particles, this general definition may yield momenta that are different from the standard $m v^i$, especially in the presence of velocity-dependent potentials (like electromagnetic fields).

---

### Momentum of a System of Particles

For a system of $N$ particles, the total linear momentum $\mathbf{P}$ is the vector sum of the individual momenta:

$$
\mathbf{P} = \sum_{n=1}^N \mathbf{p}_n = \sum_{n=1}^N m_n \mathbf{v}_n
$$

In Einstein notation, this is written by introducing an additional particle index $n$:

$$
\boxed{P^i = \sum_{n=1}^N m_n v_n^i}
$$

The index $i$ is still summed over when used in the context of the vector $\mathbf{P} = P^i \mathbf{e}_i$.

### [[Newton's Second Law]] in Terms of Momentum

[[Newton's Second Law]] is most fundamentally stated in terms of momentum:

> The net force acting on a particle is equal to the [[Time]] rate of change of its linear momentum.

$$
\mathbf{F}_{\text{net}} = \frac{d\mathbf{p}}{dt}
$$

In component form using Einstein notation, this becomes:

$$
\boxed{F^i = \frac{d p^i}{dt}}
$$

For a constant mass system where $p^i = m v^i$, this reduces to the familiar $F^i = m a^i$.
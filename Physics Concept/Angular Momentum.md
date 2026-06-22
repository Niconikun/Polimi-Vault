#Physics-Concept #DONE 

Of course. Angular momentum is a fundamental quantity in physics, crucial for understanding rotational dynamics from spinning galaxies to quantum particles.

### Formal Definition of Angular Momentum

The **angular momentum** of a particle about a point $O$ is a pseudovector (axial vector) quantity defined as the cross product of the particle's position vector (relative to $O$) and its [[Linear Momentum]].

For a single particle:
$$
\mathbf{L} = \mathbf{r} \times \mathbf{p}
$$
where $\mathbf{r}$ is the position vector from point $O$ to the particle, and $\mathbf{p}$ is the [[Linear Momentum]] of the particle.

---

### 1. Definition using Einstein Notation

Using the [[Levi-Civita symbol]] $\epsilon_{ijk}$ for the cross product, the $i$-th component of the angular momentum vector is:

$$
\boxed{L^i = \epsilon^{ijk} r_j p_k}
$$

**Explanation of the Notation:**

*   $L^i$: The $i$-th component of the angular momentum vector.
*   $\epsilon^{ijk}$: The Levi-Civita symbol (permutation tensor).
*   $r_j$: The $j$-th component of the position vector.
*   $p_k$: The $k$-th component of the [[Linear Momentum]] vector.
*   **The Rule Applied:** The repeated indices $j$ and $k$ imply summation over all spatial dimensions. The Levi-Civita symbol ensures the correct components are combined to form the cross product.

---

### 2. Angular Momentum of a System of Particles

For a system of $N$ particles, the total angular momentum about point $O$ is the vector sum of the individual angular momenta:

$$
\mathbf{L}_{\text{total}} = \sum_{n=1}^{N} \mathbf{r}_n \times \mathbf{p}_n
$$

In Einstein notation, introducing a particle index $n$:

$$
\boxed{L^i_{\text{total}} = \sum_{n=1}^{N} \epsilon^{ijk} r_{n,j} p_{n,k}}
$$

---

### 3. Angular Momentum of a [[Rigid Body]]

For a [[Rigid Body]] rotating with [[Angular Velocity]] $\boldsymbol{\omega}$, the angular momentum is related to the [[inertia tensor]] $I^{ij}$. The general form is:

$$
\boxed{L^i = I^{ij} \omega_j}
$$

where $I^{ij}$ is the **[[inertia tensor]]**, defined for a continuous body as:

$$
I^{ij} = \int_V \rho(\mathbf{r}) \left( r^2 \delta^{ij} - r^i r^j \right) dV
$$

*   **Explanation:** $r^2 = \delta_{kl} r^k r^l$ is the square of the distance from the axis, and $\rho(\mathbf{r})$ is the mass [[density]]. This expression is the rotational analogue of $\mathbf{p} = m\mathbf{v}$, but mass is replaced by a tensor that describes the mass distribution relative to the [[Rotation]] axis.


---

### 6. Derivation from Newton's Laws

Let's derive the conservation law for a single particle using Einstein notation.

Start with the definition of angular momentum:
$$
L^i = \epsilon^{ijk} r_j p_k
$$

Take the [[Time]] derivative:
$$
\frac{dL^i}{dt} = \epsilon^{ijk} \left( \frac{dr_j}{dt} p_k + r_j \frac{dp_k}{dt} \right)
$$

Recognize that $\frac{dr_j}{dt} = v_j$ and $\frac{dp_k}{dt} = F_k$ ([[Newton's Second Law]]). Also, $p_k = m v_k$. Substituting:

$$
\frac{dL^i}{dt} = \epsilon^{ijk} \left( v_j (m v_k) + r_j F_k \right) = \epsilon^{ijk} m v_j v_k + \epsilon^{ijk} r_j F_k
$$

The first term, $\epsilon^{ijk} v_j v_k$, is zero because it is the cross product of a vector with itself ($v_j v_k$ is symmetric in $j$ and $k$, while $\epsilon^{ijk}$ is antisymmetric). The second term is the definition of [[torque]], $\tau^i = \epsilon^{ijk} r_j F_k$.

Therefore:
$$
\boxed{\frac{dL^i}{dt} = \tau^i}
$$

This is the most general form of the rotational equation of motion. Conservation follows immediately when $\tau^i = 0$.

---

### Summary

*   **Angular Momentum Definition:**
    $$
    L^i = \epsilon^{ijk} r_j p_k \quad \text{(single particle)}
    $$
    $$
    L^i = I^{ij} \omega_j \quad \text{(rigid body)}
    $$


- **Governing Equation ([[Newton's Second Law]] for Rotation):**
    $$
    \frac{dL^i}{dt} = \tau^i
    $$

The [[Conservation of Angular Momentum]] is a fundamental principle of physics with profound implications, from explaining the stability of planetary orbits and the dynamics of spinning tops to governing the rules of quantum mechanics and the structure of galaxies. The Einstein notation provides a compact and elegant framework for expressing these concepts in a form that readily generalizes to complex systems and advanced physical theories.

### Inertial Tensor and General Rotation of a [[Rigid Body]]

For a single particle, the above definition is sufficient. However, for a [[Rigid Body]] rotating about an axis, every particle in the body shares the *same* [[Angular Velocity]] vector $\boldsymbol{\omega}$. The relationship between the total angular momentum $\mathbf{L}$ and the [[Angular Velocity]] is given by the **[[inertia tensor]]** $I^{ij}$.

The angular momentum $\mathbf{L}$ of a [[Rigid Body]] is related to its [[Angular Velocity]] $\boldsymbol{\omega}$ by:
$$
L^i = I^{ij} \omega_j
$$
where $I^{ij}$ is the [[inertia tensor]], defined for a collection of particles as:
$$
I^{ij} = \sum_n m_n \left( r_n^2 \delta^{ij} - r_n^i r_n^j \right)
$$
for discrete masses, or the corresponding integral for a continuous body.

In this expression, $r_n^2$ is the square of the distance of particle $n$ from the origin, and $\delta^{ij}$ is the [[Kronecker delta]].

This provides another fundamental definition of [[Angular Velocity]] in the context of dynamics:

$$
\boxed{L^i = I^{ij} \omega_j}
$$

This equation is the rotational analogue of $\mathbf{p} = m\mathbf{v}$, but mass $m$ is replaced by the [[inertia tensor]] $I^{ij}$, which describes how mass is distributed relative to the axis of rotation.
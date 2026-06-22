#Physics-Concept #DONE 

### Formal Definition of Angular Acceleration

The **angular acceleration** of a rotating object is a pseudovector quantity that specifies the [[Time]] rate of change of its [[Angular Velocity]]. It describes how quickly the [[Rotation]] is speeding up, slowing down, or changing direction.

Mathematically, angular acceleration $\boldsymbol{\alpha}$ is the first derivative of the [[Angular Velocity]] vector $\boldsymbol{\omega}$ with respect to [[time]]:

$$
\boldsymbol{\alpha} = \frac{d\boldsymbol{\omega}}{dt}
$$

---

### Definition using Einstein Notation

Starting from the [[Angular Velocity]] vector expressed in component form, $\boldsymbol{\omega} = \omega^i \mathbf{e}_i$ (or $\omega_j$, depending on index placement), we define angular acceleration by taking the [[time]] derivative.

Assuming a fixed basis (like in an [[Inertial Frame of Reference]]), the derivative of the basis vectors is zero. Therefore, the angular acceleration vector is:

$$
\boldsymbol{\alpha} = \frac{d}{dt}(\boldsymbol{\omega}) = \frac{d}{dt}(\omega^i \mathbf{e}_i) = \frac{d\omega^i}{dt} \mathbf{e}_i
$$

We define the components of angular acceleration as $\alpha^i = \frac{d\omega^i}{dt}$. This gives us the direct component-wise definition:

$$
\boxed{\boldsymbol{\alpha} = \alpha^i \mathbf{e}_i} \quad \text{where} \quad \boxed{\alpha^i = \frac{d\omega^i}{dt}}
$$

**Explanation of the Notation:**

*   $\boldsymbol{\alpha}$: The angular acceleration vector.
*   $\alpha^i$: The $i$-th component of the angular acceleration vector.
*   $\omega^i$: The $i$-th component of the [[Angular Velocity]] vector.
*   The repeated index $i$ in $\alpha^i \mathbf{e}_i$ implies summation over the three spatial dimensions.

---

### Relationship to Linear Acceleration

Just as linear velocity and [[Angular Velocity]] are related by $\mathbf{v} = \boldsymbol{\omega} \times \mathbf{r}$, we can find a similar relationship for [[acceleration]]. This is particularly important for understanding the dynamics of rotating systems.

Starting from $\mathbf{v} = \boldsymbol{\omega} \times \mathbf{r}$ and expressing it with the [[Levi-Civita Symbol]]:
$$
v^i = \epsilon^{\ ijk} \omega_j r_k
$$

We differentiate with respect to [[time]] to find the linear acceleration $a^i = \frac{dv^i}{dt}$:

$$
a^i = \frac{d}{dt}(\epsilon^{\ ijk} \omega_j r_k)
$$

Assuming a constant [[position]] vector $\mathbf{r}$ (i.e., the particle is fixed in the rotating body, so it's undergoing pure rotation), we apply the product rule. The [[Levi-Civita symbol]] is a constant, so we get:

$$
a^i = \epsilon^{\ ijk} \left( \frac{d\omega_j}{dt} r_k + \omega_j \frac{dr_k}{dt} \right)
$$

Recognizing that $\frac{d\omega_j}{dt} = \alpha_j$ (angular acceleration) and $\frac{dr_k}{dt} = v_k$ (linear velocity), and substituting the velocity expression $v_k = \epsilon_{k}^{\ mn} \omega_m r_n$, we get:

$$
a^i = \epsilon^{\ ijk} \alpha_j r_k + \epsilon^{\ ijk} \omega_j (\epsilon_{k}^{\ mn} \omega_m r_n)
$$

This expression contains the two components of acceleration for a particle in uniform circular motion:
1. **Tangential acceleration**: $\epsilon^{\ ijk} \alpha_j r_k = (\boldsymbol{\alpha} \times \mathbf{r})^i$
2. **Centripetal acceleration**: $\epsilon^{\ ijk} \epsilon_{k}^{\ mn} \omega_j \omega_m r_n$

Using vector identities, this simplifies to the well-known result:
$$
\mathbf{a} = \boldsymbol{\alpha} \times \mathbf{r} + \boldsymbol{\omega} \times (\boldsymbol{\omega} \times \mathbf{r})
$$

In Einstein notation, the complete expression for the linear acceleration of a point in a rotating [[Rigid Body]] is:

$$
\boxed{a^i = \epsilon^{\ ijk} \alpha_j r_k + \epsilon^{\ ijk} \epsilon_{k}^{\ mn} \omega_j \omega_m r_n}
$$

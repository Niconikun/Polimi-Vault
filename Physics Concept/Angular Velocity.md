#Physics-Concept #DONE 
### Formal Definition of Angular Velocity

The **angular velocity** of a rotating object is a pseudovector quantity that specifies the rate of [[Rotation]] and the axis about which the object rotates. Its magnitude is the angular speed (e.g., radians per second), and its direction is perpendicular to the [[Rotation Plane]], following the right-hand rule.

For a particle moving in a circle, the angular velocity $\boldsymbol{\omega}$ is related to the tangential velocity $\mathbf{v}$ and the [[position]] vector $\mathbf{r}$ from the center of rotation by the cross product:
$$
\mathbf{v} = \boldsymbol{\omega} \times \mathbf{r}
$$
This equation is often taken as the defining relationship.

---

### Definition using Einstein Notation and the [[Levi-Civita Symbol]]

The cross product is elegantly expressed in Einstein notation using the **[[Levi-Civita Symbol]]** (also called the permutation symbol), $\epsilon_{ijk}$.

The [[Levi-Civita symbol]] $\epsilon_{ijk}$ is defined as:
*   $\epsilon_{123} = \epsilon_{231} = \epsilon_{312} = +1$ (even permutations of 123)
*   $\epsilon_{132} = \epsilon_{321} = \epsilon_{213} = -1$ (odd permutations of 123)
*   $\epsilon_{ijk} = 0$ if any two indices are equal (e.g., $\epsilon_{112} = 0$)

The cross product of two vectors $\mathbf{A}$ and $\mathbf{B}$ is given by:
$$
(\mathbf{A} \times \mathbf{B})^i = \epsilon^{\ ijk} A_j B_k
$$
Where $\epsilon^{ijk}$ has the same values as $\epsilon_{ijk}$. (In Cartesian coordinates, the [[position]] of the indices—up or down—doesn't matter, but it's crucial in general relativity).

Using this, we can write the defining equation $\mathbf{v} = \boldsymbol{\omega} \times \mathbf{r}$ in component form. The $i$-th component of the velocity is:
$$
v^i = (\boldsymbol{\omega} \times \mathbf{r})^i = \epsilon^{\ ijk} \omega_j r_k
$$

Therefore, the formal relationship defining angular velocity in Einstein notation is:

$$
\boxed{v^i = \epsilon^{\ ijk} \omega_j r_k}
$$

**Explanation of the Notation:**

*   $v^i$: The $i$-th component of the linear velocity vector.
*   $\epsilon^{\ ijk}$: The [[Levi-Civita symbol]] used to compute the cross product.
*   $\omega_j$: The $j$-th component of the angular velocity pseudovector. Note the use of a lower index; this is often the case for pseudovectors, but $\omega^j$ is also commonly used in Cartesian coordinates.
*   $r_k$: The $k$-th component of the [[position]] vector.
*   **The Rule Applied:** The repeated indices $j$ and $k$ in $\epsilon^{\ ijk} \omega_j r_k$ imply a double sum over $j=1..3$ and $k=1..3$. The [[Levi-Civita symbol]] ensures that only the correct combinations contribute to the $i$-th component of the cross product.

---



### Summary

The angular velocity $\boldsymbol{\omega}$ is fundamentally defined by its relationship to tangential velocity via the cross product. Einstein notation, combined with the [[Levi-Civita symbol]], provides a compact and powerful way to express this relationship as $v^i = \epsilon^{\ ijk} \omega_j r_k$. For the dynamics of extended rigid bodies, its relationship to [[Angular Momentum]] via the [[inertia tensor]], $L^i = I^{ij} \omega_j$, is the more relevant definition.
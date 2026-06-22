#Physics-Concept #DONE
### Formal Definition of Acceleration

The **acceleration** of a point particle is a [[Vector]] quantity defined as the [[Time]] rate of change of its [[Velocity]] [[Vector]]. It describes how the [[velocity]] changes in both magnitude and direction. Mathematically, acceleration is the first derivative of [[velocity]] with respect to [[Time]], or equivalently, the second derivative of the [[Position]] [[Vector]] with respect to [[time]]:

$$
\mathbf{a} = \frac{d\mathbf{v}}{dt} = \frac{d^2\mathbf{r}}{dt^2}
$$

---

### Definition using Einstein Notation (Constant Basis)

We begin with the [[velocity]] [[Vector]] in a coordinate system where the basis vectors $\mathbf{e}_i$ are constant (e.g., Cartesian coordinates in an inertial frame): $\mathbf{v}(t) = v^i(t) \mathbf{e}_i$.

The acceleration is the [[time]] derivative of this expression:

$$
\mathbf{a} = \frac{d}{dt}(\mathbf{v}) = \frac{d}{dt}(v^i \mathbf{e}_i)
$$

Since the basis vectors are constant, $\frac{d\mathbf{e}_i}{dt} = 0$, and we obtain:

$$
\mathbf{a} = \frac{d v^i}{dt} \mathbf{e}_i
$$

The [[time]] derivative of the [[velocity]] component $v^i$ is defined as the **acceleration component**, denoted $a^i$:

$$
a^i \equiv \frac{d v^i}{dt} = \frac{d^2 r^i}{dt^2}
$$

Therefore, the formal definition of the acceleration [[Vector]] in Einstein notation, under the assumption of a constant basis, is:

$$
\boxed{\mathbf{a} = a^i \mathbf{e}_i} \quad \text{where} \quad \boxed{a^i = \frac{d v^i}{dt} = \frac{d^2 r^i}{dt^2}}
$$

**Explanation of the Notation:**

*   $\mathbf{a}$: The acceleration [[Vector]].
*   $a^i$: The $i$-th contravariant component of the acceleration [[Vector]]. In Cartesian coordinates, $(a^1, a^2, a^3) = (a_x, a_y, a_z)$.
*   $\mathbf{e}_i$: The $i$-th constant basis [[Vector]].
*   **The Rule Applied:** The repeated index $i$ in $a^i \mathbf{e}_i$ implies summation over $i=1$ to $n$.

---

### Important Consideration: General Coordinate Systems (Non-Constant Basis)

As with [[velocity]], the expression becomes more complex in general curvilinear coordinates (e.g., spherical coordinates) where the basis vectors $\mathbf{e}_i$ depend on the [[position]]. In this case, we must differentiate the full [[velocity]] [[Vector]] $\mathbf{v} = v^i \mathbf{e}_i$ using the product rule.

$$
\mathbf{a} = \frac{d\mathbf{v}}{dt} = \frac{d}{dt}(v^i \mathbf{e}_i) = \frac{d v^i}{dt} \mathbf{e}_i + v^i \frac{d \mathbf{e}_i}{dt}
$$

The term $\frac{d \mathbf{e}_i}{dt}$ is again handled with the chain rule. If the basis is a function of the coordinates $q^j$, then:

$$
\frac{d \mathbf{e}_i}{dt} = \frac{\partial \mathbf{e}_i}{\partial q^j} \frac{d q^j}{dt} = \frac{\partial \mathbf{e}_i}{\partial q^j} v^j
$$

Substituting this back in, we get the general expression for acceleration:

$$
\mathbf{a} = \frac{d v^i}{dt} \mathbf{e}_i + v^i v^j \frac{\partial \mathbf{e}_i}{\partial q^j}
$$

This expression contains two distinct parts:
1.  $\frac{d v^i}{dt} \mathbf{e}_i$: The rate of change of the [[velocity]] components. This represents the "linear" acceleration.
2.  $v^i v^j \frac{\partial \mathbf{e}_i}{\partial q^j}$: The term arising from the change in the direction of the basis vectors as the particle moves. This is crucial for capturing centripetal and Coriolis-type effects inherent to the coordinate system.

The partial derivative of the basis [[Vector]], $\frac{\partial \mathbf{e}_i}{\partial q^j}$, is related to the **Christoffel symbols** $\Gamma^k_{\ ij}$ used in differential geometry and general relativity, which provide a compact way to write this expression. The general form becomes:

$$
a^k = \frac{d v^k}{dt} + \Gamma^k_{\ ij} v^i v^j
$$

where $a^k$ are the components of the acceleration [[Vector]] in the general coordinate system.
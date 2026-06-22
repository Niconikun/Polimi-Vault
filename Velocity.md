#Physics-Concept #DONE 
### Formal Definition of Velocity

The **velocity** of a point particle is a [[Vector]] quantity defined as the time rate of change of its [[position]] [[Vector]]. It describes both the speed (magnitude of velocity) and the direction of motion.

Mathematically, velocity is the derivative of the position vector $\mathbf{r}(t)$ with respect to [[Time]] \(t\):

$$
\mathbf{v} = \frac{d\mathbf{r}}{dt}
$$

---

### Definition using Einstein Notation

Starting from the position vector expressed in Einstein notation, $\mathbf{r}(t) = r^i(t) \mathbf{e}_i$, we can derive the velocity. We assume the basis vectors $\mathbf{e}_i$ are constant in time, as is the case in an [[Inertial Frame of Reference]] with Cartesian coordinates.

$$
\mathbf{v} = \frac{d}{dt}(\mathbf{r}) = \frac{d}{dt}(r^i \mathbf{e}_i)
$$
Applying the derivative and using the fact that the basis vectors are constant $\frac{d\mathbf{e}_i}{dt} = 0$, we get:

$$
\mathbf{v} = \frac{d r^i}{dt} \mathbf{e}_i
$$
The time derivative of the component \(r^i\) is itself a component of the velocity [[Vector]]. We denote this component as \(v^i\):

$$
v^i \equiv \frac{d r^i}{dt}
$$

Therefore, the formal definition of the velocity [[Vector]] in Einstein notation is:

$$
{\mathbf{v} = v^i \mathbf{e}_i} \quad \text{where} \quad v^i = \frac{d r^i}{dt}
$$

**Explanation of the Notation:**

*   \(\mathbf{v}\): The velocity [[Vector]].
*   \(v^i\): The \(i\)-th **contravariant component** of the velocity [[Vector]]. In Cartesian coordinates, \((v^1, v^2, v^3) = (v_x, v_y, v_z)\).
*   \(\mathbf{e}_i\): The \(i\)-th basis vector.
*   **The Rule Applied:** The repeated index \(i\) in \(v^i \mathbf{e}_i\) implies summation over \(i=1\) to \(n\).

---

### Important Consideration: General Coordinate Systems

The above derivation assumed a **coordinate system with a fixed basis** (like Cartesian coordinates). The situation becomes more nuanced in general curvilinear coordinates (e.g., spherical or cylindrical coordinates), where the basis vectors themselves depend on the position and therefore change with time as the particle moves.

In the general case, the derivative must be applied to the entire product \(r^i \mathbf{e}_i\) using the product rule:

\[
\mathbf{v} = \frac{d}{dt}(r^i \mathbf{e}_i) = \frac{d r^i}{dt} \mathbf{e}_i + r^i \frac{d \mathbf{e}_i}{dt}
\]

The key insight is that the time derivative of the basis vector, \(\frac{d \mathbf{e}_i}{dt}\), can be related to the velocity components themselves through the chain rule. If the basis \(\mathbf{e}_i(\{q^j\})\) depends on the coordinates \(q^j\), then:

\[
\frac{d \mathbf{e}_i}{dt} = \frac{\partial \mathbf{e}_i}{\partial q^j} \frac{d q^j}{dt} = \frac{\partial \mathbf{e}_i}{\partial q^j} v^j
\]

This leads to the expression:

\[
\mathbf{v} = v^i \mathbf{e}_i + r^i \frac{\partial \mathbf{e}_i}{\partial q^j} v^j
\]

While this looks more complex, it correctly describes the velocity in any [[Coordinate System]]. For Cartesian coordinates, $\frac{\partial \mathbf{e}_i}{\partial q^j} = 0$, and the expression simplifies to the one given in the box above.
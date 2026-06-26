#Physics-Concept #DONE 

### Formal Definition of Potential Energy

The **potential energy** ($U$ or $V$) of a system is the energy stored in the system due to its position or configuration in a [[conservative force]] [[Field]]. It represents the [[Work]] that the [[Conservative Force]]s would do on the system to move it from its current configuration to a reference configuration.

For a [[conservative force]] $\mathbf{F}$, the potential energy is defined such that its negative gradient equals the force:

$$
\mathbf{F} = -\nabla U
$$

or equivalently, the difference in potential energy between two points is the negative of the work done by the [[conservative force]]:

$$
U(\mathbf{r}_B) - U(\mathbf{r}_A) = -\int_A^B \mathbf{F} \cdot d\mathbf{r}
$$

---

### 1. Fundamental Definition using Einstein Notation

The gradient operator $\nabla$ in Einstein notation is expressed as $\nabla_i = \frac{\partial}{\partial x^i}$. Therefore, the fundamental definition of a [[conservative force]] in terms of potential energy becomes:

$$
\boxed{F_i = -\frac{\partial U}{\partial x^i}}
$$

**Explanation of the Notation:**

*   $F_i$: The covariant components of the [[conservative force]] vector.
*   $U$: The scalar potential energy field, $U = U(x^1, x^2, x^3)$.
*   $\frac{\partial U}{\partial x^i}$: The partial derivative of $U$ with respect to the $i$-th coordinate.
*   The index $i$ indicates this is a component equation. Unlike previous cases, there is **no summation** here - this represents three separate equations (for $i = 1, 2, 3$).

---

### 2. Work-Energy Relationship in Einstein Notation

The work done by a conservative [[Force]] is related to the change in potential energy. The infinitesimal work is:

$$
dW = \mathbf{F} \cdot d\mathbf{r} = F_i dx^i
$$

Using the definition $F_i = -\frac{\partial U}{\partial x^i}$, we get:

$$
dW = -\frac{\partial U}{\partial x^i} dx^i
$$

The right-hand side, $\frac{\partial U}{\partial x^i} dx^i$, is exactly the differential $dU$ in Einstein notation. Therefore:

$$
dW = -dU
$$

Integrating this along a path gives the finite work-energy relationship:

$$
U(B) - U(A) = -\int_A^B F_i dx^i
$$

---

### 3. Common Potential Energy Forms in Einstein Notation

#### **[[Gravitational Potential Energy]] (Near Earth's [[Surface]])**

$$
\boxed{U = m g_{ij} g^j x^i}
$$

where $g^j$ are the components of the gravitational acceleration vector. In Cartesian coordinates with $z$ upward: $U = mgz = mg\delta_{3i}x^i$.

#### **Elastic Potential Energy (Spring)**

For a spring stretched along direction $n^i$ from equilibrium:

$$
\boxed{U = \frac{1}{2} k (\delta_{ij} \Delta x^i \Delta x^j)}
$$

where $\Delta x^i$ are the displacement components from equilibrium.

#### **Newtonian [[Gravitational Potential Energy]]**

For two masses $m_1$ and $m_2$ separated by distance $r$:

$$
U = -\frac{G m_1 m_2}{r}
$$

where $r^2 = \delta_{ij} x^i x^j$ and $x^i$ are the separation vector components. Therefore:

$$
\boxed{U = -\frac{G m_1 m_2}{\sqrt{\delta_{ij} x^i x^j}}}
$$

#### **Electrostatic Potential Energy**

For two charges $q_1$ and $q_2$:

$$
\boxed{U = \frac{1}{4\pi\epsilon_0} \frac{q_1 q_2}{\sqrt{\delta_{ij} x^i x^j}}}
$$

---

### 4. Potential Energy in General Coordinates

In general curvilinear coordinates, the gradient operation requires the [[Metric Tensor]]. The force components become:

$$
F_i = -g_{ij} \frac{\partial U}{\partial x_j}
$$

where $g_{ij}$ is the metric tensor and we've used the fact that $\frac{\partial U}{\partial x_j} = g^{jk} \frac{\partial U}{\partial x^k}$.

---

### 5. System Potential Energy

For a system of $N$ particles interacting via conservative forces, the total potential energy is:

$$
\boxed{U = \sum_{n=1}^N \sum_{m>n}^N U_{nm}(r_{nm})}
$$

where $U_{nm}$ is the pairwise potential energy between particles $n$ and $m$, and $r_{nm}^2 = \delta_{ij}(x_n^i - x_m^i)(x_n^j - x_m^j)$.

---

### 6. Lagrangian Formalism

In analytical mechanics ([[Lagrangian mechanics]]), potential energy appears in the Lagrangian:

$$
\mathcal{L} = T - U = \frac{1}{2} m g_{ij} \dot{q}^i \dot{q}^j - U(q^i)
$$

where $q^i$ are the [[Generalized Coordinates]].

---

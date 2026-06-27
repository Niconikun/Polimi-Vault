#Physics-Concept #DONE 
### Formal Definition of a Rigid Body

A **Rigid Body** is an idealized **system of particles** in which the distance between any two points within the body remains constant over [[Time]], regardless of the external forces or torques applied to it.

Mathematically, this can be stated as:

For any two points $P$ and $Q$ in the body with position vectors $\mathbf{r}_P(t)$ and $\mathbf{r}_Q(t)$ at time $t$, the following constraint holds:

$$
\boxed{|\mathbf{r}_P(t) - \mathbf{r}_Q(t)| = \text{constant} \quad \forall \; t, \; \forall \; P, Q \in \text{Body}}
$$

This is the **rigidity condition**. It implies that the body can undergo only **translational** and **rotational** motion, with no deformation (stretching, squeezing, or bending).

---

### 1. Mathematical Consequences of the Rigidity Condition

The rigidity condition has profound mathematical implications that define the entire kinematics of rigid body motion.

#### **1.1 The Rotation Tensor**

The most important consequence is that the motion of a rigid body from one configuration to another can be described by a **[[translation]]** of an arbitrary reference point *plus* a **[[Rotation]]** about that point.

Let $\mathbf{X}$ be the position vector of a point in a fixed reference configuration, and $\mathbf{x}(t)$ be its position at time $t$. The motion is described by:

$$
\boxed{\mathbf{x}(t) = \mathbf{c}(t) + \mathbf{R}(t) \cdot \mathbf{X}}
$$

where:
*   $\mathbf{c}(t)$ is the position vector of the origin of the body-fixed frame (the [[translation]]).
*   $\mathbf{R}(t)$ is the **proper orthogonal rotation tensor** (or matrix).

#### **1.2 Properties of the Rotation Tensor**

The rotation tensor $\mathbf{R}$ must satisfy the **orthogonality condition**:

$$
\boxed{\mathbf{R}^T \cdot \mathbf{R} = \mathbf{R} \cdot \mathbf{R}^T = \mathbf{I}}
$$
and
$$
\boxed{\det(\mathbf{R}) = +1}
$$

In Einstein notation, the orthogonality condition is:
$$
R_{ik} R_{jk} = R_{ki} R_{kj} = \delta_{ij}
$$

This ensures that inner products and distances are preserved, as required by the rigidity condition.

---

### 2. Kinematics of Rigid Body Motion

#### **2.1 [[Velocity Field]]: The Fundamental Kinematic Equation**

The velocity $\mathbf{v}$ of any point in the rigid body can be found by differentiating its position:
$$
\mathbf{v} = \dot{\mathbf{x}} = \dot{\mathbf{c}} + \dot{\mathbf{R}} \cdot \mathbf{X}
$$

Using the fact that $\mathbf{X} = \mathbf{R}^T \cdot (\mathbf{x} - \mathbf{c})$, and defining the **[[Angular Velocity]] [[tensor]]** $\boldsymbol{\Omega} = \dot{\mathbf{R}} \cdot \mathbf{R}^T$, we arrive at the fundamental velocity equation:

$$
\boxed{\mathbf{v} = \mathbf{v}_O + \boldsymbol{\omega} \times (\mathbf{x} - \mathbf{x}_O)}
$$

where:
*   $\mathbf{v}_O = \dot{\mathbf{c}}$ is the velocity of the reference point $O$.
*   $\boldsymbol{\omega}$ is the **[[Angular Velocity]] vector**, which is the axial vector corresponding to the skew-symmetric tensor $\boldsymbol{\Omega}$.

In Einstein notation, the velocity of a point $P$ is:

$$
\boxed{v^i_P = v^i_O + \epsilon^{\ ijk} \omega_j (x_k - x_{O,k})}
$$

#### **2.2 [[Acceleration Field]]**

The acceleration is found by differentiating the [[velocity field]]:

$$
\mathbf{a} = \dot{\mathbf{v}} = \mathbf{a}_O + \boldsymbol{\alpha} \times (\mathbf{x} - \mathbf{x}_O) + \boldsymbol{\omega} \times [\boldsymbol{\omega} \times (\mathbf{x} - \mathbf{x}_O)]
$$

where $\boldsymbol{\alpha} = \dot{\boldsymbol{\omega}}$ is the **[[Angular Acceleration]]**.

In Einstein notation, this becomes:

$$
\boxed{a^i_P = a^i_O + \epsilon^{\ ijk} \alpha_j (x_k - x_{O,k}) + \epsilon^{\ ijk} \epsilon_{k}^{\ mn} \omega_j \omega_m (x_n - x_{O,n})}
$$

The last term is the centripetal acceleration.

---

### 3. Dynamics of Rigid Bodies

The dynamics are governed by the equations of motion for [[translation]] and rotation.

#### **3.1 Newton-Euler Equations of Motion**

These are the fundamental equations describing the motion of a rigid body.

*   **[[Translation]] ([[Newton's Second Law]]):**
    $$
    \boxed{\sum \mathbf{F}_{\text{ext}} = m \mathbf{a}_G}
    $$
    The sum of all external forces equals the total mass times the acceleration of the [[Center of Mass]] $G$. In component form:
    $$
    \sum F^i_{\text{ext}} = m a^i_G
    $$

*   **Rotation ([[Euler's Law]]):**
    $$
    \boxed{\sum \boldsymbol{\tau}_G = \frac{d \mathbf{L}_G}{dt}}
    $$
    The sum of all external [[torque]]s about the [[Center of Mass]] equals the time rate of change of the [[Angular Momentum]] about the center of mass.

Using the relationship between [[Angular Momentum]] and [[Angular Velocity]], $\mathbf{L}_G = \mathbf{I}_G \cdot \boldsymbol{\omega}$, Euler's equation in a body-fixed frame (where the [[inertia tensor]] is constant) becomes:

$$
\boxed{\sum \tau^i_G = I^{ij}_G \alpha_j + \epsilon^{ijk} \omega_j I_{kl} \omega_l}
$$

This is **Euler's Equations of Motion** in component form. The term $\epsilon^{ijk} \omega_j I_{kl} \omega_l$ represents the gyroscopic or Coriolis coupling terms.

---

### 4. The [[Inertia Tensor]]

The [[inertia tensor]] is the fundamental property that quantifies the mass distribution of a rigid body and its resistance to rotational acceleration.

For a continuous rigid body, the [[inertia tensor]] about a point $O$ is defined as:

$$
\boxed{I^{ij}_O = \int_V \rho(\mathbf{x}) \left( r^2 \delta^{ij} - x^i x^j \right) dV}
$$

where:
*   $\rho(\mathbf{x})$ is the mass [[density]].
*   $r^2 = \delta_{kl} x^k x^l$ is the square of the distance from point $O$.
*   The integral is taken over the volume $V$ of the body.

The components $I^{11}, I^{22}, I^{33}$ are the **moments of inertia**, and $I^{12}, I^{13}, I^{23}$ are the **products of inertia**.

---

### 5. [[Degrees of Freedom]]

A rigid body in 3D space has **6 [[Degrees of Freedom]]**:
*   **3 Translational:** Described by the coordinates of the center of mass $(x_G, y_G, z_G)$.
*   **3 Rotational:** Described, for example, by the three [[Euler angles]] $(\phi, \theta, \psi)$.

The configuration of a rigid body is completely specified by these 6 parameters.

---

### 6. Why is this Model so Powerful?

1.  **Dramatic Simplification:** It reduces a system with a vast number of particles (~$10^{23}$) to one with only 6 [[Degrees of Freedom]].
2.  **Separation of Motion:** It cleanly separates the complex motion into independent translational and rotational dynamics.
3.  **Solvability:** The Newton-Euler equations provide a complete set of solvable differential equations of motion.
4.  **Universality:** The formulation is applicable to everything from a spinning top to a maneuvering spacecraft.

### Summary

A **Rigid Body** is formally defined by the constraint $|\mathbf{r}_P - \mathbf{r}_Q| = \text{constant}$. This leads to a kinematics described by:
$$
\mathbf{x}(t) = \mathbf{c}(t) + \mathbf{R}(t) \cdot \mathbf{X} \quad \text{with} \quad \mathbf{R}^T\mathbf{R}=\mathbf{I}, \det(\mathbf{R})=+1
$$
and a [[velocity field]]:
$$
v^i_P = v^i_O + \epsilon^{\ ijk} \omega_j (x_k - x_{O,k})
$$

Its dynamics are governed by the **Newton-Euler Equations**:
*   **[[Translation]]:** $\sum F^i_{\text{ext}} = m a^i_G$
*   **Rotation:** $\sum \tau^i_G = I^{ij}_G \alpha_j + \epsilon^{ijk} \omega_j I_{kl} \omega_l$

The [[inertia tensor]] $I^{ij} = \int_V \rho (\delta^{ij} r^2 - x^i x^j) dV$ encapsulates the body's mass distribution. This elegant framework is the cornerstone for analyzing the motion of satellites, aircraft, robots, and any solid object where deformation is negligible.
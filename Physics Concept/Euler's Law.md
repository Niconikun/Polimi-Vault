#Physics-Concept #DONE 

### Formal Definition of Euler's Law

**Euler's Law**, also called the **Euler Equations of Motion**, is the fundamental principle governing the rotational [[Rigid-Body Dynamics]]. It states that the sum of all external [[Torque]]s acting about a body's [[Center of Mass]] equals the [[Time]] derivative of the [[Angular Momentum]], as observed from an [[Inertial Frame of Reference]].

When this relationship is expressed in a [[Body Reference Frame]] (which rotates with the body), it yields the celebrated Euler Equations, which explicitly show the [[Gyroscopic Coupling]] between axes.

---

### Vector Form

The most general form of Euler's Law in a body-fixed frame is:

$$
\sum \vec{M}_C = \mathbf{I}_C \cdot \frac{d\vec{\omega}}{dt} + \vec{\omega} \times (\mathbf{I}_C \cdot \vec{\omega})
$$

Where:
- $\sum \vec{M}_C$ is the [[Vector]] sum of external torques about the [[Center of Mass]].
- $\mathbf{I}_C$ is the [[Inertia Tensor]] of the body about the [[Center of Mass]].
- $\vec{\omega}$ is the [[Angular Velocity]] vector of the body.
- $\frac{d\vec{\omega}}{dt}$ is the [[Angular Acceleration]] vector.

---

### Component Form ([[Principal Axes of Inertia]])

When the body-fixed frame is aligned with the [[Principal Axes of Inertia]] of inertia (making the [[inertia tensor]] diagonal), the equations simplify to their most familiar scalar form, known as the **Euler Equations**:

$$
\begin{aligned}
M_x &= I_{xx} \dot{\omega}_x + (I_{zz} - I_{yy}) \omega_y \omega_z \\
M_y &= I_{yy} \dot{\omega}_y + (I_{xx} - I_{zz}) \omega_z \omega_x \\
M_z &= I_{zz} \dot{\omega}_z + (I_{yy} - I_{xx}) \omega_x \omega_y
\end{aligned}
$$

Where:
- $M_x, M_y, M_z$ are the components of the external [[torque]].
- $I_{xx}, I_{yy}, I_{zz}$ are the principal [[Moment of Inertia Tensor]].
- $\omega_x, \omega_y, \omega_z$ are the components of the [[Angular Velocity]].
- $\dot{\omega}_x, \dot{\omega}_y, \dot{\omega}_z$ are the components of the [[Angular Acceleration]].

---

### Einstein Notation Form

The general vector form of Euler's Law can be expressed compactly using **Einstein Notation** (or index notation), which implies summation over repeated indices.

The equation in a body-fixed frame is:

$$
M_i = I_{ij} \dot{\omega}_j + \epsilon_{ijk} \omega_j I_{kl} \omega_l
$$

Let's break down each term:

1.  **$M_i$**: The i-th component of the external [[torque]] vector ($i = 1, 2, 3$ corresponding to x, y, z axes).

2.  **$I_{ij} \dot{\omega}_j$**:
    - $I_{ij}$ is the [[inertia tensor]] component.
    - $\dot{\omega}_j$ is the j-th component of the [[Angular Acceleration]] vector.
    - The repeated index $j$ implies summation: $\sum_{j=1}^3 I_{ij} \dot{\omega}_j = I_{i1}\dot{\omega}_1 + I_{i2}\dot{\omega}_2 + I_{i3}\dot{\omega}_3$.
    - This term represents the part of the [[torque]] that causes a direct change in [[Angular Acceleration]].

3.  **$\epsilon_{ijk} \omega_j I_{kl} \omega_l$**:
    - $\epsilon_{ijk}$ is the [[Levi-Civita Symbol]] permutation symbol, defined as:
        - $ \epsilon_{ijk} = +1 $ if $(i, j, k)$ is an even permutation of (1,2,3) (e.g., 1,2,3 or 2,3,1 or 3,1,2)
        - $ \epsilon_{ijk} = -1 $ if $(i, j, k)$ is an odd permutation of (1,2,3) (e.g., 1,3,2 or 3,2,1 or 2,1,3)
        - $ \epsilon_{ijk} = 0 $ if any indices are repeated.
    - This symbol is used to express cross products compactly.
    - The repeated indices $j, k, l$ imply a triple summation: $\sum_{j=1}^3 \sum_{k=1}^3 \sum_{l=1}^3 \epsilon_{ijk} \omega_j I_{kl} \omega_l$.
    - This entire term is the Einstein notation equivalent of the gyroscopic term $\vec{\omega} \times (\mathbf{I} \cdot \vec{\omega})$.

#### Special Case: [[Principal Axes of Inertia]] in Einstein Notation

In the [[Principal Axes of Inertia]] frame, the [[inertia tensor]] is diagonal ($I_{ij} = 0$ for $i \neq j$), so we can write $I_{ij} = I_i \delta_{ij}$ (no sum), where $\delta_{ij}$ is the [[Kronecker delta]]. The equations simplify significantly. For example, for the x-component ($i=1$):

$$
M_1 = I_1 \dot{\omega}_1 + \epsilon_{1jk} \omega_j I_k \delta_{kl} \omega_l
$$

Evaluating the [[Levi-Civita symbol]] for $i=1$ (where non-zero terms occur for $j=2, k=3$ and $j=3, k=2$):

$$
\begin{aligned}
M_1 &= I_1 \dot{\omega}_1 + \epsilon_{123} \omega_2 I_3 \omega_3 + \epsilon_{132} \omega_3 I_2 \omega_2 \\
    &= I_1 \dot{\omega}_1 + (1)\omega_2 I_3 \omega_3 + (-1)\omega_3 I_2 \omega_2 \\
    &= I_1 \dot{\omega}_1 + (I_3 - I_2) \omega_2 \omega_3
\end{aligned}
$$

This recovers the first of the scalar Euler Equations presented earlier.

### Physical Interpretation and Significance

- **The Gyroscopic Term:** The term $\epsilon_{ijk} \omega_j I_{kl} \omega_l$ (or $\vec{\omega} \times (\mathbf{I} \cdot \vec{\omega})$) is the gyroscopic [[torque]]. It arises purely from the [[Rotation]] of the body-fixed coordinate system and represents the transfer of [[Angular Momentum]] between different axes. This is the source of non-intuitive phenomena like [[precession]].
- **Fundamental for Spacecraft Dynamics:** Euler's Equations form the core of spacecraft [[attitude]] dynamics modeling. They are numerically integrated alongside the kinematic equations (e.g., using quaternions) to predict the rotational motion of a spacecraft under the influence of control torques and environmental disturbances.

In summary, **Euler's Law** provides the complete differential equations that govern how a [[Rigid Body]]'s rotation evolves in time under applied torques, with the Einstein notation offering a powerful and compact representation of these fundamental relationships.
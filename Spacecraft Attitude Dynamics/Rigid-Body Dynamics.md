#SAD #DONE 
### Formal Definition of Rigid Body Dynamics

**[[Rigid Body]] [[Dynamics]]** is the branch of classical mechanics that describes the *motion* of a [[Rigid Body]] under the influence of *[[Force]]s* and *[[Torque]]s*. It establishes the causal relationship between the external loads applied to a body and the resulting translational and rotational motion, as described by [[Newton's second law]] and its rotational analogue, [[Euler's Law]].

The study of rigid body dynamics is divided into two complementary aspects:

1.  **Translational Dynamics:** Governs the motion of the body's [[Center of Mass]].
2.  **Rotational Dynamics:** Governs the change in the body's [[Angular Velocity]], or its rotation about the [[Center of Mass]].

These two motions are governed by separate sets of differential equations and can often be analyzed independently.

### Fundamental Equations and Concepts

The entire subject of rigid body dynamics is built upon two fundamental equations, often referred to as **Euler's Laws of Motion**.

#### 1. Equation for Translational Motion ([[Newton's Second Law]])

This law states that the sum of all external forces acting on a body is equal to the [[Time]] rate of change of its [[Linear Momentum]]. For a constant mass system, this simplifies to the mass times the [[acceleration]] of its [[Center of Mass]].

$$
\sum \vec{F}_{ext} = \frac{d}{dt}(m \vec{v}_{C})
$$

If the mass $m$ is constant, this becomes:

$$
\sum \vec{F}_{ext} = m \frac{d\vec{v}_{C}}{dt} = m \vec{a}_{C}
$$

Where:
*   $\sum \vec{F}_{ext}$ is the vector sum of all external forces.
*   $m$ is the total mass of the rigid body.
*   $\vec{v}_{C}$ and $\vec{a}_{C}$ are the velocity and [[acceleration]] vectors of the center of mass $C$, respectively, measured in an [[Inertial Frame of Reference]].

#### 2. Equation for Rotational Motion ([[Euler's Law]])

This law states that the sum of all external torques (or moments) acting *about the center of mass* is equal to the time rate of change of the [[Angular Momentum]] *about the center of mass*.

$$
\sum \vec{M}_{C} = \frac{d}{dt} (\vec{H}_{C})
$$

This is the most general form. The critical step is expressing the [[Angular Momentum]] $\vec{H}_{C}$. For a rigid body, the [[Angular Momentum]] about the center of mass is related to its [[Angular Velocity]] $\vec{\omega}$ and its inertia properties by:

$$
\vec{H}_{C} = \mathbf{I}_{C} \cdot \vec{\omega}
$$

Where:
*   $\sum \vec{M}_{C}$ is the vector sum of all external torques about the center of mass.
*   $\vec{H}_{C}$ is the [[Angular Momentum]] vector about the center of mass.
*   $\mathbf{I}_{C}$ is the **[[Inertia Tensor]]**, a 3x3 symmetric matrix that describes the mass distribution of the body relative to the center of mass.
*   $\vec{\omega}$ is the [[Angular Velocity]] vector of the body.

#### The Euler's Equation of Motion

Substituting the expression for [[Angular Momentum]] into [[Euler's Law]] and carefully evaluating the derivative in the inertial frame leads to the most famous equation in rotational dynamics, **Euler's Equation**:

$$
\sum \vec{M}_{C} = \mathbf{I}_{C} \cdot \frac{d\vec{\omega}}{dt} + \vec{\omega} \times (\mathbf{I}_{C} \cdot \vec{\omega})
$$

This vector equation is typically expressed in a body-fixed coordinate system where the [[inertia tensor]] $\mathbf{I}_{C}$ is constant. Written in scalar form for the body-fixed principal axes (where the [[inertia tensor]] is diagonal), these are the **Euler's Equations**:

$$
\begin{aligned}
\sum M_{x} &= I_{xx} \dot{\omega}_x + (I_{zz} - I_{yy}) \omega_y \omega_z \\
\sum M_{y} &= I_{yy} \dot{\omega}_y + (I_{xx} - I_{zz}) \omega_x \omega_z \\
\sum M_{z} &= I_{zz} \dot{\omega}_z + (I_{yy} - I_{xx}) \omega_x \omega_y
\end{aligned}
$$

Where:
*   $I_{xx}, I_{yy}, I_{zz}$ are the principal moments of inertia.
*   $\omega_x, \omega_y, \omega_z$ are the components of the [[Angular Velocity]] vector in the body-fixed principal frame.
*   $\dot{\omega}_x, \dot{\omega}_y, \dot{\omega}_z$ are the components of the [[Angular Acceleration]].

### Key Concepts in Rigid Body Dynamics

*   **[[Inertia Tensor]] ($\mathbf{I}$):** A mathematical object that captures how the mass of a rigid body is distributed relative to a specific point. It determines the relationship between [[Angular Velocity]] and [[Angular Momentum]]. Its diagonal elements are the **moments of inertia**, and its off-diagonal elements are the **products of inertia**.
*   **[[Center of Mass]]:** The unique point at which the weighted relative position of the distributed mass sums to zero. It is the point that translates as if all external forces were applied there.
*   **[[Principal Axes of Inertia]]:** A special set of body-fixed axes for which the products of inertia are zero. The [[inertia tensor]] becomes diagonal, greatly simplifying Euler's Equations. Finding the principal axes is a central problem in dynamics.
*   **[[Gyroscopic Effect]]:** The term $\vec{\omega} \times (\mathbf{I}_{C} \cdot \vec{\omega})$ in Euler's Equation represents a gyroscopic [[torque]]. It is the source of non-intuitive dynamic behavior, such as [[precession]], where an applied [[torque]] causes a [[Rotation]] perpendicular to the [[torque]] axis.

In summary, while **kinematics** provides the language to *describe* motion ([[position]], velocity, orientation), **dynamics** provides the physical laws and equations that *predict* that motion based on its causes (forces and torques). For a [[Spacecraft]], these equations form the core of its **[[Attitude]] Dynamics and Control System (ADCS)**, used to predict and control its orientation in space.
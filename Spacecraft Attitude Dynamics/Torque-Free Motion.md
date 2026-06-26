#SAD #DONE 
### Formal Definition of [[Torque]]-Free Motion

**[[Torque]]-Free Motion** is the rotational [[Dynamics]] of a [[Rigid Body]] in the absence of any external [[Torque]]s acting on it. Formally, this condition is expressed as:

$$
\sum \vec{M}_{ext} = \vec{0}
$$

Where $\sum \vec{M}_{ext}$ is the vector sum of all external torques applied about the body's [[Center of Mass]].

Under this condition, Euler's rotational equation of motion simplifies to:

$$
\frac{d\vec{H}}{dt} = \vec{0}
$$

This leads to the fundamental principle governing [[torque]]-free motion: **The [[Angular Momentum]] vector of the body, $\vec{H}$, is constant in both magnitude and direction when viewed from an inertial reference frame.**

### Key Characteristics and Consequences

While the inertial [[Angular Momentum]] vector  is constant, the body's motion is not necessarily simple. The dynamics are governed by the [[Conservation of Angular Momentum]] and [[Kinetic Energy]], and the body's specific mass distribution (its [[Inertia Tensor]]).

#### 1. Constant [[Angular Momentum]]
$$
\vec{H} = \mathbf{I} \cdot \vec{\omega} = \text{constant (in inertial space)}
$$

#### 2. Constant [[Rotational Kinetic Energy]]
For a [[Rigid Body]], the [[Rotational Kinetic Energy]] $T_{rot}$ is also conserved in [[torque]]-free motion.
$$
T_{rot} = \frac{1}{2} \vec{\omega} \cdot \vec{H} = \frac{1}{2} \vec{\omega} \cdot (\mathbf{I} \cdot \vec{\omega}) = \text{constant}
$$

#### 3. The Nature of the Motion: [[Polhodes and Energy Ellipsoids]]

The motion of the [[Angular Velocity]] vector $\vec{\omega}$ as seen from the body-fixed frame is described by the intersection of two conserved quantities:
*   The **[[Angular Momentum]] Ellipsoid**: $\vec{H} \cdot \vec{H} = H^2 = \text{constant}$
*   The **[[Kinetic Energy]] Ellipsoid**: $T_{rot} = \frac{1}{2} \vec{\omega} \cdot (\mathbf{I} \cdot \vec{\omega}) = \text{constant}$

The path traced by the tip of the $\vec{\omega}$ vector in the body frame is a closed curve called a **polhode**.

### Special Case: Motion about Principal Axes

The simplest form of [[torque]]-free motion occurs when the body is rotating purely about one of its **[[Principal Axes of Inertia]]**. In this case, the [[angular velocity]] vector is aligned with a principal axis, and there is no [[gyroscopic coupling]].

*   **[[Stability]] of Rotation**: A necessary and sufficient condition for stability is given by the **intermediate axis theorem** (or "tennis racket theorem"):
    *   [[Rotation]] about the **major** (maximum moment of inertia) and **minor** (minimum moment of inertia) principal axes is **stable**. A small disturbance will cause the body to wobble or *nutate* in a bounded, small oscillation around the principal axis.
    *   Rotation about the **intermediate** principal axis is **unstable**. Any infinitesimal disturbance will cause the body to tumble wildly, and the $\vec{\omega}$ vector will move far from its initial orientation.

### The General Motion: [[Nutation]]

For a general tri-inertia body ($I_{xx} \neq I_{yy} \neq I_{zz}$) not spinning about a principal axis, the [[torque]]-free motion consists of two superimposed rotations:

1.  **Spin:** A rapid rotation of the body about its instantaneous axis of symmetry (if it has one, like an axisymmetric satellite).
2.  **[[Nutation]]:** A slower, conical [[precession]] of the [[Angular Velocity]] vector $\vec{\omega}$ and the body's symmetry axis about the fixed direction of the [[Angular Momentum]] vector $\vec{H}$.

This results in a wobbling motion, which is a natural, unforced response of an asymmetric [[Rigid Body]].

### Summary and Application to [[Spacecraft]]

In summary, **[[torque]]-free motion** describes the natural tumbling or spinning of a spacecraft when no control torques or significant external [[Disturbance Torques]] (like gravity gradient or magnetic torques) are acting. It is a fundamental "baseline" behavior. Understanding it is critical for:
*   **Passive Stability:** Designing satellites to be naturally stable by ensuring they spin about their major principal axis.
*   **[[Attitude Determination]]:** Predicting the [[attitude]] of a tumbling spacecraft after deployment or before active control is engaged.
*   **Dynamics & Control:** Serving as the foundation for analyzing how control torques can be applied to alter this natural motion and achieve a desired orientation.
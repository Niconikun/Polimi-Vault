#Physics-Concept #DONE 
### Formal Definition of the Center of Mass

The **Center of Mass** (CM) of a body or a system of bodies is the unique point in space where the weighted relative position of the distributed mass sums to zero. It is the point at which the entire mass of an object can be considered to be concentrated for the purpose of analyzing translational motion.

### Mathematical Formulation

The position vector of the center of mass, $\vec{R}_{CM}$, for a system of particles is defined as the mass-weighted average of the [[Position]] [[Vector]]s of all constituent particles:

$$
\vec{R}_{CM} = \frac{1}{M} \sum_{i=1}^{n} m_i \vec{r}_i
$$

Where:
- $m_i$ is the mass of the $i$-th particle.
- $\vec{r}_i$ is the position vector of the $i$-th particle.
- $M = \sum_{i=1}^{n} m_i$ is the total mass of the system.
- $n$ is the number of particles.

For a continuous [[Rigid Body]] with a [[Density]] distribution $\rho(\vec{r})$, the definition generalizes to a volume integral:

$$
\vec{R}_{CM} = \frac{1}{M} \int_V \vec{r}  \rho(\vec{r})  dV
$$

In Cartesian coordinates $(x, y, z)$, the coordinates of the center of mass are given by:

$$
X_{CM} = \frac{1}{M} \int_V x  \rho(x, y, z)  dV
$$
$$
Y_{CM} = \frac{1}{M} \int_V y  \rho(x, y, z)  dV
$$
$$
Z_{CM} = \frac{1}{M} \int_V z  \rho(x, y, z)  dV
$$

### Fundamental Properties and Physical Significance

1.  **Motion under External [[Force]]s:** The center of mass moves as if it were a point particle with the total mass of the system, acted upon by the vector sum of all external forces. This is described by [[Newton's Second Law]]:
    $$
    \sum \vec{F}_{ext} = M \frac{d^2\vec{R}_{CM}}{dt^2} = M \vec{A}_{CM}
    $$
    This means that regardless of the [[Internal Forces]] or rotations, the trajectory of the center of mass is determined solely by the net external force.

2.  **[[Torque]] and [[Rotation]]:** When analyzing rotational dynamics using Euler's equation [[Euler's Law]] ($\sum \vec{M}_C = \mathbf{I}_C \cdot \dot{\vec{\omega}} + \vec{\omega} \times (\mathbf{I}_C \cdot \vec{\omega})$), the torques and the moment of [[inertia tensor]] must be calculated *about the center of mass* for this general form to be valid. If another point is chosen, the equations become significantly more complex.

3.  **Simplification of [[Newton’s Universal Law of Gravitation]]:** In a uniform gravitational field, the net gravitational [[torque]] about the center of mass is zero. The gravitational force can be treated as acting entirely at this point, causing no net rotation. This is why the Center of Mass is often synonymous with the **Center of Gravity** in a uniform field.

### Application to Spacecraft Dynamics

In the context of spacecraft [[attitude]] dynamics and control, the center of mass is of paramount importance:

- **Attitude Control Thrusters:** Control thrusters are designed to produce torques about the center of mass. If a thruster's line of force does not pass through the CM, it will produce an unwanted translational [[acceleration]] (a "coupling") in addition to the desired torque.
- **Dynamic Balancing:** A rotating spacecraft must be dynamically balanced, meaning its principal axis of inertia must be aligned with its spin axis and pass through the center of mass. An offset between the center of mass and the geometric center of rotation leads to a wobble, requiring constant control effort to counteract.
- **Orbital and Attitude Coupling:** While orbital motion is the trajectory of the center of mass, and attitude motion is the rotation about it, these can be coupled. For example, a non-spherical mass distribution in a non-uniform gravitational field (like Earth's) experiences gravity gradient torques that depend on the location of the CM relative to other parts of the spacecraft.

In summary, the **Center of Mass** is the key reference point that decouples the complex motion of a [[Rigid Body]] into two simpler problems: the **translation** of the center of mass and the **rotation** about the center of mass. Its precise identification and management are critical for the stable operation of any spacecraft.
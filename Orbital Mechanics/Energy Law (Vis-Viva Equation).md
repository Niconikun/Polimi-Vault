 #Orbital-Mechanics #DONE 

### **Formal Definition: The Energy Law (Vis-Viva Equation)**

In the [[Two-Body Problem]] of orbital mechanics, the **Energy Law** states that the [[Specific Orbital Energy]] (total energy per unit mass) of an orbiting body remains constant throughout its [[Orbit]]. This energy is the sum of the body's specific [[Kinetic Energy]] and its specific [[Potential Energy]].

This conservation principle leads directly to the **Vis-Viva Equation** ("living force"), which relates the instantaneous [[Velocity]]  of an orbiting body to its current radial distance  [[Position]] from the primary body and the [[Semi-Major Axis]] axis of its orbit.

### **Mathematical Formulation**

The **Vis-Viva Equation** is given by:

$$
v^2 = GM \left( \frac{2}{r} - \frac{1}{a} \right)
$$

Where:
*   $v$ is the relative speed of the orbiting body at a given point in its orbit.
*   $G$ is the Universal Gravitational Constant.
*   $M$ is the mass of the central body.
*   $r$ is the distance from the center of the central body to the orbiting body.
*   $a$ is the [[Semi-Major Axis]] of the orbit.

The **[[Specific Orbital Energy]]** $\epsilon$, which the Vis-Viva equation derives from, is:

$$
\epsilon = \frac{v^2}{2} - \frac{GM}{r} = -\frac{GM}{2a}
$$

### **Detailed Explanation and Implications**

1.  **[[Conservation of Energy]]:** The equation $\epsilon = -\frac{GM}{2a}$ shows that the [[Specific Orbital Energy]] is a function **only** of the [[Semi-Major Axis]] $a$. For a given orbit, $a$ is constant, and therefore the total energy is constant. Energy is exchanged between kinetic and potential forms, but their sum remains unchanged.

2.  **Interpretation of the Vis-Viva Equation:**
    *   **At [[Periapsis]]** (closest approach, $r = r_p = a(1-e)$): The [[potential energy]] is at its minimum (most negative), so the [[Kinetic Energy]] must be at its maximum, resulting in the highest velocity $v_p$.
    *   **At [[Apoapsis]]** (farthest point, $r = r_a = a(1+e)$): The potential energy is at its maximum (less negative), so the [[Kinetic Energy]] is at its minimum, resulting in the lowest velocity $v_a$.

3.  **Orbit Classification by Energy:** The [[Specific Orbital Energy]] $\epsilon$ determines the type of orbit:
    *   **[[Elliptical Orbit]]s ($a > 0$):** $\epsilon < 0$. The object is **bound** to the central body. Its [[Kinetic Energy]] is less than the absolute value of its potential energy.
    *   **[[Parabollic Orbit]] Trajectory ($a \to \infty$):** $\epsilon = 0$. This is the escape trajectory. The object has just enough [[Kinetic Energy]] to reach infinity with zero residual velocity. The Vis-Viva equation simplifies to $v^2 = \frac{2GM}{r}$, which is the **[[Escape Velocity]]**.
    *   **[[Hyperbolic Trajectory]] Trajectory ($a < 0$):** $\epsilon > 0$. The object is **unbound**. It has excess [[Kinetic Energy]] and will reach infinity with a positive residual velocity, known as the [[Hyperbolic Excess Velocity]] $v_\infty$.

### **Key Significance**

*   **Fundamental Tool for Calculation:** The Energy Law is one of the most practical tools in orbital mechanics. It allows for the direct calculation of a spacecraft's velocity at any point in its orbit if the distance and [[Semi-Major Axis]] are known, without needing to know the orbital [[Eccentricity]] or the [[True Anomaly]].
*   **Mission Design:** It is essential for designing orbital maneuvers. For example, to transfer from one [[circular orbit]] to another, the required velocity changes ($\Delta v$) are calculated using the energy differences between the orbits.
*   **Link to Kepler's Laws:** While Kepler's Laws are geometric, the Energy Law is dynamic. It provides the physical "why" behind Kepler's observations, showing that the varying planetary speed is a direct result of energy conservation. [[Kepler's Time Law]] [[Conservation of Energy]]

In summary, the **Energy Law (Vis-Viva Equation)** is a fundamental conservation law that governs orbital motion. It provides a powerful and direct relationship between an object's position, velocity, and the size of its orbit, and it serves as the primary criterion for classifying trajectories as bound or unbound.
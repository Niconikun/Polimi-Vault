#Orbital-Mechanics #DONE 

### Formal Definition of Escape Velocity

The **Escape Velocity** ($v_e$) from a celestial body is the minimum speed that an object must have at a given point in a gravitational field to theoretically escape from that body's gravitational influence without any further propulsion, assuming a non-rotating, spherically symmetric body and neglecting other forces (like [[atmospheric drag]] or the gravitational pull of other bodies).

Mathematically, it is the speed where the object's total mechanical energy (kinetic + potential) is exactly zero, allowing it to asymptotically approach zero velocity at an infinite distance.

---

### 1. Derivation from Energy Conservation

The most fundamental definition comes from the conservation of mechanical energy [[Energy Law (Vis-Viva Equation)]] [[Planetary Constant]]. The total specific energy (energy per unit mass) for an object in a gravitational field is:

$$
E = \frac{1}{2} v^2 - \frac{GM}{r}
$$

where:
- $v$ is the object's speed
- $G$ is the gravitational constant
- $M$ is the mass of the celestial body
- $r$ is the distance from the center of the body

To escape, the object must reach infinity ($r \to \infty$) with zero [[Kinetic Energy]] ($v = 0$). Setting the total energy at infinity to zero:

$$
E_{\infty} = 0
$$

Since energy is conserved, the total energy at the starting point must also be zero:

$$
\frac{1}{2} v_e^2 - \frac{GM}{r} = 0
$$

Solving for $v_e$ gives the formal definition:

$$
\boxed{v_e = \sqrt{\frac{2GM}{r}}}
$$

---

### 2. Expression using Einstein Notation

While escape velocity is a scalar quantity, we can express the [[Kinetic Energy]] term in its derivation using Einstein notation. The condition for escape becomes:

$$
\frac{1}{2} \delta_{ij} v^i v^j - \frac{GM}{\sqrt{\delta_{kl} x^k x^l}} = 0
$$

where:
- $\delta_{ij}$ is the [[Kronecker Delta]] ([[Metric Tensor]] for Euclidean space)
- $v^i$ are the velocity components
- $x^k$ are the position vector components from the [[Center of Mass]]

Solving for the magnitude $v = \sqrt{\delta_{ij} v^i v^j}$ yields the same result:

$$
\boxed{v_e = \sqrt{\frac{2GM}{\sqrt{\delta_{kl} x^k x^l}}} = \sqrt{\frac{2GM}{r}}}
$$

---

### 3. Alternative Forms and Relationships

#### **3.1 In Terms of Surface Gravity**

The gravitational acceleration at distance $r$ is $g(r) = \frac{GM}{r^2}$. Therefore:

$$
\boxed{v_e = \sqrt{2g(r) r}}
$$

At the surface of a planet with radius $R$ and surface gravity $g_0 = \frac{GM}{R^2}$:

$$
v_e = \sqrt{2g_0 R}
$$

#### **3.2 In Terms of Orbital Velocity**

For a [[Circular Orbit]] at radius $r$, the orbital velocity is $v_c = \sqrt{\frac{GM}{r}}$. Comparing with escape velocity:

$$
\boxed{v_e = \sqrt{2} \, v_c}
$$

Escape velocity is exactly $\sqrt{2} \approx 1.414$ times the circular orbital velocity at the same radius.

#### **3.3 Relativistic Correction**

In general relativity, the escape velocity from a non-rotating spherical mass is modified to:

$$
v_e = c \sqrt{1 - \left(1 - \frac{r_s}{r}\right)^2}
$$

where $r_s = \frac{2GM}{c^2}$ is the Schwarzschild radius, and $c$ is the speed of light. For $r \gg r_s$, this reduces to the classical expression.

---

### 4. Important Properties and Implications

#### **4.1 Direction Independence**

A remarkable property is that escape velocity is independent of the direction of projection (for a non-rotating sphere). The object can be launched vertically, horizontally, or at any angle—the required speed magnitude is the same.

#### **4.2 Black Hole Connection**

When $r = r_s = \frac{2GM}{c^2}$, the classical escape velocity equals the speed of light. This defines the event horizon of a black hole in Newtonian terms, though the full general relativistic treatment is required for accuracy.

#### **4.3 Multi-body Systems**

For escape from a system of multiple bodies (e.g., escaping the [[Solar System]] from Earth), the concept becomes more complex. The required speed depends on the object's trajectory and gravitational assists.

---

### 5. Examples for Celestial Bodies

| Body | Mass (kg) | Radius (m) | Escape Velocity (km/s) |
|------|-----------|------------|------------------------|
| Earth | $5.97 \times 10^{24}$ | $6.37 \times 10^6$ | 11.2 |
| Moon | $7.35 \times 10^{22}$ | $1.74 \times 10^6$ | 2.38 |
| Sun | $1.99 \times 10^{30}$ | $6.96 \times 10^8$ | 617.5 |
| Mars | $6.42 \times 10^{23}$ | $3.39 \times 10^6$ | 5.03 |

### 6. Practical Considerations

1.  **[[Atmospheric Drag]]:** Real launch vehicles must achieve speeds greater than escape velocity to overcome atmospheric resistance.
2.  **Staged Propulsion:** Rockets don't need to reach escape velocity immediately; they can achieve it gradually through continuous propulsion.
3.  **Orbital Mechanics:** In practice, spacecraft use transfer orbits and gravitational assists rather than directly achieving escape velocity from the planet's surface.

### Summary

The escape velocity is formally defined as:

$$
\boxed{v_e = \sqrt{\frac{2GM}{r}}}
$$

This represents the minimum speed required at a distance $r$ from the center of a mass $M$ to achieve a total mechanical energy of zero, allowing the object to theoretically reach infinity with zero residual velocity. It is a fundamental benchmark in astronautics and celestial mechanics, determining which bodies can retain atmospheres and what energy is required for interplanetary travel. The factor of $\sqrt{2}$ relationship with circular orbital velocity makes it a key parameter in mission planning and trajectory design for space exploration.
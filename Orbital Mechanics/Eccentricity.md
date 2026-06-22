#Physics-Concept #Math-Concepts #Orbital-Mechanics #DONE 
### Formal Definition of Orbital Eccentricity

The **orbital eccentricity** ($e$) is a dimensionless scalar parameter that defines the shape of a conic section orbit. It quantifies the deviation of the orbit from a perfect circle.

A [[Conic Sections]] is the curve formed by the intersection of a plane with a cone. The type of conic section—and thus the orbit—is determined by the eccentricity:

- $e = 0$: Circle
- $0 < e < 1$: Ellipse
- $e = 1$: Parabola
- $e > 1$: Hyperbola

---

### 1. Geometric Definition

The most fundamental definition relates to the geometry of a [[Conic Sections]]. A conic can be defined as the set of points for which the ratio of the distance to a fixed point (the focus) and the distance to a fixed line (the directrix) is a constant, which is the eccentricity.

For an orbit with the central body at one focus $F$, and a point $P$ on the orbit:

$$
\boxed{e = \frac{\text{Distance from } P \text{ to } F}{\text{Distance from } P \text{ to the Directrix}}}
$$

This ratio is constant for all points $P$ on the orbit.

---

### 2. Definition via the Orbit Equation (Polar Form)

The equation of an orbit in polar coordinates, with the central body at the origin (a focus), is given by:

$$
\boxed{r(\theta) = \frac{p}{1 + e \cos \theta}}
$$

where:
- $r$ is the radial distance from the central body
- $\theta$ is the [[True Anomaly]] (the angle from the point of closest approach, or [[Periapsis]])
- $p$ is the [[semi-latus rectum]], a geometric parameter
- $e$ is the orbital eccentricity

This equation explicitly defines the orbit's shape, with $e$ as the controlling parameter.

---

### 3. Dynamical Definitions (in terms of Orbital Energy and [[Angular Momentum]])

Eccentricity can be derived from the constants of motion in the [[two-body problem]].

#### **3.1 In Terms of [[Specific Orbital Energy]] and [[Angular Momentum]]**

The [[Specific Orbital Energy]] ($\epsilon$) and specific [[Angular Momentum]] ($h$) are conserved. The eccentricity is related to them by:

$$
\boxed{e = \sqrt{1 + \frac{2 \epsilon h^2}{\mu^2}}}
$$

where:
- $\epsilon = \frac{v^2}{2} - \frac{\mu}{r}$ is the [[Specific Orbital Energy]] (kinetic + potential)
- $h = |\mathbf{r} \times \mathbf{v}|$ is the magnitude of the specific [[Angular Momentum]]
- $\mu = G(M + m)$ is the [[Standard Gravitational Parameter]] of the system

This is a profoundly important definition as it links the shape of the orbit ($e$) directly to the dynamical state of the orbiting body (its energy and [[Angular Momentum]]).

#### **3.2 For Elliptical Orbits ($0 \le e < 1$)**

For the important case of [[Elliptical Orbit]]s, eccentricity has a simple geometric definition:

$$
\boxed{e = \frac{c}{a} = \sqrt{1 - \left(\frac{b}{a}\right)^2}}
$$

where:
- $a$ is the [[Semi-Major Axis]]
- $b$ is the semi-minor axis
- $c$ is the linear eccentricity (the distance from the center of the ellipse to a focus)

---

### 4. Definition using the Eccentricity Vector (Laplace-Runge-Lenz Vector)

The most elegant and vectorial definition of eccentricity uses the **eccentricity vector** ($\mathbf{e}$), which is a conserved quantity in the [[two-body problem]] (for an inverse-square law force).

$$
\boxed{\mathbf{e} = \frac{\mathbf{v} \times \mathbf{h}}{\mu} - \frac{\mathbf{r}}{r}}
$$

The **orbital eccentricity** $e$ is the magnitude of this vector:

$$
e = |\mathbf{e}|
$$

The direction of $\mathbf{e}$ points from the central body towards the [[Periapsis]] (point of closest approach).

**In Einstein Notation**, the components of the eccentricity vector are:

$$
\boxed{e^i = \frac{\epsilon^{ijk} v_j h_k}{\mu} - \frac{x^i}{r}}
$$

where:
- $e^i$ are the components of the eccentricity vector
- $\epsilon^{ijk}$ is the [[Levi-Civita symbol]]
- $v_j$ are the velocity components
- $h_k$ are the components of the specific [[Angular Momentum]] vector
- $x^i$ are the position vector components
- $r = \sqrt{\delta_{mn} x^m x^n}$ is the orbital distance

---

### 5. Physical Interpretation and Ranges

The value of $e$ directly determines the orbit type:

| Eccentricity | Orbit Type | Total Energy ($\epsilon$) | Description |
|-------------|------------|----------------------------|-------------|
| $e = 0$ | Circle | $\epsilon < 0$ | Constant orbital distance |
| $0 < e < 1$ | Ellipse | $\epsilon < 0$ | Bound orbit, periodic |
| $e = 1$ | Parabola | $\epsilon = 0$ | Escape trajectory, marginally unbound |
| $e > 1$ | Hyperbola | $\epsilon > 0$ | Unbound orbit (flyby) |

---

### 6. Relationship to Orbital Velocities

Eccentricity relates to the velocity at different points in the orbit. For example, using the [[Energy Law (Vis-Viva Equation)]]:

$$
v^2 = \mu \left( \frac{2}{r} - \frac{1}{a} \right)
$$

The velocities at [[Periapsis]] ($r_p$) and [[Apoapsis]] ($r_a$) are:

$$
v_p = \sqrt{\frac{\mu}{a} \cdot \frac{1+e}{1-e}}, \quad v_a = \sqrt{\frac{\mu}{a} \cdot \frac{1-e}{1+e}}
$$

The eccentricity can be expressed as:

$$
e = \frac{v_p - v_a}{v_p + v_a}
$$

---

### 7. Example: Earth's Orbit

Earth's orbit around the Sun has an eccentricity of $e \approx 0.0167$, which is very close to circular. This small eccentricity is responsible for the variation in solar irradiance throughout the year and the slight difference in the lengths of the seasons.

### Summary

Orbital eccentricity ($e$) is formally defined through multiple equivalent approaches:

- **Geometrically:** $e = c/a$ for ellipses, or as the constant ratio of distances to focus and directrix
- **Dynamically:** $e = \sqrt{1 + \frac{2 \epsilon h^2}{\mu^2}}$ from orbital energy and [[Angular Momentum]]
- **Vectorially:** $e = |\mathbf{e}|$ where $\mathbf{e} = \frac{\mathbf{v} \times \mathbf{h}}{\mu} - \frac{\mathbf{r}}{r}$

The Einstein notation provides a compact way to express the components of the eccentricity vector, which points toward [[Periapsis]] and whose magnitude defines the orbit's shape. This parameter is fundamental to understanding and predicting orbital motion, from planetary orbits to spacecraft trajectories.
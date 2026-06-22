#DONE #Orbital-Mechanics
### **1. Problem Setup**
Given:
- Two [[position]] vectors: **$\mathbf{r}_1$** and **$\mathbf{r}_2$** (magnitudes $r_1$and $r_2$).
- Time of flight: **$\Delta t = t_2 - t_1$**.
- Gravitational parameter: **$\mu$**.

Goal:
Find the **[[Velocity]] [[Vector]]** **$\mathbf{v}_1$** and **$\mathbf{v}_2$** at [[Position]] **$\mathbf{r}_1$** and **** such that the trajectory satisfies the [[Two-Body Problem]] and the [[Time]] constraint.

---

### **2. Key Assumptions**
1. **Two-Body Motion**: Only the central body’s gravity acts on the spacecraft (no perturbations).
2. **[[Inertial Frame of Reference]]**: Positions and velocities are defined in an inertial reference frame.
3. **[[Conic Sections]] Orbits**: The transfer orbit is a conic section (ellipse, parabola, or hyperbola) with the central body at one focus.

---

### **3. Geometric Relationships**
#### **3.1. Chord and Transfer Angle**
- The **chord length** is the straight-line distance between **$\mathbf{r}_1$** and **$\mathbf{r}_2$**:
  $$
  c = |\mathbf{r}_2 - \mathbf{r}_1|.
  $$
- The **transfer angle** ($\Delta \theta$) is the angle between **$\mathbf{r}_1$** and **$\mathbf{r}_2$** as seen from the central body:
  $$
  \cos \Delta \theta = \frac{\mathbf{r}_1 \cdot \mathbf{r}_2}{r_1 r_2}.
  $$

#### **3.2. [[Semi-Major Axis]] and [[Eccentricity]]**
For an elliptic orbit, the **[[Semi-Major Axis]]** ($a$) and **[[Eccentricity]]** ($e$) are related to the radii and chord via:
$$
r_1 + r_2 = 2a (1 - e \cos \alpha),
$$
$$
c = 2a e \sin \alpha,
$$
where **$\alpha$** is the **[[True Anomaly]]** of the chord’s bisector. However, these relationships are not directly solvable for $a$and $e$without additional constraints.

---

### **4. Time of Flight and Lambert’s Equation**
The time of flight **$\Delta t$** is the integral of the orbital motion over the transfer angle. For [[Conic Sections]], this integral can be expressed using **Kepler’s equation** (for ellipses) or its hyperbolic/parabolic analogs. However, a **universal formulation** (valid for [[Conic Sections|all conic sect]]ions) is more practical.

#### **4.1. Universal Variables (Battin’s Approach)**
Introduce the **universal anomaly** ($\chi$), which unifies the treatment of [[Conic Sections]]. The time of flight is expressed as:
$$
\Delta t = \frac{r_1 r_2 \sin \Delta \theta}{\sqrt{\mu}} \left( \frac{\chi^3 S(\chi^2)}{6} + \frac{\chi}{2} \right) + \frac{r_1 + r_2 - c}{2} \sqrt{\frac{a^3}{\mu}},
$$
where:
- $S(z)$ is the **Stumpff function**(a series expansion for handling [[Conic Sections]] uniformly):
  $$
  S(z) = \frac{\sqrt{z} - \sin \sqrt{z}}{(\sqrt{z})^3} \quad \text{(for $z > 0$, ellipse)},
  $$
  $$
  S(z) = \frac{\sinh \sqrt{-z} - \sqrt{-z}}{(\sqrt{-z})^3} \quad \text{(for $z < 0$, hyperbola)},
  $$
  $$
  S(0) = \frac{1}{6} \quad \text{(parabola)}.
  $$
- The **[[Semi-Major Axis]]** ($a$) is related to $\chi$ via:
  $$
  r_1 + r_2 + c = 4a \sin^2 \left( \frac{\Delta \theta}{2} + \frac{\chi^2 S(\chi^2)}{2} \right).
  $$

#### **4.2. Lambert’s Equation**
The core of the problem reduces to solving for $\chi$ in the **universal Lambert equation**:
$$
\sqrt{\mu} \Delta t = \alpha \chi^3 S(\chi^2) + \beta \chi,
$$
where:
$$
\alpha = r_1 r_2 \sin \Delta \theta,
$$
$$
\beta = r_1 + r_2 - c.
$$
This is a **transcendental equation** in $\chi$ and is typically solved numerically (e.g., using [[Newton-Raphson Method]] iteration).

---
### **5. Solving for Velocities**
Once $\chi$ is found, the **Lagrange coefficients** ($f, g, \dot{f}, \dot{g}$) are computed to determine the velocities:
$$
\mathbf{v}_1 = \frac{1}{g} (\mathbf{r}_2 - f \mathbf{r}_1),
$$
$$
\mathbf{v}_2 = \frac{1}{g} (\dot{g} \mathbf{r}_2 - \mathbf{r}_1),
$$
where:
- $f = 1 - \frac{\chi^2}{r_1} S(\chi^2)$,
- $g = \Delta t - \frac{\chi^3}{\sqrt{\mu}} S(\chi^2)$,
- $\dot{f} = \frac{\sqrt{\mu}}{r_1 r_2} \chi \left( \frac{\chi S(\chi^2) - 1}{\chi^2 S(\chi^2)} \right)$,
- $\dot{g} = 1 - \frac{\chi^2}{r_2} S(\chi^2)$.

---
### **6. Special Cases and Validations**
1. **Minimum-Energy ([[Hohmann Transfer]])**:
   - For coplanar circular orbits, the solution reduces to the [[Hohmann Transfer]] when $\Delta t$ is half the [[orbital period]] of the transfer ellipse.
1. **Parabolic Trajectory**:
   - When $a \to \infty$, the Stumpff functions simplify, and the time of flight becomes:
     $$
     \Delta t = \frac{1}{2} \sqrt{\frac{(r_1 + r_2 + c)^3}{2\mu}}.
     $$
1. **[[Hyperbolic Trajectory]]**:
   - For $a < 0$, the Stumpff functions use hyperbolic sine/cosine, and the solution represents a flyby or escape trajectory.

---
### **7. Numerical Solution Workflow**
1. **Compute Geometric Quantities**:
   - Calculate $c$, $\Delta \theta$, $\alpha$, and $\beta$ from **$\mathbf{r}_1$** and **$\mathbf{r}_2$**.
1. **Solve for $\chi$**:
   - Use an iterative method (e.g., [[Newton-Raphson Method]]) to solve Lambert’s equation for $\chi$.
1. **Compute Lagrange Coefficients**:
   - Evaluate $f, g, \dot{f}, \dot{g}$ using $\chi$ and the Stumpff functions.
1. **Determine Velocities**:
   - Plug the Lagrange coefficients into the velocity equations to get **$\mathbf{v}_1$** and **$\mathbf{v}_2$**.

---
### **8. Challenges and Considerations**
- **Multiple Solutions**: For a given $\Delta t$, there may be **two valid orbits** (short-way and long-way transfers) or none if $\Delta t$ is too small/large.
- **Numerical Stability**: The Stumpff functions and iterative solvers must handle edge cases (e.g., near-parabolic trajectories).
- **Revolutions**: For multi-revolution transfers ($N > 0$), the time of flight includes additional orbital periods:
  $$
  \Delta t = \Delta t_{\text{direct}} + N \cdot 2\pi \sqrt{\frac{a^3}{\mu}}.
  $$

---
### **9. Example: Deriving the [[Hohmann Transfer]]**
For a [[Hohmann Transfer]] between two circular orbits with radii $r_1$ and $r_2(r_2 > r_1)$:
1. The [[Semi-Major Axis]] of the transfer ellipse is:
   $$
   a = \frac{r_1 + r_2}{2}.
   $$
2. The time of flight is half the [[orbital period]] of the transfer ellipse:
   $$
   \Delta t = \pi \sqrt{\frac{a^3}{\mu}}.
   $$
3. The velocities at **$\mathbf{r}_1$** and **$\mathbf{r}_2$** are computed using the vis-viva equation:
   $$
   v_1 = \sqrt{\mu \left( \frac{2}{r_1} - \frac{1}{a} \right)},
   $$
   $$
   v_2 = \sqrt{\mu \left( \frac{2}{r_2} - \frac{1}{a} \right)}.
   $$

---
### **10. Modern Algorithms**
- **[[Battin’s Method]]**: Uses the universal variable $\chi$ and Stumpff functions for robustness.
- **[[Gooding’s Method]]**: An alternative formulation using hyperbolic functions for improved convergence.
- **[[Izzo’s Algorithm]]**: A recent approach using **householder transformations** for faster convergence in numerical solvers.

---
### **11. Pseudocode for Numerical Solution**
```python
def solve_lambert(r1, r2, delta_t, mu):
    c = norm(r2 - r1)
    delta_theta = acos(dot(r1, r2) / (norm(r1) * norm(r2)))
    alpha = r1 * r2 * sin(delta_theta)
    beta = r1 + r2 - c

    # Initial guess for chi (e.g., using Lagrange's approximation)
    chi_initial = sqrt(beta / (2 * alpha))

    # Newton-Raphson iteration to solve Lambert's equation
    chi = newton_raphson(chi_initial, alpha, beta, delta_t, mu)

    # Compute Lagrange coefficients
    f, g, f_dot, g_dot = compute_lagrange_coefficients(chi, r1, r2, delta_t, mu)

    # Compute velocities
    v1 = (r2 - f * r1) / g
    v2 = (g_dot * r2 - r1) / g
    return v1, v2
```

---
### **12. Further Reading**
- **Battin (1999)**: *An Introduction to the Mathematics and Methods of Astrodynamics* (detailed derivation of universal variables).
- **Vallado (2013)**: *Fundamentals of Astrodynamics and Applications* (practical algorithms).
- **Izzo (2015)**: *Revisiting Lambert’s Problem* (modern numerical methods).

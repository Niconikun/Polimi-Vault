---
title: Attitude
tags:
  - spacecraft dynamics
  - orbital mechanics
  - orientation
  - angular motion
---

# Attitude

## Formal Definition

**Attitude** is the three-dimensional orientation of a spacecraft (or any rigid body) relative to a reference frame (typically inertial or orbital). Characterized mathematically by rotation matrices, quaternions, or Euler angles, attitude describes which way the spacecraft is pointing. Attitude is fundamental to spacecraft operations: solar panels must point toward the sun, antennas toward Earth, instruments toward targets. Unlike [[Orbital Mechanics|orbital state]] (position and velocity), attitude concerns rotational motion about the spacecraft's center of mass. Understanding attitude is essential to [[Attitude Determination and Control System (ADCS)|ADCS]], mission planning, and spacecraft dynamics.

## Historical Development

### Key Milestones
- **1957–1960s:** Early satellites use passive stabilization (spin, gravity gradient)
- **1960–1970:** Active three-axis control developed (Apollo, Skylab)
- **1970–1980:** Mathematical frameworks (quaternions, Davenport, TRIAD)
- **1980–Present:** Real-time attitude determination algorithms; feedback control

### Foundational Contributors
1. **Leonhard Euler (1707–1783):** Euler angles; rotational dynamics
2. **William Rowan Hamilton (1805–1865):** Quaternion algebra
3. **George Davenport (1923–1990):** Attitude determination algorithms
4. **Wernher von Braun (1912–1970):** Applied control to rockets/spacecraft

## Attitude Representation

### Euler Angles

**Three successive rotations:**
$$
\mathbf{R} = R_z(\psi) R_y(\theta) R_x(\phi)
$$

Where:
- $\phi$ (roll): Rotation about x-axis [−π, π]
- $\theta$ (pitch): Rotation about y-axis [−π/2, π/2]
- $\psi$ (yaw): Rotation about z-axis [−π, π]

**Resulting rotation matrix:**
$$
\mathbf{R} = \begin{bmatrix}
\cos\psi\cos\theta & \cos\psi\sin\theta\sin\phi - \sin\psi\cos\phi & \cos\psi\sin\theta\cos\phi + \sin\psi\sin\phi \\
\sin\psi\cos\theta & \sin\psi\sin\theta\sin\phi + \cos\psi\cos\phi & \sin\psi\sin\theta\cos\phi - \cos\psi\sin\phi \\
-\sin\theta & \cos\theta\sin\phi & \cos\theta\cos\phi
\end{bmatrix}
$$

**Conventions:**
- 3-1-3 (Z-X-Z): Common in orbital mechanics
- 3-2-1 (Z-Y-X): Aircraft convention (yaw-pitch-roll)
- Multiple conventions exist; specify clearly in documentation

**Advantages:** Intuitive; relates to physical angles.

**Disadvantages:** 
- Gimbal lock (singularity) when $\cos\theta = 0$ (i.e., $\theta = ±90°$)
- Nonlinear kinematics
- Ambiguous convention usage

### Quaternion (Euler Parameters)

**Four-parameter representation:**
$$
\mathbf{q} = \begin{bmatrix} q_0 \\ \mathbf{q}_v \end{bmatrix} = \begin{bmatrix} q_0 \\ q_1 \\ q_2 \\ q_3 \end{bmatrix}
$$

**Definition (rotation by angle θ about axis $\hat{\mathbf{u}}$):**
$$
q_0 = \cos(\theta/2), \quad \mathbf{q}_v = \hat{\mathbf{u}} \sin(\theta/2)
$$

**Unit constraint:**
$$
q_0^2 + q_1^2 + q_2^2 + q_3^2 = 1
$$

**Rotation matrix from quaternion:**
$$
\mathbf{R} = (q_0^2 - |\mathbf{q}_v|^2)\mathbf{I} + 2\mathbf{q}_v\mathbf{q}_v^T + 2q_0[\mathbf{q}_v]_{\times}
$$

Where $[\mathbf{q}_v]_{\times}$ is skew-symmetric cross-product matrix.

**Advantages:**
- No singularities (smooth over SO(3))
- Efficient computation
- Natural for feedback control
- Interpolation (SLERP) well-defined

**Disadvantages:** 
- Less intuitive physically
- Redundancy ($\mathbf{q}$ and $-\mathbf{q}$ equivalent)
- Constraint enforcement required

**Modern standard:** Quaternions dominate in spacecraft flight software.

### Direction Cosine Matrix (DCM)

**Rotation matrix:**
$$
\mathbf{R} \in SO(3), \quad \mathbf{R}^T\mathbf{R} = \mathbf{I}, \quad \det(\mathbf{R}) = 1
$$

**Each column:** Unit vector in inertial frame (projection of body-fixed axes).

**Properties:**
- 9 components; 3 constraints (orthogonality)
- Effective degrees of freedom: 3 (as expected for SO(3))

**Conversion to body frame:**
$$
\mathbf{v}_{\text{body}} = \mathbf{R} \mathbf{v}_{\text{inertial}}
$$

**Advantages:** Direct vector transformation; no trigonometric evaluation.

**Disadvantages:** Over-parameterized (9 components, 3 constraints); redundancy in storage.

### Modified Rodriguez Parameters

**Three-parameter representation:**
$$
\mathbf{p} = \tan(\theta/2) \hat{\mathbf{u}}
$$

**Minimal representation** (no over-parameterization).

**Singularity:** At $\theta = 180°$ (but rarely reached in typical spacecraft control).

**Use:** Specialized algorithms; less common than quaternions.

## Attitude Kinematics

### Angular Velocity Relationship

**Body-fixed angular velocity $\boldsymbol{\omega}$** relates to attitude rate:

**Euler angles (3-1-3 convention):**
$$
\begin{bmatrix} \dot{\phi} \\ \dot{\theta} \\ \dot{\psi} \end{bmatrix} = \begin{bmatrix}
1 & 0 & \sin\theta\sin\phi/\sin\theta \\
0 & 1 & \sin\phi \\
0 & 0 & \cos\phi
\end{bmatrix}^{-1} \begin{bmatrix} \omega_x \\ \omega_y \\ \omega_z \end{bmatrix}
$$

**Singularity:** $\sin\theta = 0$ (gimbal lock).

**Quaternion kinematics (linear):**
$$
\dot{\mathbf{q}} = \frac{1}{2} \Omega(\boldsymbol{\omega}) \mathbf{q}
$$

Where:
$$
\Omega(\boldsymbol{\omega}) = \begin{bmatrix}
0 & -\omega_x & -\omega_y & -\omega_z \\
\omega_x & 0 & \omega_z & -\omega_y \\
\omega_y & -\omega_z & 0 & \omega_x \\
\omega_z & \omega_y & -\omega_x & 0
\end{bmatrix}
$$

**Advantage:** No singularities; linear in $\boldsymbol{\omega}$.

## Attitude Dynamics

### Rotational Dynamics (Euler Equations)

**Torque balance:**
$$
\mathbf{I} \dot{\boldsymbol{\omega}} + \boldsymbol{\omega} \times (\mathbf{I} \boldsymbol{\omega}) = \boldsymbol{\tau}
$$

Where:
- $\mathbf{I}$: Inertia tensor (3×3 symmetric)
- $\boldsymbol{\omega}$: Angular velocity (body-fixed)
- $\boldsymbol{\tau}$: External torque

**In principal axes** ($\mathbf{I}$ diagonal):
$$
I_1 \dot{\omega}_1 + (I_3 - I_2) \omega_2 \omega_3 = \tau_1
$$
$$
I_2 \dot{\omega}_2 + (I_1 - I_3) \omega_3 \omega_1 = \tau_2
$$
$$
I_3 \dot{\omega}_3 + (I_2 - I_1) \omega_1 \omega_2 = \tau_3
$$

**Coupling:** Nonlinear; rotations about different axes couple through inertia.

### Angular Momentum

**Definition:**
$$
\mathbf{h} = \mathbf{I} \boldsymbol{\omega}
$$

**Conservation** (no external torque):
$$
\mathbf{h} = \text{constant}
$$

**Torque-induced change:**
$$
\dot{\mathbf{h}} = \boldsymbol{\tau}
$$

## Reference Frames

### Inertial Frame

**Fixed relative to distant stars.**

**Notation:** Superscript $I$ or subscript $\text{inertial}$.

**Examples:**
- Earth-Centered Inertial (ECI)
- Sun-Centered Inertial (SCI)

### Body-Fixed Frame

**Fixed relative to spacecraft structure.**

**Notation:** Subscript $B$ or $\text{body}$.

**Axes typically aligned with:**
- +Z: Nadir (pointing toward Earth)
- +X: Along-track (direction of motion)
- +Y: Completes right-hand frame (perpendicular to orbital plane)

**Alternative:** Vehicle axes (forward, starboard, up).

### Orbital Reference Frame (LVLH)

**Local Vertical, Local Horizontal frame:**
- Z: Nadir (toward Earth center)
- X: Along-track (velocity direction)
- Y: Cross-track (completes right-hand)

**Advantage:** Natural for orbital mechanics; [[Orbital Mechanics|gravity gradient]] torque aligned with frame axes.

### Sun-Pointed Frame

**Z-axis:** Toward sun.

**X, Y:** Arbitrary perpendicular (e.g., Z-Y-Z Euler angles with $\psi = $ sun angle).

## Disturbances Affecting Attitude

### Gravity Gradient

**Tidal torque** from Earth's gravity gradient:
$$
\boldsymbol{\tau}_{gg} = 3n^2 \hat{\mathbf{r}} \times (\mathbf{I} \hat{\mathbf{r}})
$$

Where $n$ = [[Mean Motion|mean motion]]; $\hat{\mathbf{r}}$ = local vertical.

**Effect:** Restoring (stabilizing if inertia axes aligned with orbital frame).

**Magnitude:** ~10⁻⁶ N·m for typical small satellite.

### [[Atmospheric Drag]]

**Differential pressure on surfaces creates torque:**
$$
\boldsymbol{\tau}_{\text{drag}} = \mathbf{r}_{cp} \times \mathbf{F}_D
$$

**Effect:** Can destabilize; causes tumbling.

**Magnitude:** ~10⁻⁷ to 10⁻⁵ N·m (depends on altitude, configuration).

### Solar Radiation Pressure

**Photon momentum transfer:**
$$
\boldsymbol{\tau}_{srp} = \mathbf{r}_{crp} \times \mathbf{F}_{\text{rad}}
$$

**Magnitude:** ~10⁻⁸ N·m (persistent but small).

### Magnetic Interactions

**Residual spacecraft dipole in Earth field:**
$$
\boldsymbol{\tau}_{\text{mag}} = \mathbf{m} \times \mathbf{B}
$$

**Effect:** Slow drift; can induce oscillations.

### Internal Momentum Transfer

**Reaction wheels, rotating equipment:** Create coupled dynamics.

**[[Momentum Management]]:** Desaturation required when wheels approach limits.

## Attitude Control Applications

### Earth Observation

**Nadir pointing:** Look downward for imaging.

**Slew maneuvers:** Rotate between targets (~1–10°/s typical rate).

**Constraint:** Power (solar panel must track sun); thermal (radiators face space).

### Communications

**Geostationary:** Fixed attitude (nadir-pointing).

**Inclined/LEO:** Periodic sun-pointing for power + periodic Earth-pointing for comm.

### Scientific Instruments

**Hubble Space Telescope:** Pointing ±0.01 arcsecond (3σ).

**Solar panels:** Track sun; simple rotating joint (one DOF).

### Gravity Gradient Stabilization

**Passive:** Long boom; gravity gradient torque stabilizes nadir-pointing.

**Advantage:** Minimal actuators; very low power.

**Example:** Early weather satellites, gravity gradient stabilized.

## Attitude Specification and Documentation

### Attitude Error Tolerance

**Specification example:**
- "Maintain nadir pointing ±10°; solar panel on Earth-pointing side ±5°"

**Implementation:** ADCS [[Attitude Control|control law]] commands to within tolerance.

### Attitude Maneuver Planning

**Input:** Current attitude, target attitude, slew rate limit.

**Output:** Maneuver sequence (thruster firings or reaction wheel commands).

**Time calculation:** For small angle maneuver (Δθ radians) at constant rate $\omega_r$:
$$
t_{\text{maneuver}} \approx \frac{\Delta\theta}{\omega_r}
$$

## Connection to Other Concepts

1. **Connection to [[Orbital Mechanics]]:**
   - Independent of orbital state
   - Gravity gradient torque couples them

2. **Connection to [[Attitude Determination and Control System (ADCS)]]:**
   - Fundamental parameter controlled by ADCS

3. **Connection to [[Attitude Determination]]:**
   - Estimation target

4. **Connection to [[Attitude Control]]:**
   - Closed-loop control objective

5. **Connection to [[Angular Momentum]]:**
   - Rate of momentum change drives attitude dynamics

## See Also

- [[Attitude Control]]
- [[Attitude Determination]]
- [[Attitude Determination and Control System (ADCS)]]
- [[Angular Velocity]]
- [[Moment of Inertia]]
- [[Quaternions]]
- [[Euler Angles]]
- [[Gravity Gradient]]
- [[Orbital Mechanics]]
- [[Spacecraft Dynamics]]

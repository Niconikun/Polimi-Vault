#SAD #TBD 
## Formal Definition

**Euler Angles** are a set of three angles ($\phi, \theta, \psi$) used to describe the orientation (attitude) of a [[Rigid Body]] relative to a fixed coordinate system. This is achieved by performing three successive rotations around specific axes in a predefined sequence. In spacecraft dynamics, these angles are typically referred to as **Roll, Pitch, and Yaw**. While intuitive for human visualization, Euler angles are mathematically complex because the result of the rotation depends entirely on the order in which the angles are applied.



## Historical Development

### Key Milestones
- **1770s:** Leonhard Euler introduces the "Euler Rotation Theorem," proving that any displacement of a [[Rigid Body]] with one fixed point is equivalent to a single rotation about some axis.
- **19th Century:** Euler angles become the standard for describing the "wobble" (nutation) of planets and the motion of gyroscopes.
- **1950s–Present:** Aerospace engineers adopt the "Tait-Bryan" variant of Euler angles (1-2-3 or 1-3-2 sequences) for aircraft and spacecraft navigation.

### Foundational Contributors
1. **Leonhard Euler (1707–1783):** Developed the mathematical proof that three parameters are sufficient to define 3D orientation.
2. **Peter Guthrie Tait & George H. Bryan:** Refined the notation for aeronautical engineering, moving away from the "proper" Euler angles (e.g., z-x-z) to the more practical roll-pitch-yaw sequences.

## Mathematical Formulation

### The Rotation Sequence
Orientation is achieved through three elemental rotation matrices ($\mathbf{R}_x, \mathbf{R}_y, \mathbf{R}_z$). For a common **Yaw-Pitch-Roll (3-2-1)** sequence, the total rotation matrix $\mathbf{C}$ is:

$$
\mathbf{C} = \mathbf{R}_x(\phi) \mathbf{R}_y(\theta) \mathbf{R}_z(\psi)
$$

### Kinematic Differential Equations
To link Euler angles to the angular velocities ($\omega_1, \omega_2, \omega_3$) found in **Euler's Equations of Motion**, we use:

$$
\begin{bmatrix} \dot{\phi} \\ \dot{\theta} \\ \dot{\psi} \end{bmatrix} = \frac{1}{\cos\theta} \begin{bmatrix} \cos\theta & \sin\phi\sin\theta & \cos\phi\sin\theta \\ 0 & \cos\phi\cos\theta & -\sin\phi\cos\theta \\ 0 & \sin\phi & \cos\phi \end{bmatrix} \begin{bmatrix} \omega_1 \\ \omega_2 \\ \omega_3 \end{bmatrix}
$$

*(Note the $1/\cos\theta$ term, which leads to the singularity known as [[Gimbal Lock]].)*

## Fundamental Principles

### Core Assumptions
1. **Order Matters:** Rotations in 3D are non-commutative. A $90^\circ$ Roll followed by a $90^\circ$ Pitch does not result in the same orientation as a $90^\circ$ Pitch followed by a $90^\circ$ Roll.
2. **Body-Fixed vs. Space-Fixed:** In spacecraft, we usually use **Intrinsic Rotations**, where each subsequent rotation is around the "new" axis of the moved body.

### Governing Laws
- **Euler's Rotation Theorem:** The underlying geometric principle that justifies using three angles.
- **[[Direction Cosine Matrix]] (DCM):** The $3 \times 3$ matrix formed by the product of the three Euler rotations.

## Theoretical Framework

### Proper Euler Angles vs. Tait-Bryan Angles
- **Proper Euler Angles:** The first and third axes are the same (e.g., $z-x-z$ or $y-z-y$). Commonly used in physics and molecular dynamics.
- **Tait-Bryan Angles:** All three axes are different (e.g., $x-y-z$ or $z-y-x$). These are the Roll, Pitch, and Yaw used in aerospace.



## Physical Interpretation

### [[Gimbal Lock]]
The "Achilles' heel" of Euler angles is **[[Gimbal Lock]]**. When the middle angle ($\theta$ in a 3-2-1 sequence) reaches $\pm 90^\circ$, the first and third axes align. Mathematically, the system loses a degree of freedom, and the differential equations "blow up" (divide by zero). Physically, the spacecraft's computer loses the ability to distinguish between a roll and a yaw.

## Advantages and Limitations

### Strengths
1. **Intuitive:** It is easy for a pilot or engineer to visualize a "$10^\circ$ Pitch up" maneuver.
2. **Minimalist:** Uses only three parameters to describe orientation.

### Limitations
1. **Singularities:** The [[Gimbal Lock]] issue makes them dangerous for high-maneuverability craft or all-attitude pointing.
2. **Computational Cost:** Calculating trig functions (sin/cos) is slower for onboard flight computers than the simple arithmetic used in **Quaternions**.

## Applications

### Aerospace Engineering
1. **Cockpit Displays:** Displaying attitude information to astronauts or pilots.
2. **Control Laws:** Used in "Small-Angle" approximations for stable satellites where $\theta$ never approaches $90^\circ$.
3. **Mission Planning:** Defining the "Target Attitude" for a science instrument relative to the Earth.

## See Also

- [[Quaternion]] (The singularity-free alternative)
- [[Euler's Law]]
- [[Direction Cosine Matrix]]
- [[Principal Axes of Inertia]]

## Recommended Tags:
#attitude-dynamics #aerospace-engineering #euler-angles #rotation-matrix #gimbal-lock #kinematics #navigation
## Formal Definition

**Modified Rodrigues Parameters** (MRPs) are a three-parameter attitude representation defined by scaling the unit rotation axis ($\mathbf{e}$) by the tangent of **one-fourth** of the rotation angle ($\theta/4$). MRPs were developed to overcome the $180^\circ$ singularity of the [[Gibbs Vector]] (Classical Rodrigues Parameters) while maintaining a minimal three-parameter set. By shifting the singularity point to $360^\circ$ (a full revolution), MRPs allow for all-attitude maneuvers without the redundant fourth parameter required by Quaternions. They are widely considered the most efficient parameters for modern non-linear attitude estimation and control.



## Historical Development

### Key Milestones
- **19th Century:** The mathematical concept of stereographic projection is established, providing the geometric basis for MRPs.
- **1991:** **Wiener and Marandi** formally introduce MRPs to the aerospace community as a way to avoid the $180^\circ$ singularity of Gibbs vectors.
- **1990s:** **Hanspeter Schaub** and **John Junkins** popularize MRPs in the field of spacecraft dynamics, proving their utility in Lyapunov-based control and Kalman filtering.
- **Present:** MRPs are the standard representation for "Error Attitude" in high-performance satellite control systems.

### Foundational Contributors
1. **Hanspeter Schaub:** A leading figure in modern astrodynamics who formalized the use of MRPs for complex spacecraft maneuvers.
2. **John Junkins:** Contributed extensively to the analytical mechanics and stability proofs involving MRPs.

## Mathematical Formulation

### Definition
The MRP vector $\boldsymbol{\sigma}$ is defined using the Euler axis $\mathbf{e}$ and rotation angle $\theta$:
$$\boldsymbol{\sigma} = \mathbf{e} \tan\left(\frac{\theta}{4}\right)$$

### Relation to Quaternions
MRPs can be derived directly from unit quaternions ($\mathbf{q}$):
$$\boldsymbol{\sigma} = \frac{\boldsymbol{\rho}}{1 + q_4} = \begin{bmatrix} q_1/(1+q_4) \\ q_2/(1+q_4) \\ q_3/(1+q_4) \end{bmatrix}$$

### Kinematic Differential Equation
The rate of change of $\boldsymbol{\sigma}$ is governed by a quadratic expression in $\boldsymbol{\sigma}$:
$$\dot{\boldsymbol{\sigma}} = \frac{1}{4} \left[ (1 - \sigma^2) \mathbf{I} + 2 [\boldsymbol{\sigma}\times] + 2 \boldsymbol{\sigma}\boldsymbol{\sigma}^T \right] \boldsymbol{\omega}$$
*Where $\sigma^2 = \boldsymbol{\sigma}^T \boldsymbol{\sigma}$ is the squared magnitude of the vector.*

## Fundamental Principles

### Core Assumptions
1. **Singularity at $360^\circ$:** The representation fails only at a full revolution ($\theta = 2\pi$), where the tangent goes to infinity.
2. **Shadow Point Logic:** To handle rotations approaching $360^\circ$, MRPs utilize a "Shadow Set" to flip the representation back to a smaller magnitude.

### Governing Laws
- **The Shadow Point Transformation:** Any rotation $\boldsymbol{\sigma}$ has a shadow counterpart $\boldsymbol{\sigma}^S$ that represents the same orientation:
  $$\boldsymbol{\sigma}^S = -\frac{\boldsymbol{\sigma}}{\sigma^2}$$
  By switching to the shadow set when $\sigma^2 > 1$ (i.e., $\theta > 180^\circ$), the singularity is avoided entirely.



## Theoretical Framework

### Stereographic Projection
MRPs are mathematically equivalent to a stereographic projection of the 4D unit [[Quaternion]] sphere onto a 3D plane, with the projection point located at the "South Pole" of the sphere ($q_4 = -1$). This geometric mapping explains why they are so effective at linearizing the rotation space for small-to-medium angles.

## Physical Interpretation

### The "Stretched" Axis
If a spacecraft rotates, the MRP vector grows along the axis of rotation. Because it uses $\theta/4$, it grows much more slowly than the [[Gibbs Vector]]. Even a massive $180^\circ$ flip results in a vector magnitude of only $1.0$ ($\tan(45^\circ) = 1$). This "slow growth" provides excellent numerical stability for almost all maneuvers a satellite will ever perform.

## Advantages and Limitations

### Strengths
1.  **Minimalism:** Only 3 parameters; no need to maintain a "unit norm" constraint like quaternions.
2.  **Wide Range:** Can represent any rotation up to (but not including) $360^\circ$ without a singularity.
3.  **Efficiency:** Quadratic kinematics are faster to integrate than trigonometric [[Euler angles]].

### Limitations
1.  **The $360^\circ$ Wall:** While rare in pointing, a full tumble still requires a "shadow set" switch to avoid numerical overflow.
2.  **Complexity:** The math for successive rotations (composition) is more complex than [[Quaternion]] multiplication.

## Applications

### Spacecraft Guidance & Control
1.  **Non-linear Control:** Used to design "Global" control laws where a satellite must slew from any orientation to any other.
2.  **Kalman Filtering:** The preferred state representation for attitude error in Extended Kalman Filters (EKF) due to its minimal nature.
3.  **Optimization:** Used in trajectory optimization where the redundant 4th parameter of a [[Quaternion]] would complicate the solver.

## See Also

- [[Gibbs Vector]]
- [[Quaternion]]
- [[Euler Axis and Angle]]
- [[Lyapunov Stability Theorems]]

## Recommended Tags:
#attitude-dynamics #MRP #rodrigues-parameters #kinematics #spacecraft-control #mathematics #nonlinear-control
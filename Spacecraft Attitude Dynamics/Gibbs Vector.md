#SAD #TBD 
## Formal Definition

The **Gibbs Vector** ($\mathbf{g}$) is a three-parameter representation of a 3D rotation, defined by scaling the unit rotation axis ($\mathbf{e}$) by the tangent of half the rotation angle ($\theta/2$). Unlike Quaternions, which use a four-element vector to avoid singularities, the Gibbs Vector uses only three elements, making it a "minimal" representation. However, this comes at the cost of a mathematical singularity at $\theta = 180^\circ$ (where the tangent function goes to infinity). It is widely used in attitude estimation and control because its kinematic equations are quadratic rather than trigonometric.



## Historical Development

### Key Milestones
- **1840:** Olinde Rodrigues derives the parameters as part of his study on rotation groups, though they initially lack a specific name.
- **1884:** **Josiah Willard Gibbs** popularizes the vector form in his lectures on vector analysis, leading to the name "Gibbs Vector."
- **1960s:** Aerospace engineers adopt the parameters as "Classical Rodrigues Parameters" (CRP) to simplify the non-linear filtering of satellite attitude.
- **1990s:** The development of **[[Modified Rodrigues Parameters (MRP)]]** solves the $180^\circ$ singularity problem while keeping the benefits of the Gibbs Vector.

### Foundational Contributors
1. **Josiah Willard Gibbs (1839–1903):** An American scientist who pioneered vector calculus and applied these parameters to rigid-body kinematics.
2. **Olinde Rodrigues (1795–1851):** The French mathematician who first discovered the underlying group properties of these parameters.

## Mathematical Formulation

### Definition
The Gibbs vector $\mathbf{g}$ is defined using the Euler axis $\mathbf{e}$ and rotation angle $\theta$:
$$\mathbf{g} = \mathbf{e} \tan\left(\frac{\theta}{2}\right)$$

### Relation to Quaternions
The Gibbs vector is essentially the ratio of the [[Quaternion]]'s vector part ($\boldsymbol{\rho}$) to its scalar part ($q_4$):
$$\mathbf{g} = \frac{\boldsymbol{\rho}}{q_4} = \begin{bmatrix} q_1/q_4 \\ q_2/q_4 \\ q_3/q_4 \end{bmatrix}$$

### Kinematic Differential Equation
The primary advantage of the Gibbs vector is that its rate of change is algebraic and lacks trigonometric functions:
$$\dot{\mathbf{g}} = \frac{1}{2} [\mathbf{I} + [\mathbf{g}\times] + \mathbf{g}\mathbf{g}^T] \boldsymbol{\omega}$$
*Where $[\mathbf{g}\times]$ is the skew-symmetric matrix of the Gibbs vector.*

## Fundamental Principles

### Core Assumptions
1. **Rotation Limit:** The rotation angle must be strictly less than $180^\circ$ ($-\pi < \theta < \pi$).
2. **[[Rigid Body]]:** The vector describes the orientation of a rigid frame relative to a reference frame.

### Governing Laws
- **Successive Rotations:** Two rotations $\mathbf{g}_1$ and $\mathbf{g}_2$ can be combined using the **Rodrigues Composition Formula**:
  $$\mathbf{g}_{total} = \frac{\mathbf{g}_1 + \mathbf{g}_2 - \mathbf{g}_2 \times \mathbf{g}_1}{1 - \mathbf{g}_1 \cdot \mathbf{g}_2}$$

## Theoretical Framework

### The Singularity at $180^\circ$
As the rotation angle $\theta$ approaches $180^\circ$, $\tan(\theta/2)$ approaches infinity. This means the Gibbs vector cannot represent a "half-turn" (a complete flip). In spacecraft dynamics, if a satellite is expected to perform all-attitude maneuvers, the Gibbs vector is often replaced by **[[Modified Rodrigues Parameters (MRP)]]**, which push the singularity to $360^\circ$ by using $\tan(\theta/4)$ instead.

[Image showing the tangent function singularity at 180 degrees for Gibbs vectors]

## Physical Interpretation

### Projection onto a Plane
You can visualize the Gibbs vector as a **stereographic projection** of a rotation from a 4D hypersphere onto a 3D hyperplane. The "stretching" of the vector as it approaches $180^\circ$ is the result of the projection point reaching the "equator" of the rotation space.

## Advantages and Limitations

### Strengths
1. **Minimalism:** Uses only 3 parameters (no redundant constraint like the [[Quaternion]] unit norm).
2. **Computation:** Extremely efficient for integration and "Cayley transforms" in flight software.
3. **Linearity:** For small angles, the Gibbs vector is nearly linear ($\mathbf{g} \approx \mathbf{e}\theta/2$).

### Limitations
1. **Singularity:** Completely fails at $180^\circ$, making it unsuitable for tumbling spacecraft or complex flip maneuvers.
2. **Numerical Sensitivity:** Becomes very large and unstable as the rotation approaches the $180^\circ$ limit.

## Applications

### Spacecraft [[Attitude Control]]
1. **Attitude Estimation:** Used in Kalman Filters where a 3-component state vector is easier to manage than a 4-component [[Quaternion]].
2. **Small-Angle Pointing:** Ideal for satellites that stay "near" an equilibrium (like [[Nadir]]-pointing) where the $180^\circ$ singularity is never reached.
3. **Computer Vision:** Often used in robotics to describe the orientation of a camera relative to a target.

## See Also

- [[Quaternion]]
- [[Euler Axis and Angle]]
- [[Modified Rodrigues Parameters (MRP)]]
- [[Direction Cosine Matrix]]

## Recommended Tags:
#attitude-dynamics #gibbs-vector #rodrigues-parameters #kinematics #mathematics #spacecraft-control #navigation
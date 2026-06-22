#SAD #TBD 
## Formal Definition

The **Euler Axis and Angle** representation (also known as the **Rotation Vector** or **Axis-Angle** representation) states that any displacement of a [[Rigid Body]] such that one point remains fixed is equivalent to a single rotation by a specific angle ($\theta$) about a fixed axis ($\mathbf{e}$). While [[Euler Angles]] use three successive rotations around varying axes, this method defines the orientation using a single geometric operation. The "Euler Axis" is the eigenvector of the rotation matrix corresponding to the eigenvalue of 1, representing the line in space that remains unchanged by the rotation.



## Historical Development

### Key Milestones
- **1775:** Leonhard Euler presents his **Rotation Theorem** to the Saint Petersburg Academy, proving that the combination of any number of rotations is itself a single rotation.
- **1840s:** Rodrigues develops the rotation formula (Rodrigues' Rotation Formula) that allows for the easy calculation of vectors rotated about an arbitrary axis.
- **1960s:** Aerospace engineers begin utilizing Axis-Angle parameters as an intermediate step to convert human-readable [[Euler Angles]] into computer-efficient Quaternions.

### Foundational Contributors
1. **Leonhard Euler (1707–1783):** Proved the geometric existence of a single axis for any 3D rotation.
2. **Olinde Rodrigues (1795–1851):** Provided the trigonometric vector formula that operationalized Euler’s theorem.

## Mathematical Formulation

### The Rotation Vector ($\boldsymbol{\theta}$)
The orientation is often represented by a single vector whose direction is the axis and whose magnitude is the angle:
$$\boldsymbol{\theta} = \theta \mathbf{e}$$
Where $\mathbf{e} = [e_x, e_y, e_z]^T$ is a unit vector ($|\mathbf{e}| = 1$).

### Relation to the [[Direction Cosine Matrix]] (DCM)
Using **Rodrigues' Rotation Formula**, a rotation matrix $\mathbf{R}$ can be constructed from an axis $\mathbf{e}$ and angle $\theta$:
$$\mathbf{R} = \mathbf{I} + (\sin\theta)[\mathbf{e}\times] + (1 - \cos\theta)[\mathbf{e}\times]^2$$
Where $[\mathbf{e}\times]$ is the skew-symmetric cross-product matrix of the axis.

### Extraction from a Matrix
If given a rotation matrix $\mathbf{R}$, the angle $\theta$ is found via the trace:
$$\theta = \arccos\left(\frac{\text{Tr}(\mathbf{R}) - 1}{2}\right)$$

## Fundamental Principles

### Core Assumptions
1. **Fixed Point:** The rotation must occur around a fixed origin (usually the spacecraft's Center of Mass).
2. **Rigidity:** The body does not deform during the rotation.

### Governing Laws
- **Euler’s Rotation Theorem:** The fundamental "Law" that guarantees an axis exists for every possible orientation change.
- **Eigenvalue Property:** The axis $\mathbf{e}$ is the only vector that satisfies $\mathbf{R}\mathbf{e} = \mathbf{e}$.

## Theoretical Framework

### The Link to Quaternions
The Axis-Angle representation is the "DNA" of a [[Quaternion]][[Quaternion|. A quater]]nion $\mathbf{q}$ is built directly from these parameters:
- **Vector part:** $\mathbf{q}_{1,2,3} = \mathbf{e} \sin(\theta/2)$
- **Scalar part:** $q_4 = \cos(\theta/2)$

This relationship makes it easy to move from a geometric visual (the Axis and Angle) to a singularity-free computation (the [[Quaternion]]).

[Image showing the relationship between rotation axis, angle, and [[Quaternion]] components]

## Physical Interpretation

### The "Screwdriver" Analogy
Think of the Euler Axis as the shaft of a screwdriver. No matter how complex the final orientation of the spacecraft is, there is a specific direction you can point that screwdriver (the axis) and a specific amount you can turn the handle (the angle) to reach that orientation in one single, clean motion.

## Advantages and Limitations

### Strengths
1. **Geometric Clarity:** Much easier to visualize than a $3 \times 3$ matrix or a 4D [[Quaternion]].
2. **Compactness:** Uses only three independent parameters (direction of $\mathbf{e}$ and magnitude of $\theta$).
3. **Shortest Path:** Represents the "Great Circle" path (geodesic) between two orientations.

### Limitations
1. **Ambiguity at Zero:** If $\theta = 0$, the axis $\mathbf{e}$ is undefined (it could be anything).
2. **Numerical Sensitivity:** Extracting the axis from a matrix becomes numerically unstable as $\theta$ approaches $0$ or $180^\circ$.

## Applications

### Spacecraft Control
1. **Slew Manoeuvers:** When a satellite needs to turn from Star A to Star B, the flight computer calculates the Euler Axis between the two and commands the reaction wheels to spin around that specific axis.
2. **Robotic Path Planning:** Ensuring a robotic arm moves in a smooth arc rather than jerky sequential movements.
3. **Animation and VR:** Used in "Interpolation" to make rotations look natural and smooth.

## See Also

- [[Euler Angles]]
- [[Quaternion]]
- [[Direction Cosine Matrix]]
- [[Euler's Law]]

## Recommended Tags:
#attitude-dynamics #axis-angle #euler-rotation-theorem #kinematics #mathematics #rotation-vector #spacecraft-control
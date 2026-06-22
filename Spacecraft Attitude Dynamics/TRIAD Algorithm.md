## Formal Definition

The **TRIAD Algorithm** is a deterministic method used to estimate the 3D attitude (the [[Direction Cosine Matrix]], $\mathbf{A}$) of a spacecraft by processing two non-parallel vector measurements. By comparing two unit vectors measured in the spacecraft body frame (e.g., from a Sun sensor and a [[Magnetometer]]) to their known directions in a reference frame (e.g., from a solar/magnetic model), TRIAD constructs two orthogonal coordinate systems. The unique rotation matrix that transforms the reference frame into the body frame is then calculated algebraically.



## Historical Development

### Key Milestones
- **1964:** **Harold Black** publishes the algorithm in the *AIAA Journal*, providing the first practical solution for 3D attitude determination for the Transit satellite program.
- **1965:** Grace Wahba formalizes "[[Wahba's Problem]]," recognizing that TRIAD is a specific, non-optimal solution to a broader optimization problem.
- **1980s–Present:** While more "optimal" algorithms like **QUEST** or **Filter QUEST** are used for high-precision missions, TRIAD remains the industry-standard "Sanity Check" and initialization tool because of its speed and simplicity.

### Foundational Contributors
1. **Harold Black:** The primary inventor of the algorithm at the Johns Hopkins Applied Physics Laboratory.
2. **Grace Wahba:** Provided the mathematical context that allowed TRIAD to be compared against other estimation methods.

## Mathematical Formulation

TRIAD requires two vectors: a "Primary" vector ($\mathbf{V}_1$) which is considered more accurate, and a "Secondary" vector ($\mathbf{V}_2$).

### 1. Construct the Body Frame Triad ($\mathbf{b}_1, \mathbf{b}_2, \mathbf{b}_3$)
Using the measured vectors $\mathbf{s}_1, \mathbf{s}_2$ in the body frame:
- $\hat{\mathbf{b}}_1 = \mathbf{s}_1$
- $\hat{\mathbf{b}}_2 = \frac{\mathbf{s}_1 \times \mathbf{s}_2}{|\mathbf{s}_1 \times \mathbf{s}_2|}$
- $\hat{\mathbf{b}}_3 = \hat{\mathbf{b}}_1 \times \hat{\mathbf{b}}_2$

### 2. Construct the Reference Frame Triad ($\mathbf{r}_1, \mathbf{r}_2, \mathbf{r}_3$)
Using the known reference vectors $\mathbf{v}_1, \mathbf{v}_2$ (e.g., from a star catalog or IGRF):
- $\hat{\mathbf{r}}_1 = \mathbf{v}_1$
- $\hat{\mathbf{r}}_2 = \frac{\mathbf{v}_1 \times \mathbf{v}_2}{|\mathbf{v}_1 \times \mathbf{v}_2|}$
- $\hat{\mathbf{r}}_3 = \hat{\mathbf{r}}_1 \times \hat{\mathbf{r}}_2$

### 3. Calculate the Attitude Matrix ($\mathbf{A}$)
The [[Direction Cosine Matrix]] is found by:
$$\mathbf{A} = \begin{bmatrix} \hat{\mathbf{b}}_1 & \hat{\mathbf{b}}_2 & \hat{\mathbf{b}}_3 \end{bmatrix} \begin{bmatrix} \hat{\mathbf{r}}_1 & \hat{\mathbf{r}}_2 & \hat{\mathbf{r}}_3 \end{bmatrix}^T$$

## Fundamental Principles

### Core Assumptions
1. **Non-Parallel Vectors:** The two vectors must not be parallel (collinear); the algorithm fails if $\mathbf{s}_1 \times \mathbf{s}_2 = 0$.
2. **Primary Weighting:** TRIAD assumes the first vector ($\mathbf{V}_1$) is "truth" and essentially discards any information in the second vector that contradicts the direction of the first.

### Governing Laws
- **Orthogonality:** The resulting matrix $\mathbf{A}$ is a member of the Special Orthogonal group $SO(3)$.
- **Cross-Product Property:** The algorithm relies on the fact that the cross product of two vectors is invariant under rotation.

## Theoretical Framework

### The "Sub-Optimal" Nature
TRIAD is a **deterministic** algorithm, not a statistical one. It uses the minimum amount of information possible. If you have three or more sensors, TRIAD cannot use the extra data. More advanced algorithms (like QUEST) are "Optimal" because they use a weighted average of all available sensors to minimize noise.

[Image comparing TRIAD deterministic frames vs QUEST weighted optimization]

## Physical Interpretation

### The "Anchor and Swing"
Imagine you are lost at sea. You see a lighthouse (Vector 1) and a mountain (Vector 2). 
1. You point your ship directly at the lighthouse (this defines your first axis).
2. You then figure out which "side" the mountain is on relative to the lighthouse (this defines your second axis).
3. The third axis is just the "up" direction perpendicular to the other two.
By "anchoring" to the most reliable landmark first, you build a coordinate system on your ship that you can compare to a map.

## Advantages and Limitations

### Strengths
1. **Speed:** Extremely fast; involves simple vector cross products and one matrix multiplication.
2. **No Initial Guess:** Unlike a Kalman Filter, TRIAD works instantly with no prior knowledge of the attitude (Lost-In-Space).
3. **Simplicity:** Very easy to code and debug in flight software.

### Limitations
1. **Non-Optimal:** It throws away information from the second vector to satisfy the first.
2. **Two Vectors Only:** Cannot handle more than two sensors simultaneously.
3. **Sensitivity:** If the two sensors are nearly parallel, the "Normal" vector ($\mathbf{b}_2$) becomes extremely noisy.

## Applications

### Spacecraft Processing
1.  **Initial Acquisition:** Finding the attitude immediately after the satellite is released from the rocket.
2.  **Kalman Filter Initialization:** Providing the first "Guess" to start the recursive estimation process.
3.  **Coarse Control:** Used in CubeSats where a [[Magnetometer]] and Sun Sensor are the only sensors available.

## See Also

- [[Wahba's Problem]]
- [[QUEST Algorithm]]
- [[Direction Cosine Matrix]]
- [[Sun Sensor]]
- [[Magnetometer]]

## Recommended Tags:
#attitude-determination #TRIAD #Wahbas-problem #vector-math #navigation #spacecraft-sensors #DCM
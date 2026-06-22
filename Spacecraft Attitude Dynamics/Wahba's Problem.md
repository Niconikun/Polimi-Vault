## Formal Definition

**Wahba’s Problem** is a mathematical optimization problem that seeks to find the best-fit rotation matrix (Attitude) between two sets of vector observations. Specifically, given a set of unit vectors measured in a body frame (e.g., from onboard sensors) and their corresponding known unit vectors in a reference frame (e.g., from a star catalog), Wahba’s Problem aims to find the orthogonal matrix $\mathbf{A}$ that minimizes the weighted sum of the squared distances between them. It is the core "cost function" for almost all spacecraft attitude determination software.



## Historical Development

### Key Milestones
- **1965:** **Grace Wahba** poses the problem as a "Problem 65-1" in the *SIAM Review*, asking for a solution to find the least-squares estimate of spacecraft attitude.
- **1966–1968:** Several closed-form solutions are proposed, most notably by Davenport, using the "q-method" which converts the problem into an eigenvalue problem.
- **1981:** **Malcolm Shuster** develops the **QUEST** ([[Quaternion]] Estimator) algorithm, providing a faster, more computationally efficient way to solve Wahba's problem in real-time.
- **Present:** Modern variations of the problem account for "time-varying" vectors and are integrated into Extended Kalman Filters (EKF).

### Foundational Contributors
1. **Grace Wahba:** An American statistician who generalized the problem for the aerospace community.
2. **Paul Davenport:** Developed the transformation that allowed the problem to be solved using quaternions.

## Mathematical Formulation

### The Cost Function ($J$)
The goal is to find the [[Direction Cosine Matrix]] $\mathbf{A}$ that minimizes:

$$J(\mathbf{A}) = \frac{1}{2} \sum_{i=1}^{n} w_i \| \mathbf{b}_i - \mathbf{A} \mathbf{r}_i \|^2$$

### Component Breakdown
- **$w_i$**: The **weighting factor** for the $i$-th sensor. If a Star Tracker is $100\times$ more accurate than a [[Magnetometer]], its $w_i$ will be significantly higher.
- **$\mathbf{b}_i$**: The unit [[Vector]] measured in the **Body frame**.
- **$\mathbf{r}_i$**: The known unit vector in the **Reference frame**.
- **$\mathbf{A}$**: The $3 \times 3$ orthogonal rotation matrix (the unknown).

### The Solution via QUEST
By expanding the cost function, the problem can be rewritten as maximizing a "gain" function $g(\mathbf{q})$ using quaternions:
$$g(\mathbf{q}) = \mathbf{q}^T \mathbf{K} \mathbf{q}$$
Where $\mathbf{K}$ is a $4 \times 4$ matrix built from the sensor data. The optimal attitude is the **eigenvector** corresponding to the largest eigenvalue of $\mathbf{K}$.

## Fundamental Principles

### Core Assumptions
1. **Unit Vectors:** All observations must be normalized to unit length.
2. **Zero-Mean Noise:** Assumes that sensor errors are Gaussian and random.
3. **[[Rigid Body]]:** Assumes all sensors are rigidly mounted and their relative alignments are known.

### Governing Laws
- **Least-Squares Estimation:** The statistical principle that the most likely "truth" is the one that minimizes the sum of the squares of the errors.

## Theoretical Framework

### Deterministic vs. Optimal
- **Deterministic (TRIAD):** Uses exactly two vectors. It "cheats" by assuming one vector is perfect, making it sub-optimal.
- **Optimal (Wahba Solutions):** Uses $n$ vectors ($n \geq 2$). It "balances" the errors across all sensors based on their weights. Even if you have 50 stars in view, Wahba's problem allows you to use all of them to find one single, highly accurate attitude.

[Image comparing deterministic TRIAD vs Wahba's optimal least-squares fit]

## Physical Interpretation

### The "Rubber Band" Analogy
Imagine you have several points on a globe (Reference frame) and several corresponding points on a ball in your hand (Body frame). You connect each pair with a rubber band. The "strength" of each rubber band is the weight ($w_i$). When you let go, the ball in your hand will rotate until the tension in all the rubber bands is minimized. The final orientation of the ball is the solution to Wahba's Problem.

## Advantages and Limitations

### Strengths
1.  **Sensor Fusion:** Allows a spacecraft to combine data from wildly different sensors (Star Tracker, Sun Sensor, [[Magnetometer]]) into one result.
2.  **Noise Rejection:** By using many vectors, the "random" errors in individual sensors tend to cancel each other out.
3.  **Versatility:** The math is the same regardless of whether you are using two sensors or two thousand.

### Limitations
1.  **Ambiguity:** If all the vectors are parallel, the problem has no unique solution.
2.  **Computational Cost:** Solving for eigenvalues (like in [[Davenport's q-method]]) can be intensive for very old or tiny flight computers.

## Applications

### Attitude Determination
1.  **[[QUEST Algorithm]]:** The most common real-time solver used in satellites today.
2.  **Star Pattern Recognition:** Determining which stars are which by finding the rotation that matches the image to the map.
3.  **Sensor Calibration:** Determining if a sensor has "tilted" out of alignment over time by analyzing the residual errors in the Wahba solution.

## See Also

- [[TRIAD Algorithm]]
- [[QUEST Algorithm]]
- [[Quaternion]]
- [[Direction Cosine Matrix]]

## Recommended Tags:
#attitude-determination #Wahbas-problem #least-squares #optimization #sensor-fusion #astrodynamics #mathematics
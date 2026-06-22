#attitude-determination #wahbas-problem #optimal-estimation #spacecraft-dynamics #ADCS #SAD 

**Definition:**
Wahba's Problem is a classic optimization problem in the field of [[Attitude Determination]] that seeks to find the optimal rotation matrix (i.e., the attitude) that minimizes a weighted least-squares cost function between two sets of [[Vector]] observations. Formally, it is the problem of finding the proper orthogonal matrix **A** that minimizes the loss function:

$$
L(\mathbf{A}) = \frac{1}{2} \sum_{i=1}^{n} w_i \lVert \mathbf{b}_i - \mathbf{A} \mathbf{r}_i \rVert^2
$$

Where:
*   **A** is the $3 \times 3$ **[[Direction Cosine Matrix]] (DCM)** representing the unknown attitude we wish to find. It is a proper orthogonal matrix, meaning $\mathbf{A}^T\mathbf{A} = \mathbf{I}$ and $\det(\mathbf{A}) = +1$.
*   $\mathbf{b}_i$ is a set of $n \geq 2$ unit vectors measured in the **body frame** of the vehicle (e.g., from star trackers, sun sensors, magnetometers).
*   $\mathbf{r}_i$ is the corresponding set of $n \geq 2$ unit vectors known in the **reference frame** (e.g., an inertial frame like ECI or an orbital frame).
*   $w_i$ are non-negative weights assigned to each [[vector]] pair, typically based on the accuracy or noise characteristics of the respective sensors.
*   $L(\mathbf{A})$ is the loss function to be minimized.

---

#### **Detailed Interpretation**

The core idea is to find the single best "rotation" that aligns the known reference vectors $\mathbf{r}_i$ with their measured counterparts $\mathbf{b}_i$ as closely as possible. The weights $w_i$ allow more accurate measurements (e.g., from a star tracker) to have a greater influence on the solution than less accurate ones (e.g., from a coarse sun sensor).

The problem is "loss of information" because [[vector]] measurements alone do not give a unique attitude; multiple rotations can partially align the sets. Wahba's problem provides the mathematically optimal single-frame solution.

---

#### **Mathematical Reformulation**

The original cost function can be rewritten into a more convenient form:

$$
L(\mathbf{A}) = \sum w_i - \text{tr}(\mathbf{A} \mathbf{B}^T)
$$

Where $\mathbf{B}$ is the **attitude profile matrix**:

$$
\mathbf{B} = \sum_{i=1}^{n} w_i \mathbf{b}_i \mathbf{r}_i^T
$$

Since $\sum w_i$ is a constant, minimizing $L(\mathbf{A})$ is equivalent to **maximizing the gain function**:

$$
g(\mathbf{A}) = \text{tr}(\mathbf{A} \mathbf{B}^T) = \sum_{i=1}^{n} w_i (\mathbf{b}_i \cdot \mathbf{A} \mathbf{r}_i)
$$

This reformulation is the starting point for most solution algorithms.

---

#### **Solution Algorithms**

Several efficient algorithms have been developed to solve Wahba's problem.

*   **[[QUEST Algorithm]] ([[Quaternion]] ESTimator):** The most famous method. It solves for the optimal [[Quaternion]] by finding the largest eigenvalue of a certain matrix. It is computationally efficient and widely used in practice.
*   **[[TRIAD Algorithm]]:** An analytical, non-optimal method that provides an exact solution but only for two [[vector]] pairs. It ignores the weighting and is less accurate than optimal methods when more than two vectors are available.
*   **FOAM (Fast Optimal Attitude Matrix):** Directly computes the optimal DCM from the singular value decomposition (SVD) of the $\mathbf{B}$ matrix.
*   **ESOQ (Estimator of the Optimal [[Quaternion]]):** Another eigenvalue-based method, related to QUEST.

---

#### **Applications**

Wahba's problem is the theoretical foundation for many [[attitude determination]] systems, especially those using:
*   **[[Star Tracker]]** measurements.
*   Combinations of sensors, such as a **[[Sun Sensor]] + [[Magnetometer]]** in small satellites.

---
#### **See Also**
*   [[Davenport's q-Method]] - A precursor to QUEST that also uses eigenvalue decomposition.
*   [[Kalman Filter]] - A recursive estimator often used for [[attitude determination]] that can incorporate dynamics and statistical noise models, often using the solution to Wahba's problem as a measurement update.

---
**Source / Further Reading:**
*   Original Paper: Wahba, G. (1965). "A Least Squares Estimate of Satellite Attitude".
*   Markley, F. L., & Crassidis, J. L. (2014). *Fundamentals of Spacecraft [[Attitude Determination]] and Control*. Springer.
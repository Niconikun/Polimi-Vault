#attitude-determination #quest-algorithm #wahbas-problem #[[Quaternion]] #optimal-estimation #ADCS #SAD 

**Definition:**
The **QU**aternion **EST**imator (QUEST) algorithm is a computationally efficient, deterministic method for solving [[Wahba's Problem]]. It is the first algorithm to directly compute the optimal **[[Quaternion]]** that minimizes Wahba's loss function without an iterative search. Its key innovation is recasting the problem into finding the largest [[Eigenvalues & Eigenvectors]] and corresponding eigenvector of a specially constructed matrix.

---

#### **Core Concept**

QUEST solves [[Wahba's problem]] by finding the optimal [[Quaternion]], which is the eigenvector corresponding to the largest eigenvalue of the **K-matrix** (or Davenport's matrix). The algorithm is celebrated for its speed, making it suitable for real-time [[attitude determination]] on spacecraft with limited computational resources.

---

#### **Mathematical Formulation**

Given a set of vector observations and their weights, the first step is to compute the **attitude profile matrix**, $\mathbf{B}$:

$$
\mathbf{B} = \sum_{i=1}^{n} w_i \mathbf{b}_i \mathbf{r}_i^T
$$

From $\mathbf{B}$, we form the $4 \times 4$ symmetric **K-matrix**:

$$
\mathbf{K} = \begin{bmatrix}
\mathbf{S} - \sigma \mathbf{I} & \mathbf{z} \\
\mathbf{z}^T & \sigma
\end{bmatrix}
$$

Where:
*   $\mathbf{S} = \mathbf{B} + \mathbf{B}^T$
*   $\mathbf{z} = \sum_{i=1}^{n} w_i (\mathbf{b}_i \times \mathbf{r}_i) = [B_{23} - B_{32}, B_{31} - B_{13}, B_{12} - B_{21}]^T$
*   $\sigma = \text{tr}(\mathbf{B})$
*   $\mathbf{I}$ is the $3 \times 3$ identity matrix.

The optimal [[Quaternion]], $\mathbf{q}_{opt}$, that minimizes Wahba's loss function is the eigenvector of $\mathbf{K}$ associated with its **largest eigenvalue**, $\lambda_{max}$.

---

#### **The QUEST Algorithm Steps**

1.  **Compute Inputs:** Calculate the attitude profile matrix $\mathbf{B}$, and then the vectors and scalars $\mathbf{S}$, $\mathbf{z}$, and $\sigma$.

2.  **Find the Largest Eigenvalue ($\lambda_{max}$):** Instead of performing a full eigenvalue decomposition, QUEST uses the [[characteristic equation]] of the $\mathbf{K}$-matrix. The largest eigenvalue is found by solving:
    $$
    \lambda_{max} = \lambda_{opt}
    $$
    This is typically done by applying [[Newton-Raphson Method]] iteration to the [[characteristic equation]], using $\lambda_0 = \sum w_i$ as a very accurate initial guess. This is a key reason for the algorithm's speed.

3.  **Compute the Optimal [[Quaternion]]:** Once $\lambda_{max}$ is known, the optimal [[Quaternion]] is calculated using the formula:
    $$
    \mathbf{q}_{opt} = \frac{1}{\sqrt{\gamma^2 + \lVert \mathbf{x} \rVert^2}} \begin{bmatrix} \mathbf{x} \\ \gamma \end{bmatrix}
    $$
    where:
    *   $\alpha = \lambda_{max}^2 - \sigma^2 + \text{tr}(\text{adj}(\mathbf{S}))$ (where $\text{adj}$ is the adjugate matrix)
    *   $\mathbf{x} = [\alpha \mathbf{I} + \beta \mathbf{S} + \mathbf{S}^2] \mathbf{z}$
    *   $\beta = \lambda_{max} - \sigma$
    *   $\gamma = (\lambda_{max} + \sigma)\beta - \det(\mathbf{S})$

    This step avoids a full eigenvector decomposition.

4.  **Normalize the [[Quaternion]]:** The resulting [[Quaternion]] $\mathbf{q}_{opt}$ is normalized to ensure it is a unit [[Quaternion]].

---

#### **Advantages and Disadvantages**

**Advantages:**
*   **Computational Efficiency:** Significantly faster than a general-purpose eigenvalue solver. The [[Newton-Raphson Method]] step for the eigenvalue is highly efficient.
*   **Non-Iterative Nature:** Provides a direct, closed-form solution once the eigenvalue is found.
*   **Widely Adopted:** It has been the workhorse algorithm for many spacecraft missions due to its proven performance and reliability.

**Disadvantages:**
*   **Numerical Issues:** Can suffer from numerical ill-conditioning when the two largest eigenvalues are very close or when the optimal eigenvalue is nearly equal to the initial guess $\lambda_0$. This is known as the "degeneracy" or "windmill" case.
*   **[[Singularity]]:** The [[Quaternion]] computation step has a mathematical singularity when $\gamma = 0$ and $\lVert \mathbf{x} \rVert = 0$, although this is a rare occurrence.

---

#### **Relationship to Other Methods**

*   **[[Davenport's q-Method]]:** QUEST is a computationally optimized version of the q-method. The q-method also uses the $\mathbf{K}$-matrix but solves for the eigenvector using a full eigenvalue decomposition, which is more computationally expensive.
*   **[[Wahba's Problem]]:** QUEST is a direct solution to this problem.
*   **[[TRIAD Algorithm]]:** Unlike the optimal QUEST, TRIAD is a sub-optimal, deterministic method that only uses two vector measurements exactly and ignores weights.

---
#### **See Also**
*   **[[ESOQ Algorithm]]** - A related eigenvector-based algorithm developed to address some of QUEST's numerical shortcomings.
*   **[[Kalman Filter]]** - A recursive filter that often uses the output of a QUEST solution as a measurement update for a more robust, dynamic attitude estimate.

---
**Source / Further Reading:**
*   Original Paper: Shuster, M. D., and Oh, S. D. (1981). "Three-Axis Attitude Determination from Vector Observations." *Journal of Guidance, Control, and Dynamics*.
*   Markley, F. L., & Crassidis, J. L. (2014). *Fundamentals of Spacecraft Attitude Determination and Control*. Springer.
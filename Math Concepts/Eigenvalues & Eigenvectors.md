#linear-algebra #eigenvalue #eigenvector #matrix-theory #attitude-determination #quest-algorithm #Math-Concepts 

**Definition:**
In [[linear algebra]], an **eigenvector** of a square matrix **A** is a nonzero vector **v** that, when multiplied by **A**, changes at most by a scalar factor. The corresponding **eigenvalue** (often denoted by λ, lambda) is the scalar factor by which the eigenvector is scaled. This relationship is formally defined by the **eigenvalue equation**:

$$
\mathbf{A} \mathbf{v} = \lambda \mathbf{v}
$$

Where:
*   **A** is an $n \times n$ matrix.
*   **v** is the eigenvector, a nonzero $n \times 1$ column vector.
*   λ is the eigenvalue, a scalar (which can be real or complex).

---

#### **Geometric Interpretation**

The equation $\mathbf{A} \mathbf{v} = \lambda \mathbf{v}$ reveals a fundamental property: the [[Transformation]] defined by the matrix **A**,
 when applied to its eigenvector **v**, does not rotate the vector. It only **stretches** or **shrinks** it by a factor of λ (or reverses its direction if λ is negative). The line spanned by the eigenvector is an **invariant [[Transformation]] subspace** under the transformation.

For example:
*   If $|\lambda| > 1$, the eigenvector is stretched.
*   If $|\lambda| = 1$, the eigenvector is unchanged in length (critical for rotation matrices).
*   If $0 < |\lambda| < 1$, the eigenvector is shrunk.
*   If $\lambda < 0$, the direction of the vector is reversed.

---

#### **Mathematical Solution: The [[Characteristic Equation]]**

The eigenvalues of a matrix **A** are found by solving the **[[characteristic equation]]**:

$$
\det(\mathbf{A} - \lambda \mathbf{I}) = 0
$$

Where $\mathbf{I}$ is the identity matrix of the same dimension as **A**. The left-hand side, $\det(\mathbf{A} - \lambda \mathbf{I})$, is a polynomial in λ called the **characteristic polynomial**. The roots of this polynomial are the eigenvalues of **A**.

Once an eigenvalue λ is known, its corresponding eigenvector **v** is found by solving the system of linear equations:

$$
(\mathbf{A} - \lambda \mathbf{I}) \mathbf{v} = \mathbf{0}
$$

---

#### **Relevance in [[Attitude Determination]] and Control**

Eigenvalue analysis is central to several key areas in [[Attitude Determination and Control System (ADCS)]]:

1.  **Solving [[Wahba's Problem]]:**
    Algorithms like the **[[QUEST Algorithm]]** and **[[Davenport's q-Method]]** rely fundamentally on eigenvalues. The optimal attitude [[Quaternion]] is the **eigenvector corresponding to the largest eigenvalue** of the Davenport K-matrix. The eigenvalue itself represents the optimal "gain" or quality of the fit from Wahba's loss function.

2.  **Stability Analysis of Controllers:**
    In [[Attitude Control]], the dynamics of a closed-loop system are often described by a state-space matrix. The **stability** of the system is determined by the eigenvalues of this matrix (often called the system's *poles*).
    *   A system is **stable** if all eigenvalues have **negative real parts** (they lie in the left-half of the complex plane).
    *   An eigenvalue with a positive real part indicates an **unstable** mode that will grow over time.

3.  **[[Principal Axes of Inertia]] and [[Inertia Tensor]]:**
    The **moment of [[inertia tensor]]**, **I**, is a symmetric 3x3 matrix. Its eigenvectors define the spacecraft's **principal axes**. When rotating about a principal axis, the [[Angular Momentum]] vector is parallel to the [[Angular Velocity]] vector, simplifying the dynamics ($\mathbf{L} = \mathbf{I}\boldsymbol{\omega}$ becomes a scalar equation along each principal axis). The corresponding eigenvalues are the **principal moments of inertia**.

4.  **Vibration Modes (Flexible Spacecraft):**
    For spacecraft with flexible appendages (like solar panels), the equations of motion can be decomposed into modes. Each mode has a characteristic shape (eigenvector) and [[Natural Frequency]] (related to the eigenvalue).

---

#### **Special Case: Eigenvalues of a Rotation Matrix**

For a proper 3x3 rotation matrix (a.k.a., a [[Direction Cosine Matrix]]), which is an **orthogonal matrix** ($\mathbf{A}^T\mathbf{A} = \mathbf{I}$), the eigenvalues have a special property:
*   One eigenvalue is always **+1**.
*   The other two eigenvalues are complex conjugates that lie on the unit circle, $e^{\pm i\phi}$, where $\phi$ is the angle of rotation.

The **eigenvector corresponding to the eigenvalue +1** is the **axis of rotation** (Euler's axis). This is a direct link to the [[Quaternion]] representation of attitude.

---
#### **See Also**
*   **Eigenvector** - The vector component of the eigen-pair.
*   **[[Characteristic Equation]]** - The equation used to find eigenvalues.
*   **[[Principal Component Analysis (PCA)]]** - A statistical technique that uses eigenvalue decomposition to find the principal directions in data.
*   **[[Pole Placement]]** - A control design technique that specifically sets the eigenvalues of the closed-loop system to achieve desired stability and performance characteristics.

---
**Source / Further Reading:**
*   Strang, G. (2016). *Introduction to Linear Algebra*. Wellesley-Cambridge Press.
*   Markley, F. L., & Crassidis, J. L. (2014). *Fundamentals of Spacecraft Attitude Determination and Control*. Springer. (For applications in ADCS).
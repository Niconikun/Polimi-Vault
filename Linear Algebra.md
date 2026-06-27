---
title: Linear Algebra
tags:
  - mathematics
  - control theory
  - numerical methods
  - systems theory
---

# Linear Algebra

## Formal Definition

**Linear algebra** is the branch of mathematics concerned with [[Vector|vectors]], [[Matrix|matrices]], linear transformations, and systems of linear equations. It provides the fundamental mathematical framework for studying linear systems, vector spaces, and their properties. Linear algebra is indispensable in modern applied mathematics, engineering, computer science, and physics, particularly in [[Control Systems|control theory]], [[State Vector|state-space representation]] of dynamical systems, and numerical computation.

## Historical Development

### Key Milestones
- **1683:** Gottfried Wilhelm Leibniz develops the theory of determinants
- **1750:** Gabriel Cramer publishes Cramer's rule for solving linear systems
- **1858:** Arthur Cayley introduces matrix notation and matrix algebra
- **1926:** Werner Heisenberg uses matrix formulation in quantum mechanics
- **1960s:** Development of modern computational linear algebra algorithms (LU decomposition, QR decomposition)
- **20th-21st Century:** Linear algebra becomes central to computer graphics, machine learning, and modern control systems

### Foundational Contributors
1. **Arthur Cayley (1821–1895):** Developed matrix theory and linear transformations
2. **David Hilbert (1862–1943):** Formulated abstract vector spaces and spectral theory
3. **John von Neumann (1903–1957):** Developed numerical algorithms and functional analysis foundations
4. **Alston Householder & Gene Golub:** Advanced computational methods in linear algebra

## Mathematical Formulation

### Basic Objects and Operations

**Vector (Column Vector in $\mathbb{R}^n$):**
$$
\mathbf{v} = \begin{bmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{bmatrix}
$$

**Matrix (Linear Map from $\mathbb{R}^m$ to $\mathbb{R}^n$):**
$$
\mathbf{A} = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1m} \\ a_{21} & a_{22} & \cdots & a_{2m} \\ \vdots & \vdots & \ddots & \vdots \\ a_{n1} & a_{n2} & \cdots & a_{nm} \end{bmatrix}
$$

**Matrix-Vector Multiplication:**
$$
\mathbf{y} = \mathbf{A}\mathbf{x}
$$

Where $\mathbf{A} \in \mathbb{R}^{m \times n}$, $\mathbf{x} \in \mathbb{R}^n$, and $\mathbf{y} \in \mathbb{R}^m$.

**Matrix-Matrix Multiplication:**
$$
\mathbf{C} = \mathbf{A}\mathbf{B}
$$

where $\mathbf{C}_{ij} = \sum_{k=1}^{p} \mathbf{A}_{ik}\mathbf{B}_{kj}$.

### Fundamental Concepts

**Vector Space:**
A set $V$ with operations of vector addition and scalar multiplication satisfying eight axioms (closure, associativity, commutativity, identity, inverse, distributivity, associativity of scalar multiplication, scalar identity).

**Linear Independence:**
A set of vectors $\{\mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_k\}$ is linearly independent if:
$$
c_1\mathbf{v}_1 + c_2\mathbf{v}_2 + \cdots + c_k\mathbf{v}_k = \mathbf{0} \implies c_i = 0 \, \forall i
$$

**Basis and Dimension:**
A [[Linear Independence|linearly independent]] spanning set of a vector space; dimension is the number of basis vectors.

**Rank:**
The dimension of the column space (or row space) of a matrix; maximum number of linearly independent rows or columns.

## Special Cases

### Important Matrix Classes

1. **Identity Matrix:**
   $$
   \mathbf{I} = \begin{bmatrix} 1 & 0 & \cdots & 0 \\ 0 & 1 & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & 1 \end{bmatrix}
   $$

2. **Diagonal Matrix:**
   $$
   \mathbf{D} = \begin{bmatrix} d_1 & 0 & \cdots & 0 \\ 0 & d_2 & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & d_n \end{bmatrix}
   $$

3. **Orthogonal Matrix:** $\mathbf{Q}^T\mathbf{Q} = \mathbf{I}$ (preserves vector lengths and angles)

4. **Symmetric Matrix:** $\mathbf{A} = \mathbf{A}^T$ (eigenvalues are real, eigenvectors orthogonal)

5. **Positive Definite Matrix:** $\mathbf{x}^T\mathbf{A}\mathbf{x} > 0$ for all $\mathbf{x} \neq \mathbf{0}$

## Fundamental Principles

### Core Theorems

1. **Rank-Nullity Theorem:**
   $$
   \text{rank}(\mathbf{A}) + \text{nullity}(\mathbf{A}) = n
   $$
   where $n$ is the number of columns.

2. **Spectral Theorem:** For symmetric matrices, there exists an orthonormal basis of [[Eigenvectors]] with real eigenvalues.

3. **Singular Value Decomposition (SVD):** Every matrix $\mathbf{A} \in \mathbb{R}^{m \times n}$ can be decomposed as:
   $$
   \mathbf{A} = \mathbf{U}\boldsymbol{\Sigma}\mathbf{V}^T
   $$
   where $\mathbf{U}, \mathbf{V}$ are orthogonal and $\boldsymbol{\Sigma}$ is diagonal.

4. **Cayley-Hamilton Theorem:** Every square matrix satisfies its own characteristic polynomial.

## Theoretical Framework

### Eigenvalue Decomposition

For a diagonalizable matrix $\mathbf{A}$:
$$
\mathbf{A} = \mathbf{P}\boldsymbol{\Lambda}\mathbf{P}^{-1}
$$

Where:
- $\mathbf{P}$: matrix of eigenvectors
- $\boldsymbol{\Lambda}$: diagonal matrix of eigenvalues
- Eigenvalues satisfy: $\det(\mathbf{A} - \lambda \mathbf{I}) = 0$
- Eigenvectors satisfy: $\mathbf{A}\mathbf{v} = \lambda \mathbf{v}$

**Applications:**
- Stability analysis via eigenvalues of system matrix $\mathbf{A}$ in [[State Vector]] dynamics
- Principal component analysis in machine learning
- Vibration modes in structural dynamics

### Matrix Norms and Conditioning

**Frobenius Norm:**
$$
\|\mathbf{A}\|_F = \sqrt{\sum_{i,j} a_{ij}^2}
$$

**Spectral Norm (Operator Norm):**
$$
\|\mathbf{A}\|_2 = \sqrt{\lambda_{\max}(\mathbf{A}^T\mathbf{A})}
$$

**Condition Number:**
$$
\kappa(\mathbf{A}) = \|\mathbf{A}\| \cdot \|\mathbf{A}^{-1}\|
$$
Measures sensitivity to numerical errors; large condition number indicates ill-conditioning.

## Classification and Variants

### By System Type

1. **Overdetermined Systems** ($m > n$): More equations than unknowns; typically no exact solution
   - Solved via [[Least Squares Method]]: $\mathbf{A}^T\mathbf{A}\mathbf{x} = \mathbf{A}^T\mathbf{b}$

2. **Square Systems** ($m = n$): Equal equations and unknowns
   - Unique solution if matrix is invertible: $\mathbf{x} = \mathbf{A}^{-1}\mathbf{b}$

3. **Underdetermined Systems** ($m < n$): More unknowns than equations
   - Infinite solutions; minimum-norm solution via Moore-Penrose [[Pseudo-inverse|pseudo-inverse]]

### By Computational Method

1. **Direct Methods:** [[QR Decomposition|QR decomposition]], LU factorization, exact arithmetic
2. **Iterative Methods:** Power method, [[Subspace Iteration Method]], conjugate gradient
3. **Sparse Methods:** Specialized algorithms for sparse matrices (many zeros)

## Practical Algorithms

### Gaussian Elimination and LU Decomposition

Decomposes $\mathbf{A} = \mathbf{L}\mathbf{U}$ where $\mathbf{L}$ is lower triangular, $\mathbf{U}$ is upper triangular.

**Forward substitution:** Solve $\mathbf{L}\mathbf{y} = \mathbf{b}$  
**Back substitution:** Solve $\mathbf{U}\mathbf{x} = \mathbf{y}$

### QR Decomposition

Decomposes $\mathbf{A} = \mathbf{Q}\mathbf{R}$ where:
- $\mathbf{Q}$: orthogonal matrix (columns are orthonormal)
- $\mathbf{R}$: upper triangular matrix

Preferred for numerical stability and solving least squares problems.

### Eigenvalue Computation

**Power Method:** Iteratively computes dominant eigenvalue
$$
\mathbf{v}_{k+1} = \frac{\mathbf{A}\mathbf{v}_k}{\|\mathbf{A}\mathbf{v}_k\|}
$$

**QR Algorithm:** Computes all eigenvalues via repeated QR decomposition

## Relationship to Other Concepts

1. **Connection to [[Control Systems]]:**
   - [[State Vector]] dynamics: $\dot{\mathbf{x}} = \mathbf{A}\mathbf{x} + \mathbf{B}\mathbf{u}$
   - Stability determined by eigenvalues of $\mathbf{A}$
   - Pole placement and [[Linear Quadratic Regulator]] use eigenvalue assignment

2. **Connection to [[Differential Equations]]:**
   - Systems of linear ODEs: $\dot{\mathbf{x}} = \mathbf{A}\mathbf{x}$ has solution $\mathbf{x}(t) = e^{\mathbf{A}t}\mathbf{x}_0$
   - Characteristic polynomial determines solution structure

3. **Connection to [[Numerical Analysis]]:**
   - Foundation for computational methods
   - Error analysis via condition numbers
   - Stability of algorithms

4. **Connection to [[Signal Processing]] and [[Machine Learning]]:**
   - Matrix operations underlie neural networks
   - Fast Fourier Transform uses matrix factorization
   - Data compression via SVD

## Applications

### Engineering and Physics

- **Structural Analysis:** Stiffness matrices and mode superposition
- **Circuit Analysis:** Nodal admittance and impedance matrices
- **Spacecraft Dynamics:** [[State Vector]] representation of attitude control systems
- **Quantum Mechanics:** Operators as matrices, measurements as eigenvalue problems

### Control and Estimation

- **[[Linear Quadratic Regulator|Optimal Control]]:** Solve Riccati equations via eigenvalue methods
- **[[Kalman Filter]]:** Uses matrix operations for estimation and covariance propagation
- **Observer Design:** Eigenvalue assignment for state estimation

### Computation and Data

- **Image Processing:** Convolutions implemented as matrix multiplications
- **Machine Learning:** Neural network training via gradient-based optimization
- **Data Compression:** Principal component analysis via SVD

## See Also

- [[State Vector]]
- [[Linear Quadratic Regulator]]
- [[Kalman Filter]]
- [[Control Systems]]
- [[Differential Equations]]
- [[Least Squares Method]]
- [[QR Decomposition]]
- [[Characteristic Equation]]
- [[Numerical Analysis]]
- [[Signal Processing]]

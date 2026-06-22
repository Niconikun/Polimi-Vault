## Formal Definition

The **Gram-Schmidt Process** is an algorithm for orthogonalizing a set of linearly independent vectors in an inner product space. The method takes a non-orthogonal basis and produces an orthonormal basis by successively subtracting the projection of each vector onto the subspace spanned by the previously orthogonalized vectors. Gram-Schmidt is fundamental to numerical linear algebra, forming the theoretical and computational basis for QR decomposition and many applications in scientific computing.

## Historical Development

### Key Milestones
- **1883:** J.P. Gram publishes the orthogonalization method in the context of least squares problems
- **1907:** Erhard Schmidt rediscovers the method while studying integral equations
- **1950s:** Algorithm recognized as fundamental to numerical linear algebra
- **1960s:** Development of modified Gram-Schmidt for improved numerical stability
- **1970s:** Analysis of numerical stability and round-off error propagation
- **1980s:** Integration into standard linear algebra packages (LINPACK, LAPACK)
- **1990s:** Parallel versions for high-performance computing
- **2000s:** Applications in signal processing and machine learning

### Foundational Contributors
1. **Jørgen Pedersen Gram (1850-1916):** First described the orthogonalization process in "On Series Development Using the Least Squares Method"
2. **Erhard Schmidt (1876-1959):** Independently developed the method in the context of Hilbert spaces
3. **Alston Scott Householder (1904-1993):** Analyzed numerical stability aspects
4. **James H. Wilkinson (1919-1986):** Provided detailed error analysis for numerical implementations

## Mathematical Formulation

### General Form

Given a set of linearly independent vectors $\{\mathbf{v}_1, \mathbf{v}_2, \ldots, \mathbf{v}_n\}$ in an inner product space $V$, the Gram-Schmidt process produces an orthonormal set $\{\mathbf{u}_1, \mathbf{u}_2, \ldots, \mathbf{u}_n\}$ where:
1. $\text{span}\{\mathbf{u}_1, \ldots, \mathbf{u}_k\} = \text{span}\{\mathbf{v}_1, \ldots, \mathbf{v}_k\}$ for all $k$
2. $\langle \mathbf{u}_i, \mathbf{u}_j \rangle = \delta_{ij}$ (orthonormal)

### Classical Gram-Schmidt Algorithm

For $k = 1, 2, \ldots, n$:

**Projection step:**
$$
\mathbf{u}_k = \mathbf{v}_k - \sum_{j=1}^{k-1} \text{proj}_{\mathbf{u}_j}(\mathbf{v}_k)
$$

where $\text{proj}_{\mathbf{u}_j}(\mathbf{v}_k) = \frac{\langle \mathbf{v}_k, \mathbf{u}_j \rangle}{\langle \mathbf{u}_j, \mathbf{u}_j \rangle} \mathbf{u}_j$

**Normalization step:**
$$
\mathbf{u}_k = \frac{\mathbf{u}_k}{\|\mathbf{u}_k\|}
$$

### Modified Gram-Schmidt Algorithm (Numerically Stable Version)

For $k = 1, 2, \ldots, n$:
1. $\mathbf{u}_k = \mathbf{v}_k$
2. For $j = 1, 2, \ldots, k-1$:
   $$
   r_{jk} = \langle \mathbf{u}_k, \mathbf{u}_j \rangle
   $$
   $$
   \mathbf{u}_k = \mathbf{u}_k - r_{jk} \mathbf{u}_j
   $$
3. $r_{kk} = \|\mathbf{u}_k\|$
4. $\mathbf{u}_k = \frac{\mathbf{u}_k}{r_{kk}}$

### Matrix Formulation (QR Decomposition)

Given matrix $A \in \mathbb{R}^{m \times n}$ with linearly independent columns $\mathbf{a}_1, \ldots, \mathbf{a}_n$, Gram-Schmidt computes:
$$
A = QR
$$
where $Q \in \mathbb{R}^{m \times n}$ has orthonormal columns and $R \in \mathbb{R}^{n \times n}$ is upper triangular.

**Recursive construction:**
$$
\mathbf{q}_k = \frac{\mathbf{a}_k - \sum_{j=1}^{k-1} \langle \mathbf{a}_k, \mathbf{q}_j \rangle \mathbf{q}_j}{\|\mathbf{a}_k - \sum_{j=1}^{k-1} \langle \mathbf{a}_k, \mathbf{q}_j \rangle \mathbf{q}_j\|}
$$

**Matrix entries:**
$$
r_{jk} = \langle \mathbf{a}_k, \mathbf{q}_j \rangle, \quad j < k
$$
$$
r_{kk} = \|\mathbf{a}_k - \sum_{j=1}^{k-1} r_{jk} \mathbf{q}_j\|
$$

## Fundamental Principles

### Orthogonality Principle

**Key idea:** At each step, subtract from the current vector its components in the directions of all previously orthogonalized vectors:
$$
\mathbf{u}_k \perp \text{span}\{\mathbf{u}_1, \ldots, \mathbf{u}_{k-1}\}
$$

**Geometric interpretation:** Successive orthogonal projection onto orthogonal complements.

### Span Preservation

**Invariant property:** For each $k$:
$$
\text{span}\{\mathbf{u}_1, \ldots, \mathbf{u}_k\} = \text{span}\{\mathbf{v}_1, \ldots, \mathbf{v}_k\}
$$

**Inductive construction:** Each step adds one dimension while maintaining orthogonality to previous dimensions.

### Norm Preservation (up to scaling)

**Before normalization:** 
$$
\|\mathbf{u}_k\| = \|\mathbf{v}_k - \sum_{j=1}^{k-1} \text{proj}_{\mathbf{u}_j}(\mathbf{v}_k)\|
$$

**After normalization:** $\|\mathbf{u}_k\| = 1$

## Theoretical Framework

### Existence and Uniqueness

**Theorem:** For any finite set of linearly independent vectors in an inner product space, there exists a unique (up to sign) orthonormal set with the same span constructed via Gram-Schmidt.

**Proof sketch:** Induction on the number of vectors, using the fact that $\mathbf{v}_k \notin \text{span}\{\mathbf{v}_1, \ldots, \mathbf{v}_{k-1}\}$ ensures $\mathbf{u}_k \neq \mathbf{0}$.

### Relationship to QR Decomposition

**Matrix factorization viewpoint:** Gram-Schmidt is one method to compute QR decomposition:
- $Q$ matrix: orthonormal vectors from Gram-Schmidt
- $R$ matrix: coefficients from projection steps
- $A = QR$ provides both orthogonalization and triangularization

### Numerical Stability Analysis

**Classical Gram-Schmidt:** Can lose orthogonality due to round-off error when vectors are nearly linearly dependent.

**Modified Gram-Schmidt:** Improved stability by orthogonalizing against all previous vectors at each step:
$$
\|\mathbf{q}_i^T \mathbf{q}_j\| \leq \epsilon \cdot \kappa(A), \quad i \neq j
$$
where $\epsilon$ is machine precision and $\kappa(A)$ is condition number.

### Error Propagation

**Forward error bound:** For computed vectors $\tilde{\mathbf{q}}_k$:
$$
\|\tilde{\mathbf{q}}_k - \mathbf{q}_k\| \leq c_1(n) \epsilon \kappa(A)
$$

**Loss of orthogonality:** 
$$
\|I - \tilde{Q}^T \tilde{Q}\| \leq c_2(n) \epsilon \kappa(A)
$$

## Classification and Variants

### By Algorithm Type
1. **Classical Gram-Schmidt (CGS):** Straightforward but numerically unstable
2. **Modified Gram-Schmidt (MGS):** More stable, reorthogonalizes at each step
3. **Householder QR:** Uses reflections, most stable but more expensive
4. **Givens QR:** Uses rotations, stable and suitable for sparse matrices

### By Application Domain
1. **Standard Gram-Schmidt:** For real vector spaces with Euclidean inner product
2. **Complex Gram-Schmidt:** For complex vector spaces with Hermitian inner product
3. **Weighted Gram-Schmidt:** For inner products with weight matrices
4. **Block Gram-Schmidt:** For orthogonalizing blocks of vectors simultaneously

### By Implementation Strategy
1. **Sequential Gram-Schmidt:** One vector at a time
2. **Parallel Gram-Schmidt:** Multiple vectors processed concurrently
3. **Iterative Gram-Schmidt:** With reorthogonalization for higher accuracy
4. **Selective Gram-Schmidt:** Only orthogonalize when needed based on condition estimates

## Derivation and Proof

### Derivation from Orthogonal Projection

**Starting point:** Given $\mathbf{v}_1, \ldots, \mathbf{v}_n$, want orthonormal $\mathbf{q}_1, \ldots, \mathbf{q}_n$ with same span.

**Step 1:** First vector:
$$
\mathbf{q}_1 = \frac{\mathbf{v}_1}{\|\mathbf{v}_1\|}
$$

**Step k:** Orthogonalize $\mathbf{v}_k$ against previous $\mathbf{q}_1, \ldots, \mathbf{q}_{k-1}$:
$$
\mathbf{w}_k = \mathbf{v}_k - \sum_{j=1}^{k-1} \langle \mathbf{v}_k, \mathbf{q}_j \rangle \mathbf{q}_j
$$

**Normalization:**
$$
\mathbf{q}_k = \frac{\mathbf{w}_k}{\|\mathbf{w}_k\|}
$$

**Proof of orthogonality:** For $i < k$:
$$
\langle \mathbf{q}_k, \mathbf{q}_i \rangle = \frac{1}{\|\mathbf{w}_k\|} \left( \langle \mathbf{v}_k, \mathbf{q}_i \rangle - \sum_{j=1}^{k-1} \langle \mathbf{v}_k, \mathbf{q}_j \rangle \langle \mathbf{q}_j, \mathbf{q}_i \rangle \right)
$$
Since $\langle \mathbf{q}_j, \mathbf{q}_i \rangle = \delta_{ji}$:
$$
\langle \mathbf{q}_k, \mathbf{q}_i \rangle = \frac{1}{\|\mathbf{w}_k\|} \left( \langle \mathbf{v}_k, \mathbf{q}_i \rangle - \langle \mathbf{v}_k, \mathbf{q}_i \rangle \right) = 0
$$

### QR Decomposition Derivation

**From Gram-Schmidt to QR:** Let $A = [\mathbf{a}_1, \ldots, \mathbf{a}_n]$. Gram-Schmidt gives:
$$
\mathbf{a}_k = \sum_{j=1}^{k} r_{jk} \mathbf{q}_j
$$
where $r_{jk} = \langle \mathbf{a}_k, \mathbf{q}_j \rangle$ for $j < k$ and $r_{kk} = \|\mathbf{w}_k\|$.

**Matrix form:** 
$$
A = [\mathbf{q}_1, \ldots, \mathbf{q}_n] 
\begin{bmatrix}
r_{11} & r_{12} & \cdots & r_{1n} \\
0 & r_{22} & \cdots & r_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \cdots & r_{nn}
\end{bmatrix}
= QR
$$

## Physical Interpretation

### Geometric Construction

**Vector subtraction of projections:** Each step removes the component of the current vector that lies in the subspace spanned by previous vectors:
- Visualizable in 3D as successive perpendicular drops
- Creates orthogonal coordinate system from arbitrary basis
- Analogous to constructing perpendicular axes from slanted ones

### Stability Analogy

**Structural engineering analogy:** Like ensuring load paths are orthogonal to avoid coupled deformations:
- Non-orthogonal basis vectors create "cross-talk" between dimensions
- Gram-Schmidt decouples directions, making analysis simpler
- Similar to principal stress transformation in mechanics

### Signal Processing Interpretation

**Filtering viewpoint:** Gram-Schmidt acts as a decorrelator:
- Input: correlated signals (non-orthogonal vectors)
- Output: uncorrelated signals (orthogonal vectors)
- Each step removes correlation with previous signals
- Basis for whitening filters and independent component analysis

## Applications

### Numerical Linear Algebra
1. **QR decomposition:** Fundamental algorithm for solving linear systems
2. **Least squares problems:** Orthogonal basis simplifies normal equations
3. **Eigenvalue algorithms:** Used in QR algorithm and subspace methods
4. **Singular value decomposition:** Building block for computing SVD
5. **Linear independence testing:** Detects near-linear dependence

### Engineering Disciplines
1. **Structural analysis:** [[Modal Analysis]] and coordinate transformation
2. **Control systems:** State-space realization and model reduction
3. **Signal processing:** Adaptive filters and spectral estimation
4. **Computer graphics:** Orthonormal basis for lighting calculations
5. **Robotics:** Jacobian orthogonalization for singularity avoidance

### Scientific Computing
1. **Finite element methods:** Constructing orthogonal shape functions
2. **Computational fluid dynamics:** Pressure projection methods
3. **Quantum mechanics:** Orthogonalizing wavefunctions
4. **Statistics:** Principal component analysis and regression
5. **Machine learning:** Feature orthogonalization and whitening

## Implementation Considerations

### Numerical Stability

**Classical vs. Modified Gram-Schmidt:**
- **CGS:** $\|\mathbf{q}_i^T \mathbf{q}_j\| \approx \epsilon \cdot \kappa^2(A)$
- **MGS:** $\|\mathbf{q}_i^T \mathbf{q}_j\| \approx \epsilon \cdot \kappa(A)$

**Reorthogonalization:** If $\|\mathbf{w}_k\|$ is small relative to $\|\mathbf{v}_k\|$, reorthogonalize:
$$
\mathbf{w}_k \leftarrow \mathbf{w}_k - \sum_{j=1}^{k-1} \langle \mathbf{w}_k, \mathbf{q}_j \rangle \mathbf{q}_j
$$

### Computational Complexity

**For $m \times n$ matrix ($m \geq n$):**
- **CGS:** $\approx 2mn^2$ flops
- **MGS:** $\approx 2mn^2$ flops (same operation count, better stability)
- **Householder QR:** $\approx 2mn^2 - \frac{2}{3}n^3$ flops (more stable)

**Memory requirements:** $O(mn)$ for storing $Q$ matrix

### Algorithm Implementation

```python
def modified_gram_schmidt(A):
    """
    Modified Gram-Schmidt for QR decomposition
    
    Parameters
    ----------
    A : numpy.ndarray
        Input matrix of size m x n with linearly independent columns
    
    Returns
    -------
    Q : numpy.ndarray
        Orthonormal matrix of size m x n
    R : numpy.ndarray
        Upper triangular matrix of size n x n
    """
    m, n = A.shape
    Q = np.zeros((m, n))
    R = np.zeros((n, n))
    
    for k in range(n):
        # Copy k-th column of A to q
        q = A[:, k].copy()
        
        # Orthogonalize against previous columns
        for j in range(k):
            R[j, k] = np.dot(Q[:, j], q)
            q -= R[j, k] * Q[:, j]
        
        # Check for linear dependence
        norm_q = np.linalg.norm(q)
        if norm_q < 1e-12:
            raise ValueError("Columns of A are linearly dependent")
        
        # Normalize and store
        R[k, k] = norm_q
        Q[:, k] = q / norm_q
    
    return Q, R
```

### Parallel Implementation

**Block Gram-Schmidt:**
1. Partition vectors into blocks
2. Orthogonalize within each block
3. Orthogonalize blocks against each other
4. Suitable for distributed memory systems

**Communication pattern:** All-reduce for dot products, all-gather for orthogonalization against previous vectors

## Advantages and Limitations

### Strengths
1. **Conceptual simplicity:** Easy to understand and implement
2. **Incremental computation:** Can add vectors without recomputing everything
3. **Flexibility:** Works with any inner product space
4. **Numerical stability (MGS):** Reasonably stable for well-conditioned problems
5. **Parallelizability:** Block versions suitable for parallel computing

### Weaknesses
1. **Numerical instability (CGS):** Can lose orthogonality for ill-conditioned matrices
2. **Sequential nature:** Difficult to parallelize efficiently
3. **O(n²) complexity:** Expensive for large matrices
4. **Breakdown for dependent vectors:** Requires linear independence
5. **Storage requirements:** Need to store all vectors during processing

### Validity Range
- **Applicable when:** Matrix has full column rank, condition number not too large
- **Not applicable when:** Columns are linearly dependent or nearly dependent
- **Best results:** With modified Gram-Schmidt and reorthogonalization
- **Alternative needed:** For very ill-conditioned problems, use Householder QR

## Advanced Topics

### Weighted Gram-Schmidt

**For weighted inner products:** $\langle \mathbf{x}, \mathbf{y} \rangle_W = \mathbf{x}^T W \mathbf{y}$ where $W$ is symmetric positive definite:
$$
\mathbf{q}_k = \frac{\mathbf{v}_k - \sum_{j=1}^{k-1} \frac{\langle \mathbf{v}_k, \mathbf{q}_j \rangle_W}{\langle \mathbf{q}_j, \mathbf{q}_j \rangle_W} \mathbf{q}_j}{\|\mathbf{v}_k - \sum_{j=1}^{k-1} \frac{\langle \mathbf{v}_k, \mathbf{q}_j \rangle_W}{\langle \mathbf{q}_j, \mathbf{q}_j \rangle_W} \mathbf{q}_j\|_W}
$$

**Applications:** Finite elements with non-uniform meshes, statistics with correlated errors

### Iterative Refinement

**Double Gram-Schmidt:** Apply Gram-Schmidt twice to improve orthogonality:
1. Compute $Q_1, R_1 = \text{GS}(A)$
2. Compute $Q_2, R_2 = \text{GS}(Q_1)$
3. $Q = Q_2$, $R = R_2 R_1$

**Error reduction:** Can improve orthogonality by factor $\epsilon \kappa(A)$ to $\epsilon$

### Randomized Gram-Schmidt

**For very large matrices:** Use randomization to reduce computational cost:
1. Sketch matrix using random projections
2. Apply Gram-Schmidt to sketch
3. Map back to original space

**Theoretical guarantees:** High probability bounds on orthogonality loss

### Gram-Schmidt in Function Spaces

**For orthogonal polynomials:** Construct orthogonal polynomial bases:
- Start with monomials $1, x, x^2, \ldots$
- Apply Gram-Schmidt with appropriate inner product
- Yields Legendre, Chebyshev, Hermite polynomials

**Continuous analogue:** Apply to basis functions in $L^2$ space

## Special Cases and Examples

### 2D and 3D Geometric Examples

**In $\mathbb{R}^2$:** Given $\mathbf{v}_1 = (1, 1)$, $\mathbf{v}_2 = (1, 0)$:
1. $\mathbf{q}_1 = \frac{1}{\sqrt{2}}(1, 1)$
2. $\mathbf{w}_2 = (1, 0) - \frac{1}{2}(1, 1) = (\frac{1}{2}, -\frac{1}{2})$
3. $\mathbf{q}_2 = \frac{1}{\sqrt{2}}(1, -1)$

**In $\mathbb{R}^3$:** Standard basis construction from arbitrary vectors.

### Ill-Conditioned Example

**Hilbert matrix:** $H_n$ with $h_{ij} = 1/(i+j-1)$:
- Condition number grows exponentially: $\kappa(H_n) \approx e^{3.5n}$
- Classical Gram-Schmidt fails for $n > 10$
- Modified Gram-Schmidt with reorthogonalization works for larger $n$

### Application in [[Structural Dynamics]]

**Mass-normalized mode shapes:** Given approximate mode shapes $\Phi$, orthogonalize with respect to mass matrix $M$:
$$
\Psi = \text{GS}_M(\Phi)
$$
where $\text{GS}_M$ uses inner product $\langle \mathbf{x}, \mathbf{y} \rangle_M = \mathbf{x}^T M \mathbf{y}$.

**Result:** $\Psi^T M \Psi = I$, $\Psi^T K \Psi = \Lambda$ (diagonal)

## Error Analysis

### Round-off Error Propagation

**For modified Gram-Schmidt:** Computed vectors satisfy:
$$
\tilde{Q} = Q + E, \quad \|E\| \leq c(n) \epsilon \|A\| \|A^\dagger\|
$$
where $A^\dagger$ is pseudoinverse.

**Loss of orthogonality:** 
$$
\|I - \tilde{Q}^T \tilde{Q}\| \leq c'(n) \epsilon \kappa(A)
$$

### Breakdown Conditions

**Linear dependence detection:** When $\|\mathbf{w}_k\| < \tau \|\mathbf{v}_k\|$:
- $\tau \approx \epsilon$ for exact dependence
- $\tau \approx \sqrt{\epsilon}$ for numerical rank detection
- Algorithm can continue by setting $\mathbf{q}_k = \mathbf{0}$ or generating random orthogonal vector

### Forward Error Analysis

**For computed QR factorization:** 
$$
\|\tilde{Q}\tilde{R} - A\| \leq f(m, n) \epsilon \|A\|
$$
where $f(m, n)$ is low-degree polynomial in $m$ and $n$.

## Relationship to Other Concepts

### Connection to QR Decomposition

**Gram-Schmidt as QR algorithm:** One method to compute $A = QR$
**Alternative methods:** Householder reflections, Givens rotations
**Comparison:** Gram-Schmidt is simpler but less stable than Householder

### Relationship to Least Squares

**Normal equations:** $A^TA\mathbf{x} = A^T\mathbf{b}$
**QR approach:** $R\mathbf{x} = Q^T\mathbf{b}$ (more stable)
**Gram-Schmidt computes $Q$ and $R$ for QR approach**

### Contrast with Householder QR

**Gram-Schmidt:**
- Computes $Q$ explicitly
- More intuitive geometric interpretation
- Less stable for ill-conditioned problems

**Householder:**
- Implicitly computes $Q$ as product of reflections
- More numerically stable
- Better for rank-deficient problems

### Connection to Orthogonal Polynomials

**Gram-Schmidt process:** Applied to monomials with weighted inner products
**Result:** Classical orthogonal polynomials (Legendre, Chebyshev, etc.)
**Applications:** Spectral methods, Gaussian quadrature

## Historical Context and Evolution

### Original Motivation

**Least squares problems:** Gram developed the method while studying approximations using least squares in 1883.

**Integral equations:** Schmidt rediscovered the method while studying eigenvalue problems for integral operators in 1907.

**Numerical linear algebra:** Became fundamental algorithm with the development of digital computers in the 1950s.

### Evolution Over Time

1. **1883-1907:** Independent discoveries by Gram and Schmidt
2. **1950s:** Implementation on early computers, recognition of numerical issues
3. **1960s:** Development of modified Gram-Schmidt for better stability
4. **1970s:** Error analysis by Wilkinson and others
5. **1980s:** Inclusion in LINPACK and other numerical libraries
6. **1990s:** Parallel implementations for high-performance computing
7. **2000s:** Applications in signal processing and machine learning
8. **2010s:** Randomized variants for large-scale problems

### Modern Perspectives

**Still fundamental:** Despite more stable alternatives, Gram-Schmidt remains important pedagogically and for certain applications.

**Randomized linear algebra:** Gram-Schmidt forms basis for randomized orthogonalization methods.

**Tensor computations:** Extended to higher-order tensors for multilinear algebra.

## Pedagogical Approach

### Teaching Strategies

1. **Geometric introduction:** Start with 2D and 3D examples showing orthogonal projection
2. **Step-by-step derivation:** Show the projection formula and normalization
3. **Numerical examples:** Illustrate with small matrices, compare CGS vs MGS
4. **Connection to applications:** Show how QR decomposition solves least squares
5. **Implementation exercise:** Have students code both classical and modified versions

### Common Misconceptions

1. **"Gram-Schmidt always produces perfect orthogonality":** Neglects numerical stability issues
2. **"Classical and modified are mathematically different":** They're algebraically identical but numerically different
3. **"Gram-Schmidt only works for Euclidean inner products":** Works for any inner product space
4. **"The order of vectors doesn't matter":** Different order produces different orthonormal basis (though same span)

### Learning Resources

**Foundational Texts:**
- Golub & Van Loan, "Matrix Computations" (Chapter 5)
- Trefethen & Bau, "Numerical Linear Algebra" (Lecture 8)
- Demmel, "Applied Numerical Linear Algebra" (Chapter 2)
- Strang, "[[Linear Algebra]] and Its Applications" (Chapter 4)

**Online Resources:**
- MIT OpenCourseWare 18.06 (Linear Algebra)
- Khan Academy: Gram-Schmidt process visualizations
- Wikipedia: Detailed algorithm and examples
- YouTube: 3Blue1Brown geometric explanations

**Interactive Tools:**
- GeoGebra: Visualize Gram-Schmidt in 2D and 3D
- Jupyter notebooks: Numerical experiments with different matrices
- MATLAB/Octave: Compare `qr` function with custom Gram-Schmidt

## Implementation in Software

### MATLAB Implementation

```matlab
function [Q, R] = gram_schmidt(A, mode)
% Gram-Schmidt QR factorization
% mode: 'classical' or 'modified'
    
    [m, n] = size(A);
    Q = zeros(m, n);
    R = zeros(n, n);
    
    if strcmpi(mode, 'classical')
        % Classical Gram-Schmidt
        for k = 1:n
            % Project a_k onto previous q's
            for j = 1:k-1
                R(j, k) = Q(:, j)' * A(:, k);
            end
            
            % Compute q_k
            q = A(:, k);
            for j = 1:k-1
                q = q - R(j, k) * Q(:, j);
            end
            
            % Normalize
            R(k, k) = norm(q);
            if R(k, k) > eps
                Q(:, k) = q / R(k, k);
            else
                error('Columns of A are linearly dependent');
            end
        end
        
    else
        % Modified Gram-Schmidt
        V = A;  % Working copy
        
        for k = 1:n
            % Normalize current column
            R(k, k) = norm(V(:, k));
            if R(k, k) > eps
                Q(:, k) = V(:, k) / R(k, k);
            else
                error('Columns of A are linearly dependent');
            end
            
            % Orthogonalize remaining columns against q_k
            for j = k+1:n
                R(k, j) = Q(:, k)' * V(:, j);
                V(:, j) = V(:, j) - R(k, j) * Q(:, k);
            end
        end
    end
end
```

### Python with NumPy/SciPy

```python
import numpy as np

def gram_schmidt_qr(A, mode='modified', reorthogonalize=False):
    """
    Gram-Schmidt QR factorization with optional reorthogonalization
    
    Parameters
    ----------
    A : numpy.ndarray
        Input matrix (m x n), m >= n
    mode : str
        'classical' or 'modified'
    reorthogonalize : bool
        Whether to apply double orthogonalization
        
    Returns
    -------
    Q : numpy.ndarray
        Orthogonal matrix (m x n)
    R : numpy.ndarray
        Upper triangular matrix (n x n)
    """
    m, n = A.shape
    Q = np.zeros((m, n), dtype=A.dtype)
    R = np.zeros((n, n), dtype=A.dtype)
    
    if mode == 'classical':
        for k in range(n):
            # Compute projections onto previous vectors
            for j in range(k):
                R[j, k] = np.dot(Q[:, j], A[:, k])
            
            # Compute orthogonal vector
            q = A[:, k].copy()
            for j in range(k):
                q -= R[j, k] * Q[:, j]
            
            # Optional reorthogonalization
            if reorthogonalize:
                for j in range(k):
                    r = np.dot(Q[:, j], q)
                    q -= r * Q[:, j]
                    R[j, k] += r
            
            # Normalize
            norm_q = np.linalg.norm(q)
            if norm_q < np.finfo(A.dtype).eps * m:
                raise ValueError(f"Column {k} is linearly dependent")
            
            R[k, k] = norm_q
            Q[:, k] = q / norm_q
            
    else:  # modified
        V = A.copy()
        
        for k in range(n):
            # Normalize k-th column
            norm_v = np.linalg.norm(V[:, k])
            if norm_v < np.finfo(A.dtype).eps * m:
                raise ValueError(f"Column {k} is linearly dependent")
            
            R[k, k] = norm_v
            Q[:, k] = V[:, k] / norm_v
            
            # Orthogonalize remaining columns
            for j in range(k+1, n):
                R[k, j] = np.dot(Q[:, k], V[:, j])
                V[:, j] -= R[k, j] * Q[:, k]
            
            # Optional reorthogonalization
            if reorthogonalize:
                for j in range(k+1, n):
                    r = np.dot(Q[:, k], V[:, j])
                    V[:, j] -= r * Q[:, k]
                    R[k, j] += r
    
    return Q, R
```

### Commercial Software Implementation

**MATLAB:**
- `qr(A, 0)`: Economy QR decomposition using Householder (default)
- `gs(A)`: Gram-Schmidt in some toolboxes
- Custom implementation as shown above

**LAPACK:**
- `DGEQRF`: QR factorization using Householder (standard)
- No direct Gram-Schmidt routine (considered less stable)

**NumPy/SciPy:**
- `np.linalg.qr`: Uses LAPACK (Householder)
- `scipy.linalg.qr`: Similar to NumPy
- Custom Gram-Schmidt needed for pedagogical purposes

## See Also

- [[QR Decomposition]]
- Householder Transformation]]
- Givens Rotation]]
- [[Orthogonalization]]
- [[Least Squares Method]]
- [[Linear Independence]]
- Inner Product Space]]
- [[Orthonormal Basis]]
- Singular Value Decomposition]]
- Eigenvalue Decomposition]]
- [[Matrix Factorization]]
- [[Numerical Stability]]
- Condition Number]]
- [[Projection Matrix]]
- [[Vector Space]]
- [[Basis Transformation]]
- [[Modal Analysis]]
- [[Finite Element Method]]

---

*Note: The Gram-Schmidt Process represents a fundamental algorithm in linear algebra for constructing orthonormal bases. Despite its numerical limitations compared to Householder QR, its geometric intuition and incremental nature make it invaluable for pedagogical purposes and certain applications where explicit Q is needed or vectors arrive sequentially.*
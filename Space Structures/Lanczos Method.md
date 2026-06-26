## Formal Definition

The **Lanczos Method** is an iterative algorithm for approximating eigenvalues and eigenvectors of large, sparse symmetric (or Hermitian) matrices. It constructs an orthonormal basis for the Krylov subspace, reducing the original matrix to tridiagonal form through a three-term recurrence relation. This transformation enables efficient computation of extreme eigenvalues without storing the full matrix, making it particularly valuable for problems where matrix factorization is computationally prohibitive.

## Historical Development

### Key Milestones
- **1950:** Cornelius Lanczos publishes the algorithm for eigenvalue computation
- **1970s:** Paige's analysis reveals numerical instability in finite precision
- **1980s:** Development of reorthogonalization techniques to maintain stability
- **1990s:** Implicitly Restarted Lanczos (IRL) and integration into ARPACK
- **2000s:** Block Lanczos variants and parallel implementations emerge
- **2010s:** Applications in quantum chemistry and machine learning expand
- **2020s:** GPU acceleration and tensor Lanczos for higher-order problems

### Foundational Contributors
1. **Cornelius Lanczos (1893-1974):** Developed the original algorithm
2. **Chris Paige (b. 1945):** Pioneered numerical stability analysis
3. **Beresford Parlett (1932-2020):** Advanced practical implementations
4. **Jane Cullum (1934-2020):** Developed techniques for spurious eigenvalue identification
5. **Youcef Saad (b. 1950):** Contributed to Krylov subspace methods theory

## Mathematical Formulation

### Basic Three-Term Recurrence

Given a symmetric matrix $A \in \mathbb{R}^{n \times n}$ and starting vector $\mathbf{q}_1$ with $\|\mathbf{q}_1\| = 1$:

**Initialization:** $\mathbf{q}_0 = \mathbf{0}$, $\beta_1 = 0$

**For $j = 1, 2, \ldots, m$:**
1. $\mathbf{v} = A \mathbf{q}_j$
2. $\alpha_j = \mathbf{q}_j^T \mathbf{v}$
3. $\mathbf{v} = \mathbf{v} - \alpha_j \mathbf{q}_j - \beta_j \mathbf{q}_{j-1}$
4. $\beta_{j+1} = \|\mathbf{v}\|$
5. If $\beta_{j+1} \neq 0$: $\mathbf{q}_{j+1} = \mathbf{v} / \beta_{j+1}$

### Matrix Formulation

**Lanczos decomposition:** After $m$ steps:
$$
A Q_m = Q_m T_m + \beta_{m+1} \mathbf{q}_{m+1} \mathbf{e}_m^T
$$
where:
- $Q_m = [\mathbf{q}_1, \mathbf{q}_2, \ldots, \mathbf{q}_m]$ has orthonormal columns
- $T_m$ is symmetric tridiagonal:
$$
T_m = \begin{bmatrix}
\alpha_1 & \beta_2 & & \\
\beta_2 & \alpha_2 & \ddots & \\
& \ddots & \ddots & \beta_m \\
& & \beta_m & \alpha_m
\end{bmatrix}
$$
- $\mathbf{e}_m = (0, \ldots, 0, 1)^T \in \mathbb{R}^m$

### Krylov Subspace Interpretation

The Lanczos vectors span the Krylov subspace:
$$
\mathcal{K}_m(A, \mathbf{q}_1) = \text{span}\{\mathbf{q}_1, A\mathbf{q}_1, \ldots, A^{m-1}\mathbf{q}_1\}
$$
and satisfy:
$$
Q_m^T A Q_m = T_m
$$

## Fundamental Principles

### Three-Term Recurrence Property

**Symmetry exploitation:** For symmetric matrices, [[orthogonalization]] against all previous vectors reduces to [[orthogonalization]] against only the last two vectors:
$$
\mathbf{q}_{j+1} \perp \text{span}\{\mathbf{q}_1, \ldots, \mathbf{q}_{j-1}\}
$$
automatically due to symmetry.

**Minimal recurrence:** Only $\alpha_j, \beta_j, \mathbf{q}_{j-1}, \mathbf{q}_j$ needed to compute $\mathbf{q}_{j+1}$.

### Tridiagonal Reduction

**Projection viewpoint:** $T_m$ represents $A$ restricted to the Krylov subspace:
- $T_m = Q_m^T A Q_m$
- Eigenvalues of $T_m$ (Ritz values) approximate eigenvalues of $A$
- Eigenvectors of $T_m$ give coefficients for Ritz vectors: $\mathbf{u}_i = Q_m \mathbf{y}_i$

### Optimal Approximation Property

**Rayleigh-Ritz in Krylov subspace:** Lanczos implicitly performs Rayleigh-Ritz projection:
- Ritz values $\theta_i^{(m)}$ = eigenvalues of $T_m$
- Ritz vectors $Q_m \mathbf{y}_i^{(m)}$ approximate eigenvectors of $A$
- For given $m$, these are optimal approximations in $\mathcal{K}_m(A, \mathbf{q}_1)$

## Theoretical Framework

### Convergence Theory

**Kaniel-Paige-Saad bounds:** For eigenvalues $\lambda_1 \geq \lambda_2 \geq \cdots \geq \lambda_n$:

**Extreme eigenvalues:**
$$
\lambda_1 - \theta_1^{(m)} \leq \frac{(\lambda_1 - \lambda_n) \tan^2 \theta(\mathbf{q}_1, \mathbf{v}_1)}{T_{m-1}(1 + 2\gamma_1)^2}
$$
where $T_{m-1}$ is Chebyshev polynomial, $\gamma_1 = (\lambda_1 - \lambda_2)/(\lambda_2 - \lambda_n)$.

**General eigenvalue $\lambda_i$:**
$$
\frac{\theta_i^{(m)} - \lambda_i}{\lambda_i - \lambda_n} \leq \frac{\kappa_i \tan^2 \theta(\mathbf{q}_1, \mathcal{V}_i)}{T_{m-i}(1 + 2\gamma_i)^2}
$$
where $\mathcal{V}_i = \text{span}\{\mathbf{v}_1, \ldots, \mathbf{v}_i\}$, $\gamma_i = (\lambda_i - \lambda_{i+1})/(\lambda_{i+1} - \lambda_n)$, $\kappa_i = \prod_{j=1}^{i-1} \frac{\lambda_j - \lambda_n}{\lambda_j - \lambda_i}$.

### Finite Precision Effects

**Loss of orthogonality:** In floating-point arithmetic, Lanczos vectors lose orthogonality:
- Initially slow, then accelerates as Ritz values converge
- Leads to "ghost" or spurious eigenvalues
- Explained by Paige's theory

**Semiorthogonality:** Vectors remain semiorthogonal: $|\mathbf{q}_i^T \mathbf{q}_j| \leq \sqrt{\epsilon}$ until corresponding Ritz value converges.

### Connection to Moment Matching

**Moments of spectral distribution:** Lanczos approximates moments:
$$
\mathbf{q}_1^T A^k \mathbf{q}_1 = \mathbf{e}_1^T T_m^k \mathbf{e}_1, \quad k = 0, 1, \ldots, 2m-1
$$

**Gaussian quadrature:** Eigenvalues of $T_m$ are nodes of Gaussian quadrature rule for Riemann-Stieltjes integral with measure defined by $A$ and $\mathbf{q}_1$.

## Classification and Variants

### By Orthogonalization Strategy
1. **Basic Lanczos:** No reorthogonalization (unstable but memory-efficient)
2. **Full reorthogonalization:** Orthogonalize against all previous vectors
3. **Selective reorthogonalization:** Orthogonalize only against converged Ritz vectors
4. **Partial reorthogonalization:** Periodic reorthogonalization when needed

### By Problem Type
1. **Standard symmetric Lanczos:** For $A\mathbf{x} = \lambda\mathbf{x}$, $A = A^T$
2. **Hermitian Lanczos:** For complex Hermitian matrices
3. **Generalized Lanczos:** For $A\mathbf{x} = \lambda B\mathbf{x}$, with $A, B$ symmetric, $B$ positive definite
4. **Shift-and-invert Lanczos:** For interior eigenvalues using $(A - \sigma I)^{-1}$

### By Implementation Approach
1. **Simple Lanczos:** Basic three-term recurrence
2. **Block Lanczos:** Multiple starting vectors for multiple/multiple eigenvalues
3. **Implicitly Restarted Lanczos (IRL):** Implicit shifting to focus on desired part of spectrum
4. **Rational Lanczos:** For rational eigenvalue problems

### Special Purpose Variants
1. **Lanczos bidiagonalization:** For SVD computation (Lanczos for $A^TA$)
2. **Nonsymmetric Lanczos:** For nonsymmetric matrices (two three-term recurrences)
3. **Look-ahead Lanczos:** Handles breakdown in nonsymmetric case
4. **Communication-avoiding Lanczos:** Reduces synchronization in parallel computing

## Derivation and Proof

### Derivation from [[Arnoldi Method]]

**Arnoldi process:** For general matrix, constructs Hessenberg matrix:
$$
A Q_m = Q_m H_m + h_{m+1,m} \mathbf{q}_{m+1} \mathbf{e}_m^T
$$

**Symmetry simplification:** When $A$ symmetric, $H_m$ symmetric ⇒ tridiagonal:
- $H_m = T_m$
- Only three diagonals nonzero due to symmetry

**Three-term recurrence proof:** From Arnoldi:
$$
h_{j,k} = \mathbf{q}_j^T A \mathbf{q}_k
$$
By symmetry: $h_{j,k} = h_{k,j}$
If $\mathbf{q}_j \perp \mathcal{K}_{j-1}(A, \mathbf{q}_1)$, then for $k < j-1$:
$$
h_{j,k} = \mathbf{q}_j^T (A \mathbf{q}_k) = \mathbf{q}_j^T (\text{linear combination of } \mathbf{q}_1, \ldots, \mathbf{q}_{k+1}) = 0
$$
Thus $h_{j,k} = 0$ for $k < j-1$, making $H_m$ tridiagonal.

### Optimality Proof

**Krylov subspace property:** $\mathcal{K}_m(A, \mathbf{q}_1) = \text{range}(Q_m)$

**Rayleigh-Ritz:** For any vector $\mathbf{y} \in \mathbb{R}^m$, $Q_m \mathbf{y} \in \mathcal{K}_m(A, \mathbf{q}_1)$

**Rayleigh quotient:** $\rho(\mathbf{y}) = \frac{\mathbf{y}^T T_m \mathbf{y}}{\mathbf{y}^T \mathbf{y}}$

**Minimax theorem:** Ritz values $\theta_i^{(m)}$ satisfy:
$$
\theta_i^{(m)} = \min_{\dim(S)=i} \max_{\mathbf{0} \neq \mathbf{y} \in S} \rho(\mathbf{y})
$$
where $S \subseteq \mathbb{R}^m$. This matches Rayleigh-Ritz optimality.

### Convergence Proof Sketch

**Key idea:** Chebyshev polynomials minimize maximum deviation on interval.

**Construct polynomial:** Let $p_{m-1}(t)$ be polynomial of degree $m-1$ with $p_{m-1}(\lambda_1) = 1$ that minimizes max norm on $[\lambda_n, \lambda_2]$.

**Error bound:** Using Chebyshev polynomials:
$$
\lambda_1 - \theta_1^{(m)} \leq (\lambda_1 - \lambda_n) \left[ \frac{1}{T_{m-1}(1 + 2\gamma_1)} \right]^2 \tan^2 \theta(\mathbf{q}_1, \mathbf{v}_1)
$$
where $\gamma_1 = (\lambda_1 - \lambda_2)/(\lambda_2 - \lambda_n)$.

## Physical Interpretation

### Vibrating String Analogy

**Tridiagonal matrix $T_m$:** Represents discretized vibrating string:
- $\alpha_i$: Mass at point $i$
- $\beta_i$: Spring constant between points $i-1$ and $i$
- Eigenvalues: Natural frequencies of string
- Eigenvectors: Mode shapes

**Lanczos process:** Successively adds masses and springs to string model.

### Energy Propagation

**Starting vector $\mathbf{q}_1$:** Initial excitation pattern
**Matrix multiplication $A\mathbf{q}_j$:** Propagates excitation through system
**Orthogonalization:** Removes components already captured in model

**Wave propagation analogy:** Like sending pulse through medium and observing reflections.

### Filter Diagonalization

**Spectral filtering:** Lanczos acts as adaptive filter bank:
- Each iteration adds resolution to spectral estimate
- Converges first to eigenvalues where $\mathbf{q}_1$ has large component
- Similar to Prony's method for exponential fitting

## Applications

### Engineering Disciplines
1. **[[Structural Dynamics]]:** Vibration mode extraction for large structures
2. **Mechanical Engineering:** Rotor dynamics, critical speed analysis
3. **Electrical Engineering:** Power system stability, network analysis
4. **Aerospace Engineering:** Flutter analysis, aircraft mode computation
5. **Civil Engineering:** Seismic analysis, building modal properties

### Scientific Fields
1. **Quantum Chemistry:** Electronic structure calculations (Hartree-Fock, DFT)
2. **Computational Physics:** Many-body problems, quantum field theory
3. **Materials Science:** Phonon spectra, electronic band structure
4. **Statistics:** Principal component analysis for large datasets
5. **[[Machine Learning]]:** Kernel methods, spectral clustering

### Practical Implementations
- **[[Finite Element Analysis (FEA)]]:** Eigenvalue extraction in NASTRAN, ANSYS, ABAQUS
- **Control systems:** Model reduction via balanced truncation
- **[[Signal processing]]:** Spectral estimation, frequency analysis
- **Quantum computing:** Ground state energy estimation
- **Data science:** Dimensionality reduction, manifold learning

## Implementation Considerations

### Basic Algorithm Implementation

**Simple Lanczos (no reorthogonalization):**
```
function lanczos(A, q1, m):
    n = size(A, 1)
    Q = zeros(n, m)          # Optional: store for reorthogonalization
    alpha = zeros(m)
    beta = zeros(m+1)
    
    q_prev = zeros(n)
    q = q1 / norm(q1)
    beta[1] = 0
    
    for j = 1 to m:
        # Matrix-vector multiplication
        v = A * q
        
        # Compute alpha[j]
        alpha[j] = dot(q, v)
        
        # Three-term recurrence
        v = v - alpha[j] * q - beta[j] * q_prev
        
        # Compute beta[j+1]
        beta[j+1] = norm(v)
        
        # Store q (if storing)
        if storing_Q:
            Q[:, j] = q
        
        # Check for breakdown
        if beta[j+1] == 0:
            break
        
        # Update for next iteration
        q_prev = q
        q = v / beta[j+1]
    
    # Construct tridiagonal matrix T
    T = diag(alpha) + diag(beta[2:m], 1) + diag(beta[2:m], -1)
    
    return T, Q (if stored)
```

### Reorthogonalization Strategies

**Full reorthogonalization (expensive but stable):**
```
# After computing v in basic algorithm:
for i = 1 to j:
    r = dot(Q[:, i], v)
    v = v - r * Q[:, i]
beta[j+1] = norm(v)
```

**Selective reorthogonalization (Paige's criterion):**
- Maintain semiorthogonality: $|\mathbf{q}_i^T \mathbf{q}_j| \leq \sqrt{\epsilon}$
- Reorthogonalize against \(\mathbf{q}_i\) when bound violated
- Typically needed only for converged Ritz vectors

**Partial reorthogonalization:**
- Periodically orthogonalize against all previous vectors
- Example: every 10-20 iterations

### Implicit Restarting

**Motivation:** Control subspace dimension while focusing on desired eigenvalues.

**IRL Algorithm (Implicitly Restarted Lanczos):**
1. Run Lanczos for $m+p$ steps ($m$ desired, $p$ extra)
2. Compute eigenvalues of $T_{m+p}$
3. Select $p$ shifts $\mu_1, \ldots, \mu_p$ (unwanted eigenvalues)
4. Apply $p$ steps of implicit QR with shifts $\mu_i$
5. Truncate to first $m$ columns, obtain new starting vector
6. Repeat until convergence

**Mathematical basis:** Equivalent to applying polynomial filter $\prod_{i=1}^p (T - \mu_i I)$ to starting vector.

### Parallel Implementation

**Matrix-vector multiplication:** Can be parallelized if $A$ distributed
- Row-wise distribution: each processor owns subset of rows
- Requires communication for dot products

**Block Lanczos:** Process multiple vectors simultaneously:
- Better cache utilization
- Higher computational intensity
- Can compute multiple eigenvalues in single iteration

**Communication-avoiding Lanczos:** Uses $s$-step approach:
- Perform $s$ iterations with one synchronization
- Increases computational work but reduces communication

## Advantages and Limitations

### Strengths
1. **Memory efficiency:** Only stores few vectors (if no reorthogonalization)
2. **Computational efficiency:** Only matrix-vector multiplications needed
3. **Fast convergence:** For extreme eigenvalues, often superlinear
4. **No factorization required:** Avoids $O(n^3)$ complexity of direct methods
5. **Adaptive:** Can be restarted to focus on specific eigenvalues

### Weaknesses
1. **Loss of orthogonality:** Basic algorithm numerically unstable
2. **Spurious eigenvalues:** Ghost eigenvalues appear due to finite precision
3. **Starting vector dependence:** May miss eigenvalues if starting vector has zero component
4. **Breakdown:** Can occur if $\beta_{j+1} = 0$ (rare in practice)
5. **Slow for interior eigenvalues:** Without shift-and-invert acceleration

### Validity Range
- **Optimal for:** Large sparse symmetric matrices, extreme eigenvalues
- **Effective with:** Shift-and-invert for interior eigenvalues
- **Not recommended for:** Dense matrices (QR algorithm better)
- **Requires care for:** Clustered eigenvalues, high multiplicity

## Advanced Topics

### Lanczos Bidiagonalization for SVD

**For SVD of $A \in \mathbb{R}^{m \times n}$:** Apply Lanczos to $A^TA$ or $AA^T$:
- Computes singular values/vectors without forming $A^TA$
- Uses two three-term recurrences:
  - $AV_k = U_{k+1} B_k$
  - $A^T U_{k+1} = V_k B_k^T + \alpha_{k+1} \mathbf{v}_{k+1} \mathbf{e}_{k+1}^T$
where $B_k$ is bidiagonal.

**Application:** Latent semantic analysis, image [[compression]].

### Connection to Conjugate Gradient

**CG for $A\mathbf{x} = \mathbf{b}$:** Equivalent to Lanczos for $A$ with starting vector $\mathbf{r}_0/\|\mathbf{r}_0\|$:
- CG residuals $\mathbf{r}_k$ are Lanczos vectors up to scaling
- CG iterates minimize error in $A$-norm over Krylov subspace
- Lanczos tridiagonal matrix appears in CG three-term recurrence

**Implication:** Eigenvalue information available from CG iteration history.

### Nonlinear Eigenvalue Problems

**Polynomial eigenvalue problems:** $P(\lambda)\mathbf{x} = \mathbf{0}$ with $P(\lambda) = \sum_{i=0}^d \lambda^i A_i$
**Linearization:** Convert to larger linear problem, apply Lanczos
**Rational Lanczos:** For rational functions of $A$

### Tensor Lanczos

**For higher-order tensors:** Generalize Lanczos to tensor decompositions
**Applications:** Psychometrics, chemometrics, data mining
**Challenge:** Loss of orthogonality more severe

## Special Cases and Examples

### Tridiagonal Matrix Example

**Matrix:**
$$
A = \text{tridiag}(-1, 2, -1) \in \mathbb{R}^{1000 \times 1000}
$$
Eigenvalues: $\lambda_k = 2 - 2\cos(\frac{k\pi}{n+1})$, $k=1,\ldots,n$

**Lanczos behavior:**
- Starting vector: random unit vector
- First Ritz value converges to $\lambda_1$ in ~10 iterations
- After 50 iterations, 10 extreme eigenvalues accurate to $10^{-8}$
- Ghost eigenvalues appear after ~70 iterations without reorthogonalization

### Clustered Eigenvalues Example

**Matrix:** Diagonal with values 1.0, 1.001, 1.002, ..., 2.0
**Challenge:** Small gaps between eigenvalues slow convergence
**Solution:** Use shift-and-invert with shift near cluster

### Breakdown Example

**Matrix with invariant subspace:** If $\mathbf{q}_1$ lies in invariant subspace of dimension $k$, Lanczos terminates at step $k$ ($\beta_{k+1} = 0$)
**Example:** $A = \text{diag}(1,1,2,3,\ldots)$, $\mathbf{q}_1 = (1,1,0,\ldots)/\sqrt{2}$
**Result:** Lanczos produces 2×2 tridiagonal matrix, captures only eigenvalue 1

### Industrial Scale Problem

**Automotive chassis [[vibration analysis]]:**
- Matrix: 2,000,000 DOFs, bandwidth ~1000
- Desired: First 50 modes (0-200 Hz)
- Method: Block Lanczos with shift-and-invert
- Computation: 4 hours on 32 cores
- Memory: 200 MB for Lanczos vectors vs 16 TB for full matrix

## Error Analysis

### Finite Precision Analysis

**Paige's results:** In floating-point arithmetic, computed quantities satisfy:
$$
A \tilde{Q}_m = \tilde{Q}_m \tilde{T}_m + \beta_{m+1} \tilde{\mathbf{q}}_{m+1} \mathbf{e}_m^T + F_m
$$
where $\|F_m\| \leq \epsilon \|A\|$, $\epsilon$ machine epsilon.

**Loss of orthogonality bound:**
$$
\|I - \tilde{Q}_m^T \tilde{Q}_m\| \leq c(m, n) \epsilon \kappa(V_m) \|A\|
$$

**Semiorthogonality:** Lanczos vectors remain semiorthogonal until corresponding Ritz value converges:
$$
|\tilde{\mathbf{q}}_i^T \tilde{\mathbf{q}}_j| \leq \sqrt{\epsilon} \quad \text{until } \theta_i^{(m)} \text{ converges}
$$

### Spurious Eigenvalues

**Identification methods:**
1. **Cullum-Willoughby test:** Compare eigenvalues of $T_m$ with those of $T_m^{(1)}$ (T with first row/column removed)
2. **Residual test:** Compute $\|A\mathbf{u}_i - \theta_i \mathbf{u}_i\|$ for all Ritz pairs
3. **Orthogonality test:** Check $|\mathbf{u}_i^T \mathbf{u}_j|$ for $i \neq j$

**Ghost eigenvalues:** Appear as extra copies of true eigenvalues, caused by loss of orthogonality.

### A Posteriori Error Bounds

**For Ritz pair $(\theta, \mathbf{u})$:**
$$
\min_{\lambda \in \Lambda(A)} |\lambda - \theta| \leq \frac{\|A\mathbf{u} - \theta\mathbf{u}\|}{\|\mathbf{u}\|}
$$

**Componentwise bound:** For eigenvector approximation:
$$
|\mathbf{v}_k^T \mathbf{u}| \leq \frac{\|A\mathbf{u} - \theta\mathbf{u}\|}{\text{gap}_k}
$$
where $\text{gap}_k = \min_{i \neq k} |\lambda_i - \theta|$

### Convergence Monitoring

**Residual norms:** For Ritz pair $(\theta_i^{(m)}, \mathbf{u}_i^{(m)} = Q_m \mathbf{y}_i^{(m)})$:
$$
\|A\mathbf{u}_i^{(m)} - \theta_i^{(m)} \mathbf{u}_i^{(m)}\| = |\beta_{m+1} \mathbf{e}_m^T \mathbf{y}_i^{(m)}|
$$

**Convergence criterion:** Stop when $|\beta_{m+1} \mathbf{e}_m^T \mathbf{y}_i^{(m)}| < \tau \|A\|$ for desired eigenvalues.

## Relationship to Other Concepts

### Comparison with [[Arnoldi Method]]

**Arnoldi:** For general matrices, produces Hessenberg matrix
**Lanczos:** Special case for symmetric matrices, produces tridiagonal matrix
**Relationship:** Lanczos = Arnoldi with symmetry ⇒ three-term recurrence

### Comparison with Subspace Iteration

**Subspace iteration:** Fixed subspace, linear convergence
**Lanczos:** Adaptive Krylov subspace, often superlinear convergence
**Hybrid:** Subspace iteration with Ritz acceleration similar to Lanczos

### Connection to Jacobi-Davidson Method

**Jacobi-Davidson:** Correction equation to improve eigenvector approximation
**Lanczos:** Builds Krylov subspace, extracts approximations via Rayleigh-Ritz
**Comparison:** Jacobi-Davidson often better for interior eigenvalues

### Relationship to QR Algorithm

**QR algorithm:** For dense matrices, computes all eigenvalues
**Lanczos:** For sparse matrices, computes subset via projection
**Connection:** Implicit restarting in Lanczos uses QR algorithm on small tridiagonal matrix

### Integration with Preconditioning

**Preconditioned Lanczos:** For generalized eigenvalue problems
**Example:** For $A\mathbf{x} = \lambda B\mathbf{x}$, use preconditioner $M \approx B^{-1}$
**Challenge:** Maintain symmetry with preconditioning

## Historical Context and Evolution

### Original Motivation

**Lanczos's 1950 paper:** "An iteration method for the solution of the eigenvalue problem of linear differential and integral operators"
**Goal:** Efficient method for practical large-scale problems in physics
**Context:** Early digital computers, need for algorithms avoiding full storage

### Evolution Over Time

1. **1950-1970:** Initial use, recognition of numerical issues
2. **1970-1980:** Paige's analysis, understanding of finite precision behavior
3. **1980-1990:** Reorthogonalization techniques, implicitly restarted variants
4. **1990-2000:** ARPACK software, widespread adoption in engineering
5. **2000-2010:** Parallel implementations, block variants, quantum chemistry applications
6. **2010-present:** GPU acceleration, tensor extensions, machine learning applications

### Modern Reformulations

- **Randomized Lanczos:** With theoretical guarantees for approximation
- **Streaming Lanczos:** For data streams and online eigenvalue estimation
- **Federated Lanczos:** For distributed data with privacy constraints
- **Quantum Lanczos:** For quantum computers (variational quantum eigensolver)

## Pedagogical Approach

### Teaching Strategies

1. **From [[Power Method]] to Lanczos:** Show as generalization to multiple vectors
2. **Geometric interpretation:** Orthogonal projection in Krylov subspace
3. **Numerical experiments:** Demonstrate loss of orthogonality and remedies
4. **Physical analogies:** Vibrating string, wave propagation
5. **Implementation project:** Code simple Lanczos, compare with library routines

### Common Misconceptions

1. **"Lanczos always loses orthogonality":** Can be controlled with reorthogonalization
2. **"Lanczos computes eigenvalues directly":** Computes Ritz values that approximate eigenvalues
3. **"More iterations always improve accuracy":** Eventually spurious eigenvalues appear
4. **"Lanczos only works for extreme eigenvalues":** Shift-and-invert enables interior eigenvalues
5. **"Lanczos is obsolete":** Still widely used, basis for many modern eigensolvers

### Learning Resources

**Foundational Texts:**
- Parlett, "The Symmetric Eigenvalue Problem"
- Saad, "Numerical Methods for Large Eigenvalue Problems"
- Golub & Van Loan, "Matrix Computations" (Chapter 9)
- Cullum & Willoughby, "Lanczos Algorithms for Large Symmetric Eigenvalue Computations"

**Online Resources:**
- ARPACK User's Guide (netlib.org)
- SLEPc Documentation (slepc.upv.es)
- Wikipedia: "Lanczos algorithm" with detailed examples
- YouTube: Visualizations of Lanczos convergence

**Software Tutorials:**
- MATLAB: `eigs` function tutorial
- Python: `scipy.sparse.linalg.eigsh` examples
- Julia: `Arpack.jl` and `KrylovKit.jl` tutorials
- PETSc/SLEPc: Parallel eigenvalue solver tutorials

## Implementation in Software

### MATLAB Implementation

```matlab
function [T, Q, lambda, V] = lanczos_full(A, q1, m, reorth)
% Lanczos algorithm with optional reorthogonalization
% A: symmetric matrix (n x n)
% q1: starting vector (n x 1)
% m: number of Lanczos steps
% reorth: 0=none, 1=full, 2=selective
% Returns: T (tridiagonal), Q (basis), lambda (Ritz values), V (Ritz vectors)

n = size(A, 1);
Q = zeros(n, m);
alpha = zeros(m, 1);
beta = zeros(m+1, 1);

% Normalize starting vector
q = q1 / norm(q1);
q_prev = zeros(n, 1);
beta(1) = 0;

for j = 1:m
    % Store current vector
    Q(:, j) = q;
    
    % Matrix-vector multiplication
    v = A * q;
    
    % Compute alpha[j]
    alpha(j) = q' * v;
    
    % Three-term recurrence
    v = v - alpha(j) * q - beta(j) * q_prev;
    
    % Reorthogonalization
    if reorth == 1  % Full
        for i = 1:j
            r = Q(:, i)' * v;
            v = v - r * Q(:, i);
        end
    elseif reorth == 2  % Selective (simplified)
        % Check orthogonality against converged vectors
        % (In practice, need to track which Ritz values converged)
        if j > 10
            for i = max(1, j-10):j
                if abs(Q(:, i)' * v) > sqrt(eps)
                    r = Q(:, i)' * v;
                    v = v - r * Q(:, i);
                end
            end
        end
    end
    
    % Compute beta[j+1]
    beta(j+1) = norm(v);
    
    % Check for breakdown
    if beta(j+1) < eps * norm(A, 'fro')
        fprintf('Lanczos breakdown at iteration %d\n', j);
        m = j;  % Actual number of iterations
        Q = Q(:, 1:m);
        alpha = alpha(1:m);
        beta = beta(1:m+1);
        break;
    end
    
    % Update for next iteration
    q_prev = q;
    q = v / beta(j+1);
end

% Construct tridiagonal matrix
T = diag(alpha) + diag(beta(2:m), 1) + diag(beta(2:m), -1);

% Compute Ritz values and vectors
if nargout > 2
    [Y, Theta] = eig(T);
    lambda = diag(Theta);
    % Sort eigenvalues (largest first)
    [lambda, idx] = sort(lambda, 'descend');
    Y = Y(:, idx);
    % Ritz vectors
    V = Q * Y;
end

end

% Implicitly Restarted Lanczos (simplified)
function [lambda, V, iters] = irlanczos(A, nev, m, maxit, tol)
% nev: number of eigenvalues wanted
% m: Lanczos basis size (typically 2*nev to 4*nev)

n = size(A, 1);
p = m - nev;  % Number of shifts

% Initial Lanczos decomposition
q1 = randn(n, 1);
q1 = q1 / norm(q1);
[T, Q] = lanczos_full(A, q1, m, 1);  % With full reorthogonalization

for iter = 1:maxit
    % Compute eigenvalues of T
    [Y, Theta] = eig(T);
    theta = diag(Theta);
    
    % Sort, keep nev largest
    [theta, idx] = sort(theta, 'descend');
    Y = Y(:, idx);
    
    % Check convergence for first nev Ritz pairs
    converged = false(nev, 1);
    for i = 1:nev
        u = Q * Y(:, i);
        r = A * u - theta(i) * u;
        if norm(r) < tol * norm(A, 'fro')
            converged(i) = true;
        end
    end
    
    if all(converged)
        lambda = theta(1:nev);
        V = Q * Y(:, 1:nev);
        iters = iter;
        return;
    end
    
    % Apply implicit restart
    % Select shifts (unwanted eigenvalues)
    shifts = theta(nev+1:end);
    
    % Apply p steps of implicit QR with shifts
    [Qk, T] = implicit_qr_shifts(T, shifts);
    
    % Update Lanczos basis
    Q = Q * Qk;
    
    % Extend Lanczos factorization
    % (In practice, continue Lanczos from step m-p+1)
    q = Q(:, m-p+1);  % Last vector after truncation
    [T_add, Q_add] = lanczos_full(A, q, p, 1);
    
    % Merge (details omitted for brevity)
    % ...
end

warning('IRLanczos did not converge in %d iterations', maxit);
lambda = theta(1:nev);
V = Q * Y(:, 1:nev);
iters = maxit;

end
```

### Python Implementation

```python
import numpy as np
from scipy.sparse.linalg import eigsh
import scipy.sparse as sp

def lanczos(A, v0, m, reorth=False):
    """
    Basic Lanczos algorithm for symmetric matrix A
    
    Parameters
    ----------
    A : array or sparse matrix
        Symmetric matrix (n x n)
    v0 : array
        Starting vector (n,)
    m : int
        Number of Lanczos steps
    reorth : bool or str
        Reorthogonalization: False, 'full', or 'selective'
    
    Returns
    -------
    T : array (m x m)
        Tridiagonal matrix
    Q : array (n x m) or None
        Lanczos vectors (if stored)
    """
    n = v0.shape[0]
    
    # Initialize
    Q = np.zeros((n, m)) if reorth else None
    alpha = np.zeros(m)
    beta = np.zeros(m+1)
    
    # Normalize starting vector
    q_prev = np.zeros(n)
    q = v0 / np.linalg.norm(v0)
    beta[0] = 0.0
    
    # Matrix-vector product function
    if sp.issparse(A):
        matvec = A.dot
    else:
        matvec = lambda x: A @ x
    
    for j in range(m):
        # Store vector if needed
        if Q is not None:
            Q[:, j] = q
        
        # Matrix-vector multiplication
        v = matvec(q)
        
        # Compute alpha[j]
        alpha[j] = np.dot(q, v)
        
        # Three-term recurrence
        v = v - alpha[j] * q - beta[j] * q_prev
        
        # Reorthogonalization
        if reorth == 'full' and Q is not None:
            for i in range(j):
                r = np.dot(Q[:, i], v)
                v = v - r * Q[:, i]
        elif reorth == 'selective' and Q is not None and j > 0:
            # Simplified selective reorthogonalization
            # In practice, need more sophisticated criterion
            for i in range(max(0, j-10), j):
                dot_prod = np.dot(Q[:, i], v)
                if abs(dot_prod) > np.sqrt(np.finfo(float).eps):
                    v = v - dot_prod * Q[:, i]
        
        # Compute beta[j+1]
        beta[j+1] = np.linalg.norm(v)
        
        # Check for breakdown
        if beta[j+1] < np.finfo(float).eps * np.linalg.norm(A, 'fro'):
            print(f'Lanczos breakdown at iteration {j+1}')
            m = j + 1
            if Q is not None:
                Q = Q[:, :m]
            alpha = alpha[:m]
            beta = beta[:m+1]
            break
        
        # Update for next iteration
        q_prev = q
        if beta[j+1] > 0:
            q = v / beta[j+1]
        else:
            # Breakdown, generate random vector orthogonal to previous
            q = np.random.randn(n)
            if Q is not None:
                for i in range(j+1):
                    q = q - np.dot(Q[:, i], q) * Q[:, i]
            q = q / np.linalg.norm(q)
    
    # Construct tridiagonal matrix
    T = np.diag(alpha[:m]) + np.diag(beta[2:m], 1) + np.diag(beta[2:m], -1)
    
    return T, Q

def lanczos_eigsh(A, k, which='LA', m=20, maxiter=100, tol=1e-8):
    """
    Lanczos for computing k eigenvalues using SciPy's interface
    which: 'LA' (largest algebraic), 'SA' (smallest algebraic), etc.
    """
    # Use SciPy's implementation (which uses ARPACK)
    return eigsh(A, k=k, which=which, ncv=m, maxiter=maxiter, tol=tol)

# Example: SVD via Lanczos bidiagonalization
def lanczos_bidiag(A, k):
    """
    Lanczos bidiagonalization for SVD
    Returns top k singular values/vectors
    """
    m, n = A.shape
    if sp.issparse(A):
        A = A.tocsr()
        At = A.T.tocsr()
        matvec_u = lambda x: A.dot(x)
        matvec_v = lambda x: At.dot(x)
    else:
        matvec_u = lambda x: A @ x
        matvec_v = lambda x: A.T @ x
    
    # Initialize
    u = np.random.randn(m)
    u = u / np.linalg.norm(u)
    v = np.zeros(n)
    beta = np.zeros(k+1)
    alpha = np.zeros(k)
    
    U = np.zeros((m, k))
    V = np.zeros((n, k))
    
    beta[0] = 0
    v_prev = np.zeros(n)
    
    for j in range(k):
        # Bidiagonalization step
        v = matvec_v(u) - beta[j] * v_prev
        alpha[j] = np.linalg.norm(v)
        if alpha[j] > 0:
            v = v / alpha[j]
        
        U[:, j] = u
        V[:, j] = v
        
        u = matvec_u(v) - alpha[j] * u
        
        # Reorthogonalize (optional)
        for i in range(j):
            u = u - np.dot(U[:, i], u) * U[:, i]
        
        beta[j+1] = np.linalg.norm(u)
        if beta[j+1] > 0:
            u = u / beta[j+1]
        
        v_prev = v
    
    # Construct bidiagonal matrix
    B = np.diag(alpha) + np.diag(beta[1:k], -1)
    
    # Compute SVD of B
    Ub, S, Vb = np.linalg.svd(B, full_matrices=False)
    
    # Compute singular vectors of A
    U_final = U @ Ub
    V_final = V @ Vb.T
    
    return S[:k], U_final[:, :k], V_final[:, :k]
```

### Commercial Software Features

**ANSYS Mechanical:**
- Block Lanczos eigensolver for large [[Modal Analysis]]
- Automatic shift selection for frequency ranges
- GPU acceleration option
- Distributed memory parallelization

**NASTRAN:**
- SOL 103: Normal modes with Lanczos method
- SOL 107: Complex eigenvalues using complex Lanczos
- Automated estimation of optimal subspace size
- DMAP alter for custom Lanczos parameters

**ABAQUS:**
- Lanczos eigensolver for symmetric eigenvalue problems
- Subspace iteration as alternative
- Frequency extraction and buckling analysis

**MATLAB:**
- `eigs` function: Uses ARPACK (Implicitly Restarted Lanczos/Arnoldi)
- Support for function handles (matrix-free)
- Various convergence controls and options

## See Also

- [[Arnoldi Method]]
- [[Krylov Subspace Method]]
- [[Ritz Method (Rayleigh-Ritz Method)]]
- [[Power Method]]
- [[Inverse Power Method]]
- [[QR Algorithm]]
- [[Implicitly Restarted Arnoldi]]
- [[Jacobi-Davidson Method]]
- [[Tridiagonal Matrix]]
- [[Sparse Matrix]]
- [[Eigenvalue Problem]]
- [[Singular Value Decomposition]]
- [[Conjugate Gradient Method]]
- [[Modal Analysis]]
- [[Finite Element Analysis (FEA)]]
- [[Numerical Linear Algebra]]

---

*Note: The Lanczos Method remains a cornerstone algorithm for large-scale eigenvalue problems, particularly in engineering applications like [[Structural Dynamics]]. Its combination of efficiency, adaptability through restarting, and strong theoretical foundations ensure its continued relevance despite the challenge of numerical stability in finite precision arithmetic.*
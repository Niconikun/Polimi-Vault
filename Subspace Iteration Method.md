## Formal Definition

The **Subspace Iteration Method** (also known as **Simultaneous Iteration**) is an iterative numerical algorithm that extends the [[Power Method]] to compute multiple eigenvalues and eigenvectors simultaneously. This method iteratively refines a subspace of vectors, converging to the invariant subspace corresponding to the desired eigenvalues. Particularly effective for large, sparse matrices, subspace iteration provides a robust approach for extracting several extreme eigenvalues and their associated eigenvectors without requiring complete matrix diagonalization.

## Historical Development

### Key Milestones
- **1950s:** Early developments in simultaneous iteration for eigenvalue problems
- **1960s:** K. J. Bathe formalizes the method for [[Structural Dynamics]] applications
- **1970s:** Integration with Sturm sequence checks for eigenvalue counts
- **1980s:** Convergence analysis and optimization for finite element applications
- **1990s:** Implementation in commercial finite element software packages
- **2000s:** Extension to nonlinear and generalized eigenvalue problems
- **2010s:** Parallel implementations for high-performance computing

### Foundational Contributors
1. **K. J. Bathe (b. 1943):** Popularized subspace iteration for [[Structural Dynamics]]
2. **B. N. Parlett (1932-2020):** Advanced convergence analysis of subspace methods
3. **H. Rutishauser (1918-1970):** Early work on simultaneous iteration techniques
4. **G. H. Golub (1932-2007):** Contributions to numerical methods for eigenvalue problems

## Mathematical Formulation

### Basic Algorithm

Given an \( n \times n \) matrix \( A \) and an initial \( n \times p \) matrix \( V^{(0)} \) with orthonormal columns (\( p > m \), where \( m \) is the number of desired eigenvalues):

**Iteration steps:**
1. **Matrix multiplication:** \( W^{(k)} = A V^{(k-1)} \)
2. **[[Orthogonalization]]:** \( V^{(k)} R^{(k)} = W^{(k)} \) (QR decomposition)
3. **Rayleigh-Ritz projection:** Form \( H^{(k)} = (V^{(k)})^T A V^{(k)} \)
4. **Solve reduced problem:** \( H^{(k)} Q^{(k)} = Q^{(k)} \Theta^{(k)} \)
5. **Subspace update:** \( V^{(k)} = V^{(k)} Q^{(k)} \)

### Matrix Formulation

**Simultaneous power iteration:** For \( p \) vectors simultaneously:
$$
V^{(k)} = \text{orthonormalize}(A^k V^{(0)})
$$

**Rayleigh-Ritz procedure:** At iteration \( k \), approximate eigenpairs \( (\theta_i^{(k)}, \mathbf{q}_i^{(k)}) \) satisfy:
$$
H^{(k)} \mathbf{q}_i^{(k)} = \theta_i^{(k)} \mathbf{q}_i^{(k)}, \quad H^{(k)} = (V^{(k)})^T A V^{(k)}
$$

**Approximate eigenvectors:** \( \mathbf{u}_i^{(k)} = V^{(k)} \mathbf{q}_i^{(k)} \)

### Convergence Rates

**For eigenvalues:** 
$$
|\lambda_i - \theta_i^{(k)}| = O\left( \left| \frac{\lambda_{p+1}}{\lambda_i} \right|^{2k} \right)
$$

**For eigenvectors:**
$$
\sin \angle(\mathbf{u}_i^{(k)}, \mathbf{v}_i) = O\left( \left| \frac{\lambda_{p+1}}{\lambda_i} \right|^k \right)
$$

where \( \lambda_1 \geq \lambda_2 \geq \cdots \geq \lambda_n \) and \( p \geq m \).

## Fundamental Principles

### Simultaneous Power Iteration

**Key idea:** Apply [[Power Method]] to multiple vectors simultaneously:
- Each vector converges to dominant eigenvector
- Orthogonalization prevents all vectors converging to same direction
- Maintains linear independence throughout iterations

### Rayleigh-Ritz Projection

**Projection technique:** Restrict [[Eigenvalue Problem]] to current subspace:
- Construct \( H = V^T A V \) (Rayleigh quotient matrix)
- Solve small dense [[Eigenvalue Problem]]: \( H Q = Q \Theta \)
- Extract approximate eigenpairs: \( (\theta_i, V\mathbf{q}_i) \)

**Optimal approximation:** For given subspace, Rayleigh-Ritz provides best approximations to eigenvectors.

### Subspace Tracking

**Dynamic dimension:** Number of vectors \( p \) typically larger than desired eigenvalues \( m \):
- **Oversampling:** \( p = \min(2m, m+8) \) often recommended
- **Convergence monitoring:** Track multiple eigenpairs simultaneously
- **Locking converged vectors:** Stop iterating converged eigenvectors

## Theoretical Framework

### Convergence Analysis

**Theorem:** If \( \lambda_1 \geq \lambda_2 \geq \cdots \geq \lambda_n > 0 \) and \( V^{(0)} \) has full rank projection onto span of first \( p \) eigenvectors, then subspace iteration converges.

**Convergence factors:** For \( i = 1, \ldots, m \):
$$
\tan \angle(\mathcal{R}(V^{(k)}), \mathcal{V}_i) \leq \left( \frac{\lambda_{p+1}}{\lambda_i} \right)^k \tan \angle(\mathcal{R}(V^{(0)}), \mathcal{V}_i)
$$

where \( \mathcal{V}_i = \text{span}\{\mathbf{v}_1, \ldots, \mathbf{v}_i\} \).

### Orthogonalization Importance

**Loss of orthogonality:** Without orthogonalization, all vectors converge to dominant eigenvector.

**Methods for maintaining orthogonality:**
1. **Classical Gram-Schmidt:** Simple but numerically unstable
2. **Modified Gram-Schmidt:** More stable, commonly used
3. **Householder QR:** Most stable, higher computational cost
4. **SVQB (Singular Value QR):** For very ill-conditioned subspaces

### Shift-and-Invert Acceleration

**For interior eigenvalues:** Apply subspace iteration to \( (A - \sigma I)^{-1} \):
- Converges to eigenvalues closest to shift \( \sigma \)
- Requires solving linear systems at each iteration
- More expensive per iteration but fewer iterations needed

## Classification and Variants

### By Problem Type
1. **Standard subspace iteration:** For \( A\mathbf{x} = \lambda\mathbf{x} \)
2. **Generalized subspace iteration:** For \( A\mathbf{x} = \lambda B\mathbf{x} \)
3. **Nonlinear subspace iteration:** For \( T(\lambda)\mathbf{x} = \mathbf{0} \)
4. **Symmetric subspace iteration:** Exploiting symmetry for efficiency

### By Orthogonalization Strategy
1. **Full orthogonalization:** Complete reorthogonalization each iteration
2. **Selective orthogonalization:** Orthogonalize only against converged vectors
3. **Partial orthogonalization:** Periodic full orthogonalization
4. **Block orthogonalization:** Orthogonalize blocks of vectors

### By Implementation Approach
1. **Basic subspace iteration:** As described above
2. **Chebyshev accelerated:** Polynomial acceleration for faster convergence
3. **Preconditioned subspace iteration:** With preconditioner for shifted problems
4. **Parallel subspace iteration:** Distributed implementation for large problems

## Derivation and Proof

### Derivation from [[Power Method]]

**Extension to multiple vectors:** Start with \( p \) linearly independent vectors \( V^{(0)} \).

**Power iteration applied simultaneously:**
$$
V^{(k)} = A^k V^{(0)}
$$

**Problem:** Columns of \( V^{(k)} \) become increasingly aligned with dominant eigenvector.

**Solution:** Orthonormalize after each multiplication:
$$
V^{(k)} R^{(k)} = A V^{(k-1)} \quad \text{(QR factorization)}
$$

**Rayleigh-Ritz enhancement:** To improve convergence, compute optimal approximations in current subspace:
1. Form \( H^{(k)} = (V^{(k)})^T A V^{(k)} \)
2. Solve \( H^{(k)} Q^{(k)} = Q^{(k)} \Theta^{(k)} \)
3. Update \( V^{(k)} \leftarrow V^{(k)} Q^{(k)} \)

### Convergence Proof

**Assumptions:** \( A \) symmetric positive definite, eigenvalues \( \lambda_1 > \lambda_2 > \cdots > \lambda_n > 0 \).

**Key steps:**
1. Express \( V^{(0)} = \widetilde{V}C + \widetilde{V}_\perp D \) where \( \widetilde{V} \) contains first \( p \) eigenvectors
2. After \( k \) iterations: \( V^{(k)} = \text{orthonormal}(A^k V^{(0)}) \)
3. Show \( \|(I - \widetilde{V}\widetilde{V}^T) V^{(k)}\| \leq \left( \frac{\lambda_{p+1}}{\lambda_1} \right)^k \|D\| \|C^{-1}\| \)
4. Rayleigh-Ritz approximations converge at twice the rate

### Error Bounds

**For Ritz values \( \theta_i^{(k)} \):**
$$
0 \leq \lambda_i - \theta_i^{(k)} \leq (\lambda_i - \lambda_{p+1}) \left( \frac{\lambda_{p+1}}{\lambda_i} \right)^{2k} \tan^2 \angle(\mathcal{R}(V^{(0)}), \mathcal{V}_i)
$$

**For Ritz vectors \( \mathbf{u}_i^{(k)} \):**
$$
\sin \angle(\mathbf{u}_i^{(k)}, \mathbf{v}_i) \leq \frac{\lambda_i - \lambda_{p+1}}{\lambda_i - \lambda_{i-1}} \left( \frac{\lambda_{p+1}}{\lambda_i} \right)^k \tan \angle(\mathcal{R}(V^{(0)}), \mathcal{V}_i)
$$

## Physical Interpretation

### Modal Excitation and Filtering

**[[Structural Dynamics]] analogy:** Simultaneously excite structure with multiple force patterns:
- Each iteration applies dynamic stiffness matrix
- [[Orthogonalization]] maintains distinct excitation patterns
- Converges to true mode shapes

**Frequency domain view:** Acts as parallel bandpass filter bank:
- Each vector tuned to different frequency range
- Orthogonalization prevents mode mixing
- Rayleigh-Ritz provides optimal frequency estimates

### Energy Distribution Tracking

**Subspace energy:** Track how energy distributes among subspace vectors:
- Initially distributed according to initial conditions
- With iterations, energy concentrates in directions of dominant eigenvectors
- Orthogonalization redistributes energy to maintain diversity

### Convergence Visualization

**Trajectory in Grassmannian:** Subspace iteration follows path in Grassmann manifold \( Gr(p, n) \):
- Each iteration: linear transformation followed by projection to nearest orthonormal basis
- Converges to invariant subspace spanned by desired eigenvectors
- Geometric interpretation helps understand convergence properties

## Applications

### Engineering Disciplines
1. **[[Structural Dynamics]]:** Computing multiple vibration modes of large structures
2. **Mechanical Engineering:** Rotor dynamics, critical speed analysis
3. **Electrical Engineering:** Power system stability, eigenanalysis of networks
4. **Aerospace Engineering:** Flutter analysis, aircraft mode shapes
5. **Civil Engineering:** Seismic analysis, building mode extraction

### Scientific Fields
1. **Quantum Chemistry:** Computing multiple electronic states
2. **Computational Physics:** Band structure calculations in solids
3. **Fluid Dynamics:** Stability analysis of fluid flows
4. **Acoustics:** Room mode calculations
5. **Materials Science:** Phonon dispersion relations

### Practical Implementations
- **[[Finite Element Analysis (FEA)]]:** Extracting multiple vibration modes
- **Control systems:** Model reduction via balanced truncation
- **[[Signal processing]]:** Subspace-based frequency estimation
- **[[Machine learning]]:** Principal component analysis for large datasets
- **Quantum computing:** Ground and excited state calculations

## Implementation Considerations

### Algorithm Implementation

**Basic subspace iteration pseudocode:**
```
function subspace_iteration(A, m, max_iter, tol):
    p = min(2*m, m+8)          # Number of subspace vectors
    n = size(A, 1)
    
    # Initialize random orthonormal matrix
    V = random_normal(n, p)
    V, _ = qr(V)               # Orthonormalize
    
    converged = zeros(m, bool)
    eigenvalues = zeros(m)
    
    for iter = 1 to max_iter:
        # Matrix multiplication
        W = A * V
        
        # Orthogonalization (Modified Gram-Schmidt)
        for j = 1 to p:
            for i = 1 to j-1:
                W[:,j] -= (V[:,i]' * W[:,j]) * V[:,i]
            W[:,j] = W[:,j] / norm(W[:,j])
        
        # Rayleigh-Ritz projection
        H = W' * A * W         # p x p matrix
        Theta, Q = eig(H)      # Solve small eigenvalue problem
        
        # Sort eigenvalues (descending for largest, ascending for smallest)
        idx = sort_indices(Theta, order='descending')
        Theta = Theta[idx]
        Q = Q[:, idx]
        
        # Update subspace
        V = W * Q
        
        # Check convergence for first m eigenpairs
        for i = 1 to m:
            if not converged[i]:
                # Compute residual
                u = V[:, i]    # Approximate eigenvector
                theta = Theta[i]  # Approximate eigenvalue
                r = A * u - theta * u
                
                if norm(r) < tol * norm(A):
                    converged[i] = true
                    eigenvalues[i] = theta
        
        if all(converged[1:m]):
            break
    
    # Extract converged eigenpairs
    eigenvectors = V[:, 1:m]
    eigenvalues = Theta[1:m]
    
    return eigenvalues, eigenvectors
```

### Orthogonalization Techniques

**Modified Gram-Schmidt (MGS):**
```
for j = 1 to p:
    v = W[:, j]
    for i = 1 to j-1:
        r = dot(V[:, i], v)
        v = v - r * V[:, i]
    r = norm(v)
    V[:, j] = v / r
    R[j, j] = r
```

**Householder QR:** More stable but more expensive
**SVQB (Singular Value QR):** For ill-conditioned subspaces

### Convergence Acceleration

**Polynomial acceleration:** Use Chebyshev polynomials to enhance convergence:
- Filter subspace to emphasize desired eigenvalues
- Apply polynomial \( p_k(A) \) instead of \( A^k \)
- Requires eigenvalue bounds for polynomial construction

**Shift-and-invert:** For interior eigenvalues:
- Apply subspace iteration to \( (A - \sigma I)^{-1} \)
- Requires solving linear systems: \( (A - \sigma I)W = V \)
- Use preconditioned iterative solvers for large systems

### Parallel Implementation

**Data distribution:**
- Distribute matrix \( A \) by rows or blocks
- Distribute subspace vectors across processors
- Collective operations for orthogonalization

**Communication patterns:**
- All-reduce for dot products in orthogonalization
- All-gather for matrix multiplication with distributed matrix
- Overlap computation and communication

## Advantages and Limitations

### Strengths
1. **Multiple eigenpairs:** Computes several eigenvalues/vectors simultaneously
2. **Robust convergence:** Reliable for well-separated extreme eigenvalues
3. **Memory efficient:** Only stores subspace vectors, not full matrix
4. **Sparse matrix friendly:** Only matrix-vector multiplications needed
5. **Parallelizable:** Natural parallelism in matrix-vector operations

### Weaknesses
1. **Slow convergence:** For clustered eigenvalues or interior eigenvalues
2. **[[Orthogonalization]] cost:** Can be significant for large subspaces
3. **Initial subspace sensitivity:** Convergence depends on initial subspace
4. **No a priori error bounds:** Difficult to predict iteration count
5. **Locking mechanism needed:** For stopping iterations on converged vectors

### Validity Range
- **Optimal for:** Computing several extreme eigenvalues of large sparse matrices
- **Less effective for:** Interior eigenvalues without shift-and-invert
- **Not recommended for:** Computing many eigenvalues (more than 50-100)
- **Best results:** When \( \lambda_m \gg \lambda_{m+1} \) (well-separated eigenvalues)

## Advanced Topics

### Block Krylov Methods

**Lanczos/Arnoldi connection:** Subspace iteration generates Krylov subspace:
$$
\mathcal{K}_k(A, V^{(0)}) = \text{span}\{V^{(0)}, AV^{(0)}, \ldots, A^{k-1}V^{(0)}\}
$$

**Implicit restarting:** Combines subspace iteration with filtering:
- Apply polynomial filter to remove unwanted components
- Truncate and restart with refined subspace
- Basis for implicitly restarted Arnoldi (IRA) methods

### Nonlinear Eigenvalue Problems

**Subspace iteration for \( T(\lambda)\mathbf{x} = \mathbf{0} \):**
1. Linearize at current eigenvalue approximations
2. Apply subspace iteration to linearized problems
3. Update eigenvalue approximations via Rayleigh quotient
4. Repeat until convergence

**Applications:** Damped vibration systems, delay differential equations.

### Randomized Subspace Iteration

**Random initialization:** Start with random subspace
**Oversampling:** Use \( p = m + r \) where \( r \) is oversampling factor
**Theoretical guarantees:** High probability convergence bounds
**Applications:** Very large problems, streaming data

### Dynamic Subspace Sizing

**Adaptive subspace dimension:** Adjust \( p \) during iteration:
- Increase if convergence slow
- Decrease if many vectors converged
- Based on convergence monitoring and residual estimates

**Locking and purging:** Remove converged vectors, add new random vectors

## Special Cases and Examples

### Benchmark Problems

**Tridiagonal matrix (Poisson equation):**
$$
A = \text{tridiag}(-1, 2, -1) \in \mathbb{R}^{1000 \times 1000}
$$
Eigenvalues: \( \lambda_i = 2 - 2\cos(\frac{i\pi}{n+1}) \), \( i = 1, \ldots, n \)

**Subspace iteration for 10 smallest eigenvalues:**
- Use shift-and-invert with \( \sigma = 0 \)
- Subspace size: \( p = 20 \)
- Convergence: ~15 iterations to \( 10^{-8} \) tolerance

**Laplacian on 2D grid:** 100×100 grid, \( n = 10,000 \)
- Compute 20 smallest eigenvalues
- Subspace size: \( p = 40 \)
- Memory: Store 40 vectors of length 10,000 = 3.2MB (double precision)
- Compared to storing full matrix: 800MB

### Analytical Convergence

**2×2 block analysis:** For matrix with eigenvalues \( \lambda_1 > \lambda_2 > \lambda_3 > \cdots \):

**Subspace of size 2:** Convergence to first two eigenvectors:
$$
\tan \angle(\mathcal{R}(V^{(k)}), \text{span}\{\mathbf{v}_1, \mathbf{v}_2\}) \leq \left( \frac{\lambda_3}{\lambda_2} \right)^k \tan \angle(\mathcal{R}(V^{(0)}), \text{span}\{\mathbf{v}_1, \mathbf{v}_2\})
$$

**Ritz value convergence:**
$$
|\lambda_i - \theta_i^{(k)}| \leq \left( \frac{\lambda_3}{\lambda_i} \right)^{2k} |\lambda_i - \lambda_3| \tan^2 \angle(\cdot)
$$

### Industrial Applications

**Aircraft wing vibration analysis:**
- Matrix size: \( n \approx 500,000 \) DOFs
- Desired: First 20 vibration modes (0-50 Hz)
- Method: Subspace iteration with shift-and-invert (\( \sigma = (2\pi \cdot 30)^2 \))
- Result: 20 modes in 25 iterations, 4 hours compute time
- Memory: 20 subspace vectors = 80MB vs. full matrix = 2TB

**Electronic structure calculation:**
- Hamiltonian matrix: \( n \approx 10,000 \) (dense)
- Desired: 50 lowest eigenstates
- Method: Subspace iteration with Chebyshev acceleration
- Result: 50 states in 40 iterations, 30 minutes
- Accuracy: \( 10^{-6} \) Hartree for energies

## Error Analysis

### Forward Error Bounds

**For Ritz values:** 
$$
|\lambda_i - \theta_i^{(k)}| \leq \frac{\|r_i^{(k)}\|^2}{\delta_i^{(k)}}
$$
where \( r_i^{(k)} = A\mathbf{u}_i^{(k)} - \theta_i^{(k)}\mathbf{u}_i^{(k)} \) and \( \delta_i^{(k)} = \min_{j \neq i} |\theta_j^{(k)} - \theta_i^{(k)}| \).

**For Ritz vectors:**
$$
\sin \angle(\mathbf{u}_i^{(k)}, \mathbf{v}_i) \leq \frac{\|r_i^{(k)}\|}{\delta_i^{(k)}}
$$

**A priori bounds:** As given in convergence theory section.

### Backward Error Analysis

**Computed eigenpairs \( (\tilde{\lambda}_i, \tilde{\mathbf{u}}_i) \):** There exists \( E_i \) with \( \|E_i\| = O(\epsilon \|A\|) \) such that:
$$
(A + E_i)\tilde{\mathbf{u}}_i = \tilde{\lambda}_i\tilde{\mathbf{u}}_i
$$

**Subspace condition:** For entire computed invariant subspace \( \tilde{U} \), there exists \( E \) with \( \|E\| = O(\epsilon \|A\|) \) such that:
$$
(A + E)\tilde{U} = \tilde{U}\tilde{\Lambda}
$$
where \( \tilde{\Lambda} = \text{diag}(\tilde{\lambda}_1, \ldots, \tilde{\lambda}_m) \).

### Orthogonality Error

**Loss of orthogonality:** In finite precision, \( \tilde{U}^T\tilde{U} \neq I \).

**Error bound:** With MGS orthogonalization:
$$
\|I - \tilde{U}^T\tilde{U}\| \leq c_1(n, p)\epsilon \kappa(V)
$$
where \( \kappa(V) \) is condition number of subspace basis.

**Reorthogonalization:** May be needed if \( \|I - V^TV\| > \sqrt{\epsilon} \).

## Relationship to Other Concepts

### Comparison with Lanczos/Arnoldi

**Subspace iteration:**
- Explicit subspace construction
- Simultaneous iteration on multiple vectors
- Linear convergence, robust

**Lanczos/Arnoldi:**
- Implicit subspace construction via recurrence
- Typically faster convergence for extremal eigenvalues
- Can suffer from loss of orthogonality

**Hybrid methods:** Subspace iteration with Ritz acceleration similar to Arnoldi.

### Connection to [[Power Method]]

**[[Power Method]]:** Single vector, converges to dominant eigenvector
**Subspace iteration:** Multiple vectors, converges to invariant subspace
**Relationship:** Subspace iteration = parallel power methods + orthogonalization

### Integration with Rayleigh-Ritz

**Rayleigh-Ritz procedure:** Optimal projection onto subspace
**Subspace iteration:** Generates improving subspace
**Combination:** Subspace iteration provides subspace, Rayleigh-Ritz extracts best approximations

### Relationship to QR Algorithm

**QR algorithm:** For dense matrices, computes all eigenvalues
**Subspace iteration:** For large sparse matrices, computes subset
**Connection:** QR algorithm can be viewed as subspace iteration on full basis with exact orthogonalization

## Historical Context and Evolution

### Original Motivation

**Structural engineering needs:**
- Compute multiple vibration modes of large structures
- Finite element models produced large sparse matrices
- Full diagonalization computationally impossible
- Need for reliable method for few extreme eigenvalues

**Early developments:** Simultaneous iteration suggested by several researchers independently.

### Evolution Over Time

1. **1960s:** Basic algorithm development, convergence analysis
2. **1970s:** Implementation in structural analysis software (NASTRAN, ANSYS)
3. **1980s:** Integration with shift-and-invert, parallel implementations
4. **1990s:** Comparison with Lanczos/Arnoldi, hybrid methods
5. **2000s:** Randomized variants, applications in data science
6. **2010s:** GPU implementations, very large-scale problems

### Modern Reformulations

- **Randomized subspace iteration:** With theoretical guarantees
- **Streaming subspace iteration:** For data streams and online learning
- **Federated subspace iteration:** For distributed data with privacy
- **Quantum subspace iteration:** For quantum computers

## Pedagogical Approach

### Teaching Strategies

1. **From [[Power Method]] to subspace iteration:** Extend single vector to multiple vectors
2. **Geometric visualization:** Show subspace convergence in 3D examples
3. **Hands-on implementation:** Code simple version, experiment with parameters
4. **Comparison with other methods:** Contrast with Lanczos, QR algorithm

### Common Misconceptions

1. **"Subspace iteration always converges to extremal eigenvalues":** Can target interior eigenvalues with shift-and-invert
2. **"More vectors always faster convergence":** Optimal subspace size depends on eigenvalue distribution
3. **"Orthogonalization is optional":** Critical for maintaining linear independence
4. **"Subspace iteration is obsolete":** Still widely used, especially in [[Structural Dynamics]]

### Learning Resources

**Foundational Texts:**
- Bathe, "Finite Element Procedures"
- Parlett, "The Symmetric Eigenvalue Problem"
- Saad, "Numerical Methods for Large Eigenvalue Problems"
- Golub & Van Loan, "Matrix Computations"

**Online Resources:**
- MIT OpenCourseWare 18.335: Numerical Linear Algebra
- NLAFET Educational Resources on Eigenvalue Algorithms
- Wikipedia: "Subspace iteration" with examples
- YouTube: Visualizations of subspace convergence

**Software Tutorials:**
- MATLAB: Subspace iteration implementation examples
- Python/SciPy: Using sparse matrices with subspace iteration
- SLEPc: Parallel eigenvalue solver tutorial
- ANSYS: [[Modal Analysis]] with subspace iteration

## Implementation in Software

### MATLAB Implementation

```matlab
function [lambda, V, resnorms, iters] = subspace_iteration(A, m, maxit, tol)
    % Subspace iteration for computing m largest eigenvalues of A
    % A: symmetric matrix (n x n)
    % m: number of eigenvalues desired
    % maxit: maximum iterations
    % tol: convergence tolerance
    
    n = size(A, 1);
    p = min(2*m, m + 8);  % Subspace dimension
    
    % Initialize random orthonormal matrix
    V = randn(n, p);
    [V, ~] = qr(V, 0);  % Economy QR
    
    % Preallocate
    lambda = zeros(m, 1);
    resnorms = zeros(maxit, m);
    converged = false(m, 1);
    
    fprintf('Subspace iteration: n=%d, m=%d, p=%d\n', n, m, p);
    
    for iter = 1:maxit
        % Matrix multiplication
        W = A * V;
        
        % Orthogonalization (Modified Gram-Schmidt)
        for j = 1:p
            for i = 1:j-1
                r = V(:, i)' * W(:, j);
                W(:, j) = W(:, j) - r * V(:, i);
            end
            nrm = norm(W(:, j));
            if nrm > 0
                W(:, j) = W(:, j) / nrm;
            else
                % Handle zero vector (add random component)
                W(:, j) = randn(n, 1);
                for i = 1:j-1
                    r = V(:, i)' * W(:, j);
                    W(:, j) = W(:, j) - r * V(:, i);
                end
                W(:, j) = W(:, j) / norm(W(:, j));
            end
        end
        
        % Rayleigh-Ritz projection
        H = W' * (A * W);  % p x p matrix
        [Q, Theta] = eig(H);
        theta = diag(Theta);
        
        % Sort eigenvalues (descending for largest)
        [theta, idx] = sort(theta, 'descend');
        Q = Q(:, idx);
        
        % Update subspace
        V = W * Q;
        
        % Check convergence for first m eigenpairs
        nconv = 0;
        for i = 1:m
            if ~converged(i)
                u = V(:, i);
                lam = theta(i);
                r = A * u - lam * u;
                resnorm = norm(r);
                resnorms(iter, i) = resnorm;
                
                if resnorm < tol * norm(A, 'fro')
                    converged(i) = true;
                    lambda(i) = lam;
                    nconv = nconv + 1;
                end
            else
                resnorms(iter, i) = 0;
            end
        end
        
        fprintf('Iteration %3d: %2d converged, max residual = %.2e\n', ...
                iter, nconv, max(resnorms(iter, 1:m)));
        
        if all(converged(1:m))
            iters = iter;
            resnorms = resnorms(1:iter, :);
            lambda = theta(1:m);
            V = V(:, 1:m);
            fprintf('Converged in %d iterations\n', iter);
            return;
        end
    end
    
    iters = maxit;
    warning('Subspace iteration did not converge in %d iterations', maxit);
    lambda = theta(1:m);
    V = V(:, 1:m);
end

% Shift-and-invert subspace iteration
function [lambda, V] = subspace_iteration_si(A, sigma, m, maxit, tol)
    % Subspace iteration with shift-and-invert for eigenvalues near sigma
    n = size(A, 1);
    p = min(2*m, m + 8);
    
    % Factor (A - sigma*I)
    [L, U, P] = lu(A - sigma * eye(n));
    
    % Initialize
    V = randn(n, p);
    [V, ~] = qr(V, 0);
    
    for iter = 1:maxit
        % Solve (A - sigma*I)W = V
        W = U \ (L \ (P * V));
        
        % Orthogonalize
        [W, ~] = qr(W, 0);
        
        % Rayleigh-Ritz for (A - sigma*I)^{-1}
        H = W' * A * W;
        [Q, Theta] = eig(H);
        theta = diag(Theta);
        
        % Sort by distance to sigma
        [~, idx] = sort(abs(theta - sigma), 'ascend');
        theta = theta(idx);
        Q = Q(:, idx);
        
        % Update subspace
        V = W * Q;
        
        % Check convergence
        % ... similar to basic version
    end
    
    lambda = theta(1:m);
    V = V(:, 1:m);
end
```

### Python Implementation

```python
import numpy as np
from scipy.linalg import qr, eig, norm
from scipy.sparse.linalg import splu, spsolve

def subspace_iteration(A, m, max_iter=100, tol=1e-8, verbose=True):
    """
    Subspace iteration for symmetric matrix A
    
    Parameters
    ----------
    A : array or sparse matrix
        Symmetric matrix (n x n)
    m : int
        Number of eigenvalues desired
    max_iter : int
        Maximum iterations
    tol : float
        Convergence tolerance
    verbose : bool
        Print progress information
    
    Returns
    -------
    eigenvalues : array (m,)
        Computed eigenvalues
    eigenvectors : array (n, m)
        Computed eigenvectors
    resnorms : list
        Residual norms per iteration
    n_iter : int
        Number of iterations performed
    """
    n = A.shape[0]
    p = min(2 * m, m + 8)  # Subspace dimension
    
    # Initialize random orthonormal matrix
    V = np.random.randn(n, p)
    V, _ = qr(V, mode='economic')
    
    eigenvalues = np.zeros(m)
    converged = np.zeros(m, dtype=bool)
    all_resnorms = []
    
    for n_iter in range(1, max_iter + 1):
        # Matrix multiplication
        if hasattr(A, 'dot'):
            W = A.dot(V)  # Sparse matrix
        else:
            W = A @ V      # Dense matrix
        
        # Modified Gram-Schmidt orthogonalization
        for j in range(p):
            for i in range(j):
                r = np.dot(V[:, i], W[:, j])
                W[:, j] -= r * V[:, i]
            nrm = norm(W[:, j])
            if nrm > 0:
                W[:, j] /= nrm
            else:
                # Handle zero vector
                W[:, j] = np.random.randn(n)
                for i in range(j):
                    r = np.dot(V[:, i], W[:, j])
                    W[:, j] -= r * V[:, i]
                W[:, j] /= norm(W[:, j])
        
        # Rayleigh-Ritz projection
        if hasattr(A, 'dot'):
            H = W.T @ A.dot(W)
        else:
            H = W.T @ (A @ W)
        
        # Solve small eigenvalue problem
        theta, Q = eig(H)
        theta = np.real(theta)  # A is symmetric
        
        # Sort eigenvalues (descending for largest)
        idx = np.argsort(theta)[::-1]
        theta = theta[idx]
        Q = Q[:, idx]
        
        # Update subspace
        V = W @ Q
        
        # Check convergence
        resnorms = np.zeros(m)
        n_converged = 0
        
        for i in range(m):
            if not converged[i]:
                u = V[:, i]
                lam = theta[i]
                
                if hasattr(A, 'dot'):
                    r = A.dot(u) - lam * u
                else:
                    r = A @ u - lam * u
                
                resnorm = norm(r)
                resnorms[i] = resnorm
                
                if resnorm < tol * np.linalg.norm(A, 'fro'):
                    converged[i] = True
                    eigenvalues[i] = lam
                    n_converged += 1
        
        all_resnorms.append(resnorms.copy())
        
        if verbose:
            max_res = np.max(resnorms) if len(resnorms) > 0 else 0
            print(f'Iteration {n_iter:3d}: {n_converged:2d} converged, '
                  f'max residual = {max_res:.2e}')
        
        if np.all(converged):
            break
    
    # Extract results
    eigenvalues = theta[:m]
    eigenvectors = V[:, :m]
    
    return eigenvalues, eigenvectors, all_resnorms, n_iter

def subspace_iteration_shift_invert(A, sigma, m, max_iter=100, tol=1e-8):
    """
    Subspace iteration with shift-and-invert for eigenvalues near sigma
    """
    n = A.shape[0]
    p = min(2 * m, m + 8)
    
    # Create shifted matrix
    if hasattr(A, 'tocsc'):
        # Sparse matrix
        import scipy.sparse as sp
        M = A - sigma * sp.eye(n)
        solver = splu(M.tocsc())
        solve = lambda x: solver.solve(x)
    else:
        # Dense matrix
        M = A - sigma * np.eye(n)
        lu = np.linalg.lu_factor(M)
        solve = lambda x: np.linalg.lu_solve(lu, x)
    
    # Initialize
    V = np.random.randn(n, p)
    V, _ = qr(V, mode='economic')
    
    for n_iter in range(1, max_iter + 1):
        # Solve (A - sigma*I)W = V
        W = solve(V)
        
        # Orthogonalize
        W, _ = qr(W, mode='economic')
        
        # Rayleigh-Ritz
        if hasattr(A, 'dot'):
            H = W.T @ A.dot(W)
        else:
            H = W.T @ (A @ W)
        
        theta, Q = eig(H)
        theta = np.real(theta)
        
        # Sort by distance to sigma
        idx = np.argsort(np.abs(theta - sigma))
        theta = theta[idx]
        Q = Q[:, idx]
        
        # Update subspace
        V = W @ Q
        
        # Check convergence (similar to above)
        # ...
    
    eigenvalues = theta[:m]
    eigenvectors = V[:, :m]
    
    return eigenvalues, eigenvectors
```

### Commercial Software Features

**ANSYS Mechanical:**
- Subspace iteration as default eigensolver for large models
- Automatic selection of subspace size
- Shift-and-invert for frequency ranges
- GPU acceleration option

**NASTRAN:**
- SOL 103: Normal modes with subspace iteration
- Automated shift strategies
- DMAP alter for custom subspace iteration

**ABAQUS:**
- Subspace iteration eigensolver
- Lanczos as alternative
- Frequency extraction with subspace method

**MATLAB:**
- `eigs` with 'sr' (smallest real) uses subspace iteration concepts
- Custom implementations using matrix-vector multiplication

## See Also

- [[Power Method]]
- [[Inverse Power Method]]
- [[Lanczos Method]]
- [[Arnoldi Method]]
- [[Ritz Method (Rayleigh-Ritz Method)]]
- Krylov Subspace Method
- [[QR Algorithm]]
- [[Simultaneous Iteration]]
- Block Power Method
- [[Orthogonalization]]
- [[Gram-Schmidt Method]]
- [[Subspace Projection]]
- [[Eigenvalue Problem]]
- [[Sparse Matrix]]
- [[Finite Element Analysis (FEA)]]
- [[Modal Analysis]]
- [[Structural Dynamics]]
- [[Numerical Linear Algebra]]

---

*Note: The Subspace Iteration Method represents a fundamental algorithm for computing multiple eigenvalues and eigenvectors of large matrices. Its robustness, combined with its ability to handle very large sparse systems, makes it indispensable in engineering applications such as [[Structural Dynamics]], where computing several vibration modes is essential for design and analysis.*
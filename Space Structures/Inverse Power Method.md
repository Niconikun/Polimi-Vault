## Formal Definition

The **Inverse Power Method** (also known as **Inverse Iteration**) is an iterative numerical algorithm for finding the eigenvalue of a matrix that is closest to a specified shift value and its corresponding eigenvector. This method is essentially the Power Method applied to the inverse of a shifted matrix, allowing convergence to any eigenvalue rather than just the dominant one. The Inverse Power Method is particularly valuable for finding eigenvalues near a known approximation and for computing eigenvectors with high accuracy once an eigenvalue approximation is known.

## Historical Development

### Key Milestones
- **1940s:** Helmut Wielandt introduces the Inverse Power Method as a tool for eigenvalue computation
- **1950s:** John H. Wilkinson analyzes and formalizes the method's convergence properties
- **1960s:** Integration with Rayleigh quotient iteration for accelerated convergence
- **1970s:** Application to large sparse matrices using iterative linear solvers
- **1980s:** Development of shift strategies for computing interior eigenvalues
- **1990s:** Implementation in numerical linear algebra libraries (LAPACK, ARPACK)
- **2000s:** Extension to generalized eigenvalue problems and nonlinear eigenvalue problems

### Foundational Contributors
1. **Helmut Wielandt (1910-2001):** Introduced the Inverse Power Method
2. **John H. Wilkinson (1919-1986):** Analyzed numerical stability and convergence
3. **James H. Wilkinson (1919-1986):** Advanced the method's use in practical computations
4. **Beresford N. Parlett (1932-2020):** Contributed to modern eigenvalue algorithms based on inverse iteration

## Mathematical Formulation

### Basic Algorithm

Given an \( n \times n \) matrix \( A \), shift \( \sigma \), and initial vector \( \mathbf{v}^{(0)} \):

**Algorithm steps:**
1. Choose shift \( \sigma \) (approximation to desired eigenvalue)
2. Choose initial nonzero vector \( \mathbf{v}^{(0)} \)
3. For \( k = 0, 1, 2, \ldots \) until convergence:
   a. Solve \( (A - \sigma I) \mathbf{w}^{(k+1)} = \mathbf{v}^{(k)} \)
   b. Normalize: \( \mathbf{v}^{(k+1)} = \frac{\mathbf{w}^{(k+1)}}{\|\mathbf{w}^{(k+1)}\|} \)
   c. Compute Rayleigh quotient: \( \mu^{(k+1)} = (\mathbf{v}^{(k+1)})^T A \mathbf{v}^{(k+1)} \)

### Mathematical Representation

**Iterative process:**
Let \( B = (A - \sigma I)^{-1} \). Inverse iteration applies Power Method to \( B \):
$$
\mathbf{v}^{(k+1)} = \frac{B \mathbf{v}^{(k)}}{\|B \mathbf{v}^{(k)}\|}
$$

**Eigenvalue approximation:** The eigenvalue \( \lambda \) closest to \( \sigma \) satisfies:
$$
\lambda \approx \sigma + \frac{1}{\mu}
$$
where \( \mu \) is the dominant eigenvalue of \( B \).

**Rayleigh quotient iteration variant:** Update shift each iteration:
$$
\sigma^{(k)} = \frac{(\mathbf{v}^{(k)})^T A \mathbf{v}^{(k)}}{(\mathbf{v}^{(k)})^T \mathbf{v}^{(k)}}
$$

### Rate of Convergence

The convergence rate depends on the ratio:
$$
\left| \frac{\lambda - \sigma}{\lambda' - \sigma} \right|
$$
where \( \lambda \) is the target eigenvalue and \( \lambda' \) is the next closest eigenvalue to \( \sigma \). If \( \sigma \) is close to \( \lambda \), convergence is rapid.

## Fundamental Principles

### Shift-and-Invert Transformation

**Key idea:** Transform [[Eigenvalue Problem]] so desired eigenvalue becomes dominant:
- Original problem: Find \( \lambda \) near \( \sigma \)
- Transformed problem: Apply Power Method to \( (A - \sigma I)^{-1} \)
- Dominant eigenvalue of transformed matrix: \( \frac{1}{\lambda - \sigma} \)

**Advantage:** Can find any eigenvalue, not just extreme ones.

### Choice of Shift

**Strategies for selecting \( \sigma \):**
1. **Fixed shift:** Known approximation to desired eigenvalue
2. **Rayleigh quotient shift:** Update based on current eigenvector approximation
3. **Spectrum slicing:** For finding multiple eigenvalues in an interval
4. **Dynamic shift:** Adjust based on convergence behavior

**Optimal shift:** When \( \sigma = \lambda \) (exact eigenvalue), convergence becomes extremely fast.

### Linear System Solution

At each iteration, must solve:
$$
(A - \sigma I) \mathbf{w} = \mathbf{v}
$$

**Solution methods:**
- **Direct methods:** LU factorization for small to medium matrices
- **Iterative methods:** For large sparse matrices (CG, GMRES, MINRES)
- **Preconditioning:** Essential for efficiency with iterative solvers

## Theoretical Framework

### Relationship to Power Method

**Connection:** Inverse Power Method = Power Method applied to \( (A - \sigma I)^{-1} \)

**Proof:** If \( A\mathbf{v} = \lambda\mathbf{v} \), then:
$$
(A - \sigma I)^{-1} \mathbf{v} = \frac{1}{\lambda - \sigma} \mathbf{v}
$$
Thus \( \mathbf{v} \) is eigenvector of \( (A - \sigma I)^{-1} \) with eigenvalue \( 1/(\lambda - \sigma) \).

**Consequence:** The eigenvalue of \( A \) closest to \( \sigma \) becomes the dominant eigenvalue of \( (A - \sigma I)^{-1} \).

### Convergence Analysis

**Theorem:** If \( A \) is diagonalizable with eigenvalues \( \lambda_1, \ldots, \lambda_n \) and \( |\lambda_1 - \sigma| < |\lambda_i - \sigma| \) for \( i > 1 \), then Inverse Power Method converges to eigenvector corresponding to \( \lambda_1 \).

**Convergence factor:**
$$
\left\| \mathbf{v}^{(k)} - \mathbf{v}_1 \right\| = O\left( \left| \frac{\lambda_1 - \sigma}{\lambda_2 - \sigma} \right|^k \right)
$$
where \( \lambda_2 \) is second closest eigenvalue to \( \sigma \).

**Rayleigh quotient iteration:** Cubic convergence for symmetric matrices, quadratic for non-symmetric.

### Deflation Techniques

**Finding multiple eigenvalues:** After finding \( (\lambda_1, \mathbf{v}_1) \), work with deflated matrix:

**Hotelling deflation (symmetric case):**
$$
A^{(2)} = A - \lambda_1 \mathbf{v}_1 \mathbf{v}_1^T
$$

**Wielandt deflation (general case):**
$$
A^{(2)} = (I - \mathbf{v}_1 \mathbf{u}_1^T) A (I - \mathbf{v}_1 \mathbf{u}_1^T)^{-1}
$$
where \( \mathbf{u}_1 \) is left eigenvector.

## Classification and Variants

### By Shift Strategy
1. **Fixed shift inverse iteration:** Constant shift throughout
2. **Rayleigh quotient iteration:** Shift updated each iteration to current Rayleigh quotient
3. **Generalized Rayleigh quotient iteration:** For generalized eigenvalue problems
4. **Ostrowski inverse iteration:** With optimized shift updates

### By Matrix Type
1. **Standard inverse iteration:** For \( A\mathbf{v} = \lambda\mathbf{v} \)
2. **Generalized inverse iteration:** For \( A\mathbf{v} = \lambda B\mathbf{v} \)
3. **Symmetric inverse iteration:** Exploits symmetry for efficiency
4. **Non-symmetric inverse iteration:** With additional considerations for complex eigenvalues

### By Implementation Approach
1. **Direct inverse iteration:** Using explicit factorization of \( A - \sigma I \)
2. **Iterative inverse iteration:** Using iterative linear solvers
3. **Preconditioned inverse iteration:** With preconditioner for faster linear solves
4. **Block inverse iteration:** For multiple eigenvalues simultaneously

## Derivation and Proof

### Derivation from First Principles

**Step 1: Start with [[Eigenvalue Problem]]**
$$
A\mathbf{v} = \lambda\mathbf{v}
$$

**Step 2: Introduce shift**
$$
(A - \sigma I)\mathbf{v} = (\lambda - \sigma)\mathbf{v}
$$

**Step 3: Invert (assuming \( \lambda \neq \sigma \))**
$$
(A - \sigma I)^{-1} \mathbf{v} = \frac{1}{\lambda - \sigma} \mathbf{v}
$$

**Step 4: Apply Power Method**
Iterate: \( \mathbf{v}^{(k+1)} = \frac{(A - \sigma I)^{-1} \mathbf{v}^{(k)}}{\|(A - \sigma I)^{-1} \mathbf{v}^{(k)}\|} \)

**Step 5: Practical implementation**
Solve linear system instead of explicit inversion:
$$
(A - \sigma I) \mathbf{w}^{(k+1)} = \mathbf{v}^{(k)}
$$

### Proof of Convergence

**Assumptions:**
- \( A \) diagonalizable: \( A = X\Lambda X^{-1} \)
- Eigenvalues ordered by distance to \( \sigma \): \( |\lambda_1 - \sigma| < |\lambda_2 - \sigma| \leq \cdots \leq |\lambda_n - \sigma| \)
- Initial vector: \( \mathbf{v}^{(0)} = \sum_{i=1}^n c_i \mathbf{x}_i \) with \( c_1 \neq 0 \)

**Analysis:**
After \( k \) iterations:
$$
\mathbf{v}^{(k)} = \frac{(A - \sigma I)^{-k} \mathbf{v}^{(0)}}{\|(A - \sigma I)^{-k} \mathbf{v}^{(0)}\|}
= \frac{\sum_{i=1}^n c_i (\lambda_i - \sigma)^{-k} \mathbf{x}_i}{\|\sum_{i=1}^n c_i (\lambda_i - \sigma)^{-k} \mathbf{x}_i\|}
$$

Factor \( (\lambda_1 - \sigma)^{-k} \):
$$
\mathbf{v}^{(k)} = \frac{c_1 \mathbf{x}_1 + \sum_{i=2}^n c_i \left( \frac{\lambda_1 - \sigma}{\lambda_i - \sigma} \right)^k \mathbf{x}_i}{\|c_1 \mathbf{x}_1 + \sum_{i=2}^n c_i \left( \frac{\lambda_1 - \sigma}{\lambda_i - \sigma} \right)^k \mathbf{x}_i\|}
$$

Since \( \left| \frac{\lambda_1 - \sigma}{\lambda_i - \sigma} \right| < 1 \) for \( i \geq 2 \), terms vanish as \( k \to \infty \), leaving \( \mathbf{v}^{(k)} \to \mathbf{x}_1 \).

## Physical Interpretation

### Vibration Mode Identification

**Structural dynamics context:** For [[Eigenvalue Problem]] \( (K - \omega^2 M)\boldsymbol{\phi} = \mathbf{0} \):
- Shift \( \sigma \) corresponds to approximate [[Natural Frequency]] squared
- Inverse iteration finds mode shape closest to that frequency
- Used in experimental [[Modal Analysis]] to extract specific modes

### Resonance Tuning

**Engineering design:** To avoid resonance at operating frequency \( \omega_0 \):
- Set shift \( \sigma = \omega_0^2 \)
- Inverse iteration finds closest [[Natural Frequency]]
- Design modifications to move eigenvalue away from \( \sigma \)

### Quantum State Calculation

**Quantum mechanics:** For Hamiltonian \( H \), shift \( \sigma \) near energy level of interest:
- Inverse iteration computes corresponding wavefunction
- More efficient than full diagonalization for specific states

### Sensitivity Analysis

**Perturbation interpretation:** Inverse iteration computes sensitivity of eigenvalue to changes:
- Solution of \( (A - \sigma I)\mathbf{w} = \mathbf{v} \) gives first-order perturbation
- Used in stability analysis and design optimization

## Applications

### Engineering Disciplines
1. **Structural Engineering:** Finding specific vibration modes, buckling modes
2. **Mechanical Engineering:** Rotor dynamics, critical speed analysis
3. **Electrical Engineering:** Power system stability, eigenfrequency of circuits
4. **Aerospace Engineering:** Flutter analysis, aircraft mode shapes
5. **Civil Engineering:** Seismic analysis, soil-structure interaction modes

### Scientific Fields
1. **Quantum Chemistry:** Electronic structure calculations for specific states
2. **Computational Physics:** Band structure calculations in solids
3. **Fluid Dynamics:** Stability analysis of fluid flows
4. **Acoustics:** Room mode calculations at specific frequencies
5. **Materials Science:** Phonon dispersion at specific wavevectors

### Practical Implementations
- **[[Finite Element Analysis (FEA)]]:** Extracting specific vibration modes
- **Control systems:** [[Pole placement]] and stability margin calculation
- **[[Signal processing]]:** Frequency estimation in spectral analysis
- **[[Machine learning]]:** Principal component analysis for specific components
- **Computational chemistry:** Excited state calculations

## Implementation Considerations

### Linear System Solution

**Direct methods (small to medium matrices):**
```
// LU factorization (once, reused each iteration)
[L, U, P] = lu(A - sigma*I);
for each iteration:
    w = U \ (L \ (P * v));
```

**Iterative methods (large sparse matrices):**
```
// Preconditioned conjugate gradient
M = preconditioner(A - sigma*I);
for each iteration:
    w = pcg(A - sigma*I, v, tol, maxit, M);
```

**Factorization reuse:** For fixed shift, factor once and reuse.

### Shift Selection Strategies

**Initial shift selection:**
1. **From physical knowledge:** Approximate [[Natural Frequency]], energy level
2. **From previous computation:** Result of lower-fidelity model
3. **From spectral estimates:** Gershgorin circles, eigenvalue bounds
4. **From bisection:** When searching for eigenvalues in interval

**Dynamic shift updating (Rayleigh quotient iteration):**
```
sigma_new = (v' * A * v) / (v' * v);
// Update factorization if shift changed significantly
if |sigma_new - sigma| > tolerance:
    sigma = sigma_new;
    recompute factorization of (A - sigma*I);
```

### Stopping Criteria

**Common convergence tests:**
1. **Eigenvalue relative change:**
   $$
   \frac{|\lambda^{(k)} - \lambda^{(k-1)}|}{|\lambda^{(k)}|} < \tau
   $$

2. **Residual norm:**
   $$
   \|A\mathbf{v}^{(k)} - \lambda^{(k)}\mathbf{v}^{(k)}\| < \tau \|A\|
   $$

3. **Angle between successive vectors:**
   $$
   \sin \angle(\mathbf{v}^{(k)}, \mathbf{v}^{(k-1)}) < \tau
   $$

4. **Linear system residual (for iterative solves):**
   $$
   \|(A - \sigma I)\mathbf{w} - \mathbf{v}\| < \tau
   $$

**Typical values:** \( \tau = 10^{-8} \) for double precision, \( \tau = 10^{-6} \) for iterative solves.

### Numerical Stability

**Ill-conditioning issues:** When \( \sigma \) very close to eigenvalue:
- Matrix \( A - \sigma I \) nearly singular
- Solution of linear system sensitive to rounding errors
- May need extended precision or iterative refinement

**Stabilization techniques:**
- Use iterative refinement after direct solve
- Apply orthogonal transformations for better conditioning
- Use higher precision arithmetic for critical steps

## Advantages and Limitations

### Strengths
1. **Finds any eigenvalue:** By appropriate choice of shift
2. **Rapid convergence:** Especially when shift close to eigenvalue (Rayleigh quotient iteration gives cubic convergence)
3. **High accuracy:** For eigenvectors, often more accurate than eigenvalues
4. **Sparse matrix friendly:** Only requires solving linear systems, not explicit inversion
5. **Memory efficient:** Only needs storage for matrix and few vectors

### Weaknesses
1. **Requires linear solves:** Can be expensive for large systems
2. **Need good shift:** Convergence slow if shift not near eigenvalue
3. **Factorization cost:** For direct methods, need to factor matrix for each new shift
4. **Only one eigenpair:** Finds only eigenpair closest to shift
5. **Ill-conditioning:** When shift very close to eigenvalue, linear system ill-conditioned

### Validity Range
- **Applicable when:** Matrix is diagonalizable, shift not exactly equal to eigenvalue
- **Not applicable when:** Matrix defective at eigenvalue of interest
- **Optimal for:** Computing specific eigenpairs when good shift available

## Advanced Topics

### Rayleigh Quotient Iteration

**Accelerated version:** Update shift each iteration using Rayleigh quotient

**Algorithm:**
1. Start with initial vector \( \mathbf{v}^{(0)} \), \( \|\mathbf{v}^{(0)}\| = 1 \)
2. For \( k = 0, 1, 2, \ldots \):
   a. \( \sigma^{(k)} = (\mathbf{v}^{(k)})^T A \mathbf{v}^{(k)} \)
   b. Solve \( (A - \sigma^{(k)} I) \mathbf{w}^{(k+1)} = \mathbf{v}^{(k)} \)
   c. \( \mathbf{v}^{(k+1)} = \mathbf{w}^{(k+1)} / \|\mathbf{w}^{(k+1)}\| \)

**Convergence:** Cubic for symmetric matrices, quadratic for non-symmetric.

### Generalized Eigenvalue Problems

**For \( A\mathbf{v} = \lambda B\mathbf{v} \):** Inverse iteration solves:
$$
(A - \sigma B) \mathbf{w} = B \mathbf{v}
$$

**Special cases:**
- \( B \) positive definite: Cholesky factorization for efficiency
- \( B \) singular: Use regularization or projected methods
- Generalized Rayleigh quotient: \( \sigma = \frac{\mathbf{v}^T A \mathbf{v}}{\mathbf{v}^T B \mathbf{v}} \)

### Block Inverse Iteration

**For multiple eigenvalues:** Simultaneously compute \( p \) eigenvectors

**Algorithm:**
1. Start with \( n \times p \) matrix \( V^{(0)} \) with orthonormal columns
2. For \( k = 0, 1, 2, \ldots \):
   a. Solve \( (A - \sigma I) W^{(k)} = V^{(k)} \)
   b. Orthogonalize \( W^{(k)} \): \( V^{(k+1)} R^{(k+1)} = W^{(k)} \) (QR factorization)
   c. Compute Rayleigh-Ritz approximation on \( V^{(k+1)} \)

**Applications:** Subspace iteration, computing eigenvalue clusters.

### Nonlinear Eigenvalue Problems

**For \( T(\lambda)\mathbf{v} = \mathbf{0} \):** Nonlinear inverse iteration:
1. Linearize around current approximation \( \lambda^{(k)} \)
2. Solve \( T(\lambda^{(k)}) \mathbf{w} = T'(\lambda^{(k)}) \mathbf{v}^{(k)} \)
3. Update eigenvector and eigenvalue

**Applications:** Damped vibration systems, delay differential equations.

## Special Cases and Examples

### Benchmark Problems

**Simple 3×3 symmetric matrix:**
$$
A = \begin{bmatrix}
2 & -1 & 0 \\
-1 & 2 & -1 \\
0 & -1 & 2
\end{bmatrix}
$$
Eigenvalues: \( \lambda = 2 - \sqrt{2}, 2, 2 + \sqrt{2} \approx 0.5858, 2.0000, 3.4142 \)

**Inverse iteration with \( \sigma = 0.6 \):**
- Converges to \( \lambda_1 \approx 0.5858 \), eigenvector \( \approx [0.5, 0.7071, 0.5]^T \)
- Convergence factor: \( \left| \frac{0.5858-0.6}{2.0-0.6} \right| \approx 0.0101 \) (fast)

**Inverse iteration with \( \sigma = 2.5 \):**
- Converges to \( \lambda_2 = 2.0 \), eigenvector \( \approx [0.7071, 0, -0.7071]^T \)
- Convergence factor: \( \left| \frac{2.0-2.5}{1.5858-2.5} \right| \approx 0.548 \) (slower)

### Analytical Solutions

**2×2 matrix analysis:** For \( A = \begin{bmatrix} a & b \\ c & d \end{bmatrix} \), shift \( \sigma \):

Eigenvalues: \( \lambda_{1,2} = \frac{a+d}{2} \pm \sqrt{\left(\frac{a-d}{2}\right)^2 + bc} \)

Inverse iteration convergence factor:
$$
\rho = \left| \frac{\lambda_1 - \sigma}{\lambda_2 - \sigma} \right|
$$

When \( \sigma = \lambda_1 + \epsilon \), \( \rho \approx \left| \frac{\epsilon}{\lambda_2 - \lambda_1} \right| \), very small for small \( \epsilon \).

### Industrial Applications

**Structural mode extraction for aircraft wing:**
- Matrix size: \( n \approx 10^6 \) DOFs from finite element model
- Desired: First bending mode (approx 2 Hz)
- Shift: \( \sigma = (2\pi \times 2)^2 \approx 157.9 \) rad²/s²
- Method: Preconditioned conjugate gradient for linear solves
- Result: Mode shape in 15 iterations, 2 hours compute time vs. 20 hours for full [[Modal Analysis]]

**Quantum chemistry calculation for excited state:**
- Hamiltonian matrix from basis set: \( n \approx 10^4 \)
- Desired: First excited state energy near -0.5 Hartree
- Shift: \( \sigma = -0.5 \)
- Method: Direct LU factorization (dense matrix)
- Result: Energy -0.4923 Hartree, wavefunction in 8 iterations

## Error Analysis

### Forward Error Analysis

**Error in eigenvector:** After \( k \) iterations:
$$
\|\mathbf{v}^{(k)} - \mathbf{v}_1\| \leq C \left| \frac{\lambda_1 - \sigma}{\lambda_2 - \sigma} \right|^k
$$

**Error in eigenvalue (Rayleigh quotient):**
$$
|\lambda^{(k)} - \lambda_1| \leq C' \left| \frac{\lambda_1 - \sigma}{\lambda_2 - \sigma} \right|^{2k}
$$

**Rayleigh quotient iteration:** Cubic convergence:
$$
|\lambda^{(k+1)} - \lambda_1| \leq C'' |\lambda^{(k)} - \lambda_1|^3
$$

### Backward Error Analysis

**Computed eigenpair \( (\tilde{\lambda}, \tilde{\mathbf{v}}) \):** There exists \( E \) with \( \|E\| = O(\epsilon \|A\|) \) such that:
$$
(A + E)\tilde{\mathbf{v}} = \tilde{\lambda}\tilde{\mathbf{v}}
$$
where \( \epsilon \) is machine precision.

**Linear solve error:** If linear system solved with residual \( \mathbf{r} \), then:
$$
(A - \sigma I)\tilde{\mathbf{w}} = \mathbf{v} + \mathbf{r}
$$
Affects convergence but method often tolerant to modest solve errors.

### Condition Number Effects

**Eigenvalue condition number:** For simple eigenvalue \( \lambda \):
$$
\kappa(\lambda) = \frac{\|\mathbf{x}\|\|\mathbf{y}\|}{|\mathbf{y}^T\mathbf{x}|}
$$
where \( \mathbf{x} \) right eigenvector, \( \mathbf{y} \) left eigenvector.

**Symmetric case:** \( \kappa(\lambda) = 1 \), optimal conditioning.

**Ill-conditioned eigenvalues:** Inverse iteration may need more iterations or higher precision.

## Relationship to Other Concepts

### Comparison with Power Method

**Power Method:**
- Finds dominant eigenvalue
- Only matrix-vector multiplications
- Linear convergence based on \( |\lambda_2/\lambda_1| \)

**Inverse Power Method:**
- Finds eigenvalue closest to shift
- Requires solving linear systems
- Linear convergence based on \( |(\lambda_1-\sigma)/(\lambda_2-\sigma)| \)
- Can be much faster with good shift

### Connection to Rayleigh Quotient Iteration

**Inverse iteration:** Fixed shift or occasionally updated

**Rayleigh quotient iteration:** Shift updated every iteration to current Rayleigh quotient

**Relationship:** Rayleigh quotient iteration is inverse iteration with optimal shift strategy.

### Integration with Lanczos/Arnoldi Methods

**Shift-and-invert transformation:** Used in implicitly restarted Arnoldi to compute eigenvalues near shift:
1. Apply Arnoldi to \( (A - \sigma I)^{-1} \)
2. Converges quickly to eigenvalues near \( \sigma \)
3. Basis for ARPACK software

### Relationship to Newton's Method

**Rayleigh quotient iteration** can be derived as Newton's method applied to:
$$
F(\mathbf{v}, \lambda) = \begin{bmatrix} (A - \lambda I)\mathbf{v} \\ \frac{1}{2}(1 - \mathbf{v}^T\mathbf{v}) \end{bmatrix} = \mathbf{0}
$$

**Connection:** Both have local cubic convergence for symmetric problems.

## Historical Context and Evolution

### Original Motivation

**Structural engineering needs:**
- Compute specific vibration modes of large structures
- Avoid full eigenvalue decomposition which was computationally prohibitive
- Early applications in aircraft and bridge design

**Quantum mechanics applications:**
- Compute specific energy states of atoms and molecules
- Ground state and excited state calculations
- Basis for many quantum chemistry methods

### Evolution Over Time

1. **1940s-1950s:** Initial development, theoretical analysis
2. **1960s-1970s:** Implementation in early scientific computing software
3. **1980s-1990s:** Integration with sparse linear solvers, preconditioning techniques
4. **2000s-2010s:** Parallel implementations, GPU acceleration
5. **2020s-present:** Integration with machine learning for shift prediction

### Modern Reformulations

- **Randomized inverse iteration:** Using random projections for very large problems
- **Streaming inverse iteration:** For data streams and online eigenvalue problems
- **Quantum inverse iteration:** For quantum computers using phase estimation
- **Federated inverse iteration:** For distributed data with privacy constraints

## Pedagogical Approach

### Teaching Strategies

1. **Contrast with Power Method:** Show how inversion allows targeting any eigenvalue
2. **Geometric interpretation:** Visualize convergence to eigenvector as linear system solutions
3. **Physical examples:** Vibration modes, quantum states
4. **Numerical experiments:** Implement, observe convergence rates for different shifts

### Common Misconceptions

1. **"Inverse iteration requires matrix inversion":** Actually solves linear systems, not explicit inversion
2. **"Always converges to closest eigenvalue":** Only if initial vector has component in that direction
3. **"Rayleigh quotient iteration always converges":** May converge to different eigenvalue if initial guess poor
4. **"Need exact factorization":** Iterative linear solvers with sufficient accuracy work well

### Learning Resources

**Foundational Texts:**
- Golub & Van Loan, "Matrix Computations"
- Parlett, "The Symmetric Eigenvalue Problem"
- Saad, "Numerical Methods for Large Eigenvalue Problems"
- Watkins, "Fundamentals of Matrix Computations"

**Online Resources:**
- MIT OpenCourseWare 18.335: Numerical Linear Algebra
- NLAFET Educational Resources on Eigenvalue Algorithms
- Wikipedia: "Inverse iteration" with examples and pseudocode
- YouTube: Visualizations of inverse iteration convergence

**Software Tutorials:**
- MATLAB: Inverse iteration implementation examples
- Python/SciPy: Using sparse linear solvers with inverse iteration
- LAPACK: Reference implementations in FORTRAN
- SLEPc: Parallel eigenvalue solver tutorial

## Implementation in Software

### MATLAB Implementation

```matlab
function [lambda, v, iter] = inverse_power_method(A, sigma, v0, maxiter, tol, use_rayleigh)
    % Inverse Power Method / Rayleigh Quotient Iteration
    % Inputs:
    %   A: n x n matrix
    %   sigma: initial shift (scalar)
    %   v0: initial vector (n x 1)
    %   maxiter: maximum iterations
    %   tol: convergence tolerance
    %   use_rayleigh: true for Rayleigh quotient iteration
    % Outputs:
    %   lambda: computed eigenvalue
    %   v: computed eigenvector
    %   iter: number of iterations performed
    
    n = size(A, 1);
    v = v0 / norm(v0);
    lambda_old = sigma;
    current_sigma = sigma;
    
    % Precompute factorization if shift fixed
    if ~use_rayleigh
        [L, U, P] = lu(A - sigma * eye(n));
    end
    
    for iter = 1:maxiter
        % Update shift for Rayleigh quotient iteration
        if use_rayleigh
            current_sigma = v' * A * v;  % Rayleigh quotient
            % Recompute factorization if shift changed significantly
            if iter == 1 || abs(current_sigma - lambda_old) > 0.1 * abs(lambda_old)
                [L, U, P] = lu(A - current_sigma * eye(n));
            end
        end
        
        % Solve linear system (A - sigma*I)w = v
        w = U \ (L \ (P * v));
        
        % Normalize
        v = w / norm(w);
        
        % Compute Rayleigh quotient
        lambda = v' * A * v;
        
        % Check convergence
        if abs(lambda - lambda_old) < tol * abs(lambda)
            break;
        end
        
        lambda_old = lambda;
    end
    
    % Ensure eigenpair satisfies Ax = lambda x accurately
    lambda = v' * (A * v);
end

% Example usage:
% A = gallery('tridiag', 100, -1, 2, -1);  % Tridiagonal matrix
% v0 = randn(100, 1);
% [lambda, v, iter] = inverse_power_method(A, 0.5, v0, 100, 1e-8, true);
```

### Python Implementation

```python
import numpy as np
from scipy.linalg import lu_factor, lu_solve, norm
from scipy.sparse.linalg import splu, spsolve

def inverse_power_method(A, sigma, v0=None, max_iter=100, tol=1e-8, 
                         use_rayleigh=False, sparse=False):
    """
    Inverse Power Method with optional Rayleigh quotient iteration
    
    Parameters
    ----------
    A : array or sparse matrix
        Input matrix (n x n)
    sigma : float
        Initial shift
    v0 : array, optional
        Initial vector (n,)
    max_iter : int
        Maximum iterations
    tol : float
        Convergence tolerance
    use_rayleigh : bool
        If True, update shift using Rayleigh quotient
    sparse : bool
        If True, use sparse linear algebra
        
    Returns
    -------
    lambda_est : float
        Estimated eigenvalue
    v : array
        Estimated eigenvector
    n_iter : int
        Number of iterations
    """
    n = A.shape[0]
    
    # Initial vector
    if v0 is None:
        v = np.random.randn(n)
    else:
        v = v0.copy()
    v = v / norm(v)
    
    # Initial values
    lambda_old = sigma
    current_sigma = sigma
    
    # Prepare linear solver
    if sparse:
        # For sparse matrices
        if use_rayleigh:
            # Will update factorization if needed
            solver_info = {'factorization': None, 'last_sigma': None}
        else:
            M = A - sigma * sparse.eye(n)
            solver = splu(M.tocsc())
            solve = lambda b: solver.solve(b)
    else:
        # For dense matrices
        if use_rayleigh:
            solver_info = {'lu': None, 'piv': None, 'last_sigma': None}
        else:
            M_dense = A - sigma * np.eye(n)
            lu, piv = lu_factor(M_dense)
            solve = lambda b: lu_solve((lu, piv), b)
    
    for n_iter in range(1, max_iter + 1):
        # Update shift for Rayleigh quotient iteration
        if use_rayleigh:
            current_sigma = v @ A @ v  # Rayleigh quotient
            
            # Update factorization if shift changed significantly
            update_factorization = False
            if n_iter == 1 or abs(current_sigma - lambda_old) > 0.1 * abs(lambda_old):
                update_factorization = True
            
            if sparse:
                if update_factorization or solver_info['factorization'] is None:
                    M = A - current_sigma * sparse.eye(n)
                    solver_info['factorization'] = splu(M.tocsc())
                    solver_info['last_sigma'] = current_sigma
                solve = lambda b: solver_info['factorization'].solve(b)
            else:
                if update_factorization or solver_info['lu'] is None:
                    M_dense = A - current_sigma * np.eye(n)
                    solver_info['lu'], solver_info['piv'] = lu_factor(M_dense)
                    solver_info['last_sigma'] = current_sigma
                solve = lambda b: lu_solve((solver_info['lu'], solver_info['piv']), b)
        
        # Solve (A - sigma*I)w = v
        w = solve(v)
        
        # Normalize
        v = w / norm(w)
        
        # Compute Rayleigh quotient
        if sparse:
            lambda_est = v @ A.dot(v)
        else:
            lambda_est = v @ (A @ v)
        
        # Check convergence
        if abs(lambda_est - lambda_old) < tol * abs(lambda_est):
            break
        
        lambda_old = lambda_est
    
    # Final Rayleigh quotient
    if sparse:
        lambda_est = v @ A.dot(v)
    else:
        lambda_est = v @ (A @ v)
    
    return lambda_est, v, n_iter

# Generalized eigenvalue problem version
def generalized_inverse_power_method(A, B, sigma, v0=None, max_iter=100, tol=1e-8):
    """
    Inverse Power Method for generalized eigenvalue problem A*x = lambda*B*x
    """
    n = A.shape[0]
    
    if v0 is None:
        v = np.random.randn(n)
    else:
        v = v0.copy()
    v = v / norm(v)
    
    lambda_old = sigma
    
    # Factor (A - sigma*B) for efficiency
    M = A - sigma * B
    lu, piv = lu_factor(M)
    
    for n_iter in range(1, max_iter + 1):
        # Solve (A - sigma*B)w = B*v
        b = B @ v
        w = lu_solve((lu, piv), b)
        
        # Normalize
        v = w / norm(w)
        
        # Generalized Rayleigh quotient
        lambda_est = (v @ A @ v) / (v @ B @ v)
        
        # Check convergence
        if abs(lambda_est - lambda_old) < tol * abs(lambda_est):
            break
        
        lambda_old = lambda_est
    
    return lambda_est, v, n_iter
```

### Commercial Software Features

**MATLAB:**
- `eigs(A, k, sigma)`: Computes k eigenvalues closest to sigma using shift-and-invert Arnoldi
- Custom implementations using `lu` and backslash operator
- Parallel computing toolbox for distributed inverse iteration

**Python SciPy:**
- `scipy.sparse.linalg.eigs(A, k, sigma)`: ARPACK wrapper for eigenvalues near sigma
- `scipy.linalg.eig()`: Dense eigenvalue solver with optional subset selection
- Custom implementations with `scipy.sparse.linalg.splu` for sparse matrices

**Intel MKL:**
- PARDISO sparse direct solver for efficient linear system solutions
- Optimized BLAS for matrix operations in dense case
- Parallel implementation for multicore processors

**ANSYS:**
- [[Modal Analysis]] with shift option for specific frequency ranges
- Lanczos solver with shift-and-invert for large eigenvalue problems
- GPU acceleration for matrix operations

## See Also

- [[Power Method]]
- Rayleigh Quotient Iteration
- Shift-and-Invert Transformation
- [[Lanczos Method]]
- [[Arnoldi Method]]
- [[Generalized Eigenvalue Problem]]
- [[Eigenvalue Problem]]
- Spectral Transformation
- Deflation Method
- [[Subspace Iteration Method]]
- Newton's Method
- Condition Number
- Linear System Solution
- Preconditioning
- Sparse Matrix
- [[Numerical Linear Algebra]]
- Vibration Analysis
- [[Quantum Mechanics]]

---

*Note: The Inverse Power Method is a fundamental algorithm in numerical linear algebra that transforms the challenge of computing specific eigenvalues into a sequence of linear system solutions. Its ability to converge rapidly to eigenvalues near a specified shift, especially when combined with Rayleigh quotient updates, makes it indispensable for applications ranging from structural dynamics to quantum chemistry where specific eigenpairs are of interest.*
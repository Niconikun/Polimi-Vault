## Formal Definition

The **Mode Displacement Method** is a [[Modal Superposition]] technique used in [[Structural Dynamics]] to compute the dynamic response of linear systems by expressing the physical displacements as a linear combination of the system's mode shapes. This method directly uses the modal coordinates to represent the [[Displacement Field]], providing an efficient and accurate approach for solving dynamic response problems when only a limited number of modes contribute significantly to the response. MDM is particularly valuable for large-scale structural systems where full time-history analysis would be computationally prohibitive.

## Historical Development

### Key Milestones
- **1920s:** Development of [[Modal Analysis]] theory by Lord Rayleigh and others
- **1940s:** Formalization of [[Modal Superposition]] methods for structural dynamics
- **1960s:** Implementation in early finite element software for earthquake engineering
- **1970s:** Development of numerical algorithms for efficient modal extraction
- **1980s:** Comparison studies with [[Mode Acceleration Method (MAM)]] establishing relative merits
- **1990s:** Extension to nonlinear systems and adaptive modal truncation
- **2000s:** Implementation in commercial finite element packages with automated mode selection

### Foundational Contributors
1. **Lord Rayleigh (1842-1919):** Developed Rayleigh's quotient and foundational modal concepts
2. **Ray W. Clough (1920-2016):** Advanced finite element methods and [[Modal Analysis]] techniques
3. **Edward L. Wilson (b. 1931):** Developed numerical methods for [[Modal Analysis]] in structural dynamics
4. **Klaus-Jürgen Bathe (b. 1943):** Contributed to modal superposition methods in [[Finite Element Analysis (FEA)]]

## Mathematical Formulation

### Basic Formulation

For a linear dynamic system with $n$ [[degrees of freedom]], the equation of motion is:
$$
\mathbf{M}\ddot{\mathbf{u}} + \mathbf{C}\dot{\mathbf{u}} + \mathbf{K}\mathbf{u} = \mathbf{F}(t)
$$

Using modal transformation $\mathbf{u} = \boldsymbol{\Phi}\mathbf{q}$, where $\boldsymbol{\Phi}$ is the modal matrix containing $m$ mode shapes ($m \ll n$):

**Modal equations:**
$$
\mathbf{I}\ddot{\mathbf{q}} + \boldsymbol{\Xi}\dot{\mathbf{q}} + \boldsymbol{\Omega}^2\mathbf{q} = \boldsymbol{\Phi}^T\mathbf{F}(t)
$$

where:
- $\mathbf{I}$ = identity matrix (modal mass normalization)
- $\boldsymbol{\Xi} = \text{diag}(2\zeta_i\omega_i)$ = modal damping matrix
- $\boldsymbol{\Omega}^2 = \text{diag}(\omega_i^2)$ = diagonal matrix of squared natural frequencies
- $\mathbf{q}(t)$ = modal coordinates

### Modal Coordinate Solution

Each modal coordinate satisfies:
$$
\ddot{q}_i(t) + 2\zeta_i\omega_i\dot{q}_i(t) + \omega_i^2 q_i(t) = f_i(t)
$$

where $f_i(t) = \boldsymbol{\phi}_i^T\mathbf{F}(t)$ is the modal force.

**Time-domain solution (Duhamel's integral):**
$$
q_i(t) = \frac{1}{\omega_{di}} \int_0^t f_i(\tau) e^{-\zeta_i\omega_i(t-\tau)} \sin[\omega_{di}(t-\tau)] d\tau + \text{initial condition terms}
$$

where $\omega_{di} = \omega_i\sqrt{1-\zeta_i^2}$.

### Displacement Recovery

Physical displacements are recovered via superposition:
$$
\mathbf{u}(t) = \sum_{i=1}^m \boldsymbol{\phi}_i q_i(t)
$$

**Matrix form:**
$$
\mathbf{u}(t) = \boldsymbol{\Phi}_m \mathbf{q}(t)
$$
where $\boldsymbol{\Phi}_m$ contains the first $m$ mode shapes.

## Fundamental Principles

### Modal Superposition Principle

**Key assumption:** Dynamic response can be approximated by superposition of a limited number of dominant modes:
$$
\mathbf{u}(t) \approx \sum_{i=1}^m \boldsymbol{\phi}_i q_i(t), \quad m \ll n
$$

**Modal truncation criteria:**
1. **Frequency cut-off:** Include all modes with $\omega_i \leq \omega_{\max}$
2. **Mass participation:** Include modes until $\sum_{i=1}^m \Gamma_i^2 \geq$ target percentage
3. **Energy criteria:** Based on modal strain energy participation

### Orthogonality Conditions

Mode shapes satisfy:
$$
\boldsymbol{\phi}_i^T\mathbf{M}\boldsymbol{\phi}_j = \delta_{ij} \quad \text{(mass orthonormalization)}
$$
$$
\boldsymbol{\phi}_i^T\mathbf{K}\boldsymbol{\phi}_j = \omega_i^2\delta_{ij}
$$
$$
\boldsymbol{\phi}_i^T\mathbf{C}\boldsymbol{\phi}_j = 2\zeta_i\omega_i\delta_{ij} \quad \text{(for proportional [[damping]])}
$$

### Mode Selection Criteria

**Modal effectiveness index:**
$$
\eta_i = \frac{|\boldsymbol{\phi}_i^T\mathbf{F}|}{\omega_i^2}
$$

**Mass participation factor:**
$$
\Gamma_i = \frac{\boldsymbol{\phi}_i^T\mathbf{M}\mathbf{r}}{\boldsymbol{\phi}_i^T\mathbf{M}\boldsymbol{\phi}_i}
$$
where $\mathbf{r}$ is influence vector for specific loading direction.

## Theoretical Framework

### Reduced-Order Modeling

MDM creates reduced-order model:
- **Full model:** $n$ DOFs, dense matrices
- **Reduced model:** $m$ modal coordinates, diagonal matrices
- **Computational savings:** $O(m)$ vs $O(n)$ for each time step

### Time Integration of Modal Equations

**Decoupled system advantages:**
- Each modal equation solved independently
- Different time steps can be used for different frequency ranges
- Analytical solutions available for many forcing functions

**Numerical integration options:**
- **Exact solution:** For piecewise linear forcing
- **Newmark-β method:** For general forcing
- **[[Runge-Kutta Methods]]:** For nonlinear modal forces
- **State-space methods:** For first-order form

### Frequency Domain Implementation

For harmonic loading $\mathbf{F}(t) = \mathbf{F}_0 e^{i\omega t}$:
$$
\mathbf{u}(\omega) = \sum_{i=1}^m \frac{\boldsymbol{\phi}_i\boldsymbol{\phi}_i^T\mathbf{F}_0}{\omega_i^2 - \omega^2 + i2\zeta_i\omega_i\omega}
$$

**Steady-state response:**
$$
\mathbf{u}(t) = \text{Re}\left[\sum_{i=1}^m \frac{\boldsymbol{\phi}_i\boldsymbol{\phi}_i^T\mathbf{F}_0 e^{i\omega t}}{\omega_i^2 - \omega^2 + i2\zeta_i\omega_i\omega}\right]
$$

## Classification and Variants

### By Modal Selection Approach
1. **Fixed mode count:** Prespecified number of modes
2. **Frequency-based:** All modes below cutoff frequency
3. **Participation-based:** Based on modal participation factors
4. **Adaptive selection:** Modes selected based on excitation characteristics

### By Damping Treatment
1. **Proportional damping:** Classical modal damping
2. **Non-proportional damping:** Complex mode superposition
3. **[[Rayleigh Damping]]:** $\mathbf{C} = \alpha\mathbf{M} + \beta\mathbf{K}$
4. **Modal damping:** Direct specification of $\zeta_i$

### By Implementation Strategy
1. **Direct MDM:** Standard formulation as described
2. **Enhanced MDM:** With static correction or residual flexibility
3. **Block Lanczos MDM:** For very large systems
4. **Component Mode MDM:** Using component mode synthesis

### By Application Domain
1. **Seismic analysis:** Response spectrum or time history
2. **Wind engineering:** [[Random Vibration]] analysis
3. **Machinery dynamics:** Harmonic and transient analysis
4. **Wave propagation:** High-frequency vibration

## Derivation and Proof

### Step-by-Step Derivation

**Step 1: [[Eigenvalue Problem]] solution**
Solve undamped eigenvalue problem:
$$
\mathbf{K}\boldsymbol{\phi}_i = \omega_i^2\mathbf{M}\boldsymbol{\phi}_i
$$
for $i = 1, 2, \ldots, m$.

**Step 2: Modal transformation**
Define transformation matrix $\boldsymbol{\Phi} = [\boldsymbol{\phi}_1, \boldsymbol{\phi}_2, \ldots, \boldsymbol{\phi}_m]$
and coordinate transformation:
$$
\mathbf{u} = \boldsymbol{\Phi}\mathbf{q}
$$

**Step 3: Project equations onto modal subspace**
Premultiply equation of motion by $\boldsymbol{\Phi}^T$:
$$
\boldsymbol{\Phi}^T\mathbf{M}\boldsymbol{\Phi}\ddot{\mathbf{q}} + \boldsymbol{\Phi}^T\mathbf{C}\boldsymbol{\Phi}\dot{\mathbf{q}} + \boldsymbol{\Phi}^T\mathbf{K}\boldsymbol{\Phi}\mathbf{q} = \boldsymbol{\Phi}^T\mathbf{F}(t)
$$

**Step 4: Apply orthogonality conditions**
Assuming mass-normalized modes ($\boldsymbol{\phi}_i^T\mathbf{M}\boldsymbol{\phi}_i = 1$) and proportional damping:
$$
\mathbf{I}\ddot{\mathbf{q}} + \text{diag}(2\zeta_i\omega_i)\dot{\mathbf{q}} + \text{diag}(\omega_i^2)\mathbf{q} = \boldsymbol{\Phi}^T\mathbf{F}(t)
$$

**Step 5: Decoupled equations**
$$
\ddot{q}_i + 2\zeta_i\omega_i\dot{q}_i + \omega_i^2 q_i = f_i(t), \quad i = 1, 2, \ldots, m
$$
where $f_i(t) = \boldsymbol{\phi}_i^T\mathbf{F}(t)$.

### Convergence Proof

**Error bound for modal truncation:**
Let $\mathbf{u}_{\text{exact}} = \sum_{i=1}^n \boldsymbol{\phi}_i q_i$ and $\mathbf{u}_m = \sum_{i=1}^m \boldsymbol{\phi}_i q_i$.

**Energy norm error:**
$$
\|\mathbf{u}_{\text{exact}} - \mathbf{u}_m\|_E \leq \frac{1}{\omega_{m+1}^2} \|\mathbf{F} - \mathbf{F}_m\|
$$
where $\mathbf{F}_m$ is projection of $\mathbf{F}$ onto spanned subspace.

**Proof:** Using orthogonality and Bessel's inequality in energy inner product space.

## Physical Interpretation

### Modal Filtering Concept

Each mode acts as a mechanical filter:
- **Low-pass characteristic:** Higher modes less excited for smooth loads
- **Frequency-dependent amplification:** Near resonance, specific modes dominate
- **Spatial filtering:** Modes capture specific deformation patterns

### Energy Distribution

**Modal energy decomposition:**
$$
E_{\text{total}} = \sum_{i=1}^m E_i
$$
where $E_i = \frac{1}{2}\dot{q}_i^2 + \frac{1}{2}\omega_i^2 q_i^2$ is energy in mode $i$.

**Participation visualization:**
- Pie charts showing modal energy contributions
- Time histories of modal energies
- Cumulative energy plots

### Wave Propagation Perspective

For distributed systems:
- **Low modes:** Global, long wavelength deformations
- **High modes:** Local, short wavelength deformations
- **Cutoff frequency:** Minimum frequency for wave propagation in discretized system

## Applications

### Engineering Disciplines
1. **Earthquake Engineering:** Seismic response analysis of buildings and bridges
2. **Aerospace Engineering:** Dynamic response of aircraft and spacecraft structures
3. **Mechanical Engineering:** [[Vibration analysis]] of machinery and rotating equipment
4. **Civil Engineering:** Wind-induced vibration of tall structures
5. **Nuclear Engineering:** Seismic qualification of nuclear power plant components

### Scientific Fields
1. **Geophysics:** Ground motion amplification studies
2. **Acoustics:** Structural-acoustic interaction problems
3. **Biomechanics:** Bone and tissue [[vibration analysis]]
4. **Materials Science:** Dynamic characterization of composites

### Practical Implementations
- **Building seismic design:** Response spectrum analysis
- **Offshore platform analysis:** Wave loading response
- **Automotive NVH analysis:** Road and engine vibration
- **Turbomachinery analysis:** Blade vibration under aerodynamic loads
- **Satellite deployment analysis:** Dynamic loads during launch

## Implementation Considerations

### Modal Extraction Methods

**Eigensolvers for large systems:**
1. **Subspace iteration:** For few lowest modes
2. **[[Lanczos Method]]:** Efficient for large sparse matrices
3. **AMSES (Automated Multi-level Substructuring):** For very large problems
4. **Block Lanczos:** For clustered eigenvalues

**Computational complexity:**
- **Dense matrices:** $O(n^3)$ for full solution, $O(n^2m)$ for subspace methods
- **Sparse matrices:** $O(n^{1.5})$ to $O(n^2)$ depending on sparsity
- **Parallel computation:** Modes can be extracted in parallel

### Mode Selection Strategy

**Systematic approach:**
1. **Initial estimate:** Based on cutoff frequency $f_{\max} = \kappa f_{\text{max excitation}}$
   Typically $\kappa = 1.5$ to $3.0$
2. **Mass participation check:** Ensure sufficient mass participation in each direction
3. **Effectiveness verification:** Check modal loads $|f_i|$ for given excitation
4. **Convergence test:** Compare responses with increasing number of modes

**Automatic selection algorithms:**
- Based on modal [[Kinetic Energy]]
- Based on [[Strain Energy]] participation
- Based on force projection norms

### Numerical Implementation Details

**Time integration of modal equations:**
```python
# Pseudocode for modal time integration
def modal_time_integration(phi, omega, zeta, F, dt, nsteps):
    m = phi.shape[1]  # Number of modes
    q = np.zeros((nsteps, m))
    qdot = np.zeros((nsteps, m))
    
    # Modal forces
    f_modal = phi.T @ F
    
    for i in range(m):
        # Solve SDOF system for each mode
        q[:, i], qdot[:, i] = solve_sdof(omega[i], zeta[i], f_modal[i,:], dt)
    
    # Recover physical response
    u = phi @ q.T  # nDOF × nsteps
    return u, q
```

**Efficient recovery of secondary quantities:**
- **Stresses:** $\boldsymbol{\sigma}(t) = \sum_{i=1}^m \boldsymbol{\sigma}_i q_i(t)$ where $\boldsymbol{\sigma}_i$ are modal stresses
- **Forces:** Modal contribution to element forces
- **Reactions:** Modal contribution to support reactions

## Advantages and Limitations

### Strengths
1. **Computational efficiency:** $O(m)$ vs $O(n)$ operations per time step
2. **Physical insight:** Modal contributions clearly identifiable
3. **Adaptive accuracy:** Can increase modes until convergence
4. **Parallelization:** Independent solution of modal equations
5. **Reusability:** Once modes extracted, can be used for multiple load cases

### Weaknesses
1. **Modal truncation error:** Neglected higher modes may be important
2. **Poor convergence for:** Localized loads, impact, high-frequency content
3. **Damping limitations:** Assumes proportional damping for real modes
4. **Nonlinearity limitation:** Only applicable to linear or linearized systems
5. **Initial cost:** Modal extraction can be expensive for very large systems

### Validity Range
- **Applicable when:** System is linear, damping is proportional or light
- **Not applicable when:** Strong nonlinearities, non-proportional heavy damping
- **Optimal for:** Systems with well-separated modes, smooth loading

## Advanced Topics

### Residual Flexibility Corrections

**Static correction:** Account for contribution of truncated modes:
$$
\mathbf{u}(t) = \sum_{i=1}^m \boldsymbol{\phi}_i q_i(t) + \mathbf{u}_{\text{static}}
$$

where $\mathbf{u}_{\text{static}} = \mathbf{K}^{-1}\mathbf{F}(t) - \sum_{i=1}^m \frac{\boldsymbol{\phi}_i\boldsymbol{\phi}_i^T}{\omega_i^2}\mathbf{F}(t)$.

**Modal Acceleration Method (MAM):** Alternative formulation with better convergence.

### Nonlinear Extension

**Modal-based nonlinear methods:**
1. **Modal derivative approach:** Account for geometric nonlinearity
2. **Enriched basis methods:** Include modal derivatives in basis
3. **Reduced-order modeling:** Proper orthogonal decomposition (POD)
4. **Implicit condensation:** System equivalent reduction expansion process (SEREP)

### Stochastic Dynamics

**[[Random Vibration]] via MDM:** For Gaussian random excitation:
- **Modal cross-correlations:** Important for closely spaced modes
- **Complete quadratic combination (CQC):** For modal response combination
- **Power spectral density:** Modal decomposition of response PSD

### Component Mode Synthesis Integration

**MDM with CMS:**
1. Extract component modes via Craig-Bampton or similar
2. Assemble reduced system matrices
3. Perform MDM on reduced system
4. Expand to full physical coordinates

## Special Cases and Examples

### Benchmark Problems

**Cantilever beam under tip load:**
- **System:** Steel beam, length $L = 2$ m, $E = 200$ GPa, $I = 1\times10^{-6}$ m⁴
- **Loading:** Triangular pulse force at tip, duration $0.1$ s, peak $1000$ N
- **Modal convergence:** Tip displacement vs number of modes included:

| Modes Included | Tip Displacement (mm) | Error vs 10 modes |
|----------------|----------------------|-------------------|
| 1              | 15.2                 | 25%               |
| 3              | 19.1                 | 6%                |
| 5              | 20.1                 | 1%                |
| 10             | 20.3                 | 0%                |

**Seismic analysis of 10-story building:**
- **Model:** Shear building with uniform story mass and stiffness
- **Excitation:** El Centro 1940 NS earthquake record
- **Mode selection:** First 3 modes capture 85% mass participation
- **Results:** Inter-story drifts within 5% of direct integration

### Analytical Solutions

**Simply supported beam with moving load:**
Load $F$ moving at constant velocity $v$:
$$
u(x,t) = \sum_{i=1}^\infty \phi_i(x) q_i(t)
$$
where $\phi_i(x) = \sin(i\pi x/L)$ and
$$
q_i(t) = \frac{2F}{\rho AL\omega_i^2} \left[ \sin(\omega_i t) - \frac{\omega_i}{\omega_{di}} \sin(\omega_{di}t) e^{-\zeta_i\omega_i t} \right]
$$
for $\omega_{di} = \sqrt{\omega_i^2 - (i\pi v/L)^2}$.

### Design Examples

**Machine foundation isolation:**
- **Problem:** Reduce vibration transmission from rotating machinery
- **Solution:** Use MDM to identify dominant transmission paths
- **Design:** Tuned mass damper designed based on modal properties
- **Verification:** Experimental [[Modal Analysis]] confirms predicted modes

**Building retrofit for seismic upgrade:**
- **Existing structure:** Identify deficient modes via MDM
- **Retrofit design:** Add braces to stiffen specific modes
- **Verification:** Updated MDM shows improved performance

## Error Analysis

### Modal Truncation Error

**Error measure:**
$$
\varepsilon_m = \frac{\|\mathbf{u}_{\text{exact}} - \mathbf{u}_m\|}{\|\mathbf{u}_{\text{exact}}\|}
$$

**Theoretical bound:** For static correction:
$$
\varepsilon_m \leq \frac{\|\mathbf{F} - \mathbf{P}_m\mathbf{F}\|}{\omega_{m+1}^2}
$$
where $\mathbf{P}_m$ projects onto first $m$ modes.

**Practical estimation:**
1. **Modal contribution factor:** $C_i = |q_i| \|\boldsymbol{\phi}_i\|$
2. **Cumulative contribution:** $\sum_{i=1}^m C_i / \sum_{i=1}^n C_i$
3. **Energy ratio:** Modal strain energy participation

### Numerical Errors

**Eigensolver accuracy:**
- **Tolerance settings:** Typically $10^{-6}$ to $10^{-8}$ for frequencies
- **Orthogonality check:** $\max|\boldsymbol{\phi}_i^T\mathbf{M}\boldsymbol{\phi}_j| < \text{tol}$
- **Mass normalization accuracy**

**Time integration errors:**
- **Modal equation integration:** Typically higher order than direct integration
- **Stability:** Unconditionally stable for exact SDOF solution
- **Accuracy:** Controlled by modal frequency and time step

### Parameter Sensitivity

**Sensitivity to damping:**
$$
\frac{\partial u}{\partial \zeta_i} = -\frac{2\omega_i q_i}{\omega_{di}} \boldsymbol{\phi}_i \int_0^t \tau f_i(\tau) e^{-\zeta_i\omega_i(t-\tau)} \cos[\omega_{di}(t-\tau)] d\tau
$$

**Most sensitive when:** $\omega \approx \omega_i$ (near resonance)

## Relationship to Other Concepts

### Comparison with [[Mode Acceleration Method (MAM)]]

**MDM:**
- Direct displacement computation
- Good for displacement-dominated problems
- Requires many modes for force convergence

**MAM:**
- Computes acceleration then integrates for displacement
- Better convergence for forces and stresses
- Includes static correction implicitly

**Hybrid methods:** Combine advantages of both approaches.

### Connection to Direct Integration Methods

**MDM advantages:**
- Larger time steps possible (modal filtering)
- Parallel computation of modal equations
- Selective inclusion of high-frequency content

**Direct integration advantages:**
- No modal extraction cost
- Handles nonlinearities directly
- No modal truncation error

### Relationship to Response Spectrum Analysis

**Response spectrum method:** Uses MDM concepts:
1. Modal decomposition of excitation
2. SDOF response for each mode (from spectrum)
3. Modal combination rules (SRSS, CQC)

**MDM for time history:** Generalization to arbitrary loading.

### Connection to Model Reduction Techniques

**Proper Orthogonal Decomposition (POD):**
- Data-driven basis vs physics-based (modal) basis
- POD optimal for specific loading
- Modes optimal for free vibration

**Krylov subspace methods:** Moment-matching vs modal superposition.

## Historical Context and Evolution

### Original Motivation

**Early structural dynamics:**
- Need for efficient seismic analysis methods
- Limited computational resources in 1960s-1970s
- Development of [[Finite Element Method]] created large systems needing reduction

**Military applications:**
- Aircraft and missile dynamic response
- Nuclear weapon effects on structures
- Ship [[vibration analysis]]

### Evolution Over Time

1. **1960s:** Basic modal superposition implemented in early FEM codes
2. **1970s:** Comparison studies with direct integration methods
3. **1980s:** Development of component mode synthesis methods
4. **1990s:** Adaptive modal selection, error estimation
5. **2000s:** Integration with model reduction techniques
6. **2010s:** GPU acceleration, real-time applications

### Modern Reformulations

- **[[Dynamic Substructuring]]:** MDM applied to component-level models
- **Parametric model order reduction:** For design optimization
- **Machine learning enhancements:** Neural networks for mode selection
- **Digital twin integration:** Real-time modal updating from sensor data

## Pedagogical Approach

### Teaching Strategies

1. **Step-by-step development:** From SDOF to MDOF to modal superposition
2. **Physical demonstrations:** Simple beam experiments showing mode contributions
3. **Computer laboratories:** MATLAB/ANSYS implementations
4. **Case studies:** Real-world applications showing efficiency gains

### Common Misconceptions

1. **"All modes must be included":** Actually, few modes often sufficient
2. **"MDM only works for harmonic loading":** Works for any loading
3. **"Modal damping is arbitrary":** Should be based on experimental data or material properties
4. **"MDM eliminates high-frequency content":** Only if those modes are truncated

### Learning Resources

**Foundational Texts:**
- Clough and Penzien, "Dynamics of Structures"
- Bathe, "Finite Element Procedures"
- Craig and Kurdila, "Fundamentals of Structural Dynamics"
- Chopra, "Dynamics of Structures: Theory and Applications to Earthquake Engineering"

**Online Resources:**
- MIT OpenCourseWare: Structural Dynamics
- NAFEMS Benchmark Studies on Modal Methods
- ANSYS Learning Hub: Modal Analysis Tutorials
- Wolfram Demonstrations: Modal Superposition

**Software Tutorials:**
- ABAQUS: Modal Dynamics Analysis
- SAP2000: Modal Time History Analysis
- OpenSees: Modal Analysis Commands
- MATLAB: Modal Analysis Toolbox

## Implementation in Software

### MATLAB Implementation

```matlab
function [u, t] = modeDisplacementMethod(M, K, C, F, t_vec, n_modes)
    % MDM implementation for linear dynamic analysis
    % Inputs:
    %   M, K, C: Mass, stiffness, damping matrices
    %   F: Force matrix (nDOF x nsteps)
    %   t_vec: Time vector
    %   n_modes: Number of modes to include
    
    % Solve eigenvalue problem for first n_modes
    [phi, omega2] = eigs(K, M, n_modes, 'sm');
    omega = sqrt(diag(omega2));
    
    % Mass normalize mode shapes
    for i = 1:n_modes
        phi(:,i) = phi(:,i) / sqrt(phi(:,i)'*M*phi(:,i));
    end
    
    % Modal damping (assuming [[Rayleigh damping]])
    alpha = 0.01; beta = 0.001;
    zeta = alpha./(2*omega) + beta*omega/2;
    
    % Project forces onto modal coordinates
    F_modal = phi' * F;
    
    % Time integration for each modal coordinate
    nsteps = length(t_vec);
    q = zeros(n_modes, nsteps);
    
    for i = 1:n_modes
        % Solve SDOF equation for mode i
        [~, q_i] = ode45(@(t,q) modalEquation(t, q, omega(i), zeta(i), ...
                        t_vec, F_modal(i,:)), t_vec, [0; 0]);
        q(i,:) = q_i(:,1)';
    end
    
    % Recover physical displacements
    u = phi * q;
end

function dqdt = modalEquation(t, q, omega, zeta, t_vec, f_modal)
    % SDOF modal equation
    f_interp = interp1(t_vec, f_modal, t);
    dqdt = [q(2); 
            f_interp - 2*zeta*omega*q(2) - omega^2*q(1)];
end
```

### Python with SciPy

```python
import numpy as np
from scipy.linalg import eigh
from scipy.integrate import solve_ivp

def mode_displacement_method(M, K, F, t, n_modes=10, damping_ratio=0.02):
    """
    MDM implementation for structural dynamics
    """
    # Solve eigenvalue problem
    vals, vecs = eigh(K, M, subset_by_index=[0, n_modes-1])
    omega = np.sqrt(vals)
    
    # Mass normalize eigenvectors
    for i in range(n_modes):
        m_i = vecs[:, i] @ M @ vecs[:, i]
        vecs[:, i] = vecs[:, i] / np.sqrt(m_i)
    
    # Modal forces
    F_modal = vecs.T @ F
    
    # Time integration for modal coordinates
    n_dof, n_steps = F.shape
    q = np.zeros((n_modes, n_steps))
    
    for i in range(n_modes):
        # Define modal equation
        def modal_eq(t, y, omega_i=omega[i], zeta_i=damping_ratio):
            # Interpolate modal force
            f_idx = np.searchsorted(t_array, t, side='right') - 1
            f_i = F_modal[i, min(f_idx, n_steps-1)]
            return [y[1], f_i - 2*zeta_i*omega_i*y[1] - omega_i**2*y[0]]
        
        # Solve SDOF
        sol = solve_ivp(modal_eq, [t[0], t[-1]], [0, 0], 
                       t_eval=t, method='RK45')
        q[i, :] = sol.y[0, :]
    
    # Recover physical response
    u = vecs @ q
    return u, q, omega, vecs
```

### Commercial Software Features

**ANSYS Mechanical:**
- MODOPT command for modal extraction
- MXPAND for mode expansion
- DMPRAT for modal damping definition
- [[Modal Superposition]] in transient analysis

**ABAQUS:**
- *FREQUENCY step for modal extraction
- *MODAL DYNAMIC for time history analysis
- Modal damping definitions
- Residual mode enhancement option

**NASTRAN:**
- SOL 103 for normal modes
- SOL 112 for modal [[Frequency Response Function (FRF)]]
- SOL 129 for modal transient response
- DMIG for modal data recovery

**SAP2000:**
- Modal load cases
- Modal time history analysis
- Modal combination methods
- Modal participation display

## See Also

- [[Modal Analysis]]
- [[Mode Acceleration Method (MAM)]]
- [[Modal Superposition]]
- [[Natural Frequency]]
- [[Mode Shape]]
- [[Damping Ratio]]
- [[Finite Element Method]]
- [[Structural Dynamics]]
- [[Response Spectrum Analysis]]
- [[Direct Integration Method]]
- [[Modal Truncation]]
- [[Modal Participation Factor]]
- [[Rayleigh Damping]]
- [[Component Mode Synthesis]]
- [[Reduced Order Modeling]]
- [[Dynamic Substructuring]]
- [[Seismic Analysis]]
- [[Time History Analysis]]
- [[Frequency Response Function (FRF)]]
- [[Eigenvalue Problem]]

---

*Note: The Mode Displacement Method represents a cornerstone of computational [[Structural Dynamics]], providing an efficient and physically insightful approach to dynamic response analysis. Its combination of computational efficiency with clear physical interpretation makes it indispensable for large-scale linear dynamic problems across aerospace, civil, mechanical, and earthquake engineering applications.*
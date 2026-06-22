## Formal Definition

**Modal Analysis** is an analytical technique used to determine the inherent dynamic characteristics of engineering structures and mechanical systems. It decomposes complex vibration behavior into a set of simple oscillatory motions called **normal modes**, each characterized by a [[Natural Frequency]], damping ratio, and mode shape. This decomposition provides fundamental insights into how structures will respond to dynamic loading, enabling prediction, diagnosis, and optimization of dynamic performance across mechanical, aerospace, civil, and automotive engineering applications.

## Historical Development

### Key Milestones
- **1700s:** Daniel Bernoulli and Leonhard Euler develop mathematical theory of vibrating strings and beams
- **1877:** Lord Rayleigh publishes "The Theory of Sound," introducing Rayleigh's method for approximating natural frequencies
- **1940s:** Development of experimental vibration measurement techniques during World War II
- **1965:** [[Fast Fourier Transform (FFT)]] algorithm enables efficient experimental modal analysis
- **1970s:** Commercial finite element software incorporates modal analysis capabilities
- **1980s:** Development of Polyreference and ERA algorithms for multi-input modal identification
- **1990s:** Operational modal analysis emerges for output-only system identification

### Foundational Contributors
1. **Lord Rayleigh (1842-1919):** Developed Rayleigh's quotient and energy methods for vibration analysis
2. **R. E. D. Bishop (1925-2019):** Pioneered modern experimental modal analysis techniques
3. **D. J. Ewins (1940-2021):** Authored definitive textbook "Modal Testing: Theory, Practice and Application"
4. **R. R. Craig (1934-2020):** Developed component mode synthesis methods
5. **N. M. M. Maia (b. 1952):** Advanced modal identification algorithms and correlation techniques

## Mathematical Formulation

### [[Eigenvalue Problem]]

For an undamped linear system with $n$ [[degrees of freedom]]:
$$
\mathbf{M}\ddot{\mathbf{x}} + \mathbf{K}\mathbf{x} = \mathbf{0}
$$

Assume harmonic solution $\mathbf{x} = \boldsymbol{\phi}e^{i\omega t}$:
$$
(-\omega^2\mathbf{M} + \mathbf{K})\boldsymbol{\phi} = \mathbf{0}
$$

This yields the generalized [[Eigenvalue Problem]]:
$$
\mathbf{K}\boldsymbol{\phi}_i = \omega_i^2\mathbf{M}\boldsymbol{\phi}_i
$$

where:
- $\omega_i$ = $i$-th [[Natural Frequency]] (rad/s)
- $\boldsymbol{\phi}_i$ = corresponding mode shape (eigenvector)
- $\mathbf{M}$ = mass matrix (symmetric, positive definite)
- $\mathbf{K}$ = stiffness matrix (symmetric, positive semi-definite)

### Damped Systems

For proportionally damped systems ($\mathbf{C} = \alpha\mathbf{M} + \beta\mathbf{K}$):
$$
\mathbf{M}\ddot{\mathbf{x}} + \mathbf{C}\dot{\mathbf{x}} + \mathbf{K}\mathbf{x} = \mathbf{0}
$$

Mode shapes remain real and identical to undamped case. The modal equations become:
$$
\ddot{q}_i + 2\zeta_i\omega_i\dot{q}_i + \omega_i^2 q_i = 0
$$

where $\zeta_i$ is modal damping ratio.

### Orthogonality Conditions

Mode shapes satisfy:
$$
\boldsymbol{\phi}_i^T\mathbf{M}\boldsymbol{\phi}_j = 0 \quad \text{and} \quad \boldsymbol{\phi}_i^T\mathbf{K}\boldsymbol{\phi}_j = 0 \quad \text{for } i \neq j
$$

Define modal mass and modal stiffness:
$$
m_i = \boldsymbol{\phi}_i^T\mathbf{M}\boldsymbol{\phi}_i, \quad k_i = \boldsymbol{\phi}_i^T\mathbf{K}\boldsymbol{\phi}_i
$$
Then $\omega_i = \sqrt{k_i/m_i}$.

## Fundamental Principles

### [[Modal Superposition]]

Any dynamic response can be expressed as linear combination of mode shapes:
$$
\mathbf{x}(t) = \sum_{i=1}^n \boldsymbol{\phi}_i q_i(t) = \boldsymbol{\Phi}\mathbf{q}(t)
$$

where $\boldsymbol{\Phi} = [\boldsymbol{\phi}_1, \boldsymbol{\phi}_2, \ldots, \boldsymbol{\phi}_n]$ is modal matrix and $q_i(t)$ are modal coordinates.

### Modal Transformation

Applying coordinate transformation $\mathbf{x} = \boldsymbol{\Phi}\mathbf{q}$ to equations of motion:
$$
\boldsymbol{\Phi}^T\mathbf{M}\boldsymbol{\Phi}\ddot{\mathbf{q}} + \boldsymbol{\Phi}^T\mathbf{C}\boldsymbol{\Phi}\dot{\mathbf{q}} + \boldsymbol{\Phi}^T\mathbf{K}\boldsymbol{\Phi}\mathbf{q} = \boldsymbol{\Phi}^T\mathbf{F}(t)
$$

Using orthogonality yields decoupled equations:
$$
\ddot{q}_i + 2\zeta_i\omega_i\dot{q}_i + \omega_i^2 q_i = \frac{\boldsymbol{\phi}_i^T\mathbf{F}(t)}{m_i}
$$

### Modal Participation

**Modal participation factor:**
$$
\Gamma_i = \frac{\boldsymbol{\phi}_i^T\mathbf{M}\mathbf{r}}{\boldsymbol{\phi}_i^T\mathbf{M}\boldsymbol{\phi}_i}
$$
where $\mathbf{r}$ is influence vector for base excitation.

**Effective modal mass:**
$$
m_{i,\text{eff}} = \frac{(\boldsymbol{\phi}_i^T\mathbf{M}\mathbf{r})^2}{\boldsymbol{\phi}_i^T\mathbf{M}\boldsymbol{\phi}_i}
$$

Important for seismic design to ensure sufficient modes captured.

## Theoretical Framework

### [[Frequency Response Function (FRF)]] Representation

Frequency resp]]onse function (FRF) matrix can be expressed as modal summation:
$$
\mathbf{H}(\omega) = \sum_{i=1}^n \frac{\boldsymbol{\phi}_i\boldsymbol{\phi}_i^T}{m_i[(\omega_i^2 - \omega^2) + i(2\zeta_i\omega_i\omega)]}
$$

**Receptance form:** $\mathbf{H}(\omega) = (-\omega^2\mathbf{M} + i\omega\mathbf{C} + \mathbf{K})^{-1}$

### State-Space Formulation

For general [[Viscous Damping]], use [[State-Space Representation]]:
$$
\begin{aligned}
\dot{\mathbf{z}} &= \mathbf{A}\mathbf{z} + \mathbf{B}\mathbf{u} \\
\mathbf{y} &= \mathbf{C}\mathbf{z} + \mathbf{D}\mathbf{u}
\end{aligned}
$$

where $\mathbf{z} = \begin{bmatrix} \mathbf{x} \\ \dot{\mathbf{x}} \end{bmatrix}$. Eigenvalues of $\mathbf{A}$ give complex poles $\lambda_i = -\zeta_i\omega_i \pm i\omega_i\sqrt{1-\zeta_i^2}$.

### Complex Modes

For non-proportional damping, mode shapes become complex:
- Real part: Stationary deformation pattern
- Imaginary part: Phase differences between points
- Nodes become traveling points rather than stationary lines

## Classification and Variants

### By Analysis Approach
1. **Analytical Modal Analysis:** Using mathematical models (differential equations)
2. **Computational Modal Analysis:** Finite element or boundary element methods
3. **Experimental Modal Analysis (EMA):** Measuring physical structures
4. **Operational Modal Analysis (OMA):** Using operational response data only

### By Damping Treatment
1. **Undamped modal analysis:** $\mathbf{C} = \mathbf{0}$
2. **Proportionally damped:** $\mathbf{C} = \alpha\mathbf{M} + \beta\mathbf{K}$
3. **Non-proportionally damped:** General [[Viscous Damping]]
4. **Structural damping:** Complex stiffness formulation

### By Domain of Analysis
1. **Frequency domain methods:** Using FRFs
2. **Time domain methods:** Using impulse responses or time histories
3. **Spatial domain methods:** Using mode shape expansions

### By Model Type
1. **Discrete parameter models:** Lumped mass-spring systems
2. **Continuous systems:** Analytical solutions for beams, plates, shells
3. **Distributed parameter systems:** Partial differential equation solutions

## Derivation and Proof

### From [[Hamilton's Principle]]

For conservative system, [[Hamilton's Principle]] states:
$$
\delta \int_{t_1}^{t_2} (T - V) dt = 0
$$

where $T = \frac{1}{2}\dot{\mathbf{x}}^T\mathbf{M}\dot{\mathbf{x}}$ and $V = \frac{1}{2}\mathbf{x}^T\mathbf{K}\mathbf{x}$.

Applying variational calculus yields [[Euler-Lagrange Equations]]:
$$
\frac{d}{dt}\left(\frac{\partial T}{\partial \dot{\mathbf{x}}}\right) - \frac{\partial (T - V)}{\partial \mathbf{x}} = \mathbf{0}
$$

which gives $\mathbf{M}\ddot{\mathbf{x}} + \mathbf{K}\mathbf{x} = \mathbf{0}$.

### Rayleigh's Method Proof

**Rayleigh quotient:** For an assumed mode shape $\boldsymbol{\psi}$:
$$
R(\boldsymbol{\psi}) = \frac{\boldsymbol{\psi}^T\mathbf{K}\boldsymbol{\psi}}{\boldsymbol{\psi}^T\mathbf{M}\boldsymbol{\psi}}
$$

**[[Stationarity]] property:** $R(\boldsymbol{\psi})$ is stationary at true mode shapes.

**Proof:** Consider variation $\boldsymbol{\psi} + \epsilon\boldsymbol{\eta}$ and require $\frac{dR}{d\epsilon}\big|_{\epsilon=0} = 0$.

### Component Mode Synthesis

**[[Craig-Bampton Method]]:** Partition [[degrees of freedom]] into boundary (b) and interior (i):
$$
\begin{bmatrix}
\mathbf{M}_{bb} & \mathbf{M}_{bi} \\
\mathbf{M}_{ib} & \mathbf{M}_{ii}
\end{bmatrix}
\begin{bmatrix}
\ddot{\mathbf{x}}_b \\ \ddot{\mathbf{x}}_i
\end{bmatrix} +
\begin{bmatrix}
\mathbf{K}_{bb} & \mathbf{K}_{bi} \\
\mathbf{K}_{ib} & \mathbf{K}_{ii}
\end{bmatrix}
\begin{bmatrix}
\mathbf{x}_b \\ \mathbf{x}_i
\end{bmatrix} =
\begin{bmatrix}
\mathbf{F}_b \\ \mathbf{0}
\end{bmatrix}
$$

Use constraint modes $\boldsymbol{\Psi}_c = -\mathbf{K}_{ii}^{-1}\mathbf{K}_{ib}$ and fixed-interface normal modes from $\mathbf{K}_{ii}\boldsymbol{\Phi}_n = \mathbf{M}_{ii}\boldsymbol{\Phi}_n\boldsymbol{\Omega}_n^2$.

## Physical Interpretation

### Mode Shapes as Standing Waves

Each mode represents a standing wave pattern:
- **Nodes:** Points with zero displacement (for real modes)
- **Anti-nodes:** Points with maximum displacement
- **Spatial wavelength:** Decreases with increasing mode number

### Modal Contributions

**Participation of modes in response:**
- Low-frequency modes: Govern global, low-energy deformation
- High-frequency modes: Govern local, high-energy deformation
- **Modal truncation:** Often only first $m \ll n$ modes needed for engineering accuracy

### Beat Phenomenon

When two close modes exist:
$$
x(t) = \phi_1\cos(\omega_1 t) + \phi_2\cos(\omega_2 t)
$$
produces beats at frequency $\frac{\omega_1 - \omega_2}{2}$.

### Damping Visualization

**Complex modes:** Show traveling wave character
**Proportional damping:** Nodes remain fixed points
**Hysteretic damping:** Frequency-independent energy loss per cycle

## Applications

### Engineering Disciplines
1. **Aerospace Engineering:** Aircraft flutter analysis, spacecraft [[Structural Dynamics]]
2. **Mechanical Engineering:** Rotor dynamics, machinery vibration diagnosis
3. **Civil Engineering:** Seismic analysis, bridge dynamics, tall building design
4. **Automotive Engineering:** NVH (Noise, Vibration, Harshness) analysis
5. **Marine Engineering:** Ship hull vibration, offshore platform dynamics

### Scientific Fields
1. **Acoustics:** Room modes, musical instrument design
2. **Geophysics:** Earth's normal modes, seismology
3. **Biomechanics:** Bone vibration, hearing mechanics
4. **Materials Science:** Characterization of composite materials

### Practical Implementations
- **Structural health monitoring:** Damage detection via modal parameter changes
- **Vibration troubleshooting:** Identifying sources of excessive vibration
- **Finite element model validation:** Correlation with experimental results
- **Active vibration control:** Controller design based on modal decomposition
- **Noise control:** Identifying structural paths for noise transmission

## Implementation Considerations

### Finite Element Modal Analysis

**Procedure:**
1. **Mesh generation:** Discretize geometry into finite elements
2. **Assembly:** Form global $\mathbf{M}$ and $\mathbf{K}$ matrices
3. **Boundary conditions:** Apply constraints to remove [[Rigid Body]] modes
4. **Eigensolution:** Solve $\mathbf{K}\boldsymbol{\phi} = \omega^2\mathbf{M}\boldsymbol{\phi}$
5. **Post-processing:** Animate mode shapes, calculate modal parameters

**Eigensolvers:**
- **Subspace iteration:** For large sparse systems, few modes needed
- **[[Lanczos Method]]:** Efficient for large eigenvalue problems
- **QR algorithm:** For full matrices, all eigenvalues
- **AMSES:** Automated multi-level substructuring

### Experimental Modal Testing

**Procedure:**
1. **Test planning:** Define measurement points, excitation locations
2. **Instrumentation:** Install accelerometers, force transducers
3. **Data acquisition:** Measure FRFs using impact hammer or shaker
4. **Parameter extraction:** Identify $\omega_i$, $\zeta_i$, $\boldsymbol{\phi}_i$ from FRFs
5. **Validation:** Check modal assurance criterion (MAC)

**Excitation methods:**
- **Impact testing:** Quick, portable, but limited force control
- **Shaker testing:** Controlled excitation, better for nonlinear systems
- **Operational excitation:** Using ambient or operational forces

### Parameter Estimation Methods

**Frequency domain:**
- **Peak picking:** Simple but limited accuracy
- **Circle fitting:** Accurate for single modes
- **Rational fraction polynomial:** Global method for multiple modes
- **Least squares complex exponential:** Time domain equivalent

**Time domain:**
- **Ibrahim Time Domain (ITD):** Early time domain method
- **Eigensystem Realization Algorithm (ERA):** State-space approach
- **Stochastic Subspace Identification (SSI):** For operational modal analysis

## Advantages and Limitations

### Strengths
1. **Physical insight:** Reveals fundamental dynamic characteristics
2. **Model reduction:** Enables efficient dynamic analysis via modal truncation
3. **Design guidance:** Identifies critical frequencies to avoid [[Resonance]]
4. **Damage detection:** Sensitive indicator of structural changes
5. **Experimental correlation:** Basis for validating computational models

### Weaknesses
1. **Linear assumption:** Limited to linear or linearized systems
2. **Mode truncation:** Higher modes neglected may be important
3. **Damping uncertainty:** Difficult to model and measure accurately
4. **Computational cost:** Large models require significant resources
5. **Experimental errors:** Noise, leakage, nonlinearities affect measurements

### Validity Range
- **Applicable when:** Linear time-invariant systems, small vibrations
- **Not applicable when:** Large deformations, strong nonlinearities, impact loading
- **Breakdown scenarios:** Plastic deformation, clearance nonlinearities, fluid-structure interaction with strong coupling

## Advanced Topics

### Nonlinear Modal Analysis

**Nonlinear normal modes (NNMs):**
- Definition: Notions extending linear modes to nonlinear systems
- Properties: Frequency-energy dependence, modal interactions
- Computation: Harmonic balance, shooting methods, continuation

**Modal interactions:**
- Internal [[Resonance]]: Energy exchange between modes
- Auto-parametric resonance: Coupling through nonlinear terms
- Mode localization: In disordered or mistuned systems

### Stochastic Modal Analysis

**Random eigenvalue problems:**
For systems with uncertain parameters:
$$
(\mathbf{K} + \Delta\mathbf{K})\boldsymbol{\phi} = \omega^2(\mathbf{M} + \Delta\mathbf{M})\boldsymbol{\phi}
$$

**Methods:**
- Monte Carlo simulation
- Perturbation methods
- Polynomial chaos expansion
- Random matrix theory

### Substructuring Methods

**Component mode synthesis (CMS):**
- [[Craig-Bampton Method]]
- MacNeal-Rubin method
- Free-interface methods
- Dual Craig-Bampton

**Interface reduction:**
- Characteristic constraint modes
- Interface modes
- Primal/dual assembly

### Sensitivity Analysis

**Modal parameter derivatives:**
$$
\frac{\partial \omega_i}{\partial p} = \frac{1}{2\omega_i}\frac{\boldsymbol{\phi}_i^T\left(\frac{\partial \mathbf{K}}{\partial p} - \omega_i^2\frac{\partial \mathbf{M}}{\partial p}\right)\boldsymbol{\phi}_i}{\boldsymbol{\phi}_i^T\mathbf{M}\boldsymbol{\phi}_i}
$$

Applications: Structural optimization, model updating, damage localization.

## Special Cases and Examples

### Benchmark Problems

**Cantilever beam:**
- Analytical solution from [[Euler-Bernoulli Beam Element]]:
  $$
  \omega_n = \beta_n^2\sqrt{\frac{EI}{\rho AL^4}}
  $$
  where $\beta_1 = 1.875$, $\beta_2 = 4.694$, $\beta_3 = 7.855$
- Mode shapes: Combinations of sine, cosine, hyperbolic functions

**Simply supported plate:**
- Natural frequencies:
  $$
  \omega_{mn} = \pi^2\left[\left(\frac{m}{a}\right)^2 + \left(\frac{n}{b}\right)^2\right]\sqrt{\frac{D}{\rho h}}
  $$
  where $D = \frac{Eh^3}{12(1-\nu^2)}$
- Mode shapes: $\phi_{mn}(x,y) = \sin\left(\frac{m\pi x}{a}\right)\sin\left(\frac{n\pi y}{b}\right)$

### Industrial Examples

**Automotive body-in-white:**
- First [[torsion]] mode: ~30-40 Hz
- First bending mode: ~40-50 Hz
- Local panel modes: >80 Hz
- Target: Separate from engine excitation frequencies (idle ~20-30 Hz, cruise harmonics)

**Wind turbine tower:**
- First fore-aft mode: ~0.3-0.5 Hz
- First side-side mode: ~0.3-0.5 Hz
- Important to avoid 1P (rotor speed) and 3P (blade passing) excitations

### Modal Testing Standards

**ISO 7626:** Vibration testing for experimental modal analysis
**ASTM E2534:** Guide for conducting sensory evaluation on vibration
**NASA-HDBK-7005:** Dynamic environmental criteria

## Error Analysis

### Finite Element Discretization Errors

**Mesh convergence:**
$$
\omega_{\text{FEM}} = \omega_{\text{exact}} + Ch^p
$$
where $h$ = element size, $p$ = polynomial order

**Numerical pollution:** For wave propagation problems, need $\frac{\omega h}{c} \ll 1$

**Locking phenomena:**
- Shear locking in beams/plates
- Volumetric locking in nearly incompressible materials
- Membrane locking in shells

### Experimental Errors

**Measurement errors:**
- Accelerometer mass loading: $\frac{\Delta \omega}{\omega} \approx -\frac{1}{2}\frac{m_{\text{sensor}}}{m_{\text{effective}}}$
- Cable effects, electromagnetic interference
- Calibration errors (typically 1-3%)

**Signal processing errors:**
- **Leakage:** Windowing effects in FFT
- **Aliasing:** Insufficient sampling rate
- **Noise:** Signal-to-noise ratio limitations
- **Transient effects:** Incomplete decay between impacts

### Modal Parameter Uncertainty

**Cramer-Rao bounds:** Theoretical lower bounds on variance of estimated parameters
**Confidence intervals:** From [[covariance]] matrix of estimation algorithm
**Monte Carlo analysis:** For nonlinear or complex error propagation

## Relationship to Other Concepts

### Connection to [[Frequency Response Function (FRF)]]

Modal decomposition of FRF:
$$
H_{jk}(\omega) = \sum_{i=1}^n \frac{\phi_{ji}\phi_{ki}}{m_i[(\omega_i^2 - \omega^2) + i(2\zeta_i\omega_i\omega)]}
$$

Each peak corresponds to a [[Natural Frequency]], peak width relates to damping, peak height relates to mode shape.

### Contrast with Direct Time Integration

- **Modal analysis:** Uncoupled equations, efficient for linear systems
- **Direct integration:** Coupled equations, necessary for nonlinear systems
- **Choice depends on:** System linearity, number of time steps, required outputs

### Relationship to Wave-Based Methods

**High-frequency dynamics:**
- Modal density increases with frequency
- Statistical energy analysis (SEA) more appropriate
- Wave approaches: WIA, SEA, hybrid methods

**Mid-frequency:** Modal and wave methods both applicable, hybrid approaches needed.

### Connection to Control Theory

**Modal control:** Design controllers to affect specific modes
**Spillover:** Control of low modes excites uncontrolled high modes
**Model reduction:** Balanced truncation, Hankel norm approximation

## Historical Context and Evolution

### Original Motivation

**Early developments:**
- Musical instruments: Understanding harmonics and timbre
- Clockmaking: Pendulum dynamics for timekeeping
- Structural failures: Resonance disasters (Tacoma Narrows Bridge, 1940)

**Military applications:**
- Aircraft flutter during World War II
- Missile and spacecraft [[Structural Dynamics]]
- Submarine acoustics and vibration

### Evolution Over Time

1. **Pre-1900:** Analytical solutions for simple systems
2. **1900-1950:** Experimental methods development
3. **1960-1980:** Computational methods (FEM), modal testing standardization
4. **1990-2010:** Operational modal analysis, stochastic methods
5. **2010-present:** Digital twins, machine learning applications, real-time monitoring

### Modern Reformulations

- **Blind modal identification:** Using unsupervised learning
- **Digital image correlation:** Full-field modal analysis
- **Laser Doppler vibrometry:** Non-contact high-resolution measurements
- **Embedded sensors:** MEMS accelerometers for continuous monitoring

## Pedagogical Approach

### Teaching Strategies

1. **Physical demonstrations:** Simple beams, plates, and strings
2. **Hands-on testing:** Impact testing with accelerometers
3. **Computer simulations:** MATLAB/ANSYS modal analysis
4. **Case studies:** Real-world failure analysis due to resonance

### Common Misconceptions

1. **"Mode shapes are unique":** Only defined up to scaling factor
2. **"All modes are equally important":** Often only first few dominate response
3. **"Natural frequencies are fixed":** Change with boundary conditions, temperature, damage
4. **"Experimental and analytical modes should match exactly":** Discrepancies expected due to modeling assumptions

### Learning Resources

**Foundational Texts:**
- Ewins, "Modal Testing: Theory, Practice and Application"
- Maia & Silva, "Theoretical and Experimental Modal Analysis"
- Craig & Kurdila, "Fundamentals of Structural Dynamics"
- Clough & Penzien, "Dynamics of Structures"

**Online Resources:**
- MIT OpenCourseWare: Dynamics and Control
- Siemens LMS Virtual Lab
- Wolfram Demonstrations: Modal Analysis
- YouTube: Modal testing demonstrations

**Software Tutorials:**
- ANSYS Modal Analysis Workbench
- MATLAB Modal Analysis Toolbox
- ME'scopeVES Tutorials
- ABAQUS Modal Analysis Examples

## Implementation in Software

### MATLAB Implementation

```matlab
% Modal analysis of discrete system
M = diag([10, 20, 15]);                % Mass matrix
K = [30 -20 0; -20 40 -20; 0 -20 30];  % Stiffness matrix

% Solve eigenvalue problem
[V, D] = eig(K, M);
omega = sqrt(diag(D));                 % Natural frequencies (rad/s)
f = omega/(2*pi);                       % Natural frequencies (Hz)
phi = V;                               % Mode shapes

% Normalize mode shapes (mass normalization)
for i = 1:size(phi,2)
    phi(:,i) = phi(:,i)/sqrt(phi(:,i)'*M*phi(:,i));
end

% Plot mode shapes
figure;
for i = 1:3
    subplot(3,1,i);
    stem(phi(:,i), 'filled');
    title(sprintf('Mode %d: f = %.2f Hz', i, f(i)));
    ylabel('Amplitude');
end
```

### Python with SciPy

```python
import numpy as np
from scipy.linalg import eigh
import matplotlib.pyplot as plt

# Mass and stiffness matrices
M = np.diag([10, 20, 15])
K = np.array([[30, -20, 0],
              [-20, 40, -20],
              [0, -20, 30]])

# Solve generalized eigenvalue problem
vals, vecs = eigh(K, M)
omega = np.sqrt(vals)           # Natural frequencies (rad/s)
f = omega/(2*np.pi)             # Natural frequencies (Hz)

# Mass normalize mode shapes
for i in range(vecs.shape[1]):
    vecs[:,i] = vecs[:,i]/np.sqrt(vecs[:,i].T @ M @ vecs[:,i])

# Plot
fig, axes = plt.subplots(3, 1, figsize=(8, 10))
for i in range(3):
    axes[i].stem(range(1,4), vecs[:,i], linefmt='b-', markerfmt='bo', basefmt='r-')
    axes[i].set_title(f'Mode {i+1}: f = {f[i]:.2f} Hz')
    axes[i].set_ylabel('Amplitude')
    axes[i].grid(True)
plt.tight_layout()
plt.show()
```

### Commercial Software Features

**ANSYS Mechanical:**
- Block Lanczos, PCG Lanczos, unsymmetric eigensolvers
- Pre-stressed modal analysis
- Cyclic symmetry for rotating structures
- Damped modal analysis options

**NASTRAN:**
- SOL 103: Normal modes analysis
- SOL 110: Complex eigenvalues (damped)
- SOL 111: Modal [[Frequency Response Function (FRF)]]
- DMAP alter for customized modal analysis

**LMS Test.Lab:**
- Impact testing workflow
- MIMO shaker testing
- PolyMAX parameter estimation
- Modal validation tools (MAC, COMAC)

**ABAQUS:**
- Lanczos and subspace iteration eigensolvers
- Modal dynamics for transient response
- Complex eigenvalue analysis for damped systems
- Frequency extraction with acoustic-structural coupling

## See Also

- [[Natural Frequency]]
- [[Mode Shape]]
- [[Damping Ratio]]
- [[Finite Element Analysis (FEA)]]
- [[Frequency Response Function (FRF)]]
- [[Experimental Modal Analysis]]
- [[Operational Modal Analysis]]
- [[Modal Assurance Criterion]]
- [[Modal Participation Factor]]
- [[Rayleigh's Method]]
- [[Component Mode Synthesis]]
- [[Normal Modes]]
- [[Eigenvalue Problem]]
- [[Structural Dynamics]]
- [[Vibration Analysis]]
- [[Seismic Analysis]]
- [[Rotor Dynamics]]
- [[Flutter Analysis]]
- [[Dynamic Substructuring]]
- [[Modal Truncation]]
- [[Complex Modes]]

---

*Note: Modal analysis represents one of the most powerful tools in structural dynamics, bridging theoretical understanding, computational prediction, and experimental verification. Its ability to decompose complex dynamic behavior into fundamental components makes it indispensable for design, analysis, and troubleshooting across virtually all engineering disciplines involving dynamic systems.*
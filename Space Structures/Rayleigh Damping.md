## Formal Definition

**Rayleigh [[Damping]]** (also known as **proportional damping**) is a [[mathematical model]] for [[Viscous Damping]] in linear dynamic systems where the damping matrix is expressed as a linear combination of the mass and stiffness matrices. Formulated as $C = \alpha M + \beta K$, where $\alpha$ and $\beta$ are the Rayleigh damping coefficients, this model ensures that the damping matrix is diagonalizable by the same modal transformation that diagonalizes the mass and stiffness matrices, thereby preserving the orthogonality of mode shapes and enabling decoupled [[Modal Analysis]].

## Historical Development

### Key Milestones
- **1877:** Lord Rayleigh first proposes the concept of proportional damping in "The Theory of Sound"
- **1950s:** Formal development for [[Structural Dynamics]] applications
- **1960s:** Implementation in [[Finite Element Analysis (FEA)]] software
- **1970s:** Development of methods for determining Rayleigh coefficients from experimental data
- **1980s:** Recognition of limitations for non-classically damped systems
- **1990s:** Integration with component mode synthesis and substructuring methods
- **2000s:** Extension to frequency-dependent and nonlinear damping models
- **2010s:** Application in seismic design codes and performance-based engineering

### Foundational Contributors
1. **Lord Rayleigh (John William Strutt, 1842-1919):** Proposed the original concept of proportional damping
2. **Stephen Timoshenko (1878-1972):** Applied Rayleigh damping to engineering vibration problems
3. **Ray W. Clough (1920-2016):** Incorporated Rayleigh damping in finite element formulations
4. **K. J. Bathe (b. 1943):** Developed practical implementations in computational structural dynamics
5. **J. S. Przemieniecki (1925-2012):** Advanced [[Modal Analysis]] techniques for damped systems

## Mathematical Formulation

### General Form

**Rayleigh damping matrix:**
$$
C = \alpha M + \beta K
$$
where:
- $M \in \mathbb{R}^{n \times n}$: Mass matrix
- $K \in \mathbb{R}^{n \times n}$: Stiffness matrix
- $\alpha$: Mass-proportional damping coefficient (units: s⁻¹)
- $\beta$: Stiffness-proportional damping coefficient (units: s)

### Modal Transformation

For undamped eigenproblem: $K\Phi = M\Phi\Omega^2$, where:
- $\Phi = [\phi_1, \phi_2, \ldots, \phi_n]$: Modal matrix (mass-normalized: $\Phi^T M\Phi = I$)
- $\Omega^2 = \text{diag}(\omega_1^2, \omega_2^2, \ldots, \omega_n^2)$: Diagonal matrix of squared natural frequencies

**Modal damping matrix:**
$$
\Phi^T C\Phi = \alpha\Phi^T M\Phi + \beta\Phi^T K\Phi = \alpha I + \beta\Omega^2
$$

**Modal damping ratios:**
$$
\zeta_i = \frac{1}{2}\left(\frac{\alpha}{\omega_i} + \beta\omega_i\right), \quad i = 1, 2, \ldots, n
$$

### Frequency Domain Formulation

**Complex frequency response:** For harmonic excitation $\mathbf{f}(t) = \mathbf{F}e^{i\omega t}$:
$$
[-\omega^2 M + i\omega C + K]\mathbf{X}(\omega) = \mathbf{F}(\omega)
$$

With Rayleigh damping:
$$
[-\omega^2 M + i\omega(\alpha M + \beta K) + K]\mathbf{X}(\omega) = [M(-\omega^2 + i\omega\alpha) + K(1 + i\omega\beta)]\mathbf{X}(\omega) = \mathbf{F}(\omega)
$$

## Fundamental Principles

### Proportional Damping Property

**Diagonalizability:** The key property of Rayleigh damping is that the damping matrix is diagonalized by the undamped modal matrix:
- $\Phi^T C\Phi = \text{diag}(2\zeta_1\omega_1, 2\zeta_2\omega_2, \ldots, 2\zeta_n\omega_n)$
- This enables [[Decoupling]] of the equations of motion into independent SDOF systems

**Physical interpretation:**
- $\alpha M$: Represents damping forces proportional to absolute velocities (e.g., air resistance)
- $\beta K$: Represents damping forces proportional to deformation rates (e.g., material internal friction)

### Energy Dissipation Characteristics

**Dissipation per cycle:** For mode $i$ with circular frequency $\omega$:
$$
\Delta E_i = \pi\omega X_i^2 (2\zeta_i m_i\omega) = \pi X_i^2 (\alpha m_i + \beta k_i)\omega
$$
where $m_i = \phi_i^T M\phi_i = 1$ (mass-normalized), $k_i = \omega_i^2$

**Frequency dependence:**
- Mass-proportional term: $\zeta_i \propto 1/\omega_i$ (decreases with frequency)
- Stiffness-proportional term: $\zeta_i \propto \omega_i$ (increases with frequency)
- Combined: Parabolic variation with frequency

### Orthogonality Preservation

**Modal [[Decoupling]]:** The equations of motion transform to:
$$
\ddot{q}_i(t) + 2\zeta_i\omega_i\dot{q}_i(t) + \omega_i^2 q_i(t) = \phi_i^T \mathbf{f}(t), \quad i = 1, 2, \ldots, n
$$
where $\mathbf{x}(t) = \Phi\mathbf{q}(t)$

**Independent modal responses:** Each modal coordinate $q_i(t)$ can be solved independently and superimposed.

## Theoretical Framework

### Derivation from Variational Principles

**Rayleigh's dissipation function:** For a system with [[Viscous Damping]], define:
$$
\mathcal{R} = \frac{1}{2}\dot{\mathbf{x}}^T C\dot{\mathbf{x}}
$$

**Extended [[Hamilton's Principle]]:**
$$
\delta\int_{t_1}^{t_2} (T - V)dt + \int_{t_1}^{t_2} \delta W_{nc} dt = 0
$$
where $\delta W_{nc} = -\frac{\partial\mathcal{R}}{\partial\dot{\mathbf{x}}} \cdot \delta\mathbf{x}$

**For Rayleigh damping:** $\mathcal{R} = \frac{1}{2}\dot{\mathbf{x}}^T(\alpha M + \beta K)\dot{\mathbf{x}}$

### Modal Damping Ratio Function

**Frequency dependence:** 
$$
\zeta(\omega) = \frac{1}{2}\left(\frac{\alpha}{\omega} + \beta\omega\right)
$$

**Minimum damping ratio:** Occurs at $\omega_{\text{min}} = \sqrt{\alpha/\beta}$:
$$
\zeta_{\text{min}} = \sqrt{\alpha\beta}
$$

**Critical points:**
- $\zeta(\omega) = \zeta_{\text{min}}$ at $\omega = \sqrt{\alpha/\beta}$
- $\zeta(\omega) \to \infty$ as $\omega \to 0$ (for $\alpha > 0$)
- $\zeta(\omega) \to \infty$ as $\omega \to \infty$ (for $\beta > 0$)

### Stability Analysis

**For stable system:** Require $\zeta_i > 0$ for all modes:
- $\alpha > 0$ and $\beta > 0$ ensures positive damping for all frequencies
- For $\alpha < 0$ or $\beta < 0$, some modes may have negative damping (unstable)

**Energy decay rate:** Total mechanical energy satisfies:
$$
\frac{dE}{dt} = -\dot{\mathbf{x}}^T C\dot{\mathbf{x}} = -\alpha\dot{\mathbf{x}}^T M\dot{\mathbf{x}} - \beta\dot{\mathbf{x}}^T K\dot{\mathbf{x}} \leq 0
$$

## Classification and Variants

### By Coefficient Determination Method
1. **Frequency-based Rayleigh damping:** Coefficients chosen to match damping at specific frequencies
2. **Modal-based Rayleigh damping:** Coefficients chosen to match modal damping ratios
3. **Experimental Rayleigh damping:** Coefficients identified from vibration tests
4. **Code-specified Rayleigh damping:** Coefficients prescribed by design codes (e.g., ASCE 7)

### By Extension Type
1. **Classical Rayleigh damping:** $C = \alpha M + \beta K$
2. **Extended Rayleigh damping:** $C = M\sum_{i=0}^{m} \alpha_i(M^{-1}K)^i$
3. **Cauchy damping:** $C = M f(M^{-1}K)$ where $f$ is a function
4. **Fractional derivative damping:** Generalization using fractional calculus

### By Application Domain
1. **Structural Rayleigh damping:** For buildings, bridges, offshore structures
2. **Soil-structure interaction damping:** With frequency-dependent soil properties
3. **Acoustic-structural damping:** For coupled vibro-acoustic systems
4. **Rotordynamic damping:** For rotating machinery with gyroscopic effects

## Derivation and Proof

### Derivation from Physical Principles

**Assumption 1:** Damping forces consist of two components:
1. Forces proportional to absolute velocities (air drag, support friction)
2. Forces proportional to deformation rates (material [[Hysteresis]], internal friction)

**Mathematical representation:**
$$
\mathbf{f}_d = C\dot{\mathbf{x}} = C_1\dot{\mathbf{x}} + C_2\dot{\mathbf{x}}
$$

**Assumption 2:** $C_1$ proportional to mass matrix, $C_2$ proportional to stiffness matrix:
- Mass-proportional damping: $C_1 = \alpha M$ (damping force ∝ absolute velocity)
- Stiffness-proportional damping: $C_2 = \beta K$ (damping force ∝ strain rate)

**Combination:** $C = \alpha M + \beta K$

### Proof of Modal [[Decoupling]]

**Given:** $M\Phi = K\Phi\Omega^{-2}$ (mass-normalized: $\Phi^T M\Phi = I$, $\Phi^T K\Phi = \Omega^2$)

**Compute modal damping matrix:**
$$
\Phi^T C\Phi = \Phi^T(\alpha M + \beta K)\Phi = \alpha\Phi^T M\Phi + \beta\Phi^T K\Phi = \alpha I + \beta\Omega^2
$$

**Diagonal structure:** Since $\Omega^2$ is diagonal, $\alpha I + \beta\Omega^2$ is diagonal.

**Modal damping ratios:** Diagonal elements are $2\zeta_i\omega_i$, so:
$$
2\zeta_i\omega_i = \alpha + \beta\omega_i^2 \Rightarrow \zeta_i = \frac{1}{2}\left(\frac{\alpha}{\omega_i} + \beta\omega_i\right)
$$

### Optimal Coefficient Selection

**Given target damping ratios $\zeta_a, \zeta_b$ at frequencies $\omega_a, \omega_b$:**
$$
\begin{cases}
\zeta_a = \frac{1}{2}\left(\frac{\alpha}{\omega_a} + \beta\omega_a\right) \\
\zeta_b = \frac{1}{2}\left(\frac{\alpha}{\omega_b} + \beta\omega_b\right)
\end{cases}
$$

**Solve for $\alpha, \beta$:**
$$
\alpha = \frac{2\omega_a\omega_b(\zeta_a\omega_b - \zeta_b\omega_a)}{\omega_b^2 - \omega_a^2}, \quad \beta = \frac{2(\zeta_b\omega_b - \zeta_a\omega_a)}{\omega_b^2 - \omega_a^2}
$$

**Special case $\zeta_a = \zeta_b = \zeta$:**
$$
\alpha = \frac{2\zeta\omega_a\omega_b}{\omega_a + \omega_b}, \quad \beta = \frac{2\zeta}{\omega_a + \omega_b}
$$

## Physical Interpretation

### Mass-Proportional Damping Component

**Physical meaning:** Represents damping forces proportional to absolute velocities:
- Air resistance on moving surfaces
- [[Viscous Damping]] at supports or foundations
- Equivalent to dashpots connecting masses to fixed ground

**Energy interpretation:** Dissipates [[Kinetic Energy]]: $P_{\text{diss}} = \alpha\dot{\mathbf{x}}^T M\dot{\mathbf{x}}$

**Frequency behavior:** Dominates at low frequencies, provides high damping for [[Rigid Body]] modes

### Stiffness-Proportional Damping Component

**Physical meaning:** Represents damping forces proportional to deformation rates:
- Material internal friction (hysteretic damping)
- Joint friction in structural connections
- Equivalent to dashpots in parallel with springs

**Energy interpretation:** Dissipates [[Strain Energy]] rate: $P_{\text{diss}} = \beta\dot{\mathbf{x}}^T K\dot{\mathbf{x}}$

**Frequency behavior:** Dominates at high frequencies, provides increasing damping with frequency

### Combined Physical System

**Parallel arrangement:** Mass-proportional dashpots from each mass to ground, plus stiffness-proportional dashpots parallel to each spring

**Continuous systems:** For distributed parameter systems:
- Mass-proportional: $c(x) = \alpha m(x)$
- Stiffness-proportional: $c(x) = \beta EI(x)$ for beams

**Limitation:** Stiffness-proportional damping can overdamp high-frequency modes, causing numerical issues in time integration

## Applications

### Engineering Disciplines
1. **Structural Engineering:** Earthquake analysis of buildings and bridges
2. **Mechanical Engineering:** Vibration analysis of machinery and vehicles
3. **Aerospace Engineering:** Dynamic analysis of aircraft and spacecraft
4. **Civil Engineering:** Seismic design of dams, tunnels, and offshore platforms
5. **Geotechnical Engineering:** Soil-structure interaction problems

### Analysis Types
1. **Modal time history analysis:** For earthquake engineering
2. **Response spectrum analysis:** Using modal damping ratios
3. **Frequency domain analysis:** For harmonic and [[Random Vibration]]
4. **Stability analysis:** For flutter and dynamic instability
5. **Transient dynamic analysis:** For impact and blast loading

### Design Codes and Standards
1. **ASCE 7-16:** Minimum damping ratios for different structural types
2. **IBC 2018:** Damping values for seismic design
3. **Eurocode 8:** Damping for earthquake-resistant structures
4. **AASHTO:** Bridge design specifications
5. **API RP 2A:** Offshore platform design

## Implementation Considerations

### Coefficient Determination Methods

**Method 1: Match damping at two frequencies:**
Given $\zeta_1$ at $\omega_1$, $\zeta_2$ at $\omega_2$:
$$
\alpha = \frac{2\omega_1\omega_2(\zeta_1\omega_2 - \zeta_2\omega_1)}{\omega_2^2 - \omega_1^2}, \quad \beta = \frac{2(\zeta_2\omega_2 - \zeta_1\omega_1)}{\omega_2^2 - \omega_1^2}
$$

**Method 2: Equal damping at two frequencies:**
For $\zeta$ at $\omega_1$ and $\omega_2$:
$$
\alpha = \frac{2\zeta\omega_1\omega_2}{\omega_1 + \omega_2}, \quad \beta = \frac{2\zeta}{\omega_1 + \omega_2}
$$

**Method 3: Minimize error over frequency range:**
Solve optimization problem:
$$
\min_{\alpha,\beta} \int_{\omega_{\min}}^{\omega_{\max}} [\zeta_{\text{target}}(\omega) - \frac{1}{2}(\alpha/\omega + \beta\omega)]^2 d\omega
$$

### Finite Element Implementation

**ANSYS APDL:**
```
ALPHAD, alpha_value    ! Mass damping coefficient
BETAD, beta_value      ! Stiffness damping coefficient
```

**ABAQUS:**
```
*DAMPING, RAYLEIGH
alpha_value, beta_value
```

**NASTRAN:**
```
PARAM, ALPHA1, alpha_value
PARAM, BETA1, beta_value
```

**MATLAB:**
```matlab
alpha = 0.1;  % Mass damping coefficient
beta = 0.001; % Stiffness damping coefficient
C = alpha*M + beta*K;
```

### Time Integration Considerations

**Stability condition:** For explicit methods (e.g., Central Difference):
$$
\Delta t \leq \Delta t_{\text{crit}} = \frac{2}{\omega_{\max}}\left(\sqrt{1+\zeta_{\max}^2} - \zeta_{\max}\right)
$$
where $\zeta_{\max} = \max_i \zeta_i$

**Numerical damping:** Some integration methods (e.g., Newmark with $\gamma > 0.5$) add numerical damping that interacts with Rayleigh damping

**High-frequency damping:** Stiffness-proportional term can cause excessive damping of high-frequency modes, potentially stabilizing spurious high-frequency oscillations

## Advantages and Limitations

### Strengths
1. **Mathematical convenience:** Preserves modal orthogonality, enabling decoupled analysis
2. **Physical basis:** Represents two common damping mechanisms
3. **Computational efficiency:** Only two parameters to define entire damping matrix
4. **Well-established:** Extensive theoretical development and software implementation
5. **Frequency control:** Can tailor damping variation with frequency

### Weaknesses
1. **Oversimplification:** Real damping often more complex than two-parameter model
2. **Unrealistic frequency dependence:** Damping ratios vary as $1/\omega + \omega$, which may not match reality
3. **Overdamping of high frequencies:** Can suppress important high-[[Frequency Response Function (FRF)]]
4. **Coupled modes for non-proportional damping:** Not suitable for systems with localized damping
5. **Difficult to determine coefficients:** Experimental identification challenging

### Validity Range
- **Appropriate for:** Systems where damping is distributed similarly to mass and stiffness
- **Less accurate for:** Systems with concentrated dampers or highly non-uniform damping
- **Good approximation when:** Damping ratios are similar across frequency range of interest
- **Not recommended for:** Systems with highly frequency-dependent damping or negative damping

## Advanced Topics

### Extended Rayleigh Damping

**Higher-order models:** 
$$
C = M\sum_{i=0}^{m} \alpha_i(M^{-1}K)^i
$$

**Cauchy damping:** 
$$
C = M f(M^{-1}K)
$$
where $f$ is a function chosen to match desired damping-frequency relationship

**Rational approximation:** For better frequency matching

### Non-proportional Damping Extensions

**Modal damping augmentation:** Add diagonal modal damping matrix:
$$
C = \Phi \text{diag}(2\zeta_1\omega_1, \ldots, 2\zeta_n\omega_n) \Phi^T
$$

**Combined approach:** Rayleigh damping plus modal correction:
$$
C = \alpha M + \beta K + \Phi D_m \Phi^T
$$
where $D_m$ is diagonal modal damping matrix

### Frequency-Dependent Rayleigh Damping

**Piecewise Rayleigh damping:** Different $(\alpha, \beta)$ pairs for different frequency bands

**Weighted combination:** 
$$
C = \sum_{k=1}^{p} w_k(\alpha_k M + \beta_k K)
$$
where weights $w_k$ may be frequency-dependent

### Experimental Identification

**Frequency domain methods:** Fit $\alpha, \beta$ to measured [[Frequency Response Function (FRF)]] functions

**Time domain methods:** System identification from free vibration or forced response

**Bayesian approaches:** Incorporate uncertainty in damping estimates

## Special Cases and Examples

### Building Structure Example

**10-story steel moment frame:**
- Fundamental period: $T_1 = 2.0\,\text{s}$ ($\omega_1 = 3.14\,\text{rad/s}$)
- Second mode period: $T_2 = 0.7\,\text{s}$ ($\omega_2 = 8.98\,\text{rad/s}$)
- Target damping: $\zeta = 0.02$ (2%) for both modes

**Calculate coefficients:**
$$
\alpha = \frac{2\zeta\omega_1\omega_2}{\omega_1 + \omega_2} = \frac{2\times0.02\times3.14\times8.98}{3.14+8.98} = 0.093\,\text{s}^{-1}
$$
$$
\beta = \frac{2\zeta}{\omega_1 + \omega_2} = \frac{2\times0.02}{3.14+8.98} = 0.0033\,\text{s}
$$

**Resulting damping ratios:**
- Mode 1 ($\omega_1 = 3.14$): $\zeta_1 = 0.02$
- Mode 2 ($\omega_2 = 8.98$): $\zeta_2 = 0.02$
- Mode 10 ($\omega_{10} = 31.4$): $\zeta_{10} = 0.053$ (overdamped!)

### Beam with Rayleigh Damping

**Cantilever steel beam:**
- Length $L = 2\,\text{m}$, cross-section $0.1\times0.01\,\text{m}$
- Material: $E = 200\,\text{GPa}$, $\rho = 7850\,\text{kg/m}^3$
- First two natural frequencies: $f_1 = 16.1\,\text{Hz}$, $f_2 = 101\,\text{Hz}$
- Target: 2% damping at both frequencies

**Finite element model:** 10 Euler-Bernoulli beam elements
- Mass matrix $M$, stiffness matrix $K$
- Rayleigh coefficients: $\alpha = 2.02\,\text{s}^{-1}$, $\beta = 3.16\times10^{-5}\,\text{s}$
- Modal damping: $\zeta_1 = 0.02$, $\zeta_2 = 0.02$, $\zeta_3 = 0.034$, $\zeta_4 = 0.056$, ...

### Seismic Analysis Example

**ASCE 7-16 requirements:** For steel moment frames:
- Effective damping: 2-5% of critical
- For response spectrum analysis: 5% damping typically used

**Rayleigh coefficients for 5% damping:**
- Control periods: $T_1 = 2.0\,\text{s}$, $T_2 = 0.2\,\text{s}$ (cover significant mass participation)
- $\omega_1 = 3.14\,\text{rad/s}$, $\omega_2 = 31.4\,\text{rad/s}$
- $\alpha = 0.502\,\text{s}^{-1}$, $\beta = 0.0029\,\text{s}$

### Numerical Stability Example

**Explicit dynamics problem:**
- Highest frequency: $\omega_{\max} = 1000\,\text{rad/s}$
- Rayleigh coefficients: $\alpha = 0.1$, $\beta = 0.001$
- Maximum damping ratio: $\zeta_{\max} = 0.5(0.1/1000 + 0.001\times1000) = 0.50005$
- Critical time step for central difference:
$$
\Delta t_{\text{crit}} = \frac{2}{1000}\left(\sqrt{1+0.50005^2} - 0.50005\right) = 0.00115\,\text{s}
$$

## Error Analysis

### Approximation Error

**For mode i:** Difference between target $\zeta_i^{\text{target}}$ and Rayleigh $\zeta_i^{\text{Rayleigh}}$:
$$
\epsilon_i = \zeta_i^{\text{target}} - \frac{1}{2}\left(\frac{\alpha}{\omega_i} + \beta\omega_i\right)
$$

**[[Root Mean Square (RMS)]] error over m modes:**
$$
\text{RMSE} = \sqrt{\frac{1}{m}\sum_{i=1}^{m} \epsilon_i^2}
$$

**Optimal coefficients:** Minimize RMSE subject to $\alpha, \beta \geq 0$

### Frequency Range Selection Error

**Effect of control frequency selection:** Poor choice of $\omega_a, \omega_b$ leads to:
- Underdamping in middle frequency range
- Overdamping at extremes
- Can be mitigated by using three or more control points with weighted least squares

### Modal Truncation Error

**For truncated [[Modal Analysis]]:** Using first $m$ modes ($m < n$):
- Error from neglected higher modes
- Stiffness-proportional damping amplifies error (higher modes more damped)
- Can use [[Mode Acceleration Method (MAM)]] or residual flexibility to reduce error

### Numerical Integration Error

**Time step sensitivity:** For stiffness-proportional damping:
- High-frequency modes heavily damped
- Can allow larger time steps in explicit integration
- But may suppress physically important high-frequency content

**Amplitude decay and period elongation:** [[Newmark Method]] with Rayleigh damping:
- Additional numerical damping beyond physical damping
- Need to verify time step sensitivity

## Relationship to Other Concepts

### Comparison with Modal Damping

**Rayleigh damping:**
- Defined in physical coordinates: $C = \alpha M + \beta K$
- Preserves modal orthogonality by construction
- Only two parameters for entire system
- Frequency dependence fixed by formula

**Modal damping:**
- Defined in modal coordinates: $C_m = \text{diag}(2\zeta_i\omega_i)$
- Can specify different $\zeta_i$ for each mode
- More flexibility but requires modal transformation
- No simple physical coordinate representation

### Connection to [[Viscous Damping]]

**Rayleigh as special case:** Rayleigh damping is a specific form of [[Viscous Damping]] with constrained structure

**General [[Viscous Damping]]:** Arbitrary symmetric positive semidefinite matrix $C$
- Does not generally preserve modal orthogonality
- Requires state-space formulation for analysis
- More parameters needed

### Relationship to Hysteretic Damping

**Complex stiffness model:** $K^* = K(1 + i\eta)$
- Frequency-independent damping ratio $\eta$
- Not directly comparable to Rayleigh damping

**Equivalent [[Viscous Damping]]:** At frequency $\omega$:
$$
c_{\text{eq}} = \frac{\eta k}{\omega} \Rightarrow \zeta = \frac{\eta}{2}
$$
For Rayleigh damping to match: $\alpha/\omega + \beta\omega = \eta$, which cannot hold for all $\omega$

### Extension to Non-proportional Damping

**When Rayleigh insufficient:** For systems with localized dampers, soil-structure interaction, or fluid-structure interaction

**Caughey damping series:** 
$$
C = M\sum_{k=0}^{N-1} a_k(M^{-1}K)^k
$$
Generalizes Rayleigh damping (which has $N=2$)

## Historical Context and Evolution

### Original Motivation

**Rayleigh's 1877 work:** In "The Theory of Sound", Rayleigh sought mathematical simplification for damped vibration analysis

**Key insight:** If damping distribution follows mass and stiffness distributions, [[Modal Analysis]] remains valid

**Early applications:** Analysis of musical instruments, clock escapements, and building vibrations

### Evolution Over Time

1. **1877-1950:** Theoretical development, limited practical application
2. **1950-1970:** Adoption in earthquake engineering and aerospace
3. **1970-1990:** Implementation in commercial finite element software
4. **1990-2010:** Recognition of limitations, development of alternatives
5. **2010-present:** Hybrid approaches combining Rayleigh with other damping models

### Modern Reformulations

- **Component mode synthesis:** Rayleigh damping for substructures
- **Multi-support excitation:** Different damping for different support motions
- **Performance-based design:** Frequency-dependent Rayleigh coefficients
- **Uncertainty quantification:** Probabilistic Rayleigh damping parameters

## Pedagogical Approach

### Teaching Strategies

1. **Physical analogies:** Dashpots connected to ground (αM) and parallel to springs (βK)
2. **Mathematical derivation:** From modal [[Decoupling]] requirement
3. **Numerical examples:** Simple 2-DOF systems to illustrate principles
4. **Software exercises:** Implement Rayleigh damping in MATLAB or finite element software
5. **Experimental correlation:** Compare Rayleigh model with measured damping

### Common Misconceptions

1. **"Rayleigh damping is always physically accurate":** It's a mathematical convenience, not always physically realistic
2. **"α and β can be negative":** Negative coefficients can lead to negative damping (instability)
3. **"Rayleigh damping works for any system":** Fails for systems with highly non-proportional damping
4. **"The two frequencies can be chosen arbitrarily":** Poor choice leads to unrealistic damping at other frequencies
5. **"Rayleigh damping is frequency-independent":** The coefficients are constant, but damping ratio varies with frequency

### Learning Resources

**Foundational Texts:**
- Clough & Penzien, "Dynamics of Structures" (Chapter 11)
- Chopra, "Dynamics of Structures: Theory and Applications to Earthquake Engineering"
- Bathe, "Finite Element Procedures"
- Craig & Kurdila, "Fundamentals of Structural Dynamics"

**Online Resources:**
- MIT OpenCourseWare: 2.003 Engineering Dynamics
- NISEE e-Library: Rayleigh damping in earthquake engineering
- Wolfram Demonstrations: Rayleigh damping visualization
- YouTube: Tutorials on implementing Rayleigh damping

**Software Tutorials:**
- ANSYS: Rayleigh damping in transient dynamics
- ABAQUS: Damping options in dynamic analysis
- MATLAB: Modal analysis with Rayleigh damping
- OpenSees: Rayleigh damping for seismic analysis

## Implementation in Software

### MATLAB Implementation

```matlab
function [alpha, beta, zeta] = rayleigh_coefficients(omega_target, zeta_target, omega_range)
% Compute Rayleigh damping coefficients to match target damping ratios
%
% Inputs:
%   omega_target: vector of target frequencies [rad/s]
%   zeta_target: vector of target damping ratios at omega_target
%   omega_range: optional frequency range for evaluation
%
% Outputs:
%   alpha: mass-proportional damping coefficient
%   beta: stiffness-proportional damping coefficient
%   zeta: damping ratios over omega_range (if provided)

    % For two target points
    if length(omega_target) == 2 && length(zeta_target) == 2
        omega1 = omega_target(1);
        omega2 = omega_target(2);
        zeta1 = zeta_target(1);
        zeta2 = zeta_target(2);
        
        % Solve linear system for alpha, beta
        A = [1/omega1, omega1; 1/omega2, omega2];
        b = 2*[zeta1; zeta2];
        x = A\b;
        alpha = x(1);
        beta = x(2);
        
    % For more than two points (least squares fit)
    elseif length(omega_target) > 2
        % Form least squares problem: 2*zeta_i = alpha/omega_i + beta*omega_i
        A = [1./omega_target(:), omega_target(:)];
        b = 2*zeta_target(:);
        
        % Solve with non-negativity constraints
        options = optimset('Display', 'off');
        x = lsqnonneg(A, b, options);
        alpha = x(1);
        beta = x(2);
        
    else
        error('Number of target points must be at least 2');
    end
    
    % Evaluate damping ratio function if frequency range provided
    if nargin >= 3 && nargout >= 3
        zeta = 0.5*(alpha./omega_range + beta*omega_range);
    else
        zeta = [];
    end
end

function [M, K, C] = assemble_rayleigh_damped_system(M_elem, K_elem, alpha, beta)
% Assemble global matrices with Rayleigh damping
%
% Inputs:
%   M_elem: cell array of element mass matrices
%   K_elem: cell array of element stiffness matrices
%   alpha: mass-proportional damping coefficient
%   beta: stiffness-proportional damping coefficient
%
% Outputs:
%   M: global mass matrix
%   K: global stiffness matrix
%   C: global damping matrix (Rayleigh)

    % Determine system size from first element
    n_dof = size(M_elem{1}, 1);
    n_nodes = length(M_elem);
    
    % Initialize global matrices
    M = zeros(n_dof * n_nodes);
    K = zeros(n_dof * n_nodes);
    
    % Assemble global matrices
    for i = 1:n_nodes
        dofs = (i-1)*n_dof + (1:n_dof);
        M(dofs, dofs) = M(dofs, dofs) + M_elem{i};
        K(dofs, dofs) = K(dofs, dofs) + K_elem{i};
    end
    
    % Apply boundary conditions (remove fixed DOFs)
    % ... (boundary condition implementation)
    
    % Form Rayleigh damping matrix
    C = alpha*M + beta*K;
end

function [freq, zeta, modes] = modal_analysis_rayleigh(M, K, C, n_modes)
% Perform modal analysis for Rayleigh-damped system
%
% Inputs:
%   M, K, C: mass, stiffness, damping matrices
%   n_modes: number of modes to compute
%
% Outputs:
%   freq: natural frequencies (Hz)
%   zeta: modal damping ratios
%   modes: mode shapes

    % Solve undamped eigenvalue problem
    [V, D] = eigs(K, M, n_modes, 'sm');
    omega = sqrt(diag(D));  % rad/s
    freq = omega/(2*pi);    % Hz
    
    % Normalize mode shapes to unit modal mass
    for i = 1:n_modes
        m_i = V(:,i)'*M*V(:,i);
        V(:,i) = V(:,i)/sqrt(m_i);
    end
    
    % Compute modal damping ratios for Rayleigh damping
    zeta = zeros(n_modes, 1);
    for i = 1:n_modes
        zeta(i) = 0.5*(V(:,i)'*C*V(:,i))/omega(i);
    end
    
    % Verify proportional damping (should be diagonal)
    C_modal = V'*C*V;
    off_diag_norm = norm(C_modal - diag(diag(C_modal)), 'fro');
    if off_diag_norm > 1e-10
        warning('Damping is non-proportional. Off-diagonal norm: %e', off_diag_norm);
    end
    
    modes = V;
end

% Example: 3-DOF shear building with Rayleigh damping
function example_rayleigh_shear_building()
    % Building parameters
    n_stories = 3;
    m = 1000 * ones(n_stories, 1);  % kg (floor masses)
    k = 1e6 * ones(n_stories, 1);   % N/m (story stiffnesses)
    
    % Assemble mass and stiffness matrices
    M = diag(m);
    K = zeros(n_stories);
    for i = 1:n_stories
        K(i,i) = K(i,i) + k(i);
        if i > 1
            K(i,i-1) = K(i,i-1) - k(i);
            K(i-1,i) = K(i-1,i) - k(i);
            K(i-1,i-1) = K(i-1,i-1) + k(i);
        end
    end
    
    % Compute undamped natural frequencies
    [V, D] = eig(K, M);
    omega = sqrt(diag(D));
    [omega, idx] = sort(omega);
    V = V(:, idx);
    
    % Set target damping: 2% for modes 1 and 3
    omega_target = [omega(1); omega(3)];
    zeta_target = [0.02; 0.02];
    
    % Compute Rayleigh coefficients
    [alpha, beta] = rayleigh_coefficients(omega_target, zeta_target);
    
    % Form damping matrix
    C = alpha*M + beta*K;
    
    % Compute modal damping ratios
    n_modes = n_stories;
    [freq, zeta_modal, modes] = modal_analysis_rayleigh(M, K, C, n_modes);
    
    % Display results
    fprintf('Rayleigh coefficients:\n');
    fprintf('  alpha = %.4f s^{-1}\n', alpha);
    fprintf('  beta = %.6f s\n', beta);
    fprintf('\nModal properties:\n');
    for i = 1:n_modes
        fprintf('Mode %d: f = %.2f Hz, ζ = %.3f%%\n', ...
                i, freq(i), 100*zeta_modal(i));
    end
    
    % Plot damping ratio vs frequency
    omega_plot = linspace(0.5*omega(1), 2*omega(end), 1000);
    zeta_plot = 0.5*(alpha./omega_plot + beta*omega_plot);
    
    figure;
    plot(omega_plot, 100*zeta_plot, 'b-', 'LineWidth', 2);
    hold on;
    plot(omega, 100*zeta_modal, 'ro', 'MarkerSize', 10, 'LineWidth', 2);
    xlabel('Frequency (rad/s)');
    ylabel('Damping Ratio (%)');
    title('Rayleigh Damping: Frequency Dependence');
    legend('Rayleigh curve', 'Modal values', 'Location', 'best');
    grid on;
end
```

### Python Implementation

```python
import numpy as np
import scipy.linalg as la
import matplotlib.pyplot as plt

class RayleighDamping:
    """Class for Rayleigh damping analysis"""
    
    def __init__(self, M, K):
        """
        Initialize system with mass and stiffness matrices
        
        Parameters
        ----------
        M : ndarray
            Mass matrix (n x n)
        K : ndarray
            Stiffness matrix (n x n)
        """
        self.M = M
        self.K = K
        self.n = M.shape[0]
        
        # Compute undamped modal properties
        self._compute_undamped_modes()
    
    def _compute_undamped_modes(self):
        """Solve undamped eigenvalue problem"""
        # Solve generalized eigenvalue problem
        self.omega, self.Phi = la.eigh(self.K, self.M)
        self.omega = np.sqrt(self.omega)  # rad/s
        self.freq = self.omega / (2*np.pi)  # Hz
        
        # Sort by frequency
        idx = np.argsort(self.omega)
        self.omega = self.omega[idx]
        self.freq = self.freq[idx]
        self.Phi = self.Phi[:, idx]
        
        # Mass-normalize mode shapes
        for i in range(self.n):
            m_i = self.Phi[:, i].T @ self.M @ self.Phi[:, i]
            self.Phi[:, i] = self.Phi[:, i] / np.sqrt(m_i)
    
    def compute_coefficients(self, omega_target, zeta_target):
        """
        Compute Rayleigh coefficients to match target damping ratios
        
        Parameters
        ----------
        omega_target : array_like
            Target frequencies (rad/s)
        zeta_target : array_like
            Target damping ratios at omega_target
        
        Returns
        -------
        alpha : float
            Mass-proportional coefficient
        beta : float
            Stiffness-proportional coefficient
        """
        omega_target = np.asarray(omega_target)
        zeta_target = np.asarray(zeta_target)
        
        if len(omega_target) == 2 and len(zeta_target) == 2:
            # Exact solution for two points
            omega1, omega2 = omega_target
            zeta1, zeta2 = zeta_target
            
            A = np.array([[1/omega1, omega1],
                          [1/omega2, omega2]])
            b = 2 * np.array([zeta1, zeta2])
            x = np.linalg.solve(A, b)
            alpha, beta = x
            
        elif len(omega_target) >= 2:
            # Least squares solution for multiple points
            A = np.column_stack([1/omega_target, omega_target])
            b = 2 * zeta_target
            x, residuals, rank, s = np.linalg.lstsq(A, b, rcond=None)
            alpha, beta = x
            
            # Ensure non-negative coefficients
            alpha = max(alpha, 0)
            beta = max(beta, 0)
            
        else:
            raise ValueError("At least two target points required")
        
        return alpha, beta
    
    def form_damping_matrix(self, alpha, beta):
        """
        Form Rayleigh damping matrix
        
        Parameters
        ----------
        alpha : float
            Mass-proportional coefficient
        beta : float
            Stiffness-proportional coefficient
        
        Returns
        -------
        C : ndarray
            Damping matrix
        """
        return alpha * self.M + beta * self.K
    
    def compute_modal_damping(self, alpha, beta, n_modes=None):
        """
        Compute modal damping ratios for given Rayleigh coefficients
        
        Parameters
        ----------
        alpha : float
            Mass-proportional coefficient
        beta : float
            Stiffness-proportional coefficient
        n_modes : int, optional
            Number of modes to compute (default: all)
        
        Returns
        -------
        zeta : ndarray
            Modal damping ratios
        """
        if n_modes is None:
            n_modes = self.n
        
        zeta = np.zeros(n_modes)
        for i in range(n_modes):
            zeta[i] = 0.5 * (alpha / self.omega[i] + beta * self.omega[i])
        
        return zeta
    
    def frequency_response(self, alpha, beta, omega_exc, F):
        """
        Compute frequency response for harmonic excitation
        
        Parameters
        ----------
        alpha : float
            Mass-proportional coefficient
        beta : float
            Stiffness-proportional coefficient
        omega_exc : array_like
            Excitation frequencies (rad/s)
        F : ndarray
            Force vector (n x 1) or (n x len(omega_exc))
        
        Returns
        -------
        X : ndarray
            Complex displacement amplitudes
        """
        C = self.form_damping_matrix(alpha, beta)
        
        if F.ndim == 1:
            F = F.reshape(-1, 1)
        
        omega_exc = np.asarray(omega_exc)
        n_freq = len(omega_exc)
        X = np.zeros((self.n, n_freq), dtype=complex)
        
        for i, omega in enumerate(omega_exc):
            # Dynamic stiffness matrix
            D = -omega**2 * self.M + 1j * omega * C + self.K
            
            # Solve for response
            if F.shape[1] == 1:
                X[:, i] = la.solve(D, F.flatten())
            else:
                X[:, i] = la.solve(D, F[:, i])
        
        return X
    
    def plot_damping_curve(self, alpha, beta, omega_range=None, ax=None):
        """
        Plot damping ratio vs frequency curve
        
        Parameters
        ----------
        alpha : float
            Mass-proportional coefficient
        beta : float
            Stiffness-proportional coefficient
        omega_range : tuple, optional
            Frequency range to plot (min, max)
        ax : matplotlib axis, optional
            Axis to plot on
        """
        if ax is None:
            fig, ax = plt.subplots(figsize=(8, 6))
        
        if omega_range is None:
            omega_min = 0.5 * self.omega[0]
            omega_max = 2.0 * self.omega[-1]
        else:
            omega_min, omega_max = omega_range
        
        omega_plot = np.linspace(omega_min, omega_max, 1000)
        zeta_plot = 0.5 * (alpha / omega_plot + beta * omega_plot)
        
        # Modal damping ratios
        zeta_modal = self.compute_modal_damping(alpha, beta)
        
        ax.plot(omega_plot, 100*zeta_plot, 'b-', linewidth=2, label='Rayleigh curve')
        ax.plot(self.omega[:len(zeta_modal)], 100*zeta_modal, 'ro', 
                markersize=8, label='Modal values')
        
        ax.set_xlabel('Frequency (rad/s)')
        ax.set_ylabel('Damping Ratio (%)')
        ax.set_title('Rayleigh Damping Frequency Dependence')
        ax.legend()
        ax.grid(True, alpha=0.3)
        
        return ax

# Example usage
if __name__ == "__main__":
    # Create a simple 5-DOF shear building model
    n_dof = 5
    m = 1000.0  # kg (each floor)
    k = 1e6     # N/m (each story)
    
    # Mass matrix (diagonal)
    M = m * np.eye(n_dof)
    
    # Stiffness matrix (tridiagonal)
    K = np.zeros((n_dof, n_dof))
    for i in range(n_dof):
        K[i, i] = 2 * k
        if i > 0:
            K[i, i-1] = -k
            K[i-1, i] = -k
    K[0, 0] = k  # First story only connected to ground
    
    # Create Rayleigh damping analyzer
    rd = RayleighDamping(M, K)
    
    print(f"Natural frequencies: {rd.freq:.2f} Hz")
    
    # Set target damping: 2% at first and third modes
    omega_target = [rd.omega[0], rd.omega[2]]
    zeta_target = [0.02, 0.02]
    
    # Compute Rayleigh coefficients
    alpha, beta = rd.compute_coefficients(omega_target, zeta_target)
    print(f"\nRayleigh coefficients:")
    print(f"  alpha = {alpha:.4f} s⁻¹")
    print(f"  beta  = {beta:.6f} s")
    
    # Compute modal damping ratios
    zeta_modal = rd.compute_modal_damping(alpha, beta)
    print(f"\nModal damping ratios:")
    for i, (f, z) in enumerate(zip(rd.freq, zeta_modal)):
        print(f"  Mode {i+1}: f = {f:.2f} Hz, ζ = {100*z:.2f}%")
    
    # Plot damping curve
    fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))
    
    rd.plot_damping_curve(alpha, beta, ax=ax1)
    
    # Frequency response example
    omega_exc = np.linspace(0, 50, 500)
    F = np.zeros(n_dof)
    F[0] = 1000  # Force on first floor
    
    X = rd.frequency_response(alpha, beta, omega_exc, F)
    
    # Plot frequency response of first floor
    ax2.plot(omega_exc, np.abs(X[0, :]), 'b-', linewidth=2)
    ax2.set_xlabel('Excitation Frequency (rad/s)')
    ax2.set_ylabel('|X₁(ω)| (m/N)')
    ax2.set_title('Frequency Response of First Floor')
    ax2.grid(True, alpha=0.3)
    
    plt.tight_layout()
    plt.show()
```

### Commercial Software Implementation

**ANSYS Mechanical:**
```apdl
! Mass and stiffness proportional damping
ALPHAD, 0.1      ! Alpha coefficient
BETAD, 0.001    ! Beta coefficient

! Modal analysis with Rayleigh damping
ANTYPE, MODAL    ! Modal analysis
MODOPT, LANB, 10 ! Block Lanczos, 10 modes
MXPAND, 10       ! Expand 10 modes
SOLVE

! Transient analysis with Rayleigh damping
ANTYPE, TRANS    ! Transient analysis
TRNOPT, FULL     ! Full transient
TIMINT, ON       ! Time integration on
ALPHAD, 0.1
BETAD, 0.001
KBC, 1           ! Stepped loads
TIME, 10         ! End time
NSUBST, 1000     ! Number of substeps
SOLVE
```

**ABAQUS:**
```inp
*DAMPING, RAYLEIGH
0.1, 0.001

*STEP, NAME=Modal
*FREQUENCY
10
*END STEP

*STEP, NAME=Transient
*DYNAMIC
0.01, 10.0
*END STEP
```

**NASTRAN:**
```bdf
$ Direct matrix input for Rayleigh damping
PARAM, ALPHA1, 0.1
PARAM, BETA1, 0.001

$ Modal analysis
SOL 103
METHOD = 1
$
$ Transient analysis
SOL 109
TSTEP = 1
```

**OpenSees:**
```tcl
# Rayleigh damping in OpenSees
set alphaM 0.1;    # mass-proportional
set betaK 0.001;   # stiffness-proportional
set betaKinit 0.0; # initial stiffness-proportional
set betaKcomm 0.0; # committed stiffness-proportional

rayleigh $alphaM $betaK $betaKinit $betaKcomm

# Alternative: specify damping at two periods
set xi 0.02;     # damping ratio
set T1 2.0;      # first mode period
set T2 0.2;      # second mode period

set w1 [expr 2*3.14159/$T1]
set w2 [expr 2*3.14159/$T2]
set a0 [expr $xi*2*$w1*$w2/($w1 + $w2)]
set a1 [expr $xi*2/($w1 + $w2)]

rayleigh $a0 0.0 $a1 0.0
```

## See Also

- [[Viscous Damping]]
- [[Modal Damping]]
- [[Proportional Damping]]
- [[Non-proportional Damping]]
- [[Critical Damping]]
- [[Damping Ratio]]
- [[Mass Matrix]]
- [[Stiffness Matrix]]
- [[Modal Analysis]]
- [[Finite Element Analysis (FEA)]]
- [[Structural Dynamics]]
- [[Seismic Analysis]]
- [[Caughey Damping]]
- [[Hysteretic Damping]]
- [[Frequency-Dependent Damping]]

---

*Note: Rayleigh damping provides a mathematically convenient and computationally efficient approach to modeling [[Viscous Damping]] in linear dynamic systems. While its assumptions of proportional damping may not always match physical reality, its ability to preserve modal orthogonality makes it invaluable for practical engineering analysis, particularly in seismic design and vibration analysis of complex structures.*
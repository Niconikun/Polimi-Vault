## Formal Definition

The **Craig-Bampton Method** (also known as **Fixed-Interface Component Mode Synthesis**) is a [[Dynamic Substructuring]] technique that reduces large finite element models by partitioning them into substructures and representing each substructure with a reduced set of [[Generalized Coordinates]]. This method combines fixed-interface normal modes and constraint modes to create a transformation matrix that significantly reduces the number of [[degrees of freedom]] while preserving the dynamic characteristics and interface compatibility between substructures.

## Historical Development

### Key Milestones
- **1968:** Roy R. Craig Jr. and Mervyn C. C. Bampton publish their seminal paper "Coupling of Substructures for Dynamic Analyses"
- **1970s:** Initial implementation in NASTRAN and other commercial finite element software
- **1980s:** Extension to rotating machinery and aerospace applications
- **1990s:** Development of automated substructuring algorithms and parallel implementations
- **2000s:** Integration with optimization and design exploration workflows
- **2010s:** Application to uncertainty quantification and model updating
- **2020s:** Implementation in real-time simulation and digital twin technologies

### Foundational Contributors
1. **Roy R. Craig Jr. (b. 1930):** Co-developed the method with Bampton
2. **Mervyn C. C. Bampton (1932-2011):** Co-developed the method with Craig
3. **Robert L. Harder (1927-2003):** Contributed to implementation in NASTRAN
4. **Thomas K. Caughey (1924-2013):** Advanced component mode synthesis techniques
5. **R. R. Craig Jr. and A. J. Kurdila:** Subsequent developments in [[Dynamic Substructuring]]

## Mathematical Formulation

### Basic Partitioning

**Substructure partitioning:** Divide the full finite element model into substructures (components):

For each substructure $s$, partition [[degrees of freedom]] into:
- **Interface DOFs $x_b$:** Boundary/connection points
- **Internal DOFs $x_i$:** Interior points

**Equation of motion for substructure $s$:**
$$
\begin{bmatrix}
M_{ii} & M_{ib} \\
M_{bi} & M_{bb}
\end{bmatrix}
\begin{bmatrix}
\ddot{x}_i \\ \ddot{x}_b
\end{bmatrix}
+
\begin{bmatrix}
K_{ii} & K_{ib} \\
K_{bi} & K_{bb}
\end{bmatrix}
\begin{bmatrix}
x_i \\ x_b
\end{bmatrix}
=
\begin{bmatrix}
0 \\ f_b
\end{bmatrix}
$$

### Transformation Matrix

**Craig-Bampton transformation:** 
$$
\begin{bmatrix}
x_i \\ x_b
\end{bmatrix}
=
\begin{bmatrix}
\Phi_{ik} & \Psi_{ib} \\
0 & I_{bb}
\end{bmatrix}
\begin{bmatrix}
p_k \\ x_b
\end{bmatrix}
= T
\begin{bmatrix}
p_k \\ x_b
\end{bmatrix}
$$

where:
- $\Phi_{ik}$: Fixed-interface normal modes (eigenmodes with boundary fixed)
- $\Psi_{ib} = -K_{ii}^{-1} K_{ib}$: Constraint modes (static response to unit displacements at boundaries)
- $p_k$: Modal coordinates ($k \ll \text{dim}(x_i)$)
- $I_{bb}$: Identity matrix for boundary DOFs

### Reduced Matrices

**Reduced mass matrix:**
$$
M_{\text{red}} = T^T M T =
\begin{bmatrix}
I_{kk} & M_{kb} \\
M_{bk} & M_{bb}^{\text{red}}
\end{bmatrix}
$$

**Reduced stiffness matrix:**
$$
K_{\text{red}} = T^T K T =
\begin{bmatrix}
\Lambda_{kk} & 0 \\
0 & K_{bb}^{\text{red}}
\end{bmatrix}
$$

**where:**
- $I_{kk}$: Identity matrix (mass-normalized modes)
- $\Lambda_{kk} = \text{diag}(\omega_k^2)$: Diagonal matrix of squared fixed-interface frequencies
- $M_{kb} = \Phi_{ik}^T M_{ii} \Psi_{ib} + \Phi_{ik}^T M_{ib}$
- $M_{bb}^{\text{red}} = \Psi_{ib}^T M_{ii} \Psi_{ib} + \Psi_{ib}^T M_{ib} + M_{bi} \Psi_{ib} + M_{bb}$
- $K_{bb}^{\text{red}} = K_{bb} - K_{bi} K_{ii}^{-1} K_{ib}$

### Assembly of Substructures

**For multiple substructures:** After reduction, substructures are assembled using interface compatibility:

**Interface constraints:** $x_b^{(1)} = x_b^{(2)} = \ldots = x_b^{(N)}$ at connection points

**Assembly equation:** 
$$
\begin{bmatrix}
M_{\text{red}}^{(1)} & 0 & \cdots \\
0 & M_{\text{red}}^{(2)} & \cdots \\
\vdots & \vdots & \ddots
\end{bmatrix}
\begin{bmatrix}
\ddot{q}^{(1)} \\ \ddot{q}^{(2)} \\ \vdots
\end{bmatrix}
+
\begin{bmatrix}
K_{\text{red}}^{(1)} & 0 & \cdots \\
0 & K_{\text{red}}^{(2)} & \cdots \\
\vdots & \vdots & \ddots
\end{bmatrix}
\begin{bmatrix}
q^{(1)} \\ q^{(2)} \\ \vdots
\end{bmatrix}
=
\begin{bmatrix}
f^{(1)} \\ f^{(2)} \\ \vdots
\end{bmatrix}
$$

with interface constraints enforced.

## Fundamental Principles

### Fixed-Interface Normal Modes

**Definition:** Eigenmodes obtained by fixing all boundary DOFs:
$$
(K_{ii} - \omega_k^2 M_{ii}) \phi_k = 0
$$

**Properties:**
- Represent internal dynamic behavior
- Orthogonal with respect to $M_{ii}$ and $K_{ii}$
- Mass-normalized: $\Phi_{ik}^T M_{ii} \Phi_{ik} = I$, $\Phi_{ik}^T K_{ii} \Phi_{ik} = \Lambda$

**Selection criteria:** Include modes up to:
- Frequency cutoff (e.g., 1.5× maximum frequency of interest)
- Effective mass participation (e.g., 90% in each direction)
- Modal [[Strain Energy]] criteria

### Constraint Modes

**Definition:** Static deformation shapes due to unit displacements at boundary DOFs:
$$
\Psi_{ib} = -K_{ii}^{-1} K_{ib}
$$

**Physical interpretation:** Columns of $\Psi_{ib}$ represent the static deformation when one boundary DOF is given unit displacement while all others are fixed.

**Properties:**
- Ensure exact static response at interface
- Guarantee displacement compatibility between substructures
- Provide correct load paths

### Reduction Error Control

**Guyan reduction error:** Craig-Bampton improves upon Guyan (static) reduction by:
- Including dynamic modes for internal behavior
- Maintaining exact static response at boundaries
- Better approximation of inertial effects

**Frequency range validity:** Reduced model accurate up to approximately 1.5× highest retained mode frequency.

### Interface Compatibility

**Geometric compatibility:** Same displacements at connected interfaces:
$$
x_b^{(m)} = x_b^{(n)} \text{ for connected substructures } m \text{ and } n
$$

**Force equilibrium:** Interface forces sum to zero at connections

**Assembly methods:**
- Direct assembly with boolean matrices
- Lagrange multipliers
- Penalty methods

## Theoretical Framework

### Exactness Properties

**Static exactness:** For static problems with forces applied only at boundaries, Craig-Bampton gives exact solution regardless of number of kept modes.

**Proof:** Static equation with boundary forces only:
$$
\begin{bmatrix}
K_{ii} & K_{ib} \\
K_{bi} & K_{bb}
\end{bmatrix}
\begin{bmatrix}
x_i \\ x_b
\end{bmatrix}
=
\begin{bmatrix}
0 \\ f_b
\end{bmatrix}
$$

From first equation: $x_i = -K_{ii}^{-1} K_{ib} x_b = \Psi_{ib} x_b$

Thus exact solution captured by constraint modes alone.

**Dynamic completeness:** With all fixed-interface modes included, model is exact.

### Error Bounds

**Modal truncation error:** For harmonic response at frequency $\omega$, error bounded by:
$$
\|x_{\text{exact}} - x_{\text{red}}\| \leq C \sum_{k \notin \text{retained}} \frac{\|\phi_k^T f\|}{\omega_k^2 - \omega^2}
$$

where $C$ depends on [[Damping]] and excitation.

**Mass coupling error:** Off-diagonal terms $M_{kb}$ couple boundary and modal coordinates, important for dynamic response.

### Convergence Analysis

**As number of kept modes increases:**
- Natural frequencies converge from above (upper bounds)
- Mode shapes converge in [[Strain Energy]] norm
- [[Frequency Response Function (FRF)]] converges pointwise

**Rate of convergence:** Depends on spectral gap and spatial distribution of loads.

### Alternative Formulations

**Free-interface methods:** Use free-interface modes instead of fixed-interface
**Hybrid methods:** Combine fixed and free interface approaches
**Double mode synthesis:** Include attachment modes or residual flexibility

## Classification and Variants

### By Interface Treatment
1. **Fixed-interface CMS:** Original Craig-Bampton method
2. **Free-interface CMS:** Use free-interface normal modes (MacNeal, Rubin)
3. **Hybrid-interface CMS:** Mixed fixed/free interfaces
4. **Loaded-interface CMS:** Include static modes for interface loading

### By Mode Selection Criteria
1. **Frequency truncation:** Keep modes below cutoff frequency
2. **Modal effective mass:** Keep modes with significant effective mass
3. **Modal [[Strain Energy]]:** Keep modes with high [[Strain Energy]] in critical regions
4. **Load-dependent modes:** Include static correction modes for specific loads

### By Application Domain
1. **Structural CMS:** For buildings, bridges, aircraft
2. **Rotordynamic CMS:** For rotating machinery with gyroscopic effects
3. **Acoustic CMS:** For vibro-acoustic problems
4. **Thermal-structural CMS:** For coupled thermal-structural analysis

### By Implementation Approach
1. **Manual CMS:** User-defined substructuring
2. **Automatic CMS:** Automated partitioning algorithms
3. **Parallel CMS:** Distributed computation of substructures
4. **Adaptive CMS:** Dynamic mode selection based on error estimates

## Derivation and Proof

### Derivation from Substructuring Principles

**Starting point:** Partition equations of motion for substructure:

**Static condensation:** From static equilibrium with no internal forces:
$$
K_{ii} x_i + K_{ib} x_b = 0 \Rightarrow x_i = -K_{ii}^{-1} K_{ib} x_b = \Psi_{ib} x_b
$$

**Dynamic correction:** Add dynamic modes to capture inertial effects:
$$
x_i = \Psi_{ib} x_b + \Phi_{ik} p_k
$$
where $\Phi_{ik}$ are fixed-interface modes satisfying $(K_{ii} - \omega_k^2 M_{ii}) \phi_k = 0$

**Matrix form:** 
$$
\begin{bmatrix}
x_i \\ x_b
\end{bmatrix}
=
\begin{bmatrix}
\Phi_{ik} & \Psi_{ib} \\
0 & I
\end{bmatrix}
\begin{bmatrix}
p_k \\ x_b
\end{bmatrix}
$$

### Proof of Orthogonality Properties

**Fixed-interface modes:** Solve $K_{ii} \Phi_{ik} = M_{ii} \Phi_{ik} \Lambda_{kk}$

**Mass orthogonality:** 
$$
\Phi_{ik}^T M_{ii} \Phi_{ik} = I
$$
by mass normalization.

**Stiffness orthogonality:**
$$
\Phi_{ik}^T K_{ii} \Phi_{ik} = \Lambda_{kk}
$$

**Constraint mode properties:** From definition $\Psi_{ib} = -K_{ii}^{-1} K_{ib}$:

**Orthogonality to fixed-interface modes:**
$$
\Phi_{ik}^T K_{ii} \Psi_{ib} = -\Phi_{ik}^T K_{ib} = 0
$$
since $\Phi_{ik}$ satisfy fixed boundary conditions.

### Reduction Proof

**Transform equations:** Pre- and post-multiply by $T^T$ and $T$:

**Mass matrix:** 
$$
T^T M T =
\begin{bmatrix}
\Phi_{ik}^T & 0 \\
\Psi_{ib}^T & I
\end{bmatrix}
\begin{bmatrix}
M_{ii} & M_{ib} \\
M_{bi} & M_{bb}
\end{bmatrix}
\begin{bmatrix}
\Phi_{ik} & \Psi_{ib} \\
0 & I
\end{bmatrix}
$$

**Compute blocks:**
- $M_{kk} = \Phi_{ik}^T M_{ii} \Phi_{ik} = I$ (mass-normalized)
- $M_{kb} = \Phi_{ik}^T M_{ii} \Psi_{ib} + \Phi_{ik}^T M_{ib}$
- $M_{bb}^{\text{red}} = \Psi_{ib}^T M_{ii} \Psi_{ib} + \Psi_{ib}^T M_{ib} + M_{bi} \Psi_{ib} + M_{bb}$

**Stiffness matrix:**
$$
T^T K T =
\begin{bmatrix}
\Phi_{ik}^T & 0 \\
\Psi_{ib}^T & I
\end{bmatrix}
\begin{bmatrix}
K_{ii} & K_{ib} \\
K_{bi} & K_{bb}
\end{bmatrix}
\begin{bmatrix}
\Phi_{ik} & \Psi_{ib} \\
0 & I
\end{bmatrix}
$$

**Compute blocks:**
- $K_{kk} = \Phi_{ik}^T K_{ii} \Phi_{ik} = \Lambda_{kk}$
- $K_{kb} = \Phi_{ik}^T K_{ii} \Psi_{ib} + \Phi_{ik}^T K_{ib} = 0$ (by orthogonality)
- $K_{bb}^{\text{red}} = \Psi_{ib}^T K_{ii} \Psi_{ib} + \Psi_{ib}^T K_{ib} + K_{bi} \Psi_{ib} + K_{bb} = K_{bb} - K_{bi} K_{ii}^{-1} K_{ib}$

## Physical Interpretation

### Mechanical Analogy

**Substructure as "super-element":** Each reduced substructure behaves like:
- **Constraint modes:** Represent how substructure deforms when boundaries move
- **Fixed-interface modes:** Represent internal vibrations when boundaries are clamped

**Assembly analogy:** Like connecting springs (constraint modes) with attached masses (modal coordinates)

### Wave Propagation View

**Short-wavelength vs. long-wavelength:**
- Constraint modes capture long-wavelength deformation (global behavior)
- Fixed-interface modes capture short-wavelength vibration (local behavior)

**Frequency filtering:** Low-[[Frequency Response Function (FRF)]] dominated by constraint modes, high-frequency by fixed-interface modes.

### Energy Partitioning

**[[Strain Energy]] distribution:**
- In constraint modes: Energy from interface motion
- In fixed-interface modes: Energy from internal vibration

**Load paths:** Constraint modes show how forces flow through structure from boundaries.

## Applications

### Engineering Disciplines
1. **Aerospace Engineering:** Aircraft, spacecraft, launch vehicle analysis
2. **Automotive Engineering:** Full vehicle NVH analysis, crash simulation
3. **Civil Engineering:** Large building and bridge analysis
4. **Mechanical Engineering:** Machinery, rotating equipment, assemblies
5. **Marine Engineering:** Ship and offshore platform dynamics

### Specific Applications
1. **NVH Analysis:** Noise, vibration, and harshness in automotive and aerospace
2. **Seismic Analysis:** Building response to earthquakes
3. **Crashworthiness:** Vehicle crash simulation with component models
4. **Aeroelasticity:** Aircraft flutter analysis with reduced structural models
5. **Control System Design:** Reduced-order models for controller design

### Industrial Software Implementation
- **NASTRAN:** CMSUP entry for Craig-Bampton reduction
- **ANSYS:** Component Mode Synthesis (CMS) technology
- **ABAQUS:** Substructuring and *SUBSTRUCTURE options
- **Siemens NX/Nastran:** Superelement and CMS capabilities
- **MSC Nastran:** SE Bulk Data entries for superelements

## Implementation Considerations

### Substructure Partitioning Strategies

**Manual partitioning:** Based on:
- Physical components (wings, fuselage, engine)
- Functional units (chassis, powertrain, body)
- Material boundaries (steel, aluminum, composite)

**Automatic partitioning:** Algorithms for:
- Graph partitioning (METIS, SCOTCH)
- Interface minimization
- Load balancing for parallel processing

**Partitioning criteria:**
- Number of interface DOFs (minimize)
- Substructure size balance
- Physical connectivity

### Mode Selection Criteria

**Frequency cutoff:** Keep all modes below $f_{\text{cut}} = \alpha f_{\text{max}}$, typically $\alpha = 1.5-2.0$

**Modal effective mass:** Keep modes until cumulative effective mass exceeds threshold (e.g., 90%) in each direction:
$$
m_{\text{eff},k} = \frac{(\phi_k^T M r)^2}{\phi_k^T M \phi_k}
$$
where $r$ is [[Rigid Body]] vector.

**Modal strain energy:** Keep modes with high strain energy in critical regions.

**Load-dependent vectors:** Include static modes for specific load cases.

### Computational Aspects

**Matrix operations required:**
1. Solve $K_{ii} \Phi = M_{ii} \Phi \Lambda$ (partial eigensolution)
2. Compute $\Psi_{ib} = -K_{ii}^{-1} K_{ib}$ (static condensation)
3. Form reduced matrices $M_{\text{red}}, K_{\text{red}}$

**Numerical methods:**
- For large $K_{ii}$: Use sparse direct solvers or iterative methods
- For eigenproblem: Lanczos, subspace iteration, AMLS
- For $K_{ii}^{-1} K_{ib}$: Solve multiple right-hand sides efficiently

### Assembly and Solution

**Interface handling methods:**
1. **Direct assembly:** Eliminate redundant interface DOFs
2. **Lagrange multipliers:** Enforce compatibility exactly
3. **Penalty methods:** Approximate enforcement with stiff springs
4. **Master-slave elimination:** Retain master DOFs, eliminate slaves

**Recovery of internal responses:** After solving reduced system:
$$
x_i = \Phi_{ik} p_k + \Psi_{ib} x_b
$$

**Stress recovery:** May require [[mode acceleration method]] for accurate stresses.

## Advantages and Limitations

### Strengths
1. **Significant model reduction:** DOFs reduced by orders of magnitude
2. **Exact static behavior:** Constraint modes ensure exact static response at boundaries
3. **Component reuse:** Substructure models can be reused in different assemblies
4. **Parallel processing:** Substructure analysis can be done in parallel
5. **Commercial software support:** Widely implemented in major FE codes

### Weaknesses
1. **Fixed-interface assumption:** May over-stiffen substructure if interfaces are actually flexible
2. **Mode selection difficulty:** Choosing appropriate number of modes is nontrivial
3. **Interface growth:** Many interface DOFs can limit reduction
4. **Nonlinear limitations:** Primarily for linear dynamics (extensions to nonlinear exist)
5. **[[Damping]] modeling:** Complex to include detailed [[Damping]] in reduced model

### Validity Range
- **Excellent for:** Linear dynamic analysis, [[Frequency Response Function (FRF)]], [[Modal Analysis]]
- **Good for:** Transient response with bandwidth-limited excitation
- **Limited for:** Nonlinear analysis, high-frequency dynamics (> 2× highest retained mode)
- **Not suitable for:** Problems with significant nonlinearities at interfaces

## Advanced Topics

### Craig-Bampton with Free Interfaces

**Alternative formulation:** Use free-interface normal modes instead of fixed-interface:

**Transformation:**
$$
\begin{bmatrix}
x_i \\ x_b
\end{bmatrix}
=
\begin{bmatrix}
\Phi_{ik}^{\text{free}} & \Psi_{ib}^{\text{residual}} \\
\Phi_{bk}^{\text{free}} & I
\end{bmatrix}
\begin{bmatrix}
p_k \\ x_b
\end{bmatrix}
$$

**Advantages:** Better for components with flexible interfaces
**Disadvantages:** More complex, may require residual flexibility modes

### Modal Truncation Augmentation

**Residual flexibility:** Add static correction for truncated modes:
$$
\Psi_{ib}^{\text{residual}} = -K_{ii}^{-1} K_{ib} - \sum_{k=1}^{m} \frac{\phi_k \phi_k^T}{\omega_k^2} K_{ib}
$$

**Improved convergence:** Better accuracy with fewer modes.

### Nonlinear Craig-Bampton

**For geometric nonlinearities:** Use modal derivatives or implicit condensation

**For material nonlinearities:** Employ system equivalent reduction expansion process (SEREP) or proper orthogonal decomposition (POD)

**Interface nonlinearities:** Include nonlinear joint models at interfaces.

### Uncertainty Quantification

**Probabilistic Craig-Bampton:** Treat substructure parameters as random variables

**Interval analysis:** Account for parameter uncertainties with bounds

**Model updating:** Use experimental data to update reduced models.

## Special Cases and Examples

### Aircraft Wing-Body Example

**Substructure 1 (Wing):**
- Internal DOFs: 100,000
- Interface DOFs: 500 (at wing-body connection)
- Fixed-interface modes kept: 50 (up to 50 Hz)
- Reduction: 100,500 → 550 DOFs (182× reduction)

**Substructure 2 (Fuselage):**
- Internal DOFs: 200,000
- Interface DOFs: 500 + 300 (wing + tail connections)
- Fixed-interface modes kept: 80 (up to 40 Hz)
- Reduction: 200,800 → 880 DOFs (228× reduction)

**Assembly:** 550 + 880 = 1,430 DOFs (vs. original 301,300 DOFs, 211× reduction)

**Accuracy:** Natural frequencies within 1% up to 30 Hz.

### Automotive Chassis Example

**Components:** Body, suspension, powertrain, seats
**Interfaces:** Mounting points, joints
**Reduction:** 2 million DOFs → 5,000 DOFs (400× reduction)
**Application:** Full vehicle NVH analysis up to 200 Hz

### Spacecraft Example

**Modular assembly:** Bus, payload, solar arrays, antennas
**Dynamic analysis:** For launch loads and on-orbit maneuvers
**Reduction enables:** Coupled control-structure simulation

### Benchmark Problems

**NASA Almond:**
- Standard test problem for CMS methods
- Comparisons with exact solution
- Used to validate implementation accuracy

## Error Analysis

### Modal Truncation Error

**Frequency error:** For natural frequencies, error approximately:
$$
\frac{\omega_i^{\text{red}} - \omega_i^{\text{exact}}}{\omega_i^{\text{exact}}} \approx \sum_{k \notin \text{kept}} \frac{c_{ik}^2}{\omega_i^2 - \omega_k^2}
$$
where $c_{ik}$ are coupling coefficients.

**Mode shape error:** Measured by MAC (Modal Assurance Criterion):
$$
\text{MAC}(\phi_i, \phi_i^{\text{red}}) = \frac{|\phi_i^T \phi_i^{\text{red}}|^2}{(\phi_i^T \phi_i)(\phi_i^{\text{red}T} \phi_i^{\text{red}})}
$$

### Static Error Measures

**For static loads at boundaries:** Error zero by construction.

**For internal loads:** Error depends on number of kept modes and load distribution.

**Recovery error:** For stresses and strains, may need mode acceleration correction.

### Convergence Monitoring

**Energy-based error indicators:**
- Modal strain energy fraction
- [[Kinetic Energy]] distribution
- Load participation factors

**Frequency-based criteria:**
- Change in eigenvalues with added mode[[Frequency Response Function (FRF)]]s
- Frequency resp]]onse error at target frequencies

## Relationship to Other Concepts

### Comparison with Guyan Reduction

**Guyan (static) reduction:** 
- Uses only constraint modes: $x_i = -K_{ii}^{-1} K_{ib} x_b$
- Accurate only for static or very low-frequency problems
- Over-stiffens dynamic response

**Craig-Bampton:** 
- Adds fixed-interface dynamic modes
- Accurate for dynamic problems up to retained mode frequencies
- More [[degrees of freedom]] but much more accurate

### Connection to Component Mode Synthesis

**Craig-Bampton as CMS variant:** One specific implementation of CMS

**Other CMS methods:**
- **MacNeal-Rubin:** Free-interface CMS
- **Benfield-Hruda:** Loaded-interface CMS
- **Hintz:** Hybrid-interface CMS

**Unified framework:** All project onto subspace of mode shapes and constraint modes.

### Relationship to Superelements

**Superelement concept:** General approach for substructuring

**Craig-Bampton as superelement generation method:** One way to create reduced superelements

**Alternative superelement methods:** 
- Static condensation
- Dynamic condensation
- SEREP (System Equivalent Reduction Expansion Process)

### Integration with Model Order Reduction

**Proper Orthogonal Decomposition (POD):** Data-driven reduction alternative

**Balanced Truncation:** For control applications

**Krylov subspace methods:** Moment-matching approaches

**Craig-Bampton advantages:** Physically interpretable, preserves interfaces, exact static behavior.

## Historical Context and Evolution

### Original Development

**Craig and Bampton's 1968 paper:** 
- Motivation: Analysis of large spacecraft structures (Saturn V, Apollo)
- Need: Handle models too large for available computers
- Innovation: Combine static (constraint) and dynamic (fixed-interface) modes

**Early applications:** 
- NASA space program
- Aerospace industry
- Nuclear power plant structures

### Evolution in Practice

**1970s-1980s:** 
- Implementation in NASTRAN and other commercial codes
- Application to automotive and aerospace industries
- Development of automated substructuring tools

**1990s-2000s:** 
- Parallel processing implementations
- Integration with optimization workflows
- Extension to nonlinear problems

**2010s-present:** 
- Real-time simulation applications
- Digital twin technology
- Uncertainty quantification
- Machine learning enhanced reduction

### Current Research Directions

- **Nonlinear Craig-Bampton:** For geometric and material nonlinearities
- **Adaptive reduction:** Automatic mode selection based on error estimates
- **Multi-physics coupling:** Thermal, acoustic, fluid-structure interaction
- **High-performance computing:** GPU acceleration, distributed memory algorithms

## Pedagogical Approach

### Teaching Strategies

1. **Physical analogy:** Spring-mass systems to illustrate substructuring
2. **Step-by-step derivation:** From full equations to reduced system
3. **Hands-on examples:** Simple beam or frame structures
4. **Software exercises:** Implement in MATLAB, then use commercial FE software
5. **Error analysis:** Compare reduced vs. full model results

### Common Misconceptions

1. **"More modes always better":** Diminishing returns, optimal number exists
2. **"Craig-Bampton works for any frequency":** Accurate only up to ~1.5× highest kept mode
3. **"Any partitioning works":** Poor partitioning can degrade accuracy
4. **"Reduced model is always faster":** Overhead can outweigh benefits for small models
5. **"Interface DOFs don't matter":** Many interface DOFs limit reduction

### Learning Resources

**Foundational Texts:**
- Craig, R. R., & Kurdila, A. J., "Fundamentals of Structural Dynamics"
- Geradin, M., & Rixen, D., "Mechanical Vibrations: Theory and Application to Structural Dynamics"
- Bathe, K. J., "Finite Element Procedures"
- NASTRAN Theoretical Manual

**Online Resources:**
- NASA Technical Reports on CMS
- MIT OpenCourseWare: [[Finite Element Analysis (FEA)]]
- Wolfram Demonstrations: Component Mode Synthesis
- YouTube: Craig-Bampton method tutorials

**Software Tutorials:**
- NASTRAN: CMSUP and superelement tutorials
- ANSYS: Component Mode Synthesis workshops
- MATLAB: Implementation examples
- Siemens NX/Nastran: Superelement analysis guide

## Implementation in Software

### Python Implementation

```python
import numpy as np
from scipy.linalg import eigh
from scipy.sparse import csc_matrix, block_diag
import scipy.sparse.linalg as spla

class CraigBamptonSubstructure:
    """Class for Craig-Bampton reduction of a substructure"""
    
    def __init__(self, M, K, boundary_dofs, n_modes=None):
        """
        Initialize substructure for Craig-Bampton reduction
        
        Parameters
        ----------
        M : ndarray or sparse matrix
            Mass matrix (n x n)
        K : ndarray or sparse matrix
            Stiffness matrix (n x n)
        boundary_dofs : list or array
            Indices of boundary DOFs
        n_modes : int, optional
            Number of fixed-interface modes to keep
            If None, determine based on frequency cutoff
        """
        self.M = M
        self.K = K
        self.boundary_dofs = np.asarray(boundary_dofs)
        self.n = M.shape[0]
        
        # Internal DOFs
        all_dofs = np.arange(self.n)
        self.internal_dofs = np.setdiff1d(all_dofs, self.boundary_dofs)
        
        self.n_b = len(self.boundary_dofs)
        self.n_i = len(self.internal_dofs)
        
        # Partition matrices
        self._partition_matrices()
        
        # Determine number of modes if not specified
        if n_modes is None:
            # Default: keep modes up to 2x highest frequency of interest
            # or maximum possible
            n_modes = min(50, self.n_i)
        self.n_modes = n_modes
        
        # Perform reduction
        self._reduce()
    
    def _partition_matrices(self):
        """Partition mass and stiffness matrices"""
        i = self.internal_dofs
        b = self.boundary_dofs
        
        self.M_ii = self.M[np.ix_(i, i)]
        self.M_ib = self.M[np.ix_(i, b)]
        self.M_bi = self.M[np.ix_(b, i)]
        self.M_bb = self.M[np.ix_(b, b)]
        
        self.K_ii = self.K[np.ix_(i, i)]
        self.K_ib = self.K[np.ix_(i, b)]
        self.K_bi = self.K[np.ix_(b, i)]
        self.K_bb = self.K[np.ix_(b, b)]
    
    def _reduce(self):
        """Perform Craig-Bampton reduction"""
        # 1. Compute fixed-interface normal modes
        self._compute_fixed_interface_modes()
        
        # 2. Compute constraint modes
        self._compute_constraint_modes()
        
        # 3. Build transformation matrix
        self._build_transformation_matrix()
        
        # 4. Compute reduced matrices
        self._compute_reduced_matrices()
    
    def _compute_fixed_interface_modes(self):
        """Compute fixed-interface normal modes"""
        # Solve eigenvalue problem: K_ii * Phi = M_ii * Phi * Lambda
        if self.n_modes >= self.n_i:
            # If keeping all modes, use dense eigensolver
            eigvals, eigvecs = eigh(self.K_ii.toarray() if hasattr(self.K_ii, 'toarray') 
                                   else self.K_ii,
                                   self.M_ii.toarray() if hasattr(self.M_ii, 'toarray') 
                                   else self.M_ii)
            # Sort by ascending eigenvalue
            idx = np.argsort(eigvals)
            self.omega = np.sqrt(eigvals[idx[:self.n_modes]])
            self.Phi_i = eigvecs[:, idx[:self.n_modes]]
        else:
            # Use sparse eigensolver for partial solution
            # Note: 'SM' finds smallest eigenvalues
            eigvals, eigvecs = spla.eigsh(self.K_ii, k=self.n_modes, M=self.M_ii,
                                         which='SM')
            self.omega = np.sqrt(eigvals)
            self.Phi_i = eigvecs
        
        # Mass-normalize mode shapes
        for k in range(self.n_modes):
            m_k = self.Phi_i[:, k].T @ self.M_ii @ self.Phi_i[:, k]
            self.Phi_i[:, k] = self.Phi_i[:, k] / np.sqrt(m_k)
        
        # Verify orthogonality
        PhiTMPhi = self.Phi_i.T @ self.M_ii @ self.Phi_i
        PhiTKPhi = self.Phi_i.T @ self.K_ii @ self.Phi_i
        
        self.Lambda = np.diag(self.omega**2)
    
    def _compute_constraint_modes(self):
        """Compute constraint modes: Psi = -K_ii^{-1} * K_ib"""
        # Solve K_ii * Psi = -K_ib
        if hasattr(self.K_ii, 'toarray'):
            # Sparse matrix
            self.Psi_i = -spla.spsolve(self.K_ii, self.K_ib)
        else:
            # Dense matrix
            self.Psi_i = -np.linalg.solve(self.K_ii, self.K_ib)
    
    def _build_transformation_matrix(self):
        """Build Craig-Bampton transformation matrix"""
        n_total = self.n
        n_red = self.n_modes + self.n_b
        
        # Initialize transformation matrix
        self.T = np.zeros((n_total, n_red))
        
        # Fill transformation matrix
        # Modal coordinates part
        self.T[np.ix_(self.internal_dofs, np.arange(self.n_modes))] = self.Phi_i
        
        # Constraint modes part
        self.T[np.ix_(self.internal_dofs, 
                      np.arange(self.n_modes, self.n_modes + self.n_b))] = self.Psi_i
        
        # Boundary DOFs (identity)
        self.T[np.ix_(self.boundary_dofs,
                      np.arange(self.n_modes, self.n_modes + self.n_b))] = np.eye(self.n_b)
    
    def _compute_reduced_matrices(self):
        """Compute reduced mass and stiffness matrices"""
        # Reduced mass matrix
        self.M_red = self.T.T @ self.M @ self.T
        
        # Reduced stiffness matrix
        self.K_red = self.T.T @ self.K @ self.T
        
        # Should have block structure:
        # M_red = [I, M_kb; M_bk, M_bb_red]
        # K_red = [Lambda, 0; 0, K_bb_red]
        
        # Extract blocks for verification
        self.M_kk = self.M_red[:self.n_modes, :self.n_modes]
        self.M_kb = self.M_red[:self.n_modes, self.n_modes:]
        self.M_bb_red = self.M_red[self.n_modes:, self.n_modes:]
        
        self.K_kk = self.K_red[:self.n_modes, :self.n_modes]
        self.K_kb = self.K_red[:self.n_modes, self.n_modes:]
        self.K_bb_red = self.K_red[self.n_modes:, self.n_modes:]
    
    def get_reduction_statistics(self):
        """Get statistics about the reduction"""
        stats = {
            'original_dofs': self.n,
            'reduced_dofs': self.n_modes + self.n_b,
            'reduction_ratio': self.n / (self.n_modes + self.n_b),
            'n_modes': self.n_modes,
            'n_boundary': self.n_b,
            'n_internal': self.n_i,
            'max_frequency': self.omega[-1] if len(self.omega) > 0 else 0,
            'min_frequency': self.omega[0] if len(self.omega) > 0 else 0
        }
        return stats
    
    def recover_full_response(self, q_red):
        """
        Recover full response from reduced coordinates
        
        Parameters
        ----------
        q_red : ndarray
            Reduced coordinates [p_k; x_b]
        
        Returns
        -------
        x_full : ndarray
            Full displacement vector
        """
        return self.T @ q_red
    
    def get_interface_forces(self, q_red, q_dot_red=None, q_ddot_red=None):
        """
        Compute interface forces from reduced coordinates
        
        Parameters
        ----------
        q_red : ndarray
            Reduced coordinates
        q_dot_red : ndarray, optional
            Reduced velocities
        q_ddot_red : ndarray, optional
            Reduced accelerations
        
        Returns
        -------
        f_interface : ndarray
            Interface forces
        """
        # Interface forces = K_bi * x_i + K_bb * x_b + inertia terms
        # In reduced coordinates, can compute from reduced matrices
        if q_ddot_red is not None:
            # Dynamic case: f = M * a + K * x
            f_red = self.M_red @ q_ddot_red + self.K_red @ q_red
        else:
            # Static case: f = K * x
            f_red = self.K_red @ q_red
        
        # Interface forces are last n_b entries of f_red
        return f_red[self.n_modes:]

class CraigBamptonAssembly:
    """Class for assembling multiple Craig-Bampton substructures"""
    
    def __init__(self, substructures, connections=None):
        """
        Initialize assembly of substructures
        
        Parameters
        ----------
        substructures : list
            List of CraigBamptonSubstructure objects
        connections : list, optional
            List of connection definitions
            Each connection: [(sub_idx1, dof_idx1), (sub_idx2, dof_idx2)]
        """
        self.substructures = substructures
        self.connections = connections if connections is not None else []
        self.n_sub = len(substructures)
        
        # Assemble system
        self._assemble()
    
    def _assemble(self):
        """Assemble reduced substructures"""
        # Build block diagonal matrices
        M_blocks = []
        K_blocks = []
        T_blocks = []
        
        for sub in self.substructures:
            M_blocks.append(sub.M_red)
            K_blocks.append(sub.K_red)
            T_blocks.append(sub.T)
        
        # Block diagonal matrices (unassembled)
        self.M_block = block_diag(M_blocks)
        self.K_block = block_diag(K_blocks)
        self.T_block = block_diag(T_blocks)
        
        # Count DOFs
        self.n_dof_unassembled = sum(sub.M_red.shape[0] for sub in self.substructures)
        
        # Apply interface constraints if connections exist
        if self.connections:
            self._apply_interface_constraints()
        else:
            self.M_assembled = self.M_block
            self.K_assembled = self.K_block
            self.T_assembled = self.T_block
            self.n_dof_assembled = self.n_dof_unassembled
    
    def _apply_interface_constraints(self):
        """Apply interface constraints using master-slave elimination"""
        # Build mapping from substructure DOFs to global DOFs
        sub_dof_offsets = [0]
        for sub in self.substructures:
            sub_dof_offsets.append(sub_dof_offsets[-1] + sub.M_red.shape[0])
        
        # Identify master and slave DOFs
        # For simplicity, we'll use Lagrange multipliers
        # In practice, would use more efficient methods
        
        # For now, just keep unassembled
        self.M_assembled = self.M_block
        self.K_assembled = self.K_block
        self.T_assembled = self.T_block
        self.n_dof_assembled = self.n_dof_unassembled
        
        # Flag that constraints not yet applied
        self.constraints_applied = False
    
    def apply_lagrange_multipliers(self):
        """Apply constraints using [[Lagrange multiplier]] method"""
        # Build constraint matrix C such that C * q = 0
        n_constraints = len(self.connections)
        
        if n_constraints == 0:
            return self.M_block, self.K_block
        
        # Initialize constraint matrix
        C = np.zeros((n_constraints, self.n_dof_unassembled))
        
        # Build constraint equations
        for i, conn in enumerate(self.connections):
            (s1, d1), (s2, d2) = conn
            
            # Map to global DOF indices
            # Need to account for modal vs boundary DOFs in each substructure
            # This is simplified - in practice need careful mapping
            
            # For demonstration: assume d1, d2 are indices in reduced system
            offset1 = sum(sub.M_red.shape[0] for sub in self.substructures[:s1])
            offset2 = sum(sub.M_red.shape[0] for sub in self.substructures[:s2])
            
            global_dof1 = offset1 + d1
            global_dof2 = offset2 + d2
            
            # Constraint: q1 - q2 = 0
            C[i, global_dof1] = 1
            C[i, global_dof2] = -1
        
        # Form augmented system with Lagrange multipliers
        n = self.n_dof_unassembled
        m = n_constraints
        
        M_aug = np.zeros((n + m, n + m))
        K_aug = np.zeros((n + m, n + m))
        
        M_aug[:n, :n] = self.M_block
        K_aug[:n, :n] = self.K_block
        K_aug[:n, n:] = C.T
        K_aug[n:, :n] = C
        
        self.M_assembled = M_aug
        self.K_assembled = K_aug
        self.constraints_applied = True
        self.n_dof_assembled = n + m
        
        return M_aug, K_aug
    
    def solve_eigenproblem(self, n_modes=10):
        """Solve eigenvalue problem for assembled system"""
        if self.constraints_applied:
            # For augmented system, need to handle constraints
            # Would use appropriate method for constrained system
            pass
        else:
            # Standard eigenvalue problem
            if n_modes >= self.n_dof_assembled:
                eigvals, eigvecs = eigh(self.K_assembled, self.M_assembled)
            else:
                eigvals, eigvecs = spla.eigsh(self.K_assembled, k=n_modes,
                                             M=self.M_assembled, which='SM')
        
        omega = np.sqrt(eigvals)
        return omega, eigvecs
    
    def recover_full_displacements(self, q_assembled):
        """Recover full displacements from assembled reduced coordinates"""
        if self.constraints_applied:
            # q_assembled includes Lagrange multipliers
            # Extract only displacement part
            n_disp = self.n_dof_unassembled
            q_disp = q_assembled[:n_disp]
        else:
            q_disp = q_assembled
        
        # Map to full displacements
        x_full = self.T_assembled @ q_disp
        
        return x_full

# Example usage
if __name__ == "__main__":
    # Create a simple example: Two beams connected end-to-end
    from scipy.sparse import diags
    
    def create_beam_matrices(n_elements, L=1.0, EI=1.0, rhoA=1.0):
        """Create mass and stiffness matrices for a Euler-Bernoulli beam"""
        n_nodes = n_elements + 1
        n_dof = 2 * n_nodes  # y-displacement and rotation per node
        
        # Element matrices (simplified)
        # Using consistent mass and stiffness matrices for Euler-Bernoulli beam
        le = L / n_elements
        
        # Element stiffness matrix
        k_elem = (EI / le**3) * np.array([
            [12, 6*le, -12, 6*le],
            [6*le, 4*le**2, -6*le, 2*le**2],
            [-12, -6*le, 12, -6*le],
            [6*le, 2*le**2, -6*le, 4*le**2]
        ])
        
        # Element mass matrix
        m_elem = (rhoA * le / 420) * np.array([
            [156, 22*le, 54, -13*le],
            [22*le, 4*le**2, 13*le, -3*le**2],
            [54, 13*le, 156, -22*le],
            [-13*le, -3*le**2, -22*le, 4*le**2]
        ])
        
        # Assemble global matrices
        K = np.zeros((n_dof, n_dof))
        M = np.zeros((n_dof, n_dof))
        
        for e in range(n_elements):
            dofs = np.array([2*e, 2*e+1, 2*e+2, 2*e+3])
            K[np.ix_(dofs, dofs)] += k_elem
            M[np.ix_(dofs, dofs)] += m_elem
        
        return M, K
    
    # Create two beams
    n_elem1 = 50
    n_elem2 = 50
    
    M1, K1 = create_beam_matrices(n_elem1, L=2.0)
    M2, K2 = create_beam_matrices(n_elem2, L=2.0)
    
    # Define boundary DOFs
    # For beam 1: right end is boundary (last 2 DOFs: displacement and rotation)
    bdof1 = [2*n_elem1, 2*n_elem1 + 1]
    
    # For beam 2: left end is boundary (first 2 DOFs)
    bdof2 = [0, 1]
    
    # Create Craig-Bampton substructures
    n_modes = 10  # Keep 10 fixed-interface modes per substructure
    
    substruct1 = CraigBamptonSubstructure(M1, K1, bdof1, n_modes)
    substruct2 = CraigBamptonSubstructure(M2, K2, bdof2, n_modes)
    
    # Print reduction statistics
    stats1 = substruct1.get_reduction_statistics()
    stats2 = substruct2.get_reduction_statistics()
    
    print("Substructure 1 reduction:")
    print(f"  Original DOFs: {stats1['original_dofs']}")
    print(f"  Reduced DOFs: {stats1['reduced_dofs']}")
    print(f"  Reduction ratio: {stats1['reduction_ratio']:.1f}x")
    print(f"  Modes kept: {stats1['n_modes']}")
    print(f"  Frequency range: {stats1['min_frequency']:.2f} - {stats1['max_frequency']:.2f} rad/s")
    
    print("\nSubstructure 2 reduction:")
    print(f"  Original DOFs: {stats2['original_dofs']}")
    print(f"  Reduced DOFs: {stats2['reduced_dofs']}")
    print(f"  Reduction ratio: {stats2['reduction_ratio']:.1f}x")
    print(f"  Modes kept: {stats2['n_modes']}")
    print(f"  Frequency range: {stats2['min_frequency']:.2f} - {stats2['max_frequency']:.2f} rad/s")
    
    # Assemble substructures
    # Connection: beam1 right end to beam2 left end
    connections = [[(0, len(bdof1)-1), (1, 0)]]  # Connect last DOF of beam1 to first DOF of beam2
    
    assembly = CraigBamptonAssembly([substruct1, substruct2], connections)
    
    # Apply Lagrange multipliers for constraints
    M_aug, K_aug = assembly.apply_lagrange_multipliers()
    
    print(f"\nAssembly:")
    print(f"  Unassembled DOFs: {assembly.n_dof_unassembled}")
    print(f"  Assembled DOFs: {assembly.n_dof_assembled}")
    
    # Solve eigenvalue problem (for unconstrained part)
    # Use block diagonal without constraints for simplicity
    omega, modes = assembly.solve_eigenproblem(n_modes=5)
    
    print(f"\nFirst 5 natural frequencies (Hz):")
    for i, w in enumerate(omega[:5]):
        print(f"  Mode {i+1}: {w/(2*np.pi):.3f}")
```

### Commercial Software Implementation

**NASTRAN:**
```nas
$ Craig-Bampton reduction in NASTRAN
$ Define superelement 10
SUPER 10
$ Grid points for substructure
GRID,1,,0.,0.,0.
GRID,2,,1.,0.,0.
...
$ Elements
CBEAM,1,100,1,2,...
...
$ Define boundary points (ASET/BSET)
ASET1,123456,100  $ Fix all DOFs at grid 100 (boundary)
$ OR use BSET for explicit boundary DOFs
BSET1,123,10,20,30  $ DOFs 1,2,3 at grids 10,20,30 are boundary

$ CMS reduction
CMSMETHOD,10,CMS
NMODES,10         $ Number of fixed-interface modes
K2PP,1.0E-6       $ Stiffness matrix coupling tolerance
$ Or use automatic mode selection:
FREQ1,100         $ Frequency cutoff (Hz)

$ Output reduced matrices
SUPORT1,10,123456 $ Support for superelement
$ Or write reduced matrices to file
MPC,100           $ Multipoint constraints for assembly

$ In main bulk data, include superelement:
include 'superelement10.op2'
$ Connect superelements
MPC,...
```

**ANSYS:**
```ansys
! Craig-Bampton in ANSYS
! Create component for substructure
/prep7
! Define geometry, mesh, materials...
! ...

! Select boundary nodes
nsel,s,loc,x,0    ! Select nodes at x=0 as boundary
cm,boundary,node  ! Create component "boundary"

! Perform CMS reduction
/solu
antype,substr     ! Substructuring analysis
seopt,matname,1   ! Create superelement matrices
nsel,all
cmsel,s,boundary  ! Select boundary component
m,all,ux,uy,uz    ! Master DOFs at boundary (all translations)
! Or use automated selection
mopt,auto,10      ! Automated mode selection, 10 modes
solve

! Write superelement matrices
selist,matname,sub  ! Write to file

! In assembly model
/prep7
! Read superelement
seread,matname,sub,,,1
! Connect to other elements/superelements
! ...
```

**ABAQUS:**
```inp
*SUBSTRUCTURE, NAME=BEAM1
*BOUNDARY, SUBSTRUCTURE NODE
100,1,6  ! Fix all DOFs at node 100 for fixed-interface modes
*STEP
*SUBSTRUCTURE GENERATE, TYPE=COMPONENT MODE SYNTHESIS
*RETAINED MODAL DOFS, NUMBER=10  ! Keep 10 fixed-interface modes
*RETAINED NODAL DOFS
10,1,3   ! Retain DOFs 1-3 at node 10 (interface)
20,1,3   ! Retain DOFs 1-3 at node 20 (interface)
*END STEP

*SUBSTRUCTURE MATRIX OUTPUT, STIFFNESS=MASS=YES
*SUBSTRUCTURE MATRIX OUTPUT, FILE=BEAM1

*ASSEMBLY, NAME=ASSEMBLY1
*INSTANCE, NAME=BEAM1_I, SUBSTRUCTURE=BEAM1
*END INSTANCE
*INSTANCE, NAME=BEAM2_I, SUBSTRUCTURE=BEAM2
*END INSTANCE

*TIE, NAME=CONNECTION
BEAM1_I.10, BEAM2_I.20

*END ASSEMBLY
```

## See Also

- Component Mode Synthesis]]
- [[Dynamic Substructuring]]
- [[Model Order Reduction]]
- Superelement]]
- [[Fixed-Interface Modes]]
- [[Constraint Modes]]
- Guyan Reduction]]
- [[Modal Analysis]]
- [[Finite Element Analysis (FEA)]]
- [[Structural Dynamics]]
- Interface Compatibility]]
- Modal Truncation]]
- Residual Flexibility]]
- [[Degrees of Freedom]]

---

*Note: The Craig-Bampton Method remains a cornerstone of [[Dynamic Substructuring]] and model reduction in [[Structural Dynamics]]. Its combination of fixed-interface normal modes for internal dynamics and constraint modes for interface compatibility provides an effective balance between model reduction and accuracy, making it indispensable for large-scale finite element analyses in aerospace, automotive, and civil engineering applications.*
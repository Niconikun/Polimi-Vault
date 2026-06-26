## Formal Definition

The **Central Difference Method** (also known as the **explicit central difference scheme**) is an explicit time integration algorithm for solving second-order [[Ordinary Differential Equations (ODEs)]], particularly those arising in [[Structural Dynamics]]. As a conditionally stable explicit method, it uses finite difference approximations for [[velocity]] and acceleration centered at the current time step, requiring only information from previous time steps to compute the next solution. This method is especially efficient for wave propagation problems and high-frequency dynamic analyses where small time steps are necessary for accuracy.

## Historical Development

### Key Milestones
- **1927:** Lewis Fry Richardson proposes finite difference methods for solving [[differential equations]]
- **1940s:** Development of explicit difference schemes for solving hyperbolic equations
- **1950s:** Application to structural dynamics problems in engineering
- **1960s:** Implementation in finite difference codes for wave propagation
- **1970s:** Integration into explicit finite element software (DYNA, PRONTO)
- **1980s:** Development of stability criteria and implementation in commercial codes (LS-DYNA, ABAQUS Explicit)
- **1990s:** Parallel implementations for impact and crash simulation
- **2000s:** Extension to multiphysics and coupled problems
- **2010s:** GPU acceleration for real-time simulation
- **2020s:** Integration with machine learning for adaptive time stepping

### Foundational Contributors
1. **Lewis Fry Richardson (1881-1953):** Pioneered finite difference methods
2. **John von Neumann (1903-1957):** Developed stability analysis for finite difference schemes
3. **Thomas J. R. Hughes (b. 1943):** Advanced computational dynamics methods
4. **John O. Hallquist (b. 1944):** Developed LS-DYNA with central difference integration
5. **Klaus-Jürgen Bathe (b. 1943):** Contributions to computational structural dynamics

## Mathematical Formulation

### Basic Formulation

**Equation of motion:**
$$
M\ddot{u}(t) + C\dot{u}(t) + Ku(t) = F(t)
$$

**Central difference approximations:**
- **Velocity:**
  $$
  \dot{u}_n = \frac{u_{n+1} - u_{n-1}}{2Δt}
  $$
- **Acceleration:**
  $$
  \ddot{u}_n = \frac{u_{n+1} - 2u_n + u_{n-1}}{Δt^2}
  $$

**Time-stepping algorithm:**
1. **Compute acceleration at time n:**
   $$
   \ddot{u}_n = M^{-1}[F_n - C\dot{u}_n - Ku_n]
   $$
2. **Update displacement at time n+1:**
   $$
   u_{n+1} = 2u_n - u_{n-1} + \ddot{u}_n Δt^2
   $$
3. **Update velocity at time n:**
   $$
   \dot{u}_n = \frac{u_{n+1} - u_{n-1}}{2Δt}
   $$

### Matrix Formulation

**For linear systems with diagonal mass matrix:** The method becomes explicitly solvable without matrix inversion:

**For each degree of freedom i:**
$$
u_i^{n+1} = \frac{Δt^2}{m_i} \left(F_i^n - \sum_{j} c_{ij} \dot{u}_j^n - \sum_{j} k_{ij} u_j^n\right) + 2u_i^n - u_i^{n-1}
$$

**With diagonal damping:** If C is diagonal or proportional to M:
$$
u_i^{n+1} = \frac{Δt^2}{m_i + \frac{Δt}{2}c_{ii}} \left(F_i^n - \sum_{j≠i} c_{ij} \dot{u}_j^n - \sum_{j} k_{ij} u_j^n\right) + \frac{2m_i - Δt^2 k_{ii}}{m_i + \frac{Δt}{2}c_{ii}} u_i^n - \frac{m_i - \frac{Δt}{2}c_{ii}}{m_i + \frac{Δt}{2}c_{ii}} u_i^{n-1}
$$

### Alternative Form: Velocity-Verlet

**Equivalent to central difference:** The Velocity-Verlet algorithm:
1. **Update velocity at half-step:**
   $$
   \dot{u}_{n+1/2} = \dot{u}_n + \frac{Δt}{2} \ddot{u}_n
   $$
2. **Update displacement:**
   $$
   u_{n+1} = u_n + Δt \dot{u}_{n+1/2}
   $$
3. **Compute acceleration at n+1:**
   $$
   \ddot{u}_{n+1} = M^{-1}[F_{n+1} - C\dot{u}_{n+1/2} - Ku_{n+1}]
   $$
4. **Complete velocity update:**
   $$
   \dot{u}_{n+1} = \dot{u}_{n+1/2} + \frac{Δt}{2} \ddot{u}_{n+1}
   $$

## Fundamental Principles

### Explicit Time Integration

**No equation solving required:** For diagonal mass matrix, each degree of freedom can be updated independently:
- No global stiffness matrix factorization
- No iterations required (for linear problems)
- Simple vector operations dominate computation

**Conditional stability:** Time step must satisfy:
$$
Δt ≤ Δt_{\text{crit}} = \frac{2}{ω_{\text{max}}} = \frac{T_{\text{min}}}{π}
$$
where \( ω_{\text{max}} \) is the highest [[Natural Frequency]] and \( T_{\text{min}} \) is the smallest period.

### Finite Difference Accuracy

**Truncation error:** Central difference approximations are second-order accurate:
- Displacement error: \( O(Δt^2) \)
- Velocity error: \( O(Δt^2) \)
- Acceleration error: \( O(Δt^2) \)

**Dispersion relation:** For wave equation \( u_{tt} = c^2 u_{xx} \):
- Numerical wave speed: \( \tilde{c} = c \frac{\sin(kcΔt/2)}{kcΔt/2} \)
- Numerical dispersion causes different frequencies to travel at different speeds

### Energy Conservation Properties

**For undamped, unforced systems:** Central difference method:
- Does not conserve energy exactly (symplectic Euler does)
- Energy oscillates but remains bounded for stable time steps
- Average energy conserved over time

**Numerical dissipation:** Minimal when stability condition is satisfied

## Theoretical Framework

### Stability Analysis

**Von Neumann stability analysis:** For model equation \( \ddot{u} + ω^2 u = 0 \):

**[[Characteristic equation]]:** 
$$
λ^2 - (2 - ω^2 Δt^2)λ + 1 = 0
$$

**Stability condition:** Roots satisfy \( |λ| ≤ 1 \) if:
$$
ω^2 Δt^2 ≤ 4 \quad \text{or} \quad Δt ≤ \frac{2}{ω}
$$

**For general systems:** Critical time step given by:
$$
Δt_{\text{crit}} = \frac{2}{ω_{\text{max}}} = \min_e \frac{l_e}{c_e}
$$
where \( l_e \) is element characteristic length and \( c_e = \sqrt{E/ρ} \) is wave speed.

### Accuracy Analysis

**Modified equation approach:** Substitute finite differences into differential equation:

**For \( \ddot{u} + ω^2 u = 0 \):** Central difference gives:
$$
\frac{u^{n+1} - 2u^n + u^{n-1}}{Δt^2} + ω^2 u^n = -\frac{ω^4 Δt^2}{12} u^n + O(Δt^4)
$$

**Thus the method solves:** 
$$
\ddot{u} + \left(ω^2 + \frac{ω^4 Δt^2}{12}\right) u = 0
$$

**Period elongation:** Numerical period \( \tilde{T} \) related to exact period \( T \):
$$
\frac{\tilde{T} - T}{T} ≈ \frac{π^2}{12} \left(\frac{Δt}{T}\right)^2
$$

### Convergence Analysis

**Lax equivalence theorem:** [[Consistency]] + Stability ⇒ Convergence

**[[Consistency]]:** Local truncation error → 0 as \( Δt → 0 \)

**Convergence rate:** Second-order for linear problems:
$$
\|u(t_n) - u^n\| ≤ C Δt^2
$$

**For nonlinear problems:** Typically first-order due to stability restrictions

## Classification and Variants

### By Problem Type
1. **Linear central difference:** For linear structural dynamics
2. **Nonlinear central difference:** For problems with geometric/material nonlinearities
3. **Explicit dynamics:** For wave propagation and impact problems
4. **[[Molecular dynamics]]:** Velocity-Verlet as variant

### By Implementation Approach
1. **Standard central difference:** As described above
2. **Velocity-Verlet:** Two-step formulation
3. **Leapfrog method:** Similar to central difference
4. **Störmer-Verlet:** Symplectic variant

### By Element Technology
1. **Lumped mass central difference:** Requires diagonal mass matrix
2. **Consistent mass central difference:** Requires mass matrix inversion (less common)
3. **Reduced integration mass:** Compromise between accuracy and efficiency

### Specialized Variants
1. **Explicit Newmark:** Central difference is Newmark with β=0, γ=1/2
2. **Explicit Runge-Kutta-Nyström:** Higher-order explicit methods
3. **Symplectic integrators:** For long-term energy conservation
4. **Adaptive central difference:** Variable time step based on stability

## Derivation and Proof

### Derivation from [[Taylor Series Expansion]]

**Taylor expansions:**
$$
u(t+Δt) = u(t) + \dot{u}(t)Δt + \frac{1}{2}\ddot{u}(t)Δt^2 + \frac{1}{6}\dddot{u}(t)Δt^3 + O(Δt^4)
$$
$$
u(t-Δt) = u(t) - \dot{u}(t)Δt + \frac{1}{2}\ddot{u}(t)Δt^2 - \frac{1}{6}\dddot{u}(t)Δt^3 + O(Δt^4)
$$

**Subtract to get velocity:**
$$
u(t+Δt) - u(t-Δt) = 2\dot{u}(t)Δt + O(Δt^3)
$$
Thus:
$$
\dot{u}(t) = \frac{u(t+Δt) - u(t-Δt)}{2Δt} + O(Δt^2)
$$

**Add to get acceleration:**
$$
u(t+Δt) + u(t-Δt) = 2u(t) + \ddot{u}(t)Δt^2 + O(Δt^4)
$$
Thus:
$$
\ddot{u}(t) = \frac{u(t+Δt) - 2u(t) + u(t-Δt)}{Δt^2} + O(Δt^2)
$$

### Stability Proof

**For model equation \( \ddot{u} + ω^2 u = 0 \):** Substitute central difference:
$$
\frac{u^{n+1} - 2u^n + u^{n-1}}{Δt^2} + ω^2 u^n = 0
$$

**Rearrange:** 
$$
u^{n+1} = (2 - ω^2 Δt^2)u^n - u^{n-1}
$$

**Matrix form:** 
$$
\begin{bmatrix} u^{n+1} \\ u^n \end{bmatrix} = A \begin{bmatrix} u^n \\ u^{n-1} \end{bmatrix}, \quad A = \begin{bmatrix} 2 - ω^2 Δt^2 & -1 \\ 1 & 0 \end{bmatrix}
$$

**[[Characteristic equation]]:** \( λ^2 - (2 - ω^2 Δt^2)λ + 1 = 0 \)

**Roots:** 
$$
λ = \frac{2 - ω^2 Δt^2 ± \sqrt{(2 - ω^2 Δt^2)^2 - 4}}{2}
$$

**Stability condition:** \( |λ| ≤ 1 \) requires \( |2 - ω^2 Δt^2| ≤ 2 \), or \( ω^2 Δt^2 ≤ 4 \)

**Thus:** \( Δt ≤ 2/ω \)

### Convergence Proof

**Local truncation error:** For smooth solution \( u(t) \):
$$
L_n = \frac{u(t_{n+1}) - 2u(t_n) + u(t_{n-1})}{Δt^2} - \ddot{u}(t_n) = \frac{Δt^2}{12} u^{(4)}(t_n) + O(Δt^4)
$$

**Thus method is consistent of order 2.**

**With stability:** Convergence follows from Lax equivalence theorem.

**Error bound:** 
$$
\max_n \|u(t_n) - u^n\| ≤ C Δt^2
$$
for linear problems.

## Physical Interpretation

### Wave Propagation Analogy

**CFL condition:** Courant-Friedrichs-Lewy condition for wave equation:
$$
c\frac{Δt}{Δx} ≤ 1
$$
where \( c \) is wave speed, \( Δx \) is spatial discretization.

**Physical meaning:** Information cannot travel more than one element per time step.

**Numerical wave speed:** Different from physical wave speed, causes dispersion.

### Mechanical Analogy

**Spring-mass system:** For SDOF system:
- Central difference approximates acceleration as finite difference
- Equivalent to explicit Euler for second-order systems
- Like solving using current forces to predict next position

**Digital signal processing view:** Central difference is a high-pass filter for displacement to get acceleration.

### Energy Flow Interpretation

**For undamped systems:** Energy oscillates between kinetic and potential:
- Numerical method introduces phase error
- Energy not conserved exactly but bounded
- Symplectic variants conserve energy better

**Numerical dissipation:** Minimal for central difference, more for other explicit methods.

## Applications

### Engineering Analysis
1. **Wave propagation:** Stress waves in solids, seismic analysis
2. **Impact and crash:** Automotive crashworthiness, bird strike
3. **Ballistics:** Projectile impact, penetration
4. **Manufacturing:** Metal forming, machining simulations
5. **Fluid-structure interaction:** Sloshing, wave impacts

### Problem Types
1. **High-frequency dynamics:** Where many modes are excited
2. **Short-duration events:** Explosions, impacts (microseconds to milliseconds)
3. **Contact problems:** With many changing contact conditions
4. **Material failure:** Fracture, fragmentation, damage evolution
5. **Highly nonlinear problems:** Large deformations, plasticity

### Software Implementation
- **LS-DYNA:** Explicit dynamics with central difference
- **ABAQUS Explicit:** Explicit dynamics solver
- **ANSYS Explicit Dynamics:** Autodyn and LS-DYNA integration
- **RADIOSS:** Explicit finite element solver
- **PRONTO3D:** Sandia's explicit dynamics code

## Implementation Considerations

### Critical Time Step Calculation

**For linear elements:** Critical time step determined by:
$$
Δt_{\text{crit}} = \min_e \frac{l_e}{c_e}
$$
where:
- \( l_e \): Characteristic element length
- \( c_e = \sqrt{\frac{E(1-ν)}{ρ(1+ν)(1-2ν)}} \): Dilatational wave speed for 3D
- \( c_e = \sqrt{\frac{E}{ρ}} \): Bar wave speed for 1D

**For different element types:**
- **Truss/beam:** \( l_e \) = element length
- **Shell:** \( l_e \) = smallest distance between nodes
- **Solid:** \( l_e \) = volume / largest face area

**With damping:** Critical time step reduced:
$$
Δt_{\text{crit}} = \frac{2}{ω_{\text{max}}} \left(\sqrt{1+ζ^2} - ζ\right)
$$
where \( ζ \) is damping ratio of highest mode.

### Mass Matrix Treatment

**Lumped mass matrix:** Essential for efficiency:
- **Row-sum technique:** \( m_{ii} = \sum_j M_{ij} \)
- **HRZ lumping:** Special scaling for [[consistency]]
- **Diagonal scaling:** \( m_{ii} = α M_{ii} \) with scaling factor α

**Advantages of lumped mass:**
- No matrix inversion needed
- Trivial to compute \( M^{-1} \)
- Better for wave propagation (less numerical dispersion)

### Algorithm Implementation

**Basic central difference algorithm:**
```
function central_difference(M, C, K, F, u0, v0, t, beta=0, gamma=0.5):
    n_steps = length(t)
    Δt = t[1] - t[0]
    
    # Initialize arrays
    u = zeros(n_dof, n_steps)
    v = zeros(n_dof, n_steps)
    a = zeros(n_dof, n_steps)
    
    # Initial conditions
    u[:,0] = u0
    v[:,0] = v0
    
    # Initial acceleration
    a[:,0] = M^{-1} * (F[:,0] - C*v[:,0] - K*u[:,0])
    
    # Special starting procedure (since we need u^{-1})
    # Use backward difference for first step or assume u^{-1} = u0 - v0*Δt
    u_minus1 = u0 - v0*Δt + 0.5*a[:,0]*Δt^2
    
    for n = 1 to n_steps-1:
        # Compute displacement at n+1
        u[:,n+1] = (Δt^2 * M^{-1}) * (F[:,n] - C*v[:,n] - K*u[:,n]) + 
                   2*u[:,n] - u[:,n-1]
        
        # Update velocity at n
        v[:,n] = (u[:,n+1] - u[:,n-1]) / (2*Δt)
        
        # Compute acceleration at n (optional)
        a[:,n] = (u[:,n+1] - 2*u[:,n] + u[:,n-1]) / Δt^2
    
    return u, v, a
```

### Starting Procedure

**Initial step problem:** Need \( u^{-1} \) to compute first step.

**Options:**
1. **Backward difference assumption:**
   $$
   u^{-1} = u^0 - \dot{u}^0 Δt + \frac{1}{2} \ddot{u}^0 Δt^2
   $$
   where \( \ddot{u}^0 = M^{-1}(F^0 - C\dot{u}^0 - Ku^0) \)

2. **Forward Euler for first step:**
   $$
   u^1 = u^0 + \dot{u}^0 Δt + \frac{1}{2} \ddot{u}^0 Δt^2
   $$
   then proceed with central difference

3. **Use half-step velocity:** Velocity-Verlet approach

### Contact and Constraints

**Contact algorithms:** Critical for impact problems:
- Penalty method
- Lagrange multipliers
- Distributed parameter method

**Constraint enforcement:** For tied interfaces or boundary conditions

**Hourglass control:** For underintegrated elements to prevent zero-energy modes

## Advantages and Limitations

### Strengths
1. **Computational efficiency:** No matrix factorization, simple vector operations
2. **Natural parallelism:** Each degree of freedom can be updated independently
3. **Robust for nonlinearities:** No convergence issues for material nonlinearities
4. **Excellent for wave propagation:** Minimal numerical dispersion with appropriate time step
5. **Handles contact well:** Naturally suited for changing boundary conditions

### Weaknesses
1. **Conditional stability:** Time step limited by smallest element
2. **Poor for low-frequency dynamics:** Inefficient for problems requiring long simulation times
3. **Mass lumping required:** For efficiency, reduces accuracy for some problems
4. **Energy conservation:** Not exactly energy-conserving
5. **Accuracy limitations:** Second-order accurate but may require very small time steps

### Validity Range
- **Excellent for:** Short-duration, high-frequency, wave propagation problems
- **Good for:** Impact, crash, explosion simulations
- **Poor for:** Quasi-static problems, low-frequency vibrations
- **Not suitable for:** Problems where implicit methods would be more efficient (large time steps possible)

## Advanced Topics

### Variable Time Stepping

**Subcycling:** Different time steps for different regions:
- Stiffer regions use smaller time steps
- Flexible regions use larger time steps
- Requires careful treatment of interfaces

**Adaptive time stepping:** Adjust Δt based on:
- Stability criteria (current critical time step)
- Error estimates
- Solution characteristics

**Multi-time-step methods:** Domain partitioning with different time integrators

### Parallel Implementation

**Domain decomposition:** Partition mesh among processors:
- Each processor updates its own domain
- Communication at boundaries each time step
- Good scaling for large problems

**GPU acceleration:** Massive parallelism for explicit methods:
- Each thread can update one degree of freedom
- Memory bandwidth critical
- CUDA/OpenCL implementations

**Vectorization:** SIMD instructions for modern CPUs

### Coupled Problems

**Thermal-structural coupling:** Sequentially coupled analysis
**Fluid-structure interaction:** Partitioned or monolithic approaches
**Electromagnetic-structural coupling:** For MEMS and other applications

### Stabilization Techniques

**Hourglass control:** For reduced integration elements:
- Stiffness-based hourglass control
- Viscous hourglass control
- Combined approaches

**Artificial viscosity:** For shock wave propagation:
- Linear and quadratic viscosity terms
- Smoothes shocks over few elements
- Based on bulk viscosity

**Stress stabilization:** For incompressible materials

## Special Cases and Examples

### 1D Wave Propagation Example

**Problem:** Elastic bar fixed at one end, impact at other:
- Length L = 1 m, area A = 0.01 m², E = 200 GPa, ρ = 7800 kg/m³
- Wave speed: \( c = \sqrt{E/ρ} = 5064 \) m/s
- Mesh: 100 elements, Δx = 0.01 m
- Critical time step: \( Δt_{\text{crit}} = Δx/c = 1.97 \) μs
- Use Δt = 1.5 μs for stability
- Impact: Velocity initial condition v₀ = 10 m/s

**Result:** Stress wave travels along bar, reflects from fixed end.

### Impact Simulation Example

**Car crash simulation:**
- Model size: 1 million elements
- Smallest element: 2 mm (for details)
- Material: Steel (c ≈ 5000 m/s)
- Critical time step: \( Δt_{\text{crit}} ≈ 0.4 \) μs
- Simulation time: 100 ms
- Time steps needed: 250,000
- Computation: 24 hours on 100 cores

### Seismic Wave Propagation

**Earthquake simulation:**
- Domain: 10 km × 10 km × 5 km
- Element size: 50 m near surface, 200 m at depth
- P-wave speed: 2000-6000 m/s
- S-wave speed: 1000-3500 m/s
- Critical time step: 0.005-0.01 s
- Simulation duration: 60 s
- Time steps: 6000-12000

## Error Analysis

### Truncation Error Analysis

**Local truncation error:** For model equation \( \ddot{u} + ω²u = 0 \):
$$
LTE = \frac{Δt²}{12} u^{(4)}(t_n) + O(Δt⁴)
$$

**Global error:** Accumulated over many steps:
$$
\|u(t_n) - u^n\| ≤ C Δt²
$$
for linear problems.

**Phase error (dispersion):** 
$$
\frac{\tilde{ω} - ω}{ω} ≈ -\frac{ω²Δt²}{24}
$$
where \( \tilde{ω} \) is numerical frequency.

### Stability Error

**Amplitude error:** For undamped system:
- No amplitude decay for central difference
- Amplitude error from phase error accumulation

**For damped system:** Numerical damping from time discretization

### Spatial Discretization Error

**Combined space-time error:** For wave equation discretized with finite elements:
$$
\text{Total error} = O(Δt²) + O(Δx²)
$$
for linear elements and central difference.

**Optimal ratio:** \( Δt/Δx = \) constant for wave propagation problems.

## Relationship to Other Concepts

### Comparison with [[Newmark Method]]

**Central difference:** Explicit, conditionally stable, β=0, γ=1/2
**Newmark implicit:** Unconditionally stable for β≥1/4, γ=1/2
**Relationship:** Central difference is a special case of Newmark family

### Connection to Finite Difference Methods

**Central difference in space and time:** For wave equation \( u_{tt} = c²u_{xx} \):
$$
\frac{u_i^{n+1} - 2u_i^n + u_i^{n-1}}{Δt²} = c² \frac{u_{i+1}^n - 2u_i^n + u_{i-1}^n}{Δx²}
$$

**CFL condition:** \( cΔt/Δx ≤ 1 \) for stability

### Relationship to Leapfrog Method

**Leapfrog for first-order systems:** Similar structure
**Central difference for second-order:** Natural extension
**Both are:** Explicit, second-order accurate, conditionally stable

### Integration with Finite Elements

**Explicit FEM:** Central difference for time, FEM for space
**Lumped mass matrix:** Essential for efficiency
**Element-by-element:** Can avoid global matrix assembly

## Historical Context and Evolution

### Early Development

**1920s-1930s:** Finite difference methods for PDEs
**1940s:** Application to hyperbolic equations (wave equations)
**1950s:** Use in structural dynamics and wave propagation

### Computational Era

**1960s:** Implementation in early computer codes
**1970s:** Development of explicit finite element methods
**1980s:** Commercial explicit codes (LS-DYNA, ABAQUS Explicit)

### Modern Developments

**1990s:** Parallel implementations, contact algorithms
**2000s:** Multiphysics coupling, GPU acceleration
**2010s:** Adaptive methods, uncertainty quantification
**2020s:** Machine learning integration, digital twins

### Current Research Directions

- **[[Machine learning]]:** For adaptive time stepping and parameter selection
- **Exascale computing:** For billion-element simulations
- **Multiscale methods:** Coupling different time scales
- **Uncertainty propagation:** Through explicit dynamics simulations

## Pedagogical Approach

### Teaching Strategies

1. **Physical demonstration:** Wave propagation in springs or slinkies
2. **Simple implementation:** 1D wave equation in MATLAB/Python
3. **Stability demonstration:** Show instability when Δt > Δt_crit
4. **Accuracy comparison:** With analytical solutions
5. **Application examples:** Impact, seismic waves

### Common Misconceptions

1. **"Explicit methods are always faster":** Only for short-duration, high-frequency problems
2. **"Smaller time step always better":** Diminishing returns, increased cost
3. **"Central difference conserves energy":** Only approximately, not exactly
4. **"Any mass matrix works":** Lumped mass required for efficiency
5. **"Stability condition is sufficient for accuracy":** Accuracy may require smaller Δt than stability"

### Learning Resources

**Foundational Texts:**
- Hughes, T. J. R., "The Finite Element Method: Linear Static and Dynamic [[Finite Element Analysis (FEA)]]"
- Bathe, K. J., "Finite Element Procedures"
- Belytschko, T., Liu, W. K., Moran, B., "Nonlinear Finite Elements for Continua and Structures"
- Zienkiewicz, O. C., Taylor, R. L., "The Finite Element Method"

**Online Resources:**
- MIT OpenCourseWare: [[Finite Element Analysis (FEA)]]
- NAFEMS benchmarks for explicit dynamics
- Wolfram Demonstrations: Wave propagation simulations
- YouTube: Explicit dynamics tutorials

**Software Tutorials:**
- LS-DYNA: Example problems for impact simulation
- ABAQUS Explicit: Tutorials for drop test simulation
- ANSYS Explicit Dynamics: Crash simulation tutorials
- OpenSees: Explicit dynamic analysis examples

## Implementation in Software

### MATLAB Implementation

```matlab
function [u, v, a, t] = central_difference_solver(M, C, K, F, t_vec, u0, v0)
% Central difference method for solving M*a + C*v + K*u = F(t)
%
% Inputs:
%   M: Diagonal mass matrix (must be diagonal for efficiency)
%   C, K: Damping and stiffness matrices
%   F: Force matrix F(:,i) for each time or function handle F(t)
%   t_vec: Time vector [t0, t1, ..., t_end]
%   u0, v0: Initial displacement and velocity
%
% Outputs:
%   u, v, a: Displacement, velocity, acceleration time histories
%   t: Time vector

    % Check if M is diagonal
    if ~isdiag(M)
        warning('Mass matrix should be diagonal for efficient explicit integration');
        % Could lump mass here if needed
    end
    
    % Check if F is function handle or matrix
    if isnumeric(F) && size(F,2) == length(t_vec)
        F_is_matrix = true;
    else
        F_is_matrix = false;
    end
    
    n_dof = length(u0);
    n_steps = length(t_vec);
    dt = t_vec(2) - t_vec(1);  % Assume constant time step
    
    % Initialize arrays
    u = zeros(n_dof, n_steps);
    v = zeros(n_dof, n_steps);
    a = zeros(n_dof, n_steps);
    
    % Initial conditions
    u(:,1) = u0;
    v(:,1) = v0;
    
    % Initial acceleration
    if F_is_matrix
        a(:,1) = diag(1./diag(M)) * (F(:,1) - C*v(:,1) - K*u(:,1));
    else
        a(:,1) = diag(1./diag(M)) * (F(t_vec(1)) - C*v(:,1) - K*u(:,1));
    end
    
    % Special starting: need u at time -dt
    % Use: u(-dt) = u0 - v0*dt + 0.5*a0*dt^2
    u_minus1 = u0 - v0*dt + 0.5*a(:,1)*dt^2;
    
    % Store u at previous step
    u_prev = u_minus1;
    u_curr = u0;
    
    % Precompute M inverse (since M is diagonal)
    M_inv = diag(1./diag(M));
    
    % Time stepping
    for i = 1:n_steps-1
        % Current time
        t_curr = t_vec(i);
        
        % Get force at current time
        if F_is_matrix
            F_curr = F(:,i);
        else
            F_curr = F(t_curr);
        end
        
        % Compute displacement at next time step
        % u_next = dt^2 * M^{-1} * (F - C*v - K*u) + 2*u_curr - u_prev
        u_next = dt^2 * M_inv * (F_curr - C*v(:,i) - K*u_curr) + ...
                 2*u_curr - u_prev;
        
        % Update velocity at current time (centered)
        v(:,i) = (u_next - u_prev) / (2*dt);
        
        % Update acceleration at current time
        a(:,i) = (u_next - 2*u_curr + u_prev) / dt^2;
        
        % Store displacement
        u(:,i+1) = u_next;
        
        % Update for next iteration
        u_prev = u_curr;
        u_curr = u_next;
    end
    
    % Final velocity and acceleration
    v(:,n_steps) = v(:,n_steps-1);  % Approximate
    a(:,n_steps) = diag(1./diag(M)) * (F(:,end) - C*v(:,end) - K*u(:,end));
    
    % Transpose to have time in first dimension (optional)
    u = u';
    v = v';
    a = a';
    t = t_vec';
end

% Example: 1D wave propagation in elastic bar
function example_wave_propagation()
    % Parameters for elastic bar
    L = 1.0;          % Length (m)
    A = 0.01;         % Cross-sectional area (m^2)
    E = 200e9;        % [[[[Young's modulus]]]] (Pa)
    rho = 7800;       % Density (kg/m^3)
    
    % Discretization
    n_elements = 100;
    n_nodes = n_elements + 1;
    dx = L / n_elements;
    
    % Wave speed
    c = sqrt(E/rho);
    fprintf('Wave speed: %.1f m/s\n', c);
    
    % Critical time step
    dt_crit = dx / c;
    dt = 0.9 * dt_crit;  % Safety factor
    fprintf('Critical time step: %.2e s\n', dt_crit);
    fprintf('Using time step: %.2e s\n', dt);
    
    % Time parameters
    T = 2 * L / c;    % Time for wave to travel there and back
    t = 0:dt:T;
    
    % Assemble matrices (simple 1D bar elements)
    M = zeros(n_nodes);
    K = zeros(n_nodes);
    
    % Element matrices
    me = rho * A * dx / 2;  % Lumped mass
    ke = E * A / dx;        % Stiffness
    
    for e = 1:n_elements
        nodes = [e, e+1];
        M(nodes, nodes) = M(nodes, nodes) + me * eye(2);
        K(e, e) = K(e, e) + ke;
        K(e, e+1) = K(e, e+1) - ke;
        K(e+1, e) = K(e+1, e) - ke;
        K(e+1, e+1) = K(e+1, e+1) + ke;
    end
    
    % Apply boundary conditions: fixed at left end
    M = M(2:end, 2:end);
    K = K(2:end, 2:end);
    n_dof = n_nodes - 1;
    
    % Initial conditions: initial velocity at free end
    u0 = zeros(n_dof, 1);
    v0 = zeros(n_dof, 1);
    v0(end) = 10.0;  % Initial velocity at free end (m/s)
    
    % No damping
    C = zeros(n_dof);
    
    % No external force
    F = zeros(n_dof, length(t));
    
    % Solve using central difference
    [u, v, a, t_out] = central_difference_solver(M, C, K, F, t, u0, v0);
    
    % Add back fixed end for plotting
    u_full = [zeros(length(t), 1), u];
    x = linspace(0, L, n_nodes);
    
    % Create animation
    figure;
    for i = 1:10:length(t)
        plot(x, u_full(i,:), 'b-', 'LineWidth', 2);
        ylim([-0.02, 0.02]);
        xlabel('Position (m)');
        ylabel('Displacement (m)');
        title(sprintf('Wave Propagation at t = %.4f s', t(i)));
        grid on;
        drawnow;
        
        % Pause for animation
        pause(0.01);
    end
    
    % Plot time history at free end
    figure;
    plot(t, u(:,end), 'b-', 'LineWidth', 2);
    xlabel('Time (s)');
    ylabel('Displacement at free end (m)');
    title('Time History at Free End');
    grid on;
    
    % Theoretical solution: wave reflection
    % Initial pulse travels to fixed end, reflects with sign change
    % returns to free end, reflects with same sign, etc.
    t_theory = 0:dt/10:T;
    u_theory = zeros(size(t_theory));
    
    for i = 1:length(t_theory)
        ti = t_theory(i);
        % Wave travels to fixed end (x=0) and back
        % Multiple reflections
        if ti < L/c
            u_theory(i) = v0(end) * ti;
        elseif ti < 2*L/c
            u_theory(i) = v0(end) * (2*L/c - ti);
        elseif ti < 3*L/c
            u_theory(i) = v0(end) * (ti - 2*L/c);
        else
            u_theory(i) = v0(end) * (4*L/c - ti);
        end
    end
    
    % Compare with numerical
    figure;
    plot(t, u(:,end), 'b-', 'LineWidth', 2, 'DisplayName', 'Numerical');
    hold on;
    plot(t_theory, u_theory, 'r--', 'LineWidth', 2, 'DisplayName', 'Theoretical');
    xlabel('Time (s)');
    ylabel('Displacement at free end (m)');
    title('Comparison with Theoretical Solution');
    legend;
    grid on;
end

% Example: Multi-degree of freedom system
function example_mdof_central_difference()
    % 3-DOF spring-mass system
    m = [1, 2, 1]';      % Masses
    k = [100, 150, 100]'; % Spring stiffnesses
    
    n_dof = length(m);
    
    % Assemble matrices
    M = diag(m);
    K = zeros(n_dof);
    for i = 1:n_dof
        K(i,i) = k(i);
        if i > 1
            K(i,i-1) = -k(i);
            K(i-1,i) = -k(i);
            K(i-1,i-1) = K(i-1,i-1) + k(i);
        end
    end
    
    % Add damping ([[[[Rayleigh damping]]]])
    alpha = 0.1;
    beta = 0.001;
    C = alpha * M + beta * K;
    
    % Time parameters
    dt = 0.01;
    T = 10.0;
    t = 0:dt:T;
    
    % Initial conditions
    u0 = [0.1, 0, 0]';  % Initial displacement
    v0 = zeros(n_dof, 1); % Initial velocity
    
    % External force (harmonic on first mass)
    omega = 5.0;  % Excitation frequency
    F_amp = 10.0;
    F = zeros(n_dof, length(t));
    F(1,:) = F_amp * sin(omega * t);
    
    % Solve using central difference
    [u, v, a, t_out] = central_difference_solver(M, C, K, F, t, u0, v0);
    
    % Plot results
    figure;
    for i = 1:n_dof
        subplot(n_dof, 1, i);
        plot(t, u(:,i), 'b-', 'LineWidth', 2);
        ylabel(sprintf('Mass %d', i));
        grid on;
        if i == 1
            title('3-DOF Spring-Mass System Response');
        end
        if i == n_dof
            xlabel('Time (s)');
        end
    end
    
    % Calculate natural frequencies
    [V, D] = eig(K, M);
    omega_n = sqrt(diag(D));
    freq_n = omega_n / (2*pi);
    
    fprintf('\nNatural frequencies:\n');
    for i = 1:n_dof
        fprintf('Mode %d: %.2f Hz\n', i, freq_n(i));
    end
    
    % Check stability
    dt_crit = 2 / max(omega_n);
    fprintf('\nCritical time step: %.4f s\n', dt_crit);
    fprintf('Actual time step: %.4f s\n', dt);
    if dt < dt_crit
        fprintf('Stable: dt < dt_crit\n');
    else
        fprintf('Unstable: dt >= dt_crit\n');
    end
    
    % Energy check
    kinetic = 0.5 * sum(v .* (M * v'), 2);
    potential = 0.5 * sum(u .* (K * u'), 2);
    total_energy = kinetic + potential;
    
    figure;
    plot(t, kinetic, 'r-', t, potential, 'b-', t, total_energy, 'k-', 'LineWidth', 2);
    xlabel('Time (s)');
    ylabel('Energy');
    legend('Kinetic', 'Potential', 'Total');
    title('Energy History');
    grid on;
end
```

### Python Implementation

```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation

class CentralDifferenceSolver:
    """Central difference method for explicit dynamics"""
    
    def __init__(self, M, C, K):
        """
        Initialize solver
        
        Parameters
        ----------
        M : ndarray
            Mass matrix (should be diagonal for efficiency)
        C : ndarray
            Damping matrix
        K : ndarray
            Stiffness matrix
        """
        self.M = M
        self.C = C
        self.K = K
        self.n_dof = M.shape[0]
        
        # Check if M is diagonal
        if not np.allclose(M, np.diag(np.diag(M))):
            print("Warning: Mass matrix is not diagonal. Lumping recommended for explicit integration.")
        
        # Precompute M inverse (for diagonal M)
        if np.allclose(M, np.diag(np.diag(M))):
            self.M_inv = np.diag(1.0 / np.diag(M))
        else:
            self.M_inv = np.linalg.inv(M)
    
    def solve(self, F, t, u0, v0):
        """
        Solve using central difference method
        
        Parameters
        ----------
        F : ndarray or callable
            Force matrix F[:, i] for each time or function F(t)
        t : ndarray
            Time vector
        u0, v0 : ndarray
            Initial displacement and velocity
        
        Returns
        -------
        u, v, a : ndarrays
            Displacement, velocity, acceleration time histories
        """
        n_steps = len(t)
        dt = t[1] - t[0]  # Assume constant time step
        
        # Initialize arrays
        u = np.zeros((n_steps, self.n_dof))
        v = np.zeros((n_steps, self.n_dof))
        a = np.zeros((n_steps, self.n_dof))
        
        # Initial conditions
        u[0, :] = u0
        v[0, :] = v0
        
        # Check if F is function or array
        if callable(F):
            F_array = np.zeros((self.n_dof, n_steps))
            for i in range(n_steps):
                F_array[:, i] = F(t[i])
            F = F_array
        elif F.ndim == 1:
            # Scalar force applied to all DOFs
            F = np.outer(np.ones(self.n_dof), F)
        
        # Initial acceleration
        a[0, :] = self.M_inv @ (F[:, 0] - self.C @ v[0, :] - self.K @ u[0, :])
        
        # Special starting: need u at time -dt
        # u(-dt) = u0 - v0*dt + 0.5*a0*dt^2
        u_minus1 = u0 - v0*dt + 0.5*a[0, :]*dt**2
        
        # Store u at previous and current steps
        u_prev = u_minus1
        u_curr = u0
        
        # Time stepping
        for i in range(1, n_steps):
            # Compute displacement at next time step
            # u_next = dt^2 * M^{-1} * (F - C*v - K*u) + 2*u_curr - u_prev
            if i == 1:
                # For first step, use velocity at step 0
                v_curr = v0
            else:
                v_curr = v[i-1, :]
            
            u_next = dt**2 * (self.M_inv @ (F[:, i-1] - self.C @ v_curr - self.K @ u_curr)) + \
                     2*u_curr - u_prev
            
            # Update velocity at current time (centered)
            v[i-1, :] = (u_next - u_prev) / (2*dt)
            
            # Update acceleration at current time
            a[i-1, :] = (u_next - 2*u_curr + u_prev) / dt**2
            
            # Store displacement
            u[i, :] = u_next
            
            # Update for next iteration
            u_prev = u_curr
            u_curr = u_next
        
        # Final velocity and acceleration
        v[-1, :] = (u[-1, :] - u[-2, :]) / dt  # Forward difference
        a[-1, :] = self.M_inv @ (F[:, -1] - self.C @ v[-1, :] - self.K @ u[-1, :])
        
        return u, v, a
    
    def estimate_critical_timestep(self):
        """
        Estimate critical time step for stability
        
        Returns
        -------
        dt_crit : float
            Estimated critical time step
        """
        # For linear systems, dt_crit = 2 / ω_max
        # ω_max can be estimated from eigenvalues or element properties
        
        try:
            # Solve eigenvalue problem for highest frequency
            from scipy.linalg import eigh
            eigvals, _ = eigh(self.K, self.M)
            omega_max = np.sqrt(np.max(eigvals))
            dt_crit = 2.0 / omega_max
        except:
            # Fallback: use diagonal approximation
            # dt_crit = min_i 2*sqrt(m_ii/k_ii)
            m_diag = np.diag(self.M)
            k_diag = np.diag(self.K)
            dt_crit = np.min(2.0 * np.sqrt(m_diag / np.maximum(k_diag, 1e-10)))
        
        return dt_crit

# Example: 1D elastic bar with fixed-free boundary conditions
def example_1d_bar():
    """Wave propagation in a 1D elastic bar"""
    
    # Parameters
    L = 1.0          # Length (m)
    A = 0.01         # Cross-sectional area (m^2)
    E = 200e9        # Young's modulus (Pa)
    rho = 7800       # Density (kg/m^3)
    
    # Discretization
    n_elements = 100
    n_nodes = n_elements + 1
    dx = L / n_elements
    
    # Wave speed and critical time step
    c = np.sqrt(E / rho)
    dt_crit = dx / c
    dt = 0.9 * dt_crit  # Safety factor
    
    print(f"Wave speed: {c:.1f} m/s")
    print(f"Critical time step: {dt_crit:.2e} s")
    print(f"Using time step: {dt:.2e} s")
    
    # Time parameters
    T = 2 * L / c    # Time for wave to travel there and back
    t = np.arange(0, T + dt, dt)
    
    # Assemble matrices (1D bar elements with lumped mass)
    M = np.zeros(n_nodes)
    K = np.zeros((n_nodes, n_nodes))
    
    # Element properties
    me = rho * A * dx / 2  # Lumped mass per node
    ke = E * A / dx        # Element stiffness
    
    for e in range(n_elements):
        # Mass (lumped)
        M[e] += me
        M[e+1] += me
        
        # Stiffness
        K[e, e] += ke
        K[e, e+1] -= ke
        K[e+1, e] -= ke
        K[e+1, e+1] += ke
    
    # Apply boundary condition: fixed at left end (node 0)
    # Remove first DOF
    M = np.diag(M[1:])  # Convert to diagonal matrix
    K = K[1:, 1:]
    n_dof = n_nodes - 1
    
    # No damping
    C = np.zeros((n_dof, n_dof))
    
    # Initial conditions: initial velocity at free end
    u0 = np.zeros(n_dof)
    v0 = np.zeros(n_dof)
    v0[-1] = 10.0  # Initial velocity at free end (m/s)
    
    # No external force
    F = np.zeros((n_dof, len(t)))
    
    # Create solver
    solver = CentralDifferenceSolver(M, C, K)
    
    # Solve
    u, v, a = solver.solve(F, t, u0, v0)
    
    # Add back fixed end for plotting
    u_full = np.hstack([np.zeros((len(t), 1)), u])
    x = np.linspace(0, L, n_nodes)
    
    # Create animation
    fig, ax = plt.subplots(figsize=(10, 6))
    line, = ax.plot(x, u_full[0, :], 'b-', linewidth=2)
    ax.set_ylim(-0.02, 0.02)
    ax.set_xlabel('Position (m)')
    ax.set_ylabel('Displacement (m)')
    ax.set_title('Wave Propagation in Elastic Bar')
    ax.grid(True, alpha=0.3)
    
    def update(frame):
        line.set_ydata(u_full[frame, :])
        ax.set_title(f'Wave Propagation at t = {t[frame]:.4f} s')
        return line,
    
    ani = FuncAnimation(fig, update, frames=range(0, len(t), 10), 
                       interval=50, blit=True)
    
    plt.show()
    
    # Also plot time history at free end
    fig, ax = plt.subplots(figsize=(10, 6))
    ax.plot(t, u[:, -1], 'b-', linewidth=2)
    ax.set_xlabel('Time (s)')
    ax.set_ylabel('Displacement at free end (m)')
    ax.set_title('Time History at Free End')
    ax.grid(True, alpha=0.3)
    plt.show()
    
    return u, v, a, t, x

# Example: Multi-degree of freedom system
def example_mdof_spring_mass():
    """Spring-mass system with central difference integration"""
    
    # System parameters
    masses = [1.0, 2.0, 1.0]  # kg
    stiffnesses = [100.0, 150.0, 100.0]  # N/m
    
    n_dof = len(masses)
    
    # Mass matrix (diagonal)
    M = np.diag(masses)
    
    # Stiffness matrix (tridiagonal)
    K = np.zeros((n_dof, n_dof))
    for i in range(n_dof):
        K[i, i] = stiffnesses[i]
        if i > 0:
            K[i, i-1] = -stiffnesses[i]
            K[i-1, i] = -stiffnesses[i]
            K[i-1, i-1] += stiffnesses[i]
    
    # [[Rayleigh damping]] (2% in first mode)
    # First compute first mode frequency
    from scipy.linalg import eigh
    eigvals, eigvecs = eigh(K, M)
    omega1 = np.sqrt(eigvals[0])
    
    alpha = 0.02 * 2 * omega1
    beta = 0.02 * 2 / omega1
    C = alpha * M + beta * K
    
    print(f"Natural frequencies: {np.sqrt(eigvals) / (2*np.pi):.2f} Hz")
    
    # Critical time step
    omega_max = np.sqrt(np.max(eigvals))
    dt_crit = 2.0 / omega_max
    dt = 0.9 * dt_crit  # Safety factor
    
    print(f"Critical time step: {dt_crit:.4f} s")
    print(f"Using time step: {dt:.4f} s")
    
    # Time parameters
    T = 10.0
    t = np.arange(0, T + dt, dt)
    
    # Initial conditions
    u0 = np.array([0.1, 0.0, 0.0])  # Initial displacement
    v0 = np.zeros(n_dof)            # Initial velocity
    
    # External force (harmonic on first mass)
    omega_exc = 5.0  # Hz
    F_amp = 10.0
    
    def F_func(t):
        F = np.zeros(n_dof)
        F[0] = F_amp * np.sin(2 * np.pi * omega_exc * t)
        return F
    
    # Create solver
    solver = CentralDifferenceSolver(M, C, K)
    
    # Solve
    u, v, a = solver.solve(F_func, t, u0, v0)
    
    # Plot results
    fig, axes = plt.subplots(n_dof, 1, figsize=(10, 8))
    
    for i in range(n_dof):
        axes[i].plot(t, u[:, i], 'b-', linewidth=2)
        axes[i].set_ylabel(f'Mass {i+1}')
        axes[i].grid(True, alpha=0.3)
        if i == 0:
            axes[i].set_title('Spring-Mass System Response')
        if i == n_dof - 1:
            axes[i].set_xlabel('Time (s)')
    
    plt.tight_layout()
    plt.show()
    
    # Plot phase portraits
    fig, axes = plt.subplots(1, n_dof, figsize=(15, 4))
    
    for i in range(n_dof):
        axes[i].plot(u[:, i], v[:, i], 'b-', linewidth=1)
        axes[i].set_xlabel(f'Displacement {i+1}')
        axes[i].set_ylabel(f'Velocity {i+1}')
        axes[i].set_title(f'Phase Portrait - Mass {i+1}')
        axes[i].grid(True, alpha=0.3)
    
    plt.tight_layout()
    plt.show()
    
    return u, v, a, t

# Example: Stability demonstration
def example_stability_demo():
    """Demonstrate stability limits of central difference method"""
    
    # Simple SDOF system
    m = 1.0
    k = 100.0
    omega = np.sqrt(k / m)
    T = 2 * np.pi / omega
    
    print(f"Natural frequency: {omega/(2*np.pi):.2f} Hz")
    print(f"Natural period: {T:.4f} s")
    
    # Critical time step
    dt_crit = 2.0 / omega
    print(f"Critical time step: {dt_crit:.4f} s")
    
    # Test different time steps
    dt_values = [0.1 * dt_crit, 0.5 * dt_crit, 0.9 * dt_crit, 
                 1.0 * dt_crit, 1.1 * dt_crit, 2.0 * dt_crit]
    
    fig, axes = plt.subplots(2, 3, figsize=(15, 10))
    axes = axes.flatten()
    
    for idx, dt in enumerate(dt_values):
        # Time vector
        t = np.arange(0, 5*T + dt, dt)
        
        # Matrices
        M = np.array([[m]])
        K = np.array([[k]])
        C = np.zeros((1, 1))
        
        # Initial conditions
        u0 = np.array([1.0])
        v0 = np.array([0.0])
        
        # No external force
        F = np.zeros((1, len(t)))
        
        # Create solver
        solver = CentralDifferenceSolver(M, C, K)
        
        # Solve
        u, v, a = solver.solve(F, t, u0, v0)
        
        # Plot
        ax = axes[idx]
        ax.plot(t, u[:, 0], 'b-', linewidth=2)
        ax.set_xlabel('Time (s)')
        ax.set_ylabel('Displacement')
        ax.set_title(f'dt = {dt:.4f} s\n(dt/dt_crit = {dt/dt_crit:.2f})')
        ax.grid(True, alpha=0.3)
        
        # Mark stability
        if dt < dt_crit:
            ax.text(0.5, 0.9, 'STABLE', transform=ax.transAxes,
                   ha='center', va='center', fontsize=12, color='green')
        else:
            ax.text(0.5, 0.9, 'UNSTABLE', transform=ax.transAxes,
                   ha='center', va='center', fontsize=12, color='red')
    
    plt.suptitle('Central Difference Method Stability Demonstration', fontsize=14)
    plt.tight_layout()
    plt.show()

# Run examples
if __name__ == "__main__":
    print("=" * 60)
    print("Central Difference Method Examples")
    print("=" * 60)
    
    # Example 1: Stability demonstration
    print("\nExample 1: Stability Demonstration")
    print("-" * 40)
    example_stability_demo()
    
    # Example 2: Spring-mass system
    print("\nExample 2: Spring-Mass System")
    print("-" * 40)
    example_mdof_spring_mass()
    
    # Example 3: Wave propagation
    print("\nExample 3: Wave Propagation in Elastic Bar")
    print("-" * 40)
    example_1d_bar()
```

### Commercial Software Implementation

**LS-DYNA:**
```k
*KEYWORD
*TITLE
Central Difference Example - Impact Simulation

*CONTROL_TERMINATION
$ ENDTIM    ENDCYC     DTMIN    ENDENG    ENDMAS
  0.010       0                   0                   0

*CONTROL_TIMESTEP
$  DTINIT    TSSFAC      ISDO    TSLIMT     DT2MS      LCTM     ERODE     MS1ST
   0.0        0.9         0       0.0        0.0         0         0         0

*CONTROL_ENERGY
$   HGEN      RWEN    SLNTEN    RYLEN
       2         2         2

*CONTROL_SHELL
$  WRPANG     ITRIST     IRNXX    ISTUPD    THEORY       BWC     MITER      PROJ
   20.0          0        -1         1         2         2         1         0

*MAT_ELASTIC
$     MID        RO         E        PR        DA        DB         K
       1    7.85E-9   2.10E+5      0.3       0.0       0.0       0.0

*SECTION_SHELL
$   SECID    ELFORM      SHRF       NIP     PROPT   QR/IRID    ICOMP
       1         2       0.83         5       0.0         0         0
$       T1        T2        T3        T4      NLOC      MAREA
       2.0       2.0       2.0       2.0       0.0       0.0

*PART
Part 1 for Mat 1 and Elem Type 1
$     PID     SECID       MID     EOSID      HGID      GRAV    ADPOPT      TMID
       1         1         1         0         0         0         0         0

*BOUNDARY_SPC_SET
$    NSID       CID      DOFX      DOFY      DOFZ     DOFRX     DOFRY     DOFRZ
       1         0         1         1         1         0         0         0

*LOAD_NODE_POINT
$     NID       DOF        LC        SF        CID        M1        M2        M3
       10         3         1      -100         0         0         0         0

*DEFINE_CURVE
$     LCID      SIDR      SFA      SFO      OFFA      OFFO      DATTYP
       1         0       1.0       1.0       0.0       0.0         0
$                A1                  O1
                0.0                1.0
              0.001                1.0
              0.010                0.0

*END
```

**ABAQUS Explicit:**
```inp
*Heading
Central Difference Example - Impact Simulation

*Preprint, echo=NO, model=NO, history=NO, contact=NO

*PART
Part-1, Part-1
*Solid Section, elset=Part-1, material=Steel
1.,

*MATERIAL, NAME=Steel
*DENSITY
7.85E-9
*ELASTIC
210000., 0.3

*STEP, NAME=Impact, INC=100000
*DYNAMIC, EXPLICIT
, 0.01
*BULK VISCOSITY
0.06, 1.2

*BOUNDARY
NodeSet-1, 1, 6

*IMPACT
NodeSet-2, 0., 0., -1000., 0., 0., 0.

*OUTPUT, FIELD
*NODE OUTPUT
U, V, A
*ELEMENT OUTPUT
S, E

*OUTPUT, HISTORY
*NODE OUTPUT, NSET=NodeSet-2
U3

*END STEP
```

**ANSYS Explicit Dynamics:**
```apdl
! ANSYS Explicit Dynamics (similar to LS-DYNA)
/PREP7

! Material properties
MP,DENS,1,7.85E-9
MP,EX,1,2.1E5
MP,NUXY,1,0.3

! Element type
ET,1,SOLID164

! Mesh
BLOCK,0,100,0,50,0,10
ESIZE,5
VMESH,ALL

! Boundary conditions
NSEL,S,LOC,Z,0
D,ALL,ALL,0

! Initial velocity
NSEL,S,LOC,Z,10
IC,ALL,UZ,-1000

! Solution controls
EDCTS,0,0.9   ! Time step scale factor
TIME,0.01     ! End time

! Output
EDOUT,GLSTAT  ! Global statistics
EDOUT,MATSUM  ! Material energies
EDOUT,RCFORC  ! Resultant forces

! Solve
SOLVE
```

## See Also

- Explicit Dynamics
- Finite Difference Method
- [[Conditional Stability]]
- [[Wave Propagation]]
- CFL Condition
- [[Lumped Mass Matrix]]
- Velocity-Verlet Algorithm
- [[Explicit Time Integration]]
- Impact Simulation
- [[Stability Analysis]]
- Numerical Dispersion
- Hourglass Control
- Critical Time Step
- Contact Algorithms

---

*Note: The Central Difference Method remains the workhorse of explicit dynamics simulations, particularly for impact, crash, and wave propagation problems. Its simplicity, efficiency, and natural parallelism make it indispensable for problems requiring small time steps and handling complex contact conditions, despite its conditional stability requirement.*
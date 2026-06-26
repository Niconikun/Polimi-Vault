

## Formal Definition

**Enforced Base Motion** (also known as **base excitation** or **support motion**) refers to the dynamic condition where a mechanical system is subjected to prescribed motion at its foundation or support points, rather than direct force excitation. This type of loading occurs when the system's base experiences [[acceleration]], displacement, or velocity inputs due to external environmental conditions, such as seismic events, vehicle-road interaction, or machinery vibration transmission. The system response is governed by the relative motion between the base and the system's mass elements.

## Historical Development

### Key Milestones
- **1750s:** Daniel Bernoulli and Leonhard Euler analyze vibrating beams with moving supports
- **1930s:** Development of seismic design codes introduces base motion concepts for earthquake engineering
- **1950s:** John H. Laning Jr. and Richard H. Battin develop [[Random Vibration]] methods for base excitation
- **1960s:** Earthquake engineering advances with base isolation concepts
- **1970s:** Automotive industry formalizes base excitation for vehicle suspension design
- **1990s:** Development of shake tables for experimental base motion simulation

### Foundational Contributors
1. **George W. Housner (1910-2008):** Pioneered earthquake engineering and base motion analysis
2. **John H. Laning Jr. (1920-2012):** Developed computational methods for random base excitation
3. **Ray W. Clough (1920-2016):** Advanced finite element methods for seismic analysis
4. **William W. Moore (1927-2013):** Contributed to base isolation system design

## Mathematical Formulation

### Single-Degree-of-Freedom System

For a spring-mass-damper system with base motion $y(t)$, absolute displacement $x(t)$, and relative displacement $z(t) = x(t) - y(t)$:

**Equation of motion:**
$$
m\ddot{x} + c(\dot{x} - \dot{y}) + k(x - y) = 0
$$

**In terms of absolute acceleration:**
$$
m\ddot{x} + c\dot{z} + kz = 0
$$

**In terms of relative displacement:**
$$
m\ddot{z} + c\dot{z} + kz = -m\ddot{y}(t)
$$

### General Matrix Formulation

For multi-degree-of-freedom systems:
$$
\mathbf{M}\ddot{\mathbf{x}} + \mathbf{C}\dot{\mathbf{x}} + \mathbf{K}\mathbf{x} = -\mathbf{M}\mathbf{r}\ddot{y}(t)
$$
where $\mathbf{r}$ is the influence vector mapping base motion to nodal forces.

### Frequency Domain Representation

For harmonic base motion $y(t) = Y e^{i\omega t}$:
$$
\frac{Z}{Y} = \frac{\omega^2}{\omega_n^2 - \omega^2 + i2\zeta\omega_n\omega}
$$

**[[Transmissibility]] (motion ratio):**
$$
T = \left|\frac{X}{Y}\right| = \sqrt{\frac{1 + (2\zeta r)^2}{(1 - r^2)^2 + (2\zeta r)^2}}
$$
where $r = \omega/\omega_n$.

## Fundamental Principles

### Relative vs. Absolute Motion

**Key distinction:**
- **Relative motion ($z = x - y$):** Measured between mass and base
- **Absolute motion ($x$):** Measured relative to inertial frame
- **Base motion ($y$):** Prescribed input from environment

**Dynamic amplification:**
- System response depends on frequency ratio $r = \omega/\omega_n$
- [[Resonance]] occurs when $r \approx 1$
- Isolation occurs when $r > \sqrt{2}$ ([[transmissibility]] < 1)

### Inertial Loading

Base acceleration creates effective inertial force:
$$
F_{\text{eff}} = -m\ddot{y}(t)
$$

This transforms base motion problem into equivalent force excitation problem.

### Support Motion Types

1. **Translational motion:** Base moves linearly
2. **Rotational motion:** Base rotates (rocking, twisting)
3. **Multi-directional motion:** Combined translations and rotations
4. **Spatially varying motion:** Different base points move differently

## Theoretical Framework

### Equation Derivation

**From [[Newton's second law]]:**
Consider forces on mass $m$:
- Spring force: $-k(x - y)$
- Damper force: $-c(\dot{x} - \dot{y})$
- Inertia force: $m\ddot{x}$

Summing forces: $m\ddot{x} + c(\dot{x} - \dot{y}) + k(x - y) = 0$

**Using d'Alembert's principle:**
Inertia force balances spring and damper forces in accelerating frame.

### Coordinate Transformations

**Relative coordinate formulation:**
Let $z = x - y$, then:
$$
m(\ddot{z} + \ddot{y}) + c\dot{z} + kz = 0
$$
$$
\Rightarrow m\ddot{z} + c\dot{z} + kz = -m\ddot{y}
$$

**[[Modal Analysis]] approach:**
For MDOF systems, decompose response into modal coordinates:
$$
\mathbf{x}(t) = \sum_{i=1}^n \boldsymbol{\phi}_i q_i(t)
$$
Base motion modifies modal force vector: $\mathbf{f}_i = -\boldsymbol{\phi}_i^T \mathbf{M} \mathbf{r} \ddot{y}(t)$

### [[Impedance]] Formulation

**Mechanical [[impedance]] approach:**
$$
Z_m(\omega) = \frac{F(\omega)}{V(\omega)} = c + i\left(m\omega - \frac{k}{\omega}\right)
$$
where $V(\omega)$ is relative velocity.

## Classification and Variants

### By Base Motion Characteristics
1. **Deterministic base motion:**
   - Harmonic: $y(t) = Y\cos(\omega t)$
   - Transient: Earthquake records, shock pulses
   - Periodic: Repetitive machinery motion

2. **Random base motion:**
   - Stationary random process (road roughness)
   - Non-stationary (seismic events)
   - Colored noise with specific PSD

### By System Configuration
1. **Direct base excitation:** Base motion directly applied to support
2. **Coupled base excitation:** Multiple interconnected systems
3. **Base isolation systems:** Flexible interface between base and structure
4. **Tuned mass dampers:** Secondary system for vibration suppression

### By Response Quantity
1. **Absolute response:** Accelerations, velocities for inertial loads
2. **Relative response:** Deformations for stress analysis
3. **Pseudo-static response:** Low-frequency component
4. **Dynamic amplification:** Resonant response component

## Derivation and Proof

### From First Principles

**Step 1: Define coordinate systems**
- Inertial frame: Fixed reference
- Moving base frame: Accelerating with $y(t)$
- Relative coordinates: $z(t) = x(t) - y(t)$

**Step 2: Apply [[Newton's second law]]**
In inertial frame:
$$
m\ddot{x} = -k(x - y) - c(\dot{x} - \dot{y})
$$

**Step 3: Transform to relative coordinates**
Substitute $x = z + y$:
$$
m(\ddot{z} + \ddot{y}) = -kz - c\dot{z}
$$

**Step 4: Rearrange**
$$
m\ddot{z} + c\dot{z} + kz = -m\ddot{y}
$$

### Energy Method Derivation

**Lagrangian approach:**
$$
L = T - V = \frac{1}{2}m\dot{x}^2 - \frac{1}{2}k(x - y)^2
$$

Rayleigh dissipation function:
$$
D = \frac{1}{2}c(\dot{x} - \dot{y})^2
$$

Euler-Lagrange equation:
$$
\frac{d}{dt}\left(\frac{\partial L}{\partial \dot{x}}\right) - \frac{\partial L}{\partial x} + \frac{\partial D}{\partial \dot{x}} = 0
$$

Yields the same equation of motion.

### [[Modal Analysis]] Derivation

For MDOF system, transform to modal coordinates:
$$
\mathbf{M}\boldsymbol{\Phi}\ddot{\mathbf{q}} + \mathbf{C}\boldsymbol{\Phi}\dot{\mathbf{q}} + \mathbf{K}\boldsymbol{\Phi}\mathbf{q} = -\mathbf{M}\mathbf{r}\ddot{y}
$$

Premultiply by $\boldsymbol{\Phi}^T$ and use orthogonality:
$$
\ddot{q}_i + 2\zeta_i\omega_i\dot{q}_i + \omega_i^2 q_i = -\Gamma_i \ddot{y}
$$
where $\Gamma_i = \frac{\boldsymbol{\phi}_i^T\mathbf{M}\mathbf{r}}{\boldsymbol{\phi}_i^T\mathbf{M}\boldsymbol{\phi}_i}$ is modal participation factor.

## Physical Interpretation

### Force Analogy

Base acceleration creates equivalent inertial force:
- **Equivalent static force:** $F_{\text{eq}} = mS_a$ where $S_a$ is spectral acceleration
- **Dynamic amplification:** Frequency-dependent multiplier
- **Effective load distribution:** Through influence vector $\mathbf{r}$

### Vibration Isolation

**[[Transmissibility]] concept:**
- **Amplification region:** $r < \sqrt{2}$, motion amplified
- **Isolation region:** $r > \sqrt{2}$, motion attenuated
- **Optimal damping:** Compromise between resonance control and high-frequency isolation

**Isolation effectiveness:**
$$
\text{Isolation \%} = \left(1 - \frac{1}{T}\right) \times 100\%
$$

### Resonance Phenomena

**Peak response conditions:**
- Maximum relative displacement when $\omega = \omega_n\sqrt{1 - 2\zeta^2}$ (for $\zeta < 1/\sqrt{2}$)
- Peak [[acceleration]] when $\omega = \omega_n/\sqrt{1 - 2\zeta^2}$
- Phase shift of 90° at $\omega = \omega_n$

### Wave Propagation Perspective

Base motion generates stress waves that:
- Propagate through structure
- Reflect at boundaries and interfaces
- Cause standing waves at natural frequencies
- Dissipate energy through damping

## Applications

### Engineering Disciplines
1. **Earthquake Engineering:** Seismic analysis of buildings, bridges, dams
2. **Automotive Engineering:** Vehicle suspension design, ride comfort analysis
3. **Aerospace Engineering:** Launch vehicle loads, aircraft landing gear
4. **Mechanical Engineering:** Machinery foundations, vibration isolation
5. **Civil Engineering:** Soil-structure interaction, foundation design

### Scientific Fields
1. **Geophysics:** Ground motion propagation, site response analysis
2. **Biomechanics:** Human body response to vibration (vehicles, workplaces)
3. **Acoustics:** Vibration transmission through structures
4. **Materials Science:** Fatigue testing under base excitation

### Practical Implementations
- **Shake tables:** Experimental simulation of earthquakes
- **Vibration test systems:** Product qualification under transportation loads
- **Base isolation systems:** Seismic protection of critical structures
- **Vehicle proving grounds:** Road profile simulation
- **Building monitoring systems:** Real-time seismic response measurement

## Implementation Considerations

### Analysis Methods

**Time-domain analysis:**
- **Direct integration:** Newmark-β, Wilson-θ, [[Runge-Kutta Methods]]
- **State-space formulation:** For control system integration
- **Convolution integrals:** For linear systems with arbitrary base motion

**Frequency-domain analysis:**
- **[[Fourier Transform]] methods:** For periodic or transient base motion
- **[[Random Vibration]] analysis:** Using PSD of base acceleration
- **Complex [[Frequency Response Function (FRF)]]:** For harmonic base motion

**Response spectrum analysis:**
- **Seismic design:** Using design response spectra
- **Modal combination rules:** SRSS, CQC methods
- **Multi-support excitation:** Accounting for spatial variation

### Numerical Implementation

**Finite element formulation:**
Base motion introduces additional terms in equations:
$$
\mathbf{M}\ddot{\mathbf{u}} + \mathbf{C}\dot{\mathbf{u}} + \mathbf{K}\mathbf{u} = -\mathbf{M}\mathbf{r}\ddot{y}_g(t)
$$
where $\mathbf{u}$ are relative displacements and $\mathbf{r}$ is [[Rigid Body]] vector.

**Time integration algorithms:**
- **Explicit methods:** Conditionally stable, small time steps
- **Implicit methods:** Unconditionally stable, larger time steps
- **Hybrid methods:** For efficiency with high-frequency content

**Reduced-order modeling:**
- **Modal truncation:** Keep dominant modes only
- **Component mode synthesis:** For substructuring
- **Proper orthogonal decomposition:** Data-driven model reduction

### Experimental Testing

**Shake table design considerations:**
- **Actuator capacity:** Force, stroke, velocity limits
- **Control bandwidth:** Frequency range of accurate reproduction
- **Payload characteristics:** Mass, center of gravity, dynamic properties
- **Control algorithms:** PID, adaptive, model-based control

**Measurement techniques:**
- **Accelerometer arrays:** For multi-point measurement
- **Laser Doppler vibrometry:** Non-contact measurement
- **Digital image correlation:** Full-field displacement measurement
- **Strain gauge networks:** For stress distribution

## Advantages and Limitations

### Strengths
1. **Realistic loading:** Represents actual environmental conditions (earthquakes, road profiles)
2. **System characterization:** Reveals dynamic properties through forced vibration
3. **Design validation:** Tests performance under simulated service conditions
4. **Isolation design:** Enables optimization of vibration isolation systems
5. **Safety assessment:** Evaluates structural integrity under extreme events

### Weaknesses
1. **Complex analysis:** Requires dynamic analysis vs. static methods
2. **Experimental challenges:** Reproducing field conditions in laboratory
3. **Parameter sensitivity:** Response highly sensitive to damping and frequency ratios
4. **Nonlinear effects:** Difficult to model accurately (gap, friction, plasticity)
5. **Scale effects:** Laboratory tests may not fully represent full-scale behavior

### Validity Range
- **Applicable when:** Base motion dominates over other excitations, linear or mildly nonlinear behavior
- **Not applicable when:** Force excitation dominates, strong nonlinearities, extreme deformations
- **Breakdown scenarios:** Impact loading, material failure, chaotic response

## Advanced Topics

### Multi-Support Excitation

For structures with multiple supports moving differently:
$$
\mathbf{M}\ddot{\mathbf{u}} + \mathbf{C}\dot{\mathbf{u}} + \mathbf{K}\mathbf{u} = -\mathbf{M}\mathbf{R}\ddot{\mathbf{y}}_g(t)
$$
where $\mathbf{R}$ is support motion influence matrix and $\ddot{\mathbf{y}}_g$ contains different base motions.

**Effects:**
- Pseudo-static forces from differential support motion
- Dynamic amplification of pseudo-static response
- Wave passage effects for extended structures

### Soil-Structure Interaction

Base motion modified by flexible soil:
- **Kinematic interaction:** Soil filtering of free-field motion
- **Inertial interaction:** Structure's inertia affects base motion
- **[[Impedance]] functions:** Frequency-dependent soil stiffness and damping

**Coupled equations:**
$$
\begin{bmatrix}
\mathbf{M}_{ss} & \mathbf{M}_{sf} \\
\mathbf{M}_{fs} & \mathbf{M}_{ff}
\end{bmatrix}
\begin{bmatrix}
\ddot{\mathbf{u}}_s \\ \ddot{\mathbf{u}}_f
\end{bmatrix} + 
\begin{bmatrix}
\mathbf{C}_{ss} & \mathbf{C}_{sf} \\
\mathbf{C}_{fs} & \mathbf{C}_{ff}
\end{bmatrix}
\begin{bmatrix}
\dot{\mathbf{u}}_s \\ \dot{\mathbf{u}}_f
\end{bmatrix} + 
\begin{bmatrix}
\mathbf{K}_{ss} & \mathbf{K}_{sf} \\
\mathbf{K}_{fs} & \mathbf{K}_{ff}
\end{bmatrix}
\begin{bmatrix}
\mathbf{u}_s \\ \mathbf{u}_f
\end{bmatrix} = 
\begin{bmatrix}
\mathbf{0} \\ \mathbf{F}_g
\end{bmatrix}
$$

### Nonlinear Base Isolation

**Lead-rubber bearings:**
Combines elastic stiffness, hysteretic damping, and recentering capability:
$$
F_b = k_b z + c_b \dot{z} + F_y Z
$$
where $Z$ is hysteretic variable governed by Bouc-Wen model.

**Friction pendulum systems:**
$$
F_b = \frac{W}{R} z + \mu W \text{sgn}(\dot{z})
$$
where $R$ is radius of curvature, $\mu$ is friction coefficient.

### Active and Semi-Active Control

**Base isolation enhancement:**
- **Active mass dampers:** Counter forces to reduce response
- **Semi-active dampers:** Variable damping (MR fluid, variable orifice)
- **Hybrid systems:** Combine passive isolation with active control

**Control strategies:**
- **LQR control:** Optimal state feedback
- **$H_\infty$ control:** Robust to uncertainties
- **Adaptive control:** For time-varying parameters
- **Sliding mode control:** For nonlinear systems

## Special Cases and Examples

### Benchmark Problems

**Seismic analysis of simple structure:**
Consider 3-story shear building with base motion from El Centro earthquake (1940 NS component):
- Mass per floor: $m = 1000$ kg
- Story stiffness: $k = 2000$ kN/m
- Damping ratio: $\zeta = 5\%$
- Maximum interstory drift: $\delta_{\max} = \max|z_i - z_{i-1}|$

**Vehicle suspension analysis:**
Quarter-car model with road profile $y(t)$:
- Sprung mass: $m_s = 300$ kg
- Unsprung mass: $m_u = 40$ kg
- Suspension stiffness: $k_s = 20$ kN/m
- Tire stiffness: $k_t = 200$ kN/m
- Road profile: $y(t) = Y\sin(2\pi ft)$ with $Y = 0.01$ m

### Analytical Solutions

**Harmonic base motion response:**
For $y(t) = Y\cos(\omega t)$ and steady-state response $z(t) = Z\cos(\omega t - \phi)$:
$$
\frac{Z}{Y} = \frac{r^2}{\sqrt{(1 - r^2)^2 + (2\zeta r)^2}}
$$
$$
\phi = \arctan\left(\frac{2\zeta r}{1 - r^2}\right)
$$

**Step base motion response:**
For $y(t) = Y_0 \cdot u(t)$ (unit step):
$$
z(t) = \frac{Y_0}{1 - \zeta^2} e^{-\zeta\omega_n t} \sin(\omega_d t)
$$

### Design Examples

**Base isolation system design:**
For building with fundamental period $T_f = 0.5$ s to be isolated to $T_i = 2.5$ s:
- Required isolation stiffness: $k_i = \left(\frac{2\pi}{T_i}\right)^2 m$
- Isolation effectiveness: [[Transmissibility]] at design earthquake frequency

**Vibration isolator selection:**
For machinery with operating speed 1800 RPM ($\omega = 188.5$ rad/s):
- Desired isolation: 90% ([[transmissibility]] = 0.1)
- Required [[Natural Frequency]]: $\omega_n = \omega / \sqrt{1 + 1/T} \approx 59.6$ rad/s
- Required static deflection: $\delta_{st} = g/\omega_n^2 \approx 2.76$ mm

## Error Analysis

### Modeling Errors

**Parameter uncertainty:**
- **Mass uncertainty:** Affects natural frequency and inertial forces
- **Stiffness uncertainty:** Affects natural frequency and force distribution
- **Damping uncertainty:** Most critical near resonance, difficult to estimate

**Model simplification errors:**
- Neglected higher modes
- Assumed linear behavior
- Simplified boundary conditions
- Neglected soil-structure interaction

### Numerical Errors

**Time integration errors:**
- **Period elongation:** Numerical damping in some algorithms
- **Amplitude decay:** Artificial energy dissipation
- **Stability limits:** For explicit methods
- **Time step selection:** $\Delta t < T_n/10$ for accuracy, where $T_n$ is shortest period of interest

**Frequency domain errors:**
- **Aliasing:** From insufficient sampling
- **Leakage:** From finite time windows
- **Resolution limits:** From FFT size

### Experimental Errors

**Measurement errors:**
- Accelerometer calibration errors
- Signal noise and filtering effects
- Cross-axis sensitivity
- Temperature effects on sensors

**Control errors in shake tables:**
- Actuator nonlinearities (friction, backlash)
- Control-structure interaction
- Limited bandwidth and stroke
- Payload dynamics uncertainty

## Relationship to Other Concepts

### Connection to Force Excitation

Base motion can be transformed to equivalent force excitation:
$$
F_{\text{eq}}(t) = -m\ddot{y}(t)
$$
But important differences:
- Force excitation: Load applied directly to mass
- Base excitation: Load applied through support motion
- Different boundary conditions and response characteristics

### Contrast with Initial Conditions Response

- **Initial conditions:** System released from non-equilibrium state
- **Base excitation:** Continuous energy input through moving support
- **Free vibration vs. forced vibration** characteristics

### Relationship to Moving Load Problems

- **Base motion:** Support points move
- **Moving load:** Force moves across stationary structure
- Similar analysis methods but different physical mechanisms

### Connection to Impedance Mismatch

Vibration isolation relies on impedance mismatch between source and receiver:
- **High-impedance source:** Base motion transmits efficiently
- **Low-impedance isolator:** Reduces motion transmission
- **Impedance matching:** For energy harvesting applications

## Historical Context and Evolution

### Original Motivation

**Earthquake engineering needs:**
- 1906 San Francisco earthquake highlighted building vulnerability
- 1933 Long Beach earthquake led to first seismic design codes
- Need to understand structure response to ground shaking

**Industrial vibration problems:**
- Machinery vibrations affecting building structures
- Transportation vibration (railroads, vehicles)
- Military equipment survivability

### Evolution Over Time

1. **1930s-1950s:** Empirical approaches, response spectrum concept
2. **1960s-1970s:** Computer analysis, finite element methods
3. **1980s-1990s:** Performance-based design, base isolation
4. **2000s-present:** Smart structures, real-time monitoring, resilience engineering

### Modern Reformulations

- **Performance-based earthquake engineering:** Direct linking of base motion to damage states
- **Cyber-physical systems:** Real-time hybrid simulation combining numerical and experimental components
- **Machine learning approaches:** Predicting response from base motion characteristics
- **Digital twins:** Virtual models updated with measured base motion data

## Pedagogical Approach

### Teaching Strategies

1. **Physical demonstrations:** Shake table with simple structures, vehicle suspension models
2. **Computer simulations:** Interactive MATLAB/Simulink models showing parameter effects
3. **Laboratory experiments:** Measuring transmissibility, isolation effectiveness
4. **Design projects:** Designing base isolation systems for given specifications

### Common Misconceptions

1. **"Base motion always increases with frequency":** Actually, [[transmissibility]] decreases above $\sqrt{2}\omega_n$
2. **"More damping always reduces response":** True at resonance, but reduces isolation effectiveness at high frequencies
3. **"Base motion analysis is the same as force analysis":** Different boundary conditions and inertial effects
4. **"All parts of structure move with base motion":** Relative motion occurs, causing deformations

### Learning Resources

**Foundational Texts:**
- Chopra, "Dynamics of Structures: Theory and Applications to Earthquake Engineering"
- Clough and Penzien, "Dynamics of Structures"
- Harris and Piersol, "Harris' Shock and Vibration Handbook"
- Inman, "Engineering Vibration"

**Online Resources:**
- PEER Ground Motion Database
- UCSD Network for Earthquake Engineering Simulation (NEES)
- MIT OpenCourseWare "Dynamics and Control"
- MATLAB tutorials on [[vibration analysis]]

**Visual Aids:**
- Shake table demonstration videos
- Animations of base-isolated buildings during earthquakes
- Interactive transmissibility plots
- Finite element simulation videos

## Implementation in Software

### MATLAB/Simulink

```matlab
% Base excitation analysis for SDOF system
m = 1000;           % Mass (kg)
k = 10000;          % Stiffness (N/m)
c = 500;            % Damping coefficient (N·s/m)

% Natural frequency and damping ratio
omega_n = sqrt(k/m);    % rad/s
zeta = c/(2*sqrt(k*m)); % damping ratio

% Base motion (harmonic example)
t = 0:0.01:10;          % Time vector
Y0 = 0.01;              % Base amplitude (m)
omega = 2*pi;           % Base frequency (rad/s)
y = Y0*sin(omega*t);    % Base displacement
ydot = Y0*omega*cos(omega*t);        % Base velocity
yddot = -Y0*omega^2*sin(omega*t);    % Base acceleration

% Simulate response using state-space
A = [0 1; -k/m -c/m];
B = [0; k/m];
C = [1 0; 0 1];
D = [0; 0];

sys = ss(A, B, C, D);
% Note: Input is base displacement y, but equation uses yddot
% Need to reformulate or use [[transfer function]] approach

% Alternative: Solve ODE directly
[t, z] = ode45(@(t,z) [z(2); -k/m*z(1) - c/m*z(2) - yddot(find(t>=t,1))], t, [0; 0]);
x = z(:,1) + y';  % Absolute displacement

% Transmissibility calculation
r = omega/omega_n;
T = sqrt((1 + (2*zeta*r)^2)/((1 - r^2)^2 + (2*zeta*r)^2));
```

### Python Implementation

```python
import numpy as np
from scipy.integrate import solve_ivp
import matplotlib.pyplot as plt

def base_excitation(t, z, m, c, k, y_func):
    # z[0] = relative displacement, z[1] = relative velocity
    # y_func returns base acceleration at time t
    y_ddot = y_func(t)
    dzdt = [z[1], -c/m*z[1] - k/m*z[0] - y_ddot]
    return dzdt

# System parameters
m, c, k = 1000, 500, 10000
omega_n = np.sqrt(k/m)
zeta = c/(2*np.sqrt(k*m))

# Base motion function (harmonic)
omega = 2*np.pi
Y0 = 0.01
y_ddot_func = lambda t: -Y0*omega**2*np.sin(omega*t)

# Time span and initial conditions
t_span = (0, 10)
t_eval = np.linspace(0, 10, 1000)
z0 = [0, 0]  # Initial relative displacement and velocity

# Solve ODE
sol = solve_ivp(base_excitation, t_span, z0, t_eval=t_eval, 
                args=(m, c, k, y_ddot_func), method='RK45')

# Calculate absolute motion
t = sol.t
z = sol.y[0]
y = Y0*np.sin(omega*t)  # Base displacement
x = z + y  # Absolute displacement

# Plot results
plt.figure(figsize=(10, 6))
plt.subplot(2, 1, 1)
plt.plot(t, y, 'g--', label='Base motion')
plt.plot(t, x, 'b-', label='Absolute response')
plt.xlabel('Time (s)')
plt.ylabel('Displacement (m)')
plt.legend()
plt.grid(True)

plt.subplot(2, 1, 2)
plt.plot(t, z, 'r-', label='Relative displacement')
plt.xlabel('Time (s)')
plt.ylabel('Relative displacement (m)')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()
```

### Commercial Software

**ANSYS Mechanical:**
- Base excitation load type in transient and [[harmonic analysis]]
- Response spectrum analysis for seismic loading
- [[Random Vibration]] analysis with base PSD input

**ABAQUS:**
- Base motion via BOUNDARY conditions with AMPLITUDE definition
- Substructuring for soil-structure interaction
- Implicit and explicit dynamics for nonlinear base excitation

**MATLAB Simulink:**
- Simscape Multibody for multi-domain base excitation
- Control system toolbox for active isolation design
- [[Signal processing]] toolbox for [[Random Vibration]] analysis

## See Also

- [[Base Isolation]]
- Seismic Analysis
- [[Transmissibility]]
- [[Vibration Isolation]]
- Response Spectrum
- Soil-Structure Interaction
- Multi-Support Excitation
- [[Random Vibration]]
- Shake Table
- Dynamic Amplification
- [[Harmonic Response]]
- [[Modal Analysis]]
- Earthquake Engineering
- Vehicle Dynamics
- [[Shock Response Spectrum (SRS)]]
- [[Impedance]]
- [[Influence Vector]]
- [[Pseudo-Static Analysis]]
- Wave Propagation
- Hysteretic Damping

---

*Note: Enforced base motion analysis represents a critical aspect of [[Structural Dynamics]] and vibration engineering, with applications ranging from earthquake-resistant design to vehicle suspension optimization. Understanding the relationship between base excitation characteristics and system response enables engineers to design structures and equipment that perform reliably under dynamic environmental conditions.*
## Formal Definition

**Viscous Damping** is a [[velocity]]-proportional energy dissipation mechanism in dynamic systems where the damping force is linearly proportional to the velocity of motion. Represented mathematically as \( F_d = c\dot{x} \), where \( c \) is the damping coefficient, viscous damping provides a simplified yet effective model for energy dissipation in mechanical, structural, and electrical systems. This linear damping model enables analytical solutions to dynamic equations and serves as the foundation for understanding more complex nonlinear damping phenomena.

## Historical Development

### Key Milestones
- **1687:** Isaac Newton formulates laws of motion, laying groundwork for damping concepts
- **1839:** G. G. Stokes derives Stokes' law for viscous drag on spheres
- **1866:** Lord Rayleigh develops theory of damping in vibrating systems
- **1920s:** Development of the Voigt model for viscoelastic materials
- **1930s:** S. Timoshenko applies viscous damping to structural vibration problems
- **1950s:** R. W. Clough and K. J. Bathe incorporate viscous damping in [[Finite Element Analysis (FEA)]]
- **1970s:** Modal damping models developed for [[Structural Dynamics]]
- **1990s:** Identification methods for damping parameters in large structures
- **2000s:** Experimental validation and refinement of damping models

### Foundational Contributors
1. **Isaac Newton (1643-1727):** Established laws of motion including resistance forces
2. **George Gabriel Stokes (1819-1903):** Developed Stokes' law for viscous drag
3. **Lord Rayleigh (1842-1919):** Formulated [[Rayleigh Damping]] model
4. **Stephen Timoshenko (1878-1972):** Applied damping concepts to engineering structures
5. **Ray W. Clough (1920-2016):** Incorporated damping in finite element methods

## Mathematical Formulation

### General Form

**Equation of motion for SDOF system:**
$$
m\ddot{x}(t) + c\dot{x}(t) + kx(t) = f(t)
$$
where:
- \( m \): mass
- \( c \): viscous damping coefficient
- \( k \): stiffness
- \( x(t) \): displacement
- \( f(t) \): external force

**Damping force:**
$$
F_d(t) = c\dot{x}(t)
$$

### Dimensionless Parameters

**Damping ratio:**
$$
\zeta = \frac{c}{c_c} = \frac{c}{2\sqrt{km}} = \frac{c}{2m\omega_n}
$$
where \( c_c = 2\sqrt{km} = 2m\omega_n \) is critical damping.

**[[Natural Frequency]]:**
$$
\omega_n = \sqrt{\frac{k}{m}}
$$

**Damped natural frequency:**
$$
\omega_d = \omega_n\sqrt{1-\zeta^2}, \quad \zeta < 1
$$

### Matrix Form for MDOF Systems

**For n-degree-of-freedom system:**
$$
M\ddot{\mathbf{x}}(t) + C\dot{\mathbf{x}}(t) + K\mathbf{x}(t) = \mathbf{f}(t)
$$
where \( M, C, K \in \mathbb{R}^{n \times n} \) are mass, damping, and stiffness matrices.

**Proportional (Rayleigh) damping:**
$$
C = \alpha M + \beta K
$$
where \( \alpha, \beta \) are [[Rayleigh Damping]] coefficients.

## Fundamental Principles

### Velocity-Proportional Dissipation

**Energy dissipation rate:** Power dissipated by viscous damping:
$$
P_d(t) = F_d(t)\dot{x}(t) = c[\dot{x}(t)]^2
$$

**Energy dissipated per cycle:** For harmonic motion \( x(t) = X\sin(\omega t) \):
$$
\Delta E = \oint F_d dx = \int_0^{2\pi/\omega} c\dot{x}^2 dt = \pi c\omega X^2
$$

**[[Hysteresis]] loop:** Elliptical force-displacement relationship with area proportional to energy dissipated.

### Critical Damping Concept

**Critical damping coefficient:** \( c_c = 2\sqrt{km} = 2m\omega_n \)
- **Underdamped (\( \zeta < 1 \)):** Oscillatory response, exponential decay
- **Critically damped (\( \zeta = 1 \)):** Fastest non-oscillatory return to equilibrium
- **Overdamped (\( \zeta > 1 \)):** Non-oscillatory, slower return to equilibrium

### Linear Superposition Principle

**For linear viscous damping:** System response to multiple forces is sum of responses to individual forces:
- Enables [[Modal Analysis]] for MDOF systems
- Preserves orthogonality of mode shapes when damping is proportional
- Allows frequency domain analysis via Fourier transforms

## Theoretical Framework

### Analytical Solutions

**Free vibration response:** For underdamped system (\( \zeta < 1 \)) with initial conditions \( x(0) = x_0, \dot{x}(0) = v_0 \):
$$
x(t) = e^{-\zeta\omega_n t}\left(x_0\cos\omega_d t + \frac{v_0 + \zeta\omega_n x_0}{\omega_d}\sin\omega_d t\right)
$$

**Forced harmonic response:** Steady-state response to \( f(t) = F_0\sin(\omega t) \):
$$
x(t) = X\sin(\omega t - \phi)
$$
where:
$$
X = \frac{F_0/k}{\sqrt{(1-r^2)^2 + (2\zeta r)^2}}, \quad r = \frac{\omega}{\omega_n}
$$
$$
\phi = \tan^{-1}\left(\frac{2\zeta r}{1-r^2}\right)
$$

**Frequency response function:**
$$
H(\omega) = \frac{1}{k - m\omega^2 + i c\omega} = \frac{1/k}{1 - r^2 + i 2\zeta r}
$$

### Energy-Based Formulation

**Total mechanical energy:**
$$
E(t) = \frac{1}{2}m\dot{x}^2(t) + \frac{1}{2}kx^2(t)
$$

**Energy dissipation:**
$$
\frac{dE}{dt} = -c\dot{x}^2(t)
$$

**Logarithmic decrement:** For underdamped free vibration:
$$
\delta = \ln\left(\frac{x_n}{x_{n+1}}\right) = \frac{2\pi\zeta}{\sqrt{1-\zeta^2}}
$$
used to experimentally determine \( \zeta \).

### [[Modal Analysis]] Framework

**For proportionally damped MDOF systems:** [[Decoupling]] through modal transformation:
Let \( \mathbf{x}(t) = \Phi\mathbf{q}(t) \), where \( \Phi \) is modal matrix containing mode shapes:
$$
\Phi^T M\Phi = I, \quad \Phi^T K\Phi = \Omega^2 = \text{diag}(\omega_i^2)
$$
For proportional damping \( C = \alpha M + \beta K \):
$$
\Phi^T C\Phi = \text{diag}(2\zeta_i\omega_i)
$$
where modal damping ratios are:
$$
\zeta_i = \frac{\alpha}{2\omega_i} + \frac{\beta\omega_i}{2}
$$

## Classification and Variants

### By Physical Mechanism
1. **Material damping:** Internal friction in materials
2. **Structural damping:** Joint friction, interface slipping
3. **Fluid damping:** Air, water, or oil resistance
4. **Electromagnetic damping:** Eddy currents, magnetic [[Hysteresis]]

### By [[Mathematical Model]]
1. **Linear viscous damping:** Force proportional to velocity
2. **Nonlinear viscous damping:** Force proportional to velocity raised to power n
3. **Coulomb damping:** Constant magnitude friction force
4. **Hysteretic damping:** Complex stiffness model (frequency-dependent)
5. **Fractional derivative damping:** Viscoelastic materials

### By System Configuration
1. **Discrete damping:** Concentrated at specific locations (dashpots)
2. **Distributed damping:** Continuously distributed throughout structure
3. **Interface damping:** At joints, connections, or boundaries
4. **Base isolation damping:** In seismic isolation systems

## Derivation and Proof

### Derivation from First Principles

**[[Newton's second law]]:** For mass with damping and spring forces:
$$
m\ddot{x} = \sum F = -c\dot{x} - kx + f(t)
$$
Rearranging gives standard equation.

**Energy approach:** From work-energy principle:
$$
dW_{\text{non-conservative}} = dE_{\text{kinetic}} + dE_{\text{potential}}
$$
Damping force does negative work: \( dW_{nc} = -c\dot{x} dx = -c\dot{x}^2 dt \)

**[[Variational Principle]]:** Using [[Hamilton's Principle]] with Rayleigh dissipation function:
$$
\mathcal{R} = \frac{1}{2}c\dot{x}^2
$$
Euler-Lagrange equation with dissipation:
$$
\frac{d}{dt}\left(\frac{\partial L}{\partial \dot{x}}\right) - \frac{\partial L}{\partial x} + \frac{\partial \mathcal{R}}{\partial \dot{x}} = 0
$$
where \( L = T - V \) is Lagrangian.

### Solution Derivation

**[[Characteristic equation]]:** Assume solution \( x(t) = Ae^{st} \) for homogeneous equation:
$$
ms^2 + cs + k = 0
$$

**Roots:**
$$
s_{1,2} = -\frac{c}{2m} \pm \sqrt{\left(\frac{c}{2m}\right)^2 - \frac{k}{m}} = -\zeta\omega_n \pm \omega_n\sqrt{\zeta^2 - 1}
$$

**For underdamped case (\( \zeta < 1 \)):**
$$
s_{1,2} = -\zeta\omega_n \pm i\omega_n\sqrt{1-\zeta^2} = -\zeta\omega_n \pm i\omega_d
$$
giving oscillatory solution with exponential decay.

### Proportional Damping Derivation

**Rayleigh's hypothesis:** Damping matrix linearly combines mass and stiffness matrices:
$$
C = \alpha M + \beta K
$$

**Modal transformation:** Pre- and post-multiply by \( \Phi^T \) and \( \Phi \):
$$
\Phi^T C\Phi = \alpha\Phi^T M\Phi + \beta\Phi^T K\Phi = \alpha I + \beta\Omega^2
$$
Thus modal damping matrix is diagonal with elements:
$$
2\zeta_i\omega_i = \alpha + \beta\omega_i^2
$$

## Physical Interpretation

### Mechanical Analogy

**Dashpot model:** Consists of piston moving through viscous fluid:
- Force proportional to velocity: \( F = c v \)
- Energy dissipated as [[heat]] in fluid
- Analogous to electrical resistor: \( V = R I \)

**Spring-damper systems:** Parallel or series combinations:
- **Kelvin-Voigt:** Spring and damper in parallel
- **Maxwell:** Spring and damper in series
- **Standard linear solid:** More complex combinations

### Energy Dissipation Visualization

**[[Hysteresis]] loops:** For harmonic excitation, plot force vs. displacement:
- Elliptical loop for linear viscous damping
- Area inside loop = energy dissipated per cycle
- Slope of major axis = stiffness
- Width proportional to damping coefficient

**Phase relationships:**
- Displacement lags force by phase angle \( \phi \)
- Velocity in phase with damping force
- [[Acceleration]] leads velocity by 90°

### Wave Propagation Interpretation

**For continuous systems:** Viscous damping causes amplitude attenuation:
$$
u(x,t) = Ae^{-\alpha x}\cos(\omega t - kx)
$$
where attenuation coefficient \( \alpha \) depends on damping.

**Quality factor Q:**
$$
Q = \frac{\omega_n}{\Delta\omega} \approx \frac{1}{2\zeta}
$$
where \( \Delta\omega \) is bandwidth at half-power points.

## Applications

### Engineering Disciplines
1. **Structural Engineering:** Earthquake-resistant design, vibration control
2. **Mechanical Engineering:** Vehicle suspension systems, machinery isolation
3. **Aerospace Engineering:** Aircraft landing gear, satellite [[attitude control]]
4. **Civil Engineering:** Bridge damping, tall building sway control
5. **Automotive Engineering:** Shock absorbers, engine mounts

### Vibration Control Systems
1. **Tuned mass dampers:** For tall buildings and bridges
2. **Base isolation systems:** For seismic protection
3. **Active vibration control:** With feedback and actuators
4. **Semi-active dampers:** Magnetorheological, electrorheological
5. **Passive damping treatments:** Constrained layer damping, viscoelastic materials

### Measurement and Testing
1. **Modal testing:** Experimental determination of damping ratios
2. **Shock testing:** Qualification of equipment for transportation
3. **Fatigue testing:** Simulating service loads with damping
4. **Seismic testing:** On shake tables for earthquake simulation

## Implementation Considerations

### Damping Coefficient Estimation

**Experimental methods:**
1. **Logarithmic decrement:** From free vibration decay
2. **Bandwidth method:** From frequency response function
3. **Half-power points:** From [[Resonance]] peak width
4. **Circle fit method:** From [[Nyquist plot]] of FRF
5. **Time domain methods:** System identification techniques

**Empirical values for common materials:**
- Steel structures: \( \zeta = 0.01 - 0.02 \)
- Reinforced concrete: \( \zeta = 0.03 - 0.05 \)
- Wood structures: \( \zeta = 0.03 - 0.05 \)
- Rubber isolators: \( \zeta = 0.05 - 0.20 \)
- Viscoelastic materials: \( \zeta = 0.10 - 0.30 \)

### Finite Element Implementation

**[[Rayleigh Damping]] in FE codes:**
```
! ANSYS example
ALPHAD, 0.1    ! Mass damping coefficient
BETAD, 0.001   ! Stiffness damping coefficient

! ABAQUS example
*DAMPING, RAYLEIGH
0.1, 0.001
```

**Modal damping in FE analysis:**
- Specify damping ratio for each mode
- Often frequency-dependent: \( \zeta_i = \zeta(\omega_i) \)
- Can include material-dependent damping

### Numerical Time Integration

**Newmark-β method for damped systems:** Update equations:
$$
\dot{x}_{n+1} = \dot{x}_n + [(1-\gamma)\ddot{x}_n + \gamma\ddot{x}_{n+1}]\Delta t
$$
$$
x_{n+1} = x_n + \dot{x}_n\Delta t + \left[\left(\frac{1}{2}-\beta\right)\ddot{x}_n + \beta\ddot{x}_{n+1}\right]\Delta t^2
$$

**For unconditional stability:** \( \gamma \geq \frac{1}{2}, \beta \geq \frac{1}{4}(\gamma+\frac{1}{2})^2 \)

**Effective stiffness for implicit integration:** 
$$
K^* = K + \frac{\gamma}{\beta\Delta t}C + \frac{1}{\beta\Delta t^2}M
$$

## Advantages and Limitations

### Strengths
1. **Mathematical simplicity:** Linear model enables analytical solutions
2. **Physical basis:** Reasonable approximation for many fluid-based damping mechanisms
3. **Modal [[Decoupling]]:** With proportional damping, enables efficient MDOF analysis
4. **Frequency independence:** Constant damping coefficient (unlike hysteretic damping)
5. **Experimental determination:** Easy to estimate from vibration tests

### Weaknesses
1. **Oversimplification:** Real damping often nonlinear and frequency-dependent
2. **Energy overestimation:** At high velocities, damping may saturate
3. **Temperature dependence:** Viscosity changes with temperature affect damping
4. **Amplitude dependence:** Real structural damping often amplitude-dependent
5. **Modal coupling:** Non-proportional damping couples modal equations

### Validity Range
- **Accurate for:** Low velocities, small amplitudes, fluid-dominated damping
- **Reasonable approximation for:** Structural damping in small vibration regime
- **Poor for:** Large amplitudes, impact loading, high-frequency vibration
- **Breakdown:** When damping force exceeds material limits or when nonlinear effects dominate

## Advanced Topics

### Non-proportional Damping

**When \( C \neq \alpha M + \beta K \):** Modal transformation doesn't diagonalize \( C \):
$$
\Phi^T C\Phi \text{ is not diagonal}
$$

**State-space formulation:** Transform second-order system to first-order:
$$
\begin{bmatrix} \dot{\mathbf{x}} \\ \ddot{\mathbf{x}} \end{bmatrix} = 
\begin{bmatrix} 0 & I \\ -M^{-1}K & -M^{-1}C \end{bmatrix}
\begin{bmatrix} \mathbf{x} \\ \dot{\mathbf{x}} \end{bmatrix} +
\begin{bmatrix} 0 \\ M^{-1} \end{bmatrix} \mathbf{f}(t)
$$

**Complex modes:** Result from non-proportional damping:
- Mode shapes are complex-valued (not just real)
- Different phase relationships between points
- More difficult to interpret physically

### Viscoelastic Damping Models

**Frequency-dependent complex modulus:** 
$$
E^*(\omega) = E'(\omega) + iE''(\omega) = E(\omega)[1 + i\eta(\omega)]
$$
where \( \eta(\omega) \) is loss factor.

**Fractional derivative models:** For materials with memory:
$$
\sigma(t) = E_0\epsilon(t) + E_1\frac{d^\alpha\epsilon(t)}{dt^\alpha}, \quad 0 < \alpha < 1
$$

**Generalized Maxwell model:** Series of spring-dashpot elements for broad frequency range.

### Stochastic Damping

**[[Random Vibration]] analysis:** For systems with random excitation:
- Damping affects mean square response
- Important for wind, earthquake, and road excitation
- Can use equivalent linearization for nonlinear damping

**Probabilistic damping models:** Treat damping as random variable or process:
- Accounts for uncertainty in damping estimates
- Important for reliability analysis

### Smart Damping Technologies

**Magnetorheological (MR) dampers:** Fluid viscosity controlled by magnetic field:
- Semi-active control
- Fast response time
- Used in automotive suspensions, building damping systems

**Electrorheological (ER) dampers:** Similar but controlled by electric field

**Shape memory alloys:** For adaptive damping systems

## Special Cases and Examples

### Vehicle Suspension System

**Quarter-car model:** Two-degree-of-freedom system:
- Sprung mass (car body) and unsprung mass (wheel assembly)
- Spring and damper between masses
- Tire modeled as spring
- Optimal damping for ride comfort vs. road holding

**Optimal damping ratio:** Typically \( \zeta \approx 0.2 - 0.3 \) for passenger cars

### Building with Tuned Mass Damper

**Taipei 101 example:**
- 730-ton tuned mass damper at top
- Damping reduces sway by 30-40%
- Viscous damping in damper mechanism
- [[Natural Frequency]] tuned to building's fundamental frequency

### Seismic Base Isolation

**Lead-rubber bearings:** Combine stiffness and damping:
- Rubber provides flexibility
- Lead plug provides hysteretic damping
- Equivalent viscous damping ratio: \( \zeta_{eq} \approx 0.10 - 0.15 \)

### Experimental Determination Example

**Cantilever beam test:**
- Steel beam: \( L = 1\,\text{m}, b = 0.05\,\text{m}, h = 0.005\,\text{m} \)
- Free vibration test: Initial displacement released
- Measure amplitudes: \( X_1 = 10.0\,\text{mm}, X_2 = 8.1\,\text{mm}, X_3 = 6.6\,\text{mm} \)
- Logarithmic decrement: \( \delta = \frac{1}{2}\ln(10.0/6.6) = 0.21 \)
- Damping ratio: \( \zeta = \frac{\delta}{\sqrt{4\pi^2 + \delta^2}} = 0.033 \)

## Error Analysis

### Measurement Uncertainties

**Logarithmic decrement method:**
- Relative error in \( \zeta \): \( \frac{\Delta\zeta}{\zeta} \approx \frac{\Delta\delta}{\delta} \)
- Amplitude measurement errors propagate
- Better to use multiple cycles: \( \delta = \frac{1}{n}\ln\left(\frac{X_1}{X_{n+1}}\right) \)

**Frequency response method:**
- Half-power point uncertainty
- Noise in FRF measurement
- Curve fitting errors

### Modeling Errors

**Proportional damping assumption:** Error when damping distribution differs from mass/stiffness:
- Modal coupling terms neglected
- Can over- or under-predict response
- Error increases with damping non-proportionality

**Linearization error:** For nonlinear damping modeled as equivalent viscous damping:
- Equivalent damping depends on amplitude
- Error increases with excitation level
- May not capture transient behavior correctly

### Numerical Errors

**Time integration:** Amplitude decay and period elongation errors:
- [[Newmark Method]]: numerical damping present even for \( \gamma > 0.5 \)
- Can artificially increase or decrease damping
- Time step selection critical: \( \Delta t < T/10 \) for accuracy

**Modal truncation:** For MDOF systems with damping:
- Higher modes may contribute to damping
- Truncation affects damping representation
- Residual flexibility methods can help

## Relationship to Other Concepts

### Comparison with Hysteretic Damping

**Viscous damping:**
- Force proportional to velocity
- Energy dissipated per cycle proportional to frequency: \( \Delta E \propto \omega \)
- Constant damping coefficient \( c \)

**Hysteretic (structural) damping:**
- Force in phase with velocity but proportional to displacement
- Energy dissipated per cycle independent of frequency
- Complex stiffness model: \( k^* = k(1 + i\eta) \)

**Equivalence:** At [[Resonance]] (\( \omega = \omega_n \)), equivalent viscous damping:
$$
c_{eq} = \frac{\eta k}{\omega_n}
$$

### Connection to Electrical Circuits

**Mechanical-electrical analogy:**
- Mass \( m \) ↔ Inductance \( L \)
- Spring \( k \) ↔ Capacitance \( 1/C \)
- Damper \( c \) ↔ Resistance \( R \)
- Force \( F \) ↔ Voltage \( V \)
- Velocity \( \dot{x} \) ↔ Current \( I \)

**RLC circuit equation:**
$$
L\ddot{q} + R\dot{q} + \frac{1}{C}q = V(t)
$$
identical to mechanical SDOF equation.

### Relationship to Aerodynamic Damping

**Fluid-structure interaction:** Damping from fluid motion:
- Linear for small velocities
- Becomes quadratic (Morison equation) at higher velocities
- Can be negative (flutter instability) in certain conditions

**Wind-induced damping:** For tall buildings:
- Positive damping for along-wind motion
- Can be negative for across-wind motion at certain wind speeds

## Historical Context and Evolution

### Original Motivation

**Industrial revolution:** Need to understand and control vibrations in machinery
**Early observations:** Frictional damping in clock pendulums, building vibrations
**Mathematical formulation:** Stokes (fluid resistance), Rayleigh (vibrating systems)

### Evolution Over Time

1. **Pre-1900:** Empirical observations, simple models
2. **1900-1950:** Development of linear vibration theory, experimental methods
3. **1950-1970:** Finite element methods, [[Modal Analysis]], digital computation
4. **1970-1990:** System identification, active control, seismic applications
5. **1990-2010:** Smart materials, health monitoring, uncertainty quantification
6. **2010-present:** Multi-physics simulations, data-driven models, digital twins

### Modern Perspectives

**From empirical to predictive:** Physics-based models combined with data
**Multi-scale damping:** From material microstructure to full structure
**Resilience-based design:** Damping for extreme events (earthquakes, winds)
**Sustainable damping:** Recyclable materials, energy harvesting

## Pedagogical Approach

### Teaching Strategies

1. **Physical demonstrations:** Spring-mass-damper systems, pendulum with dashpot
2. **Mathematical derivation:** From Newton's laws to [[characteristic equation]]
3. **Experimental measurements:** Free vibration decay, frequency response
4. **Computer simulations:** MATLAB/Simulink models, finite element software
5. **Real-world examples:** Car suspension, building sway, earthquake isolation

### Common Misconceptions

1. **"Damping always reduces vibration":** Can amplify response at certain frequencies
2. **"Higher damping is always better":** Optimal damping exists for specific objectives
3. **"Viscous damping model is always accurate":** Many real damping mechanisms are nonlinear
4. **"Damping ratio is constant":** Often depends on amplitude, frequency, temperature
5. **"Critical damping is ideal":** Often slower than slightly underdamped response

### Learning Resources

**Foundational Texts:**
- Thomson & Dahleh, "Theory of Vibration with Applications"
- Inman, "Engineering Vibration"
- Clough & Penzien, "Dynamics of Structures"
- Meirovitch, "Fundamentals of Vibration"

**Online Resources:**
- MIT OpenCourseWare: 2.003 Engineering Dynamics
- Wolfram Demonstrations: Damped Vibrations
- YouTube: Demonstrations of damping effects
- Simulation apps: PhET Interactive Simulations

**Software Tutorials:**
- MATLAB: ode45 for damped systems, System Identification Toolbox
- ANSYS/ABAQUS: Damping in transient dynamics
- Python: SciPy signal processing, [[vibration analysis]] libraries

## Implementation in Software

### MATLAB Implementation

```matlab
% SDOF viscous damping analysis
function viscous_damping_example()
    % Parameters
    m = 100;        % kg
    k = 10000;      % N/m
    zeta = 0.05;    % damping ratio
    c = 2*zeta*sqrt(m*k); % damping coefficient
    
    % Natural frequency
    wn = sqrt(k/m);
    wd = wn*sqrt(1-zeta^2);
    
    % Time [[vector]]
    t = 0:0.001:10;
    
    % Free vibration with initial conditions
    x0 = 0.1;       % initial displacement (m)
    v0 = 0;         % initial velocity (m/s)
    
    % Free response
    x_free = exp(-zeta*wn*t).*(x0*cos(wd*t) + (v0+zeta*wn*x0)/wd*sin(wd*t));
    
    % Forced harmonic response
    F0 = 100;       % Force amplitude (N)
    w = 0:0.1:50;   % Frequency range (rad/s)
    
    % Frequency response
    H = 1./(k - m*w.^2 + 1i*c*w);
    X = abs(H)*F0;
    phase = angle(H);
    
    % Plot results
    figure;
    subplot(2,2,1);
    plot(t, x_free);
    xlabel('Time (s)'); ylabel('Displacement (m)');
    title('Free Vibration Response');
    grid on;
    
    subplot(2,2,2);
    plot(w, X);
    xlabel('Frequency (rad/s)'); ylabel('Amplitude (m)');
    title('Frequency Response');
    grid on;
    
    subplot(2,2,3);
    plot(w, phase*180/pi);
    xlabel('Frequency (rad/s)'); ylabel('Phase (deg)');
    title('Phase Response');
    grid on;
    
    % Time response to harmonic force at resonance
    w_force = wn;   % excitation at natural frequency
    t_forced = 0:0.001:20;
    x_forced = (F0/(k*sqrt((1-(w_force/wn)^2)^2 + (2*zeta*w_force/wn)^2))) * ...
               sin(w_force*t_forced - atan2(2*zeta*w_force/wn, 1-(w_force/wn)^2));
    
    subplot(2,2,4);
    plot(t_forced, x_forced);
    xlabel('Time (s)'); ylabel('Displacement (m)');
    title('Forced Response at Resonance');
    grid on;
end

% MDOF with [[[[Rayleigh damping]]]]
function [freq, damp_ratios, mode_shapes] = mdof_rayleigh_damping(M, K, alpha, beta)
    % Solve undamped [[eigenvalue problem]]
    [V, D] = eig(K, M);
    wn = sqrt(diag(D));  % natural frequencies
    freq = wn/(2*pi);    % Hz
    
    % [[Rayleigh damping]] matrix
    C = alpha*M + beta*K;
    
    % Modal damping ratios
    damp_ratios = (alpha./(2*wn) + beta*wn/2);
    
    % Mode shapes
    mode_shapes = V;
    
    % Normalize mode shapes (mass normalization)
    for i = 1:size(V,2)
        mode_shapes(:,i) = V(:,i)/sqrt(V(:,i)'*M*V(:,i));
    end
end
```

### Python Implementation

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal
from scipy.linalg import eig

class ViscousDampedSystem:
    """Class for analyzing viscous damped systems"""
    
    def __init__(self, m, c, k):
        """
        Initialize SDOF system
        
        Parameters
        ----------
        m : float
            Mass (kg)
        c : float
            Damping coefficient (N·s/m)
        k : float
            Stiffness (N/m)
        """
        self.m = m
        self.c = c
        self.k = k
        
        # Compute derived properties
        self.wn = np.sqrt(k/m)  # Natural frequency (rad/s)
        self.cc = 2*np.sqrt(m*k)  # Critical damping
        self.zeta = c/self.cc  # Damping ratio
        
        if self.zeta < 1:
            self.wd = self.wn*np.sqrt(1 - self.zeta**2)  # Damped frequency
        else:
            self.wd = 0
    
    def free_response(self, x0, v0, t):
        """
        Compute free vibration response
        
        Parameters
        ----------
        x0 : float
            Initial displacement (m)
        v0 : float
            Initial velocity (m/s)
        t : array
            Time [[vector]] (s)
            
        Returns
        -------
        x : array
            Displacement response
        """
        if self.zeta < 1:  # Underdamped
            A = np.sqrt(x0**2 + ((v0 + self.zeta*self.wn*x0)/self.wd)**2)
            phi = np.arctan2(x0*self.wd, v0 + self.zeta*self.wn*x0)
            x = A*np.exp(-self.zeta*self.wn*t)*np.sin(self.wd*t + phi)
        elif self.zeta == 1:  # Critically damped
            x = np.exp(-self.wn*t)*(x0 + (v0 + self.wn*x0)*t)
        else:  # Overdamped
            s1 = -self.zeta*self.wn + self.wn*np.sqrt(self.zeta**2 - 1)
            s2 = -self.zeta*self.wn - self.wn*np.sqrt(self.zeta**2 - 1)
            A1 = (v0 - s2*x0)/(s1 - s2)
            A2 = (s1*x0 - v0)/(s1 - s2)
            x = A1*np.exp(s1*t) + A2*np.exp(s2*t)
        
        return x
    
    def frequency_response(self, omega):
        """
        Compute frequency response function
        
        Parameters
        ----------
        omega : array
            Frequency vector (rad/s)
            
        Returns
        -------
        H : array
            Complex frequency response
        """
        H = 1/(self.k - self.m*omega**2 + 1j*self.c*omega)
        return H
    
    def forced_response(self, F, t, method='analytical'):
        """
        Compute response to arbitrary force
        
        Parameters
        ----------
        F : array or callable
            Force [[vector]] or function F(t)
        t : array
            Time [[vector]]
        method : str
            'analytical' for analytical solution to simple forces
            'numerical' for numerical integration
            
        Returns
        -------
        x : array
            Displacement response
        """
        if method == 'analytical' and callable(F):
            # Use Duhamel's integral for arbitrary force
            dt = t[1] - t[0]
            x = np.zeros_like(t)
            
            # Impulse response function
            h = lambda tau: (1/(self.m*self.wd))*np.exp(-self.zeta*self.wn*tau)*np.sin(self.wd*tau)
            
            # Convolution
            for i, ti in enumerate(t):
                # Numerically integrate convolution integral
                tau_vals = np.linspace(0, ti, 100)
                integrand = F(ti - tau_vals) * h(tau_vals)
                x[i] = np.trapz(integrand, tau_vals)
        else:
            # Use numerical integration (state-space)
            A = np.array([[0, 1], [-self.k/self.m, -self.c/self.m]])
            B = np.array([[0], [1/self.m]])
            
            # State-space simulation
            from scipy.integrate import odeint
            
            def state_eq(x_state, t_curr):
                if callable(F):
                    force = F(t_curr)
                else:
                    # Interpolate force
                    force = np.interp(t_curr, t, F)
                return A @ x_state + B.flatten() * force
            
            x0_state = np.array([0, 0])  # Initial state [displacement, velocity]
            x_state = odeint(state_eq, x0_state, t)
            x = x_state[:, 0]
        
        return x

# Example usage
if __name__ == "__main__":
    # Create damped system
    sys = ViscousDampedSystem(m=100, c=200, k=10000)
    
    print(f"Natural frequency: {sys.wn:.2f} rad/s")
    print(f"Damping ratio: {sys.zeta:.3f}")
    print(f"Damped frequency: {sys.wd:.2f} rad/s")
    
    # Free response
    t = np.linspace(0, 10, 1000)
    x_free = sys.free_response(x0=0.1, v0=0, t=t)
    
    # Frequency response
    omega = np.linspace(0, 50, 500)
    H = sys.frequency_response(omega)
    
    # Forced harmonic response at [[resonance]]
    F_resonance = lambda t: 100*np.sin(sys.wn*t)
    x_forced = sys.forced_response(F_resonance, t, method='numerical')
    
    # Plot
    fig, axes = plt.subplots(2, 2, figsize=(10, 8))
    
    axes[0,0].plot(t, x_free)
    axes[0,0].set_xlabel('Time (s)')
    axes[0,0].set_ylabel('Displacement (m)')
    axes[0,0].set_title('Free Vibration Response')
    axes[0,0].grid(True)
    
    axes[0,1].plot(omega, np.abs(H))
    axes[0,1].set_xlabel('Frequency (rad/s)')
    axes[0,1].set_ylabel('|H(ω)| (m/N)')
    axes[0,1].set_title('Frequency Response Magnitude')
    axes[0,1].grid(True)
    
    axes[1,0].plot(omega, np.angle(H))
    axes[1,0].set_xlabel('Frequency (rad/s)')
    axes[1,0].set_ylabel('Phase (rad)')
    axes[1,0].set_title('Frequency Response Phase')
    axes[1,0].grid(True)
    
    axes[1,1].plot(t, x_forced)
    axes[1,1].set_xlabel('Time (s)')
    axes[1,1].set_ylabel('Displacement (m)')
    axes[1,1].set_title('Forced Response at Resonance')
    axes[1,1].grid(True)
    
    plt.tight_layout()
    plt.show()
```

### Commercial Software Features

**ANSYS Mechanical:**
- [[Rayleigh Damping]]: ALPHAD, BETAD commands
- Modal damping: DMPRAT command
- Frequency-dependent damping: via material properties
- Nonlinear damping: COMBIN14 damper element

**ABAQUS:**
- *DAMPING option for [[Rayleigh Damping]]
- Material damping: *MATERIAL, DAMPING
- Discrete dampers: DASHPOT elements
- Complex eigenvalue analysis for damped systems

**NASTRAN:**
- PARAM,G - global structural damping coefficient
- PARAM,W3 - frequency for stiffness damping
- CDAMPi, CVISC elements for discrete dampers
- Complex eigenvalue methods for flutter analysis

**MATLAB/Simulink:**
- [[Transfer Function]] models with damping
- System Identification Toolbox for damping estimation
- Control System Toolbox for damping design
- Simscape for physical modeling of damped systems

## See Also

- Structural Damping
- [[Hysteretic Damping]]
- [[Rayleigh Damping]]
- [[Modal Damping]]
- [[Critical Damping]]
- [[Damping Ratio]]
- Logarithmic Decrement
- [[Vibration Isolation]]
- Energy Dissipation
- Seismic Damping
- Tuned Mass Damper
- [[Viscoelastic Material]]
- [[Base Isolation]]
- [[Finite Element Analysis (FEA)]]
- [[Structural Dynamics]]

---

*Note: Viscous damping provides a fundamental and mathematically tractable model for energy dissipation in dynamic systems. While real-world damping mechanisms are often more complex, the viscous damping model serves as an essential building block for [[vibration analysis]], structural design, and control system development across engineering disciplines.*
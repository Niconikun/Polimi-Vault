## Formal Definition

**Transmissibility** is a dimensionless ratio that quantifies the transmission of motion or force across a system, particularly in vibration isolation contexts. It represents the ratio of the response amplitude ([[displacement]], velocity, or [[acceleration]]) of an [[isolated system]] to the input excitation amplitude when subjected to harmonic base motion. Transmissibility characterizes the effectiveness of vibration isolation systems, indicating whether vibration is amplified or attenuated across different frequency ranges. The concept is fundamental to the design of mechanical isolators, seismic protection systems, and noise control solutions.

## Historical Development

### Key Milestones
- **1900s:** Early studies of vibration isolation for machinery mounting
- **1930s:** Development of analytical methods for transmissibility in linear systems
- **1940s:** J.P. Den Hartog formalizes transmissibility theory in mechanical vibrations
- **1950s:** Application to aircraft and vehicle suspension design
- **1960s:** Extension to [[Random Vibration]] and seismic isolation
- **1980s:** Development of active and semi-active isolation with variable transmissibility

### Foundational Contributors
1. **J.P. Den Hartog (1901-1989):** Systematized transmissibility theory in vibration isolation
2. **R.E.D. Bishop (1925-2019):** Advanced understanding of vibration transmission in structures
3. **C.M. Harris (1917-2011):** Compiled comprehensive vibration isolation data and methods
4. **S. Timoshenko (1878-1972):** Contributed to foundation of [[Structural Dynamics]] theory

## Mathematical Formulation

### Basic Definition

For a single-degree-of-freedom system subjected to harmonic base excitation $y(t) = Y e^{i\omega t}$, the transmissibility $T$ is defined as:

**Displacement transmissibility:**
$$
T_d = \left|\frac{X}{Y}\right|
$$

**Force transmissibility** (for force excitation cases):
$$
T_f = \left|\frac{F_T}{F_0}\right|
$$

where:
- $X$ = amplitude of mass absolute displacement response
- $Y$ = amplitude of base displacement excitation
- $F_T$ = amplitude of force transmitted to foundation
- $F_0$ = amplitude of excitation force applied to mass

### Standard Transmissibility Formula

For a viscously damped SDOF system:
$$
T = \sqrt{\frac{1 + (2\zeta r)^2}{(1 - r^2)^2 + (2\zeta r)^2}}
$$

where:
- $r = \omega/\omega_n$ = frequency ratio
- $\omega$ = excitation frequency
- $\omega_n = \sqrt{k/m}$ = undamped [[Natural Frequency]]
- $\zeta = c/(2m\omega_n)$ = damping ratio

### Alternative Forms

**Velocity transmissibility:**
$$
T_v = \left|\frac{\dot{X}}{\dot{Y}}\right| = T_d
$$
(same magnitude for harmonic motion)

**Acceleration transmissibility:**
$$
T_a = \left|\frac{\ddot{X}}{\ddot{Y}}\right| = T_d
$$

**Transmitted force for base excitation:**
$$
F_T = kY \cdot T
$$

## Fundamental Principles

### Frequency Regions

**Three distinct regions:**
1. **Quasi-static region ($r \ll 1$):**
   - $T \approx 1$
   - System follows base motion exactly
   - No isolation, no amplification

2. **[[Resonance]] region ($r \approx 1$):**
   - $T$ reaches maximum value
   - Amplification occurs, especially for low damping
   - Maximum amplification: $T_{\max} \approx \frac{1}{2\zeta}$ for $\zeta \ll 1$

3. **Isolation region ($r > \sqrt{2}$):**
   - $T < 1$, vibration isolation achieved
   - Higher $r$ gives better isolation
   - Damping reduces isolation effectiveness in this region

### Critical Frequencies

**Resonant frequency:** Where $T$ is maximum:
$$
r_{\text{max}} = \sqrt{\frac{\sqrt{1+8\zeta^2} - 1}{2\zeta^2}} \approx 1 \text{ for small } \zeta
$$

**Isolation threshold:** Where $T = 1$:
$$
r_{\text{iso}} = \sqrt{2}
$$

**Zero transmissibility frequency:** Where transmitted force is zero (for specific systems):
$$
r_{\text{zero}} = \sqrt{2} \text{ for force excitation with specific configurations}
$$

### Damping Effects

**Contradictory roles of damping:**
1. **Beneficial at [[Resonance]]:** Reduces amplification peak
2. **Detrimental in isolation region:** Increases transmissibility
3. **Optimal damping:** Compromise between [[Resonance]] control and isolation performance

## Theoretical Framework

### Derivation from Equations of Motion

For base excitation $y(t) = Y\cos(\omega t)$:
$$
m\ddot{x} + c(\dot{x} - \dot{y}) + k(x - y) = 0
$$

Assume steady-state solution $x(t) = X\cos(\omega t - \phi)$. Substitute and solve for complex amplitude ratio:
$$
\frac{X}{Y} = \frac{1 + i2\zeta r}{1 - r^2 + i2\zeta r}
$$

Taking magnitude gives transmissibility formula.

### Force Transmissibility Derivation

For force excitation $F(t) = F_0\cos(\omega t)$ applied to mass:
$$
m\ddot{x} + c\dot{x} + kx = F_0\cos(\omega t)
$$

Force transmitted to foundation: $F_T = c\dot{x} + kx$

Solving yields same transmissibility expression: $T_f = \sqrt{\frac{1+(2\zeta r)^2}{(1-r^2)^2+(2\zeta r)^2}}$

### Generalized Transmissibility

For MDOF systems, transmissibility can be defined between any two points $i$ and $j$:
$$
T_{ij} = \left|\frac{X_i}{X_j}\right|
$$

**Modal transmissibility:** For mode $k$:
$$
T_{ij}^{(k)} = \left|\frac{\phi_{ik}}{\phi_{jk}}\right|
$$

## Classification and Variants

### By Physical Quantity
1. **Displacement transmissibility:** Most common, for vibration isolation
2. **Force transmissibility:** For force isolation (machinery mounts)
3. **Velocity transmissibility:** Used in some acoustic applications
4. **Acceleration transmissibility:** For shock and high-frequency vibration

### By System Type
1. **Linear transmissibility:** Classical theory for linear systems
2. **Nonlinear transmissibility:** For systems with nonlinear stiffness/damping
3. **Active system transmissibility:** With control forces applied
4. **Coupled system transmissibility:** For multiple interconnected systems

### By Application Context
1. **Vibration isolation transmissibility:** For machinery and equipment isolation
2. **Seismic transmissibility:** For earthquake engineering and base isolation
3. **Acoustic transmissibility:** For sound transmission through structures
4. **Thermal transmissibility:** For heat transfer analogy (less common)

## Derivation and Proof

### Step-by-Step Derivation for Base Excitation

**Step 1: Establish equations of motion**
For SDOF system with base motion $y(t)$:
$$
m\ddot{x} + c(\dot{x} - \dot{y}) + k(x - y) = 0
$$

**Step 2: Assume harmonic solutions**
Let $y(t) = Ye^{i\omega t}$ and $x(t) = Xe^{i\omega t}$

**Step 3: Substitute into equation**
$$
(-m\omega^2 X + i\omega c X + kX) e^{i\omega t} = (i\omega c Y + kY) e^{i\omega t}
$$

**Step 4: Solve for amplitude ratio**
$$
X(-m\omega^2 + i\omega c + k) = Y(i\omega c + k)
$$
$$
\frac{X}{Y} = \frac{i\omega c + k}{-m\omega^2 + i\omega c + k}
$$

**Step 5: Express in terms of dimensionless parameters**
Divide numerator and denominator by $k$:
$$
\frac{X}{Y} = \frac{1 + i2\zeta r}{1 - r^2 + i2\zeta r}
$$
where $r = \omega/\omega_n$, $\omega_n = \sqrt{k/m}$, $\zeta = c/(2m\omega_n)$

**Step 6: Compute magnitude**
$$
T = \left|\frac{X}{Y}\right| = \sqrt{\frac{(1)^2 + (2\zeta r)^2}{(1 - r^2)^2 + (2\zeta r)^2}}
$$

### Force Transmissibility Proof

**Step 1: Force excitation equation**
$$
m\ddot{x} + c\dot{x} + kx = F_0 e^{i\omega t}
$$

**Step 2: Assume solution** $x(t) = Xe^{i\omega t}$

**Step 3: Solve for response**
$$
X = \frac{F_0}{-m\omega^2 + i\omega c + k}
$$

**Step 4: Transmitted force**
$$
F_T = kx + c\dot{x} = (k + i\omega c)Xe^{i\omega t}
$$

**Step 5: Transmissibility ratio**
$$
T_f = \left|\frac{F_T}{F_0}\right| = \left|\frac{k + i\omega c}{-m\omega^2 + i\omega c + k}\right|
= \sqrt{\frac{1 + (2\zeta r)^2}{(1 - r^2)^2 + (2\zeta r)^2}}
$$

### Energy Method Derivation

Using power flow approach:
$$
T^2 = \frac{\text{Power transmitted}}{\text{Power input}} = \frac{\frac{1}{2}c\omega^2 X^2 + \frac{1}{2}k\omega X^2 \cdot \text{Re}\{H\}}{\frac{1}{2}F_0^2 \cdot \text{Re}\{1/Z\}}
$$
Yields same expression for linear systems.

## Physical Interpretation

### Vibration Isolation Mechanism

**Isolation principle:** Insert compliant element between vibration source and receiver:
- **Source:** Vibrating machinery or base motion
- **Isolator:** Spring-damper system
- **Receiver:** Foundation, structure, or sensitive equipment

**Isolation effectiveness:**
$$
\text{Isolation \%} = (1 - T) \times 100\% \quad \text{for } T < 1
$$

### Amplification vs. Attenuation

**Critical frequency ratio:**
- **Below $\sqrt{2}$:** Amplification ($T > 1$)
- **At $\sqrt{2}$:** Unity transmissibility ($T = 1$)
- **Above $\sqrt{2}$:** Attenuation ($T < 1$)

**Practical implication:** Isolators must be designed so that operating frequency $\omega > \sqrt{2} \omega_n$

### Phase Relationships

**Phase angle between response and excitation:**
$$
\phi = \tan^{-1}\left(\frac{2\zeta r^3}{1 - r^2 + (2\zeta r)^2}\right)
$$

**Important transitions:**
- $r \ll 1$: $\phi \approx 0°$ (in-phase)
- $r = 1$: $\phi = 90°$
- $r \gg 1$: $\phi \approx 180°$ (out-of-phase)

### Transmissibility Curves

**Characteristics:**
1. **Low-frequency asymptote:** $T \rightarrow 1$ as $r \rightarrow 0$
2. **[[Resonance]] peak:** Height controlled by damping
3. **High-frequency asymptote:** $T \rightarrow \frac{2\zeta}{r}$ as $r \rightarrow \infty$ (for displacement transmissibility)
4. **Isolation region slope:** Approximately -20 dB/decade for displacement

## Applications

### Engineering Disciplines
1. **Mechanical Engineering:** Machinery vibration isolation, engine mounts
2. **Civil Engineering:** Seismic base isolation, building vibration control
3. **Aerospace Engineering:** Aircraft engine mounts, satellite launch isolation
4. **Automotive Engineering:** Vehicle suspension design, cabin noise reduction
5. **Electrical Engineering:** Precision equipment isolation, clean room facilities

### Scientific Fields
1. **Acoustics:** Noise control through vibration isolation
2. **Geophysics:** Earthquake engineering and seismic protection
3. **Biomechanics:** Vibration isolation for sensitive medical equipment
4. **Materials Science:** Vibration isolation for precision manufacturing

### Practical Implementations
- **Machine mounts:** Rubber, spring, or air isolators for industrial equipment
- **Seismic isolators:** Lead-rubber bearings, friction pendulum systems for buildings
- **Vehicle suspensions:** Spring-damper systems for ride comfort
- **Optical tables:** Active and passive isolation for sensitive instruments
- **Building isolation:** For protection against traffic or construction vibration

## Implementation Considerations

### Design Procedure

**Step 1: Determine requirements**
- Operating frequency range $\omega_{\min}$ to $\omega_{\max}$
- Required isolation level (target $T$)
- Allowable static deflection $\delta_{st} = mg/k$

**Step 2: Calculate required natural frequency**
From $T = \sqrt{\frac{1+(2\zeta r)^2}{(1-r^2)^2+(2\zeta r)^2}}$, solve for $\omega_n$:
$$
\omega_n \approx \frac{\omega}{\sqrt{1 + 1/T}} \quad \text{for } r \gg 1 \text{ and small } \zeta
$$

**Step 3: Select isolator stiffness**
$$
k = m\omega_n^2
$$

**Step 4: Check static deflection**
$$
\delta_{st} = \frac{mg}{k} = \frac{g}{\omega_n^2}
$$
Must be within allowable limits.

**Step 5: Select damping**
Balance [[Resonance]] control vs. isolation performance.

### Transmissibility Measurement

**Experimental methods:**
1. **Swept-sine testing:** Measure response at various frequencies
2. **Impact testing:** Use FFT to compute transmissibility from impulse response
3. **Operational testing:** Measure during normal operation
4. **Shaker testing:** Controlled excitation with known input

**Measurement setup:**
- Two accelerometers: One on source, one on receiver
- Signal analyzer to compute [[Transfer Function]]
- Calibration for amplitude and phase accuracy

### Numerical Computation

**[[Finite Element Analysis (FEA)]]:**
- Model isolator as spring-damper elements
- Perform [[harmonic analysis]] over frequency range
- Extract transmissibility between nodes

**MATLAB implementation:**
```matlab
function T = transmissibility(r, zeta)
    T = sqrt((1 + (2*zeta*r).^2) ./ ((1 - r.^2).^2 + (2*zeta*r).^2));
end

% Example usage
r = logspace(-1, 1, 1000);  % Frequency ratio from 0.1 to 10
zeta = 0.05;                 % Damping ratio
T = transmissibility(r, zeta);
semilogx(r, 20*log10(T));    % Plot in dB
```

## Advantages and Limitations

### Strengths
1. **Quantitative design tool:** Provides exact isolation performance prediction
2. **Universal applicability:** Applies to any linear vibration isolation system
3. **Simple graphical representation:** Easy to understand via transmissibility curves
4. **Design guidance:** Clear criteria for isolation effectiveness
5. **Experimental validation:** Easily measurable for verification

### Weaknesses
1. **Linear assumption:** Real systems often have nonlinearities
2. **Single-frequency assumption:** Real excitations are often broadband
3. **SDOF limitation:** Real systems have multiple [[Degrees of Freedom]]
4. **Neglects higher modes:** Important for complex structures
5. **Steady-state assumption:** Transient effects not captured

### Validity Range
- **Applicable when:** Linear systems, harmonic excitation, steady-state conditions
- **Not applicable when:** Strong nonlinearities, impact loading, chaotic systems
- **Breakdown scenarios:** Large deformations, material yielding, clearances

## Advanced Topics

### Nonlinear Transmissibility

**Cubic stiffness (Duffing oscillator):**
$$
m\ddot{x} + c\dot{x} + kx + \alpha x^3 = F_0\cos(\omega t)
$$
Transmissibility becomes amplitude-dependent and may exhibit jump phenomena.

**Friction damping:**
With Coulomb friction, transmissibility shows different characteristics:
- Reduced [[Resonance]] peak
- More effective high-frequency isolation
- Amplitude-dependent behavior

**Piecewise linear systems:**
- Clearances or gaps create nonlinear transmissibility
- Bilinear stiffness from elastomeric isolators

### Multi-Degree-of-Freedom Transmissibility

**Matrix transmissibility:**
For MDOF systems, transmissibility matrix relates responses at different points:
$$
\mathbf{T}(\omega) = \mathbf{H}_R(\omega) \mathbf{H}_S^{-1}(\omega)
$$
where $\mathbf{H}$ are [[Frequency Response Function (FRF)]] function matrices.

**Transfer path analysis:**
Identifies dominant paths for vibration transmission in complex systems.

### Active and Semi-Active Isolation

**Active isolation:** Uses control forces to achieve desired transmissibility:
- Can achieve $T < 1$ even at low frequencies
- Adapts to changing conditions
- More complex and expensive

**Semi-active isolation:** Variable damping or stiffness:
- Skyhook damping: Achieves better isolation than passive
- Magnetorheological (MR) dampers: Fast variable damping
- Stiffness switching: For different operating conditions

### Statistical Energy Analysis (SEA)

For high-frequency vibration:
- Transmissibility replaced by coupling loss factors
- Power flow approach rather than deterministic response
- Useful for complex built-up structures

## Special Cases and Examples

### Benchmark Problems

**Simple isolator design:**
- Mass: $m = 100$ kg
- Operating frequency: $f = 30$ Hz ($\omega = 188.5$ rad/s)
- Required isolation: 90% ($T = 0.1$)
- Calculate required natural frequency and static deflection:

**Solution:**
$$
\omega_n \approx \frac{\omega}{\sqrt{1 + 1/T}} = \frac{188.5}{\sqrt{1 + 1/0.1}} = 56.2 \text{ rad/s} (8.94 \text{ Hz})
$$
$$
k = m\omega_n^2 = 100 \times (56.2)^2 = 316 \text{ kN/m}
$$
$$
\delta_{st} = \frac{mg}{k} = \frac{100 \times 9.81}{316 \times 10^3} = 3.1 \text{ mm}
$$

**Two-stage isolation:**
For better high-frequency isolation:
- Two spring-mass systems in series
- Lower [[Natural Frequency]] overall
- More complex transmissibility with two resonances

### Analytical Solutions

**Exact [[Resonance]] frequency:**
Maximum transmissibility occurs at:
$$
r_{\max} = \sqrt{\frac{\sqrt{1+8\zeta^2} - 1}{2\zeta^2}}
$$
With maximum value:
$$
T_{\max} = \sqrt{1 + \frac{1}{(2\zeta\sqrt{1-\zeta^2})^2}} \approx \frac{1}{2\zeta} \text{ for small } \zeta
$$

**High-frequency asymptote:**
For $r \gg 1$:
$$
T \approx \frac{2\zeta}{r} \quad \text{(displacement transmissibility)}
$$
In dB: $T_{\text{dB}} \approx 20\log_{10}(2\zeta) - 20\log_{10}(r)$

### Design Examples

**Engine mount design:**
- Engine mass: 200 kg
- Idle speed: 800 RPM (13.33 Hz)
- Required isolation at idle: $T < 0.25$
- Design isolator stiffness and check static deflection

**Seismic isolation for building:**
- Building weight: 50,000 kN
- Target isolated period: 2.5 s ($\omega_n = 2.51$ rad/s)
- Required total stiffness: $k = \omega_n^2 m = 3.2 \text{ kN/mm}$
- Number of isolators: 100 → each isolator stiffness: 32 kN/mm

## Error Analysis

### Modeling Errors

**Parameter uncertainties:**
- **Mass uncertainty:** $\frac{\Delta T}{T} \approx -\frac{\Delta m}{m} \cdot \frac{r^2}{1-r^2}$ near [[Resonance]]
- **Stiffness uncertainty:** $\frac{\Delta T}{T} \approx \frac{\Delta k}{k} \cdot \frac{r^2}{1-r^2}$ near [[Resonance]]
- **Damping uncertainty:** Most critical near [[Resonance]]

**Model simplifications:**
- Neglected rotational [[Degrees of Freedom]]
- Assumed rigid foundation
- Ignored isolator mass
- Linearized nonlinear behavior

### Measurement Errors

**Instrumentation errors:**
- Accelerometer calibration errors (typically 1-3%)
- Phase mismatch between sensors
- Cross-axis sensitivity
- Cable and connector effects

**Signal processing errors:**
- Leakage in FFT analysis
- Noise contamination
- Inadequate frequency resolution
- Window selection effects

### Design Margin Considerations

**Safety factors:**
- Typically design for $r > \sqrt{2} \times$ safety factor
- Account for parameter variations
- Consider temperature effects on isolator properties
- Include aging and creep effects

## Relationship to Other Concepts

### Connection to [[Frequency Response Function (FRF)]] Function

Transmissibility is a specific type of FRF:
- **FRF:** General input-output relationship
- **Transmissibility:** Specific FRF for base excitation or force transmission
- **Relationship:** $T(\omega) = |H(\omega)|$ for specific input/output pairs

### Contrast with Mobility

- **Transmissibility:** Ratio of responses (dimensionless)
- **Mobility:** Velocity response per unit force (admittance)
- **Relationship:** Different representations of system dynamics

### Connection to [[Impedance]]

**Mechanical [[impedance]]:** $Z_m = F/v$
**Transmissibility relates to [[impedance]] mismatch:**
$$
T = \left|\frac{Z_{\text{source}}}{Z_{\text{source}} + Z_{\text{isolator}}}\right|
$$
for simplified models.

### Relationship to Vibration Isolation Criteria

**ISO standards:** Specify allowable transmissibility levels for:
- Human vibration exposure (ISO 2631)
- Machine vibration (ISO 10816)
- Building vibration (ISO 10137)

## Historical Context and Evolution

### Original Motivation

**Industrial revolution challenges:**
- Factory machinery vibrations affecting buildings
- Precision manufacturing requiring stable foundations
- Early steam engine vibration problems

**Military applications:**
- Shipboard equipment isolation
- Aircraft engine mounting
- Weapon system stabilization

### Evolution Over Time

1. **1900-1920:** Empirical approaches, trial and error
2. **1930-1950:** Analytical methods developed, Den Hartog's work
3. **1960-1980:** Computer analysis, MDOF methods, [[Random Vibration]]
4. **1990-present:** Active control, smart materials, optimization

### Modern Reformulations

- **Energy harvesting:** Optimizing transmissibility for power generation
- **Metamaterials:** Creating frequency bandgaps for vibration isolation
- **Topology optimization:** Designing isolators for specific transmissibility targets
- **Digital twins:** Real-time transmissibility monitoring and prediction

## Pedagogical Approach

### Teaching Strategies

1. **Physical demonstrations:** Show simple spring-mass systems with shaker
2. **Interactive simulations:** Allow students to adjust parameters and see transmissibility curves
3. **Design projects:** Design isolator for given specifications
4. **Laboratory experiments:** Measure transmissibility of actual isolators

### Common Misconceptions

1. **"More damping always improves isolation":** False, damping hurts high-frequency isolation
2. **"Softer isolators always better":** Too soft causes large static deflections
3. **"Transmissibility less than 1 means no vibration":** Just reduced, not eliminated
4. **"Isolation works at all frequencies":** Only above $\sqrt{2}\omega_n$

### Learning Resources

**Foundational Texts:**
- Harris & Crede, "Shock and Vibration Handbook"
- Den Hartog, "Mechanical Vibrations"
- Rao, "Mechanical Vibrations"
- Inman, "Engineering Vibration"

**Online Resources:**
- MATLAB tutorials on vibration isolation
- Wolfram Demonstrations: Transmissibility plots
- MIT OpenCourseWare: Dynamics and Control
- Engineering Toolbox: Vibration isolation design guides

**Visual Aids:**
- Transmissibility curve posters showing different damping levels
- Animation of mass-spring-damper system under base excitation
- Videos of isolation systems in operation (buildings, vehicles, machinery)

## Implementation in Software

### MATLAB Implementation

```matlab
% Comprehensive transmissibility analysis
function [T, phase] = transmissibility_full(r, zeta)
    % Calculate magnitude and phase
    numerator = 1 + 1i*2*zeta*r;
    denominator = (1 - r.^2) + 1i*2*zeta*r;
    H = numerator ./ denominator;
    T = abs(H);
    phase = angle(H) * 180/pi; % degrees
end

% Plot transmissibility for various damping ratios
r = logspace(-1, 1, 1000); % Frequency ratio from 0.1 to 10
zeta_values = [0.01, 0.05, 0.1, 0.2, 0.5, 0.7];

figure;
for i = 1:length(zeta_values)
    T = transmissibility_full(r, zeta_values(i));
    semilogx(r, 20*log10(T), 'LineWidth', 2, 'DisplayName', sprintf('ζ=%.2f', zeta_values(i)));
    hold on;
end
xlabel('Frequency Ratio r = ω/ω_n');
ylabel('Transmissibility (dB)');
title('Transmissibility vs. Frequency Ratio for Various Damping Ratios');
legend('Location', 'best');
grid on;
xline(sqrt(2), '--r', 'r = √2', 'LabelVerticalAlignment', 'bottom');
yline(0, '--k', 'T = 1 (0 dB)');
```

### Python with SciPy

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal

def transmissibility(r, zeta):
    """Calculate transmissibility magnitude and phase."""
    numerator = 1 + 2j*zeta*r
    denominator = (1 - r**2) + 2j*zeta*r
    H = numerator / denominator
    return np.abs(H), np.angle(H, deg=True)

# Generate frequency ratios
r = np.logspace(-1, 1, 1000)
zeta_values = [0.01, 0.05, 0.1, 0.2, 0.5]

# Plot
plt.figure(figsize=(10, 6))
for zeta in zeta_values:
    T, phase = transmissibility(r, zeta)
    plt.semilogx(r, 20*np.log10(T), label=f'ζ={zeta}')
plt.axvline(np.sqrt(2), color='r', linestyle='--', label='r=√2')
plt.axhline(0, color='k', linestyle='--', alpha=0.5)
plt.xlabel('Frequency Ratio r = ω/ω_n')
plt.ylabel('Transmissibility (dB)')
plt.title('Transmissibility Curves for Different Damping Ratios')
plt.legend()
plt.grid(True, which='both', linestyle='--', alpha=0.5)
plt.ylim(-40, 40)
plt.show()
```

### Commercial Software

**ANSYS Mechanical:**
- Harmonic analysis with base excitation
- Transmissibility extraction between any two nodes
- Parametric studies for isolator design optimization

**MATLAB Simulink/Simscape:**
- Multi-domain isolation system modeling
- Control system design for active isolation
- Real-time simulation of transmissibility

**LMS Test.Lab:**
- Experimental [[Modal Analysis]]
- Operational deflection shapes
- Transmissibility measurement from test data

## See Also

- Vibration Isolation
- [[Frequency Response Function (FRF)]]
- Base Excitation
- Dynamic Vibration Absorber
- Mechanical Impedance
- [[Transmissibility Matrix]]
- Isolation Efficiency
- [[Harmonic Response]]
- [[Damping Ratio]]
- [[Natural Frequency]]
- Force Transmissibility
- Seismic Isolation
- Machine Mounts
- Active Vibration Control
- Passive Isolation
- Shock Transmissibility
- Acoustic Transmission Loss
- Vibration Attenuation
- Dynamic Stiffness

---

*Note: Transmissibility represents a fundamental concept in vibration engineering, providing a quantitative measure of vibration isolation effectiveness. Its mathematical formulation enables precise design of isolation systems, while its graphical representation offers intuitive understanding of the trade-offs between [[Resonance]] control and high-frequency isolation performance.*
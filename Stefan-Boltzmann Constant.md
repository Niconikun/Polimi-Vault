---
title: Stefan-Boltzmann Constant
tags:
  - thermodynamics
  - radiation
  - physics
  - astrophysics
---

# Stefan-Boltzmann Constant

## Formal Definition

The **Stefan-Boltzmann constant** ($\sigma$) is a fundamental physical constant that relates the total radiant energy emitted by a perfect black body to its absolute temperature. It appears in the Stefan-Boltzmann law, which states that the power radiated per unit surface area of a black body is proportional to the fourth power of its absolute temperature. The constant is essential in [[Thermodynamics]], [[Astrophysics]], radiative heat transfer, and the study of [[Atmosphere|atmospheric]] and [[Combustion]] processes.

## Historical Development

### Key Milestones
- **1879:** Josef Stefan experimentally discovers the T⁴ radiation law
- **1884:** Ludwig Boltzmann derives law theoretically from thermodynamic principles
- **1900:** Max Planck develops quantum theory; provides fundamental justification
- **1905–1915:** Early astrophysics applications to stellar luminosity
- **1950s–1960s:** Precision measurements; satellite thermal control applications
- **1983–2019:** CODATA refinements; value adopted as exact (2019 SI redefinition)
- **Modern Era:** Critical for climate modeling, satellite thermal analysis, laser physics

### Foundational Contributors
1. **Josef Stefan (1835–1893):** Experimental discovery of radiation law
2. **Ludwig Boltzmann (1844–1906):** Thermodynamic derivation
3. **Max Planck (1858–1947):** Quantum foundation; Planck constant relationship
4. **Arthur Schuster (1850–1934):** Early astrophysical applications
5. **CODATA Community:** Modern precision determinations

## Numerical Value and Units

### Stefan-Boltzmann Constant

$$
\sigma = 5.670374419 \times 10^{-8} \, \text{W} \, \text{m}^{-2} \, \text{K}^{-4}
$$

**Alternative expressions:**
- $\sigma = 5.670374419 \times 10^{-8}$ J s$^{-1}$ m$^{-2}$ K$^{-4}$
- $\sigma = 1.38568...$ calorie s$^{-1}$ cm$^{-2}$ K$^{-4}$ (CGS system)

**Definition basis (2019 SI):**
$$
\sigma = \frac{2\pi^5 k_B^4}{15 h^3 c^2}
$$

Where:
- $k_B = 1.380649 \times 10^{-23}$ J/K: [[Boltzmann Constant]]
- $h = 6.62607015 \times 10^{-34}$ J⋅s: Planck constant
- $c = 299792458$ m/s: speed of light
- Exact as of 2019 SI redefinition

## Mathematical Formulation

### Stefan-Boltzmann Law

**Power radiated per unit surface area:**
$$
j = \sigma T^4
$$

Where:
- $j$: radiative flux (W/m²)
- $T$: absolute temperature (K)
- $\sigma$: Stefan-Boltzmann constant

**Interpretation:** Radiative power increases rapidly with temperature (fourth-power dependence).

### Total Radiated Power

For object with surface area $A$ and emissivity $\epsilon$ (0 ≤ $\epsilon$ ≤ 1):

$$
P = \epsilon \sigma A T^4
$$

**Black body:** $\epsilon = 1$ (perfect emitter)
**Real surface:** $\epsilon < 1$ (depends on material, wavelength, temperature)

### Net Radiative Heat Transfer

For object at temperature $T$ in surroundings at temperature $T_{\text{surr}}$:

$$
P_{\text{net}} = \epsilon \sigma A (T^4 - T_{\text{surr}}^4)
$$

Object emits at rate $\sigma T^4$; absorbs from surroundings at rate $\sigma T_{\text{surr}}^4$.

### Connection to Planck's Law

**Spectral radiance** (power per unit wavelength per unit area per solid angle):

$$
L_\lambda(T) = \frac{2hc^2}{\lambda^5} \frac{1}{e^{hc/\lambda k_B T} - 1}
$$

**Integration over all wavelengths and solid angle:**
$$
j = \int_0^\infty L_\lambda(T) \, d\lambda = \sigma T^4
$$

Stefan-Boltzmann constant emerges as integration result of Planck's law.

## Fundamental Principles

### Blackbody Radiation

**Perfect blackbody:** 
- Absorbs all incident radiation (absorptivity = 1)
- Emits maximum radiation for given temperature
- Planck distribution describes spectral content

**Wien's Displacement Law** (peak wavelength):
$$
\lambda_{\text{max}} T = b = 2.897771955 \times 10^{-3} \, \text{m⋅K}
$$

Example: Sun surface (T ≈ 5778 K) peaks in visible light; Earth (T ≈ 288 K) peaks in infrared.

### Thermodynamic Basis

**From second law of thermodynamics:**

Energy density of radiation in cavity at temperature $T$:
$$
u = a T^4
$$

Where $a$ is radiation constant related to $\sigma$.

**Derivation connects:**
- Photon properties (wave-particle duality)
- Statistical mechanics (Bose-Einstein distribution)
- Thermodynamic potentials (Helmholtz free energy)

### Material Properties

**Emissivity $\epsilon(T, \lambda)$:**
- Temperature dependent for real materials
- Wavelength dependent (spectral emissivity)
- Material-specific; measured experimentally

**Emissivity values (at room temperature):**
- Polished aluminum: 0.03–0.05
- Oxidized steel: 0.8–0.9
- Human skin: 0.98
- Water: 0.96

## Relationship to Other Concepts

1. **Connection to [[Thermodynamics]]:**
   - Fundamental law of radiative heat transfer
   - Fourth law of thermodynamics (radiation)

2. **Connection to [[Planck Constant]]:**
   - Derived from quantization of electromagnetic field
   - $\sigma$ contains explicit Planck constant dependence

3. **Connection to [[Boltzmann Constant]]:**
   - Contains $k_B$ in fundamental definition
   - Links microscopic and macroscopic thermal physics

4. **Connection to [[Astrophysics]] and [[Astronomy]]:**
   - Star luminosity: $L = 4\pi R^2 \sigma T_{\text{eff}}^4$
   - Stefan-Boltzmann law enables temperature measurement

5. **Connection to [[Atmosphere]] and [[Combustion]]:**
   - Solar radiation absorbed by atmosphere
   - Thermal radiation from flames

## Computational Applications

### Solar Radiation

**Solar constant** (Earth orbital distance):
$$
I_{\text{solar}} = \frac{L_{\odot}}{4\pi d^2} = 1361 \, \text{W/m}^2
$$

Where:
- $L_{\odot} = 3.828 \times 10^{26}$ W: solar luminosity
- $d = 1.496 \times 10^{11}$ m: Earth-Sun distance (1 AU)

**Relation to solar effective temperature:**
$$
L_{\odot} = 4\pi R_{\odot}^2 \sigma T_{\text{eff,sun}}^4
$$

With $T_{\text{eff,sun}} \approx 5778$ K, $R_{\odot} \approx 6.96 \times 10^8$ m.

### Satellite Thermal Analysis

**Equilibrium temperature** for spacecraft absorbing solar radiation:

$$
T_{\text{eq}} = \left(\frac{\alpha I_{\text{solar}} A}{2\epsilon \sigma A}\right)^{1/4}
$$

Simplified (assuming spacecraft in direct Sun):
$$
T_{\text{eq}} = \left(\frac{\alpha I_{\text{solar}}}{2\epsilon \sigma}\right)^{1/4}
$$

Where:
- $\alpha$: solar absorptivity
- $\epsilon$: infrared emissivity
- Factor of 2: accounts for day-night cycle (averaging)

**Example:** CubeSat with $\alpha = 0.6$, $\epsilon = 0.85$ in Earth orbit

$$
T_{\text{eq}} = \left(\frac{0.6 \times 1361}{2 \times 0.85 \times 5.67 \times 10^{-8}}\right)^{1/4} \approx 325 \, \text{K} \approx 52°\text{C}
$$

### Planetary Temperature

**Effective temperature (energy balance):**

$$
T_{\text{eff}} = \left(\frac{L_{\text{star}}(1-A)}{16\pi \sigma d^2}\right)^{1/4}
$$

Where:
- $L_{\text{star}}$: stellar luminosity
- $A$: planetary albedo (reflectivity)
- $d$: orbital distance

**Earth example:**
- Solar input: ~342 W/m² (after distance correction)
- Albedo: 0.31
- Without greenhouse effect: $T_{\text{eff}} \approx 255$ K (−18°C)
- With atmosphere: $T_{\text{eff}} \approx 288$ K (+15°C)

### Radiative Heat Transfer Rate

**Cooling by radiation** (Newton-style law):

$$
\frac{dE}{dt} = -\epsilon \sigma A (T^4 - T_{\text{surr}}^4)
$$

**For small temperature differences** (linearization):
$$
\frac{dE}{dt} \approx -4\epsilon \sigma A T_{\text{surr}}^3 (T - T_{\text{surr}})
$$

Approximates exponential cooling with effective heat transfer coefficient $h = 4\epsilon \sigma T_{\text{surr}}^3$.

## Practical Applications

### Thermal Engineering

**Radiator Design:**
- Spacecraft radiator power: $P = \epsilon \sigma A T^4$
- Maximize $\epsilon$ (black coating); minimize mass/area
- Trade-off with solar absorptivity ($\alpha$)

**Temperature Control:**
- Multi-layer insulation (MLI): reduces radiative coupling
- Selective coatings: high $\epsilon$ in infrared, low $\alpha$ in solar

### Pyrometry (Temperature Measurement)

**Infrared thermography:**
- Noncontact temperature measurement
- Requires emissivity correction: $T = (L_\lambda/(\epsilon \sigma))^{1/4}$

**Optical pyrometer:**
- Compares target brightness to reference source

### Climate Science

**Greenhouse effect modeling:**
- Earth radiates at 288 K; atmosphere absorbs and re-radiates
- Enhanced greenhouse effect from CO₂, CH₄ increases atmospheric opacity
- Equilibrium shifts to higher surface temperature

**Radiative forcing:**
$$
\Delta F = 5.35 \ln(C/C_0) \, \text{W/m}^2
$$

Relates CO₂ concentration to additional heat trapping (Stefan-Boltzmann effect).

### Astronomy and Stellar Astrophysics

**Hertzsprung-Russell Diagram:**
- Stellar temperature from color (Wien's law)
- Stellar luminosity from apparent magnitude
- Radius: $R = \sqrt{L/(4\pi \sigma T^4)}$

**Example:** Betelgeuse (red supergiant)
- $T_{\text{eff}} \approx 3500$ K, $L \approx 1.26 \times 10^5 L_{\odot}$
- Radius: $R \approx 700 R_{\odot}$ (enormous size, low temperature)

## Advanced Topics

### Spectral Emissivity

**Real materials:** emissivity varies with wavelength and temperature

$$
L_\lambda(T) = \epsilon_\lambda(T) L_{\lambda,\text{BB}}(T)
$$

**Application:** Selective surfaces
- High $\epsilon$ in infrared (radiation cooling)
- Low $\alpha$ in solar spectrum (minimize solar heating)
- Efficiency: selectivity $S = \alpha/\epsilon > 1$

### Radiative Transport Equation

In participating media (gases, dusty air):

$$
\frac{dI}{ds} = -\kappa_\lambda I + \kappa_\lambda \sigma T^4/\pi
$$

Stefan-Boltzmann law provides source term for radiative transfer.

### Radiation-Conduction Coupling

Combined heat transfer:
$$
\rho c_p \frac{\partial T}{\partial t} = k \nabla^2 T - \frac{\partial}{\partial x}(\epsilon \sigma T^4)
$$

Nonlinear coupling; requires iterative solution methods.

## Table of Radiative Properties

| Material | Emissivity (thermal) | Absorptivity (solar) | Temperature Range |
|---|---|---|---|
| Polished aluminum | 0.04 | 0.10 | All |
| Oxidized aluminum | 0.25 | 0.45 | All |
| Black paint | 0.98 | 0.96 | Room–500K |
| White paint | 0.95 | 0.25 | Room–500K |
| Polished copper | 0.05 | 0.10 | Room temp |
| Oxidized copper | 0.85 | 0.70 | All |
| Glass | 0.88 | 0.10 | Room–1000K |

## See Also

- [[Thermodynamics]]
- [[Planck Constant]]
- [[Boltzmann Constant]]
- [[Heat Transfer]]
- [[Astrophysics]]
- [[Solar Radiation]]
- [[Atmosphere]]
- [[Combustion]]
- [[Wien's Displacement Law]]
- [[Planck's Law]]

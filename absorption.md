---
title: Absorption
tags:
  - thermodynamics
  - optics
  - material science
  - radiation
---

# Absorption

## Formal Definition

**Absorption** is the physical process by which electromagnetic radiation or other forms of energy are taken up by matter, converting incident energy into internal energy of the material. It is characterized by the **absorptivity** (α), a dimensionless property ranging from 0 to 1, representing the fraction of incident radiant energy that is absorbed rather than reflected or transmitted. Absorption is fundamental to [[Thermodynamics]], [[Heat Transfer]], [[Optics]], and appears in applications ranging from spacecraft thermal design to optical sensing and [[Signal Processing]].

## Historical Development

### Key Milestones
- **1666:** Isaac Newton's prism experiments; foundation of light absorption concepts
- **1820s:** Joseph Fraunhofer observes absorption lines in solar spectrum
- **1860:** Gustav Kirchhoff establishes relationship between absorptivity and emissivity (Kirchhoff's Law)
- **1900:** Max Planck develops quantum theory; explains absorption at atomic level
- **1905:** Albert Einstein explains photoelectric effect; photon absorption
- **1950s–1960s:** Aerospace applications; spacecraft thermal control via absorption
- **1980s–Present:** Nanomaterials, selective absorbers, metamaterials with tailored absorption

### Foundational Contributors
1. **Isaac Newton (1643–1727):** Light dispersion; foundation of spectroscopy
2. **Joseph von Fraunhofer (1787–1826):** Spectral absorption lines mapping
3. **Gustav Kirchhoff (1824–1887):** Law of thermal radiation absorption/emission
4. **Max Planck (1858–1947):** Quantum theory explaining energy absorption
5. **Albert Einstein (1879–1955):** Photoelectric effect; photon absorption

## Mathematical Formulation

### Absorptivity Definition

**Absorptivity (α):**
$$
\alpha = \frac{\Phi_{\text{absorbed}}}{\Phi_{\text{incident}}}
$$

Where:
- $\Phi_{\text{absorbed}}$: Radiant power absorbed (W)
- $\Phi_{\text{incident}}$: Total incident radiant power (W)
- Range: $0 \leq \alpha \leq 1$

**Material classification:**
- Perfect blackbody: $\alpha = 1$ (absorbs all incident radiation)
- Perfect reflector: $\alpha = 0$ (absorbs nothing)
- Real materials: $0 < \alpha < 1$

### Energy Conservation

For opaque surface (no transmission):
$$
\alpha + \rho = 1
$$

Where $\rho$ is **reflectivity** (fraction reflected).

For semi-transparent material:
$$
\alpha + \rho + \tau = 1
$$

Where $\tau$ is **transmissivity** (fraction transmitted).

### Spectral Absorption

**Absorption varies with wavelength:**
$$
\alpha(\lambda, T) = \text{spectral absorptivity}
$$

**Average absorptivity over spectrum:**
$$
\bar{\alpha} = \frac{\int_0^\infty \alpha(\lambda) E_\lambda(\lambda) d\lambda}{\int_0^\infty E_\lambda(\lambda) d\lambda}
$$

Where $E_\lambda(\lambda)$ is spectral irradiance.

### Kirchhoff's Law of Thermal Radiation

**At thermal equilibrium:**
$$
\alpha(\lambda, T) = \varepsilon(\lambda, T)
$$

**Interpretation:** At a given wavelength and temperature, absorptivity equals emissivity.

**Consequence:** Perfect absorber (blackbody, $\alpha = 1$) is also perfect emitter ($\varepsilon = 1$).

### Absorption Coefficient (Beer-Lambert Law)

For transmission through absorbing medium:
$$
I(x) = I_0 e^{-\mu x}
$$

Where:
- $\mu$: absorption coefficient (m⁻¹)
- $x$: distance traveled through medium
- $I_0$: initial intensity
- $I(x)$: intensity at depth $x$

**Optical depth:**
$$
\tau_{\text{opt}} = \mu x
$$

## Fundamental Principles

### Quantum Mechanical Absorption

**Photon absorption process:**

Photon with energy $E = h\nu$ interacts with electron:
- If $E > E_{\text{gap}}$: photon absorbed, electron excited to higher energy level
- If $E < E_{\text{gap}}$: photon passes through (transparent)
- If $E = E_{\text{gap}}$: resonant absorption (maximum absorption)

**Excited state relaxation:**

Electron returns to ground state via:
- **Radiative decay:** Re-emission of photon (luminescence)
- **Non-radiative decay:** Heat generation (thermal energy)

### Molecular Absorption

**Vibrational transitions** (infrared range):

Molecules absorb radiation matching vibrational modes:
- Stretching modes: νs ≈ 500–3000 cm⁻¹
- Bending modes: νb ≈ 100–500 cm⁻¹

**Application:** [[Heat Transfer]] through atmospheric windows; greenhouse gas absorption.

### Surface Absorption

**Material-dependent mechanisms:**

1. **Bulk absorption:** Distributed throughout volume (dark materials)
2. **Surface absorption:** Concentrated at surface (thin films, coatings)
3. **Resonant absorption:** Sharp peaks at specific wavelengths (optical resonators)

## Connection to Other Concepts

1. **Connection to [[Stefan-Boltzmann Constant]]:**
   - Absorbed solar power: $P = \alpha S A \cos(\theta)$
   - Related to [[Heat Transfer]] and temperature equilibrium

2. **Connection to [[Kirchhoff-Love Shell Element]] and [[Absorptivity]]:**
   - Material properties in thermal FEA
   - Boundary conditions for heat transfer

3. **Connection to [[Emissivity]]:**
   - Kirchhoff's law: $\alpha(\lambda, T) = \varepsilon(\lambda, T)$
   - Radiative heat balance

4. **Connection to [[Optics]] and [[Signal Processing]]:**
   - Optical absorption limits transmission
   - Sensor response via photoelectric absorption

5. **Connection to [[Atmosphere]]:**
   - Atmospheric absorption of solar radiation
   - Greenhouse gas absorption (CO₂, CH₄, H₂O)

## Types of Absorption

### Solar Absorption

**Sun's spectrum:** Peak in visible range (0.2–3.0 μm)

**Solar absorptivity** ($\alpha_s$): Material property in solar spectrum

**Aerospace application:** 
- Black paint: $\alpha_s \approx 0.95$ (absorbs most solar energy)
- White paint: $\alpha_s \approx 0.25$ (reflects most solar energy)
- Multi-layer insulation (MLI): $\alpha_s \approx 0.05$ (highly reflective)

### Thermal (Infrared) Absorption

**Earth's thermal radiation:** Peak in infrared (3–50 μm)

**Thermal emissivity** ($\varepsilon$): Material property in thermal spectrum

**Example:** Gold foil: $\alpha_s = 0.3$ (shiny), $\varepsilon = 0.02$ (poor radiator)

### Acoustic Absorption

**Sound wave absorption:** Mechanical vibration damping

**Absorption coefficient** (Sabine): 0–1 scale

**Applications:** Sound isolation, vibration damping in aerospace structures

## Practical Applications

### Spacecraft Thermal Control

**Temperature equilibrium:**
$$
\alpha_s S A = \varepsilon \sigma T^4 A + Q_{\text{internal}}
$$

**Design trade-off:**
- High $\alpha_s$, low $\varepsilon$: Selective absorber (rejects heat)
- Low $\alpha_s$, high $\varepsilon$: Rejects solar, radiates thermal (passive cooling)

**Example:** Mars rover radiator uses paint with $\alpha_s/\varepsilon \approx 0.3$ (heat rejection).

### Optical Filters and Sensors

**Bandpass filter:** Absorbs all except narrow wavelength range

**Photodetector:** Absorbs photons in specific range; generates electrical signal

**Spectrometer:** Measures absorption spectrum at different wavelengths

### Atmospheric Science

**Atmospheric window:** 8–13 μm transparent (low absorption)

**Greenhouse effect:** CO₂, CH₄ absorb in infrared → atmosphere warms

**Ozone depletion:** CFCs absorb UV, preventing ozone formation

### Material Testing

**UV absorption test:** Determine material degradation by UV exposure

**Thermal absorption analysis:** FEA with temperature-dependent $\alpha(T)$

## Measurement Methods

### Spectrophotometry

**Transmitted light method:**
$$
\alpha = 1 - T - \rho
$$

Where $T$ is transmissivity (measured by spectrophotometer).

**Integrating sphere:** Measures hemispherical reflectivity; $\alpha = 1 - \rho$.

### Thermal Analysis

**Calorimetry:** Measure temperature rise from known solar input

**Differential scanning calorimetry (DSC):** Heat absorption during phase transitions

### Direct Measurement

**Radiometer:** Measure incident vs. absorbed power directly

**Thermal imaging:** Observe temperature distribution on surface

## Absorption Spectra

### Common Materials

| Material | Solar α | Thermal ε | Application |
|---|---|---|---|
| Black paint | 0.95 | 0.90 | Solar absorber |
| White paint | 0.25 | 0.95 | Thermal radiator |
| Gold foil | 0.30 | 0.02 | Solar reflector |
| Polished aluminum | 0.10 | 0.05 | Highly reflective |
| Carbon black | 0.99 | 0.98 | Perfect absorber (test reference) |
| Glass | 0.08 | 0.88 | Transmissive to solar, opaque to thermal |

## Connection to Related Phenomena

### Fluorescence vs. Phosphorescence

**Fluorescence:** Immediate re-emission after absorption (nanoseconds)

**Phosphorescence:** Delayed re-emission; energy stored in metastable state

Both involve absorption, followed by radiative relaxation.

### Photochemical Reactions

**Photosynthesis:** Absorption of photons drives chemical reactions

**Photopolymerization:** UV absorption initiates polymer cross-linking

## Advanced Topics

### Nonlinear Absorption

**Multi-photon absorption:** Simultaneous absorption of two or more photons

**Saturation:** At high intensity, absorption decreases (excited state population saturates)

### Metamaterials

**Engineered absorption:** Design structures to achieve specific absorption spectra

**Perfect absorption:** Metasurfaces with $\alpha = 1$ across broadband spectrum

**Application:** Thermal emitters, solar absorbers with unprecedented efficiency

## See Also

- [[Absorptivity]]
- [[Emissivity]]
- [[Stefan-Boltzmann Constant]]
- [[Heat Transfer]]
- [[Thermodynamics]]
- [[Optics]]
- [[Kirchhoff's Law]]
- [[Radiation]]
- [[Spectroscopy]]
- [[Atmosphere]]

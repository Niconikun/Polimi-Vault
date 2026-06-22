## Formal Definition

**Sectorial and Tesseral Harmonics** are the components of a celestial body's gravitational potential expansion that account for mass variations across both **latitude and longitude**. While Zonal harmonics ($J_n$) describe "rings" of mass parallel to the equator, Sectorial and Tesseral harmonics describe the "lumpiness" or longitudinal asymmetry of a planet. These terms are essential for modeling orbits around bodies that are not perfectly axisymmetric, such as the Moon or the Earth (due to mountain ranges, ocean basins, and tectonic density variations).



## Historical Development

### Key Milestones
- **1867:** William Thomson (Lord Kelvin) and Peter Tait formalize the mathematical treatment of spherical harmonics in *Treatise on Natural Philosophy*.
- **1960s:** Early satellite tracking (Transit and Telstar) reveals that Earth’s equator is slightly elliptical, a result of the $C_{22}$ and $S_{22}$ sectorial terms.
- **1990s:** The MGS (Mars Global Surveyor) mission maps the extreme tesseral harmonics of Mars, dominated by the massive Tharsis volcanic plateau.
- **2011:** The GRAIL mission maps the Moon's gravity field to unprecedented high degrees, revealing the "crustal lumpy" nature of the lunar interior.

## Mathematical Formulation

In the full geopotential expansion, the terms involving longitude ($\lambda$) are the Sectorial and Tesseral harmonics:

$$V_{S,T} = \frac{\mu}{r} \sum_{n=2}^{\infty} \sum_{m=1}^{n} \left( \frac{R}{r} \right)^n P_{nm}(\sin \phi) \left[ C_{nm} \cos(m\lambda) + S_{nm} \sin(m\lambda) \right]$$

### Component Breakdown
- **$n$ (Degree):** Corresponds to the vertical resolution (latitude).
- **$m$ (Order):** Corresponds to the horizontal resolution (longitude).
- **$P_{nm}$:** Associated Legendre functions.
- **$C_{nm}, S_{nm}$:** Spherical harmonic coefficients determined by satellite observation.

### Classification
1.  **Sectorial Harmonics ($n = m$):** Mass is concentrated in "sectors" or "orange slices" along longitudes. They describe the "ellipticity" of the equator.
    
2.  **Tesseral Harmonics ($n \neq m$):** Mass is arranged in a "checkerboard" pattern of alternating density across the surface. These capture localized features like mountain ranges or deep-sea trenches.
    

## Fundamental Principles

### Resonance
Unlike Zonal harmonics (which cause constant drifting), Sectorial and Tesseral harmonics can lead to **Orbital Resonance**. If a satellite’s [[orbital period]] is a simple fraction of the planet’s rotation period (e.g., GPS satellites or Geostationary satellites), these "lumps" can repeatedly tug on the satellite at the same point in its orbit, causing significant altitude or longitudinal drift.

### Governing Laws
- **Laplace's Equation:** These functions represent the angular portion of the solution to $\nabla^2 V = 0$ in spherical coordinates.
- **Orthogonality:** Each harmonic is mathematically independent of the others, allowing complex gravity fields to be built from simple building blocks.

## Theoretical Framework

### Geostationary Stability
The Earth's $C_{22}$ term (equatorial ellipticity) creates four equilibrium points in geostationary orbit:
- **Stable Points:** Located at approx. $75^\circ E$ and $105^\circ W$. Satellites will naturally "roll" toward these valleys in the gravity field.
- **Unstable Points:** Located at $15^\circ W$ and $165^\circ E$. Satellites at these points will "slide" away toward the stable points without active station-keeping.



## Physical Interpretation

### The "Lumpy" Planet
If Zonal harmonics describe Earth as an "oblate lemon," Sectorial and Tesseral harmonics describe it as a "lumpy potato." For most Earth-orbiting satellites, these effects are much smaller than $J_2$, but for Low Earth Orbit (LEO) satellites or lunar orbiters (where the Moon is very "lumpy"), these terms are the primary reason orbits decay or become unstable over time.

## Advantages and Limitations

### Strengths
1. **High Fidelity:** Essential for precise orbit determination (e.g., GPS, where centimeter-level accuracy is required).
2. **Interior Mapping:** Allows geophysicists to "see" under the surface to detect mineral deposits or tectonic structures.

### Limitations
1. **Computational Cost:** A high-degree model (e.g., EGM2008 goes to degree $n=2159$) requires massive matrix calculations.
2. **Short Range:** These effects decay very rapidly with distance ($1/r^{n+1}$), meaning they are negligible for deep-space probes.

## Applications

### Engineering Disciplines
1. **GEO Station-Keeping:** Calculating the "East-West" maneuvers needed to keep a satellite from drifting toward the gravity valleys.
2. **Lunar Mission Design:** Navigating around "[[Mascons]]" (Mass Concentrations) on the Moon which can cause a spacecraft to crash if not accounted for.
3. **Planetary Science:** Using gravity maps to model the thickness of the Martian crust or the liquid core of Europa.

## See Also

- [[Zonal Harmonic Potentials]]
- [[Geoid]]
- [[Mascons]]
- [[Station-Keeping]]
- [[Spherical Harmonics]]

## Recommended Tags:
#astrodynamics #geophysics #orbital-mechanics #spherical-harmonics #gravity-field #geodesy
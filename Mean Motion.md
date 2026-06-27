---
title: Mean Motion
tags:
  - orbital mechanics
  - celestial mechanics
  - satellite dynamics
  - kepler motion
---

# Mean Motion

## Formal Definition

**Mean motion** (denoted $n$ or $\mu$) is the average angular [[Velocity]] of an orbiting body as it traverses its orbital path. It represents the time-averaged rate at which an orbiting object moves through its orbit and is fundamentally related to the orbital [[Period]] through [[Kepler's Laws]]. For an orbit with period $T$, the mean motion is defined as $n = 2\pi/T$ (in radians per unit time).

## Historical Development

### Key Milestones
- **1687:** Isaac Newton's "Principia Mathematica" establishes the foundation for orbital mechanics and periodic motion
- **1805:** Laplace and others develop perturbation theory using mean motion as a fundamental parameter
- **1840s–1850s:** Development of astronomical almanacs systematically tabulating mean motion for celestial bodies
- **1957:** Sputnik launch initiates modern space age; mean motion becomes essential for satellite tracking
- **1960s–1970s:** Two-Line Element (TLE) sets standardize mean motion as key orbital element for satellite propagation

### Foundational Contributors
1. **Johann Kepler (1571–1630):** Established Kepler's laws relating orbital period to semi-major axis
2. **Isaac Newton (1643–1727):** Derived gravitational dynamics underlying orbital mechanics
3. **Pierre-Simon Laplace (1749–1827):** Developed perturbation theory using mean motion
4. **Celestrak/NORAD Developers:** Standardized mean motion reporting in satellite tracking

## Mathematical Formulation

### General Form

For a [[Kepler]] orbit around a central body:
$$
n = \sqrt{\frac{\mu}{a^3}}
$$

Where:
- $n$: mean motion (radians per unit time)
- $\mu$: gravitational parameter of the central body (km³/s²)
- $a$: semi-major axis of the orbit (km)

This can also be expressed in terms of orbital period:
$$
n = \frac{2\pi}{T}
$$

### Component Breakdown

**Kepler's Third Law Relation:**
$$
T = 2\pi\sqrt{\frac{a^3}{\mu}} = \frac{2\pi}{n}
$$

**Mean Angular Position:**
The mean anomaly $M(t)$ evolves linearly with mean motion:
$$
M(t) = M_0 + n(t - t_0)
$$

Where:
- $M(t)$: [[Mean Anomaly]] at time $t$
- $M_0$: initial mean anomaly
- $t_0$: reference epoch

### Special Cases

1. **Circular Orbit:** For a circular orbit ($e = 0$), mean motion equals true angular velocity
   $$
   n = \sqrt{\frac{\mu}{a^3}} = \frac{2\pi}{T}
   $$

2. **Low Earth Orbit (LEO):** Typical mean motion ~0.070 rad/min (≈ 11 orbits/day)
   $$
   n_{\text{LEO}} \approx 0.0011 \text{ rad/s}
   $$

3. **Geostationary Orbit:** Mean motion exactly matches Earth's rotation
   $$
   n_{\text{GEO}} = \frac{2\pi}{86400 \text{ s}} \approx 7.27 \times 10^{-5} \text{ rad/s}
   $$

## Fundamental Principles

### Core Assumptions

1. **Two-Body Problem:** Analysis typically assumes a test particle orbiting a central gravitating body
2. **Keplerian Motion:** Assumes no perturbations (ideal case); real satellites experience perturbations
3. **Constant Parameters:** Semi-major axis and gravitational parameter are treated as constant (approximately true over short timescales)

### Governing Laws/Theorems

- **Kepler's Second Law:** The radius vector sweeps equal areas in equal times; mean motion connects this to period
- **Kepler's Third Law:** Period squared proportional to semi-major axis cubed; mean motion inversely proportional to $\sqrt{a^3}$
- **Conservation of Angular Momentum:** In unperturbed orbits, angular momentum (and hence mean motion for fixed $a$) is conserved

## Theoretical Framework

### Orbital Elements Representation

Mean motion is one of the six classical [[Orbital Mechanics|orbital elements]] (along with semi-major axis, eccentricity, inclination, longitude of ascending node, and argument of perigee). However, it is redundant with semi-major axis through Kepler's third law.

**Two-Line Element (TLE) Format:**
In [[NORAD]] TLEs, mean motion is reported in revolutions per day:
$$
n_{\text{rev/day}} = \frac{n_{\text{rad/s}} \times 86400}{2\pi}
$$

### Relationship to Other Concepts

1. **Connection to [[Orbital Period]]:**
   - Direct relationship: $T = 2\pi/n$
   - Uniquely determines period for a given orbit

2. **Connection to [[Semi-Major Axis|Semi-Latus Rectum]] and [[Kepler's Third Law]]:**
   - $n = \sqrt{\mu/a^3}$ directly from Kepler's third law
   - Determines time-averaged orbital angular velocity

3. **Connection to [[Mean Anomaly]]:**
   - Mean anomaly increases linearly: $M(t) = M_0 + n(t - t_0)$
   - Used to compute [[Eccentric Anomaly]] and true position

4. **Connection to [[Perturbation|Secular Perturbations]]:**
   - Real satellites have time-varying mean motion due to perturbations
   - Nodal precession and apsidal precession are expressed relative to mean motion

## Practical Calculation

### From Orbital Elements

Given semi-major axis $a$ in km and using Earth's gravitational parameter $\mu_{\oplus} = 398,600.4418$ km³/s²:

$$
n \text{ [rad/s]} = \sqrt{\frac{398600.4418}{a^3}}
$$

### From Orbital Period

Given period $T$ in seconds:
$$
n \text{ [rad/s]} = \frac{2\pi}{T}
$$

### Example: International Space Station (ISS)

- Orbital period: ~90.3 minutes
- Semi-major axis: ~6,720 km
- Mean motion: $n \approx 0.001160$ rad/s $\approx 1.163$ rev/day

## Perturbations and Variations

### Secular Perturbations

Real satellites experience long-term (secular) changes in mean motion due to:
- **Oblateness ($J_2$ perturbation):** Non-spherical Earth shape
- **Atmospheric drag:** Gradual decay in [[Low Earth Orbit]] spacecraft
- **Lunisolar perturbations:** Gravitational influence of Moon and Sun

These are often expressed as mean motion rates $\dot{n}$:
$$
\dot{n} = \frac{dn}{dt}
$$

### Short-Periodic Perturbations

Higher-frequency variations superimposed on secular trends, typically negligible for long-term predictions.

## Applications

### Satellite Tracking and Propagation

Mean motion is essential for:
- Computing satellite position at future times
- Ephemeris generation
- [[Orbit]] determination from ground observations
- [[Orbital Mechanics|Orbital]] prediction algorithms (e.g., SGP4 model)

### Orbital Maneuvers

Mean motion changes are used to plan:
- [[Phasing Maneuvers]] between spacecraft
- [[Station-Keeping]] maneuvers to maintain mean motion
- [[Transfer Orbits]]

### Resonance and Stability

- Mean motion ratios determine long-term stability
- Mean motion resonances (e.g., 2:1 [[Kozai-Lidov Resonance]]) create dynamical structures

## See Also

- [[Orbital Period]]
- [[Kepler's Third Law]]
- [[Mean Anomaly]]
- [[Eccentric Anomaly]]
- [[Orbital Mechanics]]
- [[Semi-Major Axis]]
- [[Kepler Motion]]
- [[Perturbation]]
- [[Two-Body Problem]]
- [[State Vector]]
- [[Orbit Propagation]]

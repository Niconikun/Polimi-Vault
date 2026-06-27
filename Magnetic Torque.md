---
title: Magnetic Torque
tags:
  - electromagnetism
  - spacecraft dynamics
  - attitude control
  - magnetic fields
---

# Magnetic Torque

## Formal Definition

**Magnetic torque** is the rotational force exerted on a magnetic dipole (current loop, magnet, or magnetically charged particle) in a non-uniform [[Magnetic Field]]. It arises from the interaction between the magnetic moment of an object and the external magnetic field. For spacecraft, magnetic torque is a passive method for attitude control and stabilization, widely used in small satellites and CubeSats due to its simplicity, low cost, and minimal power requirements.

## Historical Development

### Key Milestones
- **1865:** James Clerk Maxwell develops full electromagnetic theory; predicts magnetic torque
- **1920s–1930s:** First theoretical analysis of satellite magnetic stabilization
- **1960s–1970s:** Early satellites employ magnetic damping for attitude control
- **1980s+:** Magnetic coils become standard for small spacecraft attitude control
- **2000s+:** CubeSat revolution popularizes magnetic torque as primary control method
- **Modern Era:** Machine learning optimizes magnetic control algorithms

### Foundational Contributors
1. **James Clerk Maxwell (1831–1879):** Theoretical prediction from electromagnetic theory
2. **Carl Friedrich Gauss (1777–1855):** Magnetic field characterization and dipole theory
3. **Hugh Alfvén (1908–1995):** Magnetohydrodynamics and space plasma physics
4. **Michail Gryzlov (1980s+):** Modern magnetic control theory and algorithms

## Mathematical Formulation

### Magnetic Torque on Dipole

**Torque on Magnetic Dipole:**
$$
\boldsymbol{\tau} = \boldsymbol{\mu} \times \mathbf{B}
$$

Where:
- $\boldsymbol{\mu}$: magnetic dipole moment (A·m²)
- $\mathbf{B}$: magnetic field (Tesla)
- $\times$: vector cross product

**Magnitude:**
$$
|\boldsymbol{\tau}| = \mu B \sin(\theta)
$$

Where $\theta$ is angle between dipole moment and field direction.

**Maximum torque:** When $\theta = 90°$ (perpendicular alignment)

### Magnetic Dipole Moment

**From Current Loop:**
$$
\mu = I \cdot A
$$

Where:
- $I$: current through loop (A)
- $A$: area enclosed by loop (m²)

**From Magnetized Material:**
$$
\boldsymbol{\mu} = \mathbf{M} \cdot V
$$

Where:
- $\mathbf{M}$: magnetization (A/m)
- $V$: volume (m³)

### Magnetic Field from Dipole

**Field due to magnetic dipole:**
$$
\mathbf{B}(\mathbf{r}) = \frac{\mu_0}{4\pi r^3}\left[3(\boldsymbol{\mu} \cdot \hat{\mathbf{r}})\hat{\mathbf{r}} - \boldsymbol{\mu}\right]
$$

On dipole axis ($\mathbf{r} \parallel \boldsymbol{\mu}$):
$$
B = \frac{\mu_0}{2\pi r^3} \mu
$$

## Spacecraft Applications

### Magnetic Attitude Control

**Three-Axis Control via Magnetic Coils:**

Spacecraft equipped with three orthogonal magnetic coils:
$$
\boldsymbol{\mu} = \mu_x \hat{\mathbf{x}} + \mu_y \hat{\mathbf{y}} + \mu_z \hat{\mathbf{z}}
$$

Each coil independently controlled to produce desired torque:
$$
\boldsymbol{\tau} = \boldsymbol{\mu} \times \mathbf{B}_{\text{Earth}}
$$

**Advantages:**
- No consumables (passive system)
- Low power: coils energized only as needed
- Highly reliable; simple electronics
- Scalable from small to medium satellites

**Disadvantages:**
- Torque depends on local magnetic field strength and orientation
- Field varies with orbit and geographic location
- Control authority limited by coil size and power

### Gravity Gradient Stabilization

**Magnetic enhancement of gravity gradient:**
$$
\boldsymbol{\tau}_{\text{mag}} = \boldsymbol{\mu} \times \mathbf{B}
$$

Combined with gravity gradient:
$$
\boldsymbol{\tau}_{\text{gg}} = 3\frac{\mu_0}{R^3}(\mathbf{I}_{xx} - \mathbf{I}_{yy}) \sin(\theta)\cos(\theta) \hat{\mathbf{z}}
$$

Magnetic torque can stabilize or destabilize depending on alignment.

### Active Magnetic Damping

**Eddy Current Damping:**

Conductor moving through magnetic field experiences:
$$
\mathbf{F}_{\text{Lorentz}} = q(\mathbf{v} \times \mathbf{B})
$$

For space applications with permanent magnets and conductive materials.

## Earth's Magnetic Field

### Geomagnetic Field Characteristics

**Dipole Model:**
$$
B_r = \frac{2\mu_0 m}{4\pi r^3} \cos(\lambda)
$$

Where:
- $m$: Earth's magnetic dipole moment (~7.9 × 10^15 A·m²)
- $r$: distance from Earth center
- $\lambda$: magnetic latitude

**Typical Field Strength:**
- Earth's surface: ~25–65 μT
- Low Earth Orbit (LEO): ~25–50 μT (varies with location)
- Geostationary orbit: ~1–5 μT

### Variation with Orbit

**Inclination Effects:**
- Equatorial orbit: Weaker field (~25 μT)
- Polar orbit: Stronger field (~60 μT at poles)
- Inclined orbit: Variable field throughout orbit

**Local Time Variation:**
- Field magnitude and direction change as satellite orbits
- Enables vector control in three dimensions

## Control System Design

### Linear Feedback Control

**Simple proportional control:**
$$
\boldsymbol{\mu} = -K \boldsymbol{\omega}
$$

Where:
- $K$: control gain (A·m²·s/rad)
- $\boldsymbol{\omega}$: angular velocity

**Torque:**
$$
\boldsymbol{\tau} = (-K\boldsymbol{\omega}) \times \mathbf{B} = -K(\boldsymbol{\omega} \times \mathbf{B})
$$

Provides damping proportional to angular rate.

### Quaternion-Based Control

**Attitude error represented by quaternion $\mathbf{q}_e$:**

Control law:
$$
\boldsymbol{\mu} = K_p \mathbf{q}_{e,v} - K_d (\boldsymbol{\omega} \times \mathbf{B})
$$

Where:
- $\mathbf{q}_{e,v}$: vector part of error quaternion
- $K_p, K_d$: proportional and derivative gains

### Constraints and Optimization

**Power Constraint:**
$$
P = I^2 R = \frac{\mu^2 R}{A^2}
$$

Higher dipole moment requires more power (quadratic scaling).

**Coil Design Trade-off:**
- Larger coil area $A$ → lower power for given moment
- Size/mass constraints
- Thermal dissipation limits

## Practical Implementation

### Magnetic Coil Design

**Single-Turn Rectangular Coil:**
$$
\mu = I \cdot A = I \cdot (L_1 \times L_2)
$$

**Multi-Turn Coil:**
$$
\mu = N \cdot I \cdot A
$$

Where $N$ is number of turns.

**Practical Range:** CubeSats typically 0.1–10 A·m² per axis.

### Control Hardware

**Magnetic Sensor (Magnetometer):**
- Measures local [[Magnetic Field]] in three axes
- Provides feedback for magnetic field vector

**Current Driver:**
- Supplies current to magnetic coils
- PWM (pulse-width modulation) control typical

**IMU (Inertial Measurement Unit):**
- Measures angular velocity
- Feedback for rate damping

## Relationship to Other Concepts

1. **Connection to [[Attitude Control]]:**
   - Passive (permanent magnet) or active (electromagnet) torque control
   - Alternative to reaction wheels or thrusters

2. **Connection to [[Spacecraft Attitude Dynamics]]:**
   - Rotational dynamics equation:
     $$\mathbf{I} \boldsymbol{\alpha} = \boldsymbol{\tau}_{\text{mag}} + \boldsymbol{\tau}_{\text{gravity gradient}} + \boldsymbol{\tau}_{\text{disturbance}}$$

3. **Connection to [[Magnetic Field]]:**
   - Fundamental to torque generation
   - Earth's field is the "actuator"

4. **Connection to [[Electromagnetism]]:**
   - Cross product of dipole moment and field
   - Derived from Lorentz force on moving charges

5. **Connection to [[Control Systems]]:**
   - Feedback control laws for attitude regulation
   - Non-linear control due to cross product

## Advantages and Limitations

### Advantages

| Aspect | Benefit |
|--------|---------|
| Power | Minimal power required (only coil resistance) |
| Cost | Inexpensive coils and drivers |
| Reliability | No moving parts; very reliable |
| Lifetime | No consumables; indefinite lifespan |
| Scalability | Works for small satellites (CubeSats) to medium |

### Limitations

| Aspect | Limitation |
|--------|-----------|
| Authority | Limited by field strength (~50 μT in LEO) |
| Controllability | Cannot generate torque parallel to field |
| Altitude | Weaker field at higher altitudes (geostationary) |
| Time-Variation | Field changes with orbit position |
| Performance | Slower response than reaction wheels |

## Applications and Examples

### CubeSats and Small Satellites

**Primary attitude control for CubeSats (1U–3U):**
- Replace reaction wheels for cost/power savings
- Magnetic coils standard actuators
- Ground magnetic field provides free actuation

**Example:** Dellingr CubeSat uses magnetic coils for 3-axis control

### Lunar and Deep Space

**Weaker at high altitude:**
- Magnetic control impractical beyond ~35,000 km
- Gravitational potential dominates
- Alternative methods required

### Deorbiting and Station-Keeping

**Passive deorbit:**
- Magnetic dipole induces eddy currents in conductive atmosphere
- Natural orbital decay
- Application: end-of-life deorbit of old satellites

## Advanced Control Techniques

### Model Predictive Control (MPC)

**Predicts future field:** Based on orbit propagation and Earth's magnetic model
$$
\min_{\boldsymbol{\mu}} \sum_{k=0}^{N} \left\|\mathbf{q}_k - \mathbf{q}_d\right\|^2 + \lambda \|\boldsymbol{\mu}_k\|^2
$$

Subject to constraints on dipole moment and power.

### Machine Learning Control

**Neural Networks:** Learn optimal control policies from simulations

**Advantages:** Handle model uncertainties and time-varying field

## See Also

- [[Attitude Control]]
- [[Spacecraft Attitude Dynamics]]
- [[Magnetic Field]]
- [[Electromagnetism]]
- [[Control Systems]]
- [[Torque]]
- [[ADCS]] (Attitude Determination and Control System)
- [[Spacecraft]]
- [[Gravity Gradient]]

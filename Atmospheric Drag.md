---
title: Atmospheric Drag
tags:
  - orbital mechanics
  - aerospace
  - satellite dynamics
  - atmospheric physics
---

# Atmospheric Drag

## Formal Definition

**Atmospheric drag** (also called aerodynamic drag or air resistance) is the [[Radiation|retarding force]] exerted by an [[Atmosphere|atmospheric medium]] on a body moving through it. For satellites and spacecraft in low Earth orbit (LEO), atmospheric drag represents the dominant perturbation force causing orbital decay. The drag force depends on atmospheric density (which varies exponentially with altitude), spacecraft [[Velocity|velocity]], cross-sectional area, and aerodynamic properties. Understanding atmospheric drag is critical for orbital mechanics, mission planning, [[Attitude Control|attitude control]], and predicting end-of-life reentry scenarios.

## Historical Development

### Key Milestones
- **1957:** Sputnik 1 launched; unexpected rapid orbital decay due to atmospheric drag
- **1960:** Explorer satellites reveal atmospheric density variations
- **1960s–1970s:** Empirical atmospheric models developed (CIRA, MSIS)
- **1970s–Present:** High-fidelity models incorporate solar activity, magnetic indices
- **1990s–Present:** Real-time atmospheric density monitoring via satellite drag
- **2000s–Present:** Machine learning techniques for improved drag coefficient prediction

### Foundational Contributors
1. **Sergei Korolev (1906–1966):** Soviet space program; first satellite, unexpected decay
2. **Luigi Broglio (1911–2001):** Italian satellite trajectory analysis
3. **David Vallado (1960–present):** Orbital mechanics; drag modeling standard references
4. **John Emmert (1965–present):** NRLMSISE-00 atmospheric model development

## Mathematical Formulation

### Drag Force Equation

**Standard drag force:**
$$
\mathbf{F}_D = -\frac{1}{2} \rho v^2 C_D A \hat{\mathbf{v}}
$$

Where:
- $\rho$: Atmospheric density at spacecraft altitude [kg/m³]
- $v = |\mathbf{v}|$: Spacecraft speed relative to atmosphere [m/s]
- $C_D$: Drag coefficient (dimensionless; typically 2–2.5)
- $A$: Cross-sectional area perpendicular to velocity [m²]
- $\hat{\mathbf{v}}$: Unit velocity vector (drag opposes motion)

**Drag force magnitude:**
$$
F_D = \frac{1}{2} \rho v^2 C_D A
$$

### Acceleration Due to Drag

**Drag-induced acceleration:**
$$
\mathbf{a}_D = -\frac{F_D}{m} = -\frac{C_D A}{2m} \rho v^2 \hat{\mathbf{v}}
$$

**Ballistic coefficient** (inverse of sensitivity to drag):
$$
B = \frac{m}{C_D A}
$$

**Rewritten:**
$$
\mathbf{a}_D = -\frac{\rho v^2}{2B} \hat{\mathbf{v}}
$$

**Physical interpretation:** 
- High $B$ (heavy, compact): Resists drag
- Low $B$ (light, large area): Strongly affected by drag

### Drag Coefficient

**Typical values:**

| Object Type | $C_D$ | Comments |
|---|---|---|
| Smooth sphere | 0.1 | Streamlined |
| Cube | 1.05 | Bluff body |
| Flat plate (perpendicular) | 1.28 | Maximum drag |
| Cylinder (side-on) | 1.1–1.3 | Axis-dependent |
| Satellite (typical) | 2.0–2.5 | Configuration-dependent |
| Rocket body | 0.3–0.5 | Streamlined |

**Hypersonic regime** ($M > 5$):
- Free molecular flow dominates (molecules scatter individually)
- $C_D \approx 2.0–2.5$ (relatively constant)
- Temperature jump, accommodation coefficients matter

**Physical basis:** 
- Pressure drag (form drag): 50–90% of total
- Skin friction drag: 10–50% of total

### Altitude-Dependent Atmospheric Density

**Exponential model (simple):**
$$
\rho(h) = \rho_0 \exp\left(-\frac{h - h_0}{H}\right)
$$

Where:
- $\rho_0$: Reference density at $h_0$ (often sea level)
- $H$: Scale height (~7 km for Earth lower atmosphere; ~60 km for thermosphere)
- $h$: Altitude above surface

**Thermospheric scale height** (~80–500 km):
$$
H \approx 60 \text{ km} (200 \text{ K}) \text{ to } 100 \text{ km} (1000 \text{ K})$$

Hotter atmosphere → larger $H$ → larger density at fixed altitude.

## Orbital Decay

### Orbital Perturbation Equations

**Gauss planetary equations** (drift due to drag):
$$
\frac{da}{dt} = -\frac{2a^2}{L} a_D \sin(\text{true anomaly})
$$

Where:
- $a$: Semi-major axis
- $L$: Angular momentum per unit mass
- $a_D$: Drag acceleration

**Simplified circular orbit:**
$$
\frac{da}{dt} \approx -\frac{\rho v^2 C_D A}{2m}
$$

For circular orbit: $v \approx \sqrt{GM/a}$

$$
\frac{da}{dt} = -\frac{C_D A \rho}{2m} \sqrt{\frac{GM}{a}}
$$

### Decay Time (Lifetime)

**Characteristic decay timescale:**
$$
\tau \approx \frac{2m}{\rho C_D A \sqrt{GM/a}}
$$

Alternatively using ballistic coefficient:
$$
\tau \approx \frac{2aB}{\rho \sqrt{GMa}}
$$

**For typical satellite (300 km altitude):**
- $\rho \approx 10^{-9}$ kg/m³
- $a \approx 6.678 \times 10^6$ m
- $B \sim 100$ kg/m² (typical)
- $\tau \sim 10^5$ seconds $\approx 1$ day to weeks

**For higher altitudes (ISS at 400 km):**
- Density higher; decay faster (~few years)
- Requires periodic reboosts

### Decay Across Orbit

**Apsidal damping:** Perigee lower than apogee due to drag.

**Result:** Elliptical orbit circularizes; then decays uniformly in circular orbit.

**Reentry:** Occurs when altitude drops to ~80 km (thermosphere heating intense).

## Atmospheric Models

### MSIS Model (NRLMSISE-00)

**Inputs:**
- Date (solar activity varies 11-year cycle)
- Geographic latitude/longitude
- Local solar time
- Geomagnetic indices (Ap, Kp)

**Outputs:** Density, temperature, composition (N₂, O₂, He, H, O)

**Accuracy:** ±15% typical; ±100% in extreme conditions.

**Application:** Most widely used for satellite operations.

### Jacchia Model

**High-fidelity thermospheric model:**
- Temperature profile with altitude
- Composition gradients
- Temperature anomalies above geomagnetic disturbances

**Refinements:** Incorporates solar flux variations (F10.7 index).

### Drag Calculation Pipeline

1. **Get satellite state:** Position, velocity
2. **Compute altitude:** $h = r - R_E$
3. **Retrieve atmospheric density:** From model (date, geomagnetic activity)
4. **Compute relative velocity:** $\mathbf{v}_{\text{rel}} = \mathbf{v} - \mathbf{v}_{\text{wind}}$
5. **Compute drag acceleration:** $\mathbf{a}_D = -\frac{1}{2m}\rho v^2 C_D A \hat{\mathbf{v}}$
6. **Integrate equations of motion:** Update orbit over time

## Variations and Complexities

### Atmospheric Density Variations

**Solar cycle (11 years):**
- Solar maximum: Thermosphere expands; density increases ~2×
- Solar minimum: Contracted atmosphere; lower density

**Geomagnetic storms:**
- Sudden heating; density surge
- Satellites experience sudden orbital decay
- Ex: March 2022 Starlink collision with atmosphere

**Seasonal variations:**
- Asymmetry: Northern/Southern hemisphere
- Semi-annual oscillation in thermospheric scale height

**Diurnal variations:**
- Sun-facing hemisphere warmer
- Density gradients; affects drag anisotropy

### Spacecraft Properties

**Orientation effects:**
- Solar panels extended: Large cross-section; high drag
- Solar panels folded: Reduced cross-section; low drag

**Area-to-mass ratio ($A/m$):**
- Critical parameter; proportional to drag sensitivity
- Lightweight structures (solar sails): Extreme drag sensitivity
- Heavy dense objects: Drag-resistant

**Density layering within spacecraft:**
- Center of pressure may differ from center of mass
- Torques on spacecraft possible; tumbling

### Atmospheric Wind

**Relative velocity:**
$$
\mathbf{v}_{\text{rel}} = \mathbf{v}_{\text{orbit}} - \mathbf{v}_{\text{wind}}$$

**Atmospheric winds in thermosphere:**
- ~50–150 m/s typical
- Can reduce or enhance drag depending on direction
- Tidal winds, gravity waves

**Effect:** ±20% variation in drag for satellite trajectories.

## Applications and Consequences

### Satellite Lifetime Prediction

**Operational constellation:** Account for decay when planning decommissioning.

**Debris tracking:** Old satellites/debris decay; requires continuous updates.

**Reentry prediction:** When will satellite reenter? Where? When?

### Orbital Reboost

**ISS:** Reboost ~3–4 times/year to maintain 400 km altitude
- Uses Progress spacecraft or other supply vehicles
- Compensates atmospheric drag

**Cost:** Fuel, launch vehicle resources.

**Alternatives:** Electric propulsion (ion thrusters); more efficient at low thrust.

### End-of-Life Disposal

**Compliance:** Spacecraft must deorbit within 25 years (debris mitigation guidelines).

**Methods:**
1. **Natural decay:** Passive; slow
2. **Controlled deorbit:** Active; predictable reentry
3. **Transfer to graveyard orbit:** For GEO (not subject to drag)

### Solar Sail Concept

**Extreme drag sensitivity:**
- $A/m$ ratio very large (lightweight, large reflecting surface)
- Drag can provide propulsion (paradoxically!)
- Acceleration: $a = \frac{P}{2c} \times \frac{A}{m}$ (radiation pressure)

**If in low atmosphere:** Atmospheric drag competing with radiation pressure.

## Reentry Physics

### Reentry Corridor

**Reentry occurs when:** Altitude drops to ~80–120 km (thermosphere).

**Heat rate explosion:**
- Drag deceleration: ~$g$ or higher
- Kinetic energy converted to heat
- Vehicle glows brightly (fireball); visible to ground observers

**Plasma formation:** Air ionizes around vehicle; creates radio blackout.

### Reentry Corridor Width

**Too shallow:** Ricochet off atmosphere; orbit remains high.

**Too steep:** Extreme deceleration; breakup risk.

**Optimal corridor:** ~1–2° of entry angle.

### Ballistic Reentry

**Uncontrolled (most debris):**
- Vehicle tumbles; random orientation
- Unpredictable breakup altitude
- Landing zone: 200–400 km downrange from final orbit

**Controlled (capsules, Soyuz):**
- Oriented retrograde
- Heat shield protects
- Parachute deployment
- Precision landing

## Connection to Other Concepts

1. **Connection to [[Orbital Mechanics]]:**
   - Primary perturbation force in LEO
   - Modifies orbit over days/weeks

2. **Connection to [[Atmosphere]]:**
   - Density model critical input
   - Temperature determines thermospheric properties

3. **Connection to [[Aerodynamics]]:**
   - Drag coefficient empirical/experimental
   - Free molecular flow regime

4. **Connection to [[Attitude Control]]:**
   - Affects spacecraft orientation
   - Torques from non-uniform drag

5. **Connection to [[Orbital Decay]] and debris dynamics:**
   - Mechanism for satellite end-of-life
   - Debris mitigation strategy

## Practical Considerations

### Conjunction Assessment

**Satellite collision risk:**
- Drag uncertainty affects predicted position
- Conjunction prediction uncertainty grows
- Mitigation maneuvers planned if $P_c > 10^{-4}$

### Tracking and Navigation

**Ground-based radar/optical:** Update satellite states continuously.

**Two-line elements (TLE):** Decay rate embedded in mean motion.

**Propagation:** Tools like SGP4 (Simplified General Perturbations) account for drag.

### Solar Activity Impact

**F10.7 solar flux index:**
- Correlates with thermospheric density
- Predicted 11-year in advance with uncertainty

**Geomagnetic index (Ap, Kp):**
- Real-time feedback
- Allows drag updates within hours

## See Also

- [[Orbital Mechanics]]
- [[Atmosphere]]
- [[Aerodynamics]]
- [[Orbital Decay]]
- [[Satellite Dynamics]]
- [[Reentry]]
- [[Propulsion]]
- [[Attitude Control]]
- [[Space Debris]]
- [[Thermosphere]]

## Formal Definition

An **Orbital [[Inclination]] Change** (or plane change) is an orbital maneuver performed to change the angle of an orbiting body's momentum vector relative to a reference plane (e.g., the [[equatorial plane]] or the ecliptic). Unlike maneuvers that change the size or shape of an orbit, a pure [[Inclination]] change rotates the [[orbital plane]] around the line of nodes without altering the [[Semi-Major Axis]], [[Eccentricity]], or [[Argument of Periapsis]]. This maneuver is notoriously energy-intensive, as it requires changing the direction of the spacecraft's velocity vector rather than just its magnitude.



## Historical Development

### Key Milestones
- **1950s:** Mathematical formalization during the early Cold War for satellite placement in polar and Sun-synchronous orbits.
- **1963:** Launch of Syncom 2, the first satellite to successfully perform significant plane changes to achieve a [[geosynchronous orbit]].
- **1960s-70s:** Development of the "Dog-leg" maneuver during launch to minimize the $\Delta v$ penalty for high-[[inclination]] launches from low-[[Geographic Latitude]] sites (e.g., Cape Canaveral).

### Foundational Contributors
1. **Samuel Herrick (1911–1974):** Pioneer in astrodynamics who formalized the coordinate transformations and perturbative math required for plane changes.
2. **P.R. Escobal:** Author of *Methods of Orbit Determination*, providing the classical geometric derivations for efficient plane changes.

## Mathematical Formulation

### General Form
For a [[circular orbit]], the velocity change ($\Delta v_i$) required to change the [[inclination]] by an angle $\Delta i$ is given by the Law of Cosines. If the initial and final velocities are equal in magnitude ($v_i = v_f = v$):

$$
\Delta v_i = 2 v \sin\left(\frac{\Delta i}{2}\right)
$$

### Component Breakdown
- **$v$:** The orbital velocity at the point where the maneuver is performed.
- **$\Delta i$:** The desired change in [[inclination]] angle (in radians).
- **Thrust Direction:** To perform a pure [[inclination]] change, the thrust must be applied perpendicular to the [[Orbital Plane]] (Normal or Anti-Normal direction).

### Special Cases
1. **Combined Maneuver:** When changing both the orbit size (velocity magnitude) and [[inclination]] simultaneously, the $\Delta v$ is:
   $$
   \Delta v = \sqrt{v_i^2 + v_f^2 - 2 v_i v_f \cos(\Delta i)}
   $$

## Fundamental Principles

### Core Assumptions
1. **[[Impulsive Maneuver]]:** The burn is instantaneous.
2. **Node Constraints:** The maneuver must occur at the **ascending node** or **descending node** (the points where the current and target planes intersect). Firing elsewhere will change the [[Geographic Longitude]] of the Ascending Node ($\Omega$) as well.
3. **Rigid Plane:** Assumes the central body is a point mass and does not account for nodal regression caused by $J_2$ effects during the burn.

### Governing Laws
- **[[Conservation of Angular Momentum]]:** The maneuver changes the *direction* of the [[Angular Momentum]] vector $\vec{h}$ without changing its magnitude (in the case of a pure change).
- **Vector Addition:** The resulting $\Delta v$ is the vector difference between the initial velocity vector and the final velocity vector.

## Theoretical Framework

### The "Cost" of Plane Changes
Because $v$ is a multiplier in the $\Delta v_i$ equation, the cost of a plane change increases as the spacecraft gets closer to the central body (where $v$ is highest). 
- **Efficiency Strategy:** It is most efficient to perform [[inclination]] changes at the **[[apoapsis]]** (highest altitude), where the velocity $v$ is at its minimum.



## Physical Interpretation

### Geometric Meaning
Imagine a spinning bicycle wheel. To change its [[inclination]], you must apply a force perpendicular to its rotation. The "stiffer" the rotation (higher velocity), the more force is required to tilt the axis. In orbit, the spacecraft's high velocity creates immense "gyroscopic" stability that must be overcome by the rocket engine.

## Advantages and Limitations

### Strengths
1. **Mission Flexibility:** Allows satellites launched from any [[Geographic Latitude]] to reach specific targets like Geostationary ($0^\circ$) or Polar ($90^\circ$) orbits.
2. **Combined Efficiency:** Performing a plane change during a [[Hohmann Transfer]]'s second burn (at [[apoapsis]]) is significantly cheaper than doing them separately.

### Weaknesses
1. **Extreme Fuel Consumption:** A $90^\circ$ plane change requires a $\Delta v$ greater than the orbital velocity itself ($\approx 1.41 \times v$).
2. **Strict Timing:** Can only be performed at the line of nodes; missing this window requires waiting for half an [[orbital period]].

## Applications

### Engineering Disciplines
1. **Geostationary Satellites:** Changing from a launch-site [[inclination]] (e.g., $28.5^\circ$ for Kennedy Space Center) to $0^\circ$ at the circularization burn.
2. **Spy Satellites:** Transitioning to polar orbits to ensure global coverage.
3. **Lunar/Interplanetary Missions:** Aligning the spacecraft's plane with the Moon or a target planet's [[orbital plane]].

## See Also

- [[Keplerian Parameters]]
- [[Hohmann Transfer]]
- [[Specific Orbital Energy]]
- [[Standard Gravitational Parameter]]
- [[Bi-elliptic Transfer]] (often used for high-[[inclination]] changes)

## Recommended Tags:
#orbital-mechanics #astrodynamics #plane-change #delta-v #spaceflight #vector-calculus
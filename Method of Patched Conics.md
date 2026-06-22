#Orbital-Mechanics #DONE 
## Formal Definition

The **Patched Conics Method** is an analytical approximation used in astrodynamics to simplify the complex N-body problem of interplanetary travel into a series of linked two-body problems. This method divides a spacecraft's trajectory into distinct segments, or "patches," where only one dominant gravitational body is considered at a time. By treating the transition between these segments as instantaneous at the boundary of a planet's **[[Sphere of Influence]] (SOI)**, mission designers can use the relatively simple conic section equations (ellipses, hyperbolas, etc.) to calculate highly complex orbital transfers.



## Historical Development

### Key Milestones
- **17th-18th Century:** Johannes Kepler and Isaac Newton establish the laws of two-body motion ([[Conic Sections]]).
- **1950s:** The method is formalized as a standard engineering tool for early lunar and interplanetary mission planning.
- **1961:** Michael Minovitch uses patched conics at JPL to discover the potential for gravity assists (the "Grand Tour").
- **1960s:** NASA's Apollo program utilizes patched conics for rapid trajectory analysis during mission design for lunar transitions.

### Foundational Contributors
1. **Michael Minovitch (1935–present):** Revolutionized the use of the method for multi-planet [[Gravity Assist]] trajectories.
2. **Archie Roy (1924–2012):** Provided extensive academic formalization of the "patched" transition logic in celestial mechanics.

## Mathematical Formulation

### The Three Phases
A typical interplanetary transfer (e.g., Earth to Mars) is broken down as follows:

1.  **Phase 1: Departure (Planet-centric):**
    The spacecraft starts in a [[Hyperbolic Trajectory]] relative to the departure planet.
    $$v_{p1}^2 = v_{esc}^2 + v_{\infty, dep}^2$$
2.  **Phase 2: Cruise (Heliocentric):**
    Once the spacecraft reaches the SOI, it is "patched" into a heliocentric [[elliptical orbit]] (often a [[Hohmann Transfer]]).
    $$\vec{V}_{sc/sun} = \vec{V}_{planet/sun} + \vec{v}_{\infty, dep}$$
3.  **Phase 3: Arrival (Planet-centric):**
    Upon entering the target planet's SOI, the craft is treated as being in a hyperbolic approach relative to that planet.

### Boundary Condition
The "patch" occurs at the radius of the [[Sphere of Influence]] ($r_{SOI}$):
$$r_{SOI} = a \left( \frac{m}{M} \right)^{2/5}$$

## Fundamental Principles

### Core Assumptions
1. **Point-Mass Dominance:** Assumes only one gravitational body affects the spacecraft at any given time.
2. **Instantaneous Transition:** The hand-off between the planetary frame and the heliocentric frame occurs at a single point (the SOI boundary).
3. **Negligible Mass:** The spacecraft has no gravitational effect on the planets or the Sun.

### Governing Laws
- **Vis-viva Equation:** Used to calculate velocities at every point along the conic segments.
- **[[Conservation of Energy]]:** [[Specific Orbital Energy]] is conserved within each individual two-body segment, but changes relative to the Sun when the frame is switched.

## Theoretical Framework

### Coordinate Frame Switching
The core of the method is the vector addition of velocities at the SOI boundary. Because the spacecraft is "far" from the planet relative to the planet's size, its velocity relative to the planet is effectively its **[[Hyperbolic Excess Velocity]]** ($v_\infty$). By adding the planet's orbital velocity vector to the spacecraft's $v_\infty$ vector, we obtain the spacecraft's velocity relative to the Sun.



## Physical Interpretation

### The "Chain of Conics"
Imagine an interplanetary mission as a relay race. Earth "carries" the spacecraft on a hyperbolic path and hands the baton to the Sun at the SOI boundary. The Sun carries it along an elliptical arc to Mars's SOI, where Mars takes over for the final hyperbolic arrival. The Patched Conics method is the set of rules for how that "baton" (the velocity vector) is passed from one "runner" (gravitational body) to the next.

## Advantages and Limitations

### Strengths
1. **Analytical Solutions:** Does not require a supercomputer; can be solved with a scientific calculator or simple script.
2. **Rapid Iteration:** Allows mission designers to scan thousands of possible launch dates and arrival times (C3 porkchop plots) very quickly.

### Limitations
1. **Accuracy:** Ignores the "Third-Body" effect (the Sun's gravity while inside a planet's SOI), leading to errors of roughly 1–5% in $\Delta v$ requirements.
2. **Small SOI:** The approximation is less accurate for bodies with small SOIs or when trajectories pass near [[Lagrange Points]].

## Applications

### Engineering Disciplines
- **Interplanetary Mission Design:** Initial sizing of propellant tanks and launch vehicle selection.
- **Porkchop Plots:** Visualizing launch windows by calculating $v_\infty$ for various dates using patched conics.

### Practical Implementations
- **Voyager 1 & 2:** Initial trajectories were mapped using patched conics before being refined with high-fidelity numerical integrators.
- **Mars Rovers:** All NASA Mars missions use patched conics for the preliminary "interplanetary cruise" design phase.

## See Also

- [[Sphere of Influence]]
- [[Hyperbolic Excess Velocity]]
- [[Hohmann Transfer]]
- [[Energy Law (Vis-Viva Equation)]]
- [[Standard Gravitational Parameter]]

## Recommended Tags:
#orbital-mechanics #astrodynamics #patched-conics #spaceflight #interplanetary #physics #trajectory-optimization
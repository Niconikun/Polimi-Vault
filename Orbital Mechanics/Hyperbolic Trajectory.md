#Orbital-Mechanics #TBD 
## Formal Definition

A **Hyperbolic Orbit** is an unbound, open trajectory where the [[Eccentricity]] ($e$) is strictly greater than 1. In celestial mechanics, it represents the path of an object that has a velocity greater than the [[Escape Velocity]] of a central body at every point along its path. Instead of orbiting the central body, the object approaches from "infinity," reaches a point of closest approach ([[Periapsis]]), and then departs toward infinity, retaining a non-zero velocity ($v_\infty$). 



## Historical Development

### Key Milestones
- **1687:** Isaac Newton proves in the *Principia* that a $1/r^2$ force law allows for trajectories in the shape of any conic section, including hyperbolas.
- **1959:** Luna 1 becomes the first human-made object to achieve a heliocentric hyperbolic orbit after escaping Earth's gravity.
- **1970s:** The Voyager missions utilize hyperbolic "swing-bys" (Gravity Assists) to move from one planet to the next.
- **2017:** 'Oumuamua is discovered; its high [[Eccentricity]] ($e \approx 1.2$) confirms it is the first observed interstellar object on a hyperbolic trajectory through our solar system.

### Foundational Contributors
1. **Isaac Newton (1642–1727):** Mathematically unified closed (elliptical) and open (hyperbolic) celestial motion.
2. **Leonhard Euler (1707–1783):** Developed the analytical geometry and Lambert’s problem solutions applicable to hyperbolic arcs.

## Mathematical Formulation

### General Form
The distance $r$ as a function of the [[True Anomaly]] $\nu$ is:
$$r = \frac{a(e^2 - 1)}{1 + e \cos \nu}$$
*(Note: For hyperbolas, $a$ is often defined as negative, representing the distance from the center to the vertex.)*

### Energy and Velocity
The [[Specific Orbital Energy]] ($\mathcal{E}$) is positive:
$$\mathcal{E} = \frac{v^2}{2} - \frac{\mu}{r} = \frac{\mu}{2a} > 0$$

The velocity at "infinity" ([[Hyperbolic Excess Velocity]]) is:
$$v_\infty = \sqrt{\frac{\mu}{a}}$$

### Turning Angle ($\delta$)
The total angle by which the spacecraft's path is deflected is:
$$\sin\left(\frac{\delta}{2}\right) = \frac{1}{e}$$

## Fundamental Principles

### Core Assumptions
1. **$v > v_{esc}$:** The spacecraft’s [[Kinetic Energy]] exceeds its [[potential energy]] at all times.
2. **Unbound State:** The object is not gravitationally "captured"; it is merely "deflected" by the central body.

### Governing Laws
- **[[Conservation of Angular Momentum]]:** The trajectory remains in a constant plane.
- **Hyperbolic Geometry:** The trajectory follows the path between two asymptotes that intersect at the center of the hyperbola.

## Theoretical Framework

### The Hyperbolic Anomaly ($H$)
Just as ellipses use the [[Eccentric Anomaly]] ($E$), hyperbolas use the **Hyperbolic Anomaly** ($H$) to relate time to [[position]]. The hyperbolic version of Kepler’s Equation is:
$$M = e \sinh H - H$$
Where $M$ is the [[Mean Anomaly]]. This is used to solve for the time of flight between two points on the hyperbolic arc.



## Physical Interpretation

### The Interstellar "Vagabond"
A hyperbolic orbit is the "one-way street" of space. It characterizes any object that is passing through a system rather than being a part of it. In mission design, every interplanetary departure starts as a hyperbolic orbit relative to the home planet.

## Advantages and Limitations

### Strengths
1. **Efficiency:** High-velocity hyperbolic approaches are the basis for the **[[Oberth Effect]]**, where maneuvers are most efficient at [[periapsis]].
2. **Interstellar Travel:** The only conic section that allows for a total exit from a star system's influence.

### Limitations
1. **High $\Delta v$ Requirement:** Capturing into a closed orbit from a hyperbolic approach requires a significant retrograde burn to shed excess energy.
2. **Brief Encounter:** Objects on hyperbolic paths spend very little time near the central body, limiting the window for scientific observation.

## Applications

### Engineering Disciplines
1. **Interplanetary Departure/Arrival:** All "escape" trajectories are hyperbolic.
2. **Gravity Assists:** Using a planet's gravity to "bend" a hyperbolic path to change a spacecraft's heliocentric velocity.
3. **Planetary Defense:** Modeling the trajectories of incoming high-velocity comets or asteroids.

## See Also

- [[Hyperbolic Excess Velocity]]
- [[Escape Velocity]]
- [[Gravity Assist]]
- [[Energy Law (Vis-Viva Equation)]]
- [[Sphere of Influence]]

## Recommended Tags:
#orbital-mechanics #astrodynamics #hyperbolic-orbit #interstellar #spaceflight #conic-sections #physics
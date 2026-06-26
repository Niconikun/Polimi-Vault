## Formal Definition

A **Gravity Assist** is a spaceflight maneuver in which a spacecraft utilizes the relative movement and gravity of a planet or other celestial body to alter its path and speed. By entering and exiting the "[[Sphere of Influence]]" of a moving planet, the spacecraft exchanges momentum with the body. From the perspective of the planet, the spacecraft's speed is unchanged (elastic encounter), but from the perspective of the Sun (the heliocentric frame), the spacecraft can gain or lose significant velocity and change its orbital [[inclination]] without expending propellant. 

## Historical Development

### Key Milestones
- **1918:** Yuri Kondratyuk suggests in "To Whomsoever Will Read" that a spacecraft could use the gravity of celestial bodies for [[acceleration]]/deceleration.
- **1959:** The Soviet Luna 3 mission uses a gravity assist from the Moon to return to Earth's vicinity to transmit photos of the lunar far side.
- **1961:** Michael Minovitch, a UCLA graduate student working at JPL, mathematically proves that gravity assists can be used for interplanetary travel, particularly for the "Grand Tour" of the outer planets.
- **1973:** Mariner 10 becomes the first mission to use a gravity assist (Venus) to reach another planet (Mercury).

### Foundational Contributors
1. **Michael Minovitch (1935–present):** Recognized for the mathematical discovery that a planet's orbital velocity could be "tapped" to propel a spacecraft.
2. **Giuseppe 'Bepi' Colombo (1920–1984):** Proposed the specific maneuvers that allowed Mariner 10 to make multiple flybys of Mercury using Venus.
3. **Yuri Kondratyuk (1897–1942):** Early theorist who proposed the concept of using a moon's gravity for orbital capture and return.

## Mathematical Formulation

### General Form
The change in the spacecraft's heliocentric velocity ($\Delta V$) is derived from the vector difference between the inbound and outbound hyperbolic excess velocities relative to the Sun.

### Component Breakdown
Let $\vec{V}_p$ be the orbital velocity of the planet and $\vec{v}_{\infty}$ be the velocity of the spacecraft relative to the planet at infinity.
- **Inbound Velocity:** $\vec{V}_1 = \vec{V}_p + \vec{v}_{\infty, in}$
- **Outbound Velocity:** $\vec{V}_2 = \vec{V}_p + \vec{v}_{\infty, out}$

The maximum possible change in speed ($\Delta V_{max}$) occurs when the spacecraft's path is turned by an angle $\delta$:
$$
\Delta V = 2v_{\infty} \sin\left(\frac{\delta}{2}\right)
$$
Where the turn angle $\delta$ is related to the [[Eccentricity]] $e$ of the flyby hyperbola:
$$
\sin\left(\frac{\delta}{2}\right) = \frac{1}{e} = \frac{1}{1 + \frac{r_p v_{\infty}^2}{\mu}}
$$

### Results of the Maneuver
1. **Trailing Edge Flyby:** Passing "behind" the planet in its orbit adds the planet's orbital velocity to the spacecraft, increasing its heliocentric energy.
2. **Leading Edge Flyby:** Passing "in front" of the planet in its orbit subtracts velocity from the spacecraft, decreasing its heliocentric energy (used to go "inward" toward the Sun).

## Fundamental Principles

### Core Assumptions
1. **Patched Conics:** The maneuver is modeled by treating the spacecraft as being solely under the influence of the planet while inside [[Sphere of Influence|its Sphere of Influ]]ence (SOI).
2. **Elastic Collision:** The planet's mass is so large compared to the spacecraft that its own orbit is negligibly affected.
3. **Energy Conservation:** Specific mechanical energy is conserved in the planet-centered (planetocentric) frame, but not in the Sun-centered (heliocentric) frame.

### Governing Laws
- **Conservation of Momentum:** The spacecraft gains momentum that is lost by the planet (though the planet's change is infinitesimal).
- **Hyperbolic Trajectories:** The spacecraft must follow a hyperbolic path relative to the assisting body to ensure it escapes the body's gravity after the encounter.

## Physical Interpretation

### Momentum Exchange
Think of a tennis ball bouncing off a moving train. If the ball is thrown at the train, it bounces back with its original speed plus twice the speed of the train. The "Gravity Assist" is the gravitational equivalent of this "bounce." Instead of a physical collision, the spacecraft's trajectory is bent by the planet's gravity.

## Advantages and Limitations

### Strengths
1. **Propellant Savings:** Allows missions to reach the outer [[solar system]] that would otherwise require rockets larger than currently possible.
2. **Speed Generation:** Necessary for reaching high-velocity escape trajectories (e.g., New Horizons to Pluto).
3. **Braking:** Essential for missions to Mercury or the Sun to "shed" Earth's orbital velocity.

### Weaknesses
1. **Launch Windows:** Depends entirely on the alignment of the planets (e.g., the Voyager "Grand Tour" window only opens once every 175 years).
2. **Increased Flight Time:** Often requires "looping" around the inner [[solar system]] for several years to gain enough energy for the outer [[solar system]].
3. **Navigation Precision:** Small errors in the approach altitude ([[Periapsis]]) are magnified into massive errors in the departure trajectory.

## Applications

### Engineering Disciplines
- **Interplanetary Navigation:** Calculating "Multi-Body" trajectories.
- **Deep Space Network (DSN) Tracking:** Crucial for monitoring the spacecraft during the critical flyby period.

### Practical Implementations
- **Voyager 1 & 2:** Used Jupiter, Saturn, Uranus, and Neptune to exit the [[solar system]]. 
- **Cassini-Huygens:** Used four gravity assists (Venus, Venus, Earth, Jupiter) to reach Saturn.
- **Parker Solar Probe:** Uses seven flybys of Venus over seven years to gradually lower its perihelion closer to the Sun.

## See Also

- [[Standard Gravitational Parameter]]
- [[Specific Orbital Energy]]
- [[Oberth Effect]] (Often combined: a "Powered Gravity Assist")
- [[Hyperbolic Excess Velocity]]
- [[Sphere of Influence]]

## Recommended Tags:
#orbital-mechanics #astrodynamics #gravity-assist #spaceflight #interplanetary #physics #momentum-exchange
## Formal Definition

The **Hohmann Transfer Orbit** is an [[elliptical orbit]] used to transfer a spacecraft between two circular orbits of different radii in the same plane. It represents the most energy-efficient maneuver (lowest $\Delta v$) for transferring between two coplanar circular orbits sharing a common focus, provided the ratio of the final to initial semi-major axes is less than approximately 11.94. The maneuver consists of two impulsive velocity changes tangent to the spacecraft's path: one to enter the transfer ellipse and a second to circularize at the destination.

## Historical Development

### Key Milestones
- **1925:** Walter Hohmann publishes "Die Erreichbarkeit der Himmelskörper" (The Attainability of Celestial Bodies), outlining the fuel-optimal nature of the transfer.
- **1959:** First successful application during the Soviet Luna 3 mission (conceptually related, though strictly a flyby trajectory).
- **1962:** NASA's Mariner 2 uses a Hohmann-like trajectory to reach Venus.
- **1960s-Present:** Becomes the standard maneuver for geostationary satellite placement (GTO to GEO) and interplanetary missions (e.g., Earth to Mars).

### Foundational Contributors
1. **Walter Hohmann (1880–1945):** German civil engineer who first derived the mathematical principles of the transfer.
2. **Ary Sternfeld (1905–1980):** Independently calculated optimal trajectories and later introduced the [[Bi-elliptic Transfer]] as a more efficient alternative for high-ratio orbits.

## Mathematical Formulation

### General Form
The transfer relies on the **Vis-viva equation**, which relates the velocity $v$ of a body to its position $r$ and [[Semi-Major Axis]] $a$:

$$
v^2 = \mu \left( \frac{2}{r} - \frac{1}{a} \right)
$$
where $\mu = GM$ is the [[Standard Gravitational Parameter]] of the central body.

### Component Breakdown
The total velocity change ($\Delta v_{\text{total}}$) is the sum of two impulses:
1. **$\Delta v_1$:** Burn to leave the initial [[circular orbit]] ($r_1$) and enter the transfer ellipse.
2. **$\Delta v_2$:** Burn to leave the transfer ellipse and enter the final [[circular orbit]] ($r_2$).

$$
\Delta v_{\text{total}} = |\Delta v_1| + |\Delta v_2|
$$

### Orbital Elements of the Transfer Ellipse
Assuming a transfer from a smaller orbit $r_1$ to a larger orbit $r_2$:
- **Perigee distance:** $r_p = r_1$
- **Apogee distance:** $r_a = r_2$
- **[[Semi-Major Axis]] of transfer:**
  $$
  a_{\text{trans}} = \frac{r_1 + r_2}{2}
  $$

## Derivation and Proof

### Step-by-Step Derivation

**1. First Impulse ($\Delta v_1$):**
The spacecraft is initially in a [[circular orbit]] with velocity $v_{c1} = \sqrt{\mu/r_1}$. It must accelerate to the [[periapsis]] velocity of the transfer ellipse $v_{p,\text{trans}}$.

$$
v_{p,\text{trans}} = \sqrt{\mu \left( \frac{2}{r_1} - \frac{1}{a_{\text{trans}}} \right)} = \sqrt{\frac{\mu}{r_1}} \sqrt{\frac{2r_2}{r_1 + r_2}}
$$

The required delta-v is:
$$
\Delta v_1 = v_{p,\text{trans}} - v_{c1} = \sqrt{\frac{\mu}{r_1}} \left( \sqrt{\frac{2r_2}{r_1 + r_2}} - 1 \right)
$$

**2. Second Impulse ($\Delta v_2$):**
The spacecraft arrives at the [[apoapsis]] of the transfer ellipse with velocity $v_{a,\text{trans}}$. It must accelerate to the circular velocity of the destination orbit $v_{c2} = \sqrt{\mu/r_2}$.

$$
v_{a,\text{trans}} = \sqrt{\mu \left( \frac{2}{r_2} - \frac{1}{a_{\text{trans}}} \right)} = \sqrt{\frac{\mu}{r_2}} \sqrt{\frac{2r_1}{r_1 + r_2}}
$$

The required delta-v is:
$$
\Delta v_2 = v_{c2} - v_{a,\text{trans}} = \sqrt{\frac{\mu}{r_2}} \left( 1 - \sqrt{\frac{2r_1}{r_1 + r_2}} \right)
$$

## Fundamental Principles

### Core Assumptions
1. **[[Impulsive Maneuver]]:** Velocity changes are instantaneous (burn time is negligible compared to [[orbital period]]).
2. **Coplanar Orbits:** Initial and final orbits lie in the same plane ($\Delta i = 0$).
3. **[[Two-Body Problem]]:** Only the gravitational force of the central body is considered; perturbations are ignored.
4. **Tangential Burns:** Thrust vectors are parallel to the velocity vector to maximize energy change efficiency.

### Governing Laws
- **[[Conservation of Energy]]:** Specific mechanical energy dictates the [[Semi-Major Axis]] size.
- **[[Conservation of Angular Momentum]]:** Determines velocity variations at apogee and perigee relative to distance.

## Physical Interpretation

### Geometric Meaning
The Hohmann transfer is an ellipse that is *tangent* to both the initial and final circular orbits. The transfer periapsis touches the inner orbit, and the transfer [[apoapsis]] touches the outer orbit. This tangency ensures the velocity vectors are aligned, minimizing the need for steering losses.

### Energy Considerations
- **Minimum Energy:** For $r_2/r_1 < 11.94$, the Hohmann transfer requires the least [[Kinetic Energy]] change.
- **[[Oberth Effect]]:** The first burn takes advantage of the [[Oberth Effect]] by occurring at the point of highest velocity (periapsis relative to the transfer orbit), maximizing the [[Specific Orbital Energy]] gain per unit of fuel.

## Advantages and Limitations

### Strengths
1. **Fuel Efficiency:** Minimal $\Delta v$ required for standard coplanar transfers.
2. **Simplicity:** Mathematically straightforward; requires only two distinct burns.
3. **Proven Reliability:** The standard baseline for mission planning.

### Weaknesses
1. **Long Duration:** The transfer time is half the period of the transfer ellipse, which is slower than high-energy (hyperbolic) trajectories.
   $$
   t_{\text{transfer}} = \pi \sqrt{\frac{a_{\text{trans}}^3}{\mu}}
   $$
2. **Launch Windows:** For interplanetary transfers, planetary alignment must be precise (synodic period constraints).
3. **Efficiency Drop-off:** If $r_2/r_1 > 11.94$, a **[[Bi-elliptic Transfer]]** becomes more fuel-efficient, albeit significantly slower.

## Applications

### Engineering Disciplines
1. **Satellite Deployment:** GTO (Geostationary Transfer Orbit) maneuvers to reach GEO (Geostationary Orbit).
2. **Interplanetary Travel:** "Minimum energy" launch windows to Mars or Venus.
3. **Orbital Phasing:** Modifying [[orbital period]] to rendezvous with a space station.

### Practical Implementations
- **Curiosity Rover (MSL):** Utilized a Type-1 Hohmann-like trajectory for Earth-to-Mars transit.
- **Apollo Missions:** The Trans-Lunar Injection (TLI) was essentially the first leg of a modified Hohmann transfer.

## Comparison with Variants

### Contrast with [[Bi-elliptic Transfer]]
- **Bi-Elliptic:** Uses three burns and an intermediate "apogee" much farther out than the target.
- **When to use:** More efficient than Hohmann when the ratio of radii $r_2/r_1 > 11.94$.
- **Trade-off:** Bi-elliptic takes significantly longer time.

### Contrast with Fast Transfers (Lambert)
- **Lambert Transfers:** Non-tangential transfers that cut across the gap between orbits to reduce time.
- **Trade-off:** Faster transit times but significantly higher $\Delta v$ (fuel) costs.

## Pedagogical Approach

### Common Misconceptions
1. **"Shortest Path":** It is not the shortest distance (straight line) nor the fastest time; it is the most energy-efficient "natural" path.
2. **"Continuous Thrust":** The derivation assumes instantaneous kicks; low-thrust ion engines spiral out and cannot use pure Hohmann logic directly.

### Learning Resources
- **Text:** *Fundamentals of Astrodynamics* by Bate, Mueller, and White.
- **Simulation:** Kerbal Space Program (video game) provides intuitive understanding of maneuver nodes.
- **Visual:** 
## See Also

- [[Delta-v Budget]]
- [[Energy Law (Vis-Viva Equation)]]
- [[Bi-elliptic Transfer]]
- [[Keplerian Parameters]]
- [[Specific Orbital Energy]]
- [[Oberth Effect]]

## Recommended Tags:
#orbital-mechanics #astrodynamics #spaceflight #hohmann-transfer #space-maneuvers #physics
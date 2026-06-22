## Formal Definition

The **Bi-Elliptic Transfer** is an orbital maneuver used to transfer a spacecraft between two coplanar circular orbits of different radii using two intermediate transfer semi-ellipses and three impulsive burns. Unlike the two-burn [[Hohmann Transfer]], this maneuver first boosts the spacecraft to a very high intermediate [[apoapsis]] (much farther than the final target orbit) before correcting the orbit and returning to the target altitude. It becomes more fuel-efficient (lower total $\Delta v$) than the [[Hohmann Transfer]] when the ratio of the final to initial orbital radii exceeds approximately 11.94, albeit at the cost of significantly increased travel time. 

## Historical Development

### Key Milestones
- **1925:** Walter Hohmann establishes the efficiency of the two-impulse transfer, but notes the potential for other multi-impulse solutions.
- **1934:** Ary Sternfeld publishes "Initiation to Cosmonautics," where he rigorously analyzes multi-impulse transfers and identifies the conditions under which a three-impulse transfer (bi-elliptic) is superior to the [[Hohmann Transfer]].
- **1950s:** Further mathematical formalization by researchers like D.F. Lawden in the context of optimal trajectory theory.

### Foundational Contributors
1. **Ary Sternfeld (1905–1980):** The primary discoverer of the bi-elliptic efficiency paradox, showing that "going the long way around" can save fuel for high-ratio orbit changes.
2. **Klaus-Jürgen Bathe / D.F. Lawden:** Contributed to the optimization theories that validate the optimality of bi-elliptic transfers in specific regimes.

## Mathematical Formulation

### General Form
The maneuver involves three distinct velocity changes ($\Delta v$) applied at specific points. The total $\Delta v$ is:

$$
\Delta v_{\text{total}} = |\Delta v_1| + |\Delta v_2| + |\Delta v_3|
$$

### Component Breakdown
Let $r_1$ be the initial radius, $r_2$ the final radius ($r_2 > r_1$), and $r_b$ the intermediate [[apoapsis]] distance ($r_b > r_2$).

1.  **First Burn ($\Delta v_1$):** Accelerates from the initial [[circular orbit]] $r_1$ into the first elliptical transfer orbit with [[apoapsis]] $r_b$.
    $$
    \Delta v_1 = \sqrt{\frac{\mu}{r_1}} \left( \sqrt{\frac{2r_b}{r_1 + r_b}} - 1 \right)
    $$
2.  **Second Burn ($\Delta v_2$):** Occurs at the [[apoapsis]] $r_b$. This burn raises the [[Periapsis]] from $r_1$ to $r_2$. Because $r_b$ is very large, the velocity here is low, making this plane change or energy change very cheap ([[Oberth Effect]]).
    $$
    \Delta v_2 = \sqrt{\frac{\mu}{r_b}} \left( \sqrt{\frac{2r_2}{r_2 + r_b}} - \sqrt{\frac{2r_1}{r_1 + r_b}} \right)
    $$
3.  **Third Burn ($\Delta v_3$):** Occurs at the new [[Periapsis]] $r_2$. This retrograde burn circularizes the orbit at the target altitude.
    $$
    \Delta v_3 = \sqrt{\frac{\mu}{r_2}} \left( \sqrt{\frac{2r_b}{r_2 + r_b}} - 1 \right)
    $$

## Fundamental Principles

### Core Assumptions
1.  **Three-Impulse Maneuver:** The transfer is strictly defined by three instantaneous velocity changes.
2.  **Coplanar:** Typically analyzed for coplanar orbits, though the bi-elliptic transfer is also famously efficient for plane changes combined with altitude changes.
3.  **Two-Body Approximation:** Point masses subject only to central gravity.

### Governing Laws/Theorems
-   **Vis-viva Equation:** Governs velocity at all points on the ellipses.
-   **[[Oberth Effect]]:** The efficiency gain at the second burn relies heavily on the fact that the burn occurs at a very low velocity (high $r_b$), where small changes in [[Kinetic Energy]] result in large changes in orbital geometry.

## Classification and Variants

### By Apogee Distance ($r_b$)
1.  **Standard Bi-Elliptic:** Where $r_b > r_2$.
2.  **Parabolic Limit:** Where $r_b \to \infty$. This represents the theoretical maximum efficiency for the maneuver (bi-parabolic transfer).

## Physical Interpretation

### Geometric Meaning
Imagine stretching the orbit out very far to a point $r_b$. At this distant point, the spacecraft is moving very slowly. It is "cheaper" to raise the bottom of the orbit (the [[Periapsis]]) from $r_1$ to $r_2$ while the spacecraft is moving slowly at $r_b$ than it is to do it directly at $r_2$ (as in a [[Hohmann Transfer]]).

### Energy Considerations
The bi-elliptic transfer trades **time** for **energy**. By spending a long time coasting out to $r_b$ and back, the spacecraft avoids fighting the gravitational potential well "head-on" at the higher velocities found in lower orbits.

## Advantages and Limitations

### Strengths
1.  **$\Delta v$ Savings:** More efficient than Hohmann when $r_2/r_1 > 11.94$.
2.  **Plane Change Efficiency:** If a plane change ([[inclination]] change) is required, doing it at the high apogee ($r_b$) of a bi-elliptic transfer is drastically cheaper than doing it at low altitude.

### Weaknesses
1.  **Flight Time:** The travel time can be extremely long, often orders of magnitude longer than a [[Hohmann Transfer]], especially as $r_b \to \infty$.
    $$
    t_{\text{total}} = \pi \sqrt{\frac{(r_1+r_b)^3}{8\mu}} + \pi \sqrt{\frac{(r_2+r_b)^3}{8\mu}}
    $$
2.  **Complexity:** Requires three precise engine ignitions instead of two.
3.  **Perturbations:** The long excursion to $r_b$ makes the spacecraft susceptible to third-body gravitational perturbations (e.g., Moon or Sun) which may destabilize the trajectory.

### Validity Range
-   **Efficient When:** The ratio of radii $R = r_2/r_1 > 11.94$.
-   **Inefficient When:** $R < 11.94$ (Hohmann is better).
-   **Marginal Case:** Between $R \approx 11.94$ and $R \approx 15.58$, the efficiency gain is minimal; beyond 15.58, the savings become significant.

## Special Cases and Examples

### Benchmark Problems
1.  **The "Infinity" Case:**
    -   **Description:** Allowing the intermediate point $r_b$ to approach infinity.
    -   **Result:** The total $\Delta v$ approaches $\sqrt{2} v_{c1} + (\sqrt{2}-1) v_{c2}$. This is the theoretical lower bound for transfer energy between two circular orbits.

## See Also

-   [[Hohmann Transfer]]
-   [[Oberth Effect]]
-   [[Energy Law (Vis-Viva Equation)]]
-   [[Orbital Inclination Change]]
-   [[Delta-v Budget]]

## Recommended Tags:
#orbital-mechanics #astrodynamics #spaceflight #bi-elliptic-transfer #optimization #propulsion
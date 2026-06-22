## Formal Definition

A **Graveyard Orbit** is a disposal orbit located significantly above standard operational altitudes (specifically above geostationary orbit) where defunct satellites are moved at the end of their operational life. This maneuver is a critical component of space debris mitigation; by raising the altitude of a satellite, mission controllers ensure it will not collide with active satellites in the highly congested geostationary belt or interfere with future missions. 

## Historical Development

### Key Milestones
- **1977:** The first recorded intentional re-orbiting of a satellite into a higher disposal orbit (Intelsat 4-F3).
- **1997:** The Inter-Agency Space Debris Coordination Committee (IADC) formalizes the first international guidelines for the disposal of geostationary satellites.
- **2002:** The ITU (International Telecommunication Union) publishes Recommendation ITU-R S.1003.2, defining the mathematical formula for the required minimum altitude of a graveyard orbit.
- **2022:** The FCC (Federal Communications Commission) adopts a new "5-year rule" for satellites in LEO, while reinforcing disposal requirements for GEO satellites to maintain the long-term sustainability of the Clarke Belt.

### Foundational Contributors
1. **Donald J. Kessler (1940–present):** NASA scientist whose "Kessler Syndrome" theory highlighted the catastrophic risks of space debris, providing the impetus for disposal orbit protocols.
2. **Jan-Christoph Schrotter:** Contributed to the modern international regulatory frameworks for space traffic management and debris mitigation.

## Mathematical Formulation

### The IADC/ITU Minimum Altitude Formula
To ensure a satellite in a graveyard orbit does not drift back into the geostationary protected zone due to [[Solar Radiation Pressure]] and lunar/solar gravity, the minimum increase in altitude ($\Delta H$) is calculated as:

$$
\Delta H = 235 \text{ km} + (1000 \cdot C_R \cdot \frac{A}{m})
$$

### Component Breakdown
- **$235 \text{ km}$:** The baseline clearance to account for the "protected zone" around GEO (200 km) plus a 35 km buffer.
- **$C_R$:** [[Solar Radiation Pressure]] coefficient (typically between 1.2 and 1.5).
- **$A/m$:** The area-to-mass ratio of the satellite ($m^2/kg$). A satellite with large solar arrays is pushed more by sunlight, requiring a higher graveyard altitude.

## Fundamental Principles

### Core Assumptions
1. **Passive Stability:** Once moved to the graveyard orbit, the satellite is considered "dead" and will no longer perform [[station-keeping]].
2. **Fuel Reserve:** Mission success depends on the satellite retaining enough fuel at the end of its life to perform the final "Super-sync" burn.
3. **Orbital Perturbations:** The formula assumes that over the next 100 years, the satellite's [[Eccentricity]] will fluctuate due to solar pressure, but it will stay above the operational belt.

### Governing Laws
- **Law of Conservation of Momentum:** Used to calculate the impulsive $\Delta v$ required for the circularization at the higher altitude.
- **Perturbation Theory:** Specifically used to model the long-term effects of [[Solar Radiation Pressure]] on high-altitude orbits.

## Theoretical Framework

### The "Super-Synchronous" Maneuver
Moving to a graveyard orbit is a two-burn process:
1. **Perigee Raise:** A burn at perigee to raise the apoapsis into the graveyard region.
2. **Circularization:** A second burn at apoapsis to circularize the orbit.
The total $\Delta v$ required is approximately $11 \text{ m/s}$, which corresponds to about 3-6 months of normal station-keeping fuel.



## Physical Interpretation

### The "Attic" of Earth
If Geostationary Orbit is the "kitchen" of Earth's telecommunications—where everything is busy and precisely organized—the Graveyard Orbit is the "attic." It is a place where objects are stored indefinitely, away from the living space, so they don't get in the way. Because there is no atmospheric drag at 36,000 km, these satellites will remain in the graveyard orbit for millions of years.

## Advantages and Limitations

### Strengths
1. **Sustainability:** Prevents "dead" satellites from becoming unguided projectiles in a $300 \text{ billion dollar}$ industry zone.
2. **Risk Mitigation:** Significantly reduces the probability of the Kessler Syndrome in high-altitude regimes.

### Limitations
1. **Propellant Risk:** If a satellite suffers a catastrophic failure (e.g., battery explosion or electronics fried) before its end-of-life, it becomes "stuck" in the operational GEO belt, posing a permanent hazard.
2. **Finite Space:** Even the graveyard orbit is a finite shell; eventually, it may become crowded enough to require "active debris removal" (ADR).

## Applications

### Engineering and Operations
1. **Mission Planning:** Satellites are launched with "extra" fuel dedicated solely to the final disposal maneuver.
2. **Space Insurance:** Compliance with disposal guidelines is often a prerequisite for insuring a billion-dollar satellite.
3. **Space Law:** Governments fine operators (as seen with Dish Network in 2023) who fail to reach the designated graveyard altitude.

## See Also

- [[Geostationary Orbits]]
- [[Station-Keeping]]
- [[Delta-v Budget]]
- [[Solar Radiation Pressure]]
- [[Kessler Syndrome]]

## Recommended Tags:
#astrodynamics #orbital-mechanics #space-debris #GEO #satellite-disposal #space-sustainability #engineering
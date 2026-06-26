## Formal Definition

**Choked Flow** is a limiting condition that occurs when a compressible fluid passes through a restriction (like the throat of a nozzle) and reaches a [[velocity]] equal to the **local speed of sound** (M=1). Once a flow is choked, the **[[Mass Flow Rate]]** (m˙) becomes independent of the downstream (exit) pressure; decreasing the pressure outside the nozzle will no longer increase the amount of gas passing through the throat. At this point, the flow is "locked" by the upstream conditions (Pressure and Temperature) and the area of the restriction.

## Historical Development

### Key Milestones

- **1839:** **Saint-Venant** and **Wantzel** derive the first equations for the flow of air through an orifice, hinting at a maximum velocity limit.
    
- **1867:** **Osborne Reynolds** (of [[Reynolds Number]] fame) experimentally observes the choking phenomenon in steam and identifies the sonic limit at the throat.
    
- **1940s:** During the **V-2 rocket** development, engineers rely on choked flow equations to ensure a consistent, predictable mass flow into the engine, which is critical for maintaining stable combustion.
    

---

## The Physics of the "Bottleneck"

### 1. The Sonic Barrier

Pressure changes in a fluid travel at the **speed of sound**.

- In **Subsonic Flow**, a drop in pressure at the exit sends a "message" back up the pipe, telling the gas to move faster.
    
- Once the gas in the throat reaches **Mach 1**, the "message" (pressure wave) can no longer travel upstream because the gas is moving downstream at the same speed. The upstream gas "doesn't know" what's happening at the exit.
    

### 2. The Mass Flow Limit

Once the throat is choked, the density and velocity at the throat are fixed for a given set of chamber conditions. The only way to increase the mass flow is to:

- Increase the **Chamber Pressure** (Pc​).
    
- Increase the **Throat Area** (At​).
    
- Decrease the **Chamber Temperature** (Tc​) (which increases density).
    

---

## Mathematical Formulation

### 1. The Choking Condition

Flow will choke if the ratio of the **Stagnation Pressure** (P0​) to the **Back Pressure** (Pb​) exceeds a critical value:

Pb​P0​​≥(2γ+1​)γ−1γ​

_For air (γ=1.4), this critical pressure ratio is approximately **1.893**._

### 2. Choked Mass Flow Equation

The mass flow rate (m˙) for a choked, [[Isentropic Process]] nozzle is:

m˙=T0​

- Notice that the **Exit Pressure** (Pe​) is nowhere in this equation. The "bottleneck" is purely a function of what's happening _before_ the throat.
    

---

## Fundamental Principles

### Core Assumptions

1. **[[Isentropic Process]] Flow:** Assumes no heat loss or friction in the convergent section.
    
2. **Ideal Gas:** Assumes the gas behaves according to PV=nRT.
    

### Governing Laws

- **Conservation of Mass (Continuity):** m˙=ρAv.
    
- **Second Law of Thermodynamics:** Prevents the "message" from the exit from traveling faster than sound.
    

---

## Physical Interpretation

### The "Crowded Hallway" Analogy

Imagine a hallway full of people trying to get to a concert.

- At the end of the hallway is a single-person turnstile (the **Throat**).
    
- Even if you open the doors wide behind the turnstile (lower the **Back Pressure**), you can only fit one person through the turnstile per second.
    
- The only way to get more people into the concert is to push harder from behind (increase **Chamber Pressure**) or add a second turnstile (increase **Throat Area**).
    

---

## Applications

### Spacecraft Propulsion

1. **Rocket Thrust Stability:** Because the flow is choked, small pressure fluctuations in the atmosphere or the exhaust plume don't affect the combustion chamber, preventing dangerous "feedback loops."
    
2. **Cold Gas Thrusters:** Sizing the tiny orifices to ensure a specific, repeatable thrust level.
    
3. **Flow Meters:** **Sonic Orifices** are used as highly accurate flow meters because the mass flow is so predictable once choked.
    

---

## See Also

- [[De Laval Nozzle]]
    
- [[Mach Number]]
    
- [[Isentropic Process]]
    
- [[Nozzle Expansion]]
    

## Recommended Tags:

#propulsion #choked-flow #fluid-dynamics #sonic-flow #rocket-science #aerospace-engineering #mass-flow-rate
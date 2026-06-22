## Formal Definition

**Rayleigh Flow** refers to the steady, frictionless flow of a compressible fluid through a constant-area duct where **heat exchange** with the surroundings (or internal heat generation) is the primary driver of change in the fluid's properties. In Rayleigh flow, the **[[Stagnation Temperature]]** (T0​) changes as heat is added or removed, causing the Mach number to move toward **Mach 1**. Like Fanno flow, Rayleigh flow is limited by a "thermal choking" point where the flow reaches sonic velocity and cannot be further accelerated by adding more heat.

## Historical Development

### Key Milestones

- **1890s:** **Lord Rayleigh** (John William Strutt) investigates the effects of heat on sound waves and fluid motion, establishing the fundamental equations for non-adiabatic flow.
    
- **1940s:** During the development of the first **Ramjets**, Rayleigh flow becomes the primary tool for calculating the "heat addition" limits in supersonic burners.
    
- **Modern Era:** Rayleigh flow is critical for analyzing **Pulse Detonation Engines** and the thermal stability of **Nuclear Thermal Rocket (NTR)** cores.
    

---

## The "Thermal Choking" Limit

The addition of heat to a moving gas has a profound—and sometimes counter-intuitive—effect on its velocity.

### 1. Subsonic Flow (M<1)

Adding heat to a subsonic gas causes its temperature to rise, but it also causes the gas to **accelerate**. If you add enough heat, the gas will eventually reach **Mach 1** at the exit. This is called **Thermal Choking**.

### 2. Supersonic Flow (M>1)

Adding heat to a supersonic gas causes it to **decelerate**. The pressure and density increase as the gas slows down toward Mach 1. If you continue to add heat beyond the choking point, a **[[Shock Waves]]** will typically form to "readjust" the flow to subsonic speeds.

### 3. Maximum Heat Addition (Qmax​)

For any given inlet Mach number, there is a finite amount of heat that can be added before the flow chokes. In a rocket engine, if the combustion releases more energy than Qmax​, the pressure in the chamber will rise until a new equilibrium (and mass flow rate) is established.

---

## Mathematical Formulation

### 1. The Rayleigh Line

On a Temperature-Entropy (T-S) diagram, Rayleigh flow follows a specific curve called the **Rayleigh Line**.

- The top of the curve represents the point of maximum temperature.
    
- The "nose" (furthest right point) represents the point of maximum entropy, where M=1.
    

### 2. Conservation Equations

Rayleigh flow is governed by the conservation of mass and momentum (the **Rayleigh Relation**):

P+ρv2=constant

The ratio of stagnation temperatures (T0​) between two points is used to calculate the Mach number change:

T0∗​T0​​=(1+γM2)22(γ+1)M2(1+2γ−1​M2)​

_Where $T_0$ is the stagnation temperature at the sonic state (M=1).*

---

## Fundamental Principles

### Core Assumptions

1. **Constant Area:** The duct geometry does not change (A=constant).
    
2. **Frictionless:** We assume the walls are perfectly smooth (f=0) to isolate the effects of heat.
    
3. **Steady Flow:** The mass flow rate remains constant.
    

### Governing Laws

- **[[Conservation of Linear Momentum]]:** P1​+ρ1​v12​=P2​+ρ2​v22​.
    
- **[[Second Law of Thermodynamics]]:** Heat addition increases entropy (dS>0), while heat removal (cooling) decreases it.
    

---

## Physical Interpretation

### The "Crowded Concourse" Analogy

Imagine people walking down a hallway at a constant pace.

- **Heat Addition:** This is like the people suddenly becoming "energized" or hyperactive.
    
    - If they were walking (**Subsonic**), they start running faster to use up that energy, but they take up more space, eventually clogging the hallway at the exit.
        
    - If they were already sprinting (**Supersonic**), the extra energy makes them stumble and bump into each other, slowing the whole group down toward a "jogging" pace.
        

---

## Applications

### Spacecraft & Propulsion

1. **Combustion Chamber Analysis:** Predicting the pressure drop in a rocket's thrust chamber as propellants turn into high-temperature gas.
    
2. **Scramjets:** Determining the maximum fuel that can be injected into a supersonic air stream before the engine "unstarts" due to thermal choking.
    
3. **Nuclear Propulsion:** Calculating the flow velocity of hydrogen as it is flash-heated by a nuclear reactor core.
    
4. **Radiative Cooling:** Analyzing how a gas slows down or speeds up as it loses energy via radiation in a high-temperature vent line.
    

---

## See Also

- [[Fanno Flow]] (Flow with friction)
    
- [[Choked Flow]]
    
- [[Enthalpy]]
    
- [[Entropy]]
    

## Recommended Tags:

#propulsion #Rayleigh-flow #thermodynamics #heat-transfer #gas-dynamics #combustion #aerospace-engineering
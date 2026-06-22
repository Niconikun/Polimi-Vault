## Formal Definition

**Fanno Flow** refers to the steady, [[Adiabatic Process]] flow of a compressible fluid through a constant-area duct where **friction** is the primary driver of change in the fluid's properties. Unlike isentropic flow, Fanno flow is inherently **irreversible** because friction constantly generates **Entropy**. As a gas travels through a Fanno duct, its stagnation pressure always decreases, and the Mach number always moves toward **Mach 1**, regardless of whether it started as subsonic or supersonic.

## Historical Development

### Key Milestones

- **1904:** **Gino Fanno**, an Italian engineer, develops the mathematical framework for his senior thesis at the Zurich Polytechnic, providing the first rigorous look at frictional effects in high-speed gas.
    
- **1940s:** During the development of the **V-2 rocket**, Fanno flow models become critical for sizing the long propellant lines that feed the turbopumps.
    
- **Modern Era:** Fanno flow is used in the design of **Heat Exchangers** for the International Space Station (ISS) and the internal cooling passages of high-power liquid rocket engines.
    

---

## The "Sonic Limit" of Friction

The most striking characteristic of Fanno flow is that friction drives the flow toward **Choked Flow** (M=1).

### 1. Subsonic Flow (M<1)

If a gas enters a pipe at subsonic speeds, friction causes the velocity and Mach number to **increase**, while the pressure and density decrease. If the pipe is long enough, the gas will eventually reach Mach 1 at the exit.

### 2. Supersonic Flow (M>1)

If a gas enters at supersonic speeds, friction acts as a massive "brake." The velocity and Mach number **decrease**, while the pressure and density increase. Again, if the pipe is long enough, the flow will slow down until it hits Mach 1 at the exit.

### 3. The Maximum Length (L∗)

For any given inlet Mach number, there is a specific length of pipe (L∗) that will cause the flow to become **choked**. If the physical pipe is longer than L∗, the flow must "adjust" by reducing the mass flow rate at the inlet.

---

## Mathematical Formulation

### 1. The Fanno Line

On a Temperature-Entropy (T-S) diagram, Fanno flow follows a specific curve called the **Fanno Line**. The upper branch represents subsonic flow, and the lower branch represents supersonic flow. Both branches meet at the point of maximum entropy, where M=1.

### 2. The Friction Factor (f)

The effect of the duct is captured by the **Fanning Friction Factor** or the **Darcy Friction Factor**. The governing differential equation relates the change in Mach number (M) to the duct length (L) and diameter (D):

D4fL∗​=γM21−M2​+2γγ+1​ln[2+(γ−1)M2(γ+1)M2​]

---

## Fundamental Principles

### Core Assumptions

1. **Constant Area:** The pipe does not get wider or narrower (A=constant).
    
2. **[[Adiabatic Process]]:** There is no heat transfer across the pipe walls (Q=0).
    
3. **Steady Flow:** The mass flow rate remains constant throughout the duct.
    

### Governing Laws

- **Conservation of Mass:** ρv=constant.
    
- **Second Law of Thermodynamics:** Entropy must increase due to friction (dS>0). This is why the flow can only move toward the "nose" of the Fanno curve (M=1).
    

---

## Physical Interpretation

### The "Slippery vs. Sandpaper" Analogy

Imagine a long hallway.

- **Isentropic:** The floor is perfectly iced. You slide at a constant speed forever.
    
- **Fanno Flow:** The floor is covered in sandpaper.
    
    - If you are walking slowly (**Subsonic**), you have to push harder to keep moving, which actually ends up thinning out the "crowd" and making people at the end run faster to get out of the way.
        
    - If you are sprinting (**Supersonic**), the sandpaper rips at your shoes, violently slowing you down until you are just jogging at a "natural" speed (**Sonic**).
        

---

## Applications

### Spacecraft & Rockets

1. **Propellant Feed Lines:** Calculating the pressure drop between the fuel tanks and the engine. If the lines are too long or too narrow, the flow might choke, preventing the engine from reaching full thrust.
    
2. **Nuclear Thermal Rockets:** Analyzing the flow of hydrogen through long, narrow cooling channels in a nuclear reactor core.
    
3. **High-Altitude Venting:** Predicting how fast a pressurized satellite cabin would depressurize through a ruptured line or valve.
    

---

## See Also

- [[Choked Flow]]
    
- [[Rayleigh Flow]] (Flow with heat transfer)
    
- [[Mach Number]]
    
- [[Entropy]]
    

## Recommended Tags:

#propulsion #Fanno-flow #fluid-dynamics #friction #gas-dynamics #rocket-science #aerospace-engineering
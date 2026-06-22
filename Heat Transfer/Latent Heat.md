## Formal Definition

**Latent Heat** (L) is the amount of energy absorbed or released by a substance during a change of its physical state (phase) that occurs without a change in temperature. The term "latent" (meaning "hidden") refers to the fact that the energy is used to break or form molecular bonds rather than increasing the kinetic energy of the molecules. In aerospace applications, the most common form is **Latent Heat of Fusion** (Lf​), utilized in **Phase Change Materials (PCM)** to stabilize the temperature of electronics during peak loads or orbital transitions.

## Historical Development

### Key Milestones

- **1761:** **Joseph Black** discovers that ice absorbs heat without rising in temperature as it melts, leading him to realize that heat and temperature are distinct.
    
- **1970s:** NASA begins using **Phase Change Materials (PCM)**—specifically paraffin waxes—on lunar rovers and satellites to store waste heat during the day and release it during the cold lunar night.
    
- **Modern Era:** Latent heat is the fundamental principle behind **Heat Pipes** and **Loop Heat Pipes (LHP)**, which are the primary thermal transport systems for high-power modern communications satellites.
    

---

## Mathematical Formulation

### 1. The Phase Change Equation

The total heat (Q) required for a complete phase change of a mass (m) is:

Q=mL

- m: Mass of the substance (**kg**).
    
- L: Specific Latent Heat (**J/kg**).
    

### 2. Specific Latent Heat of Fusion (Lf​)

The energy required to change a solid to a liquid (or vice versa) at the melting point.

- Example: For paraffin wax (common in TCS), Lf​≈200–250 kJ/kg.
    

### 3. Specific Latent Heat of Vaporization (Lv​)

The energy required to change a liquid to a gas at the boiling point.

- This is the driving force behind **Heat Pipes**, where Lv​ is much larger than Lf​.
    

---

## Fundamental Principles

### Core Assumptions

1. **Isothermal Process:** Assumes the temperature remains exactly at the phase-change point (Tmelt​ or Tboil​) until the entire mass has transformed.
    
2. **Pure Substance:** In engineering, we often use mixtures (like waxes), which may have a small "melting range" rather than a single point.
    

### Governing Laws

- **First Law of Thermodynamics:** The energy used for the phase change must be accounted for in the system’s total energy balance (ΔU).
    

---

## Theoretical Framework

### The "Infinite Thermal Mass"

During a phase change, a material acts as if it has **infinite specific heat**.

- If you have a component mounted to a block of wax that melts at 25∘C, that component will stay at 25∘C even if you blast it with heat, as long as there is still solid wax left to melt.
    
- This provides a "thermal ceiling" that protects sensitive hardware.
    

## Physical Interpretation

### The "Ice Cube in a Drink" Analogy

Imagine a glass of water with ice on a hot day.

- As long as there is ice in the glass, the water stays at 0∘C.
    
- The sun is dumping heat into the glass, but the temperature doesn't rise. Instead, the "energy" is busy turning ice into water.
    
- Only once the last sliver of ice is gone does the water temperature begin to climb. A **PCM Heat Sink** on a satellite is just a high-tech "ice cube" designed to melt at a temperature safe for electronics (like 30∘C or 50∘C).
    

---

## Advantages and Limitations

### Strengths

1. **Mass Efficiency:** Latent heat can store far more energy per kilogram than simple thermal mass (sensible heat).
    
2. **Passive Control:** It requires no electricity or moving parts to maintain a perfectly stable temperature.
    

### Limitations

1. **Containment:** Melting wax expands; if the container isn't designed for the pressure, it can leak or burst, creating a disaster inside the satellite.
    
2. **Thermal Conductivity:** Waxes are usually poor conductors. To get the heat _into_ the wax, engineers must use metal "fins" or honeycombs inside the wax container.
    

## Applications

### Spacecraft TCS

1. **Phase Change Material (PCM) Boxes:** Used on the **Lunar Rover** and many Earth-orbiting instruments to survive high-power "burst" modes.
    
2. **Heat Pipes:** The liquid inside evaporates at the hot end (absorbing Lv​) and condenses at the cold end (releasing Lv​), moving massive amounts of heat with almost no temperature drop.
    
3. **Ablative Re-entry Shields:** The shield material melts, chars, and vaporizes, using latent heat to "carry away" the atmospheric friction heat before it reaches the astronauts.
    

---

## See Also

- [[Thermal Mass]]
    
- [[Specific Heat Capacity]]
    
- [[Heat Pipes]]
    
- [[First Law of Thermodynamics]]
    

## Recommended Tags:

#thermal-analysis #latent-heat #phase-change #PCM #spacecraft-TCS #heat-transfer #aerospace-engineering
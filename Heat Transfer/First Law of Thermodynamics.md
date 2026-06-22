## Formal Definition

The **First Law of Thermodynamics** is a version of the **Law of Conservation of Energy**, adapted for thermodynamic systems. It states that the total energy of an isolated system is constant; energy can be transformed from one form to another (such as from electrical work to heat), but it can be neither created nor destroyed. For a closed system, the change in **Internal Energy** (ΔU) is equal to the net heat (Q) added to the system minus the net work (W) done by the system. In satellite design, this law is used to perform the "Energy Balance" required to predict temperature changes over an orbit.

+2

## Historical Development

### Key Milestones

- **1840s:** **James Joule** demonstrates that mechanical work and heat are equivalent, providing the experimental proof that they are both forms of energy.
    
- **1850:** **Rudolf Clausius** and **Lord Kelvin** formally state the law, integrating it into a comprehensive theoretical framework.
    
- **1960s:** Thermal engineers for the **Gemini** and **Apollo** programs use the First Law to develop the "Nodal Network" method, which remains the industry standard for thermal modeling today.
    

### Foundational Contributors

1. **James Prescott Joule:** Established the mechanical equivalent of heat.
    
2. **Rudolf Clausius:** One of the central founders of thermodynamics who first clearly stated the First Law.
    

## Mathematical Formulation

### 1. The Classic Form

For a system undergoing a change from state 1 to state 2:

ΔU=Q−W

- ΔU: Change in internal energy (stored thermal energy).
    
- Q: Net heat transfer into the system (Solar, Albedo, Planetary IR).
    
- W: Net work done by the system (often negligible in structural thermal analysis, but critical for moving parts or actuators).
    

### 2. The Spacecraft Thermal Balance Equation

In TCS, we often express the law in terms of rates (Power):

dtdU​=Q˙​in​−Q˙​out​+P˙gen​

- dtdU​: The rate of change of stored energy (mcdtdT​).
    
- Q˙​in​: External environment loads (Solar, Albedo, Earth IR).
    
- Q˙​out​: Heat rejected via radiation (ϵσAT4).
    
- P˙gen​: Internal heat generation (battery discharge, CPU activity).
    

## Fundamental Principles

### Core Assumptions

1. **Conservation:** Energy cannot disappear; if a component gets cold, that energy _must_ have gone somewhere (radiation to space or conduction to another part).
    
2. **Closed System:** While a satellite loses mass (propellant), for thermal analysis, we generally treat the spacecraft bus as a closed system.
    

### Governing Laws

- **Law of Conservation of Energy:** The broader physical principle upon which the First Law is built.
    

## Theoretical Framework

### Steady-State vs. Transient

- **Steady-State:** When dtdU​=0, the satellite is in thermal equilibrium. Total energy in = Total energy out.
    
- **Transient:** When Q˙​in​=Q˙​out​, the internal energy changes, and the satellite's **Temperature** rises or falls.
    

## Physical Interpretation

### The "Bank Account" Analogy

Imagine your satellite's internal energy is a bank account.

- **Heat (Q):** Deposits made by the Sun.
    
- **Work (W):** Money spent to move the satellite or operate mechanisms.
    
- **Internal Energy (U):** Your current balance. The First Law simply says: **Balance = Previous Balance + Deposits - Withdrawals**. If you take in more energy than you radiate away, your "thermal balance" (temperature) goes up.
    

## Advantages and Limitations

### Strengths

1. **Unbreakable Rule:** Provides a check for any thermal model; if energy isn't conserved, the model is wrong.
    
2. **Simplicity:** Reduces complex orbital environments into a single scalar addition/subtraction problem.
    

### Limitations

1. **No Directionality:** The First Law tells you energy is conserved, but it doesn't tell you _where_ it wants to go (you need the **Second Law** for that).
    
2. **Quality of Energy:** It treats high-grade electrical energy and low-grade heat as equal in terms of total Joules.
    

## Applications

### Spacecraft Design

1. **Battery Sizing:** Calculating the heat generated during rapid charging/discharging cycles.
    
2. **Safe Mode Analysis:** Determining how long a satellite can survive in eclipse without power before it freezes.
    
3. **Heater Sizing:** Using the energy balance to determine the minimum wattage required to maintain a component above its survival temperature.
    

---

## See Also

- [[Heat]]
    
- [[Temperature]]
    
- [[Specific Heat Capacity]]
    
- [[Second Law of Thermodynamics]]
    

## Recommended Tags:

#thermal-analysis #first-law-of-thermodynamics #energy-balance #spacecraft-TCS #thermodynamics #aerospace-engineering
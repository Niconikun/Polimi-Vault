## Formal Definition

**Thermal Contact Resistance** is the resistance to heat flow that occurs at the interface between two solid surfaces in contact. This phenomenon arises because no surface is perfectly smooth; on a microscopic scale, "roughness" ensures that contact only occurs at discrete peaks called **asperities**. In the vacuum of space, heat cannot conduct through the air gaps between these asperities nor can it convect; it is restricted to conduction through the actual contact points and radiation across the gaps. This results in a significant temperature drop (ΔT) across the interface, even if the materials themselves are excellent conductors.

## Historical Development

### Key Milestones

- **1930s-40s:** Early studies in contact mechanics by researchers like **Bowden and Tabor** establish the relationship between load, surface area, and actual contact.
    
- **1960s:** The **Apollo Program** highlights the danger of contact resistance. Engineers realized that electronic components could overheat despite being bolted to a "cold" plate because the vacuum interface acted as an insulator.
    
- **1980s:** **M.M. Yovanovich** develops the industry-standard models for predicting contact conductance based on surface roughness, material hardness, and contact pressure.
    

### Foundational Contributors

1. **M. Michael Yovanovich:** His theoretical models are the basis for almost all modern aerospace software (like Thermal Desktop) used to calculate contact resistance.
    
2. **Kenneth Coon:** A NASA pioneer who focused specifically on bolted joint thermal behavior in vacuum environments.
    

## Mathematical Formulation

### 1. The Resistance Equation

Thermal contact resistance is defined by the ratio of the temperature drop to the heat flow rate:

Rc​=Q˙​ΔTinterface​​

The units are **K/W**.

### 2. Thermal Contact Conductance (hc​)

Engineers often use the inverse, **conductance**, which is normalized by the contact area (A):

Q˙​=hc​AΔTinterface​

_Where hc​ is measured in W/m2⋅K._

### 3. Factors Influencing hc​

hc​ is a complex function of:

- **Contact Pressure (P):** Higher pressure flattens asperities, increasing contact area.
    
- **Surface Roughness (σ):** Smoother surfaces generally have lower resistance.
    
- **Material Hardness (H):** Softer materials (like aluminum) deform more easily to fill gaps than hard materials (like steel).
    

## Fundamental Principles

### Core Assumptions

1. **Vacuum Environment:** In space, we assume the interstitial gas conductivity is zero (kgas​=0).
    
2. **Plastic Deformation:** At the microscopic contact points, the pressure is so high that the metal peaks are assumed to deform plastically.
    

### Governing Laws

- **Fourier's Law:** Still governs the heat flow through the individual asperities, but the "effective" area is only a tiny fraction (often <2%) of the total apparent area.
    

## Theoretical Framework

### The "Bottleneck" Effect

Even if you have two massive blocks of high-conductivity aluminum, the joint between them acts as a **bottleneck**.

- If the joint is loose, Rc​ is high → the component gets hot.
    
- If the joint is tight (high torque on bolts), Rc​ is low → the component stays cool.
    

## Physical Interpretation

### The "Crowded Bridge" Analogy

Imagine two large islands (the materials) connected by a series of very narrow, flimsy bridges (the asperities).

- The islands can hold thousands of people (heat), but everyone has to wait in a long line to squeeze across the narrow bridges.
    
- On Earth, "Convection" is like having a ferry service (air) running between the islands to help move people.
    
- In space, the ferry service is cancelled. If those bridges break or are too few, the people get stuck on the first island and it becomes overcrowded (overheated).
    

## Advantages and Limitations

### Strengths

1. **Thermal Isolation:** Sometimes Rc​ is used intentionally (using "thermal washers") to prevent heat from moving into sensitive areas like cryogenic sensors.
    
2. **Predictability:** With enough testing, Rc​ can be predicted accurately enough to size heaters and radiators.
    

### Limitations

1. **Uncertainty:** Rc​ is notoriously difficult to calculate perfectly because it depends on microscopic surface finishes that vary from part to part.
    
2. **Hysteresis:** If you bolt and unbolt a joint multiple times, the Rc​ might change because the asperities have been flattened in different ways.
    

## Applications

### Spacecraft Assembly

1. **Thermal Interface Materials (TIM):** Using soft "Gap Pads," graphite sheets, or silicone grease to fill the microscopic voids and reduce Rc​.
    
2. **Bolted Joint Standards:** Specifying high torque values for bolts on high-power components (like Transponders) to ensure low contact resistance.
    
3. **Deployable Radiators:** Modeling the resistance at the hinges of a deployable panel to ensure heat can actually reach the radiator surface.
    

---

## See Also

- [[Thermal Conductivity]]
    
- [[Fourier's Law]]
    
- [[Thermal Resistance]]
    
- [[Radiation]]
    

## Recommended Tags:

#thermal-analysis #contact-resistance #spacecraft-TCS #vacuum-heat-transfer #mechanical-joints #aerospace-engineering
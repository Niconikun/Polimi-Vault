## Formal Definition

**Absorptivity** (α) is a dimensionless property (ranging from 0 to 1) that represents the fraction of incident radiant energy (irradiation) that is absorbed by a [[Surface|[[surfa]]ce]]. In aerospace engineering, we specifically focus on **Solar Absorptivity** (αs​), which characterizes a material's behavior under the high-energy, short-wavelength spectrum of the Sun (approximately **0.2 to 3.0 μm**). A surface with an absorptivity of 1 is a perfect absorber (a blackbody), while a surface with an absorptivity of 0 reflects all incoming energy.

+1

## Historical Development

### Key Milestones

- **1860:** **Gustav Kirchhoff** demonstrates that for any material in thermal equilibrium, its capacity to absorb radiation is equal to its capacity to emit it at a specific wavelength (αλ​=ϵλ​).
    
- **1950s-60s:** During the **Vanguard** and **Explorer** missions, engineers realized that the ratio of solar absorptivity to infrared emissivity (α/ϵ) was the most critical parameter for determining the steady-state temperature of a satellite.
    
- **1970s:** The development of **Spectral Reflectometers** allows for the precise measurement of α across the solar spectrum, essential for deep-space probe design.
    

### Foundational Contributors

1. **Gustav Kirchhoff:** Established the fundamental link between absorption and emission.
    
2. **Wilhelm Wien:** His work on the displacement of radiation peaks helped engineers understand why a surface might behave differently in the "Visible" (Solar) spectrum versus the "Infrared" (Thermal) spectrum.
    

## Mathematical Formulation

### 1. The Ratio Definition

α=Ginc​Gabs​​

- Gabs​: Absorbed irradiation (W/m2).
    
- Ginc​: Total incident irradiation (W/m2).
    

### 2. Relationship to Other Properties

According to the conservation of energy, for an opaque surface:

α+ρ=1

- ρ: **Reflectivity** (fraction of energy bounced off).
    

### 3. Solar Heat Input

The heat power (Q˙​solar​) absorbed by a spacecraft surface of area A is:

Q˙​solar​=αs​⋅S⋅A⋅cos(θ)

- S: Solar Constant (≈1361 W/m2 at 1 AU).
    
- θ: Angle of incidence relative to the surface normal.
    

## Fundamental Principles

### Core Assumptions

1. **Spectral Independence (Gray Body):** While α actually varies with wavelength, we often use a single "Solar Absorptivity" value averaged over the solar spectrum for simplicity.
    
2. **Opaqueness:** Most spacecraft external surfaces (metals/paints) are opaque, meaning the transmissivity (τ) is zero.
    

### Governing Laws

- **Conservation of Energy:** Incident energy must be either absorbed, reflected, or transmitted.
    
- **[[Kirchhoff's Law]]:** α(λ,T)=ϵ(λ,T). Note that for a satellite, α (Solar) is **not** usually equal to ϵ (Infrared) because the Sun and the satellite are at vastly different temperatures.
    

## Theoretical Framework

### The α/ϵ Ratio

The equilibrium temperature of a satellite is primarily driven by this ratio:

- **High α/ϵ (e.g., Polished Gold):** Absorbs solar heat well but can't radiate it away. It gets **very hot**.
    
- **Low α/ϵ (e.g., White Paint):** Reflects most solar heat and radiates internal heat efficiently. It stays **very cool**.
    

## Physical Interpretation

### The "T-Shirt" Analogy

Imagine standing in the sun on a summer day.

- **Black T-Shirt (α≈0.9):** Absorbs nearly all the sunlight. You feel hot almost immediately.
    
- **White T-Shirt (α≈0.2):** Reflects most of the sunlight. You feel much cooler. In space, we "dress" the satellite in white paint or silvered film to prevent the Sun from overheating the electronics.
    

## Advantages and Limitations

### Strengths

1. **Passive Thermal Control:** By selecting materials with specific α values, we can keep a satellite at room temperature without using power.
    
2. **Predictability:** Solar absorptivity is relatively stable and well-documented for most aerospace materials.
    

### Limitations

1. **UV Degradation:** Solar radiation (especially UV) causes "darkening" or "yellowing" of white paints over time, which **increases** α and causes the satellite to get hotter as it ages.
    
2. **Angle Sensitivity:** For some materials, α changes significantly if the Sun hits the surface at a shallow angle.
    

## Applications

### Spacecraft Thermal Control

1. **Solar Arrays:** Designed with specific coatings to maximize α in the wavelengths where solar cells are most efficient.
    
2. **Radiators:** Coated with "White Paint" or "Silvered Teflon" to achieve the lowest possible α (to ignore the Sun) and the highest possible ϵ (to dump heat).
    
3. **MLI Outer Layers:** Using aluminized Kapton (which is yellow/gold) to achieve a specific α to balance environmental heating.
    

---

## See Also

- [[Emissivity]]
    
- [[Reflectivity]]
    
- [[Kirchhoff's Law]]
    
- [[Solar Constant]]
    

## Recommended Tags:

#thermal-analysis #absorptivity #radiation #solar-heating #spacecraft-TCS #aerospace-engineering #Kirchhoff-Law
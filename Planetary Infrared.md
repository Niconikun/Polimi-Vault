## Formal Definition

**Planetary Infrared** (also known as Earth Infrared or Outgoing Longwave Radiation - OLR) is the thermal radiation emitted by a planet's surface and atmosphere into space. Unlike solar radiation, which is short-wave (0.2–3.0 μm), planetary infrared is long-wave radiation (5.0–50.0 μm), corresponding to the planet's relatively low temperature (typically ≈250–290 K). Because it is long-wave radiation, it is governed by a spacecraft material's **Infrared Emissivity** (ϵ), not its solar absorptivity.

## Historical Development

### Key Milestones

- **1859:** **John Tyndall** identifies that certain gases in the atmosphere (like CO2​ and water vapor) absorb and re-emit infrared radiation, establishing the basis for planetary thermal emission.
    
- **1960s:** Early **TIROS** satellites began mapping Earth's infrared emission, revealing that the planet is not a uniform radiator; deserts "glow" much brighter in IR than the poles.
    
- **Present Day:** Global climate models and spacecraft thermal tools (like Thermal Desktop) use data from **ERBE** (Earth Radiation Budget Experiment) to provide precise, latitude-dependent IR flux values.
    

---

## Mathematical Formulation

### 1. The Planetary Flux (qir​)

The planet is modeled as a blackbody (or gray body) at a specific temperature (Tp​). The flux emitted by the planet is:

qir​=ϵp​σTp4​

- For **Earth**, the average IR flux is approximately **237 W/m2**.
    
- This value varies by latitude: higher at the equator (≈280 W/m2) and lower at the poles (≈150 W/m2).
    

### 2. Incident Heat Load on Spacecraft

The heat power (Q˙​ir​) absorbed by a spacecraft surface is:

Q˙​ir​=ϵ⋅qir​⋅Fs−p​

- ϵ: **Infrared Emissivity** of the spacecraft surface.
    
- Fs−p​: **View Factor** between the spacecraft and the planet.
    

---

## Fundamental Principles

### Core Assumptions

1. **Diffuse Emission:** The planet is assumed to emit radiation equally in all directions (Lambertian radiator).
    
2. **Long-Wave Characteristics:** Because the wavelengths are long (>5 μm), metals with low emissivity will reflect this heat, while white paints (which are "black" in IR) will absorb it.
    

### Governing Laws

- **Stefan-Boltzmann Law:** Determines the total power emitted by the planet based on its temperature.
    
- **Wien's Displacement Law:** Explains why the planet's radiation peak is in the infrared (≈10 μm) rather than the visible spectrum.
    

---

## Theoretical Framework

### Day vs. Night

Unlike Albedo, Planetary IR does not disappear when the satellite enters the eclipse (shadow).

- On the **Day Side**, the planet is slightly warmer, so the IR load is higher.
    
- On the **Night Side**, the planet cools, but the atmosphere retains enough heat that the IR load only drops by about **10–20%**. This makes it the primary external heat source during the "Cold Case" (eclipse) part of an orbit.
    

## Physical Interpretation

### The "Hot Sidewalk" Analogy

Imagine walking barefoot on a sidewalk at midnight.

- The sun has been down for hours, so there is no **Solar** load.
    
- There is no light reflecting, so there is no **Albedo**.
    
- However, you can still feel the heat rising from the concrete against your skin. That "invisible glow" of stored heat is the sidewalk's **Infrared Emission**. For a satellite, the Earth is that giant, warm sidewalk.
    

---

## Advantages and Limitations

### Strengths

1. **Passive Warmth:** In deep eclipse, planetary IR can prevent a satellite's batteries from freezing, acting as a natural "space heater."
    
2. **Attitude Determination:** **Earth Sensors** (Horizon Sensors) use the contrast between the "warm" Earth IR and the "cold" space (3 K) to determine the spacecraft's orientation.
    

### Limitations

1. **Latitude Sensitivity:** If a satellite is in a polar orbit, the IR load drops significantly as it passes over the ice caps, requiring more active heater power.
    
2. **Measurement Drift:** Atmospheric changes (like increased greenhouse gases or cloud cover) can slightly alter the local IR flux.
    

## Applications

### Spacecraft TCS

1. **Nadir-Facing Radiators:** Designers avoid putting radiators on the Earth-facing (Nadir) side because the constant ≈237 W/m2 IR load reduces the radiator's efficiency.
    
2. **Thermal Blanket (MLI) Design:** Using low-emissivity outer layers to block planetary IR from entering sensitive instrument bays.
    
3. **Cryogenic Missions:** Telescopes like **JWST** must stay far away from Earth (at the L2 point) because Earth’s Planetary IR would "blind" their mid-infrared sensors.
    

---

## See Also

- [[Emissivity]]
    
- [[Solar Constant]]
    
- [[Albedo]]
    
- [[View Factor]]
    
- [[Wien's Displacement Law]]
    

## Recommended Tags:

#thermal-analysis #planetary-infrared #spacecraft-TCS #environmental-loads #LEO #infrared-radiation #aerospace-engineering
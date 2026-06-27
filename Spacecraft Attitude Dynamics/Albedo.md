## Formal Definition

**Albedo** is a dimensionless measure of the [[reflectivity]] of a [[Surface]], defined as the ratio of reflected solar radiation to the total incident solar radiation. In the context of spacecraft engineering, it specifically refers to the fraction of sunlight reflected by a planet (or moon) back into space. For a "perfect" absorber (blackbody), the albedo is $0$, while for a "perfect" reflector, the albedo is $1$. The Earth's average albedo is approximately **0.30**, though this value fluctuates significantly based on cloud cover, ice caps, and vegetation.



## Historical Development

### Key Milestones
- **1760:** Johann Heinrich Lambert introduces the concept in his work *Photometria*, establishing the mathematical foundation for how surfaces reflect light.
- **1960s:** The first satellite measurements of Earth's albedo are conducted by the TIROS and Nimbus programs, revealing that the Earth was darker than previously estimated.
- **2000s–Present:** Instruments like **CERES** (Clouds and the Earth's Radiant Energy System) provide real-time, high-accuracy global albedo maps to study climate change and satellite thermal loads.

### Foundational Contributors
1. **Johann Heinrich Lambert (1728–1777):** Defined the "Lambertian" surface, which reflects light uniformly in all directions.
2. **Jean-Baptiste Joseph Fourier (1768–1830):** His work on planetary heat balance was the first to recognize the importance of reflected vs. absorbed energy.

## Mathematical Formulation

### The Albedo Ratio ($A$)
Albedo is calculated as:
$$A = \frac{P_{reflected}}{P_{incident}}$$

### Component Breakdown
- **$P_{reflected}$:** The radiant flux (power) reflected by the surface.
- **$P_{incident}$:** The total solar radiant flux hitting the surface ([[Solar Constant]] $\approx 1361 \text{ W/m}^2$ at 1 AU).

### Bond Albedo vs. Geometric Albedo
1.  **Bond Albedo:** The fraction of total solar energy reflected back into space in all directions. Crucial for **Energy Balance** calculations.
2.  **Geometric Albedo:** The brightness of a body as seen from the source (the Sun) compared to a flat Lambertian disk. Crucial for **Optical Sensors**.

## Fundamental Principles

### Core Assumptions
1. **Spectral Dependency:** Albedo varies with the wavelength of light. Most spacecraft calculations use a "bolometric" albedo averaged across the visible and UV spectrum.
2. **[[Diffuse Reflection]]:** Most planetary surfaces are modeled as Lambertian (diffuse) reflectors rather than specular (mirror-like) reflectors.

### Governing Laws
- **[[Lambert’s Cosine Law]]:** The intensity of reflected light is proportional to the cosine of the angle between the observer and the surface normal.
- **[[Conservation of Energy]]:** Incident energy that is not reflected ($1 - A$) is absorbed and must be re-emitted as infrared radiation ([[Heat]]).

## Theoretical Framework

### Albedo in [[Attitude Determination]]
Albedo acts as a **noise source** for optical sensors. 
- **Sun Sensors:** Reflected light from the Earth's atmosphere can "confuse" a sun sensor, making it think there are two suns or shifting the perceived center of the Sun by several degrees.
- **[[Earth Sensor]]:** While IR sensors are less affected, visible-light horizon sensors must distinguish between the "bright" limb (Albedo) and the "dark" limb of the planet.



## Physical Interpretation

### The "Backlight" Effect
If you are standing on a satellite in Low Earth Orbit, you are hit by light from two directions: directly from the Sun and "backlight" reflected off the Earth. This reflected light is the Albedo. It is why the Earth looks so bright from space and why satellites don't go completely dark even when they are positioned such that the Sun is behind them.

## Advantages and Limitations

### Strengths
1.  **Thermal Regulation:** Higher albedo surfaces (white paint, MLI blankets) keep spacecraft cool by reflecting solar energy.
2.  **Solar Power:** In some cases, high-albedo surfaces (like the Moon's surface) can provide a small boost to solar panel output via reflected light.

### Limitations
1.  **Variable Noise:** Because clouds move and ice melts, Albedo is highly unpredictable, making it difficult to "program out" of sensor algorithms.
2.  **Heat Load:** For satellites in very low orbits, Albedo can contribute up to **10–15%** of the total thermal load, requiring larger radiators.

## Applications

### Spacecraft Engineering
1.  **Thermal Design:** Calculating the required size of radiators to handle absorbed solar and albedo heat.
2.  **Sensor Calibration:** Creating "albedo maps" so the flight computer can ignore reflected light when using sun sensors.
3.  **Climate Monitoring:** Measuring changes in Earth's albedo to track global warming and polar ice melt.

## See Also

- [[Sun Sensor]]
- [[Earth Sensor]]
- [[Blackbody Radiation]]
- [[Solar Constant]]

## Recommended Tags:
#physics #thermodynamics #albedo #earth-observation #spacecraft-design #optics #planetary-science
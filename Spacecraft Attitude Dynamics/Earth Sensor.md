## Formal Definition

An **Earth Sensor** is an [[attitude determination]] instrument that detects the infrared (IR) "limb" or horizon of the Earth to determine the spacecraft's orientation relative to the **[[Nadir]]** (the direction pointing directly toward the center of the planet). Because the Earth’s atmosphere emits a consistent infrared signature (primarily from CO2 at the $15 \mu m$ band), these sensors can distinguish the planet from the cold background of space regardless of whether the Earth is in daylight or shadow. They are the primary sensors used for Earth-pointing missions, such as telecommunications and weather satellites.



## Historical Development

### Key Milestones
- **1960s:** Early meteorological satellites (TIROS) utilize simple "Horizon Scanners" to maintain a stable view of the atmosphere.
- **1970s:** The development of **Static Earth Sensors** (no moving parts) improves reliability for long-duration geostationary missions.
- **1990s:** Advancements in **Microbolometer** technology allow for smaller, uncooled IR detectors, reducing the mass and power requirements for Earth sensors.
- **Present:** While star trackers have replaced Earth sensors for high-precision missions, Earth sensors remain the standard for "always-on" nadir pointing in Geostationary (GEO) communication satellites.

### Foundational Contributors
1. **The Nimbus Satellite Program:** Pioneered the use of infrared horizon sensing for stabilized Earth observation.
2. **Standard Earth Sensor (SES) Manufacturers:** Companies like Sodern and Barnes Engineering standardized the "bolometer" designs used throughout the Cold War and modern era.

## Mathematical Formulation

### The Nadir Vector ($\mathbf{N}$)
The sensor measures the angle to the horizon at multiple points around the Earth's disk. If the angles to the horizon on opposite sides ($\beta_1, \beta_2$) are equal, the sensor is perfectly aligned with the Nadir.

### The Pitch and Roll Error
The angular displacement (error) from the Nadir is typically calculated as:
$$\theta_{error} = \frac{\beta_{left} - \beta_{right}}{2}$$
$$\phi_{error} = \frac{\beta_{top} - \beta_{bottom}}{2}$$

### Component Breakdown
- **$\beta$:** The angle between the sensor boresight and the detected IR horizon.
- **$\mathbf{N}_{body}$:** The resulting unit vector in the spacecraft frame pointing toward the center of the Earth.



## Fundamental Principles

### Core Assumptions
1. **Infrared Consistency:** Assumes the Earth is a uniform IR source (specifically in the $14\text{--}16 \mu m$ range) to avoid interference from clouds or terrain.
2. **Oblateness Model:** Assumes the Earth is an oblate spheroid; the onboard software must correct for the fact that the Earth looks "flatter" at the poles.

### Governing Laws
- **Planck’s Law:** The basis for detecting the IR radiation emitted by the Earth’s CO2 layer.
- **Geometry of the Circle:** Used to calculate the center of the Earth’s disk based on the detected curvature of the horizon.

## Theoretical Framework

### Types of Earth Sensors
1.  **Scanning Earth Sensor:** Uses a rotating mirror to "sweep" a bolometer across the horizon. High accuracy but has moving parts that can wear out.
2.  **Static Earth Sensor:** Uses multiple fixed-view IR telescopes pointed at different parts of the horizon. No moving parts, making it extremely reliable for GEO satellites.
3.  **Earth Albedo Sensors:** (Rare) Uses visible light; limited because they do not work on the "night" side of the orbit.

## Physical Interpretation

### The "Horizon Finder"
An Earth sensor is like a person standing on a ship looking at the horizon to see if the boat is tilting. By looking at the "edge" of the world in every direction, the satellite can tell if it is leaning too far to the left (roll) or forward (pitch). It provides a direct link between the spacecraft's "down" and the planet's "center."

## Advantages and Limitations

### Strengths
1.  **Direct Nadir Sensing:** Tells you exactly where the Earth is, which is what most satellites care about.
2.  **Day/Night Capability:** Works perfectly in the Earth's shadow because it senses heat (IR), not visible light.
3.  **Autonomous:** Does not require a star catalog or complex pattern recognition.

### Limitations
1.  **Altitude Sensitivity:** A sensor designed for LEO ($500$ km) will not work at GEO ($35,786$ km) because the Earth appears much smaller.
2.  **2-Axis Only:** Like sun sensors, a single Earth sensor cannot detect "Yaw" (rotation around the Nadir vector).
3.  **Atmospheric Noise:** Seasonal changes in the atmosphere can slightly shift the detected "height" of the horizon, introducing small errors.

## Applications

### Spacecraft Systems
1.  **Telecommunications:** Keeping antennas pointed at specific ground stations.
2.  **Weather Satellites:** Ensuring the cameras are always looking at the atmosphere.
3.  **Earth Observation:** Maintaining the "Nadir-pointing" requirement for global imaging.

## See Also

- [[Sun Sensor]]
- [[Star Tracker]]
- [[Direction Cosine Matrix]]
- [[Geostationary Orbits]]

## Recommended Tags:
#attitude-determination #earth-sensor #nadir-pointing #spacecraft-sensors #infrared #satellite-subsystems #optical-sensors
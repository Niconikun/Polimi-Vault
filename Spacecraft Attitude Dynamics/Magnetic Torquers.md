## Formal Definition

A **Magnetic Torquer** is an electromagnetic actuator that generates control torques on a spacecraft by interacting with the local planetary magnetic field. It consists of an electric coil (or a coil wrapped around a ferromagnetic core) through which current is passed to create a magnetic dipole moment ($\mathbf{m}$). This dipole experiences a physical torque when it attempts to align itself with the planet's magnetic field ($\mathbf{B}$). Because they require only electricity and no moving parts or propellant, they are the primary tool for "momentum dumping" and low-authority [[attitude control]] in Low Earth Orbit (LEO).



## Historical Development

### Key Milestones
- **1960s:** Early LEO satellites (like the Transit series) begin using simple permanent magnets and later electromagnets to provide passive and active stabilization.
- **1970s:** The development of "Torque Rods" with high-permeability cores allows for much higher torque-to-weight ratios.
- **1990s–Present:** Magnetorquers become a standard subsystem for almost every LEO mission, including the Hubble Space Telescope and nearly all CubeSats.
- **2020s:** Advanced algorithms allow "underactuated" satellites to maintain full 3-axis control using only magnetic torquers by leveraging the Earth's changing magnetic field vector along the orbit.

### Foundational Contributors
1. **James Maxwell (1831–1879):** His equations provide the fundamental physics of electromagnetism and the force on a magnetic dipole.
2. **Robert J. McElvain:** One of the early pioneers in the 1960s who formalized the control laws for active magnetic desaturation of reaction wheels.

## Mathematical Formulation

### The Torque Equation
The torque ($\mathbf{M}$) produced by a magnetic torquer is the cross product of its magnetic dipole moment ($\mathbf{m}$) and the local magnetic field ($\mathbf{B}$):

$$\mathbf{M} = \mathbf{m} \times \mathbf{B}$$

### Component Breakdown
- **$\mathbf{m}$:** The magnetic dipole moment (Am²), defined by the number of turns ($N$), the current ($I$), and the area of the coil ($A$): $m = NIA$.
- **$\mathbf{B}$:** The local magnetic field vector (Tesla), usually predicted by a model like the International Geomagnetic Reference Field (IGRF).
- **$\mathbf{M}$:** The resulting torque (Nm). 

### The Underactuation Constraint
Because of the cross-product, a magnetic torquer **cannot** produce torque parallel to the magnetic field line. 
$$\mathbf{M} \cdot \mathbf{B} = 0$$
This means that at any single instant, the spacecraft is "underactuated" (it can only rotate around two axes).



## Fundamental Principles

### Core Assumptions
1. **Planetary Field:** Assumes the spacecraft is orbiting a body with a significant magnetic field (e.g., Earth, Jupiter, Saturn). They are useless in deep space or around the Moon/Mars.
2. **Linearity:** Assumes the magnetic core (if present) does not reach magnetic saturation within the operational current range.

### Governing Laws
- **[[Lorentz Force]] Law:** The underlying physics of how moving charges in the coil experience a force in a magnetic field.
- **Biot-Savart Law:** Describes how the current in the torquer generates its own magnetic field.

## Theoretical Framework

### Momentum Desaturation (The "Dump")
The most common use for magnetic torquers is to "unload" or "dump" momentum from **Reaction Wheels**. 
1. The reaction wheel reaches its speed limit (saturation) due to external disturbances.
2. The magnetic torquer is energized to create a torque that opposes the wheel's momentum.
3. The wheel slows down while the magnetic torquer "pushes" against the Earth's magnetic field to keep the spacecraft steady.

## Physical Interpretation

### The "Compass" Effect
A magnetic torquer essentially turns the entire spacecraft into a giant compass needle. By changing the current in the coils, the flight computer can change which way the "needle" wants to point, allowing it to "lean" against the Earth's magnetic field to rotate the bus.

## Advantages and Limitations

### Strengths
1. **Infinite Life:** No moving parts to wear out and no propellant to exhaust.
2. **Low Cost/Mass:** Simple copper coils are lightweight and inexpensive.
3. **Simplicity:** Extremely high reliability compared to mechanical actuators.

### Limitations
1. **Low Torque:** The forces are very weak; they cannot perform fast maneuvers (slews).
2. **Altitude Dependent:** The Earth's magnetic field drops off with the cube of the distance ($1/r^3$), making them ineffective in Medium or Geostationary orbits.
3. **Control Ambiguity:** You cannot produce torque in the direction of the field line, requiring orbital motion to change the field geometry and regain full control.

## Applications

### Spacecraft Systems
1. **CubeSats:** Often the *only* active [[attitude control]] system on small satellites.
2. **Hubble Space Telescope:** Uses four large torque rods to manage momentum without contaminating its sensitive optics with [[thruster]] exhaust.
3. **LEO Communications Constellations:** Used for long-term [[station-keeping]] and attitude maintenance.

## See Also

- [[Reaction Wheels]]
- [[Control Moment Gyros (CMGs)]]
- [[International Geomagnetic Reference Field (IGRF)]]
- [[Momentum Exchange]]

## Recommended Tags:
#attitude-control #magnetorquers #spacecraft-engineering #LEO #electromagnetism #momentum-dumping #satellite-subsystems
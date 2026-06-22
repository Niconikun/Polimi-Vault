## Formal Definition

A **Reaction Wheel** (RW) is a type of momentum exchange device used in spacecraft [[attitude control]] to rotate the vehicle without the use of external thrusters. It consists of a fly-wheel (a heavy rotating mass) attached to an electric motor. By accelerating or decelerating the wheel, the spacecraft exerts a torque on the wheel; according to Newton’s Third Law, the wheel exerts an equal and opposite torque on the spacecraft bus. This allows for extremely precise pointing and slewing maneuvers by "trading" angular momentum between the wheels and the body of the spacecraft.



## Historical Development

### Key Milestones
- **1950s:** The concept of using internal rotating masses for satellite stabilization is theorized during early Vanguard and Explorer mission planning.
- **1960s:** Reaction wheels are successfully integrated into the **Orbiting Astronomical Observatory (OAO-2)**, proving that telescopes could be held steady enough for deep-space imaging.
- **1990s–Present:** The maturation of high-reliability brushless DC motors and precision bearings allows reaction wheels to operate continuously for decades (e.g., Hubble Space Telescope, Kepler).
- **2010s:** The failure of reaction wheels on the Kepler Space Telescope leads to the development of "Two-Wheel" control modes, utilizing [[Solar Radiation Pressure]] as a virtual third wheel.

### Foundational Contributors
1. **James Webb (1906–1992):** As NASA Administrator, he oversaw the development of the stabilization technologies required for the first generation of space telescopes.
2. **Kelsey Walker Jr.:** A pioneer in the development of the "[[momentum bias]]" and reaction wheel control laws for early communications satellites.

## Mathematical Formulation

### Conservation of Angular Momentum
In the absence of external torques, the total angular momentum ($\mathbf{H}_{total}$) of the system (spacecraft + wheels) is conserved:
$$\mathbf{H}_{total} = \mathbf{H}_{bus} + \mathbf{H}_{wheels} = \text{constant}$$

### The Governing Equation
The torque produced on the spacecraft ($\mathbf{M}_{bus}$) is the negative rate of change of the wheels' angular momentum:
$$\mathbf{M}_{bus} = -\frac{d}{dt} (\mathbf{I}_w \boldsymbol{\omega}_w)$$

### Component Breakdown
- $\mathbf{I}_w$: The moment of inertia of the reaction wheel.
- $\boldsymbol{\omega}_w$: The [[Angular Velocity]] (spin rate) of the wheel.
- $\mathbf{M}_{bus}$: The resulting control torque applied to the spacecraft.

## Fundamental Principles

### Core Assumptions
1. **Internal System:** Reaction wheels cannot change the *total* angular momentum of the spacecraft; they only move it around.
2. **Rigid Coupling:** The motor housing is assumed to be perfectly rigid relative to the spacecraft bus.

### Governing Laws
- **Newton’s Third Law:** Every action (spinning the wheel) has an equal and opposite reaction (spinning the spacecraft).
- **Euler’s Equations of Motion:** The RW torques are treated as the $M$ terms in the spacecraft's rotational equations.

## Theoretical Framework

### Momentum Management and Saturation
Because reaction wheels have a physical speed limit (e.g., 5,000 RPM), they can become **saturated**. If a constant external torque (like atmospheric drag) keeps pushing the satellite in one direction, the wheel must spin faster and faster to counteract it. Eventually, the wheel reaches its maximum speed and can no longer provide torque. At this point, the spacecraft must perform a **Momentum Dump** using thrusters or magnetic torquers to slow the wheels down.



## Physical Interpretation

### The Office Chair Analogy
If you sit on a spinning office chair and hold a bicycle wheel, spinning the bicycle wheel clockwise will cause you and the chair to rotate counter-clockwise. You haven't pushed off the floor; you have simply "exchanged" momentum with the wheel. A spacecraft does exactly this in the vacuum of space.

## Advantages and Limitations

### Strengths
1. **Precision:** Can provide tiny, incremental torques for arc-second pointing (essential for telescopes).
2. **Fuel Efficiency:** Runs on electricity (solar power) rather than finite chemical propellant.
3. **Reversibility:** Can spin in both directions to provide positive or negative torque.

### Limitations
1. **Saturation:** Requires a secondary system (thrusters/torquers) to "unload" momentum periodically.
2. **Mechanical Wear:** Bearings can fail over time due to friction and lubrication breakdown.
3. **Vibration (Jitter):** Tiny imbalances in the spinning wheel can cause high-frequency vibrations that blur sensitive camera images.

## Applications

### Spacecraft Systems
1. **Space Telescopes:** Hubble and JWST use reaction wheels to stay locked onto distant galaxies for hours at a time.
2. **Earth Observation:** Satellites like WorldView use high-torque wheels to quickly "snap" from one target to another on the ground.
3. **Deep Space Probes:** Voyagers and New Horizons use them to keep high-gain antennas pointed at Earth.

## See Also

- [[Control Moment Gyros (CMGs)]]
- [[Magnetic Torquers]]
- [[Euler's Law]]
- [[Angular Momentum]]
- [[Station-Keeping]]

## Recommended Tags:
#attitude-control #spacecraft-engineering #reaction-wheels #momentum-exchange #satellite-dynamics #pointing-precision
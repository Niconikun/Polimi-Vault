## Formal Definition

A **Control Moment Gyroscope** (CMG) is an [[attitude control]] actuator consisting of a spinning rotor with a fixed angular momentum magnitude, mounted on one or more motorized gimbals. Unlike a reaction wheel, which changes its *spin rate* to produce torque, a CMG tilts the *axis* of the spinning rotor. This tilting motion leverages the gyroscopic effect to produce an output torque that is significantly larger than the input torque required to move the gimbal. CMGs are primarily used on large spacecraft (like the ISS) or high-agility satellites that require massive torques for rapid reorientation.



## Historical Development

### Key Milestones
- **1960s:** NASA begins exploring CMGs for the Apollo Applications Program (which became Skylab) to manage the massive inertia of a manned space station.
- **1973:** Skylab launches with three large CMGs, proving the technology can maintain attitude for years without fuel.
- **1980s–90s:** The Soviet Mir space station utilizes "Gyrodynes" (Russian term for CMGs) for its complex modular stabilization.
- **2000s:** The International Space Station (ISS) integrates four large double-gimbal CMGs to counteract atmospheric drag and gravity gradients.

### Foundational Contributors
1. **The Charles Stark Draper Laboratory:** Pioneers in the development of gyroscopic guidance and control logic for the US space program.
2. **N.N. Sheremetievsky:** A key Soviet engineer who spearheaded the development of Gyrodynes for the Salyut and Mir programs.

## Mathematical Formulation

### The Gyroscopic Torque
The torque ($\mathbf{M}$) produced by a CMG is the cross product of the gimbal's [[Angular Velocity]] ($\dot{\boldsymbol{\delta}}$) and the rotor's angular momentum ($\mathbf{h}$):

$$\mathbf{M} = \dot{\boldsymbol{\delta}} \times \mathbf{h}$$

### Component Breakdown
- **$\mathbf{h}$:** The angular momentum of the rotor (fixed speed, fixed mass).
- **$\dot{\boldsymbol{\delta}}$:** The rate at which the gimbal is being tilted (the control input).
- **$\mathbf{M}$:** The resulting output torque (perpendicular to both the gimbal axis and the spin axis).

### Torque Amplification
The "magic" of the CMG lies in the fact that a small amount of energy spent tilting the gimbal produces a massive amount of torque on the spacecraft bus. This amplification ratio can be as high as $10:1$ or more compared to reaction wheels.

## Fundamental Principles

### Core Assumptions
1. **Constant Rotor Speed:** The rotor is kept at a constant, high RPM; torque is generated only by changing its direction.
2. **Conservation of Momentum:** Like reaction wheels, CMGs are momentum exchange devices and cannot change the system's total angular momentum without an external "dump."

### Governing Laws
- **Euler’s Equations of Motion:** The CMG torques are incorporated as external control inputs to the body's rotational dynamics.
- **Law of Gyroscopic [[Precession]]:** The physical principle that causes a torque to appear $90^\circ$ away from the direction of the applied gimbal force.

## Theoretical Framework

### Singularities
The most significant challenge with CMGs is the **Internal Singularity**. As the gimbals rotate to provide torque, they can reach a geometric configuration where the combined angular momentum vectors are aligned in such a way that the CMG array can no longer produce torque in a specific direction. Complex "Singularity Avoidance" algorithms are required in the flight software to navigate around these mathematical dead zones.



## Physical Interpretation

### The "Bicycle Wheel" Effect
If you hold a spinning bicycle wheel while sitting on a swivel chair and tilt the wheel to the left, you will immediately feel a powerful force spinning your chair. You didn't have to speed up the wheel; you simply changed its direction. A CMG does this with high-precision motors and massive rotors.

## Advantages and Limitations

### Strengths
1. **High Torque-to-Weight Ratio:** Can move massive spacecraft (like the ISS) that would require prohibitively large and heavy reaction wheels.
2. **High Agility:** Allows imaging satellites to "slew" and settle on targets much faster than other actuators.
3. **Efficiency:** Minimal power consumption for the amount of torque produced.

### Limitations
1. **Complexity:** Mechanical complexity of the gimbals and the mathematical complexity of the control laws.
2. **Vibration:** The high-speed rotors and gimbal movements can introduce "jitter" into sensitive instruments.
3. **Singularities:** The risk of the system "locking up" if the gimbals reach certain orientations.

## Applications

### Spacecraft Systems
1. **International Space Station (ISS):** Uses four "Double-Gimbal" CMGs to maintain its orientation relative to Earth.
2. **High-Resolution Imaging Satellites:** Satellites like WorldView-3 use CMGs to rapidly pivot between ground targets.
3. **Military Satellites:** Used for rapid retargeting of sensors or communication links.

## See Also

- [[Reaction Wheels]]
- [[Magnetic Torquers]]
- [[Euler's Law]]
- [[Gimbal Lock]]

## Recommended Tags:
#attitude-control #spacecraft-engineering #CMG #gyroscopic-effect #ISS #satellite-dynamics #high-torque
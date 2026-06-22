## Formal Definition

An **Inertial Measurement Unit (IMU)** is an electronic device that measures and reports a spacecraft’s specific force, angular rate, and sometimes the magnetic field surrounding the craft, using a combination of **accelerometers** and **gyroscopes**. By integrating these measurements over time, the IMU allows the onboard computer to track the spacecraft's attitude and position without any external reference (a process known as **Dead Reckoning**). In attitude dynamics, the IMU is the primary source of "high-frequency" data used to bridge the gaps between slower "absolute" sensor updates.



## Historical Development

### Key Milestones
- **1940s:** Development of heavy, liquid-floated "Mechanical Gyroscopes" for V-2 rockets and early ballistic missiles.
- **1960s:** The **Apollo PGNCS** (Primary Guidance, Navigation, and Control System) utilizes a gimbaled IMU that allows astronauts to navigate to the Moon even when the Earth and stars are obscured.
- **1970s–80s:** Invention of **RLG** (Ring Laser Gyros) and **FOG** (Fiber Optic Gyros), which use the [[Sagnac effect]] instead of spinning masses, eliminating moving parts.
- **2000s–Present:** The rise of **MEMS** (Micro-Electro-Mechanical Systems) IMUs allows for tiny, low-power units suitable for CubeSats and small drones.

### Foundational Contributors
1. **Charles Stark Draper (1901–1987):** The "father of inertial navigation" who led the MIT team that developed the Apollo guidance systems.
2. **Georges Sagnac (1869–1928):** Discovered the interference effect in light used by modern laser and fiber optic gyroscopes.

## Mathematical Formulation

### Integration of Angular Rate
The IMU’s gyroscopes measure the [[Angular Velocity]] vector ($\boldsymbol{\omega}$). To find the attitude (represented as a [[Quaternion]] $\mathbf{q}$), the flight computer integrates the kinematic differential equation:

$$\dot{\mathbf{q}} = \frac{1}{2} \mathbf{\Omega}(\boldsymbol{\omega}) \mathbf{q}$$

### The Bias Model
Real IMU measurements ($\tilde{\boldsymbol{\omega}}$) are never perfect; they include a constant or slowly-varying **Bias** ($b$) and **Noise** ($\eta$):
$$\tilde{\boldsymbol{\omega}} = \boldsymbol{\omega} + b + \eta$$

### Dead Reckoning Errors
Because the computer is integrating velocity to find position ($x = \int v \, dt$), any tiny error in the initial measurement grows over time.
- **Velocity error** grows linearly ($t$).
- **Position error** grows quadratically ($t^2$).

## Fundamental Principles

### Core Assumptions
1. **Inertial Frame:** Assumes the measurements are taken relative to an "inertial" (non-accelerating) [[frame of reference]].
2. **Short-Term Accuracy:** Assumes the IMU is highly accurate over seconds or minutes, even if it "drifts" over hours.

### Governing Laws
- **Newton’s Second Law:** Accelerometers measure the non-gravitational "specific force" acting on the craft.
- **[[Sagnac Effect]]:** (For RLG/FOG) Light traveling in a rotating loop takes different amounts of time to return to the source depending on the direction of rotation.



## Theoretical Framework

### Sensor Fusion (The Kalman Filter)
In modern spacecraft, the IMU is almost never used alone. It is paired with an "absolute" sensor (like a Star Tracker) using a **Kalman Filter**:
- **The IMU** provides high-speed updates (e.g., 100 Hz) to keep the control system responsive.
- **The Star Tracker** provides slow, absolute updates (e.g., 1 Hz) to "reset" the IMU's drift.

## Physical Interpretation

### The "Eyes Closed" Analogy
If you close your eyes and someone spins your chair, you know you are spinning because your inner ear feels the acceleration. You don't know exactly which way you are facing after five minutes, but you know every time the chair speeds up or slows down. The IMU is that "inner ear" for the satellite.

## Advantages and Limitations

### Strengths
1. **Self-Contained:** Does not need the Sun, Earth, or stars to work; it functions in total darkness or during a maneuver.
2. **High Bandwidth:** Can detect very fast "jitters" or tumbles that optical sensors are too slow to see.
3. **Continuity:** Provides a bridge during sensor "blinding" events (e.g., when the Sun enters the Star Tracker's view).

### Limitations
1. **Drift:** Every IMU eventually "drifts" away from the truth. Without a star tracker to reset it, the spacecraft will eventually become "lost."
2. **Sensitivity:** High-precision IMUs (RLGs) are very expensive and sensitive to temperature changes.

## Applications

### Spacecraft Systems
1. **Launch Vehicles:** Rockets rely almost exclusively on IMUs to stay on course during the high-vibration ascent to orbit.
2. **Maneuvering:** Used during "slews" to ensure the spacecraft stops exactly at the target orientation.
3. **Entry, Descent, and Landing (EDL):** Mars landers use IMUs to sense atmospheric deceleration and time the deployment of parachutes.

## See Also

- [[Quaternion]]
- [[Star Tracker]]
- [[Gimbal Lock]]
- [[Kalman Filter]]

## Recommended Tags:
#attitude-determination #IMU #inertial-navigation #gyroscopes #accelerometers #dead-reckoning #spacecraft-sensors
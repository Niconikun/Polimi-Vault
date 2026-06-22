## Formal Definition

A **State Observer** is a mathematical system that estimates the internal "state" of a real-world system (the plant) based on the measurements of its inputs and outputs. In many practical scenarios, the full state of a spacecraft (such as the exact [[Angular Velocity]] of a reaction wheel or the precise attitude of the bus) cannot be measured directly due to sensor noise, physical constraints, or cost. The observer runs a simulation of the system in parallel with the actual hardware, comparing the simulated output to the real sensor data and using the "error" between them to continuously correct its internal model.



## Historical Development

### Key Milestones
- **1960:** **Rudolf Kalman** introduces the Kalman Filter, which is effectively an "Optimal Observer" designed to handle systems with significant random noise.
- **1964:** **David Luenberger** introduces the "Luenberger Observer," a simpler, deterministic observer for systems where noise is less of a factor but the state is still hidden.
- **1970s:** Observers become standard in aerospace for "sensorless" control, allowing computers to estimate variables like velocity using only position sensors.

### Foundational Contributors
1. **David Luenberger:** Developed the observer theory for linear systems, defining how to "place" the observer poles to ensure fast convergence.
2. **Rudolf Kalman:** Provided the statistical framework for observers in noisy environments.

## Mathematical Formulation

### The Plant (Real System)
The real spacecraft dynamics are typically modeled as:
$$\dot{\mathbf{x}} = \mathbf{A}\mathbf{x} + \mathbf{B}\mathbf{u}$$
$$\mathbf{y} = \mathbf{C}\mathbf{x}$$
*Where $\mathbf{x}$ is the true state, $\mathbf{u}$ is the control input, and $\mathbf{y}$ is the sensor measurement.*

### The Observer (Estimated System)
The observer creates an estimate ($\mathbf{\hat{x}}$) using a copy of the plant model plus a **Correction Term**:
$$\dot{\mathbf{\hat{x}}} = \mathbf{A}\mathbf{\hat{x}} + \mathbf{B}\mathbf{u} + \mathbf{L}(\mathbf{y} - \mathbf{C}\mathbf{\hat{x}})$$

### Component Breakdown
- **$\mathbf{A}\mathbf{\hat{x}} + \mathbf{B}\mathbf{u}$:** The "Predictor"—it uses physics to guess what the spacecraft should be doing.
- **$\mathbf{y} - \mathbf{C}\mathbf{\hat{x}}$:** The "Innovation" (or measurement error)—the difference between the real sensor and the guess.
- **$\mathbf{L}$:** The **Observer Gain**. This matrix determines how much the computer "trusts" the sensors versus its own physics model.

## Fundamental Principles

### Core Assumptions
1. **[[Observability]]:** For an observer to work, the system must be "Observable." This means the internal states must eventually "show up" in the output data ($\mathbf{y}$).
2. **Model Accuracy:** The observer is only as good as the math used to build it. If the $\mathbf{A}$ matrix is wrong, the observer will drift.

### Governing Laws
- **The [[Separation Principle]]:** This critical law states that you can design your **Controller** (to move the satellite) and your **Observer** (to see the satellite) independently, and when you put them together, the whole system will still be stable.

## Theoretical Framework

### Closing the Loop
The observer creates a "Virtual Reality" of the spacecraft inside the computer. 
1. The computer looks at the virtual spacecraft.
2. It looks at the real sensor data.
3. If the real sensor says "I'm at 10 degrees" and the virtual one says "I'm at 9 degrees," the observer "nudges" the virtual model toward the 10-degree mark.
4. The **Controller** then uses this refined "Virtual" state to fire the thrusters.

## Physical Interpretation

### The "Driver and Passenger" Analogy
Imagine you are driving a car (the Plant). You can see the road, but you don't have a speedometer. Your passenger has a map and a stopwatch (the Observer). Based on how fast the scenery is passing and the map data, the passenger "estimates" your speed. They tell you, "I think we are going 60 mph." You use that estimate to adjust your foot on the gas (the Controller).

## Advantages and Limitations

### Strengths
1.  **Cost Savings:** Allows you to estimate values (like [[Angular Acceleration]]) without buying expensive specialized sensors.
2.  **Noise Filtering:** Because it uses a physics model, the observer can "smooth out" shaky or jumpy sensor data.
3.  **Redundancy:** If a sensor fails, a well-tuned observer can "fly the ship" for a short time using only its internal physics simulation.

### Limitations
1.  **Phase Lag:** Observers can introduce a slight delay in the data, which can cause instability if the gain ($\mathbf{L}$) is set too high.
2.  **Complexity:** Non-linear observers (like for complex tumbling) are mathematically difficult to prove stable.

## Applications

### Spacecraft Control
1.  **Rate Estimation:** Using Star Tracker images (position) to estimate the [[Angular Velocity]] ($\boldsymbol{\omega}$) of the satellite.
2.  **Disturbance Estimation:** Observing how much the satellite "drifts" to calculate the strength of an unknown disturbance torque.
3.  **Flexible Structures:** Estimating the "wobble" of large solar arrays so the control system can dampen the vibration.

## See Also

- [[Kalman Filter]] (The most common observer)
- [[PID Controller]]
- [[Lyapunov Stability Theorems]]
- [[Disturbance Torques]]

## Recommended Tags:
#control-theory #state-observer #estimation #Luenberger #Kalman #spacecraft-control #automation #state-space
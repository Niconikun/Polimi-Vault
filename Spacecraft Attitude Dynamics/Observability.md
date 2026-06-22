## Formal Definition

**Observability** is a measure of how well the internal states of a system can be inferred by knowledge of its external outputs (sensor measurements). In spacecraft dynamics, a system is "Observable" if, by looking at a finite sequence of sensor data (like Sun sensor readings and gyroscopes), the onboard computer can uniquely determine the spacecraft's current attitude and velocity. If a system is "Unobservable," it means there is a "blind spot" in the sensor suite—an internal motion or error that is occurring but remains invisible to the flight computer.



## Historical Development

### Key Milestones
- **1960:** **Rudolf Kalman** introduces the Dual Concepts of [[Controllability]] and Observability, proving they are mathematical "duals" of each other.
- **1960s:** NASA engineers use observability analysis to prove that a satellite can determine its orbit using only angles-only measurements (like tracking a star's position relative to the horizon).
- **1970s:** The development of the **[[Extended Kalman Filter]] (EKF)** relies on the local observability of non-linear systems to ensure the filter doesn't "diverge" or guess incorrectly.

### Foundational Contributors
1. **Rudolf Kalman:** Established the "Observability Matrix," the definitive algebraic test for linear systems.
2. **David Luenberger:** Developed the observer theory that relies on the system being observable to function.

## Mathematical Formulation

### The Observability Matrix ($\mathcal{O}$)
For a linear system defined by $\dot{\mathbf{x}} = \mathbf{Ax}$ and $\mathbf{y} = \mathbf{Cx}$, where $\mathbf{x}$ is an $n$-dimensional state vector and $\mathbf{y}$ is the sensor output, the Observability Matrix is:
$$\mathcal{O} = \begin{bmatrix} \mathbf{C} \\ \mathbf{CA} \\ \mathbf{CA}^2 \\ \dots \\ \mathbf{CA}^{n-1} \end{bmatrix}$$

### The Rank Test
A system is **completely observable** if and only if the matrix $\mathcal{O}$ has **full rank** ($n$). 
- If $\text{rank}(\mathcal{O}) = n$, the sensors provide enough information to reconstruct the entire state vector.
- If $\text{rank}(\mathcal{O}) < n$, the system has "unobservable modes"—changes happening inside the satellite that the sensors cannot detect.



## Fundamental Principles

### Core Assumptions
1. **The [[Duality Principle]]:** A system $(\mathbf{A, B})$ is controllable if and only if the "dual" system $(\mathbf{A}^T, \mathbf{B}^T)$ is observable. This allows engineers to use the same math tools for both problems.
2. **Model Knowledge:** Observability assumes you know the physics of the system ($\mathbf{A}$). If your physics model is wrong, you might think you are seeing a state when you are actually seeing noise.

### Governing Laws
- **The Gramian Test:** A more advanced integral-based test used for time-varying systems where the satellite's sensors might only be observable during specific parts of the orbit.

## Theoretical Framework

### The "Hidden" State
Imagine a satellite with a vibrating solar panel. If you only have an attitude sensor on the main bus, and the vibration of the panel doesn't "shake" the bus enough to be measured, that vibration is **Unobservable**. To fix this, you would need to add an accelerometer to the panel itself. Observability analysis tells you exactly where you need to add sensors to remove these "blind spots."

## Physical Interpretation

### The "Opaque Box" Analogy
Imagine a machine inside a locked wooden box. You can see smoke coming out of a vent (the Output), but you cannot see the gears inside (the State).
- If the amount of smoke tells you exactly how fast the gears are turning, the system is **Observable**.
- If the smoke stays exactly the same whether the gears are turning fast or slow, the system is **Unobservable**. You would need a different "vent" (sensor) to see what's happening.

## Advantages and Limitations

### Strengths
1.  **Sensor Selection:** Helps engineers decide the minimum number of sensors needed to save mass and power while still knowing the satellite's state.
2.  **Filter Stability:** Ensures that a **Kalman Filter** will stay "locked" onto the truth. If a state becomes unobservable, the filter will start to guess, and the error will grow to infinity.

### Limitations
1.  **Numerical Precision:** Like [[Controllability]], a matrix can be "nearly" unobservable, meaning the math works but the sensor noise is so high that the estimate is practically useless.
2.  **Non-Linearity:** In complex maneuvers, a state might be unobservable while sitting still but become observable once the satellite starts to rotate (this is common in "[[Magnetometer]]-only" navigation).

## Applications

### Spacecraft Estimation
1.  **Gyro-Bias Estimation:** Determining the "drift" of an IMU by observing how the Star Tracker readings change over time.
2.  **Orbit Determination:** Reconstructing a 6-DOF orbit ([[position]] and velocity) using only ground-station range measurements.
3.  **Sensorless Control:** Estimating the speed of a motor by observing the voltage and current spikes, rather than using a dedicated tachometer.

## See Also

- [[Controllability]]
- [[State Observer]]
- [[Kalman Filter]]
- [[TRIAD Algorithm]]

## Recommended Tags:
#control-theory #observability #Kalman #state-estimation #sensors #linear-algebra #spacecraft-engineering
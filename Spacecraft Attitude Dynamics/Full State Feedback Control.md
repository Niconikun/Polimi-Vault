## Formal Definition

**Full State Feedback (FSF) Control** (also known as [[Pole Placement]]) is a control strategy where the control input ($\mathbf{u}$) is calculated as a linear combination of all the system's internal "states" ($\mathbf{x}$). Unlike traditional PID control, which usually looks at a single [[Error Signal]] (like "pointing error"), FSF utilizes the entire state vector (attitude, [[Angular Velocity]], actuator rates, etc.) to determine the optimal command. In this framework, the gain matrix ($\mathbf{K}$) is "placed" such that the closed-loop system behaves with a specific desired speed and damping.



## Historical Development

### Key Milestones
- **1950s:** The shift from classical "[[Transfer Function]]" control to **Modern Control Theory** (State-Space) begins as aerospace systems become too complex for simple loops.
- **1960:** **Rudolf Kalman** publishes on "[[Controllability]]," providing the mathematical proof that a system can only be controlled via FSF if it meets specific criteria.
- **1970s–Present:** FSF becomes the standard for high-performance aircraft (like the F-16) and complex spacecraft, as it naturally handles the coupling between different axes (e.g., roll affecting yaw).

### Foundational Contributors
1. **Rudolf Kalman:** Established the [[State-Space Representation]] that makes FSF possible.
2. **Aleksandr Lyapunov:** Provided the stability proofs used to ensure that the feedback gains ($\mathbf{K}$) won't cause the system to "explode."

## Mathematical Formulation

### The State-Space System
The dynamics of the spacecraft are represented as:
$$\dot{\mathbf{x}} = \mathbf{A}\mathbf{x} + \mathbf{B}\mathbf{u}$$

### The Control Law
In Full State Feedback, the control input is defined as:
$$\mathbf{u} = -\mathbf{K}\mathbf{x}$$

### The Closed-Loop Dynamics
Substituting the control law back into the dynamics yields:
$$\dot{\mathbf{x}} = (\mathbf{A} - \mathbf{B}\mathbf{K})\mathbf{x}$$

### The Goal
The engineer chooses the values in the matrix **$\mathbf{K}$** such that the eigenvalues of the new "system matrix" $(\mathbf{A} - \mathbf{B}\mathbf{K})$ are in a stable, desirable location. This process is known as **[[Pole Placement]]**.



## Fundamental Principles

### Core Assumptions
1. **Linearity:** The system must be linear (or linearized) for the math to hold perfectly.
2. **[[Controllability]]:** The system must be "Controllable." This means the actuators must be physically capable of moving every single state in the vector $\mathbf{x}$.

### Governing Laws
- **The [[Separation Principle]]:** Allows the design of the **[[State Observer]]** and the **Full State Feedback Controller** to be done independently.
- **Cayley-Hamilton Theorem:** Used in the background to calculate the gain matrix $\mathbf{K}$.

## Theoretical Framework

### The "All-Seeing" Controller
Traditional control is like driving a car while only looking at the speedometer. **Full State Feedback** is like driving while knowing the speed, the engine temperature, the tire pressure, and the incline of the road all at once. By using all this information, the controller can be much more aggressive and precise without overshooting the target.

## Physical Interpretation

### The "Damped Spring"
Imagine a satellite as a mass on a spring. A simple controller might just pull on the spring when it's too long. FSF looks at how long the spring is (Position) AND how fast it's moving (Velocity). By "weighting" the velocity, the controller can slow down the satellite *before* it reaches the target, resulting in a perfect, smooth stop with no "ringing" or oscillation.

## Advantages and Limitations

### Strengths
1.  **Multi-Variable Control:** Can manage $X, Y,$ and $Z$ axes simultaneously, accounting for the fact that they "talk" to each other.
2.  **Total Stability:** If the system is controllable, you can mathematically guarantee that the system will be stable.
3.  **Optimization:** Forms the basis for **LQR ([[Linear Quadratic Regulator]])** control, which finds the "cheapest" or "fastest" way to move the ship.

### Limitations
1.  **State Availability:** It requires you to know *every* state. If you don't have a sensor for a state, you **must** use a **[[State Observer]]** to estimate it.
2.  **Model Sensitivity:** If your physics model ($\mathbf{A}$ and $\mathbf{B}$) is slightly off, the high-performance gains can actually make the system unstable (Robustness issues).

## Applications

### Spacecraft Guidance
1.  **Precision Slew:** Moving a telescope from one star to another with zero oscillation.
2.  **Rendezvous and Docking:** Managing the 6-DOF ([[degrees of freedom]]) required for two ships to meet in orbit.
3.  **Active Vibration Suppression:** Using sensors on a large solar array to actively "counter-wobble" the panel so it doesn't snap off.

## See Also

- [[State Observer]]
- [[PID Controller]]
- [[Linear Quadratic Regulator]]
- [[Lyapunov Stability Theorems]]

## Recommended Tags:
#control-theory #full-state-feedback #pole-placement #state-space #modern-control #spacecraft-dynamics #automation
## Formal Definition

**Steady-State Error** ($e_{ss}$) is the discrepancy between the reference input and the actual output of a system as [[Time]] ($t$) reaches infinity. It represents the "final" accuracy of a control system after all transient oscillations ([[Overshoot]] and ringing) have died down. In spacecraft pointing, steady-state error is often caused by external [[Disturbance Torques]] (like gravity gradients) that the controller is not "strong" enough to fully cancel out. Mathematically, it is evaluated using the **Final Value Theorem** of the [[Laplace Transform]].



## Historical Development

### Key Milestones
- **19th Century:** James Watt and James Clerk Maxwell analyze "offset" in steam engine governors, which is the mechanical equivalent of steady-state error.
- **1922:** **Nicolas Minorsky** publishes his work on the **[[PID Controller]]**, specifically introducing the "Integral" (I) term to eliminate steady-state error in the automatic steering of ships.
- **1960s:** Precision requirements for the **Orbiting Astronomical Observatory (OAO)** necessitate the use of high-gain integral control to eliminate errors caused by magnetic disturbances.

### Foundational Contributors
1. **Nicolas Minorsky:** Proved that adding an integrator to the control loop is the mathematical solution to the steady-state error problem.
2. **James Clerk Maxwell:** Provided the first rigorous mathematical analysis of control stability and error.

## Mathematical Formulation

### The [[Error Signal]]
In a closed-loop system, the error is defined as:
$$E(s) = R(s) - Y(s)$$

### The Final Value Theorem
The steady-state error can be calculated directly from the system's [[transfer function]] without solving the differential equations:
$$e_{ss} = \lim_{t \to \infty} e(t) = \lim_{s \to 0} s E(s)$$

### System Type and Error
The error depends on the **System Type** (the number of pure integrators, $1/s$, in the loop):
- **Type 0:** Constant error for a step input (e.g., a simple proportional controller).
- **Type 1:** Zero error for a step input, but constant error for a ramp (tracking a moving target).
- **Type 2:** Zero error for a ramp, but constant error for an acceleration input.

| Input Type | Type 0 System | Type 1 System | Type 2 System |
| :--- | :--- | :--- | :--- |
| **Step (Position)** | Finite Error | **Zero Error** | **Zero Error** |
| **Ramp (Velocity)** | Infinite Error | Finite Error | **Zero Error** |
| **Parabola (Accel)**| Infinite Error | Infinite Error | Finite Error |

## Fundamental Principles

### Core Assumptions
1. **Stability:** Steady-state error only exists if the system is stable. If the system is unstable, the error goes to infinity.
2. **Linearity:** Assumes the actuators aren't "saturated" (e.g., the reaction wheel hasn't reached max speed).

### Governing Laws
- **Internal Model Principle:** To track a specific type of input (like a constant or a ramp) with zero steady-state error, the controller must "contain" a model of that input (an integrator).



## Theoretical Framework

### The Battle Against Disturbances
A satellite is constantly hit by a **Disturbance Torque** ($T_d$). 
- A **Proportional (P)** controller is like a spring; it needs an error to generate a force. Therefore, it will always have a steady-state error because it needs that "stretch" to fight the constant push of the disturbance.
- An **Integral (I)** controller is like a memory; it remembers that the disturbance is there and keeps building up force until the error is exactly zero.

## Physical Interpretation

### The "Leaky Bucket" Analogy
Imagine trying to keep a bucket full of water while it has a hole in the bottom (the Disturbance). 
- **Proportional Control:** You pour in more water as the level drops. Eventually, you find a level where the water you pour in matches the water leaking out. The bucket is stable, but not "Full"—that gap is the **Steady-State Error**.
- **Integral Control:** You notice the level is still low, so you keep turning up the tap more and more until the bucket stays perfectly full despite the leak.

## Advantages and Limitations

### Strengths
1.  **Predictability:** Allows engineers to specify a "Pointing Accuracy" (e.g., 0.001 degrees) for a telescope.
2.  **Diagnostic Tool:** A high steady-state error often signals that a disturbance torque is stronger than the physics model predicted.

### Limitations
1.  **[[Integrator Windup]]:** While adding an "I" term fixes error, it can cause the actuators to "wind up" and [[Overshoot]] the target aggressively.
2.  **Sensor Bias:** If your sensor has a 1-degree bias, the controller will reach "Zero Error" relative to the sensor, but you will still be 1 degree off from the truth.

## Applications

### Spacecraft Precision
1.  **[[Nadir]] Pointing:** Ensuring a weather satellite points exactly at the Earth's center despite the gravity gradient.
2.  **Solar Tracking:** Keeping solar panels perpendicular to the Sun to maximize power.
3.  **Deep Space Communication:** Eliminating the tracking error in a high-gain antenna as it follows the Earth's motion.

## See Also

- [[PID Controller]]
- [[Disturbance Torques]]
- [[Final Value Theorem]]
- [[Stability Analysis]]

## Recommended Tags:
#control-theory #steady-state-error #PID #feedback-control #spacecraft-pointing #mathematics #integration
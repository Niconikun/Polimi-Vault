## Formal Definition

**State-Space Representation** is a [[mathematical model]] of a physical system as a set of input, output, and state variables related by first-order differential equations. In this framework, the "State" of the spacecraft is represented by a vector ($\mathbf{x}$), which contains all the information necessary to predict the future behavior of the system. By arranging these equations into a matrix format, engineers can analyze complex, Multi-Input Multi-Output (MIMO) systems—such as a satellite with three reaction wheels and multiple sensors—using the tools of [[linear algebra]].



## Historical Development

### Key Milestones
- **19th Century:** Henri Poincaré and other mathematicians develop "State Variable" theory to solve problems in celestial mechanics (the precursor to orbital mechanics).
- **1960:** **Rudolf Kalman** formalizes the modern State-Space approach, introducing concepts of Controllability and [[Observability]]. This marked the transition from "Classical Control" (Laplace/Frequency domain) to "Modern Control" (Time domain).
- **1960s:** NASA's Apollo program is the first major application of State-Space theory, used to manage the complex switching logic and multi-axis maneuvers required for the lunar landing.

### Foundational Contributors
1. **Rudolf Kalman:** The "father" of modern control who unified the matrix approach for estimation and control.
2. **Aleksandr Lyapunov:** Provided the stability analysis techniques used specifically on state-space models.

## Mathematical Formulation

The standard linear state-space model consists of two primary equations:

### 1. The State Equation (The Physics)
Describes how the internal state changes over time based on the current state and the control inputs:
$$\dot{\mathbf{x}} = \mathbf{A}\mathbf{x} + \mathbf{B}\mathbf{u}$$

### 2. The Output Equation (The Sensors)
Describes what the sensors actually "see" based on the internal state:
$$\mathbf{y} = \mathbf{C}\mathbf{x} + \mathbf{D}\mathbf{u}$$

### Component Breakdown
- **$\mathbf{x}$:** The **State Vector** (e.g., $[ \text{position}, \text{velocity}, \text{attitude}, \text{rate} ]^T$).
- **$\mathbf{A}$:** The **System Matrix**, defining the internal dynamics (how states affect each other).
- **$\mathbf{B}$:** The **Input Matrix**, defining how the actuators (thrusters) affect the state.
- **$\mathbf{C}$:** The **Output Matrix**, mapping the internal state to the sensor readings.
- **$\mathbf{D}$:** The **Feedthrough Matrix**, representing any direct effect of input on output (usually zero in aerospace).



## Fundamental Principles

### Core Assumptions
1. **First-Order Form:** Any high-order differential equation (like $\mathbf{F}=m\mathbf{a}$, which is second-order) must be broken down into multiple first-order equations to fit the $\dot{\mathbf{x}}$ format.
2. **Linearity:** The standard matrices assume the system is linear. For non-linear spacecraft (tumbling), we use a **Linearized State-Space** model around a specific point (like [[Nadir]]-pointing).

### Governing Laws
- **The State [[State Transition Matrix]] ($\Phi$):** The mathematical operator that "propels" the state vector forward through time.

## Theoretical Framework

### The N-Dimensional State Space
If a satellite has 6 states (3 for attitude, 3 for rate), it exists as a single point in a **6-Dimensional Geometry**. Moving the satellite isn't just "turning it"; it is mathematically "tracing a path" through this 6D space. Control theory then becomes the task of finding the shortest or most fuel-efficient path between two points in this geometry.

## Physical Interpretation

### The "Snapshot" Analogy
Imagine a movie. A single frame is the **State Vector**—it shows where everyone is. But to know what happens in the *next* frame, you also need to know the velocity of the actors. Therefore, the "State" is the minimum amount of information you need at this exact moment to know exactly where the system will be in the next second, provided you know what the pilot (the input) is doing.

## Advantages and Limitations

### Strengths
1.  **MIMO Handling:** Unlike PID, it can handle 10 inputs and 10 outputs in a single set of equations.
2.  **Time-Varying Systems:** Can easily account for a satellite's mass changing as it burns fuel (changing the $A$ and $B$ matrices over time).
3.  **Optimization:** Required for advanced techniques like **LQR**, **Kalman Filtering**, and **MPC**.

### Limitations
1.  **Complexity:** Requires significantly more "pen-and-paper" math and matrix algebra than classical tuning.
2.  **Internal Blindness:** If you don't pick your states correctly, you might end up with an **Unobservable** system where things are happening that you can't see.

## Applications

### Spacecraft GNC
1.  **Attitude Estimation:** The core of the **[[Extended Kalman Filter]] (EKF)**.
2.  **[[Structural Dynamics]]:** Modeling the vibration modes of the International Space Station's trusses.
3.  **Orbit Determination:** Representing the position and velocity of a probe as it approaches a planet.

## See Also

- [[Full State Feedback Control]]
- [[State Observer]]
- [[Controllability]]
- [[Observability]]

## Recommended Tags:
#control-theory #state-space #linear-algebra #modern-control #system-dynamics #mathematics #MIMO
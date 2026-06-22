## Formal Definition

A **Multi-Input Multi-Output (MIMO)** system is a dynamical model that possesses multiple control inputs and multiple measured outputs. Unlike SISO systems, where each input-output pair is analyzed in isolation, MIMO systems account for **coupling**—the phenomenon where a single input (e.g., firing a roll thruster) affects multiple outputs (e.g., changing both roll and yaw due to gyroscopic effects). Because of this complexity, MIMO systems are almost exclusively analyzed using **[[State-Space Representation]]** and linear algebra rather than classical frequency-domain methods.



## Historical Development

### Key Milestones
- **1950s:** The development of supersonic aircraft and early ballistic missiles reveals that SISO "loop-by-loop" design fails when axes are heavily coupled.
- **1960:** **Rudolf Kalman** introduces the state-space framework, providing the first unified mathematical language for MIMO control.
- **1980s:** **Robust Control** (H-infinity) is developed to handle the uncertainty in MIMO systems, specifically for flexible space structures like the ISS.
- **Present:** MIMO control is essential for **Active Debris Removal** and **Autonomous Docking**, where 6-DOF ([[Degrees of Freedom]]) must be managed perfectly.

### Foundational Contributors
1. **Rudolf Kalman:** Proved that MIMO systems require a centralized "State" approach to ensure total system stability.
2. **Isaac Horowitz:** Developed "Quantitative Feedback Theory" (QFT) to bridge the gap between SISO intuition and MIMO complexity.

## Mathematical Formulation

### 1. The State-Space Form (The Standard)
The matrices $\mathbf{B}$ and $\mathbf{C}$ are no longer vectors, but multi-dimensional arrays:
- **$\mathbf{u}$:** An $m \times 1$ vector of inputs.
- **$\mathbf{y}$:** A $p \times 1$ vector of outputs.
- **$\mathbf{B}$:** An $n \times m$ matrix.
- **$\mathbf{C}$:** A $p \times n$ matrix.

### 2. The [[Transfer Function]] Matrix
In the Laplace domain, a MIMO system is represented by a matrix of transfer functions, where each element $G_{ij}(s)$ describes the path from input $j$ to output $i$:
$$\mathbf{Y}(s) = \mathbf{G}(s)\mathbf{U}(s)$$



## Fundamental Principles

### Core Assumptions
1. **Coupling:** Assumes that inputs interact. In a satellite, angular momentum means that a torque in $X$ will naturally induce a motion in $Y$ (cross-coupling).
2. **Centralized Control:** Assumes that one controller "sees" all sensors and "commands" all actuators simultaneously to balance these interactions.

### Governing Laws
- **The Interaction Principle:** In MIMO systems, "Zeroing" the error in one channel may inadvertently increase the error in another channel.

## Theoretical Framework

### The Matrix Advantage
MIMO theory allows us to use **Eigenvalues** and **Singular Values** to determine stability. Instead of looking at a single [[Bode Plot]], we look at the "Principal Gains" of the system matrix. This tells us the "strongest" and "weakest" directions of control—for example, a satellite might be very easy to rotate around its long axis but very difficult (heavy) to rotate around its short axis.

## Physical Interpretation

### The "Puppeteer" Analogy
Imagine a marionette puppet.
- **SISO:** You have one string for one arm. You pull it, the arm moves.
- **MIMO:** You have ten strings. Pulling the "arm" string might also tilt the head or lift a leg because they are all physically connected. 
To make the puppet walk, you cannot just move one string at a time; you need a "Controller" (the Puppeteer) who understands how every string affects every part of the body simultaneously.

## Advantages and Limitations

### Strengths
1.  **High Performance:** Can achieve much tighter pointing accuracy by actively canceling out cross-axis disturbances.
2.  **Actuator Redundancy:** If one thruster fails, a MIMO controller can automatically re-calculate how to use the *other* thrusters to achieve the same movement.

### Limitations
1.  **Complexity:** Requires heavy on-board computation (Matrix inversions and multiplications).
2.  **Sensitivity:** A small error in your knowledge of the coupling (the $\mathbf{A}$ matrix) can lead to the controller "fighting itself," causing instability.

## Applications

### Spacecraft Mission Profiles
1.  **6-DOF Docking:** Simultaneously controlling $X, Y, Z$ position and Roll, Pitch, Yaw attitude.
2.  **Flexible Spacecraft:** Controlling a satellite with large, "floppy" solar arrays where moving the body makes the arrays wobble.
3.  **Formation Flying:** Coordinating multiple satellites to act as a single large telescope.

## See Also

- [[SISO System]]
- [[State-Space Representation]]
- [[Decoupling]]
- [[LQR Control]]

## Recommended Tags:
#control-theory #MIMO #state-space #coupling #modern-control #system-dynamics #aerospace-engineering
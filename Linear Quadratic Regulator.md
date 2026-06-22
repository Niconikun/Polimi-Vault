## Formal Definition

The **Linear Quadratic Regulator (LQR)** is an optimal control strategy that calculates the feedback gain matrix ($\mathbf{K}$) by minimizing a quadratic "cost function." This cost function represents a trade-off between two competing goals: **Regulation Performance** (how quickly and accurately the spacecraft reaches the target) and **Control Effort** (how much fuel or electricity is consumed). By adjusting weighting matrices, an engineer can tell the computer to prioritize either extreme precision or maximum fuel economy, and the LQR algorithm will solve the **Algebraic [[Riccati Equation]] (ARE)** to find the mathematically perfect balance.



## Historical Development

### Key Milestones
- **1950s:** Richard Bellman develops the "Principle of Optimality," laying the groundwork for dynamic programming.
- **1960:** **Rudolf Kalman** introduces the LQR framework, providing the first systematic way to design stable, multi-variable controllers for the aerospace industry.
- **1970s:** LQR becomes the baseline for "Optimal Guidance" in intercontinental ballistic missiles and NASA's deep-space probes.
- **Present:** LQR is the foundation for more advanced methods like **Model Predictive Control (MPC)** and is used in the landing of SpaceX Falcon 9 boosters.

### Foundational Contributors
1. **Rudolf Kalman:** Formalized the LQR problem and its relationship to the [[Riccati Equation]].
2. **Richard Bellman:** Developed the "Bellman Equation," which provides the underlying logic for optimal pathfinding.

## Mathematical Formulation

### The Cost Function ($J$)
LQR seeks to minimize the following integral over [[time]]:
$$J = \int_{0}^{\infty} (\mathbf{x}^T \mathbf{Q} \mathbf{x} + \mathbf{u}^T \mathbf{R} \mathbf{u}) dt$$

### Component Breakdown
- **$\mathbf{x}^T \mathbf{Q} \mathbf{x}$:** The penalty for **State Error**. A large $\mathbf{Q}$ means you want the satellite to stay exactly on target, no matter the cost.
- **$\mathbf{u}^T \mathbf{R} \mathbf{u}$:** The penalty for **Control Effort**. A large $\mathbf{R}$ means you want to save fuel or avoid straining your reaction wheels.
- **$\mathbf{K}$**: The optimal gain matrix, derived from the solution to the [[Riccati Equation]]:
  $$\mathbf{u} = -\mathbf{K}\mathbf{x}$$

### The Algebraic [[Riccati Equation]] (ARE)
To find $\mathbf{K}$, the computer must first solve for the matrix $\mathbf{P}$ in:
$$\mathbf{A}^T\mathbf{P} + \mathbf{P}\mathbf{A} - \mathbf{P}\mathbf{B}\mathbf{R}^{-1}\mathbf{B}^T\mathbf{P} + \mathbf{Q} = 0$$

## Fundamental Principles

### Core Assumptions
1. **Linear Dynamics:** Assumes the spacecraft can be modeled by $\dot{\mathbf{x}} = \mathbf{Ax} + \mathbf{Bu}$.
2. **Full State Availability:** Assumes every state is known (usually via a **[[State Observer]]**).
3. **Infinite Horizon:** Standard LQR assumes the mission continues long enough for the system to reach a steady state.

### Governing Laws
- **The Certainty Equivalence Principle:** States that the optimal controller remains the same even if the system has random noise, provided you use an optimal observer (Kalman Filter). This combined system is known as **LQG (Linear Quadratic Gaussian)** control.

## Theoretical Framework

### The Weighting Matrices ($\mathbf{Q}$ and $\mathbf{R}$)
LQR turns control design from "guessing where poles should go" into "deciding what is important."
- If your satellite is low on fuel, you increase the values in **$\mathbf{R}$**. The satellite will move more slowly and "lazy," but it will survive longer.
- If your satellite is about to dock and needs sub-millimeter precision, you increase **$\mathbf{Q}$**. The thrusters will fire aggressively to maintain a perfect position.



## Physical Interpretation

### The "Rubber Band and Gold" Analogy
Imagine your spacecraft is connected to its target by a rubber band. The "State Error" ($\mathbf{Q}$) is the stiffness of the rubber band—the stiffer it is, the faster the ship snaps to the target. However, every time the thrusters fire, it costs "Gold" ($\mathbf{R}$). LQR is like a manager who calculates exactly how stiff the rubber band should be so that you get to the destination on time without spending more gold than necessary.

## Advantages and Limitations

### Strengths
1.  **Guaranteed Stability:** LQR controllers are mathematically guaranteed to be stable (provided the system is controllable).
2.  **MIMO Capability:** Effortlessly handles Multi-Input Multi-Output systems where axes are cross-coupled.
3.  **Optimal Efficiency:** It is, by definition, the most efficient linear controller for the given weights.

### Limitations
1.  **Linear Only:** Performance may degrade during extreme, non-linear maneuvers (like a fast tumble).
2.  **Trial and Error:** While you don't have to guess poles, you still have to "tweak" the weights in $\mathbf{Q}$ and $\mathbf{R}$ to get the desired feel.

## Applications

### Spacecraft Mission Profiles
1.  **Station Keeping:** Maintaining a Geostationary satellite's position using the minimum amount of propellant.
2.  **Attitude Stabilization:** Smoothly dampening out the "wobble" after a spacecraft separates from its rocket.
3.  **Precision Pointing:** Holding a laser communication link steady between two moving satellites.

## See Also

- [[Full State Feedback Control]]
- [[State Observer]]
- [[Kalman Filter]]
- [[Lyapunov Stability Theorems]]

## Recommended Tags:
#control-theory #LQR #optimal-control #Kalman #Riccati-equation #spacecraft-guidance #optimization
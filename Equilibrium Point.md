## Formal Definition

An **Equilibrium Point** is a specific state ($\mathbf{x}_e$) of a dynamical system where the rate of change of the state is zero ($\dot{\mathbf{x}} = 0$). In the context of a spacecraft, this represents a "steady state" where, in the absence of external disturbances or control inputs, the vehicle will remain indefinitely. Mathematically, for a system defined by $\dot{\mathbf{x}} = f(\mathbf{x}, \mathbf{u})$, the equilibrium points are found by solving the algebraic equation $f(\mathbf{x}_e, \mathbf{u}_e) = 0$. These points are the necessary targets for linearization and stability analysis.



## Historical Development

### Key Milestones
- **17th Century:** Isaac Newton identifies the "equilibrium of forces" in his study of statics and celestial mechanics.
- **1892:** **Aleksandr Lyapunov** publishes his work on the stability of motion, categorizing equilibrium points based on how a system behaves when nudged away from them.
- **1960s:** Aerospace engineers identify "Gravity Gradient" and "[[Lagrange Points]]" as natural equilibrium points in space that can be exploited for fuel-efficient station-keeping.

### Foundational Contributors
1. **Henri Poincaré (1854–1912):** Developed the qualitative theory of [[differential equations]] and "Phase Portraits" to visualize equilibrium.
2. **Aleksandr Lyapunov:** Formalized the mathematical definitions of stability for these points.

## Mathematical Formulation

### Finding the Point
For a non-linear system $\dot{\mathbf{x}} = f(\mathbf{x})$, the equilibrium points $\mathbf{x}_e$ are the roots of:
$$f(\mathbf{x}_e) = 0$$

### Classifying the Point (Linearization)
To understand the *nature* of the equilibrium, we look at the eigenvalues ($\lambda$) of the [[Jacobian Matrix]] $\mathbf{A} = \frac{\partial f}{\partial \mathbf{x}}$ evaluated at $\mathbf{x}_e$:

1.  **Stable (Sink/Node):** All eigenvalues have negative real parts ($\text{Re}(\lambda) < 0$).
2.  **Unstable (Source):** At least one eigenvalue has a positive real part ($\text{Re}(\lambda) > 0$).
3.  **Marginally Stable (Center):** Eigenvalues are purely imaginary ($\text{Re}(\lambda) = 0$). The system oscillates around the point (e.g., undamped libration).
4.  **Saddle Point:** A mix of positive and negative real parts; stable in one direction but unstable in another.



## Fundamental Principles

### Core Assumptions
1. **Autonomy:** Usually assumes the system is "Autonomous" (the physics don't change just because the clock is ticking).
2. **Local vs. Global:** A system can have multiple equilibrium points. A satellite might be stable pointing "[[Nadir]]" and also stable pointing "Zenith."

### Governing Laws
- **The Hartman-Grobman Theorem:** States that the behavior of a non-linear system near a hyperbolic equilibrium point is qualitatively the same as its linearized version.

## Theoretical Framework

### The "Bottom of the Bowl"
In [[control theory]], we often define our coordinates such that the desired state (e.g., pointing at a star) is at the origin ($\mathbf{x}_e = 0$). This simplifies the math for **LQR** and **State Feedback**, as the controller’s job is simply to "drive the state to zero."

## Physical Interpretation

### The "Valley and Hill" Analogy
- **Stable Equilibrium:** A marble at the bottom of a bowl. If you push it, it rolls back to the center.
- **Unstable Equilibrium:** A marble balanced on top of a mountain. A tiny nudge causes it to roll away forever.
- **Neutral Equilibrium:** A marble on a flat table. If you push it, it stays in the new spot without trying to return or run away.

## Advantages and Limitations

### Strengths
1.  **Reference for Control:** Provides the "setpoint" for almost all spacecraft pointing maneuvers.
2.  **Passive Control:** Allows for "Zero-Fuel" missions by placing the spacecraft in a naturally stable equilibrium (like a Gravity Gradient boom).

### Limitations
1.  **Bistability:** Many spacecraft equilibria are symmetric. A satellite might accidentally stabilize "upside down" because both orientations satisfy $\dot{\mathbf{x}} = 0$.
2.  **Sensitivity:** In unstable equilibria (like Lagrange Point L1), the spacecraft must constantly fire tiny thrusters to avoid "falling off" the point.

## Applications

### Spacecraft Dynamics
1.  **[[Nadir]] Pointing:** The stable equilibrium for an Earth-imaging satellite in the LVLH frame.
2.  **[[Lagrange Points]] (L1-L5):** Equilibrium points in a three-body system (like Earth-Moon-Sun) where the gravitational pulls cancel out.
3.  **Spin Stabilization:** Determining the stable axis of rotation for a "Dual-Spin" satellite.

## See Also

- [[Lyapunov Stability Theorems]]
- [[Linearization]]
- [[LVLH Reference Frame]]
- [[Lagrange Points]]

## Recommended Tags:
#dynamics #equilibrium #stability #phase-portrait #control-theory #mathematics #spacecraft-guidance
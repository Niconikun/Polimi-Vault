## Formal Definition

An **Equilibrium State** is a condition of a dynamical system in which all state variables remain constant over time in the absence of external perturbations or control inputs. For a system represented in state-space as $\dot{\mathbf{x}} = f(\mathbf{x}, \mathbf{u})$, an equilibrium state $\mathbf{x}_e$ satisfies the condition that the state derivative vector is zero: $\dot{\mathbf{x}} = \mathbf{0}$. Physically, this implies that the forces and moments acting on the system are perfectly balanced, resulting in no acceleration or change in the system's energy configuration.



## Historical Development

### Key Milestones
- **1687:** **Isaac Newton** defines static equilibrium in *Philosophiæ Naturalis Principia Mathematica*, establishing that an object at rest stays at rest unless acted upon by a force.
- **1892:** **Aleksandr Lyapunov** provides the rigorous mathematical framework to classify these states based on their "neighborhood" behavior.
- **1950s:** The concept of "Relative Equilibrium" is developed for satellites, recognizing that a spacecraft can be in equilibrium relative to a rotating frame (like Earth) while still moving in an inertial frame.

### Foundational Contributors
1. **Leonhard Euler:** Formulated the equations for [[Rigid-Body Dynamics]], allowing for the identification of rotational equilibrium states.
2. **Aleksandr Lyapunov:** Defined the "Stability of Equilibrium," which is the core of modern GNC engineering.

## Mathematical Formulation

### The Equilibrium Condition
A state $\mathbf{x}_e$ is an equilibrium state if:
$$f(\mathbf{x}_e, \mathbf{u}_e) = \mathbf{0}$$

### Linearization around the State
To analyze the "health" of an equilibrium state, we look at the system's behavior when it is perturbed by a small amount $\delta \mathbf{x}$:
$$\dot{\mathbf{x}} \approx \mathbf{A} \delta \mathbf{x}$$
Where $\mathbf{A}$ is the [[Jacobian Matrix]] evaluated at the equilibrium state. The **Eigenvalues** of $\mathbf{A}$ determine if the state is:
- **Asymptotically Stable:** The system returns to the state.
- **Unstable:** The system diverges from the state.
- **Marginally Stable:** The system orbits the state (Libration).

## Fundamental Principles

### Core Assumptions
1. **Steady State:** Assumes that the inputs ($\mathbf{u}$) are also constant at the equilibrium point.
2. **Isolation:** Assumes no stochastic (random) noise is pushing the system out of the state.

### Governing Laws
- **The [[Principle of Minimum Potential Energy]]:** Systems naturally seek equilibrium states where their potential energy is at a local minimum (stable) or maximum/saddle (unstable).



## Theoretical Framework

### Types of Equilibrium in Aerospace
1.  **Static Equilibrium:** The spacecraft is not moving and not rotating (e.g., a lander on the Lunar surface).
2.  **Relative Equilibrium:** The spacecraft is rotating or moving at a constant rate that appears "fixed" in a specific reference frame (e.g., a **Geostationary** satellite or a **[[Nadir]]-pointing** satellite).
3.  **Dynamic Equilibrium:** A state where forces (like drag and thrust) are balanced, resulting in a constant velocity (e.g., terminal velocity during reentry).

## Physical Interpretation

### The "Balanced Scale" Analogy
Imagine a traditional balance scale. 
- When the weights on both sides are equal, the scale is in an **Equilibrium State**. 
- If you tap one side, it might oscillate and return to center (**Stable**), stay tilted (**Neutral**), or if it's a top-heavy scale, it might flip over entirely (**Unstable**).

## Advantages and Limitations

### Strengths
1.  **Fuel Efficiency:** Operating at a naturally stable equilibrium state (like a Gravity Gradient) allows a satellite to maintain its orientation without using any thruster propellant.
2.  **Safety:** Knowing the equilibrium states of a tumbling satellite helps ground controllers predict where it will eventually "settle."

### Limitations
1.  **Local vs. Global:** A system may be stable in a small "pocket" (Local Equilibrium) but completely unstable if pushed too far (Global Instability).
2.  **Non-Linearity:** In non-linear systems, equilibrium states can "disappear" or "split" as parameters change (Bifurcation).

## Applications

### Spacecraft Design
1.  **[[Gravity-Gradient Stabilization]]:** Designing the satellite's mass distribution so that the "Earth-pointing" state is a stable equilibrium.
2.  **[[Lagrange Points]]:** Utilizing the $L_1$ through $L_5$ points as equilibrium states for deep-space telescopes like James Webb (JWST).
3.  **Spin Stabilization:** Using the "Major Axis Rule" to ensure a spinning satellite stays in a stable rotational equilibrium state.

## See Also

- [[Equilibrium Point]]
- [[Lyapunov Stability Theorems]]
- [[Linearization]]
- [[Lagrange Points]]

## Recommended Tags:
#dynamics #equilibrium #stability #physics #control-theory #spacecraft-design #mathematics
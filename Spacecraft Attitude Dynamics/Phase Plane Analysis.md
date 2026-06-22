## Formal Definition

**Phase-Plane Analysis** is a graphical method for studying the behavior of second-order dynamical systems by plotting the system's states (typically position $x$ and velocity $\dot{x}$) against each other in a two-dimensional plane. Each point in this "Phase Plane" represents a unique state of the system, and the path the system takes over time is called a **Trajectory**. This technique is particularly powerful for non-linear systems—such as spacecraft with deadbands or saturation—because it allows engineers to visually identify equilibrium points, limit cycles, and stability regions without solving complex differential equations analytically.



## Historical Development

### Key Milestones
- **1880s:** **Henri Poincaré** develops the qualitative theory of differential equations, inventing the phase-plane to solve the "Three-Body Problem" in celestial mechanics.
- **1920s:** The method is refined for electrical engineering to analyze oscillators and [[vacuum]] tube circuits.
- **1960s:** NASA engineers use phase-plane logic to design the **Apollo Reaction Control System (RCS)**, allowing the flight computer to decide when to "pulse" thrusters based on the satellite's position in the plane.

### Foundational Contributors
1. **Henri Poincaré:** The mathematician who shifted the focus from finding "exact formulas" to understanding the "geometric shape" of a system's behavior.
2. **Aleksandr Lyapunov:** Used phase-plane geometry to define his "Direct Method" for stability analysis.

## Mathematical Formulation

### The Phase Vector
For a second-order system $\ddot{x} = f(x, \dot{x})$, we define the state vector as:
$$\mathbf{x} = \begin{bmatrix} x \\ \dot{x} \end{bmatrix}$$

### The Vector Field
The "slope" of the trajectory at any point in the plane is given by the ratio of the state derivatives:
$$\frac{d\dot{x}}{dx} = \frac{\ddot{x}}{\dot{x}} = \frac{f(x, \dot{x})}{\dot{x}}$$
By plotting these slopes as small arrows at every point, we create a **Vector Field** or **Phase Portrait**.



## Fundamental Principles

### Core Assumptions
1. **Second-Order Limitation:** Standard phase-plane analysis is limited to two dimensions (two states). For a 6-DOF spacecraft, we usually look at one axis (e.g., Pitch and Pitch-rate) at a time.
2. **Autonomy:** Assumes the system's rules don't change over time (Time-Invariant).

### Governing Laws
- **Uniqueness of Trajectories:** In a deterministic system, trajectories can never cross each other in the phase plane.

## Theoretical Framework

### Common Phase-Plane Features
1.  **Singular Points:** Points where $\dot{x} = 0$ and $\ddot{x} = 0$ (Equilibrium Points).
2.  **Isoclines:** Lines in the plane where the trajectory slope is constant, used to hand-draw phase portraits.
3.  **Separatrix:** A boundary trajectory that separates two different types of behavior (e.g., the line between "stable orbiting" and "unstable falling").

## Physical Interpretation

### The "Mountain Map" Analogy
Imagine a marble rolling on a wavy landscape.
- The **X-axis** is the marble's position.
- The **Y-axis** is the marble's speed.
The Phase Plane is the "Topographical Map" of this landscape. It tells you that if you start at a certain height with a certain speed, you will either roll into a valley (**Stable Node**), circle around the bottom (**Center**), or fly off a cliff (**Unstable Source**).

## Advantages and Limitations

### Strengths
1.  **Visual Intuition:** You can see "at a glance" if a system will oscillate, settle, or explode.
2.  **Non-linear Friendly:** It handles "Bang-Bang" switching and friction perfectly, which Laplace transforms cannot.

### Limitations
1.  **Dimension Wall:** It is very difficult to visualize systems with more than two or three states.
2.  **No Time Scale:** While the path is clear, it's hard to tell from a standard plot *how long* it takes to move along a trajectory.

## Applications

### Spacecraft GNC
1.  **[[Thruster]] Logic Design:** Designing "Switching Lines" in the phase plane. If the state crosses a line, the [[thruster]] fires to "kick" the state back toward the origin.
2.  **Docking Maneuvers:** Visualizing the relative position and velocity of two spacecraft to ensure a safe "approach cone."
3.  **Nutation Analysis:** Studying the "wobble" of a spinning satellite to ensure it stays within a stable [[Limit Cycle]].

## See Also

- [[Limit Cycle]]
- [[Equilibrium State]]
- [[Bang-Bang Control]]
- [[Deadband]]

## Recommended Tags:
#nonlinear-dynamics #phase-plane #state-space #geometry #stability #GNC #aerospace-engineering
## Formal Definition

**Linearization** is the process of finding a linear approximation to a non-linear system at a specific operating point, known as the **Equilibrium** or **Nominal Trajectory**. Mathematically, this is achieved using a first-order **[[Taylor Series Expansion]] Expansion**. By assuming that the spacecraft will stay "close" to this nominal state, engineers can simplify the complex, non-linear equations of motion into a local linear model. This allows for the use of powerful tools like LQR, PID, and Kalman Filters, which would otherwise be mathematically intractable for non-linear systems.



## Historical Development

### Key Milestones
- **1715:** **Brook Taylor** publishes the [[Taylor Series Expansion]], providing the mathematical foundation for approximating functions.
- **1892:** **Aleksandr Lyapunov** proves that if a linearized system is stable, the original non-linear system is also locally stable (Lyapunov’s First Method).
- **1960s:** Linearization becomes the cornerstone of the **Apollo Guidance Computer**, as it allows for real-time trajectory corrections using limited processing power.

### Foundational Contributors
1. **Brook Taylor (1685–1731):** Developed the series expansion that serves as the engine for linearization.
2. **Aleksandr Lyapunov:** Formalized the "Indirect Method" of stability analysis via linearization.

## Mathematical Formulation

### The Non-Linear System
Most spacecraft dynamics follow the form:
$$\dot{\mathbf{x}} = f(\mathbf{x}, \mathbf{u})$$

### The [[Taylor Series Expansion]] Expansion
We expand the function $f$ around a nominal point $(\mathbf{x}_0, \mathbf{u}_0)$:
$$\dot{\mathbf{x}} \approx f(\mathbf{x}_0, \mathbf{u}_0) + \frac{\partial f}{\partial \mathbf{x}}\bigg|_{\mathbf{x}_0, \mathbf{u}_0} (\mathbf{x} - \mathbf{x}_0) + \frac{\partial f}{\partial \mathbf{u}}\bigg|_{\mathbf{x}_0, \mathbf{u}_0} (\mathbf{u} - \mathbf{u}_0)$$

### The Jacobian Matrices
The "slopes" of these non-linear functions are organized into matrices called **Jacobians**:
- **System Matrix ($\mathbf{A}$):** $\mathbf{A} = \frac{\partial f}{\partial \mathbf{x}}$
- **Input Matrix ($\mathbf{B}$):** $\mathbf{B} = \frac{\partial f}{\partial \mathbf{u}}$

This results in the familiar linear form: $\Delta\dot{\mathbf{x}} = \mathbf{A}\Delta\mathbf{x} + \mathbf{B}\Delta\mathbf{u}$.



## Fundamental Principles

### Core Assumptions
1. **Small Perturbations:** Linearization is only valid if the state stays very close to the nominal point. If a satellite tumbles wildly, the "linear" model will fail.
2. **Differentiability:** The non-linear function must be "smooth" (no sudden jumps or discontinuities).

### Governing Laws
- **Lyapunov’s Linearization Theorem:** States that the stability of the non-linear system is identical to the linear system, provided the eigenvalues of the linear system do not have a real part of zero.

## Theoretical Framework

### The "Operating Point"
Linearization is like taking a magnifying glass to a circle. If you zoom in far enough on any part of the circle, it looks like a straight line. 
- In **Attitude Control**, we often linearize around "[[Nadir]]-pointing." 
- In **Orbital Mechanics**, we linearize around a "Circular Orbit."
As long as the satellite doesn't drift too far from that "zoom-in" point, the straight-line math works perfectly.

## Physical Interpretation

### The "Local Flat Earth" Analogy
On a global scale, the Earth is curved. If you are planning a flight from London to Tokyo, you need complex spherical geometry. However, if you are building a house, you can assume the ground is perfectly flat. Linearization is the act of "flattening" the local neighborhood of your spacecraft's state so you can use simple geometry to control it.

## Advantages and Limitations

### Strengths
1.  **Enables Modern Control:** Without it, we couldn't use LQR, H-infinity, or standard Kalman Filters.
2.  **Computational Speed:** Linear equations are much faster for a flight computer to solve than non-linear ones.

### Limitations
1.  **Locality:** The model "breaks" if the spacecraft moves too far from the [[equilibrium point]].
2.  **Missing Physics:** Linearization discards "higher-order terms" (like $\Delta x^2$). In high-precision missions or extreme tumbles, these missing terms can cause the controller to fail.

## Applications

### Spacecraft Engineering
1.  **[[Extended Kalman Filter]] (EKF):** The EKF linearizes the orbit/attitude equations at every single time step to track the satellite.
2.  **Stability Analysis:** Determining if a satellite will remain stable after a small thruster firing.
3.  **Gain Scheduling:** Using different linear models for different parts of a mission (e.g., one model for "Cruise" and another for "Landing").

## See Also

- [[State-Space Representation]]
- [[Lyapunov Stability Theorems]]
- [[Kalman Filter]]
- [[Equilibrium Point]]

## Recommended Tags:
#mathematics #linearization #control-theory #Taylor-series #Jacobian #modeling #spacecraft-dynamics
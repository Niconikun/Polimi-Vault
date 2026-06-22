## Formal Definition

The **First Companion Form** is a specific structure for the [[State-Space Representation]] of a linear system where the coefficients of the system's **characteristic polynomial** appear directly in the last row (or column, depending on convention) of the $\mathbf{A}$ matrix. In this form, the state variables are chosen such that each state is the derivative of the previous one (i.e., $x_2 = \dot{x}_1, x_3 = \dot{x}_2$). This representation is mathematically "canonical" because any controllable single-input system can be transformed into this form, simplifying the calculation of feedback gains for [[pole placement]].



## Historical Development

### Key Milestones
- **Early 20th Century:** Mathematicians studying linear differential equations identify "companion matrices" as a way to relate a matrix to its [[characteristic equation]].
- **1960s:** With the rise of **Modern Control Theory**, the companion form is adopted as a standard tool for designing "[[Pole Placement]]" controllers, as it bypasses the need for complex matrix inversions.
- **Present:** While flight software rarely uses companion forms for real-time integration (due to numerical sensitivity), they remain the primary pedagogical tool for teaching state-space design.

### Foundational Contributors
1. **Rudolf Kalman:** Utilized canonical forms to prove the fundamental properties of controllability.
2. **Frobenius:** The "Frobenius Companion Matrix" is the mathematical namesake for this structure in [[linear algebra]].

## Mathematical Formulation

For a system with a [[characteristic equation]]:
$$s^n + a_{n-1}s^{n-1} + \dots + a_1s + a_0 = 0$$

The **First Companion Form** (Controller Canonical) is structured as follows:

### The System Matrix ($\mathbf{A}$)
$$\mathbf{A} = \begin{bmatrix} 
0 & 1 & 0 & \dots & 0 \\
0 & 0 & 1 & \dots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \dots & 1 \\
-a_0 & -a_1 & -a_2 & \dots & -a_{n-1}
\end{bmatrix}$$

### The Input Matrix ($\mathbf{B}$)
$$\mathbf{B} = \begin{bmatrix} 0 \\ 0 \\ \vdots \\ 0 \\ 1 \end{bmatrix}$$

## Fundamental Principles

### Core Assumptions
1. **Controllability:** A system can only be transformed into this form if it is **Fully Controllable**.
2. **Single-Input:** This specific structure is designed for Single-Input Single-Output (SISO) systems.

### Governing Laws
- **Similarity Transformation:** You can move from any state-space model $(\mathbf{A, B})$ to the Companion Form $(\mathbf{A}_c, \mathbf{B}_c)$ using a transformation matrix $\mathbf{T}$ built from the **Controllability Matrix**.

## Theoretical Framework

### The "Shortcut" to [[Pole Placement]]
The beauty of the First Companion Form is that the feedback gain matrix $\mathbf{K}$ is trivial to calculate. If you want the closed-loop system to have a new [[characteristic equation]] with coefficients $\alpha_i$, the required gains are simply:
$$k_i = \alpha_i - a_i$$
You can practically "read" the required control gains off the page without running complex algorithms.

## Physical Interpretation

### The "Chain of Integrators"
Think of the First Companion Form as a line of people holding hands. 
- The first person's position is $x_1$. 
- The second person ($x_2$) is how fast the first person is moving.
- The third person ($x_3$) is how fast the second person is moving.
- Only the **very last person** in the line can be pushed by the actuator ($\mathbf{B}$). 
The "Companion" part comes from the fact that the last person is also the only one who knows the "rules" (the coefficients $a_i$) that keep the whole line together.

## Advantages and Limitations

### Strengths
1.  **Design Simplicity:** Makes [[pole placement]] by hand possible, even for high-order systems.
2.  **Insight:** Shows the direct mathematical link between a [[Transfer Function]] (Laplace) and a state-space model.

### Limitations
1.  **Numerical Instability:** For high-order systems (e.g., $n > 10$), the coefficients $a_i$ can become massive, leading to "Rounding Errors" that can crash a flight computer.
2.  **Non-Physical States:** The states ($x_1, x_2, \dots$) in this form are purely mathematical; they rarely correspond to something you can actually touch or measure, like "Volts" or "Pressure."

## Applications

### Control System Design
1.  **Ackermann’s Formula:** The math behind this famous pole-placement formula relies on the properties of the Companion Form.
2.  **Filter Design:** Building digital filters wher[[Transfer Function|e the coefficient]]s of the [[transfer function]] are known.
3.  **Instructional Modeling:** The standard way students learn to convert a differential equation into a matrix.

## See Also

- [[State-Space Representation]]
- [[Controllability]]
- [[Full State Feedback Control]]
- [[Characteristic Equation]]

## Recommended Tags:
#control-theory #state-space #companion-form #canonical-forms #linear-algebra #mathematics #pole-placement
## Formal Definition

The **Second Companion Form** is a specific state-space structure where the coefficients of the system's characteristic polynomial are arranged in the first column (or row, depending on convention) of the $\mathbf{A}$ matrix. In this form, the system is organized such that the sensor output ($\mathbf{y}$) is directly tied to the first state, and the remaining states act as a chain that "observes" the error. It is the "Dual" of the Controller Canonical Form; whereas the first form is focused on how inputs $(\mathbf{B})$ flow into the state, the second form is focused on how states flow into the output $(\mathbf{C})$.



## Historical Development

### Key Milestones
- **1960:** **Rudolf Kalman** establishes the Principle of Duality, proving that for every controllable system, there is an observable "mirror" system.
- **1964:** **David Luenberger** uses this form to simplify the construction of his eponymous "Luenberger Observer," showing that observer gains can be picked just as easily as controller gains.
- **Present:** This form is the theoretical basis for "Output Feedback" designs, where the full internal state isn't known and must be reconstructed from sensor data.

### Foundational Contributors
1. **David Luenberger:** The primary proponent of using this form to build state estimators.
2. **Rudolf Kalman:** Provided the duality proof that links the first and second companion forms.

## Mathematical Formulation

For a system with a [[characteristic equation]]:
$$s^n + a_{n-1}s^{n-1} + \dots + a_1s + a_0 = 0$$

The **Second Companion Form** (Observer Canonical) is structured as:

### The System Matrix ($\mathbf{A}$)
$$\mathbf{A} = \begin{bmatrix} 
-a_{n-1} & 1 & 0 & \dots & 0 \\
-a_{n-2} & 0 & 1 & \dots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
-a_1 & 0 & 0 & \dots & 1 \\
-a_0 & 0 & 0 & \dots & 0
\end{bmatrix}$$

### The Output Matrix ($\mathbf{C}$)
$$\mathbf{C} = \begin{bmatrix} 1 & 0 & \dots & 0 & 0 \end{bmatrix}$$

*Note: In this form, the Input Matrix ($\mathbf{B}$) contains the coefficients of the [[transfer function]]'s numerator.*

## Fundamental Principles

### Core Assumptions
1. **[[Observability]]:** A system can only be transformed into this form if it is **Fully Observable**.
2. **Duality:** The $\mathbf{A}$ matrix of the Second Companion Form is the **transpose** of the $\mathbf{A}$ matrix of the [[First Companion Form]] (with coefficients re-indexed).

### Governing Laws
- **The [[Duality Principle]]:** Designing an observer for $(\mathbf{A, C})$ is mathematically identical to designing a controller for $(\mathbf{A}^T, \mathbf{C}^T)$.

## Theoretical Framework

### The Shortcut to Observer Design
In this form, the observer gain matrix $\mathbf{L}$ is incredibly simple to calculate. If you want the observer's error to decay according to a new polynomial with coefficients $\gamma_i$, the gains are:
$$l_i = \gamma_i - a_i$$
Just like the first form allowed you to "read" controller gains, this allows you to "read" the gains needed to make your sensors accurately reconstruct the spacecraft's state.

## Physical Interpretation

### The "Information Relay"
If the [[First Companion Form]] is a line of people where only the last person can be pushed, the Second Companion Form is a line where **only the first person can talk** (the sensor $\mathbf{C}$).
- The first person tells you what they see.
- They then pass information down the line to the second, third, and fourth person.
- Each person in the line uses the "rules" of the system (the coefficients $a_i$) to figure out what the person behind them must be doing.

## Advantages and Limitations

### Strengths
1.  **Observer Simplicity:** Simplifies the math for Kalman Filters and Luenberger Observers.
2.  **[[Transfer Function]] Mapping:** Directly relates the "Zeroes" of a [[transfer function]] to the $\mathbf{B}$ matrix.

### Limitations
1.  **Numerical Sensitivity:** Like the first form, it is prone to rounding errors in high-order systems.
2.  **Abstract States:** The state variables ($x_1, x_2...$) do not usually correspond to physical units like "angle" or "[[Angular Velocity]]."

## Applications

### State Estimation
1.  **Luenberger Observers:** The primary canonical form used to teach how to "place" observer poles.
2.  **[[Signal Processing]]:** Used in the realization of digital filters (IIR filters).
3.  **Fault Detection:** Using the structured error of the observer to identify when a sensor has failed.

## See Also

- [[First Companion Form]]
- [[State Observer]]
- [[Observability]]
- [[Duality Principle]]

## Recommended Tags:
#control-theory #state-space #observer-form #canonical-forms #duality #mathematics #state-estimation
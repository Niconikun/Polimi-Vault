---
title: Lyapunov Stability
tags:
  - control theory
  - dynamical systems
  - stability analysis
  - nonlinear systems
---

# Lyapunov Stability

## Formal Definition

**Lyapunov stability** is a rigorous mathematical framework for analyzing the stability of equilibrium points in [[Dynamical Systems|dynamical systems]] without explicitly solving differential equations. A system is stable in the Lyapunov sense if trajectories starting near an equilibrium point remain near it for all future time. Lyapunov theory provides necessary and sufficient conditions for stability through energy-like functions ([[Lyapunov Functions]]) and is fundamental to [[Control Systems]], nonlinear dynamics analysis, and [[Control Theory]].

## Historical Development

### Key Milestones
- **1892:** Alexander Mikhailovich Lyapunov publishes foundational stability theory
- **1902:** Lyapunov's monograph translated; limited initial impact
- **1950s–1960s:** Rediscovery; applications to aerospace control systems
- **1960s–1970s:** Krasovskii, Popov extend theory; absolute stability developed
- **1980s–1990s:** Nonlinear control renaissance; robust Lyapunov methods
- **2000s–Present:** Adaptive control, networked systems, hybrid systems

### Foundational Contributors
1. **Alexander Mikhailovich Lyapunov (1857–1918):** Founder of modern stability theory
2. **Henri Poincaré (1854–1912):** Concurrent geometric approach to stability
3. **Nikolai Krasovskii (1910–1993):** Extensions to nonlinear systems
4. **Vladimir Popov (1928–1997):** Absolute stability and frequency-domain methods
5. **Hassan Khalil (1950–):** Modern nonlinear control perspective

## Mathematical Formulation

### Dynamical System and Equilibrium

**Autonomous system:**
$$
\dot{\mathbf{x}} = \mathbf{f}(\mathbf{x})
$$

Where $\mathbf{x} \in \mathbb{R}^n$ is state vector, $\mathbf{f}: \mathbb{R}^n \to \mathbb{R}^n$ is smooth.

**Equilibrium point:**
$$
\mathbf{x}^* : \mathbf{f}(\mathbf{x}^*) = \mathbf{0}
$$

Typically consider $\mathbf{x}^* = \mathbf{0}$ (origin) without loss of generality via coordinate transformation.

### Definitions of Stability

**Lyapunov Stable:**

Equilibrium $\mathbf{x}^* = \mathbf{0}$ is stable if:
$$
\forall \epsilon > 0, \exists \delta > 0: \|\mathbf{x}(0)\| < \delta \Rightarrow \|\mathbf{x}(t)\| < \epsilon \, \forall t \geq 0
$$

Trajectories near equilibrium remain near.

**Asymptotically Stable:**

Equilibrium is stable AND attractive:
$$
\|\mathbf{x}(0)\| < \delta \Rightarrow \lim_{t \to \infty} \mathbf{x}(t) = \mathbf{0}
$$

Trajectories converge to equilibrium.

**Exponentially Stable:**

Convergence rate bounded:
$$
\|\mathbf{x}(t)\| \leq c\|\mathbf{x}(0)\| e^{-\lambda t}
$$

For constants $c, \lambda > 0$.

**Globally Asymptotically Stable:**

Asymptotically stable for all initial conditions:
$$
\forall \mathbf{x}(0) \in \mathbb{R}^n: \lim_{t \to \infty} \mathbf{x}(t) = \mathbf{0}
$$

**Unstable:**

Negation of stability; trajectories diverge from equilibrium.

## Lyapunov Functions

### First Method (Linearization)

**Linear approximation near equilibrium:**
$$
\dot{\mathbf{x}} \approx \mathbf{A} \mathbf{x}, \quad \mathbf{A} = \left.\frac{\partial \mathbf{f}}{\partial \mathbf{x}}\right|_{\mathbf{x}=0}
$$

**Linearization Theorem:**
- If all eigenvalues of $\mathbf{A}$ have negative real parts $\Rightarrow$ origin asymptotically stable
- If any eigenvalue has positive real part $\Rightarrow$ origin unstable
- Eigenvalues on imaginary axis $\Rightarrow$ linearization inconclusive

### Second Method (Lyapunov Functions)

**Lyapunov function** $V(\mathbf{x})$ with properties:

1. $V(\mathbf{0}) = 0$
2. $V(\mathbf{x}) > 0$ for all $\mathbf{x} \neq \mathbf{0}$ (positive definite)
3. $\dot{V}(\mathbf{x}) = \nabla V \cdot \mathbf{f}(\mathbf{x}) \leq 0$ (non-increasing along trajectories)

**Theorem (Basic Lyapunov):**

If such $V$ exists $\Rightarrow$ origin is (Lyapunov) stable.

If additionally $\dot{V}(\mathbf{x}) < 0$ for $\mathbf{x} \neq \mathbf{0}$ $\Rightarrow$ origin asymptotically stable.

### Interpretation

**Energy analogy:** If $V(\mathbf{x})$ is "energy-like":
- Positive definite: energy zero only at equilibrium
- $\dot{V} \leq 0$: energy non-increasing (dissipative)
- $\dot{V} < 0$: energy strictly decreasing → convergence

**Example:** Damped oscillator
$$
\ddot{x} + 2\zeta\omega_n \dot{x} + \omega_n^2 x = 0
$$

Lyapunov function:
$$
V(x, \dot{x}) = \frac{1}{2}\dot{x}^2 + \frac{1}{2}\omega_n^2 x^2
$$

(Total mechanical energy). $\dot{V} = -2\zeta\omega_n \dot{x}^2 < 0$ ensures stability.

## Regional Stability

### Basin of Attraction

**Region of attraction:**
$$
R_A = \{\mathbf{x}(0) : \lim_{t \to \infty} \mathbf{x}(t) = \mathbf{0}\}
$$

Set of initial conditions converging to equilibrium.

**Estimate via Lyapunov function:**

Level set $\Omega_c = \{\mathbf{x} : V(\mathbf{x}) \leq c\}$

If $\dot{V}(\mathbf{x}) < 0$ in region $\Omega_c$ $\Rightarrow \Omega_c \subset R_A$

**Application:** Size of allowable disturbances for feedback control.

### Domain of Attraction

**For nonlinear systems:** Often limited domain (unlike linear systems)

Example: Nonlinear pendulum $\ddot{\theta} + g\sin(\theta) = 0$

- Equilibrium at $\theta = 0$ locally asymptotically stable
- Basin of attraction: $\{(\theta, \dot{\theta}) : E < 2mgl\}$ (bounded)
- Trajectories with $E > 2mgl$ escape to infinity

## Application to Control Design

### Feedback Stabilization

**Given unstable system:** $\dot{\mathbf{x}} = \mathbf{f}(\mathbf{x}, \mathbf{u})$

**Design feedback:** $\mathbf{u} = \mathbf{k}(\mathbf{x})$ to stabilize closed-loop:
$$
\dot{\mathbf{x}} = \mathbf{f}(\mathbf{x}, \mathbf{k}(\mathbf{x}))
$$

**Lyapunov approach:**

1. Propose candidate Lyapunov function $V(\mathbf{x})$
2. Require $\dot{V}(\mathbf{x}) = \nabla V \cdot \mathbf{f}(\mathbf{x}, \mathbf{k}(\mathbf{x})) < 0$
3. Solve for control law $\mathbf{k}(\mathbf{x})$

### Linear Systems

**LQR ([[Linear Quadratic Regulator]]):**

For $\dot{\mathbf{x}} = \mathbf{A}\mathbf{x} + \mathbf{B}\mathbf{u}$, optimal control minimizes:
$$
J = \int_0^\infty (\mathbf{x}^T \mathbf{Q} \mathbf{x} + \mathbf{u}^T \mathbf{R} \mathbf{u}) \, dt
$$

**Lyapunov function:** $V(\mathbf{x}) = \mathbf{x}^T \mathbf{P} \mathbf{x}$ (positive definite)

**Closed-loop guarantee:** $\dot{V} < 0$ $\Rightarrow$ asymptotic stability.

### Nonlinear Systems

**Backstepping:**

Recursive control design using nested Lyapunov functions.

Example: System $\dot{x}_1 = x_2$, $\dot{x}_2 = -x_1 + u$

- Step 1: Virtual control $x_2^* = -x_1$ stabilizes $x_1$ subsystem
- Step 2: Design $u$ to stabilize $x_2 = x_2^* + z_2$ tracking error
- Global control: $u = -x_1 - 2(x_2 + x_1)$

## Connection to Other Stability Concepts

### Input-to-State Stability (ISS)

**Robustness to input disturbances:**
$$
\|\mathbf{x}(t)\| \leq \beta(\|\mathbf{x}(0)\|, t) + \gamma(\|\mathbf{u}\|_\infty)
$$

**Lyapunov characterization:** ISS equivalent to existence of ISS-Lyapunov function.

### Passivity

**System with input $\mathbf{u}$, output $\mathbf{y}$:**
$$
\int_0^t \mathbf{u}^T(\tau) \mathbf{y}(\tau) \, d\tau \geq -c
$$

**Lyapunov connection:** Storage function = Lyapunov function for passive systems.

### Invariant Sets

**Invariant set** $\Omega$ under $\dot{\mathbf{x}} = \mathbf{f}(\mathbf{x})$:
$$
\mathbf{x}(0) \in \Omega \Rightarrow \mathbf{x}(t) \in \Omega \, \forall t
$$

**Application:** Level sets of Lyapunov function are invariant.

## Practical Analysis Methods

### Quadratic Lyapunov Functions

For linear systems $\dot{\mathbf{x}} = \mathbf{A}\mathbf{x}$:

**Try:** $V(\mathbf{x}) = \mathbf{x}^T \mathbf{P} \mathbf{x}$

**Condition:** $\mathbf{A}^T \mathbf{P} + \mathbf{P}\mathbf{A} = -\mathbf{Q}$ (Lyapunov equation)

For $\mathbf{Q}$ positive definite, solution $\mathbf{P}$ exists and is positive definite $\Leftrightarrow$ $\mathbf{A}$ Hurwitz (stable).

### Computational Methods

**LMI (Linear Matrix Inequality) formulation:**

For nonlinear systems with polytopic uncertainty, formulate stability as optimization:
$$
\min_{\mathbf{P}} \, \text{subject to} \, \mathbf{A}^T \mathbf{P} + \mathbf{P}\mathbf{A} + \mathbf{Q} \preceq 0
$$

Solved via convex optimization (semi-definite programming).

### Perturbation Analysis

**Robustness margin:** How much uncertainty can system tolerate?

**Small gain theorem:** Sufficient condition for robust stability of feedback interconnections.

## Applications

### Spacecraft [[Attitude Control]]

**Three-axis stabilization:** Lyapunov design for magnetic torquers

Choose $V = \frac{1}{2}\boldsymbol{\omega}^T \mathbf{I} \boldsymbol{\omega} + k(\mathbf{q})$ (energy + quaternion potential)

Verify $\dot{V} < 0$ to guarantee detumbling and attitude stabilization.

### Adaptive Control

**Unknown parameters:** Design adaptive law using Lyapunov analysis

Example: Unknown gain $\theta$ in system $\dot{x} = -x + \theta x u$

**Lyapunov function:** $V = \frac{1}{2}x^2 + \frac{1}{2\gamma}(\theta - \hat{\theta})^2$

**Adaptive law:** $\dot{\hat{\theta}} = \gamma x^2 u$ ensures $\dot{V} \leq 0$.

### Power Systems Stability

**Transient stability:** Post-fault recovery of power grid

Lyapunov methods analyze if system returns to equilibrium after fault clearing.

### Biological Systems

**Population dynamics:** Predator-prey systems (Lotka-Volterra)

Lyapunov function identifies stable population distributions.

## Advanced Topics

### Time-Varying Systems

**Lyapunov-Krasovskii functional** for time-delay systems:
$$
V(t) = \int_{t-h}^t \mathbf{x}(\tau)^T \mathbf{Q} \mathbf{x}(\tau) \, d\tau
$$

Generalization to systems with memory (differential delay equations).

### Stochastic Systems

**Stochastic Lyapunov equation** for systems with noise:
$$
\dot{\mathbf{x}} = \mathbf{f}(\mathbf{x}) + \mathbf{g}(\mathbf{x})\mathbf{w}(t)
$$

Lyapunov exponents characterize stability in presence of randomness.

### Sum-of-Squares Programming

**SOS decomposition:** Express Lyapunov function as sum of squares of polynomials

Enables computational verification for polynomial systems.

## See Also

- [[Control Theory]]
- [[Control Systems]]
- [[Dynamical Systems]]
- [[Nonlinear Systems]]
- [[Stability Analysis]]
- [[Linear Quadratic Regulator]]
- [[Feedback Control]]
- [[Convergence]]
- [[Equilibrium Point]]

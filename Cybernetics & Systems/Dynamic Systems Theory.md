## 1. Core Tenets
### 1.1. [[State-Space Representation]] Representation
- **Definition**: Systems are described by **state variables** that evolve over time according to **differential equations** or **difference equations**. The **[[State-Space Representation]]** captures all possible configurations of the system.
- **Cybernetic Link**: Aligns with **control theory** (Wiener, 1948) and **[[Systems Theory]]** (Bertalanffy, 1968). The system's behavior is a **trajectory** through [[State-Space Representation]].
  - *Example*: A pendulum's state is fully described by its angle $\theta$ and [[Angular Velocity]] $\dot{\theta}$, evolving according to $\ddot{\theta} = -\frac{g}{L}\sin\theta$.

### 1.2. Nonlinear Dynamics
- **Definition**: Systems exhibit **nonlinear** relationships between variables, leading to **emergent behaviors** such as **attractors**, **bifurcations**, and **chaos**.
- **Cybernetic Link**: Resonates with **complex [[Systems Theory]]** and **synergetics** (Haken, 1977). Small changes in parameters can lead to **qualitative shifts** in system behavior.
  - *Formalism*: For a system with state $\mathbf{x} \in \mathbb{R}^n$:
    $$
    \dot{\mathbf{x}} = f(\mathbf{x}, t, \mathbf{u}),
    $$
    where $f$ is a nonlinear function and $\mathbf{u}$ are control inputs.

### 1.3. Attractors and Stability
- **Definition**: Systems evolve toward **attractor states** (fixed points, limit cycles, strange attractors) that represent **stable patterns** of behavior. Stability is determined by the **basin of attraction**.
- **Cybernetic Link**: Connects to **homeostasis** (Ashby, 1956) and **adaptive systems**. Attractors represent **viable states** that the system tends to maintain.
  - *Example*: A neural network's learned weights form an attractor in the parameter space, representing a stable solution to the learning problem.

### 1.4. [[Self-Organization]]
- **Definition**: Systems can **spontaneously develop order** through local interactions, without external control. This emerges from the **dynamics of the system** rather than pre-programmed rules.
- **Cybernetic Link**: Aligns with **[[Autopoiesis]]** (Maturana & Varela, 1980) and **synergetics**. Self-organization is a **fundamental property** of [[Complex Adaptive Systems]].
  - *Implication*: Flocks of birds exhibit coordinated motion through simple local rules, leading to emergent global patterns.

---

## 2. Formal Axioms
### Axiom 1: State Space Dynamics
A system $S$ is *dynamic* iff:
1. Its state $\mathbf{x}(t) \in \mathbb{R}^n$ evolves according to a **differential equation**:
   $$
   \dot{\mathbf{x}} = f(\mathbf{x}, t, \mathbf{u}),
   $$
   or a **difference equation** for discrete-time systems:
   $$
   \mathbf{x}_{t+1} = f(\mathbf{x}_t, t, \mathbf{u}_t).
   $$

### Axiom 2: Attractor Existence
A system $S$ exhibits **self-organization** iff:
$$
\exists \text{ attractor } A \subset \mathbb{R}^n: \lim_{t \to \infty} \mathbf{x}(t) \in A \quad \forall \mathbf{x}_0 \in B(A),
$$
where $B(A)$ is the basin of attraction of $A$.

### Axiom 3: Structural Stability
A system $S$ is **structurally stable** iff small perturbations to $f$ do not qualitatively change the system's **phase portrait** (e.g., number and type of attractors).

---

## 3. Cybernetic Frameworks Aligned with Dynamic Systems Theory
| **Framework**                    | **Connection to Dynamic Systems Theory**                                                                    |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **[[First-Order Cybernetics]]**  | Uses **[[State-Space Representation]] models** for control (e.g., [[Kalman Filter]]s, [[PID Controller]]s). |
| **[[Second-Order Cybernetics]]** | Describes **observer-system dynamics** as a coupled system (von Foerster, 1974).                            |
| **[[Autopoiesis]]**              | Models **self-producing systems** as attractors in state space (Maturana & Varela, 1980).                   |
| **[[Synergetics]]**              | Studies **emergent order** in complex systems (Haken, 1977).                                                |
| **[[Chaos Theory]]**             | Analyzes **sensitive dependence on initial conditions** (Lorenz, 1963).                                     |

---

## 4. Contrast with Other Theories
| **Theory**               | **Relation to Dynamic Systems Theory**                                                                   |
|--------------------------|----------------------------------------------------------------------------------------------------------|
| **Classical Cognitive Science** | Conflicts: Rejects **discrete symbol manipulation** in favor of **continuous state evolution**.         |
| **Connectionism**        | Compatible: Neural networks are **dynamic systems** with attractor states (e.g., Hopfield networks).   |
| **Embodied Cognition**   | Compatible: Both emphasize **real-time, context-dependent** processes.                                   |
| **[[Enactivism]]**           | Compatible: Cognition is a **trajectory** in the agent-environment state space (Thelen & Smith, 1994).  |

---

## 5. Example: Dynamic Systems in Neuroscience and Robotics
### 5.1. Neuroscience Example: Neural Fields
- **Scenario**: Modeling population dynamics in the visual cortex.
  - **DST Interpretation**:
    - Neural activity $u(\mathbf{x}, t)$ evolves according to a **partial differential equation**:
      $$
      \tau \dot{u} = -u + h + \int w(\mathbf{x}-\mathbf{x}')r(u(\mathbf{x}', t)) \, d\mathbf{x}',
      $$
      where $w$ is the connectivity kernel and $r$ is the firing rate.
    - **Attractors** represent perceived patterns (e.g., edges, orientations).

### 5.2. Robotics Example: Dynamic Walking
- **Scenario**: A passive-dynamic walker on a slope.
  - **DST Interpretation**:
    - The walker's state (angle, [[Angular Velocity]]) follows **nonlinear dynamics**:
      $$
      \ddot{\theta} = \frac{g}{L}\sin(\theta - \alpha) - \frac{\dot{\theta}^2}{L}\sin(\theta - 2\alpha),
      $$
      where $\alpha$ is the slope angle.
    - **Limit cycles** emerge as stable gait patterns without active control.

---

## 6. Criticisms and Rebuttals
| **Criticism**                          | **Dynamic Systems Theory Response**                                                                       |
|----------------------------------------|----------------------------------------------------------------------------------------------------------|
| *"DST is too mathematical."*           | **Qualitative tools** (e.g., phase portraits, bifurcation diagrams) provide intuitive insights.          |
| *"It ignores symbolic processing."*    | **Hybrid models** combine dynamic and symbolic systems (e.g., dynamic neural fields + symbols).         |
| *"It’s hard to apply to cognition."*    | **Cognitive dynamics** (e.g., decision-making as a trajectory in state space) are well-studied (Kelso, 1995). |

---

## 7. Formal Summary
Dynamic Systems Theory is a **mathematical, state-based, and emergent** framework where:
1. **Behavior** = **trajectories** in a high-dimensional state space.
2. **Stability** = **attractors** and their basins of attraction.
3. **Complexity** = **nonlinear interactions** leading to self-organization.

**Key Equation**:
For a system with state $\mathbf{x} \in \mathbb{R}^n$:
$$
\dot{\mathbf{x}} = f(\mathbf{x}, t, \mathbf{u}).
$$

---
### Tags
#dynamics #systems-theory #cybernetics #nonlinear #complexity #attractors #self-organization

---
### Suggested Additions:
1. **Diagrams** (Excalidraw):
   - A **phase portrait** showing attractors (fixed points, limit cycles).
   - A **bifurcation diagram** (e.g., logistic map).
2. **Links**:
   - Connect to [[First-Order Cybernetics]], [[Second-Order Cybernetics]], [[Autopoiesis]], and [[Chaos Theory]].
1. **Examples**:
   - Add a **biological example** (e.g., circadian rhythms as limit cycles).
   - Expand with **AI examples** (e.g., reservoir computing as a dynamic system).
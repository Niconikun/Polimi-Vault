## 1. Core Tenets
### 1.1. Objective Control Systems
- **Definition**: Focuses on **objective observation and control** of systems from an external viewpoint. The observer is **separate** from the observed system.
- **Cybernetic Link**: Aligns with **classical control theory** (Wiener, 1948) and **feedback mechanisms**. Systems are analyzed as **input-output** relationships.
  - *Example*: A thermostat regulating temperature is a **first-order cybernetic system**—it maintains a set point through negative feedback without self-reference.

### 1.2. Homeostasis and Feedback
- **Definition**: Systems maintain **homeostasis** through **feedback loops**—deviations from a goal state trigger corrective actions.
- **Cybernetic Link**: Resonates with **Ashby’s Law of Requisite Variety** (1956). The system’s stability depends on its ability to **counteract perturbations**.
  - *Formalism*: For a system $S$ with goal $G$ and current state $s_t$, the control action $a_t$ is:
    $$
    a_t = f(G - s_t),
    $$
    where $f$ is the feedback function (e.g., [[PID Controller]]).

### 1.3. Information Processing
- **Definition**: Cognition and control are **information-processing** tasks. The system **represents** the environment internally and acts based on these representations.
- **Cybernetic Link**: Connects to **classical cognitive science** (Fodor, 1975). The system operates on **symbolic** or **subsymbolic** representations of the world.
  - *Example*: A robot’s internal map of its environment is updated via sensor inputs and used for navigation.

### 1.4. Objective Reality
- **Definition**: Assumes an **objective reality** that can be observed and modeled independently of the observer. The goal is to **mirror** this reality in the system’s representations.
- **Cybernetic Link**: Contrasts with **[[Second-Order Cybernetics]]** (von Foerster, 1974). The observer is **not part** of the system being studied.
  - *Implication*: A self-driving car’s "understanding" of the road is treated as an **objective model**, not a co-constructed reality.

---

## 2. Formal Axioms
### Axiom 1: Observer Independence
A system $S$ is *first-order cybernetic* iff:
1. The observer $O$ is **external** to $S$:
   $$
   S \cap O = \emptyset.
   $$
2. Descriptions of $S$ aim to be **objective** and **observer-independent**.

### Axiom 2: Feedback Control
The system’s behavior is governed by **negative feedback** to maintain a goal state $G$:
$$
\text{Action}(S, t) = K \cdot (G - \text{State}(S, t)),
$$
where $K$ is the control gain.

### Axiom 3: [[Representationalism]]
The system $S$ operates on **internal representations** $R$ of the environment $E$:
$$
\text{Action}(S, t) = f(R(E), G),
$$
where $f$ is the decision function and $R(E)$ is the system’s model of $E$.

---

## 3. Cybernetic Frameworks Aligned with First-Order Cybernetics
| **Framework**                | **Connection to First-Order Cybernetics**                                    |
| ---------------------------- | ---------------------------------------------------------------------------- |
| **Classical Control Theory** | Systems are controlled via **feedback loops** (Wiener, 1948).                |
| **Symbolic AI**              | Cognition is **rule-based** and **representational** (Newell & Simon, 1976). |
| **[[Information Theory]]**   | Focuses on **objective information transmission** (Shannon, 1948).           |
| **[[Homeostasis]]**          | Systems maintain stability through **error correction** (Ashby, 1956).       |

---

## 4. Contrast with Other Theories
| **Theory**               | **Relation to First-Order Cybernetics**                                                                 |
|--------------------------|----------------------------------------------------------------------------------------------------------|
| **[[Second-Order Cybernetics]]** | Conflicts: First-order assumes **objective control**; second-order includes the **observer in the system**. |
| **[[Radical Constructivism]]** | Rejected: First-order assumes an **objective reality**; RC denies this.                                |
| **Embodied Cognition**   | Partial overlap: Both study **adaptive systems**, but first-order ignores the **body’s role**.           |
| **[[Enactivism]]**           | Conflicts: Enactivism rejects **internal representations**; first-order relies on them.                   |

---

## 5. Example: First-Order Cybernetics in Engineering
- **Scenario**: A cruise control system in a car.
  - **First-Order Interpretation**:
    - The system’s **goal** is to maintain a set speed $G$ (e.g., 60 mph).
    - It **objectively measures** the current speed $s_t$ and adjusts throttle via feedback:
      $$
      \text{Throttle}(t) = K_p (G - s_t) + K_i \int (G - s_t) \, dt.
      $$
    - The driver (observer) is **external** to the control loop.
  - **Cybernetic Loop**:
    $$
    \text{Speed Sensor} \xrightarrow{\text{feedback}} \text{Controller} \xrightarrow{\text{throttle}} \text{Engine} \xrightarrow{\text{acceleration}} \text{Car}.
    $$

---

## 6. Criticisms and Rebuttals
| **Criticism**                          | **First-Order Cybernetics Response**                                                                     |
|----------------------------------------|----------------------------------------------------------------------------------------------------------|
| *"It ignores the observer’s role."*    | **Objective control** is sufficient for many engineering tasks (e.g., thermostats, autopilots).         |
| *"It assumes an objective reality."*   | **Pragmatic success** (e.g., space missions) validates the approach, even if reality is constructed.      |
| *"It’s reductionist."*                 | **Modularity** enables scalable systems (e.g., hierarchical control in factories).                     |

---

## 7. Formal Summary
First-order cybernetics is an **objective, control-theoretic, and representational** framework where:
1. **Control** = **feedback loops** to maintain goal states.
2. **Knowledge** = **internal representations** of an objective environment.
3. **Observer** = **external** to the system.

**Key Equation**:
For a system $S$ with goal $G$ and state $s_t$:
$$
\text{Action}(S, t) = K \cdot (G - s_t).
$$

---
### Tags
#cybernetics #first-order #control-theory #homeostasis #feedback #systems-theory

---
### Suggested Additions:
1. **Diagrams** (Excalidraw):
   - A **feedback control loop** (e.g., thermostat or cruise control).
   - A **contrast table** of first-order vs. [[Second-Order Cybernetics]].
2. **Links**:
   - Connect to [[Second-Order Cybernetics]], [[Classical Cognitive Science]], and [[Control Theory]].
1. **Examples**:
   - Add an **industrial example** (e.g., factory automation) or **biological example** (e.g., glucose regulation).
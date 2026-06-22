## 1. Core Tenets
### 1.1. Epistemological Solipsism
- **Definition**: Knowledge is a **viable construction** by the cognizing system (e.g., organism, AI), not a mirror of objective reality.
- **Cybernetic Link**: Aligns with **[[Second-Order Cybernetics]]** (von Foerster, 1974), where the observer is part of the system. The "world" is a closed-loop of sensorimotor interactions.
  - *Example*: A robot’s reality is defined by its sensorimotor contingencies (O’Regan & Noë, 2001).

### 1.2. Viability Over Truth
- **Definition**: Cognitive constructions are judged by **viability** (fitness for purpose), not truth.
- **Cybernetic Link**: Maps to **[[homeostasis]]** (Ashby, 1956) and **adaptation**. A system’s "knowledge" is viable if it enables survival/goal achievement.
  - *Formalism*: For a system $S$ with state $s_t$ and environment $E$, a construction $C$ is *viable* if:
    $$
    \exists \text{ goal } G: \forall t, \, \text{action}(s_t, C) \rightarrow G \text{ in } E.
    $$

### 1.3. Operational Closure
- **Definition**: Systems are **organizationally closed** (Maturana & Varela, 1980). They generate their own states via recursive interactions.
- **Cybernetic Link**: Resonates with **[[Autopoiesis]]** and **circular causality**.
  - *Example*: A neural network’s weights are updated via internal rules (e.g., backpropagation), not external data.

### 1.4. Observer-Dependence
- **Definition**: All descriptions are **observer-relative**; no "God’s-eye view" exists.
- **Cybernetic Link**: Connects to **constructivist epistemology** (von Glasersfeld, 1984), where models are tools for viability, not truths.

---

## 2. Formal Axioms
### Axiom 1: Cognitive Autonomy
A system $S$ is *radically constructivist* iff:
1. State transitions are determined by **internal rules** $f: S \times P \rightarrow S$ (where $P$ are environmental perturbations).
2. No access to an "external reality" $R$; all knowledge is a function of **structural coupling** with $P$.

### Axiom 2: Viability as Epistemic Criterion
A construction $C$ is *knowledge* for $S$ iff:
$$
\exists T \text{ (time horizon)}: \, \text{viability}(C, S, E) \geq \theta \text{ (threshold)}.
$$

### Axiom 3: Non-Realism
For any two systems $S_1$ and $S_2$ with distinct sensorimotor apparatus:
$$
\not\exists \text{ isomorphism } \phi: \, \text{Reality}_{S_1} \cong \text{Reality}_{S_2}.
$$

---

## 3. Cybernetic Frameworks Aligned with RC
| **Framework**                | **Connection to Radical Constructivism**                                                                  |
| ---------------------------- | --------------------------------------------------------------------------------------------------------- |
| **[[Second-Order Cybernetics]]** | Observer is part of the system; no objective descriptions (von Foerster, 1974).                           |
| **[[Autopoiesis]]**          | Systems define their own identity through operational closure (Maturana & Varela, 1980).                  |
| **[[Enactivism]]**           | [[Cognition]] is **embodied** and **situated**; the "world" is co-constructed through action (Varela et al.). |
| **[[Control Theory]]**       | Viability = maintaining goals via feedback loops (Ashby’s *Design for a Brain*).                          |

---

## 4. Contrast with Other Epistemologies
| **Epistemology**                | **Relation to RC**                                                                        |
| ------------------------------- | ----------------------------------------------------------------------------------------- |
| **[[Realism]]**                 | Rejected: RC denies access to an observer-independent reality.                            |
| **[[Pragmatism]]**              | Partial overlap: Both emphasize utility, but RC rejects truth-as-correspondence entirely. |
| **[[Connectionism]]**           | Compatible if networks are **closed** systems constructing representations (not copying). |
| **[[First-Order Cybernetics]]** | Conflicts with [[first-order cybernetics]] (objective control); aligns with second-order.     |

---

## 5. Example: RC in AI Cybernetics
- **Scenario**: A reinforcement learning (RL) agent in a grid world.
  - **RC Interpretation**:
    - The agent’s "map" is a **viable policy** $\pi$, not a mirror of the grid.
    - The reward function is an **internal constraint**, not an external truth.
  - **Cybernetic Loop**:
    $ \text{State} \xrightarrow{\pi} \text{Action} \xrightarrow{E} \text{Perturbation} \xrightarrow{f} \text{New State}. $

---

## 6. Criticisms and Rebuttals
| **Criticism**                          | **RC + Cybernetics Response**                                                                           |
|----------------------------------------|--------------------------------------------------------------------------------------------------------|
| *"RC leads to relativism."*            | Viability is **system-specific but not arbitrary**—constrained by goals/environment.                   |
| *"How can science work if reality is constructed?"* | Science is a **viable tool** for prediction/control, not truth discovery (von Glasersfeld, 1995).       |
| *"RC ignores the external world."*     | The environment **perturbs** the system but does not **determine** its constructions (Maturana, 1970). |

---

## 7. Formal Summary
Radical constructivism in cybernetics is a **non-realist, viability-based epistemology** where:
1. **Knowledge** = internally generated constructions enabling **adaptive control**.
2. **Reality** = system-specific **operational domain** (not external ontology).
3. **Cybernetic Systems** are **autonomous**, **closed**, and **observer-dependent**.

**Key Equation**:
For a system $S$ with perturbations $P$ and internal dynamics $f$:
$$
\text{Knowledge}_S = \{ C \, | \, \text{viability}(C, S, P) \geq \theta \}.
$$

---
### Tags
#epistemology #cybernetics #autopoiesis #constructivism #second-order-cybernetics
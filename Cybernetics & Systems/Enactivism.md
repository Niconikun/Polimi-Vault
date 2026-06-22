## 1. Core Tenets
### 1.1. Embodied Cognition
- **Definition**: Cognition is **bodily mediated**; the body’s sensorimotor dynamics are constitutive of cognitive processes, not merely peripheral.
- **Cybernetic Link**: Aligns with **situated robotics** and **[[Dynamic Systems Theory]]**. Cognition emerges from the **coupling** of an agent’s body and environment.
  - *Example*: A robot’s "understanding" of a staircase is not an internal representation but the **dynamic coordination** of its legs, sensors, and motor systems (Pfeifer & Bongard, 2006).

### 1.2. Situatedness
- **Definition**: Cognition is **context-dependent**; it cannot be abstracted from the agent’s real-time interaction with its environment.
- **Cybernetic Link**: Resonates with **Ashby’s** (1956) idea of **adaptation** and **perturbation**. The environment is not a passive backdrop but a **co-determinant** of cognitive processes.
  - *Formalism*: For an agent $A$ in environment $E$, cognition $C$ is a function of the **agent-environment system**:
    $$
    C = f(A \leftrightarrow E).
    $$

### 1.3. Sense-Making ([[Autopoiesis]])
- **Definition**: Cognition is **sense-making**—the agent actively generates meaning through its interactions, not passively processing information.
- **Cybernetic Link**: Directly tied to **[[Autopoiesis]]** (Maturana & Varela, 1980). A system’s cognition is its **self-maintenance** through precarious balance with the environment.
  - *Example*: A bacterium’s "knowledge" of a sugar gradient is its **chemotactic behavior**, not a mental map.

### 1.4. Emergent Normativity
- **Definition**: Values (e.g., "good," "bad") are not pre-given but **emerge** from the agent’s **precariousness** (Di Paolo, 2005). What matters is what sustains the agent’s identity.
- **Cybernetic Link**: Connects to **homeostasis** and **viability** (Ashby, 1956). Norms are **system-relative**, not absolute.
  - *Implication*: A robot’s "goal" to avoid obstacles is not programmed as a rule but **emerges** from its need to maintain structural integrity.

---

## 2. Formal Axioms
### Axiom 1: Embodied Coupling
An agent $A$ is *enactive* iff:
1. Its cognitive processes are **constituted by** its sensorimotor dynamics $D$ in environment $E$:
   $$
   C_A = \int D \, dt \text{ (integral over time)}.
   $$
2. There is no **internal representation** of $E$; cognition is **relational** (agent-environment co-determination).

### Axiom 2: Sense-Making as Precariousness
An interaction $I$ between $A$ and $E$ is *cognitive* iff:
$$
I \text{ contributes to the maintenance of } A\text{'s autopoietic organization.}
$$
- *Formalism*: Let $\theta$ be the threshold for structural integrity. Then:
  $$
  \text{Sense-making}(I) \iff \text{viability}(A, E, I) \geq \theta.
  $$

### Axiom 3: Normativity as Emergent
A norm $N$ for $A$ is *enactive* iff:
1. $N$ arises from $A$’s **precariousness** (need to self-maintain).
2. $N$ is **not pre-specified** but emerges from $A$’s history of interactions:
   $$
   N = g(\text{history}(A \leftrightarrow E)).
   $$

---

## 3. Cybernetic Frameworks Aligned with Enactivism
| **Framework**               | **Connection to Enactivism**                                                                             |
|-----------------------------|----------------------------------------------------------------------------------------------------------|
| **[[Autopoiesis]]**             | Cognition is **self-maintenance** through operational closure (Maturana & Varela, 1980).                 |
| **[[Dynamic Systems Theory]]**  | Cognition is a **trajectory** in the agent-environment [[State-Space Representation]] (Thelen & Smith, 1994).               |
| **Situated Robotics**       | Robots "think" by **acting in the world**, not by building internal models (Brooks, 1991).               |
| **[[Second-Order Cybernetics]]**| The observer’s role is **participatory**; cognition is co-created (von Foerster, 1974).                 |

---

## 4. Contrast with Other Theories of [[Cognition]]

| **Theory**                      | **Relation to Enactivism**                                                                                        |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Classical Cognitive Science** | Rejected: Enactivism denies **internal representations** and **symbol manipulation** (Fodor, 1975).               |
| **Embodied Cognition**          | Partial overlap: Both emphasize the body, but enactivism adds **sense-making** and **[[Autopoiesis]]**.           |
| **[[Radical Constructivism]]**  | Compatible: Both reject objectivism, but enactivism focuses on **bodily interaction**, not just viability.        |
| **[[Connectionism]]**           | Conflicts: Connectionism relies on **internal patterns** (e.g., neural nets), while enactivism is **relational**. |

---

## 5. Example: Enactivism in Robotics
- **Scenario**: A hexapod robot navigating rough terrain.
  - **Enactive Interpretation**:
    - The robot’s "knowledge" of the terrain is not a map but its **dynamic gait adjustments** (e.g., compliance in leg joints).
    - Its "goal" to avoid falling is not programmed but **emerges** from the need to maintain structural integrity (precariousness).
  - **Cybernetic Loop**:
    $$
    \text{Terrain} \xrightarrow{\text{perturbation}} \text{Sensors} \xrightarrow{\text{dynamic coupling}} \text{Motors} \xrightarrow{\text{action}} \text{Terrain}.
    $$

---

## 6. Criticisms and Rebuttals
| **Criticism**                          | **Enactivist + Cybernetic Response**                                                                    |
|----------------------------------------|--------------------------------------------------------------------------------------------------------|
| *"Enactivism ignores representation."* | **Representation is replaced by **sensorimotor coordination** (Noë, 2004). The world *is* the model.   |
| *"How can complex cognition (e.g., language) emerge without symbols?"* | Language is **enactive**: a dynamic coordination of bodies/environments (e.g., gesture-speech unity).   |
| *"Enactivism is anti-computational."*  | It rejects **digital computation** but embraces **morphological computation** (Pfeifer et al., 2007).   |

---

## 7. Formal Summary
Enactivism is a **relational, embodied, and sense-making** theory of cognition where:
1. **Cognition** = **sensorimotor coordination** with the environment (not internal processing).
2. **Meaning** = **precariousness**—what sustains the agent’s autopoietic organization.
3. **Norms** = **emergent** from the agent’s history of interactions.

**Key Equation**:
For an agent $A$ in environment $E$, cognition $C$ is:
$$
C = \lim_{t \to \infty} \int (A \leftrightarrow E) \, dt.
$$

---
### Tags
#cognition #embodied #enactivism #autopoiesis #cybernetics #dynamic-systems

---
### Suggested Additions:
1. **Diagrams** (Excalidraw):
   - A **hexapod robot** showing dynamic coupling with terrain.
   - A **Venn diagram** of enactivism, embodied cognition, and radical constructivism.
2. **Links**:
   - Connect to [[Autopoiesis]], [[Radical Constructivism]], and [[Dynamic Systems Theory]].
3. **Examples**:
   - Expand with a **biological example** (e.g., bacterial chemotaxis) or **AI example** (e.g., a soft robot).
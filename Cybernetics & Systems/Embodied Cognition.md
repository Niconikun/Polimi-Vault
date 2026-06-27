## 1. Core Tenets
### 1.1. Body as Constitutive of Cognition
- **Definition**: Cognition is **fundamentally shaped by the body’s form, sensorimotor capacities, and interactions** with the environment. The body is not just a "vehicle" for the brain but a **necessary participant** in cognitive processes.
- **Cybernetic Link**: Aligns with **morphological computation** (Pfeifer & Bongard, 2006), where the body’s physical structure **offloads cognitive work** (e.g., a robot’s legs passively adapting to terrain).
  - *Example*: A chess player’s "intuition" about a move arises from **embodied simulations** of piece movements (Gallese & Lakoff, 2005).

### 1.2. Situatedness
- **Definition**: Cognition is **inextricably linked to its environmental context**. Abstract reasoning is **grounded** in sensorimotor experiences.
- **Cybernetic Link**: Resonates with **situated robotics** (Brooks, 1991) and **[[Dynamic Systems Theory]]**. The environment is a **scaffold** for cognition, not a passive backdrop.
  - *Formalism*: For an agent $A$ with body $B$ in environment $E$, cognition $C$ is:
    $$
    C = f(B \times E),
    $$
    where $f$ is a dynamic, context-sensitive function.

### 1.3. Offloading and Scaffolding
- **Definition**: Cognitive processes **extend beyond the brain** into the body and environment (e.g., tools, gestures, or external symbols). The agent **offloads** computation to its surroundings.
- **Cybernetic Link**: Connects to **extended mind theory** (Clark & Chalmers, 1998) and **stigmergy** (indirect coordination via environment, as in ant trails).
  - *Example*: Using a notebook to remember ideas is part of the **cognitive system**, not just a memory aid.

### 1.4. Sensorimotor Contingencies
- **Definition**: Cognition relies on **laws of sensorimotor interaction**—how actions change sensory inputs. Perception is **active exploration**, not passive reception.
- **Cybernetic Link**: Aligns with **enactive perception** (O’Regan & Noë, 2001) and **[[control theory]]**. The agent **probes** the environment to generate meaning.
  - *Implication*: A bat’s "knowledge" of its surroundings is its **echolocation behavior**, not an internal map.

---

## 2. Formal Axioms
### Axiom 1: Body-Environment Mutuality
An agent $A$ exhibits *embodied cognition* iff:
1. Its cognitive processes **depend on** its bodily form $B$ and environmental interactions $E$:
   $$
   C_A = g(B, E),
   $$
   where $g$ is a non-linear, dynamic function.
2. **No cognition without a body**: $C_A$ is undefined if $B$ is removed.

### Axiom 2: Offloading Principle
A cognitive task $T$ is *offloaded* iff:
$$
\exists \text{ external resource } R: \, \text{performance}(T, A \cup R) > \text{performance}(T, A).
$$
- *Example*: A mathematician’s use of paper to solve equations **extends** their cognitive system.

### Axiom 3: Sensorimotor Grounding
A concept $c$ is *embodied* for $A$ iff:
$$
c \text{ is linked to sensorimotor patterns } S \text{ such that } \text{activation}(c) \rightarrow \text{simulation}(S).
$$
- *Formalism*: For a concept like "grasp," the brain **reactivates** motor programs for hand movements (Pulvermüller, 2005).

---

## 3. Cybernetic Frameworks Aligned with Embodied Cognition
| **Framework**               | **Connection to Embodied Cognition**                                                                     |
|-----------------------------|----------------------------------------------------------------------------------------------------------|
| **Morphological Computation** | The body’s physics **replaces** computation (e.g., a robot’s passive dynamics in walking).             |
| **Situated Robotics**       | Robots "think" by **acting in the world** (Brooks, 1991).                                                |
| **[[Extended Mind Theory]]**    | Cognition **extends into the environment** (Clark & Chalmers, 1998).                                    |
| **[[Dynamic Systems Theory]]**  | Cognition is a **trajectory** in the agent-body-environment [[State-Space Representation]] (Thelen & Smith, 1994).          |
| **Stigmergy**               | Indirect coordination via **environmental modifications** (e.g., ant pheromone trails).                |

---

## 4. Contrast with Other Theories of [[Cognition]]
| **Theory**               | **Relation to Embodied Cognition**                                                                       |
|--------------------------|----------------------------------------------------------------------------------------------------------|
| **Classical Cognitive Science** | Conflicts: Rejects **disembodied symbol manipulation** (Fodor, 1975).                                    |
| **Connectionism**        | Partial overlap: Both emphasize **dynamic processes**, but embodied cognition requires a **physical body**. |
| **[[Enactivism]]**           | Compatible: Both stress **sensorimotor coupling**, but enactivism adds **[[Autopoiesis]]** and **sense-making**. |
| **[[Radical Constructivism]]** | Compatible: Both reject objectivism, but embodied cognition focuses on the **body’s role** in constructing reality. |

---

## 5. Example: Embodied Cognition in Robotics
- **Scenario**: A humanoid robot learning to stack blocks.
  - **Embodied Interpretation**:
    - The robot’s "understanding" of balance emerges from **physical interactions** (e.g., feeling the weight shift in its grippers).
    - Its "memory" of block shapes is **sensorimotor**, not a symbolic database.
  - **Cybernetic Loop**:
    $$
    \text{Blocks} \xrightarrow{\text{grip}} \text{Sensors} \xrightarrow{\text{motor response}} \text{Arm} \xrightarrow{\text{action}} \text{Blocks}.
    $$

---

## 6. Criticisms and Rebuttals
| **Criticism**                          | **Embodied Cognition Response**                                                                          |
|----------------------------------------|----------------------------------------------------------------------------------------------------------|
| *"Embodiment is irrelevant for abstract thought."* | **Abstract concepts** (e.g., time, math) are **metaphors** grounded in sensorimotor experience (Lakoff & Núñez, 2000). |
| *"How does embodiment scale to complex cognition?"* | **Hybrid systems** combine embodied and symbolic processes (e.g., language + gesture).                  |
| *"Embodiment is hard to formalize."*   | **Computational models** (e.g., neural fields, dynamic systems) capture body-environment interactions.     |

---

## 7. Formal Summary
Embodied cognition is a **body-centric, situated, and extended** theory of cognition where:
1. **Cognition** = **dynamic interaction** between body, brain, and environment.
2. **Meaning** = **sensorimotor contingencies** and **offloaded resources**.
3. **Knowledge** = **grounded** in physical and environmental constraints.

**Key Equation**:
For an agent $A$ with body $B$ in environment $E$, cognition $C$ is:
$$
C = \int (B \times E) \, dt.
$$

---
### Tags
#cognition #embodied #sensorimotor #cybernetics #dynamic-systems #extended-mind

---
### Suggested Additions:
1. **Diagrams** (Excalidraw):
   - A **robot-body-environment loop** showing offloading (e.g., using tools).
   - A **contrast table** of embodied vs. classical cognition.
2. **Links**:
   - Connect to [[Enactivism]], [[Dynamic Systems Theory]], and [[Extended Mind Theory]].
3. **Examples**:
   - Add a **biological example** (e.g., octopus arm coordination) or **[[Artificial Intelligence]] example** (e.g., Boston Dynamics robots).
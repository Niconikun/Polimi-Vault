## 1. Core Tenets
### 1.1. Operational Closure
- **Definition**: A system is **autopoietic** if it **continuously produces its own components** and organizational boundaries through recursive interactions. The system is **operationally closed**—its processes refer only to itself.
- **Cybernetic Link**: Aligns with **[[Second-Order Cybernetics]]** (von Foerster, 1974) and **[[circular causality]]**. The system’s identity is maintained through **self-referential** processes.
  - *Example*: A cell’s membrane is both a **product** of its internal processes and a **boundary** that enables those processes (Maturana & Varela, 1980).

### 1.2. Self-Production (Autopoiesis)
- **Definition**: The system’s **primary function** is to produce and maintain its own organization. It is **autonomous**—its operations are determined by its internal structure, not external inputs.
- **Cybernetic Link**: Resonates with **[[homeostasis]]** (Ashby, 1956) but extends it: autopoiesis is not just about maintaining a state but **actively generating the components** that define the system.
  - *Formalism*: For a system $S$ with components $C$ and processes $P$, autopoiesis requires:
    $$
    P(C) \rightarrow C,
    $$
    where $P(C)$ are the processes that regenerate $C$.

### 1.3. Structural Coupling
- **Definition**: While operationally closed, autopoietic systems **structurally couple** with their environment. Perturbations from the environment trigger internal changes, but the system’s response is determined by its **own organization**.
- **Cybernetic Link**: Connects to **adaptive control** and **perturbation theory**. The environment **does not instruct** the system but **triggers** its self-organized responses.
  - *Example*: An organism’s immune system adapts to pathogens, but the adaptation is governed by its **internal rules**, not the pathogen’s "instructions."

### 1.4. Cognition as Autopoiesis
- **Definition**: Cognition is the **process of autopoiesis itself**—the system’s ability to maintain its identity through structural coupling. There is no separation between "cognition" and "life."
- **Cybernetic Link**: Aligns with **[[Enactivism]]** (Varela et al., 1991) and **[[Radical Constructivism]]**. The system’s "knowledge" is its **viability** in maintaining autopoiesis.
  - *Implication*: A robot’s "understanding" of its environment is its ability to **maintain its operational closure** while interacting with it.

---

## 2. Formal Axioms
### Axiom 1: Operational Closure
A system $S$ is *autopoietic* iff:
1. It produces its own components $C$ through processes $P$:
   $$
   P: C \rightarrow C.
   $$
2. The processes $P$ are **recursive** and **self-referential**—they depend only on $S$’s internal state.

### Axiom 2: Structural Determinism
The system’s response to environmental perturbations $E$ is determined by its **current structure** $S_t$:
$$
\text{Response}(S, E) = f(S_t, E),
$$
where $f$ is a function of $S$’s internal organization, not $E$’s "intent."

### Axiom 3: Cognition as Viability
A system $S$ *cognizes* iff its structural coupling with $E$ maintains its autopoiesis:
$$
\text{Cognition}(S, E) \iff \text{viability}(S, E) \geq \theta,
$$
where $\theta$ is the threshold for maintaining operational closure.

---

## 3. Cybernetic Frameworks Aligned with Autopoiesis
| **Framework**                  | **Connection to Autopoiesis**                                                                                 |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------- |
| **[[Second-Order Cybernetics]]**   | The observer is part of the system; autopoiesis is **self-referential** (von Foerster, 1974).                 |
| **[[Enactivism]]**                 | Cognition is **sense-making** through autopoietic coupling (Varela et al., 1991).                             |
| **[[Dynamic Systems Theory]]** | Autopoiesis is a **stable trajectory** in the system’s [[State-Space Representation]] (Thelen & Smith, 1994). |
| **[[Radical Constructivism]]**     | Both reject objective reality; autopoiesis adds **self-production** as the criterion for cognition.           |

---

## 4. Contrast with Other Theories of [[Cognition]]
| **Theory**               | **Relation to Autopoiesis**                                                                               |
|--------------------------|----------------------------------------------------------------------------------------------------------|
| **Classical Cognitive Science** | Conflicts: Autopoiesis rejects **disembodied computation** and **[[representationalism]]**.                   |
| **Connectionism**        | Partial overlap: Both involve **dynamic systems**, but autopoiesis requires **self-production of components**. |
| **[[Embodied Cognition]]**   | Compatible: Both emphasize the **body’s role**, but autopoiesis focuses on **self-maintenance**.          |
| **[[Enactivism]]**           | Compatible: [[Enactivism]] extends autopoiesis to **sense-making** and **precariousness**.                     |

---

## 5. Example: Autopoiesis in Biology and AI
### 5.1. Biological Example: The Cell
- **Scenario**: A eukaryotic cell maintaining its membrane and organelles.
  - **Autopoietic Interpretation**:
    - The cell’s **identity** is its ability to produce lipids, proteins, and organelles through internal processes.
    - Its "cognition" of nutrients is the **structural coupling** that maintains its autopoiesis (e.g., glucose uptake triggers ATP production).
  - **Cybernetic Loop**:
    $$
    \text{Nutrients} \xrightarrow{\text{perturbation}} \text{Receptors} \xrightarrow{\text{metabolic pathways}} \text{Organelles} \xrightarrow{\text{self-repair}} \text{Cell}.
    $$

### 5.2. AI Example: Self-Maintaining Robot
- **Scenario**: A robot that repairs its own components using environmental resources.
  - **Autopoietic Interpretation**:
    - The robot’s "goal" is not programmed but **emerges** from its need to maintain operational closure (e.g., replacing damaged parts).
    - Its "knowledge" of tools is its ability to **use them to sustain itself**.
  - **Cybernetic Loop**:
    $$
    \text{Damage} \xrightarrow{\text{sensors}} \text{Self-Diagnosis} \xrightarrow{\text{repair actions}} \text{Tools} \xrightarrow{\text{restoration}} \text{Robot}.
    $$

---

## 6. Criticisms and Rebuttals
| **Criticism**                          | **Autopoietic Response**                                                                                 |
|----------------------------------------|----------------------------------------------------------------------------------------------------------|
| *"Autopoiesis is too biological."*     | **Artificial autopoiesis** exists (e.g., self-repairing robots; Froese & Ziemke, 2009).                   |
| *"It’s just [[homeostasis]]."*             | Autopoiesis is **generative** (produces components), not just regulatory (Ashby, 1956 vs. Maturana, 1970). |
| *"How does it explain complex cognition?"* | **Higher-order autopoiesis** (e.g., social systems) builds on basic autopoiesis (Luhmann, 1986).           |

---

## 7. Formal Summary
Autopoiesis is a **self-producing, operationally closed, and structurally coupled** theory of cognition where:
1. **Identity** = **self-production** of components through recursive processes.
2. **Cognition** = **maintenance of autopoiesis** via structural coupling.
3. **Viability** = **operational closure** in the face of perturbations.

**Key Equation**:
For a system $S$ with components $C$ and processes $P$:
$$
\text{Autopoiesis}(S) \iff P(C) \rightarrow C \land \text{closure}(P).
$$

---
### Tags
#autopoiesis #cybernetics #self-organization #enactivism #dynamic-systems #biology #AI

---
### Suggested Additions:
1. **Diagrams** (Excalidraw):
   - A **cell’s autopoietic loop** (membrane, organelles, metabolism).
   - A **robot’s self-repair cycle** (damage → diagnosis → repair).
2. **Links**:
   - Connect to [[Enactivism]], [[Radical Constructivism]], [[Dynamic Systems Theory]], and [[Second-Order Cybernetics]].
1. **Examples**:
   - Add a **social systems example** (e.g., Luhmann’s autopoietic communication systems).
   - Expand with **AI implementations** (e.g., artificial chemistry models of autopoiesis).
## 1. Core Tenets
### 1.1. Distributed Representation
- **Definition**: Knowledge is encoded in **patterns of activation** across networks of simple, interconnected units (neurons/nodes), not in discrete symbols.
- **Cybernetic Link**: Aligns with **parallel distributed processing (PDP)** and **[[Dynamic Systems Theory]]**. The network’s [[State-Space Representation]] is a **trajectory** of activations.
  - *Example*: A neural network’s "memory" of a face is a **distributed pattern** across hidden layers, not a localized symbol (Rumelhart & McClelland, 1986).

### 1.2. Subsymbolic Processing
- **Definition**: [[Cognition]] operates at a **subsymbolic level**—meaning emerges from the interaction of simple units, not pre-defined rules or symbols.
- **Cybernetic Link**: Resonates with **emergent behavior** in complex systems. High-level cognition (e.g., language) arises from low-level connections.
  - *Formalism*: For a network $N$ with weights $W$ and inputs $X$, the output $Y$ is:
    $$
    Y = \sigma(WX + b),
    $$
    where $\sigma$ is a non-linear activation function (e.g., ReLU).

### 1.3. Learning as Weight Adjustment
- **Definition**: Learning is the **adjustment of connection weights** via algorithms (e.g., [[backpropagation]]) to minimize error, not explicit rule acquisition.
- **Cybernetic Link**: Maps to **adaptive control systems** (Ashby, 1956). The network **self-organizes** through feedback.
  - *Example*: A deep learning model "learns" to classify images by iteratively tuning weights to reduce prediction errors.

### 1.4. Context-Sensitivity
- **Definition**: Processing is **context-dependent**; the same input can yield different outputs based on the network’s current state or prior activations.
- **Cybernetic Link**: Connects to **[[Dynamic Systems Theory]]**. The network’s behavior is a **trajectory** in a high-dimensional state space.
  - *Implication*: A connectionist system’s response to "dog" depends on recent activations (e.g., "animal" vs. "pet" contexts).

---

## 2. Formal Axioms
### Axiom 1: Distributed Encoding
A system $S$ is *connectionist* iff:
1. Knowledge is stored as **weight matrices** $W$ and **activation patterns** $A$:
   $$
   \text{Knowledge}_S = (W, A).
   $$
2. There are **no localized symbols**; representations are **emergent** from $W$ and $A$.

### Axiom 2: Learning as Optimization
Learning in $S$ is a process of **gradient descent** on a loss function $L$:
$$
W_{t+1} = W_t - \eta \nabla_L(W_t),
$$
where $\eta$ is the learning rate.

### Axiom 3: Context-Dependent Dynamics
The response $R$ of $S$ to input $X$ is a function of its **current state** $S_t$:
$$
R = f(X, S_t).
$$

---

## 3. Cybernetic Frameworks Aligned with Connectionism
| **Framework**               | **Connection to Connectionism**                                                                         |
|-----------------------------|----------------------------------------------------------------------------------------------------------|
| **Parallel Distributed Processing (PDP)** | Cognition is **parallel** and **distributed** across units (Rumelhart & McClelland, 1986).               |
| **[[Dynamic Systems Theory]]**  | Network activations are **trajectories** in a state space (Thelen & Smith, 1994).                        |
| **Adaptive Control**        | Learning is **error minimization** via feedback (Ashby, 1956).                                           |
| **Neural Darwinism**        | Networks "select" useful connections through competition (Edelman, 1987).                                |

---

## 4. Contrast with Other Theories of [[Cognition]]
| **Theory**               | **Relation to Connectionism**                                                                           |
|--------------------------|----------------------------------------------------------------------------------------------------------|
| **Classical Cognitive Science** | Conflicts: Rejects **symbolic rules** (Fodor & Pylyshyn, 1988) in favor of subsymbolic patterns.       |
| **Embodied Cognition**   | Partial overlap: Both emphasize **dynamic processes**, but connectionism is **disembodied** (no body). |
| **[[Enactivism]]**           | Conflicts: Enactivism rejects **internal representations**; connectionism relies on them (e.g., weights). |
| **[[Radical Constructivism]]** | Compatible if networks are **closed systems** constructing representations (not copying external reality). |

---

## 5. Example: Connectionism in [[Artificial Intelligence]]
- **Scenario**: A neural network learning to translate languages.
  - **Connectionist Interpretation**:
    - "Knowledge" of grammar is **distributed** across weights, not a rulebook.
    - Learning is **statistical adjustment** of weights to minimize [[translation]] errors.
  - **Cybernetic Loop**:
    $$
    \text{Input (e.g., "Hello")} \xrightarrow{W} \text{Hidden Activations} \xrightarrow{W} \text{Output (e.g., "Hola")} \xrightarrow{L} \text{[[Error Signal]]} \xrightarrow{\nabla} W.
    $$

---

## 6. Criticisms and Rebuttals
| **Criticism**                          | **Connectionist Response**                                                                              |
|----------------------------------------|----------------------------------------------------------------------------------------------------------|
| *"Connectionism lacks symbolic reasoning."* | **Hybrid models** (e.g., neural-symbolic [[Artificial Intelligence]]) combine subsymbolic and symbolic processing (Garcez et al., 2008). |
| *"Networks are black boxes."*          | **Interpretability tools** (e.g., attention maps, LIME) reveal patterns (Ribeiro et al., 2016).           |
| *"Connectionism ignores the body."*    | **Embodied connectionism** integrates sensors/motors (e.g., robotic [[neural networks]]).                     |

---

## 7. Formal Summary
Connectionism is a **subsymbolic, distributed, and adaptive** theory of cognition where:
1. **Knowledge** = **weight matrices** and **activation patterns** (not symbols).
2. **Learning** = **optimization** of weights via feedback (e.g., [[backpropagation]]).
3. **Processing** = **context-sensitive** dynamics in a high-dimensional state space.

**Key Equation**:
For a network with weights $W$, inputs $X$, and activation $\sigma$:
$$
Y = \sigma(WX + b).
$$

---
### Tags
#cognition #connectionism #neural-networks #AI #dynamic-systems #subsymbolic

---
### Suggested Additions:
1. **Diagrams** (Excalidraw):
   - A **neural network** with labeled weights/activations.
   - A **contrast table** of connectionism vs. symbolic [[Artificial Intelligence]].
2. **Links**:
   - Connect to [[Dynamic Systems Theory]], [[Radical Constructivism]], and [[Embodied Cognition]].
3. **Examples**:
   - Add a **biological example** (e.g., hippocampal place cells) or **[[Artificial Intelligence]] example** (e.g., Transformers).
## Formal Definition

**Physical Architecture Mapping** (also known as Functional-to-Physical Allocation) is the systems engineering process of assigning specific functions identified during functional decomposition to physical components, software modules, or human operators. It represents the transition from the "conceptual" domain (what the system does) to the "realization" domain (what the system is), establishing a definitive spatial and structural configuration that satisfies the functional requirements.

## Historical Development

### Key Milestones

- **1950s-1960s:** Developed during the ballistic missile programs to manage the mapping of complex guidance functions to early electronic hardware.
    
- **1990s:** The "V-Model" of systems engineering formalizes the "mapping" step as the bridge between the left side (requirements/functions) and the right side (components/integration).
    
- **2010s:** The adoption of **Architecture Frameworks** (like TOGAF or DoDAF) standardizes how physical views are mapped to operational and functional views.
    

### Foundational Contributors

1. **Eberhardt Rechtin (1926–2006):** Known as the "Father of Systems Architecting," he established the heuristics for mapping functions to physical forms to minimize interface complexity.
    
2. **Nam Pyo Suh (1936–Present):** Developed **Axiomatic Design**, which provides a mathematical framework for mapping Functional Requirements (FRs) to Design Parameters (DPs).
    

## Mathematical Formulation

### General Form

The mapping is often represented as a matrix transformation between the Functional Domain (F) and the Physical Domain (P):

{FR}=[A]{DP}

### Component Breakdown

- **{FR}**: A vector of Functional Requirements.
    
- **{DP}**: A vector of Design Parameters (Physical Components).
    
- **$[A]$**: The **Design Matrix**. In an ideal "Uncoupled Design," [A] is a diagonal matrix, meaning each function is satisfied by exactly one physical component.
    

## Fundamental Principles

### Core Assumptions

1. **Traceability:** Every physical component must exist to satisfy at least one function, and every function must be accounted for by at least one component.
    
2. **Allocation:** Performance budgets (mass, power, latency) are "mapped" or allocated from the system level down to the physical components during this process.
    

### Governing Laws/Theorems

- **The Coupling Principle:** If one physical component is mapped to multiple independent functions, those functions become "coupled," meaning a change in one function will inadvertently affect the other.
    

## Theoretical Framework

### Relationship to Other Concepts

1. **Connection to Functional Decomposition:**
    
    - Functional decomposition provides the input (the "what"). Physical architecture mapping provides the output (the "how").
        
2. **Connection to Interface Control Document (ICD):**
    
    - Once functions are mapped to physical components, the boundaries between those components become the subjects of the ICD.
        

## Classification and Variants

### By Mapping Topology

1. **One-to-One:** Each function is mapped to exactly one component (Ideal for modularity).
    
2. **Many-to-One:** Multiple functions are integrated into a single component (Common in "System-on-Chip" or highly integrated aerospace structures to save mass).
    
3. **One-to-Many:** A single function is distributed across multiple components (Common in redundant or distributed computing systems).
    

## Derivation and Proof

### Step-by-Step Mapping Process

1. **Identify Functional Leaves:** Take the lowest-level functions from the functional decomposition.
    
2. **Candidate Synthesis:** Brainstorm physical parts or software structures that could perform those functions.
    
3. **Trade Studies:** Evaluate candidates based on constraints (cost, weight, power).
    
4. **Allocation:** Formally assign the function to the chosen physical entity.
    
5. **Verify Coverage:** Ensure there are no "orphan functions" (functions with no hardware) or "extra hardware" (hardware with no functional purpose).
    

## Physical Interpretation

### Mechanical Significance

In spacecraft design, this involves mapping the function "Provide Structural Support" to the **Primary Bus Structure** and "Regulate Temperature" to **Radiators** and **Heaters**.

## Applications

### Engineering Disciplines

1. **Aerospace Engineering:** Mapping the "Change Attitude" function to Reaction Wheels or Thrusters.
    
2. **Automotive Engineering:** Mapping the "Decelerate Vehicle" function to the Braking Subsystem (Pads, Calipers, Rotors).
    

## Implementation Considerations

### Software Tools

- **SysML Allocation Tables:** Used to show "allocate" relationships between functional blocks and physical blocks.
    
- **N-Squared (N2) Diagrams:** Used to visualize the physical interfaces created by the mapping.
    

## Advantages and Limitations

### Strengths

1. **Optimization:** Allows for the identification of redundant components that can be consolidated.
    
2. **Impact Analysis:** If a component fails, the map immediately shows which system functions are compromised.
    

### Weaknesses

1. **Complexity:** In large systems, the mapping matrix can become massive and difficult to manage without specialized software.
    
2. **Sub-optimization:** Focusing on mapping functions perfectly can sometimes lead to a physical layout that is difficult to manufacture or maintain.
    

## See Also

- [[Functional Decomposition]]
    
- [[Subsystem]]
    
- [[Interface Control Document]]
    
- [[System Architecture]]
    
- [[Trade Study]]
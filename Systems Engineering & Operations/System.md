## Formal Definition

**A System** is a cohesive conglomeration of interrelated and interacting elements—including hardware, software, people, processes, and facilities—that work together toward a common goal. It is characterized by **emergence**, where the properties of the whole system are not found in any of the individual parts alone, and by a clearly defined **boundary** that distinguishes the system from its external environment.

## Historical Development

### Key Milestones

- **1940s:** Development of Cybernetics by Norbert Wiener, focusing on control and communication in animal and machine.
    
- **1950s:** Ludwig von Bertalanffy publishes the foundations of **General Systems Theory (GST)**, arguing for universal principles applicable to all systems regardless of their nature.
    
- **1990:** The International Council on Systems Engineering (INCOSE) is founded, formalizing "System" as a distinct engineering discipline.
    

### Foundational Contributors

1. **Ludwig von Bertalanffy (1901–1972):** Biologist who established the concept of "Open Systems" that exchange matter and energy with their environment.
    
2. **Jay Wright Forrester (1918–2016):** Founder of [[Dynamic Systems Theory]], dealing with the simulation of interactions in complex systems.
    
3. **Norbert Wiener (1894–1964):** Mathematician who established the principles of feedback and control loops within systems.
    

## Mathematical Formulation

### General Form

A system S can be formally defined as an ordered pair consisting of a set of elements E and a set of relations R mapping those elements:

S=(E,R)

### Component Breakdown

- **E={e1​,e2​,…,en​}:** The set of entities or components.
    
- **R={r1​,r2​,…,rm​}:** The set of relationships where ri​⊆E×E.
    
- **State Function:** The system state at time t can be represented as X(t), where its evolution is defined by:
    
    X˙(t)=f(X(t),U(t),t)
    
    Where U(t) represents external inputs.
    

## Fundamental Principles

### Core Assumptions

1. **Holism:** The system is viewed as a whole; analyzing parts in isolation is insufficient to understand system behavior.
    
2. **Hierarchy:** Systems exist within systems (subsystems) and are parts of larger systems (supersystems).
    
3. **[[Entropy]]:** Closed systems tend toward disorder, while open systems maintain organization through the intake of information and energy.
    

### Governing Laws/Theorems

- **The Principle of Emergence:** The whole is greater than the sum of its parts.
    
- **First Law of Systematics:** A system is more than the sum of its parts; it is the product of their interactions.
    

## Theoretical Framework

### Structural vs. Behavioral View

- **Structural:** Focuses on the physical or logical arrangement of parts (The "What").
    
- **Behavioral:** Focuses on the inputs, transformations, and outputs (The "How it works").
    

### Relationship to Other Concepts

- **System vs. Subsystem:** A system is the primary focus of interest, whereas a [[Subsystem]] is a component that is itself a system.
    
- **System vs. Environment:** Everything outside the system boundary that can influence the system or be influenced by it.
    

## Classification and Variants

### By Interaction with Environment

1. **Open System:** Exchanges energy, matter, and information with the environment (e.g., a spacecraft).
    
2. **Closed System:** Isolated from its environment; theoretical in nature but used for specific thermodynamic modeling.
    

### By Complexity

1. **Simple Systems:** Predictable, linear interactions.
    
2. **Complex Adaptive Systems (CAS):** Systems that learn or change based on experience (e.g., the global economy or an ecosystem).
    

## Physical Interpretation

### Engineering Significance

In aerospace, a "system" is the entire vehicle (e.g., the Falcon 9 rocket). It encompasses the hardware (engines), software (flight code), and the human operators (ground control).

![an engineering V-model for system development, generada por IA](https://encrypted-tbn2.gstatic.com/licensed-image?q=tbn:ANd9GcQXHhhMlG1b6kTF22ufsQgnrXWfaqaowwf_i7bVTCEY4NEcFCrb1OJ-JyPMWJ5p__eHAn3zZwkFitAIsdsP7YQ3nNJTToUT87G3TB6ubJjZuv4txp4)


## Applications

### Engineering Disciplines

1. **Aerospace Engineering:** Designing a satellite as a system of thermal, power, and propulsion subsystems.
    
2. **Systems Biology:** Modeling a cell as a system of metabolic pathways.
    

## Implementation Considerations

### Software Tools

- **SysML (Systems Modeling Language):** Used to define system blocks and their internal relationships.
    
- **Simulink:** Used for time-domain simulation of system behavior.
    

## Advantages and Limitations

### Strengths

1. **Optimization:** Allows for balancing competing requirements across different departments.
    
2. **Safety:** Identifying failure modes that occur only when components interact.
    

### Weaknesses

1. **Reductionist Failure:** If the system is too complex, engineers may revert to "siloed" thinking, missing emergent risks.
    
2. **Boundary Definition:** Incorrectly defining the system boundary can lead to missing external factors (disturbances).
    

## See Also

- [[Subsystem]]
    
- [[System Architecture]]
    
- [[Emergence]]
    
- [[Concept of Operations]]
    
- [[Interface Control Document]]
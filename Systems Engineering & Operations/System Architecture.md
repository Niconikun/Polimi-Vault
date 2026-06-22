## Formal Definition

**System Architecture** is the fundamental organization of a system, embodied in its components, their relationships to each other and the environment, and the principles governing its design and evolution. It represents a high-level conceptual model that defines the structure, behavior, and more views of a system, serving as the primary artifact to manage complexity, allocate functions to physical resources, and ensure the system meets its stakeholder requirements and quality attributes.

## Historical Development

### Key Milestones

- **1960s:** The term "Architecture" is first applied to computer systems by Gene Amdahl and others at IBM during the development of the System/360.
    
- **1987:** John Zachman publishes _"A Framework for Information Systems Architecture,"_ introducing the idea of multiple architectural viewpoints.
    
- **2011:** ISO/IEC/IEEE 42010 is established, standardizing the terminology and requirements for architectural descriptions of systems and software.
    

### Foundational Contributors

1. **Gene Amdahl (1922–2015):** Defined computer architecture as the functional appearance of a system to the user, distinct from its physical implementation.
    
2. **Eberhardt Rechtin (1926–2006):** Known as the "Father of Systems Architecting," he developed the heuristics that guide the design of complex, large-scale systems.
    
    
3. **John Zachman (1934–Present):** Created the Zachman Framework, providing a logical structure for classifying the artifacts of an enterprise architecture.
    

## Mathematical Formulation

### General Form

A System Architecture A can be modeled as an abstraction comprising a set of elements E, their relations R, and the set of constraints C:

A={E,R,C}

### Component Breakdown

- **Elements (E):** E={e1​,e2​,…,en​} representing functional or physical entities.
    
- **Relations (R):** R⊆E×E representing the interfaces, dependencies, and communication paths.
    
- **Constraints (C):** C={c1​,c2​,…,ck​} representing the design rules, performance requirements, and physical laws (e.g., mass budgets, power limits).
    

## Fundamental Principles

### Core Assumptions

1. **Holism:** The architecture focuses on the "whole" system and the emergent properties that arise from the interaction of its parts.
    
2. **Decomposition and Integration:** The architecture must provide a clear path for breaking the system down (decomposition) and putting it back together (integration).
    
3. **Viewpoint Separation:** No single diagram can capture an entire architecture; different "views" (logical, physical, functional) are required to satisfy different stakeholders.
    

### Governing Laws/Theorems

- **Conway’s Law:** Organizations which design systems are constrained to produce designs which are copies of the communication structures of these organizations.
    
- **The Principle of Least Coupling:** A well-architected system minimizes the dependencies between its components to enhance maintainability and robustness.
    

## Theoretical Framework

### The "Views" of Architecture

1. **Functional Architecture:** Defines the logical transformations and data flows required to meet system objectives.
    
2. **Physical Architecture:** Defines the actual hardware, software, and human elements and their spatial/structural arrangement.
    
3. **Technical Architecture:** Defines the standards, protocols, and technologies (the "rules") used to build the system.
    

### Relationship to Other Concepts

- **Connection to Subsystem:** The architecture defines the boundaries and responsibilities of each [[Subsystem]].
    
- **Connection to ICD:** The architecture identifies where interfaces exist; the [[Interface Control Document]] specifies the details of those interfaces.
    

## Classification and Variants

### By Structural Pattern

1. **Monolithic Architecture:** A single-tier system where all components are tightly integrated.
    
2. **Layered (Hierarchical) Architecture:** Components are organized into layers, where each layer provides services to the one above it.
    
3. **Distributed/Microservices Architecture:** A system composed of independent, networked components that communicate via messages.
    

## Physical Interpretation

### Aerospace Significance

In spacecraft engineering, the architecture defines the "Bus" vs. "Payload" split. It determines whether the satellite will be a single large platform or a constellation of smaller CubeSats to achieve the mission defined in the [[Concept of Operations]].

## Applications

### Engineering Disciplines

1. **Systems Engineering:** Creating the "Blueprints" for complex platforms like aircraft, power plants, or telecommunication networks.
    
2. **Software Engineering:** Defining the high-level structure of software applications (e.g., Client-Server, MVC).
    

## Implementation Considerations

### Software Tools

- **Enterprise Architect / Sparx:** A widely used tool for UML and SysML modeling.
    
- **Cameo Systems Modeler:** The industry standard for MBSE (Model-Based Systems Engineering).
    
- **Capella:** An open-source tool specifically designed for the Arcadia systems engineering method.
    

## Advantages and Limitations

### Strengths

1. **Complexity Management:** Provides a "Big Picture" that allows teams to understand how their specific part fits into the whole.
    
2. **Risk Identification:** Reveals potential bottlenecks, single points of failure, and interface conflicts early in the design.
    

### Weaknesses

1. **Abstractions vs. Reality:** An architecture that is too abstract may ignore critical physical constraints, leading to integration failure.
    
2. **Rigidity:** If the architecture is too "brittle," it becomes difficult to adapt the system to changing requirements or new technologies.
    

## See Also

- [[Subsystem]]
    
- [[Functional Decomposition]]
    
- [[Physical Architecture Mapping]]
    
- [[Interface Control Document]]
    
- [[Concept of Operations]]
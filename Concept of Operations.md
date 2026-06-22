## Formal Definition

**Concept of Operations (ConOps)** is a user-oriented document that describes the characteristics of a proposed system from the viewpoint of an individual who will use or operate that system. It communicates the high-level quantitative and qualitative system characteristics to the user, buyer, and other stakeholders, detailing how the system will be used, the environment in which it will operate, and the specific missions it is intended to accomplish.

## Historical Development

### Key Milestones

- **1970s-1980s:** Originated within the U.S. Department of Defense (DoD) as a means to bridge the communication gap between military commanders (users) and engineers (builders).
    
- **1992:** IEEE Std 1362 is drafted, providing a formal industry standard for the format and content of a ConOps document.
    
- **2010s:** Modern Systems Engineering adopts the ConOps as the foundational "left-side" entry point of the V-Model, driving all subsequent requirement elicitation.
    

### Foundational Contributors

1. **The Department of Defense (DoD):** Instrumental in formalizing the ConOps through the MIL-STD-490 series to ensure mission objectives drove technical design.
    
2. **IEEE (Institute of Electrical and Electronics Engineers):** Standardized the ConOps structure (IEEE 1362), ensuring its applicability beyond military use into civil and commercial engineering.
    

## Mathematical Formulation

### General Form

While primarily a narrative document, a ConOps can be represented as a set of **Operational Scenarios** (S) that map the system state (X) and environmental conditions (E) to desired outcomes (O):

S:(Xt​,Et​)→Ot+Δt​

### Component Breakdown

- **Operational Scenarios (S):** Step-by-step sequences of events.
    
- **Environment (E):** Constraints such as temperature, radiation, or communication latency.
    
- **Mission Objectives (O):** The quantitative metrics of success (e.g., "capture image with 1-meter resolution").
    

## Fundamental Principles

### Core Assumptions

1. **User-Centricity:** The document must be written in the language of the user (e.g., a pilot or technician) rather than the language of the designer (e.g., a software or mechanical engineer).
    
2. **Operational Reality:** It assumes a specific context of use, including the presence of external systems and human operators.
    
3. **Scenario-Based:** It relies on "vignettes" or use-cases to illustrate how the system functions in diverse situations (nominal, off-nominal, and emergency).
    

### Governing Laws/Theorems

- **The "Operational Imperative":** If a system requirement cannot be traced back to a need expressed in the ConOps, it is potentially gold-plating and may not add value to the mission.
    

## Theoretical Framework

### Relationship to Other Concepts

1. **Connection to Requirements Engineering:**
    
    - The ConOps is the _parent_ of the System Requirements Document (SRD). Requirements define _what_ the system must do; the ConOps defines _how_ it will be used in the field.
        
2. **Contrast with [[System Architecture]]:**
    
    - **ConOps:** Focuses on the "Black Box" behavior from the outside.
        
    - **Architecture:** Focuses on the "White Box" internal structure of subsystems.
        

## Classification and Variants

### By Application

1. **Operational Concept (OpsCon):** Specifically focuses on the operational phase of the lifecycle.
    
2. **Mission Concept:** High-level view focusing purely on the objectives (common in early-stage NASA/ESA studies).
    

## Derivation and Proof

### The 6 Key Questions of a ConOps

To derive a complete ConOps, the architect must answer:

1. **Who** are the stakeholders and operators?
    
2. **What** are the primary missions and goals?
    
3. **Where** will the system be deployed (environment)?
    
4. **When** will activities occur (timeline/sequence)?
    
5. **Why** is the system being developed (justification)?
    
6. **How** will the system be supported and maintained?
    

## Physical Interpretation

### Aerospace Significance

In spacecraft design, the ConOps details the launch phase, the deployment sequence (e.g., solar array unfurling), the science observation phase, and the eventual decommissioning or de-orbiting. It defines the "Day in the Life" (DITL) of the satellite.

## Applications

### Engineering Disciplines

1. **Aerospace Engineering:** Defining the communication windows between a Mars rover and an orbiting relay satellite.
    
2. **Traffic Systems Engineering:** Describing how an automated tolling system handles vehicles without transponders or during power outages.
    

## Implementation Considerations

### Software Tools

- **Model-Based Systems Engineering (MBSE):** Uses **Use Case Diagrams** and **Sequence Diagrams** in SysML to model the scenarios described in the ConOps.
    
- **Visual Paradigms:** High-level graphics (OV-1 diagrams) are often created in vector software to provide a "big picture" view.
    

## Advantages and Limitations

### Strengths

1. **Shared Vision:** Ensures all stakeholders have the same mental model of the system.
    
2. **Validation Baseline:** Provides the criteria for final System Validation (did we build the right system for this mission?).
    

### Weaknesses

1. **Ambiguity:** Because it is written in natural language, it can be prone to multiple interpretations if not paired with rigorous modeling.
    
2. **Stagnation:** Often neglected after the design phase, leading to a "disconnect" between how the system was designed and how it is actually operated.
    

## See Also

- [[Verification & Validation]]
    
- [[Requirements Engineering]]
    
- [[System Architecture]]
    
- [[Subsystem]]
    
- [[Interface Control Document]]
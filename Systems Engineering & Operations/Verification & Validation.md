## Formal Definition

**Verification & Validation (V&V)** is the independent set of procedures used to check that a product, service, or system meets requirements and specifications and that it fulfills its intended purpose. While often grouped together, they address two distinct questions: **Verification** asks, "Did we build the system right?" (conformance to specifications), whereas **Validation** asks, "Did we build the right system?" (satisfaction of user needs).

## Historical Development

### Key Milestones

- **1980s:** The "V-Model" emerges in German and U.S. defense standards, providing a visual mapping between development phases and their corresponding testing phases.
    
- **1997:** IEEE Standard 1012 is established, providing a rigorous framework for Software Verification and Validation.
    
- **2015:** ISO/IEC/IEEE 15288 is updated to further integrate V&V processes into the complete system life cycle.
    

### Foundational Contributors

1. **Barry Boehm (1935–2022):** Software engineer who popularized the distinction between "building the system right" and "building the right system."
    
2. **Kevin Forsberg and Harold Mooz:** Co-developers of the "V-Model" in 1991, which became the standard visualization for V&V in systems engineering.
    

## Mathematical Formulation

### General Form

V&V can be modeled as a series of mapping evaluations between different domains:

- **Verification:** f(Design)=?Requirements
    
- **Validation:** f(System)=?Stakeholder Needs
    

### Component Breakdown

- **Verification (Ver​):** Ensures that the output of a phase matches the input requirements of that phase.
    
- **Validation (Val​):** Ensures that the final realized system S operates within the operational environment E to achieve mission objective M.
    
    Val​⟹(S×E)→M
    

## Fundamental Principles

### Core Assumptions

1. **Independence:** For high-criticality systems, V&V should be performed by individuals or organizations other than those who designed the system (Independent V&V or IV&V).
    
2. **Early Start:** V&V planning begins as soon as requirements are defined, not after the system is built.
    
3. **Continuous Process:** V&V is not a final "test" phase but a continuous activity occurring throughout the lifecycle.
    

### Governing Laws/Theorems

- **The Rule of Ten:** The cost of correcting an error increases by a factor of ten for every lifecycle stage it passes through without being detected by V&V.
    

## Theoretical Framework

### Relationship to Other Concepts

1. **Connection to Requirements Engineering:**
    
    - Verification is performed against **System Requirements**. Validation is performed against **Stakeholder Requirements** or Concept of Operations (ConOps).
        
2. **Contrast with Quality Assurance (QA):**
    
    - **V&V:** Focuses on the product itself and its technical correctness.
        
    - **QA:** Focuses on the _processes_ used to create the product.
        

## Classification and Variants

### By Method (The "Four Horsemen" of V&V)

1. **Inspection:** Visual examination of documentation, code, or hardware without exercise of the system.
    
2. **Analysis:** Using mathematical models, simulations, or calculations to predict behavior.
    
3. **Demonstration:** Observing the system performing a functional task to show it works as intended without high-precision measurement.
    
4. **Test:** Exercise of the system under controlled conditions using instrumentation to collect precise data.
    

## Physical Interpretation

### Mechanical Significance

In aerospace, **Verification** includes checking that a bolt's material matches the drawing (Inspection) and that it can withstand a calculated load (Analysis). **Validation** involves a flight test to ensure the entire vehicle performs the mission as the pilot expects.

## Implementation Considerations

### Software Tools

- **DOORS/Jama:** Used for Requirement Traceability Matrices (RTM) to ensure every requirement has a corresponding verification method.
    
- **MATLAB/Simulink:** Used for "Model-in-the-Loop" (MiL) and "Hardware-in-the-Loop" (HiL) verification.
    

## Advantages and Limitations

### Strengths

1. **Risk Reduction:** Identifies defects early when they are cheapest to fix.
    
2. **Compliance:** Provides the documented evidence required for certification (e.g., FAA or NASA flight readiness).
    

### Weaknesses

1. **Cost:** Can account for 30% to 50% of the total project budget in safety-critical fields.
    
2. **Scope Creep:** If validation is not tightly bounded, "user needs" can shift during development, making the target impossible to hit.
    

## See Also

- [[Requirements Engineering]]
    
- [[System Architecture]]
    
- [[Traceability Matrix]]
    
- [[Verification Cross Reference Matrix]]
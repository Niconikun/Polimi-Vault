## Formal Definition

A **Parallel System** is a configuration where components are arranged such that there are multiple paths for a signal or function to reach its destination. In [[control theory]], parallel structures allow for the summation of different signals (such as the P, I, and D terms in a controller). In reliability engineering, a parallel system provides **redundancy**; the system only fails if _all_ parallel components fail simultaneously. This architecture is vital for high-stakes aerospace missions where "Single Points of Failure" must be eliminated.

## Historical Development

### Key Milestones

- **1940s–50s:** Early computing pioneers like **John von Neumann** develop theories on building reliable systems from unreliable parts using redundancy.
    
- **1960s:** The **Apollo Guidance Computer (AGC)** and the Saturn V launch vehicle utilize "Triple Modular Redundancy" (TMR) to ensure that a single radiation hit wouldn't abort the moon mission.
    
- **1980s:** The **Space Shuttle** employs five identical general-purpose computers in parallel to ensure flight safety during the critical reentry phase.
    

### Foundational Contributors

1. **John von Neumann:** Formalized the logic of redundancy and "probabilistic logics," which allow a system to "vote" on a correct result if one parallel branch fails.
    

## Mathematical Formulation

### 1. [[Transfer Function]] ([[Control Theory]])

For $n$ components in parallel with transfer functions $G_1(s), G_2(s), \dots, G_n(s)$, the total system output is the **sum** of the individual outputs:

$$G_{total}(s) = G_1(s) + G_2(s) + \dots + G_n(s)$$

### 2. Reliability (Redundancy)

The probability that a parallel system will fail ($Q_{sys}$) is the product of the failure probabilities ($q_i$) of its components. The reliability ($R_{sys}$) is:

$$R_{sys} = 1 - \prod_{i=1}^{n} (1 - R_i)$$

_Note: Because you are subtracting a product of decimals from 1, the total reliability is always significantly **higher** than the reliability of any single component._

## Fundamental Principles

### Core Assumptions

1. **Independence:** Assumes that the failure of one branch does not cause the other branches to fail (e.g., an electrical short in Battery A must not blow the fuse for Battery B).
    
2. **Common-Mode Failure:** The "kryptonite" of parallel systems; if a design flaw exists in all parallel units, they will all fail at the same time regardless of redundancy.
    

### Governing Laws

- **The Law of Diminishing Returns:** Adding the first backup (2 units) massive increases reliability. Adding a tenth backup adds very little reliability while greatly increasing cost and mass.
    

## Theoretical Framework

### Types of Redundancy

- **Active Redundancy:** All parallel paths operate simultaneously (e.g., four engines on a 747).
    
- **Standby (Passive) Redundancy:** Backup units are kept off until a failure is detected in the primary unit (e.g., a backup transmitter on a satellite).
    
- **Voting Logic:** Three systems run in parallel, and a "voter" picks the result agreed upon by at least two (2-out-of-3 logic).
    

## Physical Interpretation

### The "Multiple Bridges" Analogy

Imagine you need to cross a river to deliver a message.

- **Series:** You have to cross one specific bridge. If it's washed out, you fail.
    
- **Parallel:** There are three different bridges. You only need **one** to be standing to get the message across. Even if a flood takes out two, the mission is a success.
    

## Advantages and Limitations

### Strengths

1. **Fault Tolerance:** Allows the spacecraft to "fail operational" or "fail safe."
    
2. **Higher Performance:** In control, parallel structures allow different "experts" (like an Integrator for error and a Differentiator for speed) to work together.
    

### Limitations

1. **Mass and Cost:** Doubling the components doubles the weight and the price tag—a major concern in orbital launches.
    
2. **Complexity:** Requires "failure detection" logic to know when to switch to the backup.
    

## Applications

### Spacecraft Design

1. **Power Systems:** Multiple strings of solar cells in parallel; if a micrometeoroid hits one string, the others keep providing power.
    
2. **Communication:** Dual-redundant transponders (Side A and Side B).
    
3. **Propulsion:** Clusters of small thrusters where the software can redistribute the torque if one nozzle clogs.
    

---

## See Also

- [[Series System]]
    
- [[Reliability Theory]]
    
- [[Triple Modular Redundancy (TMR)]]
    
- [[Fault Tolerance]]
    

## Recommended Tags:

#systems-engineering #reliability #parallel-system #redundancy #control-theory #fault-tolerance #aerospace-design
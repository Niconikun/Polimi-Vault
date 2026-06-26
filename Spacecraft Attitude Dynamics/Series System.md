## Formal Definition

A **Series System** is a configuration of components or subsystems connected such that the output of one component serves as the input to the next. In a functional block diagram, the signal must pass through every block in sequence to reach the destination. From a reliability perspective, a series system requires every single component to function for the overall system to succeed. If a system is composed of $n$ components in series, the failure of any one component results in the failure of the entire system.

## Historical Development

### Key Milestones

- **18th-19th Century:** Early industrial machinery and telegraph lines are designed as series systems; a single break in a wire or a snapped belt would halt the entire operation.
    
- **1940s:** During WWII, the complexity of V-2 rockets and early radar systems highlights the "Product Law of Reliability," proving that adding more parts in series drastically reduces the chance of mission success.
    
- **1950s:** The development of the **Minuteman Missile** leads to the "High Reliability" movement, focusing on making individual series components extremely robust because redundancy (parallelism) was too heavy.
    

### Foundational Contributors

1. **Robert Lusser:** A pioneer of reliability theory who formulated "Lusser’s Law," which mathematically defines the reliability of series systems.
    

## Mathematical Formulation

### 1. [[Transfer Function]] (Control Theory)

For a series of $n$ linear systems with individual transfer functions $G_1(s), G_2(s), \dots, G_n(s)$, the total system [[transfer function]] $G_{total}(s)$ is the **product** of the individual functions:

$$G_{total}(s) = G_1(s) \cdot G_2(s) \cdot \dots \cdot G_n(s)$$

### 2. Reliability (Mission Success)

If $R_i$ is the probability that component $i$ will function correctly, the total system reliability $R_{sys}$ is:

$$R_{sys} = \prod_{i=1}^{n} R_i = R_1 \times R_2 \times \dots \times R_n$$

_Note: Because $R_i \le 1$, the total reliability is always less than or equal to the reliability of the weakest component._

## Fundamental Principles

### Core Assumptions

1. **Independence:** Assumes the failure or performance of one component does not physically damage the next (though it stops the signal).
    
2. **No Feedback:** In a pure series system, information only flows in one direction (Open-Loop).
    

### Governing Laws

- **Lusser’s Law:** States that the reliability of a series system is the product of the reliabilities of its components.
    

## Theoretical Framework

### The Multiplication of Errors

In a series system, errors and delays accumulate.

- **Gain:** The total gain is the product of individual gains.
    
- **Phase Lag:** The total phase lag is the **sum** of individual phase lags.
    
    In spacecraft GNC, this is critical because every sensor filter and actuator delay adds phase lag, which can eventually make a [[feedback loop]] unstable.
    

## Physical Interpretation

### The "Christmas Lights" Analogy

Imagine an old string of Christmas lights.

- If one bulb burns out, the circuit is broken and every light on the string goes dark.
    
- To fix it, you have to test every single bulb.
    
    In a satellite, a series system might be: **Battery $\to$ Power Regulator $\to$ Computer $\to$ Transmitter**. If any of these four fail, the satellite becomes a "brick."
    

## Advantages and Limitations

### Strengths

1. **Simplicity:** Easiest to design, build, and model.
    
2. **Cost and Weight:** Uses the minimum number of parts to achieve a goal, which is vital for mass-constrained missions like CubeSats.
    

### Limitations

1. **Zero Fault Tolerance:** There is no backup. A single "Single Point of Failure" (SPOF) can end the mission.
    
2. **Performance Decay:** The more stages you add, the more noise and delay are introduced into the signal.
    

## Applications

### Spacecraft Architectures

1. **Signal Chains:** A Star Tracker lens $\to$ CCD $\to$ Image Processor $\to$ Attitude Estimator.
    
2. **Launch Vehicle Stages:** The First Stage, Second Stage, and Fairing operate as a series system in time; if any stage fails to ignite or separate, the payload does not reach orbit.
    
3. **Command Strings:** The sequence of logic gates required to trigger a pyrotechnic bolt.
    

---

## See Also

- [[Parallel System]]
    
- [[Reliability Theory]]
    
- [[Transfer Function]]
    
- [[Phase Lag]]
    

## Recommended Tags:

#systems-engineering #reliability #control-theory #series-system #aerospace-design #GNC
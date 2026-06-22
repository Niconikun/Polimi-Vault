## Formal Definition

A **Feedback System** is a configuration where the output of a system is measured and "fed back" to the input to influence the future behavior of the system. By comparing the actual output (the current state) with the desired output (the setpoint), the system generates an **[[Error Signal]]**. The controller then uses this error to adjust the actuators, effectively reducing the discrepancy over time. This architecture allows a system to remain stable and accurate even in the presence of external disturbances, sensor noise, or uncertainties in the system's physics.

## Historical Development

### Key Milestones

- **1788:** **James Watt** invents the centrifugal governor for steam engines, creating the first widely used mechanical feedback system.
    
- **1868:** **James Clerk Maxwell** publishes "On Governors," the first mathematical analysis of feedback and stability.
    
- **1927:** **Harold Black** invents the negative feedback amplifier at Bell Labs, revolutionizing telecommunications.
    
- **1960s:** Feedback becomes the heart of the **Apollo Guidance Computer**, allowing the Lunar Module to throttle its engine based on real-time altitude readings from a landing radar.
    

### Foundational Contributors

1. **Harold Black:** Proved that negative feedback could trade "gain" for "consistency," making systems immune to internal component variations.
    
2. **Norbert Wiener:** Founded the field of **Cybernetics**, which is the study of feedback and control in both machines and living organisms.
    

## Mathematical Formulation

### The Closed-Loop [[Transfer Function]]

For a system with a plant $G(s)$ and a feedback sensor/path $H(s)$, the relationship between the input $R(s)$ and output $Y(s)$ is:

$$\frac{Y(s)}{R(s)} = \frac{G(s)}{1 + G(s)H(s)}$$

### The [[Characteristic Equation]]

The denominator of this fraction, $1 + G(s)H(s) = 0$, is known as the **[[Characteristic Equation]]**. The roots of this equation (the poles) determine whether the feedback will be stable or if it will cause the system to oscillate wildly.

## Fundamental Principles

### Core Assumptions

1. **[[Observability]]:** You cannot have feedback if you cannot measure the output.
    
2. **Controllability:** You cannot have feedback if the controller doesn't have the "muscles" (actuators) to change the output.
    

### Governing Laws

- **Negative Feedback:** The feedback signal is subtracted from the input. This stabilizes the system and drives the error toward zero.
    
- **Positive Feedback:** The feedback signal is added to the input. This generally leads to instability or "latching" (like the [[Schmitt Trigger]]), but it is used in oscillators.
    

## Theoretical Framework

### The Benefit of Feedback

- **Disturbance Rejection:** If a solar storm pushes your satellite, the feedback loop "sees" the change in attitude and fires a thruster to correct it.
    
- **Robustness:** Even if your thruster is 10% weaker than you thought, the feedback loop will simply leave it on slightly longer until the goal is reached.
    

## Physical Interpretation

### The "Shower Temperature" Analogy

Imagine you are adjusting the water temperature in a shower.

- **Open-Loop:** You turn the knob to a specific spot and hope for the best. If someone flushes a toilet, the water gets boiling hot, and the system doesn't care.
    
- **Feedback System:** You stick your hand in the water (Sensor). You feel it's too hot (Error). Your brain (Controller) tells your hand to turn the cold knob (Actuator). You keep adjusting until the temperature is exactly right.
    

## Advantages and Limitations

### Strengths

1. **Accuracy:** Can achieve precise results even with "cheap" or imprecise components.
    
2. **Stability:** Can make an inherently unstable system (like a rocket standing on its tail) stay perfectly upright.
    

### Limitations

1. **Instability Risk:** If the feedback is too aggressive or delayed, the system can "over-correct" and go into an out-of-control oscillation.
    
2. **Complexity:** Requires sensors and wiring that an open-loop system doesn't need.
    

## Applications

### Spacecraft GNC

1. **Attitude Control:** Using Gyros/Star Trackers to keep a telescope pointed at a star.
    
2. **Thermal Control:** Using a thermostat to pulse a heater on/off based on a temperature probe.
    
3. **Orbit Maintenance:** Using GPS to determine if a satellite has drifted and firing thrusters to return it to its "slot."
    

---

## See Also

- [[Open-Loop System]]
    
- [[Transfer Function]]
    
- [[PID Controller]]
    
- [[Stability Analysis]]
    

## Recommended Tags:

#control-theory #feedback #closed-loop #GNC #stability #cybernetics #aerospace-engineering
## Formal Definition

**Rise Time** is the time required for a system's output to go from a specified low value to a specified high value during its initial response to a step input. For underdamped systems (where oscillations occur), it is typically measured as the time to go from **0% to 100%** of the final value. For overdamped systems, it is commonly measured from **10% to 90%**. While a shorter rise time indicates a more responsive system, it often comes at the cost of increased **[[Overshoot]]** and potential structural vibration.

## Historical Development

### Key Milestones

- **1920s–30s:** Early telecommunications engineers define rise time to characterize how fast a vacuum tube or relay could "flip" states.
    
- **1950s:** The advent of supersonic flight makes rise time a critical safety metric; if an aircraft's elevators have a slow rise time, the pilot cannot pull up fast enough to avoid an obstacle.
    
- **1970s:** Digital control systems introduce the "Sample Rate" limitation, where the rise time is physically limited by how fast the computer can "talk" to the actuators.
    

## Mathematical Formulation

For a standard second-order system, the rise time is inversely proportional to the **[[Natural Frequency]]** ($\omega_n$).

### Approximate Formula (Underdamped)

For a system with a damping ratio $\zeta$ and [[Natural Frequency]] $\omega_n$:

$$t_r \approx \frac{1.8}{\omega_n}$$

_Note: This is a common rule of thumb. A more precise version for $0 < \zeta < 1$ is:_

$$t_r = \frac{\pi - \beta}{\omega_d}$$

_Where $\beta = \cos^{-1}(\zeta)$ and $\omega_d = \omega_n\sqrt{1-\zeta^2}$ (the Damped [[Natural Frequency]])._

## Fundamental Principles

### Core Assumptions

1. **Actuator Capability:** Assumes the actuators have enough "strength" (Torque/Force) to move the system that quickly. In reality, **Actuator Saturation** often limits the minimum possible rise time.
    
2. **Small Signal:** Assumes the system is operating in a linear range where the "rules" of the [[transfer function]] apply.
    

### Governing Laws

- **The Bandwidth-Rise Time Relationship:** In the frequency domain, rise time is inversely proportional to the system's bandwidth ($BW$). The "faster" the system (shorter $t_r$), the higher the frequency of signals it can track.
    

## Theoretical Framework

### The Speed vs. Precision Trade-off

Rise time is the first phase of a maneuver.

- **High Gain:** Increasing your controller gain ($K_p$) will shorten the rise time but will likely increase your **[[Overshoot]]**.
    
- **Lower Gain:** Decreasing gain makes the system safer and smoother but results in a "sluggish" rise time.
    

## Physical Interpretation

### The "Sprinting" Analogy

Imagine a 100-meter dash.

- **Rise Time:** How fast the runner gets from the starting blocks to the 100m finish line for the first time.
    
- **[[Overshoot]]:** The runner is going so fast they can't stop at the finish line and run 10 meters into the grass.
    
- **[[Settling Time]]:** The total time it takes for them to stop, turn around, and walk back to stand exactly on the finish line.
    

## Advantages and Limitations

### Strengths

1. **Combat/Evasion:** Essential for tactical maneuvers where the first few milliseconds of a response determine success (e.g., missile interception).
    
2. **Disturbance Rejection:** A system with a fast rise time can "catch" and correct a disturbance (like a gust of wind) before it pushes the craft too far.
    

### Limitations

1. **Structural Stress:** A very fast rise time implies high acceleration, which can cause "jerking" that damages delicate satellite components or solar arrays.
    
2. **Energy Consumption:** Reaching the target faster usually requires much higher peak power/fuel consumption.
    

## Applications

### Spacecraft GNC

1. **Reaction Wheel Command:** How quickly the wheel can ramp up its RPM to provide counter-torque.
    
2. **Thruster Ignition:** The "Rise Time" of the combustion chamber pressure, which determines how "sharp" the control pulse is.
    
3. **Emergency Sun Acquisition:** If a satellite loses power, it must have a fast enough rise time in its control loop to find the Sun before the batteries die.
    

---

## See Also

- [[Settling Time]]
    
- [[Overshoot]]
    
- [[Natural Frequency]]
    
- [[Bandwidth]]
    

## Recommended Tags:

#control-theory #rise-time #GNC #performance-metrics #step-response #aerospace-engineering #stability
## Formal Definition

**Overshoot** refers to the maximum amount by which a system's output exceeds its desired steady-state value (the setpoint) during its initial response to a change in input. It is typically expressed as **Percentage Overshoot (%OS)** relative to the step input magnitude. Overshoot is a direct consequence of the system's momentum (or energy storage) and the delay in the control response; if the controller cannot "brake" the system fast enough as it approaches the target, the state will swing past the desired point.

## Historical Development

### Key Milestones

- **19th Century:** Mechanical engineers noted that steam engine governors often "hunted" (oscillated) past their target speed, a physical manifestation of overshoot.
    
- **1940s:** During WWII, the need for rapid, precise tracking for anti-aircraft guns led to the formalization of "Damping" as the mathematical cure for overshoot.
    
- **1960s:** NASA's **Apollo** mission maneuvers required strict "Zero Overshoot" constraints for certain docking procedures to prevent structural damage between the Command Module and the Lunar Module.
    

### Foundational Contributors

1. **Harry Nyquist:** Provided the frequency-domain tools to predict when a system would "ring" or overshoot based on its phase margin.
    

## Mathematical Formulation

### Percentage Overshoot (%OS)

For a second-order system, overshoot is mathematically related to the **Damping Ratio** (ζ):

- **If ζ<1 (Underdamped):** The system will overshoot.
    
- **If ζ=1 (Critically Damped):** The system reaches the target as fast as possible with **zero** overshoot.
    
- **If ζ>1 (Overdamped):** The system has no overshoot but is much slower.
    

## Fundamental Principles

### Core Assumptions

1. **Linearity:** Assumes the system behaves like a standard mass-spring-damper. In reality, non-linearities like **Actuator Saturation** often make overshoot worse.
    
2. **Step Input:** Overshoot is usually measured using a "Step Response" (a sudden change in the goal).
    

### Governing Laws

- **The Law of Inertia:** Objects in motion tend to stay in motion. In a spacecraft, the [[rotational kinetic energy]] must be removed by the actuators _before_ the target angle is reached to prevent overshoot.
    

## Theoretical Framework

### The Trade-off

Overshoot is almost always in a "tug-of-war" with **[[Rise Time]]**:

- If you want the satellite to turn **faster**, you usually have to accept more **overshoot**.
    
- If you want **zero overshoot**, you usually have to accept a **slower** turn.
    

## Physical Interpretation

### The "Braking for a Red Light" Analogy

Imagine you are driving toward a stop line (the Setpoint).

- **No Overshoot:** You press the brakes smoothly and stop exactly on the line.
    
- **Overshoot:** You wait too long to brake or the road is slippery. You slide 3 feet past the line before stopping and having to reverse back to it. That 3-foot gap is your **Overshoot**.
    

## Advantages and Limitations

### Strengths

1. **Speed Indication:** A small amount of overshoot (usually 5–10%) often indicates a system that is tuned for high performance and responsiveness.
    
2. **Safety Margin:** Defining a maximum allowable overshoot (e.g., <2%) ensures that mechanical limits are never exceeded.
    

### Limitations

1. **Hardware Stress:** Large overshoots cause higher mechanical loads and can trigger safety "limit switches."
    
2. **[[Integrator Windup]]:** If not managed, the integral term in a PID controller can cause massive, destructive overshoots.
    

## Applications

### Spacecraft GNC

1. **Solar Array Deployment:** Ensuring the panels don't "snap" past their locked position, which could break the hinges.
    
2. **Star Tracking:** Minimizing overshoot so a telescope can begin taking a stable image as soon as possible after a "slew" maneuver.
    
3. **Thruster Control:** Preventing a "Bang-Bang" controller from over-correcting and causing a fuel-wasting [[Limit Cycle]].
    

---

## See Also

- [[Damping Ratio]]
    
- [[Settling Time]]
    
- [[Rise Time]]
    
- [[Integrator Windup]]
    

## Recommended Tags:

#control-theory #overshoot #damping #GNC #step-response #performance-metrics #aerospace-engineering
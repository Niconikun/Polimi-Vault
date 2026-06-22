## Formal Definition

**Deadband** is a specified range in a controller's input signal where the output remains zero. It is a non-linear characteristic introduced to prevent a system from responding to small, insignificant errors or high-frequency sensor noise. In spacecraft Attitude Determination and Control Systems (ADCS), the deadband defines the "pointing box." As long as the satellite's orientation stays within these bounds (e.g., $\pm 0.5^\circ$), the thrusters remain off to conserve propellant and reduce mechanical wear.

## Historical Development

### Key Milestones

- **Early 20th Century:** Mechanical governors for steam engines utilize "backlash" or physical gaps in linkages, which act as primitive mechanical deadbands.
    
- **1960s:** During the **Project Mercury** flights, engineers and pilots manually adjust "attitude deadbands" to balance the need for precision with the capsule's limited nitrogen supply.
    
- **1970s:** The **HEAO (High Energy Astronomy Observatory)** missions use precision-tuned digital deadbands to maintain ultra-stable pointing for X-ray telescopes without constant thruster chattering.
    

### Foundational Contributors

1. **Irmgard Flügge-Lotz:** A pioneer in "discontinuous control" (on-off systems) who established the mathematical necessity of the deadband to ensure stability in relay-based systems.
    

## Mathematical Formulation

### The Deadzone Function

The output of a deadband operator $u(t)$ based on an [[Error Signal]] $e(t)$ with a threshold $d$ is defined as:

$$u(t) = \begin{cases} e(t) - d & \text{if } e(t) > d \\ 0 & \text{if } |e(t)| \le d \\ e(t) + d & \text{if } e(t) < -d \end{cases}$$

### Impact on Fuel Consumption

In a [[Limit Cycle]] governed by a deadband, the propellant mass flow ($\dot{m}$) is often inversely proportional to the deadband width ($\alpha$). Doubling the deadband theoretically doubles the "coast time" between pulses, significantly extending mission life.

## Fundamental Principles

### Core Assumptions

1. **Acceptable Error:** Assumes the mission requirements allow for a small window of inaccuracy (e.g., a solar panel still works efficiently even if it's off by $1^\circ$).
    
2. **Noise Floor:** Assumes the deadband is wider than the [[standard deviation]] of sensor noise to prevent "false triggers."
    

### Governing Laws

- **Conservation of Momentum:** Inside the deadband, a spacecraft is essentially a "free-falling" [[Rigid Body]]; its angular momentum remains constant until it hits the edge of the deadband and the controller applies a torque.
    

## Physical Interpretation

### The "Steering Wheel Play" Analogy

Imagine driving an old truck where you can wiggle the steering wheel an inch in either direction without the tires moving.

- That inch of "play" is the **Deadband**.
    
- It prevents every tiny twitch of your hand from causing the truck to veer across the road.
    
- However, if the "play" is too large, the vehicle becomes difficult to control accurately.
    

## Advantages and Limitations

### Strengths

1. **Propellant Economy:** Stops the thrusters from fighting "ghost" errors or noise.
    
2. **Actuator Longevity:** Reduces the number of duty cycles on valves, relays, and motors.
    
3. **Vibration Reduction:** Keeps the spacecraft "quiet" for sensitive instruments by avoiding thruster shocks.
    

### Limitations

1. **Limit Cycling:** A deadband inherently creates a **[[Limit Cycle]]** oscillation.
    
2. **Steady-State Error:** By definition, a deadband allows a permanent small error to exist.
    
3. **Sensitivity:** If the deadband is too narrow, you waste fuel; if it's too wide, you might lose your communication link with Earth.
    

## Applications

### Spacecraft Systems

1. **Attitude Hold:** Keeping a satellite pointed at Earth within $\pm 1^\circ$.
    
2. **Battery Charging:** Only starting a charge cycle when the battery drops below 90% (the lower deadband) to avoid "trickle" wear.
    
3. **Momentum Management:** Allowing reaction wheel speeds to drift slightly before triggering a "desaturation" event.
    

---

## See Also

- [[Bang-Bang Control]]
    
- [[Limit Cycle]]
    
- [[Schmitt Trigger]]
    
- [[Hysteresis]]
    

## Recommended Tags:

#control-theory #deadband #ADCS #propellant-efficiency #nonlinear-systems #spacecraft-operations
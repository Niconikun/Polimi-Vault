## Formal Definition

The **Error Signal** is the difference between the **Reference Input** (desired setpoint) and the **Measured Output** (actual state) of a system. It represents the instantaneous discrepancy that the controller must work to eliminate. In a negative feedback loop, the error signal serves as the input to the controller; if the error is zero, the controller (ideally) stops changing its output because the goal has been achieved. In spacecraft GNC, an "attitude error" of 0.01∘ would be the signal that triggers a reaction wheel to speed up or slow down.

## Historical Development

### Key Milestones

- **1788:** In the Watt Steam Governor, the "error signal" was physically represented by the height of flying metal balls—the higher the balls, the greater the "speed error."
    
- **1920s:** **Nicolas Minorsky** formalizes the error signal in the context of ship steering, noting that the controller must act not just on the error itself, but on its "history" (Integral) and its "trend" (Derivative).
    
- **1940s:** During the development of radar-guided weaponry, the "error signal" became a high-frequency electronic pulse used to track aircraft.
    

### Foundational Contributors

1. **James Clerk Maxwell:** His 1868 paper was the first to mathematically treat the "error" as a variable in a differential equation.
    

## Mathematical Formulation

### The Basic Equation

In the time domain, the error signal e(t) is defined as:

e(t)=r(t)−y(t)

- r(t): Reference or Setpoint (where you want to be).
    
- y(t): Feedback or Measured Output (where you are).
    

### In the Laplace Domain

In [[Transfer Function]] notation, the error E(s) can be expressed in terms of the input R(s) and the open-loop gain L(s)=G(s)H(s):

E(s)=1+G(s)H(s)R(s)​

## Fundamental Principles

### Core Assumptions

1. **Common Units:** The reference and the feedback must be in the same units (e.g., both must be in degrees, or both must be in Volts) for the subtraction to be meaningful.
    
2. **Negative Feedback:** Assumes a "Summing Junction" where the feedback is subtracted from the input.
    

### Governing Laws

- **The Final Value Theorem:** Used to predict the **Steady-State Error**. If the error signal does not go to zero as time goes to infinity, the system has a "tracking error."
    

## Theoretical Framework

### The Controller's Perspective

The error signal is the only thing the controller "sees."

- **Proportional (P):** Looks at the **Current** error.
    
- **Integral (I):** Looks at the **Accumulated** error of the past.
    
- **Derivative (D):** Looks at the **Future** trend of the error.
    

## Physical Interpretation

### The "Speedometer" Analogy

Imagine you are driving and want to go exactly 65 mph.

- **Reference:** 65 mph.
    
- **Actual:** 62 mph.
    
- **Error Signal:** +3 mph. Your brain sees this "3 mph error" and tells your foot to press the gas. As you hit 65 mph, the error becomes 0, and you stop increasing your speed. If you hit 68 mph, the error becomes -3 mph, telling you to let off the gas.
    

## Advantages and Limitations

### Strengths

1. **Simplicity:** A single number tells the controller exactly what to do.
    
2. **Universal:** The concept works for temperature, voltage, attitude, or orbital altitude.
    

### Limitations

1. **Sensor Dependency:** If your sensor is wrong (Bias), the error signal will be wrong. The controller will achieve "Zero Error" relative to a bad sensor, leading to a physical crash.
    
2. **Noise:** High-frequency noise in the sensor can create a "jittery" error signal, causing actuators to vibrate.
    

## Applications

### Spacecraft GNC

1. **Pointing Error:** The angular difference between a telescope's current boresight and the target star.
    
2. **Velocity Error:** The difference between a lander's current descent speed and the safe touchdown speed.
    
3. **Frequency Error:** The "offset" in a communication radio's carrier frequency that must be corrected to maintain a link.
    

---

## See Also

- [[Feedback System]]
    
- [[Steady-State Error]]
    
- [[PID Control]]
    
- [[Sensors]]
    

## Recommended Tags:

#control-theory #error-signal #feedback #GNC #setpoint #mathematics #automation
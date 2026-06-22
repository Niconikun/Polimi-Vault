## Formal Definition

A **Schmitt Trigger** is a comparator circuit or logical operator that utilizes **positive feedback** to implement **[[Hysteresis]]**. Unlike a standard comparator that has a single threshold, a Schmitt Trigger has two distinct thresholds: an Upper Threshold Voltage (UTV) and a Lower Threshold Voltage (LTV). When the input signal rises above the UTV, the output switches high; it remains high until the input signal drops below the LTV. This "dual-threshold" behavior prevents "chattering"—rapid, unwanted switching caused by noise on the input signal.



## Historical Development

### Key Milestones
- **1934:** **Otto Schmitt** invents the "thermionic trigger" (using vacuum tubes) while a graduate student at Washington University in St. Louis, initially to study nerve impulse propagation.
- **1950s:** The device is adapted for transistor technology and becomes a fundamental component in digital logic for converting analog signals into square waves.
- **1960s–Present:** Schmitt Triggers are integrated into spacecraft **[[Pulse Width Modulation (PWM)]]** controllers to manage thruster firing and battery charge regulators.

### Foundational Contributors
1. **Otto Schmitt (1913–1998):** An American biophysicist and inventor who pioneered the field of biomimetics and created the trigger to solve noise problems in biological monitoring.

## Mathematical Formulation

### The [[Hysteresis]] Loop
The output state $y(t)$ is a function of the input $x(t)$ and its previous state.

- **Switch High Condition:** If $x(t) > V_{upper}$ and $y_{prev} = Low$, then $y(t) \to High$.
- **Switch Low Condition:** If $x(t) < V_{lower}$ and $y_{prev} = High$, then $y(t) \to Low$.

### The [[Hysteresis]] Width
The "[[Deadband]]" or window of noise immunity is defined as:
$$\Delta V = V_{upper} - V_{lower}$$



## Fundamental Principles

### Core Assumptions
1. **Bistability:** The output has only two stable states (High/Low, On/Off).
2. **Positive Feedback:** The circuit uses a portion of its output to "push" the threshold further away from the current input, ensuring a clean "snap" action.

### Governing Laws
- **The Barkhausen Stability Criterion:** While usually for oscillators, it describes the regenerative feedback that causes the Schmitt Trigger to "latch" once a threshold is crossed.

## Theoretical Framework

### Signal Conditioning in GNC
Spacecraft sensors (like Sun sensors or Horizon sensors) often produce signals with low-amplitude electrical noise. Without a Schmitt Trigger:
- A single threshold would cause the flight computer to think the sun is "flickering" in and out of view.
- With the Schmitt Trigger, the computer waits until the sun is "definitely" in view ($V_{upper}$) and doesn't stop until it is "definitely" gone ($V_{lower}$).

## Physical Interpretation

### The "Light Switch" Analogy
Imagine a light switch with a very strong spring. 
- You have to push it quite hard to get it to flip "Up." 
- Once it's "Up," you can wiggle it a little bit in the middle without the light turning off. 
- You have to push it quite far back "Down" to get it to click off. 
This "mechanical memory" is exactly how a Schmitt Trigger handles electronic signals.

## Advantages and Limitations

### Strengths
1.  **Noise Immunity:** Effectively ignores noise smaller than the [[Hysteresis]] width $\Delta V$.
2.  **Clean Transitions:** Converts slow-rising analog signals into fast-rising digital pulses, protecting digital components from "meta-stability."

### Limitations
1.  **Phase Lag:** Because the system waits for the signal to cross the *far* threshold, it introduces a small time delay (Phase Lag) into the control loop.
2.  **Complexity in Tuning:** If the [[Hysteresis]] window is too wide, the controller becomes "sluggish"; if it's too narrow, "chattering" returns.

## Applications

### Spacecraft Systems
1.  **Thruster Control (Bang-Bang):** Using a Schmitt Trigger to ensure a thruster stays on for a minimum duration to avoid damaging the valve with rapid-fire commands.
2.  **Power Management:** Turning on a heater when a battery drops to $0^\circ\text{C}$ and not turning it off until it reaches $+5^\circ\text{C}$ to prevent constant cycling.
3.  **Encoders:** Cleaning up the pulses from a Reaction Wheel's tachometer to accurately count RPM.

## See Also

- [[Bang-Bang Control]]
- [[Hysteresis]]
- [[Actuator Saturation]]
- [[Phase Lag]]

## Recommended Tags:
#electronics #Schmitt-trigger #[[Hysteresis]] #GNC #signal-conditioning #non-linear-control #aerospace-instrumentation
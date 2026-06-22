## Formal Definition

A **Single-Input Single-Output (SISO)** system is a dynamical model where the system's behavior is dictated by one control input ($u$) and observed through one measured output ($y$). In the context of aerospace, a SISO approach is often used by "[[Decoupling]]" complex spacecraft; for example, analyzing the pitch control of a satellite as an independent system, separate from roll and yaw. SISO systems are primarily analyzed in the **Frequency Domain** using Transfer Functions, whereas MIMO systems are analyzed in the **Time Domain** using State-Space.



## Historical Development

### Key Milestones
- **1920s–30s:** **Harry Nyquist** and **Hendrik Bode** at Bell Labs develop the foundational frequency-response methods for SISO amplifiers and telecommunications.
- **1940s:** During WWII, SISO theory is applied to radar-guided anti-aircraft guns and aircraft autopilots.
- **1948:** **Walter Evans** develops the **Root Locus** method, providing a graphical way to see how SISO systems behave as gain increases.
- **Present:** While satellites are inherently multi-variable, SISO remains the primary way engineers perform initial "loop-shaping" and stability margin analysis.

### Foundational Contributors
1. **Hendrik Bode:** Pioneer of the "[[Bode Plot]]," which visualizes SISO stability in terms of Gain and Phase margins.
2. **Harry Nyquist:** Developed the stability criterion that prevents closed-loop systems from oscillating.

## Mathematical Formulation

### 1. The [[Transfer Function]] (Laplace Domain)
The most common way to represent a SISO system is the ratio of the output to the input in the $s$-domain:
$$G(s) = \frac{Y(s)}{U(s)} = \frac{b_m s^m + \dots + b_1 s + b_0}{s^n + a_{n-1} s^{n-1} + \dots + a_0}$$

### 2. The State-Space Form (SISO Case)
In state-space, a SISO system is characterized by the dimensions of the matrices:
- **$\mathbf{B}$** is a **column vector** ($n \times 1$).
- **$\mathbf{C}$** is a **row vector** ($1 \times n$).
- **$D$** is a **scalar** ($1 \times 1$).

## Fundamental Principles

### Core Assumptions
1. **Linearity:** Most SISO tools (Laplace transforms) strictly require the system to be Linear and Time-Invariant (LTI).
2. **[[Decoupling]]:** Assumes that the single input chosen is the *only* thing significantly affecting the chosen output.

### Governing Laws
- **Superposition Principle:** The response to two different inputs is the sum of the individual responses.
- **Commutativity:** In a SISO string of components, the order of the "blocks" doesn't change the final output (unlike MIMO matrix multiplication).

## Theoretical Framework

### [[Frequency Response Function (FRF)]]
SISO systems are unique because they can be characterized by how they respond to different frequencies of "wiggling." 
- If you wiggle a satellite's thruster at 1 Hz, does the body shake at 1 Hz? 
- Is there a delay (Phase Shift)? 
- Does the shaking get bigger ([[Resonance]])? 
By analyzing these "Sine Wave" inputs, we can predict if a satellite will be stable without ever solving a differential equation.



## Physical Interpretation

### The "Single Lever" Analogy
Imagine a machine with only one lever (Input) and one dial (Output).
- You move the lever, and the dial moves.
- You can easily see the direct cause-and-effect.
In a spacecraft, this might be: "I fire the East Thruster (Input) and I observe the Eastward Velocity change (Output)." As long as firing that thruster doesn't make the satellite spin or flip, it can be treated as a SISO system.

## Advantages and Limitations

### Strengths
1.  **Intuitive Visualization:** Bode, Nyquist, and Root Locus plots provide a "picture" of stability that matrix math cannot.
2.  **Robustness Metrics:** Concepts like **Gain Margin** and **Phase Margin** are easily calculated in SISO to determine how much a sensor can fail before the ship crashes.

### Limitations
1.  **Ignores Coupling:** In reality, a satellite's Pitch affects its Yaw ([[Gyroscopic coupling]]). SISO math ignores this, which can lead to "hidden" instabilities.
2.  **Scalability:** You cannot "stack" SISO models to describe a truly complex, multi-axis vehicle.

## Applications

### Spacecraft Components
1.  **Thermostat Control:** One heater (Input) controlling one temperature sensor (Output).
2.  **Simple Pointing:** Using a single reaction wheel to control a single axis of rotation.
3.  **Battery Charging:** Controlling the voltage input from solar panels to maintain a specific battery charge level.

## See Also

- [[MIMO System]]
- [[Transfer Function]]
- [[Bode Plot]]
- [[Root Locus]]

## Recommended Tags:
#control-theory #SISO #Classical-Control #Laplace-Transform #Bode-Plot #Stability #[[Decoupling]]
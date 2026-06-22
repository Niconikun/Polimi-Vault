## Formal Definition

**Pulse Width Modulation (PWM)** is a technique used to encode a continuous (analog) signal into a pulsing digital signal. By varying the **duty cycle**—the ratio of the pulse's "on" time to the total period—the modulator controls the average power delivered to a load. In a PWM system, the frequency remains constant, while the width of each pulse is adjusted proportionally to the input command. In spacecraft systems, PWM is the primary method for driving DC motors in reaction wheels and regulating power from solar arrays to batteries.

## Historical Development

### Key Milestones

- **1920s:** Early engineers use mechanical "choppers" to regulate power in telegraphy and radio.
    
- **1960s:** The invention of the **MOSFET** and **IGBT** allows for the high-speed switching necessary to make electronic PWM practical.
    
- **1970s–Present:** PWM becomes the standard for "Switch-Mode Power Supplies" (SMPS) on spacecraft, allowing for high efficiency and minimal heat generation.
    

### Foundational Contributors

1. **H.S. Black:** While famous for the negative feedback amplifier, his work at Bell Labs on pulse-time modulation laid the groundwork for modern PWM logic.
    

## Mathematical Formulation

### The Duty Cycle ($D$)

The duty cycle is the percentage of time the signal is "high" ($T_{on}$) over one full period ($T$):

$$D = \frac{T_{on}}{T} \times 100\%$$

### Average Voltage ($V_{avg}$)

If the peak voltage is $V_{max}$, the average voltage delivered to the component is:

$$V_{avg} = D \cdot V_{max}$$

### Switching Frequency ($f$)

The frequency is the inverse of the period:

$$f = \frac{1}{T}$$

_In aerospace, this frequency is usually kept very high (above 20 kHz) to avoid audible noise and to reduce the size of inductors/capacitors._

## Fundamental Principles

### Core Assumptions

1. **Low-Pass Filtering:** Assumes that the device being controlled (like a motor) is "slow" enough to ignore the individual pulses and only respond to the average power.
    
2. **Constant Period:** Unlike PWPF, the time between the start of each pulse in PWM is strictly fixed.
    

### Governing Laws

- **Law of Conservation of Energy:** PWM is highly efficient because the switching transistor is ideally either "fully on" (zero voltage drop) or "fully off" (zero current flow), meaning almost no power is wasted as heat.
    

## Theoretical Framework

### PWM vs. PWPF

- **PWM:** Fixed frequency, variable width. Great for electric motors and heaters where the "inertia" (mechanical or thermal) is high.
    
- **PWPF:** Variable frequency, variable width. Better for gas thrusters where you want to minimize the number of valve openings to save fuel.
    

## Physical Interpretation

### The "Light Switch" Analogy

Imagine you want to dim a light bulb, but you only have an on/off switch.

- If you flip the switch on and off once every minute, the light just flickers.
    
- If you flip it on and off **100 times per second**, your eyes cannot see the flickering.
    
- If it’s "on" for 0.001s and "off" for 0.009s, the room looks dark.
    
- If it’s "on" for 0.009s and "off" for 0.001s, the room looks bright.
    

## Advantages and Limitations

### Strengths

1. **High Efficiency:** Minimal power loss compared to "Linear Regulators," which is critical for the limited power budget of a satellite.
    
2. **Digital Compatibility:** Easy to generate using a simple timer on a microcontroller (like an Arduino or a space-grade FPGA).
    

### Limitations

1. **Electromagnetic Interference (EMI):** The rapid "sharp" edges of the square waves create radio noise that can interfere with sensitive spacecraft science instruments.
    
2. **Harmonics:** Can cause vibrations or "ringing" in mechanical systems if the PWM frequency matches a structural [[Resonance]].
    

## Applications

### Spacecraft Systems

1. **Reaction Wheel Motors:** Controlling the torque by adjusting the PWM duty cycle of the motor driver.
    
2. **Heater Control:** Maintaining a precise temperature by "pulsing" the power to thermal blankets.
    
3. **Solar Charge Controllers:** Regulating the flow of energy from the panels to the battery.
    

---

## See Also

- [[Pulse-Width-Pulse-Frequency]]
    
- [[Duty Cycle]]
    
- [[MOSFET]]
    
- [[Reaction Wheels]]
    

## Recommended Tags:

#electronics #PWM #power-systems #GNC #motors #aerospace-engineering #efficiency
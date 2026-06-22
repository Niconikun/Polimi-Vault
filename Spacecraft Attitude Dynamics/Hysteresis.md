## Formal Definition

**Hysteresis** is a property of a system where the current state is dependent not only on its current input but also on its past history. This "lag" or "memory" creates a path-dependent loop where the output follows a different trajectory when the input is increasing versus when it is decreasing. In control systems, hysteresis is intentionally added to **Bang-Bang controllers** to create a "[[Deadband]]" that prevents high-frequency switching. In physics, it describes how materials (like magnetic cores or structural dampeners) dissipate energy.



## Historical Development

### Key Milestones
- **1881:** **Sir James Alfred Ewing** coins the term *hysteresis* (from the Greek word for "lagging behind") to describe the magnetic properties of iron.
- **1930s:** Control engineers begin implementing mathematical hysteresis in relay-based systems to stabilize industrial thermostats.
- **1960s:** Passive **Magnetic Hysteresis Dampening** is used on early satellites (like the Transit series) to remove rotational energy and stabilize the spacecraft relative to the Earth's magnetic field.

### Foundational Contributors
1. **Sir James Alfred Ewing:** The first to systematically measure and name the phenomenon in ferromagnetic materials.
2. **Otto Schmitt:** Utilized the principle to create the [[Schmitt Trigger]], a circuit designed specifically to provide electronic hysteresis.

## Mathematical Formulation

### The Relay with Hysteresis
In a control context, the output $u$ remains at its current state until the input $x$ crosses a specific threshold "ahead" of it:

- If $u = u_{off}$, it stays off until $x > x_{high}$.
- If $u = u_{on}$, it stays on until $x < x_{low}$.

The width of the hysteresis is defined as:
$$h = x_{high} - x_{low}$$

### Magnetic Energy Loss
The area inside a physical hysteresis loop represents the **Energy Dissipation** per cycle. In magnetic materials, this is given by:
$$W = \oint H \cdot dB$$
*Where $H$ is the magnetic field strength and $B$ is the magnetic flux density.*



## Fundamental Principles

### Core Assumptions
1. **Memory:** The system "remembers" its previous state.
2. **Bistability:** In control, the system is usually switching between two stable states.

### Governing Laws
- **The Preisach Model:** A complex mathematical framework used to model systems with "non-local" memory, often used in advanced aerospace materials and sensors.

## Theoretical Framework

### Control Hysteresis ([[Deadband]])
Without hysteresis, if a sensor signal oscillates right at the switching threshold, the actuator would flip on and off millions of times per second (chattering). Hysteresis ensures that once an actuator turns on, the input must change by a significant amount (the [[Deadband]]) before it is allowed to turn off again.

## Physical Interpretation

### The "Soggy Floorboard" Analogy
Imagine walking on a floorboard that is slightly warped.
- You step on it, and it stays flat (Input increases, state changes).
- You step off, but the board **stays down** for a second before finally popping back up.
The board didn't pop up the instant you lifted your foot; it required the "pressure" (input) to reach a much lower level before it changed its state back to the original position.

## Advantages and Limitations

### Strengths
1.  **System Stability:** Prevents "chattering" and mechanical wear in thruster valves and relays.
2.  **Passive Dampening:** Magnetic hysteresis rods can stabilize a satellite's attitude using zero power by turning [[rotational kinetic energy]] into heat.

### Limitations
1.  **Phase Lag:** Hysteresis inherently causes a delay in response, which can reduce the precision of high-speed control loops.
2.  **Accuracy Loss:** In sensors (like pressure transducers), hysteresis is an unwanted error where the reading depends on whether the pressure was rising or falling.

## Applications

### Aerospace Engineering
1.  **Magnetic Torquers:** The iron cores inside magnetorquers exhibit hysteresis, which must be accounted for in the ADCS software.
2.  **Thermostats:** Managing the temperature of sensitive satellite instruments (Heaters on at $18^\circ\text{C}$, off at $22^\circ\text{C}$).
3.  **Passive Stabilization:** Using "Hysteresis Rods" on CubeSats to dampen out post-deployment tumbling.

## See Also

- [[Schmitt Trigger]]
- [[Bang-Bang Control]]
- [[Limit Cycle]]
- [[Magnetic Torquers]]

## Recommended Tags:
#physics #control-theory #hysteresis #magnetics #nonlinear-dynamics #GNC #materials-science
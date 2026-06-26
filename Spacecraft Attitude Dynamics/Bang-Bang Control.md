## Formal Definition

**Bang-Bang Control** is a non-linear feedback control strategy that switches abruptly between two extreme states (e.g., full "on" and full "off"). Unlike a PID controller that provides a smooth, proportional command, a bang-bang controller applies the maximum possible control effort until the state reaches a specific threshold. In spacecraft applications, this is the standard method for **Reaction Control Systems (RCS)** using chemical thrusters, which are binary in nature. To prevent high-frequency switching (chattering), a **[[Deadband]]** or **[[Schmitt Trigger]]** logic is typically incorporated.



## Historical Development

### Key Milestones
- **1950s:** **Lev Pontryagin** develops the "Maximum Principle," mathematically proving that for many time-optimal problems, the best solution is to use maximum available thrust (Bang-Bang).
- **1960s:** The **Apollo Lunar Module** uses bang-bang thruster logic for attitude hold and descent, as proportional throttle for small RCS thrusters was mechanically impossible.
- **Present:** CubeSats frequently use bang-bang control for magnetic torquers and cold-gas thrusters due to the simplicity of the hardware interface.

### Foundational Contributors
1. **Lev Pontryagin:** The Soviet mathematician whose "Minimum Principle" defines the optimality of switching control.
2. **Irmgard Flügge-Lotz:** A pioneer in automatic control who wrote the foundational texts on discontinuous (on-off) control systems.

## Mathematical Formulation

### The Switching Function
The control input $u(t)$ is determined by the sign of the error $e(t)$:
$$u(t) = \begin{cases} U_{max} & \text{if } e(t) > \text{threshold} \\ -U_{max} & \text{if } e(t) < -\text{threshold} \end{cases}$$

### Time-Optimal Control
For a double-integrator system (like a satellite's rotation $\ddot{\theta} = \tau/I$), the time-optimal path to move from point A to point B is to:
1. Fire at $+U_{max}$ for the first half of the move (Acceleration).
2. Switch to $-U_{max}$ for the second half (Deceleration/Braking).



## Fundamental Principles

### Core Assumptions
1. **Binary Actuators:** Assumes the hardware cannot be throttled (e.g., a solenoid valve).
2. **Acceptable Limit Cycles:** Assumes the mission can tolerate small, constant oscillations (the satellite "wiggles" slightly within its [[Deadband]]).

### Governing Laws
- **Pontryagin's Maximum Principle:** States that to minimize time, the control must stay at its boundaries ($U_{min}$ or $U_{max}$).

## Theoretical Framework

### The [[Deadband]] and [[Hysteresis]]
To avoid "Chattering" (the thruster firing thousands of times per second), engineers implement a **[[Deadband]]**.
- **The Coast Phase:** When the satellite is within $\pm 0.1^\circ$ of the target, the thrusters do nothing.
- **The Correction:** Once it drifts out of that window, a "Bang" of thrust pushes it back toward the center.

## Physical Interpretation

### The "Thermostat" Analogy
Your home AC is a bang-bang controller. It doesn't run "at 10%" to keep the room cool. 
- It waits until the room hits $74^\circ\text{F}$ (Threshold).
- It turns on at **100% capacity** (The Bang).
- It turns off once the room hits $70^\circ\text{F}$ (The [[Hysteresis]] limit).
The [[Temperature]] "oscillates" between those two numbers; this is the **[[Limit Cycle]]**.

## Advantages and Limitations

### Strengths
1.  **Simplicity:** Extremely easy to implement in flight software.
2.  **Efficiency (Time):** It is the fastest way to move a system from one state to another.
3.  **Hardware Compatible:** The only way to operate non-throttleable thrusters.

### Limitations
1.  **Fuel Consumption:** Constant switching can lead to "Limit Cycles" that waste propellant if the [[Deadband]] is too narrow.
2.  **Mechanical Wear:** Rapid on-off cycles can reduce the lifespan of valves and relays.
3.  **Excitation of Flexible Modes:** The "sharp" shock of a bang-bang command can cause solar panels to wobble.

## Applications

### Spacecraft GNC
1.  **RCS [[Attitude Control]]:** Maintaining pointing for the ISS or the Orion capsule.
2.  **Station Keeping:** Small "drifts" followed by "burns" to stay in an orbital slot.
3.  **Thermal Control:** Turning heaters on and off to stay within survival temperatures.

## See Also

- [[Schmitt Trigger]]
- [[Hysteresis]]
- [[Deadband]]
- [[Limit Cycle]]

## Recommended Tags:
#control-theory #bang-bang-control #nonlinear-control #RCS #thrusters #optimization #GNC
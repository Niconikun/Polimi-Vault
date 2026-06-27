---
title: Attitude Determination and Control System (ADCS)
tags:
  - spacecraft systems
  - control systems
  - guidance navigation control
  - orbital mechanics
---

# Attitude Determination and Control System (ADCS)

## Formal Definition

The **Attitude Determination and Control System (ADCS)** is the integrated subsystem of a spacecraft responsible for sensing [[Attitude|spacecraft orientation]] (attitude determination) and commanding attitude corrections via actuators (attitude control). The ADCS forms the complete feedback loop: sensors measure attitude → processor computes error and control law → actuators (reaction wheels, thrusters, CMGs) apply corrective torques. The ADCS is essential for all spacecraft missions, from simple spin-stabilized satellites to agile scientific observatories. It encompasses hardware (sensors, actuators, electronics) and software (algorithms, flight code, state estimation).

## Historical Development

### Key Milestones
- **1957–1960s:** Early passive systems (spin, gravity gradient)
- **1960–1970:** First active three-axis systems (Apollo CSM, Skylab)
- **1970–1980:** [[Attitude Determination|Sun/star sensors]]; digital computers enable feedback
- **1980–1990:** [[Kalman Filter|Kalman filtering]] for state estimation; momentum-biased systems
- **1990–2000:** Autonomous attitude determination; reaction wheel arrays
- **2000–Present:** Agile spacecraft; miniaturized ADCS for CubeSats; fault-tolerant designs

### Foundational Contributors
1. **Rodney Rodríguez-Díaz (1940s–present):** Early attitude control concepts
2. **Charles Wertz (1945–present):** ADCS engineering standard references
3. **Margaret H. Hamilton (1936–present):** Onboard software; Apollo guidance
4. **David G. Hull (1940s–present):** Optimal attitude control

## ADCS Architecture

### Functional Block Diagram

```
Sensors → Attitude Determination → Control Law → Actuators
   ↓              (State Estimation)        ↓
[Measurement Update]  ←———— Feedback Loop ————← [Attitude Error]
```

**Data flow:**
1. Sensors measure attitude (sun, stars, earth, rates)
2. Processor runs [[Attitude Determination|attitude determination]] algorithm (e.g., [[Kalman Filter|Kalman filter]])
3. Outputs estimated attitude quaternion
4. Control law computes required torque
5. Actuator commands issued
6. Spacecraft reorients; cycle repeats

### Hierarchy

```
Spacecraft
├── ADCS Subsystem
│   ├── Sensors
│   │   ├── Sun Sensor
│   │   ├── Star Tracker
│   │   ├── Earth Sensor
│   │   ├── Gyroscope (IMU)
│   │   └── Magnetometer
│   ├── Flight Computer
│   │   ├── Processor
│   │   ├── Memory (ROM, RAM)
│   │   ├── Power Supply
│   │   └── Redundant Units
│   └── Actuators
│       ├── Reaction Wheels
│       ├── Control Moment Gyroscopes
│       ├── Magnetic Torquers
│       └── Thrusters
├── Power Subsystem
├── Thermal Control
├── Communications
└── Payload
```

## Sensors (Attitude Determination)

### Sun Sensor

**Principle:** Measures direction to sun from spacecraft.

**Output:** Two-axis angle (pitch, yaw relative to sun).

**Accuracy:** ±0.5–2°.

**Advantages:** Simple, low power, robust.

**Disadvantages:** Single vector (sun direction); ambiguous about roll.

**Type:** Analog (photodiode), digital (CCD array).

### Star Tracker

**Principle:** Optical sensor identifying constellations; determines attitude quaternion from star positions.

**Output:** Quaternion; attitude directly.

**Accuracy:** ±0.01–0.001° (arc-minutes to arc-seconds).

**Advantages:** Highly accurate; autonomous; no external references needed.

**Disadvantages:** High power; can be blinded by sun/moon; cold starts slow.

**Algorithm:** Image pattern recognition; catalog matching via [[Kalman Filter|Bayesian estimation]].

### Earth Sensor

**Principle:** IR sensor detects Earth's horizon; computes roll/pitch (nadir direction).

**Output:** Two-axis angle from nadir.

**Accuracy:** ±0.1–1°.

**Advantages:** Always available in LEO; low power.

**Disadvantages:** Degraded performance near poles; thermal IR ambiguous.

### Inertial Measurement Unit (IMU)

**Contains:**
- Gyroscopes: Measure angular velocity $\boldsymbol{\omega}$
- Accelerometers: Measure linear acceleration (rarely used for attitude in orbit)

**Gyroscope accuracy:** ±0.01–1°/hour drift rate.

**Advantages:** Continuous measurement; high bandwidth.

**Disadvantages:** Drift accumulates over time; requires correction from attitude sensors.

**Integration:** Fuses gyro rate with sensor measurements via [[Kalman Filter|Kalman filter]].

### Magnetometer

**Principle:** Senses local magnetic field direction; matches against [[Magnetic Field|Earth magnetic field]] model.

**Output:** Coarse attitude vector.

**Accuracy:** ±5–10° (low precision).

**Advantages:** Simple; low power; always available in LEO.

**Disadvantages:** Magnetic field gradients, spacecraft magnetic dipole contamination.

### Horizon Sensors

**Principle:** IR radiometers detect Earth's thermal emission limb.

**Measurement:** Horizon crossing times → spacecraft pitch and roll.

**Accuracy:** ±0.5–1°.

**Use:** Often paired with sun sensors for 3-axis attitude.

## Actuators (Attitude Control)

### Reaction Wheels

**Principle:** Spinning wheel exchanges momentum with spacecraft via bearings.

**Momentum storage:**
$$
h_w = I_w \omega_w
$$

**Torque produced:**
$$
\tau = \frac{dh_w}{dt} = I_w \alpha_w
$$

**Typical specs:**
- Momentum: 50–500 kg·m²/s
- Torque: 0.1–10 N·m
- Power: 10–100 W (depends on speed)

**Advantages:** High precision; continuous control.

**Disadvantages:** 
- Saturation (wheels spin up to maximum)
- Requires momentum dumping (via thrusters/magnetic torquers)
- Bearing friction; vibration coupling

**Momentum dumping:** Offload stored momentum when saturation approached.

### Control Moment Gyroscope (CMG)

**Principle:** Large momentum wheel gimbaled to change angular momentum direction.

**Torque generation:**
$$
\boldsymbol{\tau} = \mathbf{r} \times \mathbf{h}
$$

Where $\mathbf{r}$ is gimbal position; $\mathbf{h}$ is gyro momentum (fixed magnitude, rotating direction).

**Efficiency:** Small gimbal angle produces large torque (mechanical advantage).

**Typical specs:**
- Momentum: 1000–5000 kg·m²/s per CMG
- Torque authority: 100–1000 N·m
- Power: 100–500 W

**Advantages:** High torque per power; compact.

**Disadvantages:** 
- Gimbal singularity (loss of control in certain configurations)
- Complex control law
- Saturation requires desaturation maneuvers

**Applications:** ISS (4 CMGs); large agile satellites.

### Magnetic Torquers

**Principle:** Electromagnet dipole interacts with Earth's magnetic field.

$$
\boldsymbol{\tau} = \mathbf{m} \times \mathbf{B}
$$

**Torque magnitude:**
$$
|\tau| = |\mathbf{m}| |\mathbf{B}| \sin(\theta)
$$

Where $\theta$ = angle between dipole and field.

**Typical specs:**
- Dipole moment: 100–10,000 A·m²
- Torque: 0.001–0.1 N·m
- Power: <5 W

**Advantages:** 
- Low power; simple
- Inherent momentum dumping (no fuel needed)
- Continuously available

**Disadvantages:**
- Weak torque; slow control
- Field varies (~30 μT equator, ~60 μT poles)
- Limited authority; can't control yaw near poles (B field parallel)

**Applications:** CubeSats, nanosatellites; initial momentum dumping for larger spacecraft.

### Thrusters

**Principle:** Small rocket engines produce translation → offset lever arm → torque.

$$
\boldsymbol{\tau} = \mathbf{r} \times \mathbf{F}
$$

**Advantages:**
- High torque
- Momentum dumping very efficient
- Independent of environment

**Disadvantages:**
- Consumables (propellant) limited
- Vibration/jitter
- Thruster misalignment errors

**Control:** Pulsed on/off; proportional control via duty cycle.

## Attitude Determination Algorithms

### TRIAD Algorithm

**Inputs:** Two known vectors (e.g., sun direction, magnetic field) and corresponding attitude measurements.

**Outputs:** Attitude quaternion (unique solution if vectors not parallel).

**Procedure:**
1. Construct orthonormal frame from measured vectors
2. Rotate to reference frame
3. Extract quaternion from rotation matrix

**Advantage:** Deterministic; fast (no iteration).

**Disadvantage:** Requires exactly two vectors; doesn't optimally fuse multiple sensors.

### Davenport K-Matrix Method

**Inputs:** Multiple vector pairs (e.g., 3+ sensors).

**Outputs:** Optimal quaternion minimizing measurement residuals.

**Method:** Eigenvalue decomposition of weighted correlation matrix.

**Advantage:** Multi-sensor optimal; robustness.

**Disadvantage:** More computation.

### [[Kalman Filter|Kalman Filter]]

**State:** Attitude quaternion + gyro bias.

**Measurement:** Sun, star, earth sensor outputs; gyro angular rate.

**Prediction:** Integrate gyro rates (gyro model).

**Update:** Correct using sensor measurements (measurement model).

**Advantage:** 
- Optimal estimate under linear Gaussian assumptions
- Natural sensor fusion
- Gyro drift correction

**Extended Kalman Filter (EKF):** Handles nonlinear kinematics; most common for spacecraft.

### Multiplicative Kalman Filter (MKF)

**State:** Error quaternion + gyro bias (not full quaternion).

**Advantage:** Avoids normalization; more stable numerically.

**Application:** Standard in spacecraft flight software.

## Control Algorithms

### Reference Frame

**Most common:** Orbital reference frame (LVLH = Local Vertical, Local Horizontal).

**Axes:**
- X: Nadir (pointing to Earth center)
- Y: Along-track (direction of motion)
- Z: Completes right-hand frame

**Control objective:** Align spacecraft body frame with orbital frame.

### [[Attitude Control|Proportional-Derivative (PD) Control]]

**Error quaternion:**
$$
\mathbf{q}_e = \mathbf{q}_{\text{desired}}^{-1} \otimes \mathbf{q}_{\text{actual}}
$$

**Error vector (first 3 components):**
$$
\mathbf{e} = \mathbf{q}_{e,1:3}
$$

**Control torque:**
$$
\boldsymbol{\tau}_c = -K_p \mathbf{e} - K_d (\boldsymbol{\omega} - \boldsymbol{\omega}_d)
$$

**Tuning:** 
- $K_p$: Proportional gain (stiffness)
- $K_d$: Derivative gain (damping)
- Typically diagonal matrices (per axis)

### Momentum Biasing

**Strategy:** Bias one axis (e.g., z) with constant momentum.

**Advantages:**
- Reduces thruster/CMG usage for disturbances
- Gravity gradient torque can be exploited

**Disadvantage:** Two axes require active control; one axis momentum-biased.

### Slew Maneuvers

**Objective:** Rotate from current attitude to desired attitude.

**Bang-bang control:** Maximum torque until halfway, then reverse (time-optimal).

**Smooth profile:** S-curve acceleration/deceleration (reduces jerk; smoother for payloads).

**Slew rate limit:** Typical 1–10°/second (depends on payload, fuel, attitude accuracy requirement).

## System-Level Considerations

### Redundancy

**Critical functions redundant:**
- Dual reaction wheels on each axis
- Backup star tracker (if primary fails)
- Redundant flight computer

**Graceful degradation:** Loss of one sensor → switching to backup; loss of one wheel → reduced performance but continued operation.

### Autonomous Operations

**Level 1:** Ground commanding; no autonomy.

**Level 2:** Onboard tracking of reference attitude; ground programs maneuvers.

**Level 3:** Autonomous failure detection; automatic recovery (e.g., safe mode).

**Level 4:** Autonomous target acquisition, maneuver planning (advanced missions).

### Power Budget

**ADCS power consumption:**
- Sensors: 10–50 W (star tracker dominant)
- Flight computer: 5–20 W
- Actuators: 50–200 W (reaction wheels) or 1–5 W (mag torquers)

**Total:** 65–270 W typical; scales with mission requirements.

### Thermal Management

**Heat sources:** Reaction wheels (friction), electronics, thrusters.

**Radiators:** Reject waste heat; orientation affects thermal balance.

**Control:** [[Thermal Control|Thermal control]] system coordinates with ADCS.

## Performance Metrics

### Pointing Accuracy

**Defined:** RMS (root mean square) deviation from desired attitude.

**Typical:** 0.01–1° (depends on mission).

**Achieved by:** High-gain feedback; accurate sensors.

### Pointing Stability

**Jitter:** High-frequency oscillations (from reaction wheel imbalance, thruster firings).

**Drift:** Low-frequency wandering (from disturbance torques, sensor bias).

**Spec example:** Hubble: <0.01 arcsecond RMS over 100 seconds.

### Slew Rate

**Maximum angular velocity during maneuvers.**

**Typical:** 1–10°/second.

**Limited by:** Actuator torque, momentum capacity, control authority.

### Settling Time

**Time to reach pointing accuracy after maneuver commanded.**

**Typical:** 100–1000 seconds; depends on control gain and disturbance environment.

## Connection to Other Concepts

1. **Connection to [[Attitude Determination]]:**
   - Provides state estimates to control law

2. **Connection to [[Attitude Control]]:**
   - Executes torque commands

3. **Connection to [[Attitude]]:**
   - Controls this fundamental spacecraft parameter

4. **Connection to [[Orbital Mechanics]]:**
   - Affects reentry, solar panel tracking

5. **Connection to [[Control Theory]]:**
   - Feedback control systems; optimal estimation

## See Also

- [[Attitude Determination]]
- [[Attitude Control]]
- [[Attitude]]
- [[Kalman Filter]]
- [[Reaction Wheel]]
- [[Gyroscope]]
- [[Control Systems]]
- [[Guidance Navigation and Control]]
- [[Spacecraft Dynamics]]
- [[Propulsion Systems]]

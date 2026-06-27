---
title: Non-Hohmann Transfer Maneuvers
tags:
  - orbital mechanics
  - spacecraft dynamics
  - trajectory design
  - mission planning
---

# Non-Hohmann Transfer Maneuvers

## Formal Definition

**Non-Hohmann transfer maneuvers** are spacecraft orbit change techniques that deviate from the classical [[Hohmann Transfer Orbit]], offering alternative trajectory designs for changing [[Orbit|orbital]] altitude, inclination, or other orbital elements. While [[Hohmann Transfer|Hohmann transfers]] are fuel-efficient for coplanar altitude changes, non-Hohmann maneuvers may reduce transfer time at the cost of higher fuel consumption, or achieve orbital changes impossible with standard Hohmann transfers. They are essential for time-critical missions, inclination changes, and complex multi-burn trajectories.

## Historical Development

### Key Milestones
- **1925:** Walter Hohmann publishes optimal coplanar transfer theory
- **1950s–1960s:** Space programs explore rapid transit alternatives to Hohmann
- **1969:** Apollo missions use non-Hohmann trajectories for schedule flexibility
- **1970s–1980s:** Development of low-thrust spiral trajectories via electric propulsion
- **1990s+:** Numerical optimization for complex multi-burn sequences
- **Modern Era:** Autonomous guidance systems handle real-time trajectory optimization

### Foundational Contributors
1. **Walter Hohmann (1880–1945):** Fundamental optimal transfer theory
2. **Konstantin Tsiolkovsky (1857–1935):** Rocket equation and mission planning
3. **Charles Stark Draper:** Guidance and navigation for orbit changes
4. **John Coustenis, David Vallado:** Modern trajectory optimization methods

## Mathematical Formulation

### Classification of Non-Hohmann Transfers

**By Transfer Type:**

1. **Bi-elliptic Transfer:** Three burns with intermediate ellipse
2. **Parabolic Transfer:** Escape trajectory for very large altitude changes
3. **Hyperbolic Transfer:** Excess velocity for rapid transit
4. **Low-Thrust Spiral:** Continuous low acceleration (electric propulsion)
5. **Aerogravity Assist:** Combines aerodynamic effects with gravity assists

### Bi-Elliptic Transfer

**Most fuel-efficient** for large altitude increases (when $r_f/r_i > 11.94$).

**Three Burns:**
1. **First burn** at initial orbit: enter transfer ellipse 1
2. **Intermediate impulse** at apogee of transfer 1: enter transfer ellipse 2
3. **Final burn** at final orbit: circularize

**Transfer Time:**
$$
t_{\text{transfer}} = \frac{T_1}{2} + \frac{T_2}{2}
$$

Where:
- $T_1 = 2\pi\sqrt{a_1^3/\mu}$: period of first transfer ellipse
- $T_2 = 2\pi\sqrt{a_2^3/\mu}$: period of second transfer ellipse

**Fuel Requirement:**
$$
\Delta v_{\text{total}} = \sqrt{\frac{2\mu}{r_i}}\left(\sqrt{\frac{2r_b}{r_i + r_b}} - 1\right) + \sqrt{\frac{2\mu}{r_b}}\left(\sqrt{\frac{2r_f}{r_b + r_f}} - 1\right) + \sqrt{\frac{\mu}{r_f}}\left(1 - \sqrt{\frac{2r_b}{r_f + r_b}}\right)
$$

Where $r_b$ is intermediate burn altitude.

### Hohmann vs. Bi-Elliptic Comparison

**Fuel Efficiency vs. Altitude Change:**

For altitude ratio $\alpha = r_f/r_i$:
- $\alpha < 11.94$: Hohmann transfer more efficient
- $\alpha > 11.94$: Bi-elliptic more efficient
- $\alpha \to \infty$: Bi-elliptic savings approach 10% advantage

**Transition Example:**
- Low Earth Orbit (LEO) to high Earth orbit (HEO): Hohmann slightly better
- LEO to Lunar distance: Bi-elliptic significant advantage
- LEO to escape velocity: Bi-elliptic dominates

### Hyperbolic Transfer

**Excess velocity** at departure:
$$
v_\infty = \sqrt{v_{\text{orbit}}^2 - v_{\text{Hohmann}}^2}
$$

**Transfer time** for distance $d$:
$$
t = \frac{d}{v_{\infty} + v_{\text{avg}}}
$$

**Cost:** Extra fuel for excess velocity; time trade-off linear in excess velocity.

## Low-Thrust Spiral Trajectories

### Electric Propulsion

**Advantage:** High specific impulse ($I_{sp}$ = 1000-3000 s vs. 300 s for chemical)

**Disadvantage:** Low thrust requires extended spiral

**Spiral Dynamics:**
$$
\frac{dr}{d\theta} = \frac{2r \Delta a_t}{a_e^2}
$$

Where $\Delta a_t$ is tangential acceleration, $a_e$ is orbital semi-major axis.

**Transfer Time to Orbit Altitude $r_f$:**
$$
t_{\text{spiral}} \approx \frac{\mu}{g_0 I_{sp} a_t}  \ln\left(\frac{r_f}{r_i}\right)
$$

For continuous low thrust, transfer time much longer than chemical but fuel mass dramatically reduced.

### Optimization

**Trade-offs:**
- **High thrust:** Quick transfer, high fuel consumption
- **Low thrust:** Slow spiral, minimal fuel but extended mission duration
- **Optimal:** Intermediate thrust to balance mission schedule and fuel budget

## Practical Applications

### Time-Critical Missions

**Apollo Missions:** Used non-Hohmann trajectories for schedule constraints
- Rapid Earth-Moon transfer despite fuel penalty
- Trade-off: Extra fuel affordable vs. schedule flexibility critical

**Lunar Descent:** Continuous spiral descent using small thrusters
- Time-efficient approach to surface

### Large Altitude Changes

**Geosynchronous Transfer (GEO):**
- LEO (~200 km) to GEO (~36,000 km)
- Altitude ratio: ~178:1 → Bi-elliptic optimal
- ~15-20% fuel savings over Hohmann

**Lunar and Beyond:**
- Lunar transfers: Bi-elliptic significantly more efficient
- Mars transfers: Multiple flybys and gravity assists

### Inclination Changes

**Inclination Burn at Equator Crossing:**
$$
\Delta v_{\text{inc}} = 2v \sin(\Delta i / 2)
$$

**Combined Inclination + Altitude Change:**
- Perform as combined burn at ascending/descending node
- More fuel-efficient than separate burns
- Complex optimization required

### Fuel-Limited Operations

**Electric Propulsion on Deep Space Probes:**
- Dawn mission: Multiple asteroid visits via low-thrust spiral
- Extended mission duration acceptable for fuel savings
- Enables otherwise impossible mission profiles

### Space Station Reboost

**Atmospheric Drag Compensation:**
- Regular altitude maintenance burns
- Can use Hohmann or non-Hohmann depending on urgency
- Bi-elliptic if multiple station visit windows needed

## Computational Optimization

### Trajectory Optimization Problem

**Minimize:** Fuel consumption (Δv) or transfer time

**Subject to:**
- Initial conditions: $\mathbf{r}_i, \mathbf{v}_i$
- Final conditions: $\mathbf{r}_f, \mathbf{v}_f$
- Thrust constraints: $|a_t| \leq a_{\max}$
- Path constraints: Avoid Earth impact, etc.

**Solution Methods:**
1. **Indirect Methods:** Pontryagin's maximum principle; analytical solution structure
2. **Direct Methods:** Discretize trajectory; [[Optimization Theory|optimize]] numerically
3. **Heuristic:** Genetic algorithms, simulated annealing for complex constraints

### Real-Time Onboard Guidance

Modern spacecraft compute trajectories continuously:
- Sensor measurements update position/velocity
- Guidance system computes optimal remaining trajectory
- Commands executed by propulsion system

## Relationship to Other Concepts

1. **Connection to [[Hohmann Transfer Orbit]]:**
   - Hohmann is special case: fuel-optimal coplanar altitude change
   - Non-Hohmann: generalization for other mission objectives

2. **Connection to [[Orbital Mechanics]]:**
   - Based on two-body dynamics
   - Perturbations (Earth oblateness, atmospheric drag) require real trajectory correction

3. **Connection to [[Spacecraft]] Dynamics:**
   - Propulsion system thrust limitations
   - Mass variation (fuel consumption) affects acceleration
   - Guidance, navigation, and control integration

4. **Connection to [[Rocket Equation|Tsiolkovsky Rocket Equation]]:**
   - Relates Δv required to fuel consumption
   - Mission design trades between fuel and time

## Trade-off Analysis

### Time vs. Fuel Trade-off

**Parameter:** Excess velocity above Hohmann ($v_{excess}$)

**Fuel Cost:**
$$
\Delta m = m_0 \left(1 - e^{-\Delta v / (g I_{sp})}\right)
$$

Extra velocity costs exponentially more fuel.

**Time Savings:**
Linear reduction in transfer time.

**Decision Criterion:** Mission constraints determine acceptable trade-off.

### Examples

| Transfer Type | Time | Δv | Fuel (% of spacecraft) |
|---|---|---|---|
| Hohmann (LEO→GEO) | 5.27 hr | 3.87 km/s | ~45% |
| Bi-elliptic (LEO→GEO) | 5.73 hr | 3.67 km/s | ~43% |
| Fast (non-Hohmann) | 2 hr | 5.5 km/s | ~65% |
| Electric Spiral | 100+ days | 2.0 km/s | ~15% |

## See Also

- [[Hohmann Transfer Orbit]]
- [[Orbital Mechanics]]
- [[Spacecraft Dynamics]]
- [[Trajectory Design]]
- [[Propulsion Systems]]
- [[Tsiolkovsky Rocket Equation]]
- [[Spacecraft Attitude Dynamics]]
- [[Impulsive Maneuver]]
- [[Orbit]]
- [[Phasing Maneuvers]]

# **PID Controller**

#control-theory #pid-controller #feedback-control #attitude-control #ADCS #control-systems #SAD 

## **Formal Definition**

A **Proportional-Integral-Derivative (PID) Controller** is a widely used feedback control algorithm that computes a control signal based on three terms: the current error (Proportional), the accumulated past error (Integral), and the predicted future error (Derivative). It is the most common control algorithm in industrial applications and extensively used in aerospace control systems, including spacecraft [[attitude control]].

---

## **Mathematical Formulation**

### **Continuous-Time PID Controller**

The output $u(t)$ of an ideal continuous-time PID controller is:

$$
u(t) = K_p e(t) + K_i \int_0^t e(\tau) d\tau + K_d \frac{de(t)}{dt}
$$

where:
- $e(t) = r(t) - y(t)$ is the **[[Error Signal]]** (desired reference minus measured output)
- $K_p$ is the **proportional gain**
- $K_i$ is the **integral gain**
- $K_d$ is the **derivative gain**
- $u(t)$ is the **control output** (e.g., torque command)

### **[[Transfer Function]] Representation**

In the Laplace domain:

$$
C(s) = \frac{U(s)}{E(s)} = K_p + \frac{K_i}{s} + K_d s = K_p \left(1 + \frac{1}{T_i s} + T_d s\right)
$$

where:
- $T_i = K_p/K_i$ is the **integral time constant**
- $T_d = K_d/K_p$ is the **derivative time constant**

### **Parallel vs. Standard Forms**

**Parallel Form:**
$$
C(s) = K_p + \frac{K_i}{s} + K_d s
$$

**Standard Form:**
$$
C(s) = K \left(1 + \frac{1}{T_i s} + T_d s\right)
$$

---

## **Component Analysis and Physical Interpretation**

### **1. Proportional Term ($K_p e(t)$)**
- **Action:** Responds to the current error magnitude
- **Effect:** 
  - Reduces [[Rise Time]] and [[Steady-State Error]]
  - Can cause [[Overshoot]] and oscillations if too large
  - Never eliminates [[Steady-State Error]] completely
- **Physical Analogy:** "Spring" action - stronger spring gives faster response but more oscillations

### **2. Integral Term ($K_i \int e(t) dt$)**
- **Action:** Accumulates past errors over time
- **Effect:**
  - Eliminates [[Steady-State Error]] (offset)
  - Increases [[Settling Time]]
  - Can cause [[Overshoot]] and integral windup
  - Introduces phase lag
- **Physical Analogy:** "Accumulator" - sums up all past mistakes to ensure eventual correction

### **3. Derivative Term ($K_d \frac{de}{dt}$)**
- **Action:** Predicts future error based on current rate of change
- **Effect:**
  - Reduces [[Overshoot]] and oscillations
  - Improves stability margin
  - Increases [[Damping]]
  - Amplifies high-frequency noise
- **Physical Analogy:** "Dashpot" or damper - predicts where error is heading and applies braking

---

## **Practical Implementations and Variations**

### **1. Derivative Filtering**
Pure derivative action amplifies noise, so practical implementations use a filtered derivative:

$$
C(s) = K_p + \frac{K_i}{s} + \frac{K_d s}{\tau_f s + 1}
$$

where $\tau_f$ is the **derivative filter time constant**, typically $\tau_f = T_d/N$ with $N$ between 5 and 20.

### **2. Anti-Windup Mechanisms**
**Integral windup** occurs when the actuator saturates but the integrator continues accumulating error. Solutions include:

**Clamping:**
```c
if (u_saturated && error*sign(u) > 0)
    integral = integral_previous;
```

**Back-calculation:**
$$
\frac{dI}{dt} = K_i e - K_{aw}(u - u_{sat})
$$

### **3. Discrete-Time Implementation**

For digital implementation with sampling period $T_s$:

**Position Form:**
$$
u[k] = K_p e[k] + K_i T_s \sum_{j=0}^{k} e[j] + K_d \frac{e[k] - e[k-1]}{T_s}
$$

**Velocity Form (Incremental):**
$$
\Delta u[k] = K_p (e[k] - e[k-1]) + K_i T_s e[k] + \frac{K_d}{T_s} (e[k] - 2e[k-1] + e[k-2])
$$
Better for bumpless transfer and anti-windup.

---

## **Tuning Methods**

### **1. Manual Tuning (Trial and Error)**
1. Set $K_i = 0$, $K_d = 0$
2. Increase $K_p$ until sustained oscillations occur ($K_{pu}$)
3. Reduce $K_p$ to 0.5$K_{pu}$
4. Add integral term for zero [[Steady-State Error]]
5. Add derivative term to damp oscillations

### **2. Ziegler-Nichols Tuning**
Based on step response or ultimate sensitivity:

**Ultimate Sensitivity Method:**
1. Find $K_{pu}$ (gain at stability boundary) and $T_u$ (oscillation period)
2. Apply Ziegler-Nichols rules:

| Controller | $K_p$ | $T_i$ | $T_d$ |
|------------|-------|-------|-------|
| P-only     | 0.5$K_{pu}$ | - | - |
| PI         | 0.45$K_{pu}$ | $T_u$/1.2 | - |
| PID        | 0.6$K_{pu}$ | $T_u$/2 | $T_u$/8 |

### **3. Model-Based Tuning**
For plant $G(s)$, design PID parameters using:
- **[[Pole placement]]**
- **[[Frequency Response Function (FRF)]] methods** (gain/phase margin specifications)
- **Internal Model Control (IMC) tuning**
- **Optimal control criteria** (ITAE, ISE)

### **4. Auto-Tuning**
- Relay feedback auto-tuning
- Pattern recognition methods
- Adaptive tuning algorithms

---

## **Relevance in Attitude Determination and Control (ADCS)**

### **1. Single-Axis [[Attitude Control]]**
For a rigid spacecraft with single-axis dynamics $I\ddot{\theta} = \tau$, a [[PD controller]] is often sufficient:

**[[PD Controller]]:**
$$
\tau = -K_p(\theta - \theta_d) - K_d\dot{\theta}
$$

The closed-loop system becomes:
$$
I\ddot{\theta} + K_d\dot{\theta} + K_p\theta = K_p\theta_d
$$

with [[Natural Frequency]] $\omega_n = \sqrt{K_p/I}$ and [[Damping]] $\zeta = K_d/(2\sqrt{IK_p})$.

### **2. Integral Action for Disturbance Rejection**
For constant [[Disturbance Torques]] $\tau_d$, integral action is necessary:
$$
\tau = -K_p\theta - K_d\dot{\theta} - K_i\int \theta dt
$$

The integrator builds up to counteract $\tau_d$, ensuring zero [[Steady-State Error]].

### **3. [[Quaternion]]-Based [[Attitude Control]]**
For 3-axis [[attitude control]] using quaternions:
$$
\boldsymbol{\tau} = -K_p\mathbf{q}_v - K_d\boldsymbol{\omega} - K_i\int \mathbf{q}_v dt
$$
where $\mathbf{q}_v$ is the vector part of the error [[Quaternion]].

### **4. Reaction Wheel Speed Control**
For reaction wheel speed regulation:
$$
V = K_p(\omega_{cmd} - \omega) + K_i\int (\omega_{cmd} - \omega)dt
$$
where $V$ is the motor voltage command.

### **5. Limitations in Spacecraft Applications**

**Nonlinear Effects:**
- Large-angle maneuvers (non-commutativity)
- [[Actuator saturation]] (wheel speed limits, [[thruster]] on/off)
- Time-varying inertia
- Cross-axis coupling

**Solutions:**
- **Gain scheduling**: Different PID parameters for different operating regimes
- **Anti-windup**: Critical for reaction wheel and [[thruster]] control
- **Cascade control**: Inner rate loop, outer attitude loop

---

## **PID Stability Analysis**

### **Routh-Hurwitz for PID Systems**
For a system $G(s)$ controlled by PID:

**Closed-loop [[characteristic equation]]:**
$$
1 + \left(K_p + \frac{K_i}{s} + K_d s\right)G(s) = 0
$$

### **Stability Conditions for Double Integrator Plant**
For $G(s) = 1/(Is^2)$ with PID control:

Closed-loop:
$$
Is^3 + K_d s^2 + K_p s + K_i = 0
$$

**Routh array:**
$$
\begin{array}{c|cc}
s^3 & I & K_p \\
s^2 & K_d & K_i \\
s^1 & \frac{K_d K_p - I K_i}{K_d} & 0 \\
s^0 & K_i & 
\end{array}
$$

**Stability conditions:**
1. $K_d > 0$, $K_p > 0$, $K_i > 0$
2. $K_d K_p > I K_i$

---

## **Advanced PID Structures**

### **1. Series (Cascade) PID**
$$
C(s) = K \frac{(1 + T_i s)(1 + T_d s)}{T_i s}
$$
Better noise rejection but different tuning rules.

### **2. PID with Setpoint Weighting**
Separate weights for proportional and derivative terms on setpoint changes:
$$
u(t) = K_p(\beta r(t) - y(t)) + K_i\int e(t)dt + K_d(\gamma \dot{r}(t) - \dot{y}(t))
$$

### **3. Fractional-Order PID (FOPID)**
Generalized with fractional orders:
$$
C(s) = K_p + K_i s^{-\lambda} + K_d s^{\mu}, \quad \lambda, \mu \in \mathbb{R}^+
$$
Provides more tuning flexibility.

---

## **ADCS Implementation Considerations**

### **1. Digital Implementation**
```
// Discrete PID with anti-windup and filtering
void PID_Update(float error, float dt) {
    // Proportional
    P = Kp * error;
    
    // Integral with anti-windup
    I_prev = I;
    I += Ki * error * dt;
    
    // Derivative with filtering
    float error_derivative = (error - error_prev) / dt;
    D = Kd * error_derivative;
    D_filtered = (1 - alpha) * D_filtered + alpha * D;
    
    // Output saturation and anti-windup
    u = P + I + D_filtered;
    
    if (u > u_max) {
        u = u_max;
        I = I_prev;  // Clamp integrator
    } else if (u < u_min) {
        u = u_min;
        I = I_prev;  // Clamp integrator
    }
    
    error_prev = error;
}
```

### **2. Multi-Loop Architecture**
Common in spacecraft [[attitude control]]:

**Inner-Outer Loop (Cascade):**
1. **Outer loop**: Attitude error → desired angular rate
2. **Inner loop**: Rate error → torque command

**Advantages:**
- Better disturbance rejection
- Easier tuning
- Natural handling of actuator dynamics

### **3. Adaptive PID for Spacecraft**
- **Self-tuning**: Adjust parameters based on identified model
- **Gain scheduling**: Different parameters for different mission phases
- **Fuzzy PID**: Rule-based adjustment of PID parameters

---

## **Comparison with Modern Control Methods**

### **PID Advantages:**
1. **Simplicity**: Easy to understand and implement
2. **Robustness**: Works well for many systems
3. **Wide applicability**: Proven in thousands of applications
4. **Low computational cost**

### **PID Limitations:**
1. **Performance limitations**: Suboptimal for MIMO systems
2. **Tuning difficulties**: Manual tuning can be time-consuming
3. **Limited for nonlinear systems**: May require gain scheduling

### **When to Use PID in ADCS:**
- Single-axis or decoupled control
- Small-angle maneuvers
- Systems with well-separated time scales
- When computational resources are limited
- As inner loop in cascade control architecture

---

## **Historical Context**
The PID controller has evolved over a century:
- 1910s: Elmer Sperry's ship autopilot (proportional control)
- 1922: Nicolas Minorsky's theoretical analysis of PID
- 1930s: Pneumatic PID controllers in process industries
- 1942: Ziegler-Nichols tuning rules
- 1950s: Electronic PID controllers
- 1980s: Digital PID with auto-tuning
- 2000s: Adaptive and intelligent PID methods

---

## **See Also**
- **[[Proportional Control]]** - P-only controller
- **[[PI Controller]]** - Proportional-Integral controller
- **[[PD Controller]]** - Proportional-Derivative controller
- **[[Lead-Lag Compensator]]** - Frequency-domain equivalent
- **[[State-Space Control]]** - Modern control alternative
- **[[Attitude Control Laws]]** - PID applications in spacecraft control
- **[[Anti-Windup Techniques]]** - Handling [[actuator saturation]]
- **[[Digital Control Implementation]]** - Discrete-time PID

---

## **References**
1. Åström, K. J., & Hägglund, T. (2006). *Advanced PID Control*. ISA Press.
2. Franklin, G. F., Powell, J. D., & Emami-Naeini, A. (2015). *Feedback Control of Dynamic Systems*. Pearson.
3. Sidi, M. J. (1997). *Spacecraft Dynamics and Control: A Practical Engineering Approach*. Cambridge University Press.
4. O'Reilly, J. (1983). *PID Controllers for Time-Delay Systems*. Springer.
5. Bennett, S. (1993). *Development of the PID Controller*. IEEE Control Systems Magazine.
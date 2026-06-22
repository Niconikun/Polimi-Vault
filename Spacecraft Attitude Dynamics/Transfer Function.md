#control-theory #transfer-function #dynamical-systems #laplace-transform #frequency-domain #attitude-control #ADCS

## **Formal Definition**

A **Transfer Function** is a mathematical representation, in the frequency domain, of the input-output relationship of a **[[Linear Time-Invariant (LTI) System]] (LTI)** system. For a continuous-time LTI system with a single input and single output (SISO), the transfer function $G(s)$ is defined as:

$$
G(s) = \frac{Y(s)}{U(s)} = \frac{\mathcal{L}\{y(t)\}}{\mathcal{L}\{u(t)\}}
$$

where:
- $s = \sigma + j\omega$ is the complex **Laplace variable**
- $Y(s)$ is the [[Laplace Transform]] of the output signal $y(t)$
- $U(s)$ is the [[Laplace Transform]] of the input signal $u(t)$
- $\mathcal{L}\{\cdot\}$ denotes the [[Laplace Transform]]
- All initial conditions are assumed to be **zero** (a critical assumption)

For multi-input multi-output (MIMO) systems, the transfer function becomes a **matrix** of SISO transfer functions, relating each input to each output.

---

## **Mathematical Foundation**

### **From Differential Equations to Transfer Functions**
Consider an nth-order linear differential equation describing a system:
$$
a_n \frac{d^n y(t)}{dt^n} + a_{n-1} \frac{d^{n-1} y(t)}{dt^{n-1}} + \cdots + a_1 \frac{dy(t)}{dt} + a_0 y(t) = b_m \frac{d^m u(t)}{dt^m} + \cdots + b_1 \frac{du(t)}{dt} + b_0 u(t)
$$

Applying the [[Laplace Transform]] with zero initial conditions (using the property $\mathcal{L}\left\{\frac{d^n f}{dt^n}\right\} = s^n F(s)$):
$$
(a_n s^n + a_{n-1} s^{n-1} + \cdots + a_1 s + a_0) Y(s) = (b_m s^m + \cdots + b_1 s + b_0) U(s)
$$

Thus, the transfer function becomes:
$$
G(s) = \frac{Y(s)}{U(s)} = \frac{b_m s^m + b_{m-1} s^{m-1} + \cdots + b_1 s + b_0}{a_n s^n + a_{n-1} s^{n-1} + \cdots + a_1 s + a_0}
$$

---

### **Poles and Zeros: The Fundamental Characterization**

The transfer function is typically expressed in **factored form**:
$$
G(s) = K \frac{(s - z_1)(s - z_2)\cdots(s - z_m)}{(s - p_1)(s - p_2)\cdots(s - p_n)}
$$

where:
- **Zeros** ($z_i$): Roots of the numerator polynomial → values of $s$ where $G(s) = 0$
- **Poles** ($p_i$): Roots of the denominator polynomial → values of $s$ where $G(s) \to \infty$
- **Gain** ($K$): Overall system gain

The **poles** determine:
1. **System stability** (all poles must have negative real parts for stability)
2. **Transient response characteristics** (oscillation frequency, [[Damping]], [[Setting Time]])
3. **Natural modes** of the system

The **zeros** influence:
1. **[[Overshoot]]** and **undershoot** characteristics
2. **Phase characteristics** and **non-minimum phase behavior**
3. **Transmission blocking** at specific frequencies

---

## **Relevance in Attitude Determination and Control (ADCS)**

### **1. Modeling Attitude Dynamics**
For a rigid spacecraft with single-axis rotational dynamics (e.g., pitch axis), the equation of motion is:
$$
I \ddot{\theta}(t) = \tau(t)
$$
where $I$ is the moment of inertia, $\theta$ is the attitude angle, and $\tau$ is the control torque.

The transfer function from torque to angle is:
$$
G(s) = \frac{\Theta(s)}{T(s)} = \frac{1}{I s^2}
$$
This is a **double integrator**, characteristic of rigid-body rotational dynamics.

### **2. Control System Design**
Transfer functions enable systematic controller design using:

#### **Proportional-Derivative (PD) Attitude Controller**
A PD controller for attitude has transfer function:
$$
C(s) = K_p + K_d s
$$
The **open-loop transfer function** becomes:
$$
L(s) = C(s)G(s) = (K_p + K_d s)\frac{1}{I s^2} = \frac{K_d s + K_p}{I s^2}
$$
The **closed-loop transfer function** (from reference to output) is:
$$
T(s) = \frac{L(s)}{1 + L(s)} = \frac{\frac{K_d}{I} s + \frac{K_p}{I}}{s^2 + \frac{K_d}{I} s + \frac{K_p}{I}}
$$
This is a standard **second-order system** with [[Natural Frequency]] $\omega_n = \sqrt{\frac{K_p}{I}}$ and [[Damping]] ratio $\zeta = \frac{K_d}{2\sqrt{I K_p}}$.

### **3. Frequency Domain Analysis**
Transfer functions enable critical frequency-domain analyses:

#### **Bode Plots**
Magnitude and phase plots vs. frequency reveal:
- **Gain margin** and **phase margin** (stability robustness)
- **Bandwidth** (speed of response)
- **Disturbance rejection** capabilities

#### **[[Nyquist Stability Criterion]]**
Used to determine closed-loop stability by examining the open-loop transfer function's encirclement of the -1 point.

### **4. Flexible Spacecraft Dynamics**
For spacecraft with flexible appendages (solar arrays, antennas), the transfer function includes additional poles and zeros:
$$
G(s) = \frac{1}{I s^2} + \sum_{i=1}^{n} \frac{K_i}{s^2 + 2\zeta_i\omega_i s + \omega_i^2}
$$
where each term represents a **flexible mode** with [[Natural Frequency]] $\omega_i$ and [[Damping]] $\zeta_i$. This leads to complex control challenges like **spillover** and requires careful filtering.

### **5. Sensor and Actuator Dynamics**
Realistic ADCS models include transfer functions for:
- **Actuators**: Reaction wheels ($G_w(s) = \frac{K_w}{\tau_w s + 1}$), thrusters
- **Sensors**: Gyroscopes ($G_g(s) = \frac{K_g}{\tau_g s + 1}$), star trackers
- **Filters**: Anti-aliasing, notch filters for flexible modes

---

## **Key Properties and Operations**

### **Block Diagram Algebra**
Transfer functions enable systematic manipulation of interconnected systems:
- **Series connection**: $G_{total}(s) = G_1(s)G_2(s)$
- **Parallel connection**: $G_{total}(s) = G_1(s) + G_2(s)$
- **Feedback connection**: $G_{closed}(s) = \frac{G(s)}{1 + G(s)H(s)}$

### **Stability Criteria**
For an LTI system:
- **BIBO Stable** if all poles have negative real parts (left-half plane)
- **Marginally Stable** if poles on imaginary axis are simple
- **Unstable** if any pole has positive real part or repeated poles on imaginary axis

### **Time Response Characteristics**
The transfer function directly relates to time-domain response:
- **Step response**: $y(t) = \mathcal{L}^{-1}\left\{\frac{1}{s}G(s)\right\}$
- **Impulse response**: $y(t) = \mathcal{L}^{-1}\{G(s)\}$
- Key parameters: [[Rise Time]], [[Settling Time]], [[Overshoot]], [[Steady-State Error]]

---

## **Limitations and Extensions**

### **Limitations**
1. **LTI Assumption**: Only valid for linear, time-invariant systems
2. **Zero Initial Conditions**: Transfer function analysis assumes zero initial conditions
3. **Single Equilibrium**: Analysis valid around a single operating point
4. **Limited for MIMO**: While possible, MIMO transfer functions become complex

### **Extensions for ADCS Applications**
1. **Describing Functions**: For analyzing nonlinearities (saturation, deadzone)
2. **Linear Parameter-Varying (LPV) Systems**: For systems with slowly varying parameters
3. **State-Space Representations**: More general than transfer functions, especially for MIMO systems

---

## **ADCS-Specific Examples**

### **Reaction Wheel Control Loop**
For a reaction wheel controlling spacecraft attitude:
$$
G_{total}(s) = \frac{K_w}{\tau_w s + 1} \cdot \frac{1}{I s^2} \cdot \frac{K_g}{\tau_g s + 1}
$$
where terms represent wheel dynamics, [[Rigid-Body Dynamics]], and gyro dynamics respectively.

### **[[PID Controller]] for Attitude**
$$
C(s) = K_p + \frac{K_i}{s} + K_d s \cdot \frac{1}{\tau_f s + 1}
$$
Note the derivative term includes a **filter** ($\tau_f$) to limit high-frequency gain.

---

## **See Also**
- **[[Laplace Transform]]** - Mathematical foundation for transfer functions
- **[[State-Space Representation]]** - Alternative system representation
- **[[Bode Plot]]** - Frequency domain analysis tool
- **[[Nyquist Stability Criterion]]** - Stability analysis method
- **[[PID Controller]]** - Common controller structure
- **[[Root Locus]]** - Graphical design technique

---

## **References**
1. Franklin, G. F., Powell, J. D., & Emami-Naeini, A. (2015). *Feedback Control of Dynamic Systems*. Pearson.
2. Ogata, K. (2010). *Modern Control Engineering*. Prentice Hall.
3. Sidi, M. J. (1997). *Spacecraft Dynamics and Control: A Practical Engineering Approach*. Cambridge University Press.
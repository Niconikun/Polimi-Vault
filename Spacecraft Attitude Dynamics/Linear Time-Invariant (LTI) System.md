#control-theory #linear-systems #time-invariant #dynamical-systems #transfer-function #ADCS #system-identification #SAD 

## **Formal Definition**

A **Linear Time-Invariant (LTI) System** is a class of dynamical systems that satisfies two fundamental properties: **linearity** and **time-[[Invariance]]**. These systems are mathematically tractable and form the cornerstone of classical control theory, signal processing, and frequency-domain analysis.

A system is defined as LTI if it obeys the **principle of superposition** (linearity) and its characteristics do not change over time (time-[[Invariance]]).

---

## **Mathematical Characterization**

### **1. Linearity**
A system is **linear** if it satisfies both **additivity** and **homogeneity**:

**Additivity (Superposition):**
If input $x_1(t)$ produces output $y_1(t)$, and input $x_2(t)$ produces output $y_2(t)$, then the input $x_1(t) + x_2(t)$ produces output $y_1(t) + y_2(t)$.

**Homogeneity (Scaling):**
If input $x(t)$ produces output $y(t)$, then for any scalar constant $\alpha$, the input $\alpha x(t)$ produces output $\alpha y(t)$.

Combined as the **Superposition Principle**:
$$
\mathcal{H}\{\alpha_1 x_1(t) + \alpha_2 x_2(t)\} = \alpha_1 \mathcal{H}\{x_1(t)\} + \alpha_2 \mathcal{H}\{x_2(t)\}
$$
where $\mathcal{H}$ represents the system operator.

### **2. Time-[[Invariance]]**
A system is **time-invariant** if a time shift in the input signal causes an identical time shift in the output signal. Formally:

If input $x(t)$ produces output $y(t)$, then for any time shift $\tau$, the input $x(t-\tau)$ produces output $y(t-\tau)$:
$$
\mathcal{H}\{x(t-\tau)\} = y(t-\tau)
$$

The system's parameters, properties, and response characteristics do NOT change with time.

---

## **Mathematical Representation**

### **Convolution Integral Representation**
For continuous-time LTI systems, the input-output relationship is completely characterized by the system's **impulse response** $h(t)$:
$$
y(t) = x(t) * h(t) = \int_{-\infty}^{\infty} x(\tau)h(t-\tau) d\tau = \int_{-\infty}^{\infty} h(\tau)x(t-\tau) d\tau
$$
where $*$ denotes [[convolution]].

The impulse response $h(t)$ is the system's output when the input is a Dirac delta function $\delta(t)$.

### **Linear Constant-Coefficient [[Differential Equations]]**
LTI systems can be described by linear [[Ordinary Differential Equations (ODEs)]] with constant coefficients:
$$
\sum_{k=0}^{n} a_k \frac{d^k y(t)}{dt^k} = \sum_{k=0}^{m} b_k \frac{d^k x(t)}{dt^k}
$$
where $a_k$ and $b_k$ are constant coefficients (not functions of time).

---

## **Frequency Domain Representation**

### **[[Transfer Function]]**
The [[Laplace Transform]] of the impulse response yields the **[[Transfer Function]]**:
$$
H(s) = \mathcal{L}\{h(t)\} = \frac{Y(s)}{X(s)}
$$
For LTI systems, $H(s)$ is a rational function of the complex variable $s$ (for continuous-time).

### **[[Frequency Response Function (FRF)]]**
For stable LTI systems, the [[Frequency Response Function (FRF)]] is obtained by evaluating the [[Transfer Function]] on the imaginary axis:
$$
H(j\omega) = H(s)\big|_{s=j\omega} = |H(j\omega)|e^{j\angle H(j\omega)}
$$
This describes the system's steady-state response to sinusoidal inputs.

---

## **Key Properties of LTI Systems**

### **1. Commutativity**
$$
x(t) * h(t) = h(t) * x(t)
$$

### **2. Associativity**
$$
[x(t) * h_1(t)] * h_2(t) = x(t) * [h_1(t) * h_2(t)]
$$

### **3. Distributivity**
$$
x(t) * [h_1(t) + h_2(t)] = x(t) * h_1(t) + x(t) * h_2(t)
$$

### **4. Causality**
An LTI system is **causal** if and only if:
$$
h(t) = 0 \quad \text{for all } t < 0
$$

### **5. Stability (BIBO)**
An LTI system is **Bounded-Input Bounded-Output (BIBO) stable** if and only if:
$$
\int_{-\infty}^{\infty} |h(t)| dt < \infty
$$
Equivalently, all poles of $H(s)$ must lie in the left-half of the complex plane.

### **6. Invertibility**
An LTI system with impulse response $h(t)$ is invertible if there exists $h_{inv}(t)$ such that:
$$
h(t) * h_{inv}(t) = \delta(t)
$$

---

## **Relevance in Attitude Determination and Control Systems (ADCS)**

### **1. Simplified Modeling and Analysis**
While real spacecraft dynamics often contain nonlinearities ([[actuator saturation]], large-angle maneuvers), many ADCS components and subsystems are designed and analyzed as LTI systems:

- **Sensor Dynamics**: Gyroscopes, accelerometers (within their linear range)
- **Actuator Dynamics**: Reaction wheels, control moment gyros (linearized models)
- **Filter Design**: Kalman filters, complementary filters, notch filters
- **Controller Design**: PID, lead-lag compensators

### **2. Linearization Around Operating Points**
For nonlinear spacecraft dynamics:
$$
I\ddot{\theta} + \omega \times (I\omega) = \tau
$$
we can **linearize** around an [[equilibrium point]] (e.g., [[Nadir]]-pointing attitude with zero [[Angular Velocity]]):

Let $\theta = \theta_0 + \delta\theta$, $\omega = \omega_0 + \delta\omega$, and assume small perturbations. The linearized equations become LTI systems valid near the operating point.

### **3. Frequency Domain Design Techniques**
LTI theory enables powerful frequency-domain design methods for ADCS:

#### **[[Bode Plot]] Design**
- Shape open-loop [[Transfer Function]] for desired stability margins
- Design compensators to meet bandwidth requirements
- Analyze disturbance rejection capabilities

#### **Root Locus Analysis**
- Plot system poles as a function of control gain
- Design for specific transient response characteristics
- Ensure stability across gain variations

#### **[[Nyquist Stability Criterion]]**
- Assess closed-loop stability from open-loop [[Frequency Response Function (FRF)]]
- Determine gain and phase margins
- Handle systems with time delays

### **4. Digital Implementation**
Discrete-time LTI systems (governed by linear constant-coefficient difference equations) are used for digital implementation:
$$
\sum_{k=0}^{n} a_k y[n-k] = \sum_{k=0}^{m} b_k x[n-k]
$$
with Z-transform [[Transfer Function]]:
$$
H(z) = \frac{Y(z)}{X(z)} = \frac{\sum_{k=0}^{m} b_k z^{-k}}{\sum_{k=0}^{n} a_k z^{-k}}
$$

### **5. Limitations in ADCS Applications**
Despite their utility, LTI models have limitations for spacecraft:
- **Large-angle maneuvers**: Dynamics are inherently nonlinear
- **Time-varying inertia**: Fuel consumption, moving appendages
- **[[Actuator saturation]]**: Reaction wheel speed limits, [[thruster]] on/off
- **Parameter uncertainties**: Inaccurate knowledge of inertia, [[Disturbance Torques]]

These limitations necessitate **robust control** and **adaptive control** techniques.

---

## **Special Cases and Extensions**

### **1. Linear Parameter-Varying (LPV) Systems**
Systems where parameters vary with operating condition but dynamics remain linear at each instant:
$$
\dot{x} = A(\theta(t))x + B(\theta(t))u
$$
Used for spacecraft with large parameter variations.

### **2. Quasi-LTI Approximation**
When parameters vary slowly relative to system dynamics, LTI analysis can be applied at "frozen" instants of time.

### **3. Describing Function Method**
Extends frequency-domain analysis to certain nonlinearities by approximating them with equivalent linear gains.

---

## **ADCS Example: Linearized Pitch Axis Control**

Consider a spacecraft's pitch dynamics linearized around [[Nadir]]-pointing:

**Nonlinear equation**: $I_y\ddot{\theta} = \tau$

**Linearized (LTI) equation**: $I_y\delta\ddot{\theta} = \delta\tau$

**[[Transfer Function]]**: $G(s) = \frac{\Theta(s)}{T(s)} = \frac{1}{I_y s^2}$

With PD controller $C(s) = K_p + K_d s$, the closed-loop system:
$$
T_{cl}(s) = \frac{K_d s + K_p}{I_y s^2 + K_d s + K_p}
$$
is a **second-order LTI system** with [[Natural Frequency]] $\omega_n = \sqrt{K_p/I_y}$ and [[Damping]] $\zeta = K_d/(2\sqrt{I_y K_p})$.

---

## **Testing LTI Properties**

### **Linearity Test**
1. Apply inputs $x_1(t)$ and $x_2(t)$, record outputs $y_1(t)$ and $y_2(t)$
2. Apply input $\alpha_1 x_1(t) + \alpha_2 x_2(t)$
3. Check if output equals $\alpha_1 y_1(t) + \alpha_2 y_2(t)$

### **Time-[[Invariance]] Test**
1. Apply input $x(t)$, record output $y(t)$
2. Apply time-shifted input $x(t-\tau)$
3. Check if output equals $y(t-\tau)$

---

## **See Also**
- **[[Transfer Function]]** - Frequency domain representation of LTI systems
- **[[Impulse Response]]** - Time domain characterization of LTI systems
- **[[State-Space Representation]]** - Alternative representation of linear systems
- **[[BIBO Stability]]** - Stability criterion for LTI systems
- **[[Convolution]]** - Mathematical operation for LTI system response
- **[[Linearization]]** - Technique for approximating nonlinear systems as LTI
- **[[PID Controller]]** - Common LTI controller structure

---

## **References**
1. Oppenheim, A. V., Willsky, A. S., & Nawab, S. H. (1996). *Signals and Systems*. Prentice Hall.
2. Franklin, G. F., Powell, J. D., & Emami-Naeini, A. (2015). *Feedback Control of Dynamic Systems*. Pearson.
3. Sidi, M. J. (1997). *Spacecraft Dynamics and Control: A Practical Engineering Approach*. Cambridge University Press.
4. Chen, C. T. (1999). *Linear System Theory and Design*. Oxford University Press.
---
title: Laplace Transform
tags:
  - mathematics
  - control theory
  - signal processing
  - frequency domain
---

# Laplace Transform

## Formal Definition

The **Laplace transform** is an integral transform that converts a time-domain function into a complex frequency-domain representation. It extends the [[Fourier Transform]] to handle exponentially growing signals and provides a powerful method for solving [[Differential Equations]], analyzing [[Control Systems]], and characterizing system stability. The Laplace transform maps causal signals to the complex s-plane, where pole locations determine system behavior. It is fundamental to [[Control Theory]], [[Signal Processing]], and [[Dynamical Systems|system analysis]].

## Historical Development

### Key Milestones
- **1785:** Pierre-Simon Laplace introduces transform in probability theory
- **1822:** Augustin-Jean Fresnel applies to wave phenomena
- **1900s:** Heaviside's operational calculus; practical applications emerge
- **1920s:** Modern formalization of convergence and inversion
- **1950s–1970s:** Computer-era flourishing in control systems and signal processing
- **1980s–Present:** Digital control, robust Laplace-based methods

### Foundational Contributors
1. **Pierre-Simon Laplace (1749–1827):** Introduces transform in probability
2. **Augustin-Jean Fresnel (1788–1827):** Wave equation applications
3. **Oliver Heaviside (1850–1925):** Operational calculus framework
4. **Thomas Bromwich (1875–1929):** Inversion integral theory
5. **Hendrik Bode (1905–1982):** Frequency-domain control analysis

## Mathematical Formulation

### Definition

**Laplace transform of signal** $f(t)$ **:**
$$
F(s) = \mathcal{L}\{f(t)\} = \int_0^{\infty} f(t) e^{-st} \, dt
$$

Where:
- $s = \sigma + i\omega$ is complex frequency (Laplace variable)
- $\sigma$ is damping ratio (real part)
- $\omega = 2\pi f$ is angular frequency (imaginary part)
- Integration from 0 (causal signals)

**Region of Convergence (ROC):**

Transform converges for $\text{Re}(s) > \sigma_c$ (abscissa of absolute convergence).

### Inverse Laplace Transform

**Bromwich integral (contour integration):**
$$
f(t) = \mathcal{L}^{-1}\{F(s)\} = \frac{1}{2\pi i}\int_{\sigma - i\infty}^{\sigma + i\infty} F(s) e^{st} \, ds
$$

**Residue theorem** (for rational functions):
$$
f(t) = \sum_{\text{poles } s_k} \text{Res}(F(s)e^{st}, s_k)
$$

**Tables:** Most practical inversions use standard transform tables rather than contour integration.

### Common Laplace Transforms

| Function $f(t)$ | Transform $F(s)$ | ROC |
|---|---|---|
| $\delta(t)$ (impulse) | $1$ | all $s$ |
| $u(t)$ (step) | $1/s$ | $\text{Re}(s) > 0$ |
| $t$ (ramp) | $1/s^2$ | $\text{Re}(s) > 0$ |
| $e^{at}$ | $1/(s-a)$ | $\text{Re}(s) > a$ |
| $\sin(\omega t)$ | $\omega/(s^2 + \omega^2)$ | $\text{Re}(s) > 0$ |
| $\cos(\omega t)$ | $s/(s^2 + \omega^2)$ | $\text{Re}(s) > 0$ |
| $te^{at}$ | $1/(s-a)^2$ | $\text{Re}(s) > a$ |

## Fundamental Properties

### Linearity

$$
\mathcal{L}\{af(t) + bg(t)\} = aF(s) + bG(s)
$$

### Time Shifting

$$
\mathcal{L}\{f(t - T)u(t-T)\} = e^{-sT}F(s)
$$

Where $u(t)$ is unit step function.

### Frequency Shifting

$$
\mathcal{L}\{e^{at}f(t)\} = F(s - a)
$$

### Differentiation (Time Domain)

$$
\mathcal{L}\left\{\frac{df}{dt}\right\} = sF(s) - f(0^+)
$$

**Generalization:**
$$
\mathcal{L}\left\{\frac{d^n f}{dt^n}\right\} = s^n F(s) - s^{n-1}f(0) - \cdots - f^{(n-1)}(0)
$$

**Application:** Differential equations → algebraic equations in s-domain.

### Integration (Time Domain)

$$
\mathcal{L}\left\{\int_0^t f(\tau) d\tau\right\} = \frac{1}{s}F(s)
$$

### Convolution Theorem

$$
\mathcal{L}\{f(t) * g(t)\} = F(s) \cdot G(s)
$$

**Comparison to Fourier:** Same property; s-domain more general for unstable/exponential signals.

### Final Value Theorem

$$
\lim_{t \to \infty} f(t) = \lim_{s \to 0} sF(s)
$$

Provided limit exists and all poles are in left-half plane or on imaginary axis.

### Initial Value Theorem

$$
f(0^+) = \lim_{s \to \infty} sF(s)
$$

## Connection to Transfer Functions

### Transfer Function Definition

For LTI system with input $u(t)$ and output $y(t)$:

$$
H(s) = \frac{Y(s)}{U(s)} = \frac{\mathcal{L}\{y(t)\}}{\mathcal{L}\{u(t)\}}
$$

**State-space form:**
$$
\dot{\mathbf{x}} = \mathbf{A}\mathbf{x} + \mathbf{B}u$$
$$y = \mathbf{C}\mathbf{x} + \mathbf{D}u$$

**Transfer function:**
$$
H(s) = \mathbf{C}(s\mathbf{I} - \mathbf{A})^{-1}\mathbf{B} + \mathbf{D}
$$

### Pole-Zero Form

$$
H(s) = K\frac{(s - z_1)(s - z_2)\cdots(s - z_m)}{(s - p_1)(s - p_2)\cdots(s - p_n)}
$$

Where:
- Zeros: $z_i$ (output becomes zero)
- Poles: $p_i$ (system response involves terms $e^{p_i t}$)
- Pole locations determine stability and transient response

### Stability Criterion

**System stable iff all poles in left-half plane** ($\text{Re}(p_i) < 0$):

- Pole at $p = -\alpha$ → response term $e^{-\alpha t}$ (decay)
- Pole at $p = 0$ → marginally stable (step response)
- Pole at $p = \alpha > 0$ → unstable (growth)

## Solving Differential Equations

### Linear ODE with Initial Conditions

**Differential equation:**
$$
a_n\frac{d^n y}{dt^n} + \cdots + a_1\frac{dy}{dt} + a_0 y = b_m u(t)
$$

**Initial conditions:** $y(0), \dot{y}(0), \ldots, y^{(n-1)}(0)$

**Solution procedure:**

1. Apply Laplace transform to both sides
2. Use differentiation property to replace derivatives
3. Solve algebraically for $Y(s)$
4. Apply partial fraction decomposition
5. Use inverse Laplace to find $y(t)$

### Example: Second-Order System

**Equation:** $\ddot{y} + 2\zeta\omega_n\dot{y} + \omega_n^2 y = \omega_n^2 u(t)$

Initial conditions: $y(0) = 0, \dot{y}(0) = 0$; input: $u(t) = $ unit step

**Laplace domain:**
$$
s^2Y(s) + 2\zeta\omega_n sY(s) + \omega_n^2 Y(s) = \frac{\omega_n^2}{s}
$$

$$
Y(s) = \frac{\omega_n^2}{s(s^2 + 2\zeta\omega_n s + \omega_n^2)}
$$

**Inverse transform** (underdamped, $\zeta < 1$):
$$
y(t) = 1 - e^{-\zeta\omega_n t}\left[\cos(\omega_d t) + \frac{\zeta}{\sqrt{1-\zeta^2}}\sin(\omega_d t)\right]
$$

Where $\omega_d = \omega_n\sqrt{1-\zeta^2}$.

## Frequency Response and Stability Analysis

### Relationship to Fourier Transform

**Replace $s = i\omega$:**
$$
H(i\omega) = \text{Fourier transform of impulse response}
$$

**Why Laplace more general:**
- Fourier requires absolute integrability
- Laplace valid for exponentially growing signals (unstable)
- s-plane analysis includes growth rates

### Bode Plot Construction

**Logarithmic magnitude plot:**
$$
|H(i\omega)|_{\text{dB}} = 20\log_{10}|H(i\omega)|
$$

**Asymptotic approximation via pole-zero:** Each pole/zero contributes ±20 dB/decade.

**Phase plot:**
$$
\angle H(i\omega) = \arg(H(i\omega))
$$

Each pole contributes -90°; zero contributes +90°.

### Nyquist and Root Locus

**Nyquist criterion:** Feedback system stability determined by encirclement of -1 point in Nyquist plot.

**Root locus:** Locus of closed-loop poles as gain varies; graphical design method.

Both require transfer function (via Laplace); pole locations primary indicator of stability.

## Control Systems Applications

### PID Controller

**Proportional-Integral-Derivative:**
$$
U(s) = K_p E(s) + \frac{K_i}{s}E(s) + K_d s E(s)
$$

Where $E(s) = R(s) - Y(s)$ is error; $R$ is reference.

**Tuning:** Adjust $K_p, K_i, K_d$ to place closed-loop poles for desired response.

### State-Space to Transfer Function

**Realization:** Given $H(s) = \mathbf{C}(s\mathbf{I} - \mathbf{A})^{-1}\mathbf{B} + \mathbf{D}$

Multiple realizations possible; canonical forms (controllable, observable) standard.

**Minimal realization:** Fewest states; no hidden modes (pole-zero cancellations).

## Partial Fraction Decomposition

### Technique for Inversion

**Given:** $F(s) = \frac{\text{Numerator}}{\text{Denominator}}$

**Decompose into simple terms:**
$$
F(s) = \frac{A}{s - p_1} + \frac{B}{s - p_2} + \cdots
$$

**Residue formula** (simple pole at $p_k$):
$$
A_k = \lim_{s \to p_k} (s - p_k)F(s)
$$

**Repeated poles:** Denominator $(s - p_k)^n$ requires $n$ terms.

**Inverse transforms:** Lookup table applied to each term.

### Example

$$
F(s) = \frac{1}{s(s+2)} = \frac{A}{s} + \frac{B}{s+2}
$$

$A = \lim_{s \to 0} sF(s) = 1/2$; $B = \lim_{s \to -2} (s+2)F(s) = -1/2$

$$
f(t) = \frac{1}{2} - \frac{1}{2}e^{-2t}$$

## Advantages over Fourier Transform

1. **Convergence:** Valid for exponentially growing signals; Fourier requires decay
2. **Initial conditions:** Naturally incorporated via differentiation property
3. **Causality:** ROC automatically encodes causality information
4. **Stability:** Pole location immediately indicates stability
5. **Design:** s-plane geometry more intuitive for control design

## Connection to Other Concepts

1. **Connection to [[Fourier Transform]]:**
   - Laplace extends Fourier to complex s-plane
   - Fourier on imaginary axis: $s = i\omega$

2. **Connection to [[Differential Equations]]:**
   - Transforms into algebraic problems
   - Particularly suited to linear ODEs with initial conditions

3. **Connection to [[Transfer Function]]:**
   - Transfer function = Laplace ratio of output/input

4. **Connection to [[Control Systems]]:**
   - Foundation of classical control design
   - Bode, Nyquist, root locus plots

5. **Connection to [[Impulse Response]]:**
   - Impulse response = inverse Laplace of transfer function
   - Determines all system behavior

## See Also

- [[Fourier Transform]]
- [[Transfer Function]]
- [[Impulse Response]]
- [[Control Systems]]
- [[Control Theory]]
- [[Differential Equations]]
- [[Stability Analysis]]
- [[Frequency Response]]
- [[Bode Plot]]
- [[Nyquist Criterion]]

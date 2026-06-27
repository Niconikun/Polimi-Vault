---
title: Impulse Response
tags:
  - control theory
  - signal processing
  - dynamical systems
  - frequency domain
---

# Impulse Response

## Formal Definition

The **impulse response** is the output response of a [[Dynamical Systems|dynamical system]] to a Dirac delta function input. It completely characterizes the behavior of a linear time-invariant (LTI) system and serves as the foundation for understanding system dynamics in both time and frequency domains. The impulse response $h(t)$ (continuous time) or $h[n]$ (discrete time) encodes all information about system poles, stability, and energy response. It is fundamental to [[Control Systems]], [[Signal Processing]], and [[Convolution]].

## Historical Development

### Key Milestones
- **1927:** Heaviside's operational calculus; early impulse concepts
- **1930s:** Green's functions developed; impulse response theory emerges
- **1950s:** Convolution theorem formalized; impulse-driven system analysis
- **1960s–1970s:** Digital signal processing revolution; discrete impulse responses
- **1980s–1990s:** System identification from impulse tests
- **2000s–Present:** Machine learning connections; neural network impulse dynamics

### Foundational Contributors
1. **Oliver Heaviside (1850–1925):** Operational calculus framework
2. **George Green (1793–1841):** Green's functions; impulse solutions
3. **Norbert Wiener (1894–1964):** Convolution and filtering
4. **Richard Hamming (1915–1998):** Digital signal processing methods

## Mathematical Formulation

### Dirac Delta Function

**Definition (informal):**
$$
\delta(t) = \begin{cases} \infty & t = 0 \\ 0 & t \neq 0 \end{cases}
$$

**Property (sifting property):**
$$
\int_{-\infty}^{\infty} \delta(t - t_0) f(t) \, dt = f(t_0)
$$

**Laplace transform:**
$$
\mathcal{L}\{\delta(t)\} = 1
$$

**Fourier transform:**
$$
\mathcal{F}\{\delta(t)\} = 1
$$

### Continuous-Time Impulse Response

**LTI system:**
$$
\dot{\mathbf{x}}(t) = \mathbf{A}\mathbf{x}(t) + \mathbf{B}u(t)
$$
$$
y(t) = \mathbf{C}\mathbf{x}(t) + \mathbf{D}u(t)
$$

**Impulse input:** $u(t) = \delta(t)$, $\mathbf{x}(0) = 0$

**Impulse response:**
$$
h(t) = \mathbf{C}e^{\mathbf{A}t}\mathbf{B} + \mathbf{D}\delta(t)
$$

For $t > 0$ (causal system):
$$
h(t) = \mathbf{C}e^{\mathbf{A}t}\mathbf{B}
$$

### Discrete-Time Impulse Response

**Discrete system:**
$$
\mathbf{x}[n+1] = \mathbf{A}\mathbf{x}[n] + \mathbf{B}u[n]
$$
$$
y[n] = \mathbf{C}\mathbf{x}[n] + \mathbf{D}u[n]
$$

**Unit impulse:** $\delta[n] = \begin{cases} 1 & n = 0 \\ 0 & n \neq 0 \end{cases}$

**Impulse response:**
$$
h[n] = \begin{cases}
\mathbf{D} & n = 0 \\
\mathbf{C}\mathbf{A}^{n-1}\mathbf{B} & n > 0 \\
0 & n < 0
\end{cases}
$$

### Convolution with Impulse Response

**Input-output relationship (continuous):**
$$
y(t) = \int_{-\infty}^{\infty} h(t - \tau) u(\tau) \, d\tau = h(t) * u(t)
$$

**Causal causality** ($h(t) = 0$ for $t < 0$):
$$
y(t) = \int_0^t h(t - \tau) u(\tau) \, d\tau
$$

**Discrete convolution:**
$$
y[n] = \sum_{k=-\infty}^{\infty} h[n-k]u[k] = \sum_{k=0}^n h[n-k]u[k]
$$

**Key principle:** Any input can be reconstructed as superposition of delayed impulses; output is corresponding superposition of delayed impulse responses.

## Transfer Function Relationship

### Laplace Domain

**System with impulse response** $h(t)$ **has transfer function:**
$$
H(s) = \mathcal{L}\{h(t)\} = \mathbf{C}(s\mathbf{I} - \mathbf{A})^{-1}\mathbf{B} + \mathbf{D}
$$

**Inverse transform:**
$$
h(t) = \mathcal{L}^{-1}\{H(s)\}
$$

### Frequency Response

**Frequency response** (replace $s = i\omega$):
$$
H(i\omega) = \mathbf{C}(i\omega \mathbf{I} - \mathbf{A})^{-1}\mathbf{B} + \mathbf{D}
$$

**Fourier transform of impulse response:**
$$
H(i\omega) = \mathcal{F}\{h(t)\}
$$

### Z-Transform Domain

**Discrete transfer function:**
$$
H(z) = \mathbf{C}(z\mathbf{I} - \mathbf{A})^{-1}\mathbf{B} + \mathbf{D}
$$

**Inverse Z-transform:**
$$
h[n] = \mathcal{Z}^{-1}\{H(z)\}
$$

## Stability and Energy

### Stability Criterion

**System stable iff** impulse response is absolutely integrable:
$$
\int_0^\infty |h(t)| \, dt < \infty
$$

**Discrete:** $\sum_{n=0}^\infty |h[n]| < \infty$

**Pole location interpretation:**
- All poles of $H(s)$ in left-half plane $\Rightarrow$ stable
- Pole on imaginary axis → marginal stability
- Pole in right-half plane → unstable

### Energy and Parseval's Theorem

**Energy of impulse response:**
$$
E = \int_0^\infty h^2(t) \, dt = \frac{1}{2\pi}\int_{-\infty}^{\infty} |H(i\omega)|^2 \, d\omega
$$

**Discrete energy:**
$$
E = \sum_{n=0}^\infty h^2[n] = \frac{1}{2\pi}\int_{-\pi}^{\pi} |H(e^{i\omega})|^2 \, d\omega
$$

## Connection to Other Concepts

1. **Connection to [[Convolution]]:**
   - Input-output via impulse response convolution
   - Multiplication in frequency domain becomes convolution in time

2. **Connection to [[Transfer Function]]:**
   - Impulse response is inverse Laplace/Z-transform of transfer function
   - Complete characterization of LTI system

3. **Connection to [[Frequency Response]]:**
   - Fourier/frequency transform of impulse response
   - Magnitude and phase at each frequency

4. **Connection to [[Control Systems]]:**
   - Used in [[Feedback Control]] design and stability analysis
   - Step, ramp, parabolic responses derived from impulse response

5. **Connection to [[Signal Processing]]:**
   - Deconvolution: recovering input from output via impulse response
   - Wiener filtering optimal for known impulse response

## Practical Measurement and Analysis

### Experimental Determination

**Hammer Test (Impact Testing):**

Strike structure with instrumented hammer; measure accelerometer response.

**Procedure:**
1. Apply impulsive force via instrumented hammer
2. Record acceleration response via accelerometers
3. Compute FFT to obtain frequency response
4. Use FRF analyser to extract impulse response

**Advantages:**
- Nondestructive
- Quick identification
- Suitable for in-situ testing

### Computational Methods

**Time-Domain Simulation:**

Given state-space system, apply $u(t) = \delta(t)$ by setting initial conditions:
$$
\mathbf{x}(0) = \mathbf{B}
$$

Integrate system equations:
$$
\dot{\mathbf{x}} = \mathbf{A}\mathbf{x}, \quad y = \mathbf{C}\mathbf{x}
$$

Result: $y(t) = h(t)$

**Pole-Residue Decomposition:**

$$
H(s) = \sum_i \frac{r_i}{s - p_i}
$$

**Impulse response:**
$$
h(t) = \sum_i r_i e^{p_i t}
$$

Time constants $\tau_i = -1/\text{Re}(p_i)$ determine decay rates.

### Impulse Response Testing

**Three-Excitation Sequence:**

1. **Low-frequency impulse:** Reveals rigid-body dynamics
2. **Mid-frequency impulse:** Structure flexibility modes
3. **High-frequency impulse:** Sensor/fixture resonances

## Application Examples

### Mechanical Systems

**Mass-Spring-Damper System:**

$$
m\ddot{x} + c\dot{x} + kx = \delta(t)
$$

**Solution (underdamped, $\zeta < 1$):**
$$
h(t) = \frac{1}{m\omega_d} e^{-\zeta\omega_n t} \sin(\omega_d t)
$$

Where $\omega_d = \omega_n\sqrt{1-\zeta^2}$

**Physical interpretation:**
- Exponential decay with time constant $\tau = 1/(\zeta\omega_n)$
- Oscillation frequency $\omega_d$
- Amplitude proportional to $1/m$ (inertia effect)

### Electrical Circuits

**RC Low-Pass Filter:**

$$
\frac{dy}{dt} + \frac{y}{RC} = \frac{u}{RC}
$$

**Transfer function:** $H(s) = \frac{1}{RCs + 1}$

**Impulse response:**
$$
h(t) = \frac{1}{RC} e^{-t/RC}
$$

Time constant $\tau = RC$.

### Spacecraft Attitude Control

**Single-axis attitude dynamics:**

$$
I\ddot{\theta} + c\dot{\theta} + k\theta = \tau
$$

**Impulse response:** Angular velocity change $\Delta\omega = 1/I$ (angular momentum change)

Useful for analyzing detumbling maneuvers via magnetic or propulsive impulse.

## Digital Signal Processing

### FIR and IIR Filters

**FIR (Finite Impulse Response):**
$$
y[n] = \sum_{k=0}^{N} b_k u[n-k]
$$

Impulse response finite length: $h[n] = 0$ for $n > N$

**IIR (Infinite Impulse Response):**
$$
y[n] = \sum_{k=1}^M a_k y[n-k] + \sum_{k=0}^N b_k u[n-k]
$$

Impulse response infinite: $h[n] \neq 0$ for all $n \geq 0$

### Window Functions

To truncate infinite impulse response to practical length:

**Hamming window:**
$$
w[n] = 0.54 - 0.46\cos\left(\frac{2\pi n}{N-1}\right)
$$

**Design trade-off:** Higher sidelobe suppression vs. wider main lobe

## Advanced Topics

### Minimum Phase Systems

**System is minimum phase iff** all poles and zeros in left-half plane.

**Property:** Impulse response most concentrated in time (least delay).

**Application:** Inverse filtering; unique solution for system inversion.

### Regularization and Noise

**Noisy measurement:** $y_{\text{measured}} = y_{\text{true}} + \text{noise}$

**Deconvolution ill-posed:** Small noise → large errors in inversion.

**Regularization:** Add penalty term to stabilize inversion.

### Time-Delay Effects

**System with time delay $T_d$:**
$$
H(s) = e^{-sT_d} H_0(s)
$$

**Impulse response:**
$$
h(t) = h_0(t - T_d) \, u(t - T_d)
$$

Delay shifts impulse response by $T_d$.

## See Also

- [[Convolution]]
- [[Transfer Function]]
- [[Frequency Response]]
- [[Control Systems]]
- [[Signal Processing]]
- [[Laplace Transform]]
- [[Fourier Transform]]
- [[Stability Analysis]]
- [[Step Response]]
- [[Dirac Function]]

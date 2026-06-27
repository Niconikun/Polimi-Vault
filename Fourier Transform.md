---
title: Fourier Transform
tags:
  - mathematics
  - signal processing
  - frequency domain
  - spectral analysis
---

# Fourier Transform

## Formal Definition

The **Fourier transform** is a mathematical operation that decomposes a function of time (or space) into its constituent frequencies, establishing a bijective mapping between the time domain and frequency domain. It reveals the frequency content of signals and systems, enabling spectral analysis, filtering, and convolution operations. The Fourier transform is fundamental to [[Signal Processing]], [[Control Systems]], [[Differential Equations]], and virtually all areas of engineering and physics.

## Historical Development

### Key Milestones
- **1822:** Joseph Fourier introduces trigonometric series for heat equation
- **1829:** Dirichlet establishes convergence conditions (Dirichlet conditions)
- **1854:** Georg Riemann develops Riemann integral; extends applicability
- **1900s:** Complex analysis perspective (contour integration)
- **1930s:** Generalization to distributions (Dirac delta, etc.)
- **1965:** Cooley-Tukey FFT algorithm; computational revolution
- **1980s–Present:** Wavelets, time-frequency analysis, neural networks

### Foundational Contributors
1. **Joseph Fourier (1768–1830):** Heat equation and trigonometric series
2. **Jean-Baptiste Fourier (1768–1830):** Fourier analysis formalization
3. **Peter Gustav Lejeune Dirichlet (1805–1859):** Convergence theory
4. **James Clerk Maxwell (1831–1879):** Application to [[Maxwell's Equations]]
5. **James W. Cooley & John W. Tukey (1965):** Fast Fourier Transform

## Mathematical Formulation

### Fourier Series (Periodic Functions)

**For periodic function** $f(t)$ with period $T$:

$$
f(t) = \frac{a_0}{2} + \sum_{n=1}^{\infty} \left[a_n \cos\left(\frac{2\pi n t}{T}\right) + b_n \sin\left(\frac{2\pi n t}{T}\right)\right]
$$

**Fourier coefficients:**
$$
a_n = \frac{2}{T}\int_0^T f(t)\cos\left(\frac{2\pi n t}{T}\right) dt
$$
$$
b_n = \frac{2}{T}\int_0^T f(t)\sin\left(\frac{2\pi n t}{T}\right) dt
$$

**Complex exponential form:**
$$
f(t) = \sum_{n=-\infty}^{\infty} c_n e^{i2\pi n t/T}
$$

Where $c_n = \frac{1}{T}\int_0^T f(t)e^{-i2\pi n t/T} dt$

### Continuous-Time Fourier Transform

**Definition (inverse frequency convention):**
$$
F(f) = \int_{-\infty}^{\infty} x(t) e^{-i2\pi f t} \, dt
$$

**Inverse transform:**
$$
x(t) = \int_{-\infty}^{\infty} F(f) e^{i2\pi f t} \, df
$$

**Angular frequency convention** (ω = 2πf):
$$
X(\omega) = \int_{-\infty}^{\infty} x(t) e^{-i\omega t} \, dt
$$

$$
x(t) = \frac{1}{2\pi}\int_{-\infty}^{\infty} X(\omega) e^{i\omega t} \, d\omega
$$

### Discrete-Time Fourier Transform (DTFT)

**For discrete signal** $x[n]$:
$$
X(e^{i\omega}) = \sum_{n=-\infty}^{\infty} x[n] e^{-i\omega n}
$$

**Period:** $2\pi$ (inherent periodicity from sampling)

**Inverse:**
$$
x[n] = \frac{1}{2\pi}\int_0^{2\pi} X(e^{i\omega}) e^{i\omega n} \, d\omega
$$

### Discrete Fourier Transform (DFT)

**For finite sequence** $x[n]$, $n = 0, 1, \ldots, N-1$:
$$
X[k] = \sum_{n=0}^{N-1} x[n] e^{-i2\pi kn/N}
$$

**Inverse:**
$$
x[n] = \frac{1}{N}\sum_{k=0}^{N-1} X[k] e^{i2\pi kn/N}
$$

**Frequency resolution:** $\Delta f = f_s/N$ (sampling frequency / number of points)

## Fundamental Properties

### Linearity

$$
\mathcal{F}\{ax(t) + by(t)\} = aX(f) + bY(f)
$$

### Time Shifting

$$
\mathcal{F}\{x(t - t_0)\} = e^{-i2\pi f t_0} X(f)
$$

Phase shift proportional to delay.

### Frequency Shifting (Modulation)

$$
\mathcal{F}\{e^{i2\pi f_c t} x(t)\} = X(f - f_c)
$$

### Scaling

$$
\mathcal{F}\{x(at)\} = \frac{1}{|a|}X(f/a)
$$

Time compression → frequency expansion (reciprocal relationship).

### Convolution Theorem

**Time-domain convolution:**
$$
y(t) = \int_{-\infty}^{\infty} h(t-\tau)x(\tau) \, d\tau = h(t) * x(t)
$$

**Frequency-domain multiplication:**
$$
Y(f) = H(f) \cdot X(f)
$$

**Computational advantage:** FFT-based convolution faster than direct convolution for large signals.

### Parseval's Theorem (Energy)

**Time-domain energy:**
$$
E = \int_{-\infty}^{\infty} |x(t)|^2 \, dt
$$

**Frequency-domain energy:**
$$
E = \int_{-\infty}^{\infty} |X(f)|^2 \, df
$$

Energy conserved under Fourier transform (unitary operation).

### Differentiation

$$
\mathcal{F}\left\{\frac{dx}{dt}\right\} = i2\pi f \cdot X(f)
$$

**Interpretation:** Differentiation amplifies high frequencies.

### Multiplication (Duality)

$$
\mathcal{F}\{x(t) \cdot y(t)\} = X(f) * Y(f)
$$

Time-domain multiplication → frequency-domain convolution.

## Connection to Other Concepts

1. **Connection to [[Laplace Transform]]:**
   - Laplace more general (convergence); valid for unstable systems
   - Fourier special case: $s = i\omega$ (imaginary axis)
   - Fourier for stable, causal systems

2. **Connection to [[Convolution]]:**
   - Fundamental tool for convolution computation
   - Converts convolution to multiplication

3. **Connection to [[Signal Processing]]:**
   - Basis for filter design, spectral analysis
   - Frequency-domain filtering operations

4. **Connection to [[Control Systems]]:**
   - Frequency response analysis: $G(i\omega) = \mathcal{F}\{g(t)\}$
   - Bode plots, Nyquist diagrams

5. **Connection to [[Differential Equations]]:**
   - Transforms PDEs to algebraic equations (in frequency domain)
   - Enables solution of periodic-coefficient systems

## Spectrum Analysis

### Magnitude and Phase

**Complex spectrum:**
$$
X(f) = |X(f)| e^{i\phi(f)}
$$

**Magnitude spectrum:**
$$
|X(f)| = \sqrt{\text{Re}(X)^2 + \text{Im}(X)^2}
$$

**Phase spectrum:**
$$
\phi(f) = \arctan\left(\frac{\text{Im}(X)}{\text{Re}(X)}\right)
$$

### Real Signals (Hermitian Symmetry)

For real signal $x(t)$:
$$
X(-f) = X^*(f)
$$

Magnitude spectrum is even; phase spectrum is odd.

### Energy Spectral Density

$$
S(f) = |X(f)|^2
$$

Power per unit frequency (for power signals; energy spectral density for energy signals).

## Computational Methods

### Fast Fourier Transform (FFT)

**Cooley-Tukey Algorithm:**

Recursively divides DFT into smaller DFTs; reduces complexity from $O(N^2)$ to $O(N\log N)$.

**Radix-2 FFT:** Most common; requires $N = 2^m$ samples.

**Computational savings:**
- N = 1024: Direct DFT = 1,048,576 ops; FFT = 10,240 ops (~100× faster)
- N = 1,048,576 (1M): ~100,000× faster

### Windowing

**Problem:** Spectral leakage from finite-length signals

**Solution:** Apply window function to taper edges:
$$
y[n] = w[n] \cdot x[n]
$$

**Common windows:**
- Rectangular: Poor spectral leakage; narrow main lobe
- Hann: Good compromise (main lobe, sidelobe tradeoff)
- Hamming: Minimizes 4th sidelobe
- Blackman: Excellent sidelobe suppression; wider main lobe

**Trade-off:** Better sidelobe suppression → wider main lobe → frequency resolution loss

### Zero Padding

**Technique:** Append zeros to signal
$$
x_{\text{padded}}[n] = \begin{cases} x[n] & n = 0, \ldots, N-1 \\ 0 & n = N, \ldots, M-1 \end{cases}
$$

**Effect:** Increases frequency resolution; interpolates spectrum.

**Not:** Zero padding doesn't add information; reveals detail in underlying spectrum.

## Practical Applications

### Audio Signal Processing

**Music decomposition:**
- FFT reveals frequency content (musical notes)
- Frequency = pitch; magnitude = volume
- Filtering: remove unwanted frequencies

**Audio compression (MP3, AAC):**
- Frequency-domain analysis identifies perceptually irrelevant components
- Quantize less important frequencies to achieve compression

### Vibration Analysis

**Machinery condition monitoring:**
- FFT of vibration signal reveals bearing frequencies, gear mesh frequencies
- Anomalies in spectrum indicate faults (wear, imbalance, misalignment)

**Example:** Rotating machinery at 1500 RPM (25 Hz)
- 1× → 25 Hz (fundamental)
- 2× → 50 Hz (second harmonic, misalignment)
- Bearing fault frequencies → characteristic sidebands

### Communication Systems

**Modulation and Filtering:**
- Frequency shifting (modulation): $e^{i2\pi f_c t} x(t)$ → $X(f - f_c)$
- Demodulation inverse: multiply by $e^{-i2\pi f_c t}$
- Bandpass filtering: attenuate out-of-band noise

**Channel equalization:**
- Remove frequency-selective fading effects
- Inverse filter in frequency domain

### Image Processing

**2D Fourier Transform:**
$$
F(u,v) = \sum_x \sum_y f(x,y) e^{-i2\pi(ux + vy)/N}
$$

**Applications:**
- Image compression (JPEG uses DCT, related to FFT)
- Filtering (blur, sharpen, edge detection)
- Pattern recognition via frequency-domain matching

## Advanced Topics

### Short-Time Fourier Transform (STFT)

**Problem:** Fourier transform loses time information (global frequency content only)

**Solution:** Windowed Fourier transform
$$
X(t, f) = \int_{-\infty}^{\infty} x(\tau) w(\tau - t) e^{-i2\pi f \tau} \, d\tau
$$

**Time-frequency representation:** Spectrogram (magnitude of STFT)

**Application:** Speech analysis; time-varying frequencies.

### Wavelet Transform

**Alternative to STFT:**
$$
W(a, b) = \int_{-\infty}^{\infty} x(t) \psi^*\left(\frac{t-b}{a}\right) \frac{dt}{a}
$$

**Advantages:**
- Better time resolution for high frequencies
- Multiresolution analysis
- Sparse representation for transients

### Multidimensional Fourier Transform

**3D Fourier transform** (e.g., CT/MRI imaging):
$$
F(u, v, w) = \int\int\int f(x,y,z) e^{-i2\pi(ux+vy+wz)} \, dx \, dy \, dz
$$

**Application:** Inverse Fourier transform reconstructs 3D image from frequency-domain measurements.

## Dirac Function Connection

**Fourier transform of impulse:**
$$
\mathcal{F}\{\delta(t)\} = 1
$$

**Fourier transform of constant:**
$$
\mathcal{F}\{1\} = \delta(f)
$$

**Generalization:** Impulse in time → flat spectrum (all frequencies equally).

## See Also

- [[Laplace Transform]]
- [[Convolution]]
- [[Signal Processing]]
- [[Control Systems]]
- [[Frequency Response]]
- [[Differential Equations]]
- [[Complex Analysis]]
- [[Parseval's Theorem]]
- [[Fast Fourier Transform]]

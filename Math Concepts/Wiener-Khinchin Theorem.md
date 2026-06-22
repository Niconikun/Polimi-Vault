## Formal Definition

The **Wiener-Khinchin Theorem** (also known as the Wiener-Khintchine theorem) states that for a wide-sense stationary (WSS) [[Stochastic Process]], the [[Spacecraft Attitude Dynamics/Power Spectral Density (PSD)]] is the [[Fourier Transform]] of its [[Autocorrelation Function (ACF)]]. This fundamental result implies that the frequency-domain distribution of power in a random signal is uniquely determined by how the signal correlates with itself over time.

## Historical Development

### Key Milestones

- **1930:** Norbert Wiener publishes "Generalized [[Harmonic Analysis]]," providing the mathematical framework for linking correlation to spectra.
    
- **1934:** Aleksandr Khinchin independently formulates the theorem for stationary random processes in a more rigorous probabilistic context.
    
- **1940s:** The theorem becomes a cornerstone of radar development and noise analysis during World War II.
    

### Foundational Contributors

1. **Norbert Wiener (1894–1964):** An American mathematician who developed the theory for deterministic functions with finite power.
    
2. **Aleksandr Khinchin (1894–1959):** A Soviet mathematician who extended the results to the theory of probability and stochastic processes.
    

## Mathematical Formulation

### General Form

For a wide-sense stationary process $\{X(t)\}$, the Power Spectral Density $S_{XX}(f)$ and the [[Autocorrelation Function (ACF)]] $R_{XX}(\tau)$ form a [[Fourier Transform]] pair:

$$S_{XX}(f) = \int_{-\infty}^{\infty} R_{XX}(\tau) e^{-i 2\pi f \tau} \, d\tau$$

$$R_{XX}(\tau) = \int_{-\infty}^{\infty} S_{XX}(f) e^{i 2\pi f \tau} \, df$$

### Component Breakdown

- **$S_{XX}(f)$:** The [[Spacecraft Attitude Dynamics/Power Spectral Density (PSD)]], representing power per unit frequency.
    
- **$R_{XX}(\tau)$:** The [[Autocorrelation Function (ACF)]] at lag $\tau$.
    
- **$f$:** Frequency (Hz). If using angular frequency $\omega$ (rad/s), a factor of $1/2\pi$ is introduced in the inverse transform.
    

## Fundamental Principles

### Core Assumptions

1. **Wide-Sense Stationarity (WSS):** The process mean must be constant and the autocorrelation must depend only on the time lag $\tau$, not absolute time $t$.
    
2. **Finite Power:** The process must have a finite [[Mean Square Value]] (variance), ensuring the existence of the [[Fourier Transform]] in a generalized sense.
    

### Governing Laws/Theorems

- **Parseval's Theorem:** A corollary in this context is that the total power (area under the PSD) equals the [[Mean Square Value]] of the signal:
    
    $$E[X^2(t)] = R_{XX}(0) = \int_{-\infty}^{\infty} S_{XX}(f) \, df$$
    

## Theoretical Framework

### Relationship to Other Concepts

1. **Connection to [[Autocorrelation Function (ACF)]]:**
    
    - The theorem provides a method to calculate the PSD without needing the direct [[Fourier Transform]] of the signal itself (which may not exist for persistent random signals).
        
2. **Connection to [[Spacecraft Attitude Dynamics/Power Spectral Density (PSD)]]:**
    
    - It defines the physical meaning of the PSD as the "frequency-domain decomposition" of the signal's self-similarity.
        

## Physical Interpretation

### Significance in Space Structures

In the analysis of spacecraft and launch vehicles, the Wiener-Khinchin theorem is used to convert time-history data from accelerometers into **[[Random Vibration]] Profiles**.

- The **Autocorrelation** identifies the time-lagged memory of the structure ([[Damping]]).
    
- The **PSD** identifies the [[Resonance]] frequencies and energy distribution.
    
    The theorem allows engineers to characterize the "shaking" environment as a frequency-domain specification (e.g., $g^2/Hz$), which is essential for component qualification.
    

## Applications

### Engineering Disciplines

1. **[[Structural Dynamics]]:** Converting random stress-time histories into spectral density to perform fatigue life estimation.
    
2. **[[Signal Processing]]:** Designing filters to remove noise from telemetry data.
    
3. **Optics:** The theorem relates the coherence function of light to its optical spectrum (Van Cittert–Zernike theorem).
    

## Implementation Considerations

### Computational Aspects

In modern software (like MATLAB or Python/SciPy), the PSD is rarely calculated by first finding the autocorrelation and then transforming it. Instead, methods like **Welch’s Method** or the **Periodogram** are used, which utilize the FFT directly on segments of the time signal. However, the Wiener-Khinchin theorem remains the underlying theoretical justification for why these frequency-domain estimates represent the statistical nature of the process.

## Special Cases and Examples

### Example: [[White Noise]]

- **Autocorrelation:** $R_{XX}(\tau) = \delta(\tau)$ (Impulse at zero).
    
- **PSD:** $S_{XX}(f) = 1$ (Flat spectrum).
    
- **Interpretation:** Because [[White Noise]] has zero memory (uncorrelated at any $\tau > 0$), its power is spread equally across all frequencies.
    

## See Also

- [[Autocorrelation Function (ACF)]]
    
- [[Spacecraft Attitude Dynamics/Power Spectral Density (PSD)]]
    
- [[Stationarity]]
    
- [[Stochastic Process]]
    
- [[Random Vibration]]
    
- [[Fourier Transform]]
    

---

#technical-concept #mathematics #signal-processing #structural-dynamics #engineering #stochastic-processes
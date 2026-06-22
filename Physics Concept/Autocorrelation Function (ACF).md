## Formal Definition

The **Autocorrelation Function (ACF)** is a mathematical representation that quantifies the statistical [[correlation]] between values of a [[Stochastic Process]] at different points in time. For a real-valued process, it is defined as the [[expected value]] of the product of the process at time $t_1$ and time $t_2$. It serves as a measure of the "memory" of a system, indicating how long a signal remains correlated with itself before random fluctuations cause it to lose coherence.

## Historical Development

### Key Milestones

- **1920s:** G.U. Yule introduces autoregressive models in the study of sunspot cycles, laying the groundwork for [[Correlation]]-based time series analysis.
    
- **1930s:** Norbert Wiener and Aleksandr Khinchin independently establish the relationship between the autocorrelation function and the power spectrum.
    
- **1940s:** Developed extensively for radar and telecommunications during WWII to detect signals buried in noise.
    

### Foundational Contributors

1. **Norbert Wiener (1894–1964):** Formulated the mathematical generalized [[harmonic analysis]] linking time-domain [[correlation]] to frequency-domain power.
    
2. **Aleksandr Khinchin (1894–1959):** Proved the spectral decomposition of the correlation function for stationary processes.
    

## Mathematical Formulation

### General Form (Non-Stationary)

For a general [[Stochastic Process]] $\{X(t)\}$, the autocorrelation function $R_{XX}(t_1, t_2)$ is:

$$R_{XX}(t_1, t_2) = E[X(t_1)X(t_2)] = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} x_1 x_2 f_{X_1 X_2}(x_1, t_1; x_2, t_2) \, dx_1 dx_2$$

### Special Case: Wide-Sense Stationary (WSS)

For a WSS process, the function depends only on the time lag $\tau = t_2 - t_1$:

$$R_{XX}(\tau) = E[X(t)X(t+\tau)]$$

### Component Breakdown

- **$E[\cdot]$:** The ensemble average (expectation operator).
    
- **$\tau$ (Lag):** The time interval separating the two observations.
    
- **$R_{XX}(0)$:** When the lag is zero, the autocorrelation equals the [[Mean Square Value]] $E[X^2(t)]$. For a zero-mean process, this is the **[[variance]]**.
    

## Fundamental Principles

### Properties of $R_{XX}(\tau)$ for WSS Processes

1. **Symmetry (Even Function):** $R_{XX}(\tau) = R_{XX}(-\tau)$. The correlation doesn't care if the lag is forward or backward in time.
    
2. **Maximum at Zero:** $|R_{XX}(\tau)| \leq R_{XX}(0)$. A signal is always most similar to itself at zero lag.
    
3. **Periodicity:** If the underlying signal is periodic, the autocorrelation function will also be periodic with the same period.
    

### Governing Laws/Theorems

- **[[Wiener-Khinchin Theorem]]:** The autocorrelation function and the [[Spacecraft Attitude Dynamics/Power Spectral Density (PSD)]] are a [[Fourier Transform]] pair:
    
    $$S_{XX}(f) = \int_{-\infty}^{\infty} R_{XX}(\tau) e^{-j 2\pi f \tau} \, d\tau$$
    

## Theoretical Framework

### Relationship to Other Concepts

1. **Connection to [[Stationarity]]:**
    
    - If a process is WSS, its autocorrelation is invariant to absolute time shifts.
        
2. **Connection to [[Autocovariance]]:**
    
    - The autocovariance $C_{XX}(\tau)$ subtracts the mean: $C_{XX}(\tau) = R_{XX}(\tau) - \mu_X^2$.
        
3. **Connection to [[Ergodicity]]:**
    
    - In an [[Ergodic Process]], the autocorrelation can be calculated from a single time history $x(t)$ using a time-average integral:
        
        $$\mathcal{R}_{XX}(\tau) = \lim_{T \to \infty} \frac{1}{T} \int_{0}^{T} x(t)x(t+\tau) \, dt$$
        

## Classification and Variants

1. **Normalized Autocorrelation (Autocorrelation Coefficient):**
    
    Scales the function between -1 and 1:
    
    $$\rho_{XX}(\tau) = \frac{R_{XX}(\tau) - \mu^2}{\sigma^2}$$
    
2. **[[Cross-Correlation]] Function:**
    
    Measures the relationship between two _different_ processes $X(t)$ and $Y(t)$.
    

## Physical Interpretation

### Engineering Significance

In **Space Structures**, the autocorrelation function is used to identify:

- **Dominant Frequencies:** Peaks in $R_{XX}(\tau)$ reveal hidden periodicities in seemingly random vibrations.
    
- **[[Damping]] Characteristics:** The rate at which $R_{XX}(\tau)$ decays toward zero (or the mean squared) indicates the [[Damping]] in the system.
    
- **Signal-to-Noise Ratio:** Autocorrelation helps extract deterministic signals from broadband [[White Noise]], as [[White Noise]] decorrelates instantly ($\tau > 0$).
    

## Applications

### Engineering Disciplines

1. **Structural Health Monitoring:** Analyzing the "decay" of autocorrelation from ambient vibrations to detect stiffness loss.
    
2. **Aerospace Engineering:** Characterizing atmospheric turbulence or pressure fluctuations on a fuselage.
    
3. **Telecommunications:** Used in synchronization and pattern matching (e.g., GPS signal acquisition).
    

## Implementation Considerations

### Numerical Methods

In digital signal processing, the discrete autocorrelation is computed for a sequence $x[n]$:

$$\hat{R}_{XX}[m] = \frac{1}{N} \sum_{n=0}^{N-|m|-1} x[n]x[n+m]$$

### Computational Aspects

- **FFT Method:** For large datasets, it is computationally faster to compute the FFT, square the magnitude (to get the PSD), and then take the Inverse FFT to find the autocorrelation.
    

## Special Cases and Examples

### Benchmark Problems

1. **[[White Noise]]:**
    
    The autocorrelation is a Dirac delta function $\delta(\tau)$. This means the signal is completely uncorrelated with itself for any non-zero lag.
    
2. **Sine Wave ($A \sin(\omega t + \phi)$):**
    
    The autocorrelation is a cosine wave $\frac{A^2}{2} \cos(\omega \tau)$. Note that the phase information $\phi$ is lost.
    

## See Also

- [[Stochastic Process]]
    
- [[Stationarity]]
    
- [[Spacecraft Attitude Dynamics/Power Spectral Density (PSD)]]
    
- [[Wiener-Khinchin Theorem]]
    
- [[White Noise]]
    
- [[Structural Dynamics]]
    

---

#technical-concept #mathematics #signal-processing #engineering #vibration-analysis #stochastic-processes
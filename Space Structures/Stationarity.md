## Formal Definition

**Stationarity** is a fundamental property of a [[Stochastic Process]] wherein its statistical characteristics—such as mean, variance, and higher-order moments—remain invariant under time translation. In a stationary process, the probabilistic mechanisms governing the system do not change over time, meaning that a set of observations made at one time interval exhibits the same statistical behavior as a set of observations made at any other time interval of equal duration.

## Historical Development

### Key Milestones

- **1930s:** A.N. Kolmogorov establishes the rigorous foundations of [[probability theory]], including the concept of stationary processes.
    
- **1934:** Aleksandr Khinchin formulates the correlation theory of stationary processes.
    
- **1930s-40s:** Norbert Wiener and Khinchin independently derive the **[[Wiener-Khinchin Theorem]]**, linking the [[Autocorrelation Function (ACF)]] of a stationary process to its power spectral density.
    
- **1960s:** Widespread application in [[signal processing]] and control theory for analyzing random noise.
    
- **1980s:** Integration into time-series econometrics (e.g., unit root tests).
    

### Foundational Contributors

1. **Andrey Kolmogorov (1903–1987):** Laid the axiomatic basis for the theory of stationary processes.
    
2. **Aleksandr Khinchin (1894–1959):** Developed the spectral theory of stationary random processes.
    
3. **Norbert Wiener (1894–1964):** Applied stationarity concepts to generalized [[harmonic analysis]] and cybernetics.
    

## Mathematical Formulation

### General Form (Strict-Sense Stationarity)

A [[Stochastic Process]] $\{X(t)\}$ is strictly stationary if the joint probability distribution of any collection of $n$ random variables $\{X(t_1), X(t_2), \dots, X(t_n)\}$ is invariant under any time shift $\tau$.

$$F_X(x_1, t_1; x_2, t_2; \dots; x_n, t_n) = F_X(x_1, t_1+\tau; x_2, t_2+\tau; \dots; x_n, t_n+\tau)$$

where $F_X$ denotes the joint [[Cumulative Distribution Function (CDF)]].

### Component Breakdown

- **$t_i$:** Arbitrary points in time.
    
- **$\tau$:** An arbitrary time shift (lag).
    
- **[[Invariance]]:** The shape of the distribution does not depend on absolute time $t$, only on the relative intervals between points.
    

### Special Cases

1. **Wide-Sense Stationarity (WSS):**
    
    A weaker form where only the first two moments are time-invariant:
    
    $$E[X(t)] = \mu \quad (\text{constant})$$
    
    $$E[X(t)X(t+\tau)] = R_{XX}(\tau) \quad (\text{depends only on lag } \tau)$$
    

## Fundamental Principles

### Core Assumptions

1. **Time [[Invariance]]:** The physical laws or generating mechanisms producing the data do not evolve or drift during the observation period.
    
2. **Finite Moments:** For WSS, the mean and variance must be finite.
    

### Governing Laws/Theorems

- **[[Wiener-Khinchin Theorem]]:** For a wide-sense stationary process, the [[Spacecraft Attitude Dynamics/Power Spectral Density (PSD)]] $S_{XX}(\omega)$ is the [[Fourier Transform]] of the [[Autocorrelation Function (ACF)]] $R_{XX}(\tau)$:
    
    $$S_{XX}(\omega) = \int_{-\infty}^{\infty} R_{XX}(\tau) e^{-i\omega\tau} d\tau$$
    

## Theoretical Framework

### Relationship to Other Concepts

1. **Connection to [[Ergodicity]]:**
    
    - **Nature:** Stationarity is a prerequisite for [[Ergodicity]]. A process must be stationary to be ergodic, but a stationary process is not necessarily ergodic.
        
    - **Link:** If a process is ergodic, time averages converge to ensemble averages, which are constant constants (a property of stationarity).
        
2. **Contrast with [[Non-Stationary Process]]:**
    
    - **Key differences:** In non-stationary processes (e.g., random walk, earthquake ground motion), statistics like mean and variance are functions of time $t$.
        
    - **When to use:** Use stationarity for steady-state vibrations (wind, ocean waves). Use non-stationarity for transient events (explosions, seismic shocks).
        

## Classification and Variants

### By Strictness

1. **Strict-Sense Stationarity (SSS):** All statistical moments (distribution) are time-invariant. Hard to verify in practice.
    
2. **Wide-Sense Stationarity (WSS):** Only mean and autocorrelation are time-invariant. Sufficient for spectral analysis and linear systems.
    

### By Domain

1. **Cyclostationarity:** Statistical properties vary periodically with time (e.g., rotating machinery, seasonal economic data).
    
    $$R_{XX}(t, \tau) = R_{XX}(t + T, \tau)$$
    
2. **Locally Stationary:** The process behaves as stationary within short time windows but evolves slowly over long durations.
    

## Physical Interpretation

### Geometric Meaning

In a geometric sense, the "cloud" of probability density describing the state of the system does not translate or deform as it moves along the time axis; its shape remains frozen relative to the system's coordinates.

### Mechanical Significance

Represents a system in "statistical equilibrium." For example, a vehicle driving at a constant speed over a rough road surface of uniform roughness experiences stationary [[Random Vibration]]. The energy input and dissipation are balanced on average.

## Applications

### Engineering Disciplines

1. **[[Structural Dynamics]]:** Analysis of wind loads, ocean wave forces, and turbulent boundary layers.
    
2. **Communications:** Modeling background noise (thermal noise) in receiver channels.
    
3. **Geotechnical Engineering:** Analysis of micro-tremors or steady-state soil vibrations.
    

### Practical Implementations

- **Spectral Analysis:** The assumption of stationarity allows the use of FFT (Fast Fourier Transform) to compute a meaningful [[Spacecraft Attitude Dynamics/Power Spectral Density (PSD)]].
    

## Implementation Considerations

### Numerical Methods

1. **Run Test:** A non-parametric test to check for randomness and stationarity by analyzing the sequence of values above and below the median.
    
2. **Reverse Arrangements Test:** Checks for monotonic trends in the [[Mean Square Value]] of the data.
    

### Computational Aspects

- **Data Length:** To validate stationarity (especially for low frequencies), the observation time $T$ must be many times longer than the longest period of interest.
    

## Advantages and Limitations

### Strengths

1. **Analytical Power:** Enables frequency-domain analysis (PSD), which is computationally efficient and intuitive for engineers.
    
2. **Predictability:** Statistical parameters estimated from the past apply to the future.
    

### Weaknesses

1. **Idealization:** Few real-world processes are perfectly stationary forever; most are only "quasi-stationary" over short durations.
    
2. **Loss of Transient Info:** Stationarity assumptions average out transient spikes or non-repetitive events that might be critical for failure analysis.
    

### Validity Range

- **Applicable When:** Environmental conditions are constant (e.g., steady wind speed, constant RPM).
    
- **Not Applicable When:** Environmental conditions change rapidly (e.g., car accelerating, earthquake onset).
    

## Special Cases and Examples

### Benchmark Problems

1. **[[White Noise]]:**
    
    - **Description:** A signal with zero mean and constant power spectral density across all frequencies.
        
    - **Solution:** $R_{XX}(\tau) = \sigma^2 \delta(\tau)$ (Dirac delta).
        
    - **Significance:** The fundamental building block for modeling random inputs.
        

### Numerical Examples

- **Stationary:** A recording of fan noise running at constant speed.
    
- **Non-Stationary:** A recording of a door slam or an engine revving up.
    

## Error Analysis

### Sources of Error

1. **Trend Contamination:** Low-frequency trends (drifts) in data can falsely suggest non-stationarity or distort the [[Autocorrelation Function (ACF)]].
    
2. **Insufficient Duration:** Short data samples may appear non-stationary simply due to high variance in the estimator, not the process itself.
    

## Pedagogical Approach

### Teaching Strategies

1. **Visual Analogy:** Compare a stationary process to a "steady flow" of water in a pipe (properties at a point don't change with time), versus a "surge" or "pulse" (non-stationary).
    
2. **Ensemble Visualization:** Show multiple sample paths stacked vertically to illustrate that the distribution across the "vertical slice" at $t_1$ is identical to the slice at $t_2$.
    

### Common Misconceptions

1. **"Stationary means constant":** Misconception that the signal $X(t)$ itself is constant. Correction: The _statistics_ are constant; the signal fluctuates randomly.
    
2. **"Stationarity implies [[Ergodicity]]":** Clarification that while linked, a process can be stationary (statistics don't change) but not ergodic (single sample doesn't represent the whole).
    

## See Also

- [[Stochastic Process]]
    
- [[Ergodicity]]
    
- [[Power Spectral Density]]
    
- [[Autocorrelation Function (ACF)]]
    
- [[Wiener-Khinchin Theorem]]
    
- [[Non-Stationary Process]]
    

---

#technical-concept #mathematics #engineering #statistics #signal-processing #structural-dynamics
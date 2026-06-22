## Formal Definition

The **Two-Sided [[Spacecraft Attitude Dynamics/Power Spectral Density (PSD)]]**, denoted as $S_{xx}(f)$, is a frequency-domain representation of a random signal that extends over both positive and negative frequencies ($-\infty < f < \infty$). It is mathematically defined as the [[Fourier Transform]] of the signal's **Autocorrelation Function**. In this representation, the total power (variance) of the signal is distributed equally between the positive and negative frequency halves. While negative frequencies are not physically observable, the two-sided PSD is the essential theoretical framework used for rigorous mathematical analysis and [[signal processing]] algorithms in spacecraft communication and [[Structural Dynamics]].

## Historical Development

### Key Milestones

- **1930:** **Norbert Wiener** formalizes the relationship between the time-domain correlation and the two-sided power spectrum in his work on generalized [[harmonic analysis]].
    
- **1934:** **Aleksandr Khinchin** independently arrives at the same conclusion, leading to the **Wiener–Khinchin Theorem**, which serves as the bedrock of two-sided PSD theory.
    
- **1965:** The invention of the **Fast Fourier Transform (FFT)** algorithm by Cooley and Tukey makes the computation of two-sided PSDs instantaneous for modern structural engineers.
    

### Foundational Contributors

1. **Norbert Wiener:** Provided the rigorous proof that power spectra are the [[Fourier Transform]] of autocorrelation.
    
2. **Claude Shannon:** Used two-sided power spectra to define the fundamental limits of information and noise in communication channels.
    

## Mathematical Formulation

### 1. The Wiener–Khinchin Theorem

The two-sided PSD is the [[Fourier Transform]] of the autocorrelation function $R_{xx}(\tau)$:

$$S_{xx}(f) = \int_{-\infty}^{\infty} R_{xx}(\tau) e^{-j 2\pi f \tau} \, d\tau$$

### 2. Symmetry Property

For any real-valued physical signal (like the vibration of a satellite), the two-sided PSD is an **even function**:

$$S_{xx}(f) = S_{xx}(-f)$$

### 3. Total Power (The Area)

The total [[Mean Square Value]] (variance) is the integral over the entire frequency range:

$$E[X^2] = \sigma^2 = \int_{-\infty}^{\infty} S_{xx}(f) \, df$$

_Compare this to the one-sided version, where the integral starts at zero and the function is doubled._

## Fundamental Principles

### Core Assumptions

1. **[[Stationarity]]:** The statistical properties of the random process do not change over time.
    
2. **Complex Mathematics:** Utilizes complex exponentials ($e^{-j \omega t}$), which naturally result in a two-sided mathematical output.
    

### Governing Laws

- **Parseval’s Theorem:** States that the total energy of a signal is preserved when moving from the time domain to the two-sided frequency domain.
    

## Theoretical Framework

### The Mathematical Necessity

Why do we use negative frequencies?

- In the complex [[Fourier Transform]], a real-world sine wave is made of two complex rotating vectors: one rotating clockwise and one counter-clockwise.
    
- The "negative frequency" represents the vector rotating in the opposite direction.
    
- Without the negative side, the math of the Inverse Fourier Transform would not return a real-valued signal.
    

## Physical Interpretation

### The "Mirror" Analogy

Imagine you are looking at the one-sided PSD of a rocket's vibration in a mirror held at the $f=0$ axis.

- The reflection is the negative frequency side.
    
- The "Total Power" of the vibration is split in half—half in the real world (positive) and half in the mirror world (negative).
    
- To get the "total energy" for your structural analysis, you have to add both sides together.
    

## Advantages and Limitations

### Strengths

1. **Mathematical Elegance:** All standard [[signal processing]] theorems (like Convolution or Correlation) are built on the two-sided model.
    
2. **FFT Output:** Standard numerical libraries (like `numpy.fft`) provide two-sided results by default.
    

### Limitations

1. **Non-Physical:** You cannot "measure" a negative frequency with a physical sensor; it is purely a mathematical construct.
    
2. **Potential Confusion:** It is easy to accidentally use only half the power if you forget that the energy is split between the two sides.
    

## Applications

### Spacecraft Systems

1. **Digital Signal Processing (DSP):** Analyzing the noise spectrum in satellite communication links.
    
2. **Control Loop Stability:** Using two-sided spectra in the Z-domain or S-domain for GNC stability analysis.
    
3. **Data Analysis:** Processing "Raw" vibration data from flight sensors before converting it to a one-sided format for a structural report.
    

---

## See Also

- [[One-Sided PSD]]
    
- [[Wiener-Khinchin Theorem]]
    
- [[Autocorrelation Function (ACF)]]
    
- [[Fourier Transform]]
    

## Recommended Tags:

#random-analysis #two-sided-PSD #vibrations #Fourier-Transform #Wiener-Khinchin #signal-processing #aerospace-engineering
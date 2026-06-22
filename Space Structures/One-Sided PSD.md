## Formal Definition

The **One-Sided PSD**, typically denoted as Gxx​(f), is a frequency-domain function defined only for non-negative frequencies (f≥0). It is derived from the theoretical [[Two-sided PSD]] (Sxx​(f)) by doubling the values for all frequencies greater than zero. This adjustment ensures that the total area under the curve (the total power/variance) remains consistent with the time-domain signal. In structural testing, the one-sided PSD is the standard format for representing random vibration specifications, usually plotted as **g2/Hz** vs. **Frequency (Hz)**.

## Mathematical Formulation

### 1. Relationship to Two-Sided PSD

The relationship between the one-sided PSD (Gxx​) and the two-sided PSD (Sxx​) is: $$G_{xx}(f) = \begin{cases} S_{xx}(0) & \text{if } f = 0 \ 2S_{xx}(f) & \text{if } f > 0 \ 0 & \text{if } f < 0 \end{cases}$$

### 2. The [[Mean Square Value]] (The Area Rule)

Since Gxx​(f) captures all the energy of the signal, the integral is taken only from zero to infinity:

E[X2]=σ2=∫0∞​Gxx​(f)df

For a flat PSD ([[White Noise]]) over a frequency band from f1​ to f2​ with constant density A0​:

σ2=A0​×(f2​−f1​)

To find the $g_{RMS}$​, you simply take the square root of that area:

$$
g_{RMS} = \sqrt{\int_0^\inf G_{xx}(f)df}
$$

## Fundamental Principles

### Core Assumptions

1. **Physical Realism:** Assumes that negative frequencies are a mathematical construct and that all physical energy can be mapped to the positive spectrum.
    
2. **Symmetry:** Relies on the fact that for real-valued signals (like actual physical vibrations), the two-sided PSD is symmetric (Sxx​(f)=Sxx​(−f)).
    

### Governing Laws

- **Conservation of Energy:** The total [[Mean Square Value]] must remain identical regardless of whether you use the two-sided or one-sided representation.
    

## Theoretical Framework

### Why "One-Sided"?

In a lab, a spectrum analyzer or a shaker table controller doesn't "see" negative 50 Hz. By using the one-sided PSD, engineers can:

- Directly compare the plot to the physical frequencies of the satellite's structure.
    
- Simplify the integration process for calculating GRMS​.
    
- Standardize reporting—almost all NASA and ESA vibration standards (like **NASA-STD-7001**) use one-sided definitions.
    

## Physical Interpretation

### The "Folding" Analogy

Imagine a piece of paper representing the two-sided PSD, with a mirror-image graph on the left (negative) and right (positive) sides of the center.

- **One-Sided PSD** is like folding that paper in half down the middle.
    
- The "energy" on the negative side doesn't disappear; it gets added to the energy on the positive side.
    
- The resulting graph is twice as "tall" but only half as wide (starting from zero).
    

## Advantages and Limitations

### Strengths

1. **Direct Readability:** You can look at the Y-axis and see the exact energy density at a specific physical frequency.
    
2. **Efficiency:** It is computationally and visually more efficient to ignore the redundant negative half of the spectrum.
    

### Limitations

1. **Mathematical Transition:** You must be careful when using [[Fourier Transform]] identities; most theoretical math is built for "two-sided" functions, so you must remember the factor of 2 when applying it to real-world one-sided data.
    

## Applications

### Spacecraft Vibration Testing

1. **Random Vibration Specs:** Defining the "input" for a shaker table test of a CubeSat or instrument.
    
2. **G-RMS Calculation:** Quickly estimating the total vibration load by calculating the area under the one-sided PSD segments (often using the "log-log slope" integration method).
    
3. **Acoustic Load Analysis:** Characterizing the energy levels of the roar of a rocket engine in the 20 Hz to 2000 Hz range.
    

---

## See Also

- [[Spacecraft Attitude Dynamics/Power Spectral Density (PSD)]]
    
- [[Mean Square Value]]
    
- [[RMS (Root Mean Square)]]
    
- [[Autocorrelation Function (ACF)]]
    

## Recommended Tags:

#random-analysis #one-sided-PSD #vibrations #space-structures #G-RMS #structural-testing #aerospace-engineering
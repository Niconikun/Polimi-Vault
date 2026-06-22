#control-theory #stability-analysis #frequency-response #nyquist-criterion #robust-control #ADCS

## **Formal Definition**

The **Nyquist Stability Criterion** is a graphical frequency-domain method for determining the stability of a closed-loop control system by analyzing the open-loop [[Transfer Function]]'s [[Frequency Response Function (FRF)]] plot ([[Nyquist plot]]). Developed by Harry Nyquist in 1932, it provides a powerful technique that reveals not only stability but also the degree of stability through gain and phase margins. Unlike root locus methods, Nyquist criterion can handle systems with time delays and provides insights into robustness.

---

## **Mathematical Foundation**

### **Principle of Argument (Cauchy's Theorem)**

The Nyquist criterion is based on **Cauchy's argument principle** from complex analysis:

Given a complex function $F(s)$ that is analytic (except at poles) on and inside a closed contour $C$ in the s-plane, and $F(s)$ has no zeros on $C$, then:

$$
N = Z - P
$$

where:
- $N$ = Number of **clockwise** encirclements of the origin by $F(s)$ as $s$ traverses $C$ clockwise
- $Z$ = Number of zeros of $F(s)$ inside $C$
- $P$ = Number of poles of $F(s)$ inside $C$

### **Application to Control Systems**

For a closed-loop system with open-loop [[Transfer Function]] $L(s)$, the [[Characteristic Equation]] is:

$$
1 + L(s) = 0 \quad \Rightarrow \quad F(s) = 1 + L(s)
$$

The **Nyquist Path** $C$ is a contour that encircles the entire right-half s-plane (RHP), typically consisting of:
1. The imaginary axis from $-j\infty$ to $+j\infty$
2. A semicircle of infinite radius enclosing the RHP

### **Nyquist Stability Criterion Statement**

For a closed-loop system with open-loop [[Transfer Function]] $L(s)$, the closed-loop system is **stable** if and only if:

$$
N = -P
$$

where:
- $N$ = Number of **clockwise** encirclements of the point $(-1, 0)$ by the Nyquist plot of $L(s)$
- $P$ = Number of **open-loop poles** in the right-half plane (RHP)

If $P = 0$ (open-loop stable), then for closed-loop stability: $N = 0$ (no encirclements of -1).

---

## **Construction of Nyquist Plot**

### **Mapping the Nyquist Path**

The Nyquist plot is the mapping of the Nyquist contour $C$ through $L(s)$:

1. **Segment 1: Imaginary axis ($s = j\omega, \omega: -\infty \to +\infty$)**
   - Plot $L(j\omega)$ for $\omega = 0 \to +\infty$
   - The plot for $\omega = -\infty \to 0$ is the mirror image about the real axis (for real rational $L(s)$)

2. **Segment 2: Infinite semicircle ($|s| \to \infty$)**
   - For proper transfer functions ($\deg(\text{denominator}) \geq \deg(\text{numerator})$), maps to the origin
   - For strictly proper ($\deg(\text{denominator}) > \deg(\text{numerator})$), maps to origin
   - For improper systems, requires special consideration

### **Key Features of Nyquist Plot**

- **Real-axis crossings:** Where $\text{Im}[L(j\omega)] = 0$
- **Imaginary-axis crossings:** Where $\text{Re}[L(j\omega)] = 0$
- **Origin encirclements:** Important for systems with integrators
- **Critical point:** $(-1, 0)$ in the complex plane

---

## **Stability Analysis Procedure**

### **Step-by-Step Analysis**

1. **Determine open-loop poles $P_{OL}$**
   - Count poles of $L(s)$ in RHP
   - For systems with poles on imaginary axis, modify Nyquist path with infinitesimal indentations

2. **Plot $L(j\omega)$ for $\omega = 0^+ \to +\infty$**
   - Calculate magnitude $|L(j\omega)|$ and phase $\angle L(j\omega)$
   - Identify real-axis crossings

3. **Complete the Nyquist plot**
   - Add mirror image for negative frequencies
   - Add mapping of infinite semicircle

4. **Count encirclements $N$ of $(-1, 0)$**
   - Use "test ray" method: draw ray from (-1,0) to infinity
   - Count net clockwise crossings

5. **Apply Nyquist criterion: $Z = N + P$**
   - $Z$ = Number of closed-loop poles in RHP
   - For stability: $Z = 0$

### **Modified Nyquist Path for Special Cases**

For open-loop poles on imaginary axis (integrators, jω-axis poles):
- Create infinitesimal semicircular indentations around these poles
- Map these indentations to determine behavior near infinity

---

## **Stability Margins from Nyquist Plot**

### **Gain Margin (GM)**
- **Definition:** Factor by which gain can be increased before instability
- **On Nyquist plot:** Distance from (-1,0) to plot along negative real axis
- **Calculation:** 
  $$
  GM = \frac{1}{|L(j\omega_{pc})|} \quad \text{or} \quad GM_{dB} = -20\log_{10}|L(j\omega_{pc})|
  $$
  where $\omega_{pc}$ is phase crossover frequency ($\angle L(j\omega_{pc}) = -180°$)

### **Phase Margin (PM)**
- **Definition:** Additional phase lag needed to cause instability
- **On Nyquist plot:** Angle from negative real axis to intersection with unit circle
- **Calculation:**
  $$
  PM = 180° + \angle L(j\omega_{gc})
  $$
  where $\omega_{gc}$ is gain crossover frequency ($|L(j\omega_{gc})| = 1$)

### **Delay Margin**
- **Definition:** Additional time delay that can be tolerated
- **Calculation:** $ \tau_{max} = \frac{PM}{\omega_{gc}} $ (in radians)

---

## **Relevance in Attitude Determination and Control Systems (ADCS)**

### **1. Handling Time Delays**
Spacecraft control systems often have time delays due to:
- Computational delays in digital controllers
- Communication delays in distributed systems
- Actuator/sensor dynamics

**Time delay $e^{-sT}$** contributes phase lag: $\angle e^{-j\omega T} = -\omega T$ radians

**Nyquist advantage:** Can directly analyze systems with time delays, unlike Routh-Hurwitz.

**Example:** For system $L(s) = \frac{K e^{-sT}}{s^2}$:
- [[Bode Plot]] shows phase continuously decreasing
- Nyquist plot spirals inward toward origin
- Stability depends on number of encirclements

### **2. Flexible Spacecraft Stability Analysis**
For spacecraft with flexible modes:
$$
L(s) = \frac{K}{s^2} + \sum_{i=1}^{n} \frac{K_i}{s^2 + 2\zeta_i\omega_i s + \omega_i^2}
$$

**Nyquist plot shows:**
- Large loops near flexible mode frequencies
- Additional phase lag that can reduce stability margins
- Multiple real-axis crossings requiring careful encirclement counting

### **3. Robustness Analysis**
Nyquist criterion helps analyze:
- **Gain uncertainty:** Distance from (-1,0) along negative real axis
- **Phase uncertainty:** Angular deviation at unit circle
- **Multiplicative uncertainty:** Disk around nominal Nyquist plot

### **4. Non-Minimum Phase Systems**
Systems with RHP zeros (e.g., certain spacecraft configurations):
- Exhibit inverse response
- Nyquist plot shows unusual phase behavior
- Fundamental limitations on achievable bandwidth

### **5. Conditionally Stable Systems**
Some spacecraft control systems exhibit **conditional stability**:
- Stable for intermediate gains
- Unstable for both low and high gains
- Nyquist plot shows multiple encirclements changing with gain

---

## **Special Cases and Examples**

### **Example 1: First-Order System**
$$
L(s) = \frac{K}{\tau s + 1}
$$
- Nyquist plot: Semicircle in right-half plane
- Always stable for any $K > 0$ (no encirclements of -1)

### **Example 2: Double Integrator (Spacecraft Attitude)**
$$
L(s) = \frac{K}{s^2}
$$
- Nyquist plot: Entire negative real axis (twice)
- For $K > 0$: Plot lies on negative real axis
- Encirclements: None if $-1$ not reached, infinite if $K$ large
- Actually: Modified Nyquist path needed due to poles at origin

### **Example 3: Double Integrator with PD Control**
$$
L(s) = \frac{K_d s + K_p}{s^2}
$$
- Adds phase lead, pulling Nyquist plot away from (-1,0)
- Improves stability margins

### **Example 4: System with Time Delay**
$$
L(s) = \frac{K e^{-sT}}{s(s+1)}
$$
- Nyquist plot spirals inward
- Multiple encirclements possible depending on $K$ and $T$
- Critical gain: $K_{crit}$ where plot passes through (-1,0)

---

## **Comparative Advantages**

### **vs. Routh-Hurwitz**
- Handles time delays directly
- Provides stability margins
- Works with transcendental transfer functions
- Graphical insight into robustness

### **vs. Bode Plots**
- Better for conditionally stable systems
- Clear visualization of encirclements
- Direct handling of open-loop unstable systems
- More accurate for systems with rapid phase changes

### **vs. Root Locus**
- Works with time delays
- Frequency-domain insight
- Direct stability margin quantification
- Better for systems with parameter uncertainty

---

## **Practical Application in ADCS Design**

### **Design Procedure for Attitude Controller**

1. **Obtain open-loop [[Transfer Function]]** $L(s) = C(s)G(s)$
   - $G(s)$: Spacecraft dynamics (often $\frac{1}{Is^2}$ for [[Rigid Body]])
   - $C(s)$: Controller (PID, lead-lag, etc.)

2. **Plot Nyquist for nominal system**
   - Include flexible modes if significant
   - Include time delays if present

3. **Check stability criterion**
   - Count open-loop RHP poles $P$
   - Count encirclements $N$ of (-1,0)
   - Verify $Z = N + P = 0$

4. **Evaluate stability margins**
   - Gain margin > 6 dB (flexible) or 3 dB (rigid)
   - Phase margin > 30° (preferably 45°-60°)

5. **Robustness verification**
   - Add uncertainty bounds (disk margins)
   - Verify stability for all possible variations

### **Handling Integrators in Spacecraft Dynamics**

For $G(s) = 1/(Is^2)$:
1. Use modified Nyquist path with indentations around $s=0$
2. Mapping of indentation: Large semicircle in Nyquist plot
3. Count encirclements carefully

---

## **Nyquist with Uncertainties**

### **Disk Margin**
Define uncertainty as multiplicative:
$$
L_{actual}(s) = L(s)[1 + W(s)\Delta(s)], \quad |\Delta(j\omega)| \leq 1
$$

On Nyquist plot:
- Plot disks centered at $L(j\omega)$ with radius $|L(j\omega)W(j\omega)|$
- System robustly stable if no disk covers (-1,0)

### **Structured Singular Value (μ)**
For structured uncertainties:
$$
\mu = \frac{1}{\min\{k: \det(I + L(j\omega)\Delta) = 0\}}
$$
Robust stability if $\mu < 1$ for all ω.

---

## **Numerical Computation Methods**

### **Algorithm for Nyquist Plot Generation**
```
function nyquist_plot(L, omega)
    % L: transfer function, omega: frequency vector
    
    % Evaluate frequency response
    for i = 1:length(omega)
        s = 1j * omega(i);
        L_freq(i) = eval_transfer_function(L, s);
    end
    
    % Plot positive frequencies
    plot(real(L_freq), imag(L_freq));
    
    % Add negative frequencies (mirror image)
    L_neg = conj(L_freq(end:-1:1));
    plot(real(L_neg), imag(L_neg), '--');
    
    % Mark critical point
    plot(-1, 0, 'ro', 'MarkerSize', 8);
    
    % Count encirclements
    N = count_encirclements(L_freq, -1, 0);
end

function N = count_encirclements(plot_points, x0, y0)
    % Use winding number algorithm
    angle_sum = 0;
    for i = 1:length(plot_points)-1
        dx1 = real(plot_points(i)) - x0;
        dy1 = imag(plot_points(i)) - y0;
        dx2 = real(plot_points(i+1)) - x0;
        dy2 = imag(plot_points(i+1)) - y0;
        
        angle_sum = angle_sum + atan2(dx1*dy2 - dy1*dx2, dx1*dx2 + dy1*dy2);
    end
    N = round(angle_sum / (2*pi));
end
```

### **Automatic Stability Assessment**
Modern tools (MATLAB, Python control library) provide:
- `nyquist()` function for plotting
- `margin()` for stability margins
- `robstab()` for robust stability analysis

---

## **Limitations and Considerations**

### **1. Computational Complexity**
- Manual plotting is labor-intensive
- Automated tools handle complex systems
- Care needed for systems with many poles/zeros

### **2. Interpretation Challenges**
- Multiple encirclements can be confusing
- Systems with many crossings require careful counting
- Infinite plots for improper systems

### **3. Digital Systems**
For discrete-time systems:
- Use $z$-plane instead of $s$-plane
- Nyquist path encircles unit circle exterior
- Similar principles apply

### **4. Nonlinear Systems**
Direct application fails for nonlinear systems
- Use describing function method for certain nonlinearities
- Or linearize around operating point

---

## **Historical Context**
Developed by Harry Nyquist at Bell Labs in 1932 to determine stability of feedback amplifiers. Originally published in "Regeneration Theory" (1932). Extended by Bode, Black, and others. Became fundamental to control theory development in 1940s-1950s.

---

## **See Also**
- **[[Bode Plot]]** - Complementary frequency-domain analysis
- **[[Root Locus]]** - s-domain stability analysis
- **[[Routh-Hurwitz Criterion]]** - Algebraic stability test
- **[[Stability Margins]]** - Gain and phase margin concepts
- **[[Cauchy's Theorem]]** - Mathematical foundation
- **[[Robust Stability]]** - Stability under uncertainty
- **[[Describing Function]]** - Extension to nonlinear systems

---

## **References**
1. Nyquist, H. (1932). "Regeneration Theory". *Bell System Technical Journal*.
2. Franklin, G. F., Powell, J. D., & Emami-Naeini, A. (2015). *Feedback Control of Dynamic Systems*. Pearson.
3. Dorf, R. C., & Bishop, R. H. (2011). *Modern Control Systems*. Prentice Hall.
4. Sidi, M. J. (1997). *Spacecraft Dynamics and Control*. Cambridge University Press.
5. Stein, G. (2003). "Respect the Unstable". *IEEE Control Systems Magazine*.
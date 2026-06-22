### **Antenna Calculations for Ground Stations**
Antenna performance is critical for reliable spacecraft communication. Key calculations include:
1. **[[Link Budget Analysis]]**
2. **[[Antenna Gain]]**
3. **Beamwidth & Pointing Accuracy**
4. **Free-Space Path Loss (FSPL)**
5. **Received Power & Signal-to-Noise Ratio (SNR)**

---

#### **1. Link Budget Equation**
The **link budget** ensures the signal strength is sufficient for communication. The fundamental equation is:

$$
\frac{P_r}{P_t} = G_t + G_r - L_{fs} - L_{other} \quad \text{(dB)}
$$

| Parameter          | Symbol       | Units       | Description                                                                 |
|--------------------|--------------|-------------|-----------------------------------------------------------------------------|
| Transmitted Power  | $P_t$        | dBW or dBm  | Power output from the transmitter.                                         |
| Received Power     | $P_r$        | dBW or dBm  | Power at the receiver input.                                               |
| Transmit Antenna Gain | $G_t$     | dBi         | Gain of the ground station antenna.                                        |
| Receive Antenna Gain | $G_r$     | dBi         | Gain of the spacecraft antenna.                                            |
| Free-Space Loss    | $L_{fs}$     | dB          | Path loss due to distance and frequency (see Section 4).                  |
| Other Losses       | $L_{other}$  | dB          | Atmospheric absorption, polarization mismatch, cable losses, etc.          |

**Example:**
For a **35m DSN antenna** ($G_t = 72$ dBi) communicating with a Mars rover ($G_r = 30$ dBi) at a distance of **2.2 AU** (330 million km) at **X-band (8.4 GHz)**:
- $P_t = 20$ kW ($43$ dBW),
- $L_{fs} = 292$ dB (calculated below),
- $L_{other} = 3$ dB (atmospheric + pointing losses).
- **Received Power ($P_r$):**
  $43 + 72 + 30 - 292 - 3 = -150$ dBW ($= 10^{-15}$ W).

---

#### **2. Antenna Gain ($G$)**
Antenna gain quantifies how effectively an antenna directs energy in a specific direction. For a **parabolic dish**, gain is calculated as:

$
G = 10 \log_{10} \left( \eta \left( \frac{\pi D}{\lambda} \right)^2 \right) \quad \text{(dBi)}
$

| Parameter          | Symbol | Units       | Description                                                                 |
|--------------------|--------|-------------|-----------------------------------------------------------------------------|
| Diameter           | $D$    | meters      | Physical diameter of the dish.                                             |
| Wavelength         | $\lambda$ | meters   | $= \frac{c}{f}$ (e.g., $\lambda = 0.0357$ m for X-band at 8.4 GHz).        |
| Efficiency         | $\eta$  | (0–1)       | Typical values: 0.55–0.75 (55–75%) for large dishes.                       |

**Example:**
For a **35m DSN antenna** at **8.4 GHz** ($\lambda = 0.0357$ m) with $\eta = 0.65$:
$
G = 10 \log_{10} \left( 0.65 \left( \frac{\pi \times 35}{0.0357} \right)^2 \right) \approx 72 \text{ dBi}
$

---

#### **3. Beamwidth ($\theta$)**
The **[[half-power beamwidth]]** (HPBW) defines the angular width of the antenna’s main lobe:

$
\theta = \frac{70 \lambda}{D} \quad \text{(degrees, for parabolic dishes)}
$

**Example:**
For the **35m DSN antenna** at **8.4 GHz**:
$
\theta = \frac{70 \times 0.0357}{35} \approx 0.0714^\circ \quad (\text{~0.0125 radians})
$

**Implications:**
- Narrow beamwidths require **precise pointing** (e.g., DSN antennas use **monopulse tracking**).
- For LEO satellites, beamwidths are wider (e.g., a **3m dish** at **2.4 GHz** has $\theta \approx 1.7^\circ$).

---

#### **4. Free-Space Path Loss ($L_{fs}$)**
FSPL accounts for signal attenuation over distance:

$$
L_{fs} = 20 \log_{10} \left( \frac{4 \pi d}{\lambda} \right) \quad \text{(dB)}
$$

| Parameter  | Symbol    | Units  | Description                                                      |
| ---------- | --------- | ------ | ---------------------------------------------------------------- |
| Distance   | $d$       | meters | Range to the spacecraft (e.g., 400 km for LEO, 2.2 AU for Mars). |
| Wavelength | $\lambda$ | meters | As above.                                                        |

**Examples:**
| Scenario               | Distance ($d$)       | Frequency       | $L_{fs}$ (dB)  |
|------------------------|-----------------------|-----------------|----------------|
| **LEO Satellite**      | 500 km                | 2.4 GHz (S-band)| 156             |
| **GEO Satellite**      | 35,786 km             | 8.4 GHz (X-band)| 205             |
| **Mars (Opposition)**  | 2.2 AU (~330M km)     | 8.4 GHz         | 292             |


#### **5. Received Power & Signal-to-Noise Ratio (SNR)**
The **received power** ($P_r$) must exceed the receiver’s **noise floor** for successful demodulation. SNR is calculated as:

$
SNR = P_r - N \quad \text{(dB)}
$

Where:
- **Noise Power ($N$):**
  $
  N = k T B \quad \text{(Watts)}
  $
  - $k$: Boltzmann’s constant ($1.38 \times 10^{-23}$ J/K).
  - $T$: System noise temperature (K) (e.g., 20 K for cryogenically cooled DSN receivers).
  - $B$: Bandwidth (Hz) (e.g., 1 MHz for telemetry).

**Example:**
For the Mars rover example above ($P_r = -150$ dBW) with $T = 20$ K and $B = 1$ MHz:
$
N = 1.38 \times 10^{-23} \times 20 \times 10^6 = 2.76 \times 10^{-16} \text{ W} \quad (-155.6 \text{ dBW})
$
$
SNR = -150 - (-155.6) = 5.6 \text{ dB}
$
(Adequate for error-corrected data links.)

---

#### **6. Pointing Accuracy Requirements**
For narrow-beam antennas (e.g., DSN), **pointing errors** ($\Delta \theta$) must be << beamwidth ($\theta$). The **3-dB loss limit** is typically $\Delta \theta \leq 0.1 \theta$.

**Example:**
For the **35m DSN antenna** ($\theta = 0.0714^\circ$), pointing must be accurate to **~0.007°** (~25 arcseconds). Achieved via:
- **Autotrack systems** (e.g., conical scan or monopulse).
- **Ephemris data** (e.g., JPL Horizons for deep-space targets).

---

### **Practical Tools for Calculations**
1. **Software:**
   - **GMAT** (General Mission Analysis Tool): Simulates link budgets.
   - **STK** (Systems Tool Kit): Models antenna coverage and access intervals.
   - **Python Libraries:** `scipy.constants` (for $c$, $k$) and `numpy` for dB calculations.

2. **Online Calculators:**
   - [NASA DSN Link Budget Tool](https://deepspace.jpl.nasa.gov/)
   - [Satellite Tool Kit (STK) Free Trial](https://www.agi.com/)
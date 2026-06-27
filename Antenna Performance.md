---
title: Antenna Performance
tags:
  - communications
  - electromagnetics
  - signal processing
  - spacecraft systems
---

# Antenna Performance

## Formal Definition

**Antenna performance** characterizes the effectiveness of an antenna in transmitting or receiving electromagnetic signals. Key performance parameters include **gain** (directivity amplification), **beamwidth** (angular coverage), **impedance matching** (efficiency of energy transfer), **pattern** (spatial radiation characteristics), **bandwidth**, and **polarization** matching. Antenna performance is fundamental to [[Signal Processing]], spacecraft communications, ground station operations, and [[Radio Frequency (RF)]] systems. Performance directly impacts link budget, data rates, and system reliability.

## Historical Development

### Key Milestones
- **1895:** Guglielmo Marconi transmits first wireless signal; dipole antenna concept
- **1920s:** Yagi-Uda antenna development (directional improvement)
- **1940s:** Microwave antennas for radar; parabolic reflectors
- **1950s–1960s:** Satellite communications; high-gain antennas for deep space
- **1970s–1980s:** Array antennas; phased array technology
- **1990s–Present:** Phased arrays, MIMO antennas; adaptive beam steering

### Foundational Contributors
1. **Guglielmo Marconi (1874–1937):** Wireless communication pioneer
2. **Yagi Hidetsugu & Uda Shintaro (1920s):** Directional antenna design
3. **Karl Jansky (1905–1950):** Early cosmic radio observations
4. **Hendrik Colley Antennae (20th century):** Mathematical antenna theory
5. **John Kraus (1910–2005):** Horn antennas; helix antennas

## Key Performance Parameters

### Gain and Directivity

**Antenna gain** (power gain, G):
$$
G = \frac{\text{Power radiated in principal direction}}{\text{Power radiated by isotropic antenna}}
$$

**Measured in dB:**
$$
G_{\text{dBi}} = 10 \log_{10}(G)
$$

Where "dBi" = dB relative to isotropic radiator.

**Directivity (D):**
$$
D = \frac{\text{Power per unit solid angle (max direction)}}{\text{Average power per unit solid angle}}
$$

**Relationship:**
$$
G = \eta D
$$

Where $\eta$ is radiation efficiency (typically 0.9–1.0 for good antennas).

**Physical interpretation:**
- Isotropic (omnidirectional): G = 1 (0 dBi)
- Dipole: G ≈ 1.64 (2.15 dBi)
- Parabolic dish (30° beamwidth): G ≈ 50 (17 dBi) at X-band

### Beamwidth

**Half-power beamwidth (HPBW):**
$$
\theta_{-3\text{dB}} = \text{angular width where power = 50% of peak}
$$

**Relationship to gain (approximate):**
$$
G \approx \frac{4\pi}{\Omega_A}
$$

Where $\Omega_A$ is beam solid angle (steradians).

**For pencil beam:**
$$
\theta_{-3\text{dB}} \approx \frac{\lambda}{D}
$$

Where $\lambda$ is wavelength; $D$ is antenna diameter.

**Interpretation:**
- Narrower beam → higher gain
- Tracking accuracy requirement scales with beamwidth

### Sidelobe Level

**Sidelobe:** Radiation in directions other than main lobe

**Sidelobe level:**
$$
\text{SLL} = 10 \log_{10} \left(\frac{P_{\text{sidelobe}}}{P_{\text{main}}}\right) \text{ dB}
$$

**Typical:** -20 to -30 dB (sidelobe power 1/100 to 1/1000 of main lobe).

**Importance:**
- High SLL → interference from undesired directions
- Phased arrays, shaped reflectors designed to minimize

### Polarization

**Linear polarization:**
- Horizontal, vertical, ±45° (slant)
- Electric field vector orientation

**Circular polarization:**
- Right-hand circular (RHC), left-hand circular (LHC)
- Robustness to platform rotation

**Polarization loss:**
$$
L_p = 10 \log_{10}(\cos^2\theta)
$$

Where $\theta$ is angle between transmit and receive polarizations.

**Complete mismatch:** $L_p = -\infty$ (orthogonal polarizations; no coupling)

### Impedance and VSWR

**Characteristic impedance:** $Z_0 = 50$ Ω (standard), 75 Ω (video)

**Reflection coefficient:**
$$
\Gamma = \frac{Z_A - Z_0}{Z_A + Z_0}
$$

Where $Z_A$ is antenna impedance.

**Voltage Standing Wave Ratio (VSWR):**
$$
\text{VSWR} = \frac{1 + |\Gamma|}{1 - |\Gamma|}
$$

**Return loss:**
$$
\text{RL} = -20 \log_{10}(|\Gamma|) \text{ dB}
$$

**Good match:** VSWR < 2 (RL > 10 dB); power reflected < 11%.

### Efficiency

**Radiation efficiency:**
$$
\eta_{\text{rad}} = \frac{P_{\text{rad}}}{P_{\text{total}}} = \frac{P_{\text{rad}}}{P_{\text{rad}} + P_{\text{loss}}}
$$

**Loss mechanisms:**
- Dielectric losses (substrate, radome)
- Conductor losses (finite conductivity)
- Mismatch losses (impedance mismatch)

**Typical values:**
- Microstrip patch: 80–90%
- Waveguide horn: 95%+
- Slot antenna: 70–80%

## Antenna Types and Performance

| Type | Gain (dBi) | Beamwidth | Efficiency | Application |
|---|---|---|---|---|
| Dipole | 2.15 | 90° | 0.95 | VHF/UHF, portable |
| Monopole | 5.15 | 100° | 0.90 | Mobile, grounding |
| Yagi-Uda | 10–15 | 20–40° | 0.80 | UHF receiving, tracking |
| Horn | 10–20 | 10–30° | 0.98 | Satellite uplink |
| Parabolic dish | 30–50 | 1–10° | 0.90 | Deep space, Earth station |
| Patch/Microstrip | 5–9 | 60–100° | 0.85 | Mobile, satellite |
| Phased array | 20–40 | Variable | 0.80–0.95 | Beam steering |

## Connection to Other Concepts

1. **Connection to [[Signal Processing]]:**
   - Antenna performance determines signal quality
   - Gain and noise figure impact receiver [[Signal-to-noise Ratio]]

2. **Connection to [[Electromagnetic Fields]]:**
   - Antenna radiates electromagnetic energy
   - Field patterns determined by geometry, feed

3. **Connection to [[Communication Systems]]:**
   - Link budget depends on antenna gain
   - Data rate limited by SNR (antenna gain critical)

4. **Connection to [[Beamwidth]]:**
   - Directly related to antenna gain
   - Resolution and tracking accuracy depend

5. **Connection to [[Noise Temperature]]:**
   - Antenna noise figure contributes to system noise
   - Gain and directivity affect received noise power

## Link Budget Analysis

### Received Power

**Friis transmission equation:**
$$
P_r = P_t + G_t + G_r - L_p - L_f - L_a
$$

Where (in dB):
- $P_r$: Received power
- $P_t$: Transmitted power
- $G_t, G_r$: Transmit, receive antenna gains
- $L_p$: Path loss: $L_p = 20\log_{10}(4\pi d/\lambda)$ 
- $L_f$: Feeder losses (cable attenuation)
- $L_a$: Atmospheric absorption

**Path loss grows with frequency:**
- VHF (150 MHz): Low path loss
- X-band (10 GHz): High path loss
- Higher frequency trades better antenna performance (gain) against path loss

### Signal-to-Noise Ratio (SNR)

$$
\text{SNR} = \frac{P_r}{N} = \frac{P_r}{k_B T_n B}
$$

Where:
- $k_B$: Boltzmann constant
- $T_n$: System noise temperature (antenna + receiver)
- $B$: Bandwidth

**Antenna contribution:**
$$
T_{\text{ant}} = T_0 (1 - \eta) + T_{\text{sky}}
$$

Where $\eta$ is efficiency; $T_{\text{sky}}$ is sky noise (frequency-dependent).

**Improvement from directivity:**
- Focused beam (high gain) → collects noise from narrower sky region
- Reduces received thermal noise (sky noise outside beam attenuated)

## Practical Performance Considerations

### Ground Station Antennas

**Large parabolic dishes (10–40 m):**

**Performance:**
- Gain: 50–70 dBi (X-band)
- Tracking: Mechanical servo; ~0.05° accuracy
- SNR: Receiver limited (antenna noise low)

**Applications:** NASA DSN, ESA ESTRACK, space agencies worldwide

### Spacecraft Antennas

**Constraints:**
- Limited size/weight (launch vehicle constraints)
- Thermal/radiation environment
- Limited power budget

**Typical spacecraft configurations:**
- Low-gain antenna: Omnidirectional; for safe mode recovery
- Medium-gain antenna: Directional; primary communication
- High-gain antenna: Highly directional; narrow beam for efficiency

**Example (Cassini spacecraft):**
- High-gain antenna: 4 m diameter dish; 70 dBi gain at Ka-band
- Medium-gain antennas: 2 helices; 12 dBi gain (backup)
- Low-gain antenna: Omnidirectional dipole; 1 dBi gain

### Mobile/Portable Antennas

**Constraints:**
- Size limited by handset
- Omnidirectional (user mobility)
- Broadband operation (multiple frequencies)

**Performance:**
- Gain: -2 to 3 dBi (typically negative; lossy ground plane effects)
- Efficiency: 40–70% (absorption by user body)
- Polarization: Vertical, circular (user position variable)

## Measurement and Testing

### Gain Measurement Techniques

**Comparison method:**
- Compare unknown antenna to calibrated reference (gain-horn or dipole)
- Measure received power both antennas; compute gain ratio

**Substitution method:**
- Antenna under test at focus of reflector; measure radiation pattern
- Integrate pattern to compute directivity; combine with efficiency measurement

**Wheeler cap method:**
- Enclose antenna in large conductive enclosure
- Resonance frequency shift indicates efficiency

### Pattern Measurement

**Anechoic chamber:**
- RF-absorbing walls prevent reflections
- Rotate antenna under test; measure radiation pattern
- 3D pattern from multiple cuts

**Compact antenna test range (CATR):**
- Parabolic reflector creates plane wave at test zone
- Large antennas can be measured in small space

### Temperature and Environmental Testing

**Thermal cycling:** Verify gain, impedance stable across operating temperature range

**Vibration testing:** Aerospace antennas must survive launch vibration

**Humidity/salt-fog testing:** Corrosion resistance in maritime/coastal environments

## Advanced Topics

### Phased Array Antennas

**Electronically steerable beam:**

Array of elements with controllable phase:
$$
\mathbf{A}(\theta) = \sum_{n=0}^{N-1} a_n e^{-jknd\sin\theta}
$$

**Beam steering:** Phase shifters change beam direction without mechanical movement.

**Advantage:** Rapid beam scanning; multiple simultaneous beams.

**Application:** Radar, satellite communications with rapid tracking.

### MIMO Antennas

**Multiple-input, multiple-output:**

Array of antennas exploits multi-path fading → higher capacity.

**Channel capacity increase:** $C = B \log_2(1 + \text{SNR}/M)$ for M antennas.

**Challenges:** Antenna isolation (crosstalk between elements).

### Reconfigurable Antennas

**Tunable frequency:**
- Varactor diodes adjust resonance frequency
- Single antenna covers multiple bands

**Adaptable polarization:**
- Switch between linear and circular; H and V
- Maximize coupling to signal

## See Also

- [[Signal Processing]]
- [[Electromagnetics]]
- [[Beamwidth]]
- [[Signal-to-noise Ratio]]
- [[Noise Temperature]]
- [[Communication Theory]]
- [[Ground Station]]
- [[Spacecraft]]
- [[Radio Frequency (RF)]]
- [[Radiation Pattern]]

---
title: Alpha Particle
tags:
  - nuclear physics
  - radiation
  - quantum mechanics
  - particle physics
---

# Alpha Particle

## Formal Definition

An **alpha particle** (α-particle or α-ray) is a helium-4 nucleus consisting of two protons and two neutrons bound together, carrying a positive charge of +2e (double the elementary charge). It is emitted as [[Radiation|radiation]] from the nuclei of heavy elements during **alpha decay**, a form of radioactive decay where unstable nuclei reduce mass number by 4 and atomic number by 2. Alpha particles are one of the three primary forms of nuclear radiation (alongside beta particles and gamma rays) and are significant in [[Nuclear Energy]], radiation protection, and [[Particle Physics]].

## Historical Development

### Key Milestones
- **1899:** Ernest Rutherford identifies three types of radiation (α, β, γ)
- **1909:** Rutherford's gold foil experiment; establishes nuclear model via α-scattering
- **1911:** Rutherford identifies alpha particles as helium nuclei
- **1920s:** Quantum tunneling explanation of alpha decay (Gamow, Condon, Gurney)
- **1938:** First artificial alpha-producing nuclear reaction
- **1940s–1950s:** Accelerators produce alpha particles; nuclear physics research
- **1980s–Present:** Alpha sources in smoke detectors, space probes; medical applications

### Foundational Contributors
1. **Ernest Rutherford (1871–1937):** Discovery and nuclear model validation
2. **George Gamow (1904–1968):** Quantum tunneling explanation of alpha decay
3. **Edward Condon (1902–1974):** Theoretical decay constant derivation
4. **Henry Moseley (1887–1915):** Atomic number determination via X-rays
5. **Marie Curie (1867–1934):** Early radioactivity research; alpha source identification

## Physical Properties

### Composition and Charge

**Alpha particle structure:**
$$
^4_2\text{He}^{2+}: \text{2 protons} + \text{2 neutrons}
$$

**Charge:**
$$
q_\alpha = +2e = 3.204 \times 10^{-19} \text{ C}
$$

**Mass:**
$$
m_\alpha = 4.0026 \text{ u} = 6.644 \times 10^{-27} \text{ kg}
$$

Where u = atomic mass unit.

**Binding energy per nucleon:**
$$
B/A \approx 7.07 \text{ MeV/nucleon}
$$

Extremely stable (high binding energy); reason for prominence in decay.

### Kinetic Energy in Decay

**Typical alpha decay energy:**
$$
Q = M_{\text{parent}} - M_{\text{daughter}} - M_\alpha = 4-9 \text{ MeV}
$$

**Kinetic energy distribution** (momentum conservation):
$$
T_\alpha = \frac{m_{\text{daughter}}}{m_{\text{daughter}} + m_\alpha} Q \approx \frac{A-4}{A} Q
$$

For heavy nuclei (A >> 4), alpha gets ~99% of energy; recoiling daughter nucleus receives ~1%.

**Example:** Uranium-238 decay:
$$
^{238}_{92}\text{U} \to ^{234}_{90}\text{Th} + ^4_2\text{He}
$$

$Q = 4.27$ MeV; $T_\alpha \approx 4.20$ MeV; $T_{\text{Th}} \approx 0.07$ MeV.

## Alpha Decay Mechanism

### Quantum Tunneling

**Classical picture:** Alpha particle confined by nuclear potential well.

**Energy barrier height:** Coulomb repulsion of 2 protons in daughter nucleus.

**Without quantum mechanics:** Alpha with E < V (barrier height) cannot escape.

**With quantum mechanics:** Nonzero probability of tunneling through barrier.

### Decay Constant and Half-Life

**Decay law:**
$$
N(t) = N_0 e^{-\lambda t}
$$

**Half-life relation:**
$$
T_{1/2} = \frac{\ln 2}{\lambda} = 0.693 / \lambda
$$

**Geiger-Nuttal law** (empirical):
$$
\log \lambda = a + b \log E_\alpha
$$

Constants $a, b$ depend on parent nucleus.

**Gamma constant varies:**
- Fast decay (seconds): $T_{1/2} \sim 1$ s
- Slow decay (billions of years): $T_{1/2} \sim 10^9$ yr

**Examples:**
- Radon-222: $T_{1/2} = 3.8$ days (relatively fast)
- Uranium-238: $T_{1/2} = 4.5 \times 10^9$ years (very slow)
- Americium-241: $T_{1/2} = 432.2$ years (practical source)

### Tunneling Probability

**Transmission coefficient (approximate):**
$$
P \approx \exp\left(-\frac{2\pi \eta}{\ln(2\eta + \sqrt{4\eta^2 + 1})}\right)
$$

Where $\eta = Z_1 Z_2 e^2 / (2 T_\alpha)$ (Coulomb parameter).

**Physical insight:** Decay rate extremely sensitive to energy; small changes in Q cause exponential changes in half-life.

## Detection and Measurement

### Ionization in Matter

**Alpha particles highly ionizing:**

Heavy, slow-moving; intense Coulomb interaction with electrons along path.

**Energy loss (Bethe-Bloch formula):**
$$
-\frac{dE}{dx} = \frac{4\pi n e^4 Z^2}{m_e v^2} \ln\left(\frac{2m_e v^2}{I}\right)
$$

Where:
- $n$: electron density
- $Z$: alpha charge (+2)
- $v$: alpha velocity
- $I$: mean ionization potential

**Range in air (empirical):**
$$
R(\text{cm}) = 0.31 E^{1.5} \quad (E \text{ in MeV}, } 4 < E < 7)
$$

Typical range: 3–5 cm in air at 1 atm; ~0.05 mm in solid material.

### Detection Methods

**Ionization chambers:**
- Alpha ionizes gas; collected electrons measured
- Excellent energy resolution (~0.05 MeV)
- Standard technique

**Scintillation detectors:**
- Alpha hits phosphor; light pulse detected by photomultiplier
- Fast response; moderate energy resolution

**Solid-state detectors:**
- Alpha creates electron-hole pairs in silicon
- Excellent energy resolution; compact
- Common in aerospace instruments

**Nuclear track emulsions:**
- Alpha creates permanent damage trail
- Observable under microscope
- Historical method; still used for some applications

## Connection to Other Concepts

1. **Connection to [[Radiation]]:**
   - Alpha decay primary source of ionizing radiation
   - Distinct from beta (electrons) and gamma (photons)

2. **Connection to [[Nuclear Energy]]:**
   - Energy released in alpha decay from mass defect
   - Fundamental to nuclear power, weapons

3. **Connection to [[Quantum Mechanics]]:**
   - Tunneling effect central to understanding decay
   - Demonstrates wave-particle duality

4. **Connection to [[Particle Physics]]:**
   - Building block of nuclear structure
   - Particle interactions in detectors

5. **Connection to [[Atom]]:**
   - Determines element identity (atomic number)
   - Chemical properties changed by alpha decay

## Natural and Artificial Sources

### Natural Alpha Emitters

| Isotope | Half-life | Energy | Occurrence |
|---|---|---|---|
| U-238 | 4.5 Gy | 4.2 MeV | Ore deposits |
| U-235 | 704 My | 4.4 MeV | Natural uranium |
| Th-232 | 14 Gy | 4.1 MeV | Thorium ore |
| Ra-226 | 1600 y | 4.8 MeV | Radioactive decay series |
| Rn-222 | 3.8 d | 5.5 MeV | Gas from soil |

### Cosmic Alpha Particles

**Solar wind:** Continuous stream of alpha particles from Sun

**Cosmic rays:** High-energy alpha particles from deep space

**Magnetosphere interaction:** Earth's magnetic field deflects charged alphas

**Spacecraft vulnerability:** Galactic cosmic ray alphas can cause [[Single Event Upset|single-event upsets]] in electronics.

### Anthropogenic Sources

**Nuclear weapons testing:** Released alphas to atmosphere (1945–1980)

**Nuclear power plant accidents:** Chernobyl, Fukushima released alphas

**Medical applications:** Radiotherapy, diagnostic tracers

## Applications

### Smoke Detectors

**Americium-241 source:**
- Continuous alpha emission ionizes air chamber
- Smoke particles capture ions; circuit breaks; alarm triggers
- Reliability: Decades without replacement

**Safety note:** Very small amount (~0.9 μCi); closed source; radiation dose negligible.

### Radioisotope Power Sources

**Alpha decay heat used for power:**

Thermoelectric generators in space probes:
- Cassini probe: 32.8 kg Plutonium-238 (alpha emitter)
- Voyager probes: Radioisotope Thermoelectric Generators (RTGs)
- Mars rovers: RTGs provide heat and power

**Advantage:** Decades of operation independent of sunlight.

### Medical Applications

**Alpha-emitting pharmaceuticals:**
- Targeted alpha therapy (TAT): Deliver alphas directly to cancer cells
- Higher ionization → rapid cell killing
- Sparing surrounding tissue

**Examples:** Radium-223 for bone metastases; Bismuth-213 for leukemia.

### Neutron Generation

**Alpha-induced reactions produce neutrons:**
$$
^{238}\text{U} + \alpha \to ^{241}\text{Pu} + n
$$

**Application:** Portable neutron sources for soil analysis, non-destructive testing.

## Radiation Safety

### Biological Effects

**Alpha particle interactions:**
- Highly ionizing → high relative biological effectiveness (RBE ≈ 20)
- Short range → concentrated dose in small volume
- Blocked by skin; dangerous if ingested/inhaled

**Health impact:**
- External exposure: Minimal (stopped by skin, clothing, thin aluminum)
- Inhalation/ingestion: Severe (damages lungs, bone, organs)
- Radon-222 in homes → lung cancer (second leading cause after smoking)

### Shielding and Protection

**Effective shielding:**
- Paper, thin aluminum completely stop alpha
- Distance: Increase distance (intensity ∝ 1/r²)
- Ventilation: Remove radon gas; prevent accumulation

**Workplace limits:** OSHA limits breathing of alpha-emitting dust; air quality monitoring required.

## Advanced Topics

### Superheavy Element Decay

**Very heavy nuclei decay primarily via alpha emission:**

Allows exotic elements (Z > 92) to shed mass rapidly.

**Example:** Oganesson (Og, Z=118) decays to Livermorium (Lv, Z=116) via alpha.

### Cluster Decay

**Rare: emission of heavier clusters** (C-14, N-14, etc.)

**Probability:** Much lower than alpha; explains why alpha dominates.

### Resonant Tunneling

**In some cases, tunneling probability enhanced** by nuclear resonance.

**Physics:** Intermediate nuclear state increases transmission.

## See Also

- [[Radiation]]
- [[Nuclear Energy]]
- [[Quantum Mechanics]]
- [[Particle Physics]]
- [[Atom]]
- [[Radioactivity]]
- [[Beta Particle]]
- [[Gamma Particle]]
- [[Nuclear Fission]]
- [[Ionization]]

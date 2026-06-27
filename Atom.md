---
title: Atom
tags:
  - physics
  - chemistry
  - quantum mechanics
  - atomic structure
---
## Formal Definition

An **atom** is the smallest unit of matter that retains the chemical properties of an element. Composed of a dense nucleus (containing protons and neutrons) surrounded by a cloud of electrons occupying orbital shells, the atom is the fundamental building block of all macroscopic matter. Atomic structure obeys [[Quantum Mechanics|quantum mechanical]] principles; electrons occupy discrete energy levels rather than continuous orbits. Understanding atomic structure is essential to chemistry, materials science, nuclear physics, and [[Control Systems|spectroscopy]].

## Historical Development

### Key Milestones
- **440 BCE:** Leucippus and Democritus propose indivisible particles (atomos)
- **1808:** John Dalton develops atomic theory; elements made of identical atoms
- **1897:** J.J. Thomson discovers electron; proposes "plum pudding" model
- **1909:** Ernest Rutherford's alpha scattering experiment; discovers nucleus
- **1913:** Niels Bohr develops quantum mechanical atom model (hydrogen)
- **1926–1927:** Schrödinger, Heisenberg develop wave mechanics; orbital concept replaces Bohr orbits
- **1930s–Present:** Quantum electrodynamics (QED) perfects atomic calculations

### Foundational Contributors
1. **John Dalton (1766–1844):** Atomic theory foundation; indivisible atoms concept
2. **J.J. Thomson (1856–1940):** Electron discovery; charge-to-mass ratio
3. **Ernest Rutherford (1871–1937):** Nuclear model; alpha scattering
4. **Niels Bohr (1885–1962):** Quantum jumps; discrete energy levels
5. **Erwin Schrödinger (1887–1961):** Wave equation; orbital wavefunctions

## Atomic Structure

### Classical (Rutherford) Model

**Nucleus:**
- Protons: Charge +e, mass $m_p \approx 1.67 \times 10^{-27}$ kg
- Neutrons: Charge 0, mass $m_n \approx 1.68 \times 10^{-27}$ kg

**Electrons:**
- Charge −e, mass $m_e \approx 9.11 \times 10^{-31}$ kg
- $m_e / m_p \approx 1/1836$ (light compared to nucleons)

**Atom (neutral):**
- Number of protons = Number of electrons
- Atomic number $Z$ = Number of protons
- Mass number $A$ = Protons + Neutrons
- Notation: $^A_Z X$ (e.g., $^{12}_6 C$ = carbon-12)

### Quantum Mechanical Model

**Bohr model limitations:**
- Predicts only hydrogen spectrum accurately
- Fails for multi-electron atoms
- Violates uncertainty principle

**Schrödinger equation for hydrogen:**
$$
-\frac{\hbar^2}{2m_e}\nabla^2\psi + V(r)\psi = E\psi
$$

Where $V(r) = -\frac{e^2}{4\pi\epsilon_0 r}$ (Coulomb potential).

**Solutions:** Wavefunctions $\psi_{nlm}(r,\theta,\phi)$ characterized by quantum numbers:
- $n$ (principal): Energy level; $n = 1,2,3,\ldots$
- $\ell$ (orbital angular momentum): $\ell = 0,1,\ldots,n-1$ (s, p, d, f, $\ldots$)
- $m_\ell$ (magnetic): $m_\ell = -\ell, \ldots, 0, \ldots, +\ell$
- $m_s$ (spin): $m_s = \pm 1/2$

### Electron Orbitals

**Orbital ≠ Bohr orbit:**
- Orbital: Probability distribution for electron location; wavefunction $|\psi|^2$ = probability density
- Bohr orbit: Deterministic circular path (classical mechanics)

**Hydrogen energy levels:**
$$
E_n = -\frac{m_e e^4}{32\pi^2\epsilon_0^2\hbar^2 n^2} = -\frac{13.6 \text{ eV}}{n^2}
$$

**Energy differences (transitions):**
$$
\Delta E = E_f - E_i = h\nu = \frac{hc}{\lambda}
$$

Emitted/absorbed [[Radiation|photons]] correspond to specific energy transitions.

### Electron Configuration

**Aufbau principle:** Electrons fill orbitals in order of increasing energy.

**Orbital filling order:** 1s, 2s, 2p, 3s, 3p, 4s, 3d, 4p, $\ldots$

**Example (Iron, Z=26):**
$$
\text{Fe: } 1s^2 2s^2 2p^6 3s^2 3p^6 4s^2 3d^6
$$

**Valence electrons:** Outermost electrons; determine chemical reactivity.

**Pauli exclusion principle:** No two electrons in atom can have identical quantum numbers; maximum 2 per orbital (spin up/down).

## Atomic Nucleus

### Nuclear Composition

**Strong nuclear force:**
- Acts only over nuclear distances (~1 fm = $10^{-15}$ m)
- Attractive; binds protons and neutrons
- Short range; ~2 fm range

**Coulomb repulsion:**
- Protons repel each other electrostatically
- Increases with $Z^2$
- Overwhelms strong force for Z > 83 (lead region)

**Neutron-to-proton ratio:**
- Light nuclei: $N \approx Z$ (iron-56: 26p, 30n)
- Heavy nuclei: $N > Z$ (uranium-238: 92p, 146n)
- Excess neutrons stabilize against Coulomb repulsion

### Binding Energy and Mass Defect

**Mass defect:**
$$
\Delta m = Z m_p + N m_n - m_{\text{nucleus}}
$$

**Binding energy:**
$$
BE = \Delta m \cdot c^2 = [Z m_p + N m_n - m_{\text{nucleus}}]c^2
$$

**Binding energy per nucleon:**
$$
BE/A = \frac{BE}{Z + N}
$$

**Maximum:** Around iron-56 (~8.8 MeV/nucleon); indicates maximum stability.

**Fission:** Heavy nuclei (U-235, Pu-239) split; lighter nuclei have higher BE/nucleon; energy released.

**Fusion:** Light nuclei (deuterium, tritium) fuse; heavier products; energy released.

### Radioactive Decay

**Alpha decay ($\alpha = ^4_2He$):**
$$
^A_Z X \to ^{A-4}_{Z-2}Y + ^4_2He + Q
$$

Energy released $Q$; product nuclei recoil.

**Beta decay (electron emission $\beta^-$):**
$$
^A_Z X \to ^A_{Z+1}Y + e^- + \bar{\nu}_e + Q
$$

Neutron converts to proton; emits electron and antineutrino.

**Beta-plus decay ($\beta^+$):**
$$
^A_Z X \to ^A_{Z-1}Y + e^+ + \nu_e + Q
$$

Proton converts to neutron; emits positron and neutrino.

**Gamma decay ($\gamma$):**
$$
^A_Z X^* \to ^A_Z X + \gamma
$$

Excited nucleus emits high-energy photon; returns to ground state.

### Half-Life

**Exponential decay:**
$$
N(t) = N_0 e^{-\lambda t} = N_0 \left(\frac{1}{2}\right)^{t/t_{1/2}}
$$

Where:
- $\lambda$: Decay constant
- $t_{1/2}$: Half-life (time for N to drop to N₀/2)

**Relationship:**
$$
t_{1/2} = \frac{\ln(2)}{\lambda} \approx \frac{0.693}{\lambda}
$$

## Atomic Interactions

### Ionization Energy

**First ionization energy:** Energy to remove one electron.

$$
X \to X^+ + e^-
$$

**Trend:** Increases across period (left to right); jumps at noble gas completion.

**Physical basis:** Increasing nuclear charge; tighter binding.

### Electron Affinity

**Energy released when atom gains electron:**
$$
X + e^- \to X^-
$$

**Trend:** Varies irregularly; generally increase across period (except noble gases, halogens exceptional).

### Electronegativity

**Ability to attract electrons in bonding:**
- Pauling scale: 0.7 (cesium, least) to 4.0 (fluorine, most)
- Reflects ionic character of bonds
- [[Chemical Energy|determines bond polarity]]

### Ionization States

**Neutral atom:** Protons = Electrons

**Cation (positive ion):** Electrons < Protons; one or more lost

**Anion (negative ion):** Electrons > Protons; one or more gained

**Plasma:** Ionized gas; free electrons and ions.

## Atomic Spectroscopy

### Emission Spectrum

**Electron transitions from excited state ($n_i$) to lower state ($n_f$):**

$$
\Delta E = E_i - E_f = h\nu
$$

**Wavelength:**
$$
\lambda = \frac{hc}{E_i - E_f}
$$

**Hydrogen Balmer series** (transitions to n=2):
$$
\frac{1}{\lambda} = R_H \left(\frac{1}{4} - \frac{1}{n^2}\right), \quad n = 3,4,5,\ldots
$$

Where $R_H = 1.097 \times 10^7$ m$^{-1}$ (Rydberg constant).

**Produces visible lines:** H-alpha (656 nm red), H-beta (486 nm blue-green), etc.

### Absorption Spectrum

**Electrons transition from lower to higher energy level (absorb photon):**

$$
X + h\nu \to X^*
$$

**Dark lines** in continuous spectrum where photons absorbed.

**Application:** Identify elements in stellar atmospheres (Fraunhofer lines).

### Fine Structure

**Spin-orbit coupling:** Electron spin interacts with orbital magnetic field.

**Result:** Energy levels split into closely-spaced sublevels.

**Doublet pattern:** Two lines very close (e.g., sodium D-lines: 589.0 nm, 589.6 nm).

## Atomic Models and Approximations

### Bohr Model (Hydrogen)

**Quantized orbits:**
$$
L = m_e v r = n\hbar, \quad n = 1,2,3,\ldots
$$

**Energy levels:**
$$
E_n = -\frac{13.6 \text{ eV}}{n^2}
$$

**Success:** Exactly predicts hydrogen spectrum.

**Failure:** Multi-electron atoms; fine structure ignored; violates quantum uncertainty.

### Hartree-Fock Method (Multi-electron)

**Self-consistent field approach:**
- Each electron in average field of nucleus + other electrons
- Iterative solution: Guess orbitals → compute field → solve for new orbitals

**Accuracy:** ~1–5% for ground state energies.

**Application:** Calculate electron configurations; predict ionization energies; properties.

### Density Functional Theory (DFT)

**Modern computational method:**
- Electron density $\rho(\mathbf{r})$ primary variable (not complex wavefunctions)
- Exchange-correlation functional approximated
- Much faster than Hartree-Fock; good accuracy

**Application:** Materials simulation; band structure; reaction dynamics.

## Connection to Other Concepts

1. **Connection to [[Quantum Mechanics]]:**
   - Schrödinger equation governs atomic structure
   - Probability interpretation of wavefunctions

2. **Connection to [[Chemistry]]:**
   - Electron configuration determines chemical bonding
   - Valence electrons control reactivity

3. **Connection to [[Radiation|Radiation Physics]]:**
   - Spectral lines from transitions
   - Absorption/emission

4. **Connection to [[Materials Science]]:**
   - Atomic arrangements form solids
   - Band structure from overlapping orbitals

5. **Connection to [[Nuclear Physics]]:**
   - Nuclear composition; radioactive decay

## Atomic Scales and Characteristic Sizes

### Bohr Radius (Hydrogen Ground State)

$$
a_0 = \frac{4\pi\epsilon_0\hbar^2}{m_e e^2} \approx 0.53 \text{ Å} = 0.53 \times 10^{-10} \text{ m}
$$

**Typical atomic size:** 1–3 Å (0.1–0.3 nm)

### Fine Structure Constant

$$
\alpha = \frac{e^2}{4\pi\epsilon_0\hbar c} \approx 1/137
$$

**Characterizes:** Strength of electromagnetic interactions; perturbative parameter in QED.

## See Also

- [[Quantum Mechanics]]
- [[Nuclear Physics]]
- [[Atomic Spectroscopy]]
- [[Chemical Bonding]]
- [[Materials Science]]
- [[Electron Configuration]]
- [[Ionization]]
- [[Radiation]]
- [[Elementary Particles]]
- [[Thermodynamics|Thermal Properties]]

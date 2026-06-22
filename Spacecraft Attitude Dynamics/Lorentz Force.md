#SAD #TBD 
The **Lorentz force** is the combined force exerted on a **[[point charge]]** $q$ moving with velocity $\mathbf{v}$ through an **electromagnetic field**. It is a fundamental concept in **classical [[electromagnetism]]**, unifying the **[[electric force]]** and the **[[magnetic force]]** into a single expression. The Lorentz force governs the motion of charged particles in electric and magnetic fields and is a cornerstone of **electrodynamics**, **plasma physics**, and **accelerator physics**.

---

### **Mathematical Formulation**
The Lorentz force $\mathbf{F}$ acting on a point charge $q$ moving with velocity $\mathbf{v}$ in the presence of an **electric field** $\mathbf{E}$ and a **magnetic field** $\mathbf{B}$ is given by:
$$
\mathbf{F} = q (\mathbf{E} + \mathbf{v} \times \mathbf{B}),
$$
where:
- $q$ is the **electric charge** of the particle (in coulombs, C),
- $\mathbf{E}$ is the **electric field** (in volts per meter, V/m),
- $\mathbf{v}$ is the **[[Velocity]]** of the charge (in meters per second, m/s),
- $\mathbf{B}$ is the **magnetic field** (in teslas, T),
- $\times$ denotes the **cross product**.

#### **Components of the Lorentz Force**:
1. **Electric Force ($q\mathbf{E}$)**:
   - Acts in the direction of the electric field $\mathbf{E}$.
   - Responsible for acceleration (or deceleration) of the charge parallel to $\mathbf{E}$.
   - Work done by this component changes the **[[Kinetic Energy]]** of the particle.

2. **Magnetic Force ($q \mathbf{v} \times \mathbf{B}$)**:
   - Acts perpendicular to both the velocity $\mathbf{v}$ and the magnetic field $\mathbf{B}$ (given by the right-hand rule).
   - Does **no work** on the particle (since it is always perpendicular to $\mathbf{v}$), so it **does not change the [[Kinetic Energy]]** of the particle.
   - Causes the particle to follow a **curved trajectory** (e.g., circular or helical motion in uniform fields).

---

### **Key Properties**
1. **Work and Energy**:
   - The **magnetic component** of the Lorentz force does no work because it is always perpendicular to the velocity of the particle. Thus, the **total [[Kinetic Energy]]** of the particle is changed only by the electric field.
   - Mathematically, the power $P$ delivered by the Lorentz force is:
     $
     P = \mathbf{F} \cdot \mathbf{v} = q \mathbf{E} \cdot \mathbf{v},
     $
     since $\mathbf{v} \times \mathbf{B} \cdot \mathbf{v} = 0$.

2. **Trajectories in Uniform Fields**:
   - In a **uniform [[Magnetic Field]]** $\mathbf{B}$ (with $\mathbf{E} = \mathbf{0}$), a charged particle moves in a **circular or helical trajectory** with:
     - **Cyclotron frequency**: $\omega_c = \frac{|q| B}{m}$ (for motion perpendicular to $\mathbf{B}$),
     - **Larmor radius**: $r_L = \frac{m v_\perp}{|q| B}$,
     where $m$ is the mass of the particle, $v_\perp$ is the velocity component perpendicular to $\mathbf{B}$, and $B = \|\mathbf{B}\|$.
   - In **crossed electric and magnetic fields** (e.g., $\mathbf{E} \perp \mathbf{B}$), the particle follows a **trochoidal or drift motion**.

3. **Relativistic Formulation**:
   - In **special relativity**, the Lorentz force is generalized using the **electromagnetic field tensor** $F^{\mu\nu}$:
     $$
     \frac{dp^\mu}{d\tau} = q F^{\mu\nu} u_\nu,
     $$
     where $p^\mu$ is the **four-momentum**, $\tau$ is the **proper time**, and $u_\nu$ is the **four-velocity** of the particle.

---

### **Applications**
1. **Particle Accelerators**:
   - The Lorentz force is used to **confine and steer** charged particles (e.g., electrons, protons) in **cyclotrons**, **synchrotrons**, and **tokamaks**.
   - Example: In a **cyclotron**, a perpendicular magnetic field causes particles to spiral outward as they gain energy from an electric field.

2. **Plasma Physics**:
   - Governs the motion of charged particles in **plasmas** (e.g., solar wind, fusion reactors).
   - Key to understanding **magnetic confinement** in devices like **tokamaks** and **stellarators**.

3. **Electromagnetic Devices**:
   - **Mass spectrometers**: Separate ions by their mass-to-charge ratio using magnetic fields.
   - **[[Hall effect]] sensors**: Measure magnetic fields by detecting the Lorentz force on current-carrying charges.

4. **Astrophysics**:
   - Explains the motion of **cosmic rays** in galactic magnetic fields.
   - Describes the **synchrotron radiation** emitted by relativistic electrons spiraling in magnetic fields (e.g., in pulsars or active galactic nuclei).

5. **Everyday Technology**:
   - **Electric motors**: The Lorentz force acts on current-carrying wires in magnetic fields, producing torque.
   - **Cathode ray tubes (CRTs)**: Electrons are deflected by magnetic fields to create images on screens.

---

### **Derivation from Maxwell’s Equations**
The Lorentz force can be derived from the **Maxwell equations** and the **Lorentz force law** for a distribution of charges and currents. For a continuous charge distribution with charge density $\rho$ and current density $\mathbf{J}$, the force density is:
$$
\mathbf{f} = \rho \mathbf{E} + \mathbf{J} \times \mathbf{B}.
$$

---

### **Historical Context**
- Named after **Hendrik Lorentz**, who formalized the expression in 1895 as part of his work on **electron theory**.
- The force was implicitly described earlier in the works of **James Clerk Maxwell** and **André-Marie Ampère**.
- Played a crucial role in the development of **special relativity** by Albert Einstein, as it is consistent with the **principle of relativity** for electromagnetic phenomena.

---

### **Suggested Additions for Your Note**
1. **Links**:
   - [[Maxwell's Equations]] (foundation of [[electromagnetism]])
   - [[Special Relativity]] (relativistic generalization)
   - [[Cyclotron Motion]] (trajectories in magnetic fields)
   - [[Hall Effect]] (application in sensors)
2. **Diagrams**:
   - Trajectory of a charged particle in uniform $\mathbf{E}$ and $\mathbf{B}$ fields.
   - Right-hand rule for the magnetic force component.
3. **Examples**:
   - Derivation of the cyclotron frequency.
   - Application in a mass spectrometer.
4. **Tags**: `#electromagnetism`, `#classical-physics`, `#plasma-physics`, `#relativity`.

---
Would you like me to expand on any specific aspect, such as relativistic effects, numerical simulations, or experimental demonstrations?
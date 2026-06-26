#Orbital-Mechanics #DONE

### **Formal Definition**

**Gravitational Potential Energy (U)**

Gravitational potential energy is the energy stored in a system of masses by virtue of their spatial configuration within a gravitational field. It represents the [[Work]] that must be done by an external agent against the [[Conservative Force]] gravitational force to assemble the system from a reference configuration where the masses are infinitely separated, or conversely, the work that can be extracted by the gravitational force ([[Newton’s Universal Law of Gravitation]])as the system moves to that reference configuration.

### **Mathematical Formulation**

#### **1. For Two Point Masses**

The gravitational potential energy $U$ between two point masses $m_1$ and $m_2$ separated by a distance $r$ is:

$$
U(r) = -G \frac{m_1 m_2}{r}
$$

Where:
*   $G$ is the Universal Gravitational Constant.
*   The **negative sign** is fundamental and indicates that the force is **attractive**. The potential energy is defined to be zero ($U = 0$) when the separation is infinite ($r \to \infty$).

#### **2. Relation to Gravitational Force**

The gravitational force is the negative gradient of the potential energy. For a spherically symmetric field, this reduces to:

$$
\vec{F}_g = -\nabla U \quad \Rightarrow \quad F_g = -\frac{dU}{dr} = -G \frac{m_1 m_2}{r^2}
$$

This confirms that the force is the spatial rate of change of the [[potential energy]].

#### **3. For a System of Multiple Particles**

The total gravitational potential energy is the sum over all unique pairs:

$$
U_{\text{total}} = -G \sum_{i=1}^{N} \sum_{j>i}^{N} \frac{m_i m_j}{r_{ij}}
$$

Where $r_{ij}$ is the distance between mass $m_i$ and mass $m_j$.

#### **4. In a Uniform Gravitational Field (Near-Earth Approximation)**

For an object of mass $m$ at a height $h$ above a planetary surface, where the gravitational field $g$ can be considered constant, the potential energy is:

$$
U(h) = m g h
$$

**Important Note:** This is an approximation derived from the general form. The full expression, with the Earth's radius $R_E$ and mass $M_E$, is $U(r) = -G\frac{M_E m}{r}$, where $r = R_E + h$. The change in potential energy $\Delta U$ between two points near the surface is approximately $mg\Delta h$, which is why the simplified form is so useful.

### **Detailed Explanation and Key Principles**

1.  **Reference Point (Zero Potential):**
    *   The general formula $U = -G\frac{m_1 m_2}{r}$ defines the zero point of potential energy at an **infinite separation**. This is the most physically meaningful reference for an inverse-square force law, as it is the only point where the interaction truly ceases.
    *   In the near-Earth approximation $U = mgh$, the zero point is arbitrarily set at the planet's surface ($h=0$). This is valid because the *change* in potential energy ($\Delta U$), which is the physically significant quantity, is the same in both formulations for small $h$.

2.  **Why the Negative Sign?**
    *   **Bound Systems:** A negative total energy (sum of kinetic and potential) indicates a **bound system** (e.g., planets in orbit, satellites). To separate the masses to infinity (where $U=0$), positive work must be done *on* the system, increasing its energy to zero.
    *   **Work Interpretation:** The potential energy function $U(r) = -G\frac{m_1 m_2}{r}$ directly gives the work $W$ done *by the gravitational force* when a mass moves from a distance $r$ to infinity: $W = U(r) - U(\infty) = U(r) - 0$. Since this work is positive (the force and displacement are in the same direction for an attracting body moving away), the potential energy must be negative at finite $r$.

3.  **Conservatism and Path Independence:**
    *   Gravitational potential energy is a form of **[[Potential Energy]]** because the gravitational force is **conservative**. The work done in moving a mass between two points in a gravitational field depends *only on the positions of those points*, not on the path taken.
    *   This allows for the powerful application of **Conservation of Mechanical Energy**:
        $$
        E_{\text{mech}} = K + U = \text{constant}
        $$
        Where $K$ is the [[Kinetic Energy]]. For an orbiting body, this is the foundation of the [[Energy Law (Vis-Viva Equation)]].

### **Key Implications and Significance**

*   **Orbital Mechanics:** The total energy $E = \frac{1}{2}mv^2 - G\frac{Mm}{r}$ determines the type of orbit (elliptical, parabolic, hyperbolic), as previously discussed.
*   **[[Escape Velocity]]:** The minimum speed needed to escape a gravitational field from a distance $r$ is found by setting the total energy to zero (the condition for a parabolic trajectory):
    $$
    \frac{1}{2}mv_{\text{esc}}^2 - G\frac{Mm}{r} = 0 \quad \Rightarrow \quad v_{\text{esc}} = \sqrt{\frac{2GM}{r}}
    $$
*   **Potential Well:** The negative potential energy curve forms a "well." Objects are trapped in this well unless they acquire enough [[Kinetic Energy]] to reach its "rim" at $r \to \infty$.

In summary, **gravitational potential energy** is the configuration-dependent energy arising from the relative positions of masses in a gravitational field. Its rigorous definition, $U(r) = -G\frac{m_1 m_2}{r}$, with zero at infinity, is fundamental to understanding bound systems, orbital dynamics, and energy conservation in celestial mechanics.
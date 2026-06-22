#SAD #TBD

### **1. Formal Definition of Solar Radiation Pressure**

**Solar Radiation Pressure (SRP)** is a non-conservative perturbation force acting on a body in space due to the transfer of momentum from incident photons of solar radiation. Unlike gravitational forces, which are a function of mass, SRP is a function of the illuminated surface area and the optical properties of the spacecraft surface.

In the context of **[[attitude]] dynamics**, SRP is significant for two primary reasons:
1.  **Orbital Perturbation:** It induces forces that alter the orbit of a spacecraft, an effect particularly pronounced for objects with high area-to-mass ratios (e.g., geostationary satellites, solar sails, or debris).
2.  **Disturbance [[Torque]]:** Since the force acts at the center of pressure of the illuminated surface, and this point rarely coincides with the spacecraft's [[Center of Mass]], it generates a disturbance [[torque]]. This [[torque]] must be compensated for by the **[[attitude]] control system (ACS)** to maintain the desired spacecraft orientation.

---

### **2. Calculation of Solar Radiation Pressure Force**

The calculation is derived from the physics of [[photon]] momentum. The force arises from three [[photon]]-surface interactions: [[absorption]], [[specular reflection]], and [[Diffuse Reflection]].

#### **A. Fundamental Solar Radiation Pressure**

The fundamental [[Pressure]] $p_s$ exerted by solar [[Photon]]s on a perfectly absorbing, flat surface oriented normal to the [[Sun]] at a distance of 1 [[Astronomical Unit]] is given by:

$$
p_s = \frac{S}{c}
$$

Where:
*   $S$ is the **solar constant**, approximately **1361 W/m²** (the total solar irradiance at 1 AU).
*   $c$ is the **speed of light** in a vacuum ($2.998 \times 10^8$ m/s).

Thus,
$$
p_s \approx \frac{1361}{2.998 \times 10^8} \approx 4.54 \times 10^{-6} \, \text{N/m}^2 \, (\text{or Pa})
$$

This value $p_s$ is the baseline solar pressure. To account for the actual Sun-spacecraft distance $r$ (in AU), it is scaled by $\frac{1}{r^2}$.

#### **B. General Force Vector on a Flat Plate**

The total SRP force on a spacecraft is the [[Vector]] sum of the forces on all its illuminated surfaces. For a single flat plate, the force is calculated by considering its orientation and surface properties.

Let us define:
*   $\mathbf{\hat{s}}$: Unit vector pointing *from* the spacecraft *to* the Sun.
*   $\mathbf{\hat{n}}$: Unit normal vector of the surface (pointing outward from the spacecraft).
*   $A$: Illuminated surface area.
*   $\theta$: Angle of incidence, satisfying $\cos\theta = \mathbf{\hat{n}} \cdot \mathbf{\hat{s}}$. (If $\cos\theta < 0$, the surface is not illuminated).
*   $\rho$: Specular reflectance coefficient (fraction of incident photons specularly reflected).
*   $\alpha$: Absorptance coefficient (fraction of incident photons absorbed).
*   $\delta$: Diffuse reflectance coefficient (fraction of incident photons diffusely reflected).

By [[Conservation of Energy]]: $\rho + \alpha + \delta = 1$.

The total SRP force vector $\mathbf{F}_{SRP}$ on the flat plate is given by:

$$
\mathbf{F}_{SRP} = -p_s \frac{A}{r^2} \cos\theta \left[ (1 - \rho_s) \, \mathbf{\hat{s}} + 2 \left( \rho_s \cos\theta + \frac{1}{3} \delta \right) \mathbf{\hat{n}} \right]
\quad \text{for} \quad \cos\theta \geq 0
$$

$$
\mathbf{F}_{SRP} = \mathbf{0} \quad \text{for} \quad \cos\theta < 0
$$

**Term-by-Term Explanation:**
1.  **$-p_s \frac{A}{r^2} \cos\theta$**: This is the magnitude of the incident momentum flux. The $\cos\theta$ term accounts for the projected area normal to the Sun ($A_\perp = A \cos\theta$).
2.  **$(1 - \rho_s) \, \mathbf{\hat{s}}$**: This term represents the force due to absorption and the non-ideal specular component. The negative sign indicates it is in the direction opposite to the incoming photons (a "push" from the Sun).
    *   Absorption ($\alpha$): The [[photon]]'s momentum is transferred to the spacecraft, resulting in a force in the $-\mathbf{\hat{s}}$ direction.
    *   The term $(1 - \rho_s)$ is often simplified in some models, but rigorously, it should align with the coefficients defined above.
3.  **$2 \left( \rho_s \cos\theta + \frac{1}{3} \delta \right) \mathbf{\hat{n}}$**: This term represents the force due to reflection.
    *   **Specular Reflection ($\rho$)**: Photons are reflected like a mirror. The change in momentum is twice the normal component, resulting in a force along the surface normal $\mathbf{\hat{n}}$. The factor $2\rho \cos\theta$ captures this.
    *   **[[Diffuse Reflection]] ($\delta$)**: Photons are reflected isotropically (equally in all directions). The net force from this isotropic "Lambertian" reflection is along the surface normal $\mathbf{\hat{n}}$, with the factor $\frac{1}{3} \delta$ being the result of integrating the momentum transfer over a hemisphere.

A common and simpler model uses a single **reflectivity coefficient $C_r$** (also called the *radiation pressure coefficient*), where $C_r \approx 1 + \rho_s$. The force is then modeled as:

$$
\mathbf{F}_{SRP} = -p_s \frac{A_\perp}{r^2} C_r \, \mathbf{\hat{s}}
$$

Where $A_\perp$ is the projected area. While simpler, this model loses the ability to calculate the [[torque]] component normal to the Sun-line and is less accurate for detailed [[attitude]] analysis.

#### **C. Force and [[Torque]] on a Complex Spacecraft**

For a full **[[attitude]] dynamics** simulation, the total force $\mathbf{F}_{SRP,total}$ is the sum of forces on all $N$ illuminated surfaces:

$$
\mathbf{F}_{SRP,total} = \sum_{i=1}^{N} \mathbf{F}_{SRP_i}
$$

The resulting **disturbance [[torque]]** $\mathbf{\tau}_{SRP}$ about the spacecraft's [[Center of Mass]] (COM) is:

$$
\mathbf{\tau}_{SRP} = \sum_{i=1}^{N} (\mathbf{r}_{cp_i} - \mathbf{r}_{com}) \times \mathbf{F}_{SRP_i}
$$

Where:
*   $\mathbf{r}_{cp_i}$ is the position vector of the center of pressure for the $i$-th surface.
*   $\mathbf{r}_{com}$ is the position vector of the spacecraft's [[Center of Mass]].

This [[torque]] is a critical input for the design of the [[attitude]] control system.

### **Summary**

In formal terms, **solar radiation pressure is a momentum transfer phenomenon** that manifests as a surface-force perturbation. Its accurate calculation is essential for predicting long-term orbital evolution and for designing robust [[attitude]] control systems, especially for large, high-area spacecraft like modern communication satellites and space telescopes.
#Space-Structures #TBD 

### **Formal Definition of Hooke's Law**

Hooke's Law is a principle of physics that states that the force needed to extend or compress a spring by some distance is *proportional* to that distance. Formally, it describes the linear-elastic behavior of springs and other elastic bodies within their proportional limit.

The essential premise is that the deformation (strain) of an elastic material is directly proportional to the applied force (stress). This relationship was first stated by the British scientist Robert Hooke in 1676 as a Latin anagram, "ceiiinosssttuv," which he later revealed as "**Ut tensio, sic vis**" – meaning "As the extension, so the force."

---

### **1. The Scalar Form (For Ideal Springs)**

This is the most common and simplest form, applicable to an ideal spring in one dimension.

#### **Equation:**

$$ F = -k x $$

Where:
*   $F$ is the restoring force exerted by the spring (in Newtons, N).
*   $k$ is the **spring constant** or **force constant** (in Newtons per meter, N/m). It is a measure of the spring's stiffness. A higher $k$ indicates a stiffer spring.
*   $x$ is the displacement from the spring's equilibrium or relaxed position (in meters, m).
*   The **negative sign** indicates that the restoring force $F$ always acts in the direction *opposite* to the displacement $x$. For example, if you stretch the spring ($x$ is positive), the force pulls back ($F$ is negative).

#### **Graphical Representation:**

When the force applied to the spring is plotted against the displacement, Hooke's Law is represented by a straight line through the origin. The slope of this line is equal to the spring constant $k$.



The region where this linear relationship holds is called the **proportional limit**.

---

### **2. The General Tensor Form (For Continuous Elastic Materials)**

For general three-dimensional continuous materials (like a block of metal or a beam), Hooke's Law is generalized to relate the **[[Stress Tensor]] tensor** ($\sigma$) to the **[[strain]] tensor** ($\varepsilon$).

#### **Equation:**

$$ \boldsymbol{\sigma} = \mathbf{C} : \boldsymbol{\varepsilon} \quad \text{or} \quad \sigma_{ij} = C_{ijkl} \, \varepsilon_{kl} $$

Where:
*   $\boldsymbol{\sigma}$ is the Cauchy [[stress tensor]] (describing internal forces).
*   $\boldsymbol{\varepsilon}$ is the infinitesimal strain tensor (describing deformation).
*   $\mathbf{C}$ is the fourth-order **stiffness tensor**, which contains the 81 elastic moduli of the material. The colon (\(:\)) denotes the double dot product.
*   The indices $i, j, k, l$ run from 1 to 3.

This form accounts for the fact that a force applied in one direction can cause deformation in other directions (e.g., squeezing a material can cause it to expand sideways, which is the Poisson effect).

---

### **3. Simplifications for Isotropic and Linear Elastic Materials**

For isotropic materials (whose properties are identical in all directions, like most metals), the stiffness tensor simplifies significantly. The relationship can be expressed using two fundamental constants: **[[Young's Modulus]] ($E$)** and the **[[Shear Modulus]] ($G$)** or **[[Poisson's Ratio]] ($\nu$)**.

#### **a) Uniaxial Loading ([[Young's Modulus]]):**

This is the most common engineering simplification, directly analogous to the spring equation.

$$ \sigma = E \, \varepsilon $$

Where:
*   $\sigma = F/A$ is the uniaxial stress (Force per unit area).
*   $\varepsilon = \Delta L / L_0$ is the axial strain (change in length per original length).
*   $E$ is **[[Young's Modulus]]** (or the Elastic Modulus), a material-specific measure of stiffness (in Pascals, Pa). It is the macroscopic equivalent of the spring constant $k$.

> **Relationship to Scalar Form:** Substituting the definitions, $(F/A) = E \, (\Delta L / L_0)$, which can be rearranged to $F = (EA / L_0) \, \Delta L$. This shows that for a bar of material, the effective "spring constant" is $k = EA / L_0$.

#### **b) Shear Loading:**

For shear stresses and strains, the relationship is:

$$ \tau = G \gamma $$

Where:
*   $\tau$ is the [[Shear Stress]].
*   $\gamma$ is the shear strain.
*   $G$ is the **[[Shear Modulus]]**.

---

### **Limitations and the Elastic Limit**

Hooke's Law is not universally valid. It is an approximation that holds only within the **proportional limit** of the material.

*   **Proportional Limit:** The point on the stress-strain curve where the linear relationship ceases.
*   **Elastic Limit:** The maximum stress a material can withstand without permanent deformation. For many materials, it is very close to the proportional limit.
*   **Yield Point:** Beyond the elastic limit, the material begins to deform plastically (permanently). The stress may no longer increase linearly with strain, and upon unloading, the material will not return to its original shape.

The following diagram illustrates these concepts on a typical stress-strain curve for a ductile metal:



Once the yield point is passed, Hooke's Law is no longer applicable.

### **Summary of Key Points**

*   **Core Principle:** Within the elastic limit, stress is proportional to strain.
*   **Scalar Form:** $F = -k x$ (for ideal springs).
*   **General Form:** $\boldsymbol{\sigma} = \mathbf{C} : \boldsymbol{\varepsilon}$ (for anisotropic materials).
*   **Common Engineering Form:** $\sigma = E \varepsilon$ (for isotropic materials under uniaxial load).
*   **Limitation:** It is only valid up to the material's proportional limit. Beyond this, plastic deformation occurs, and the law fails.
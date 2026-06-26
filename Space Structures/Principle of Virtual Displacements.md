#Space-Structures 

### Formal Definition of the Principle of Virtual Displacements

The **Principle of Virtual Displacements** (PVD), also known as the **Principle of [[Virtual Work]]**, states:

> **A deformable body is in equilibrium if, and only if, the total [[virtual work]] done by all internal and external forces is zero for any arbitrary, infinitesimal, kinematically admissible [[virtual displacement]].**

In mathematical terms:

$$
\boxed{\delta W_{\text{internal}} + \delta W_{\text{external}} = 0 \quad \text{for all } \delta u^i \in \mathcal{V}}
$$

where $\mathcal{V}$ is the space of all kinematically admissible [[virtual displacement]] fields.

---

#### **The Principle**
Substituting these definitions, the Principle of [[Virtual Displacement]]s in its most common form is:

$$
\boxed{-\int_{\Omega} \sigma^{ij} \, \delta \varepsilon_{ij} \, d\Omega + \int_{\Omega} f^i \, \delta u_i \, d\Omega + \int_{\partial \Omega_T} T^i \, \delta u_i \, dS = 0}
$$

or, more conventionally:

$$
\boxed{\int_{\Omega} \sigma^{ij} \, \delta \varepsilon_{ij} \, d\Omega = \int_{\Omega} f^i \, \delta u_i \, d\Omega + \int_{\partial \Omega_T} T^i \, \delta u_i \, dS}
$$

**Interpretation:** The internal [[virtual work]] equals the external [[virtual work]] for any kinematically admissible virtual [[Displacement Field]].

---

### 2. The Virtual [[Strain]]-[[Displacement]] Relationship

The virtual strain $\delta \varepsilon_{ij}$ is derived from the [[virtual displacement]] $\delta u^i$ using the same kinematic relations as the real strain. For infinitesimal deformations:

$$
\boxed{\delta \varepsilon_{ij} = \frac{1}{2} (\delta u_{i,j} + \delta u_{j,i})}
$$

This is a crucial step, as it enforces compatibility on the virtual [[Displacement Field]].

---

### 3. Derivation from the [[Equilibrium Equations]] ([[Strong Form (Pointwise Form)]])

The power of the PVD is that it is equivalent to the [[Strong Form (Pointwise Form)]] of equilibrium. We can derive it directly.

Start with the [[Equilibrium Equations]] and traction boundary conditions:
1.  $\sigma^{ij}_{,j} + f^i = 0 \quad \text{in } \Omega$
2.  $\sigma^{ij} n_j = T^i \quad \text{on } \partial \Omega_T$

Now, take the equilibrium equation, multiply by an arbitrary [[virtual displacement]] $\delta u_i$, and integrate over the domain:

$$
\int_{\Omega} (\sigma^{ij}_{,j} + f^i) \, \delta u_i \, d\Omega = 0
$$

$$
\int_{\Omega} \sigma^{ij}_{,j} \, \delta u_i \, d\Omega + \int_{\Omega} f^i \, \delta u_i \, d\Omega = 0
$$

Apply the product rule to the first term:
$$
(\sigma^{ij} \, \delta u_i)_{,j} = \sigma^{ij}_{,j} \, \delta u_i + \sigma^{ij} \, \delta u_{i,j}
$$

Rearranging:
$$
\sigma^{ij}_{,j} \, \delta u_i = (\sigma^{ij} \, \delta u_i)_{,j} - \sigma^{ij} \, \delta u_{i,j}
$$

Substitute back:
$$
\int_{\Omega} \left[ (\sigma^{ij} \, \delta u_i)_{,j} - \sigma^{ij} \, \delta u_{i,j} \right] d\Omega + \int_{\Omega} f^i \, \delta u_i \, d\Omega = 0
$$

Apply the [[divergence]] theorem to the first term:
$$
\int_{\Omega} (\sigma^{ij} \, \delta u_i)_{,j} \, d\Omega = \oint_{\partial \Omega} \sigma^{ij} \, \delta u_i \, n_j \, dS
$$

The boundary $\partial \Omega$ can be split into $\partial \Omega_u$ (where $\delta u_i = 0$) and $\partial \Omega_T$ (where $\sigma^{ij} n_j = T^i$). Therefore, the boundary integral reduces to:
$$
\oint_{\partial \Omega} \sigma^{ij} \, \delta u_i \, n_j \, dS = \int_{\partial \Omega_T} T^i \, \delta u_i \, dS
$$

Now, note that $\sigma^{ij} \, \delta u_{i,j} = \sigma^{ij} \, \delta \varepsilon_{ij}$ because the [[stress tensor]] $\sigma^{ij}$ is symmetric, and thus $\sigma^{ij} \delta u_{i,j} = \sigma^{ij} \frac{1}{2}(\delta u_{i,j} + \delta u_{j,i}) = \sigma^{ij} \delta \varepsilon_{ij}$.

Putting it all together:
$$
\int_{\partial \Omega_T} T^i \, \delta u_i \, dS - \int_{\Omega} \sigma^{ij} \, \delta \varepsilon_{ij} \, d\Omega + \int_{\Omega} f^i \, \delta u_i \, d\Omega = 0
$$

Rearranging gives the final form:
$$
\int_{\Omega} \sigma^{ij} \, \delta \varepsilon_{ij} \, d\Omega = \int_{\Omega} f^i \, \delta u_i \, d\Omega + \int_{\partial \Omega_T} T^i \, \delta u_i \, dS
$$

This derivation proves the equivalence between the [[Strong Form (Pointwise Form)]] (PDEs) and the [[Weak Form (Variational Form)]] (PVD).

---

### 4. Relationship to the [[Variational Principle]]

The Principle of Virtual Displacements is essentially the **first variation of the total [[Potential Energy]] [[Functional]]**.

Recall the total potential energy:
$$
\Pi[u_i] = \int_{\Omega} \frac{1}{2} C^{ijkl} \varepsilon_{ij} \varepsilon_{kl} \, d\Omega - \int_{\Omega} f^i u_i \, d\Omega - \int_{\partial \Omega_T} T^i u_i \, dS
$$

Taking its first variation $\delta \Pi$:
$$
\delta \Pi = \int_{\Omega} C^{ijkl} \varepsilon_{kl} \, \delta \varepsilon_{ij} \, d\Omega - \int_{\Omega} f^i \, \delta u_i \, d\Omega - \int_{\partial \Omega_T} T^i \, \delta u_i \, dS
$$

Using the constitutive law $\sigma^{ij} = C^{ijkl} \varepsilon_{kl}$, this becomes:
$$
\delta \Pi = \int_{\Omega} \sigma^{ij} \, \delta \varepsilon_{ij} \, d\Omega - \int_{\Omega} f^i \, \delta u_i \, d\Omega - \int_{\partial \Omega_T} T^i \, \delta u_i \, dS
$$

Setting the first variation to zero for equilibrium, $\delta \Pi = 0$, yields:
$$
\int_{\Omega} \sigma^{ij} \, \delta \varepsilon_{ij} \, d\Omega - \int_{\Omega} f^i \, \delta u_i \, d\Omega - \int_{\partial \Omega_T} T^i \, \delta u_i \, dS = 0
$$

Which is identical to the PVD. Therefore:

$$
\boxed{\delta \Pi = 0 \quad \Longleftrightarrow \quad \text{Principle of Virtual Displacements}}
$$

---

### 5. Why is this the Foundation for Space Structure Analysis?

1.  **Basis for FEM:** The PVD is the direct starting point for the derivation of the [[Finite Element Method]]'s stiffness matrix and load vector. The unknown [[Displacement Field]] $u^i$ is approximated by shape functions, and the PVD is enforced for a finite set of virtual displacements, leading to a system of algebraic equations.
2.  **Handles Complex Conditions:** It can naturally incorporate distributed loads, body forces, and traction boundary conditions without needing to solve complex differential equations.
3.  **Less Strict Smoothness:** The PVD only requires the integrals to be defined ([[Weak Form (Variational Form)]]), meaning the stress field can have discontinuities. This is less restrictive than the [[Strong Form (Pointwise Form)]], which requires continuous derivatives.
4.  **Geometric Complexity:** It is applicable to structures with complex geometries (like satellite trusses and pressurized hulls) that are intractable with analytical PDE solutions.

### Summary

The Principle of Virtual Displacements is formally defined by the equation:
$$
\int_{\Omega} \sigma^{ij} \, \delta \varepsilon_{ij} \, d\Omega = \int_{\Omega} f^i \, \delta u_i \, d\Omega + \int_{\partial \Omega_T} T^i \, \delta u_i \, dS
$$
It is a statement of equilibrium in an integral or "weak" form, equivalent to the differential equations of equilibrium and the traction boundary conditions. It is the direct consequence of the [[Stationarity]] of the total potential energy ($\delta \Pi = 0$) and serves as the indispensable theoretical foundation for all displacement-based computational mechanics, including the [[Finite Element Analysis (FEA)]] of space structures.
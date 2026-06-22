#Math-Concepts #DONE
### Formal Definition of Noether's Theorem

**1. Preliminary Concepts**

*   **Physical System:** We consider a physical system whose dynamics are derived from an **[[Action]] principle**. The configuration of the system is described by a set of fields, $\phi^i(x)$, defined over a domain of spacetime.
*   **The Action [[Functional]]:** The dynamics are encoded in the **[[Action]] [[Functional]]**, $S[\phi]$, which is the integral of a **[[Lagrangian]] [[density]]**, $\mathcal{L}$, over spacetime:
    $$
    S[\phi] = \int_{\Omega} \mathcal{L}(\phi^i, \partial_\mu \phi^i, x^\mu) \, d^4x
    $$
    where $\Omega$ is a region of spacetime, $\partial_\mu \phi^i$ are the derivatives of the fields, and $x^\mu$ are the spacetime coordinates.
*   **Equations of Motion:** The physical, classical paths of the system are those for which the [[Action]] is stationary ($\delta S = 0$). This leads to the **[[Euler-Lagrange Equations]]**:
    $$
    \frac{\partial \mathcal{L}}{\partial \phi^i} - \partial_\mu \left( \frac{\partial \mathcal{L}}{\partial (\partial_\mu \phi^i)} \right) = 0
    $$

**2. Definition of a [[Symmetry]]**

A **[[Symmetry]]** of the physical system is a continuous transformation of the fields and coordinates:
$$
x^\mu \to x'^\mu = x^\mu + \delta x^\mu, \quad \phi^i(x) \to \phi'^{\,i}(x') = \phi^i(x) + \Delta \phi^i(x)
$$
(where $\delta x^\mu$ and $\Delta \phi^i$ are infinitesimal) that leaves the **form of the equations of motion invariant**.

A more precise and powerful criterion for a [[symmetry]] in this context is that the transformation leaves the action **form-invariant** up to a boundary term. This means that under the transformation, the Lagrangian [[density]] changes at most by a four-divergence:
$$
\mathcal{L} \to \mathcal{L}' = \mathcal{L} + \partial_\mu \Lambda^\mu
$$
for some $\Lambda^\mu$. This condition ensures that $\delta S = 0$ for the transformed fields and coordinates, hence the equations of motion are unchanged.

**3. Statement of Noether's Theorem**

**Noether's (First) Theorem:** For every continuous [[symmetry]] of the action (as defined above), there exists a corresponding **conserved current**.

More formally:

*   **Given:** A continuous transformation (a [[symmetry]]) parameterized by a set of one or more constant parameters $\epsilon^a$, such that the variation of the action vanishes, $\delta S = 0$, or equivalently, the Lagrangian [[density]] is invariant up to a four-[[divergence]], $\delta \mathcal{L} = \partial_\mu \Lambda^\mu$.
*   **Then:** There exists a conserved Noether current, $j^{\mu}_a$, one for each parameter $\epsilon^a$, which satisfies the continuity equation "on-shell" (i.e., when the equations of motion are satisfied):
    $$
    \partial_\mu j^{\mu}_a = 0
    $$
*   **The Conserved Charge:** From this conserved current, one can define a **Noether charge**:
    $$
    Q_a = \int_{\text{all space}} j^0_a \, d^3x
    $$
    The continuity equation ($\partial_\mu j^\mu = 0$) directly implies that this charge is constant in time:
    $$
    \frac{dQ_a}{dt} = 0
    $$

**4. The Explicit Form of the Noether Current**

For a transformation that mixes field and coordinate changes, the general expression for the conserved current is:
$$
j^\mu = \left( \frac{\partial \mathcal{L}}{\partial (\partial_\mu \phi^i)} \partial_\nu \phi^i - \mathcal{L} \, \delta^\mu_\nu \right) \delta x^\nu - \frac{\partial \mathcal{L}}{\partial (\partial_\mu \phi^i)} \bar{\delta}\phi^i + \Lambda^\mu
$$
where $\bar{\delta}\phi^i = \phi'^{\,i}(x) - \phi^i(x) = \Delta \phi^i - \partial_\nu \phi^i \, \delta x^\nu$ is the **variation of the field at a fixed spacetime point** (the "[[Functional]]" or "form" variation).

### Corollary: Canonical Examples

The power of the theorem is illustrated by its most famous applications:

*   **Temporal Translation [[Invariance]] ($t \to t + \epsilon$):** [[Symmetry]] under translation in [[Time]] implies **[[Conservation of Energy]]**.
*   **Spatial Translation [[Invariance]] ($\vec{x} \to \vec{x} + \vec{\epsilon}$):** [[Symmetry]] under [[Translation]] in [[Space]] implies **[[Conservation of Linear Momentum]]**.
*   **Spatial Rotation [[Invariance]]:** [[Symmetry]] under [[Rotation]] implies **[[Conservation of Angular Momentum]]**.
*   **Internal Gauge [[Invariance]] (e.g., $\psi \to e^{i\theta}\psi$):** Symmetry under a [[global phase transformation]] implies **[[Conservation of Electric Charge]]**.

### Converse Theorem

A partial converse also holds: to every conserved quantity resulting from a conservation law $\partial_\mu j^\mu = 0$, one can associate a symmetry of the [[Action]].
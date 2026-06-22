#DONE #Math-Concepts
### Formal Definition of Invariance

**1. Core Concept**

**Invariance** is the property of a mathematical object, physical quantity, or physical law remaining unchanged under a specified set of [[Transformation]]s.

**2. Formal Mathematical Context**

In mathematics, an object $O$ is said to be **invariant** under a transformation $T$ (which can be a function, map, or operator) if the application of $T$ leaves $O$ unchanged.

*   **Scalar Invariance:** If $O$ is a scalar quantity, invariance is defined as:
    $$
    T(O) = O
    $$
*   **Structural Invariance:** If $O$ is a more complex structure (e.g., an equation, a function, a geometric shape), invariance means that its essential form or properties are preserved. For an equation $F(x) = 0$, invariance under $T$ implies:
    $$
    F(T(x)) = 0 \quad \text{whenever} \quad F(x) = 0
    $$
    The equation holds true in the new coordinate system or after the transformation has been applied.

**3. Formal Physical Context**

In physics, invariance is a fundamental principle stating that the laws of nature (encapsulated in their mathematical formulations) are the same for all observers related by certain transformations. This is a more nuanced concept with several key types:

*   **Form Invariance (or [[Covariance]]):** The mathematical *form* of a physical law is preserved under a transformation. If a law is written as $\mathcal{L}(\phi, \partial \phi) = 0$ in one frame, it will be written as $\mathcal{L}(\phi', \partial' \phi') = 0$ in the transformed frame. The [[Functional]] form of the [[Lagrangian]] or the differential equation is the same.

*   **Numerical Invariance:** A specific measurable quantity remains unchanged when calculated before and after a transformation. This is the most direct type of invariance. For example, the spacetime interval in special relativity is numerically invariant under [[Lorentz Transformations]].

**4. Classification by Transformation Type**

The concept of invariance is always defined relative to a specific group of transformations:

*   **Spatial Invariance:**
    *   **Translational Invariance:** The system or law is unchanged under spatial displacements, $\vec{x} \to \vec{x} + \vec{a}$.
    *   **Rotational Invariance:** The system or law is unchanged under rotations, $\vec{x} \to R\vec{x}$, where $R$ is a rotation matrix.

*   **Temporal Invariance:** The system or law is unchanged under a translation in time, $t \to t + \tau$.

*   **Lorentz Invariance:** The law is unchanged under a Lorentz transformation (a rotation or boost in spacetime). This is a foundational principle of Special Relativity.

*   **Gauge Invariance:** The physical law is unchanged under a local transformation of the fields (a *gauge transformation*). This is a cornerstone of modern quantum field theories like the Standard Model.

*   **Scale Invariance:** The law is unchanged under a rescaling of all lengths and energies, $x^\mu \to \lambda x^\mu$. This is an approximate [[symmetry]] in some physical systems.

**5. The Connection to [[Symmetry]] and [[Noether's Theorem]]**

In the context of analytical mechanics and field theory, which we discussed with [[Noether's Theorem]], a precise definition is:

An **invariance of the [[Action]]** $S$ under a continuous transformation is a transformation of the coordinates and field variables, $x^\mu \to x'^\mu$ and $\phi^i \to \phi'^{\,i}$, such that the change in the [[Action]] is at most a surface term (and hence vanishes for variations that vanish on the boundary):
$$
\delta S = S[\phi', \partial \phi', x'] - S[\phi, \partial \phi, x] = \int_{\partial \Omega} d\Sigma_\mu \, \Lambda^\mu
$$
or, equivalently, the Lagrangian [[density]] changes by a four-[[divergence]]:
$$
\mathcal{L}'(x') = \mathcal{L}(x) + \partial_\mu \Lambda^\mu
$$
This specific type of invariance is what [[Noether's Theorem]] identifies as the sufficient condition for the existence of a conserved quantity.
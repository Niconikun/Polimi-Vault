#Physics-Concept #Space-Structures #TBD 
#### **Virtual Work**
The virtual work is the work that would be done by the real forces acting on the body if it were to undergo the [[virtual displacement]].

*   **Virtual Work of [[Internal Forces]] ([[Stress Tensor]]):**
    This is the work done by the internal stresses $\sigma^{ij}$ as they move through the virtual strains $\delta \varepsilon_{ij}$.
    $$
    \delta W_{\text{int}} = -\int_{\Omega} \sigma^{ij} \, \delta \varepsilon_{ij} \, d\Omega
    $$
    The negative sign arises because the internal stresses resist the deformation.

*   **Virtual Work of External Forces:**
    This includes body forces $f^i$ and [[surface]] tractions $T^i$.
    $$
    \delta W_{\text{ext}} = \int_{\Omega} f^i \, \delta u_i \, d\Omega + \int_{\partial \Omega_T} T^i \, \delta u_i \, dS
    $$
    where $\partial \Omega_T$ is the part of the boundary where tractions are prescribed.
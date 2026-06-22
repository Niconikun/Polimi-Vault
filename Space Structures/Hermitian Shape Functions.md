## Formal Definition

**Hermitian Shape Functions** are a class of piecewise polynomial interpolation functions used in [[Finite Element Analysis (FEA)]] that enforce continuity of both the function value and its derivatives at element boundaries. Specifically, in the context of structural mechanics, they are employed to interpolate displacement fields where continuity of slopes (first derivatives) is essential, such as in beam and plate bending problems.

For the one-dimensional case with two nodes per element and two [[Degrees of Freedom]] per node (value and derivative), the Hermitian shape functions are cubic polynomials that satisfy the [[Kronecker delta]] property for both the function and its first derivative at the nodes.

## Mathematical Formulation

For a two-node beam element of length $L$ defined on the natural coordinate $\xi \in [-1, 1]$ or local coordinate $x \in [0, L]$, the four Hermitian shape functions for $C^1$ continuity are:

### In Natural Coordinates ($\xi \in [-1, 1]$):

1. **For displacement at node 1 ($\xi = -1$):**
   $$ N_1(\xi) = \frac{1}{4}(1 - \xi)^2(2 + \xi) = \frac{1}{4}(2 - 3\xi + \xi^3) $$

2. **For rotation at node 1 ($\xi = -1$):**
   $$ N_2(\xi) = \frac{L}{8}(1 - \xi)^2(1 + \xi) = \frac{L}{8}(1 - \xi - \xi^2 + \xi^3) $$

3. **For displacement at node 2 ($\xi = 1$):**
   $$ N_3(\xi) = \frac{1}{4}(1 + \xi)^2(2 - \xi) = \frac{1}{4}(2 + 3\xi - \xi^3) $$

4. **For rotation at node 2 ($\xi = 1$):**
   $$ N_4(\xi) = \frac{L}{8}(1 + \xi)^2(\xi - 1) = \frac{L}{8}(-1 - \xi + \xi^2 + \xi^3) $$

### In Local Coordinates ($x \in [0, L]$):

1. **For displacement at node 1 ($x = 0$):**
   $$ H_1(x) = 1 - 3\left(\frac{x}{L}\right)^2 + 2\left(\frac{x}{L}\right)^3 $$

2. **For rotation at node 1 ($x = 0$):**
   $$ H_2(x) = x\left(1 - \frac{x}{L}\right)^2 $$

3. **For displacement at node 2 ($x = L$):**
   $$ H_3(x) = 3\left(\frac{x}{L}\right)^2 - 2\left(\frac{x}{L}\right)^3 $$

4. **For rotation at node 2 ($x = L$):**
   $$ H_4(x) = \frac{x^2}{L}\left(\frac{x}{L} - 1\right) $$

## Fundamental Properties

Hermitian shape functions satisfy the following essential conditions:

1. **[[Kronecker Delta]] Property:**
   - For displacement functions: $N_i(\xi_j) = \delta_{ij}$ and $\frac{dN_i}{d\xi}(\xi_j) = 0$
   - For rotation functions: $\frac{dN_i}{d\xi}(\xi_j) = \delta_{ij}$ and $N_i(\xi_j) = 0$
   Where $i, j = 1, 2$ refer to node numbers.

2. **Partition of Unity:** The displacement shape functions sum to unity:
   $$ N_1(\xi) + N_3(\xi) = 1 \quad \text{for all } \xi \in [-1, 1] $$
   (Note: $N_2$ and $N_4$ are associated with rotations and do not participate in this sum.)

3. **Interpolation Capability:** They can exactly represent any cubic polynomial over the element domain.

4. **$C^1$ Continuity:** The interpolated field $w(\xi)$ and its first derivative $\frac{dw}{d\xi}$ are continuous across element boundaries.

## Interpolation Scheme

The [[Displacement Field]] within a beam element is interpolated as:
$$ w(\xi) = \sum_{i=1}^{4} N_i(\xi) a_i = N_1 w_1 + N_2 \theta_1 + N_3 w_2 + N_4 \theta_2 $$
Where:
- $w_1, w_2$ = transverse displacements at nodes 1 and 2
- $\theta_1, \theta_2$ = rotations at nodes 1 and 2
- $a = [w_1, \theta_1, w_2, \theta_2]^T$ = vector of nodal [[degrees of freedom]]

## Derivative Relationships

The first derivative (slope) is obtained as:
$$ \frac{dw}{d\xi} = \sum_{i=1}^{4} \frac{dN_i}{d\xi} a_i $$
And the second derivative (curvature) as:
$$ \frac{d^2w}{d\xi^2} = \sum_{i=1}^{4} \frac{d^2N_i}{d\xi^2} a_i $$
This is crucial for computing bending strains $\varepsilon = -y \frac{d^2w}{dx^2}$ in beam elements.

## Applications in [[Finite Element Analysis (FEA)]]

1. **Euler-Bernoulli Beam Elements:** Primary application for slender beam bending analysis.
2. **Timoshenko Beam Elements:** Modified versions accommodate shear deformation.
3. **Plate and Shell Elements:** Extended to two dimensions for Kirchhoff-Love plate theory.
4. **Higher-Order Continuity Problems:** Any problem requiring $C^1$ or higher continuity in the solution field.

## Advantages

1. **Guaranteed Continuity:** Ensures slope continuity between elements without additional constraints.
2. **Geometric [[Invariance]]:** Maintains [[consistency]] under coordinate transformations.
3. **Optimal Convergence:** For fourth-order problems (beam bending), cubic Hermitian polynomials provide optimal convergence rates in energy norm.

## Limitations

1. **Higher Computational Cost:** More [[degrees of freedom]] per element compared to Lagrange elements.
2. **Complexity in Multidimensions:** Extension to 2D and 3D requires careful construction (e.g., Argyris triangle, Bogner-Fox-Schmit rectangle for plates).
3. **Not Suitable for $C^0$ Problems:** Overly constrained for problems requiring only displacement continuity.

## See Also

- [[Euler-Bernoulli Beam Element]]
- [[Finite Element Interpolation Functions]]
- [[Lagrangian Shape Functions]]
- [[C^k Continuity in Finite Elements]]
- [[Beam Theory Fundamentals]]
- [[Isoparametric Formulation]]
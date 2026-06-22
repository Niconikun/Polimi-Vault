#Physics-Concept #DONE 
### Formal Definition of Work

In physics, **work** is a scalar quantity that measures the energy transferred to or from an object by means of a [[force]] acting on it along a [[Displacement]]. It is defined as the line integral of the dot product of the force [[Vector]] $\mathbf{F}$ and the infinitesimal displacement [[Vector]] $d\mathbf{r}$ along the path $C$ taken by the object.

$$
W = \int_C \mathbf{F} \cdot d\mathbf{r}
$$
For a constant force acting in a straight line, this simplifies to $W = \mathbf{F} \cdot \Delta\mathbf{r}$.

---

### Definition using Einstein Notation

The power of Einstein notation shines in expressing the dot product. The dot product of two vectors in a Cartesian basis is the sum of the products of their corresponding components.

The infinitesimal [[displacement]] [[Vector]] $d\mathbf{r}$ can be written in terms of its components. In a [[coordinate system]] with basis $\mathbf{e}_i$, the [[position]] [[Vector]] is $\mathbf{r} = r^i \mathbf{e}_i$. Therefore, the differential displacement is:

$$
d\mathbf{r} = dr^i \mathbf{e}_i
$$

The force [[Vector]] is $\mathbf{F} = F^i \mathbf{e}_i$.

The integrand of the work integral is the dot product $\mathbf{F} \cdot d\mathbf{r}$. Using the properties of the dot product ($\mathbf{e}_i \cdot \mathbf{e}_j = \delta_{ij}$, the [[Kronecker delta]], for an orthonormal basis), we have:

$$
\mathbf{F} \cdot d\mathbf{r} = (F^i \mathbf{e}_i) \cdot (dr^j \mathbf{e}_j) = F^i dr^j (\mathbf{e}_i \cdot \mathbf{e}_j) = F^i dr^j \delta_{ij}
$$

Now, applying the Einstein summation convention and the rule of the [[Kronecker delta]] ($\delta_{ij} A^j = A_i$), the expression simplifies dramatically. The index $j$ is summed over, and $\delta_{ij}$ is only 1 when $j = i$, "picking out" the terms where the indices match:

$$
\mathbf{F} \cdot d\mathbf{r} = F^i dr^j \delta_{ij} = F^i dr^i
$$

Therefore, the definition of work in Einstein notation is:

$$
\boxed{W = \int_C \mathbf{F} \cdot d\mathbf{r} = \int_C F^i \, dr^i}
$$

**Explanation of the Notation:**

*   $W$: The scalar work.
*   $C$: The path of integration.
*   $F^i$: The contravariant components of the force [[Vector]].
*   $dr^i$: The differentials of the coordinates, which are the components of the infinitesimal displacement [[Vector]] $d\mathbf{r}$.
*   **The Rule Applied:** The repeated index $i$ in $F^i dr^i$ implies a sum over all spatial dimensions: $F^1 dr^1 + F^2 dr^2 + F^3 dr^3$. This is the concise Einstein notation expression for the dot product.

---
### Important Note: General Coordinates

The expression $W = \int_C F^i dr^i$ is valid in Cartesian coordinates because the basis is orthonormal ($\mathbf{e}_i \cdot \mathbf{e}_j = \delta_{ij}$). In a general curvilinear [[coordinate system]], the [[Metric Tensor]] $g_{ij}$ is needed to define the dot product correctly:

$$
\mathbf{F} \cdot d\mathbf{r} = (F^i \mathbf{e}_i) \cdot (dr^j \mathbf{e}_j) = F^i dr^j g_{ij}
$$

where $g_{ij} = \mathbf{e}_i \cdot \mathbf{e}_j$. In this general case, the work is:

$$
W = \int_C F^i dr^j g_{ij}
$$

This reduces to the previous form in Cartesian coordinates where $g_{ij} = \delta_{ij}$. The version $W = \int_C F^i dr^i$ is the most common and useful one for fundamental definitions in classical mechanics.
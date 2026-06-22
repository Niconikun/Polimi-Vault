#Physics-Concept #DONE 

For [[Rigid-Body Dynamics]] dynamics, [[Angular Acceleration]] plays the same role that linear [[acceleration]] does in translational motion. The rotational analogue of [[Newton's second law]], $\mathbf{F} = m\mathbf{a}$, is:

$$
\boldsymbol{\tau} = I \boldsymbol{\alpha}
$$

where $\boldsymbol{\tau}$ is the net torque and $I$ is the [[Moment of Inertia Tensor]] (for [[Rotation]] about a fixed axis).

In the more general case of 3D rotation, where the moment of inertia becomes a [[tensor]] $I^{ij}$, the relationship between torque $\tau^i$ and [[Angular Acceleration]] $\alpha_j$ is:

$$
\tau^i = I^{ij} \alpha_j
$$

This is directly analogous to $F^i = m a^i$ but accounts for the fact that the rotational inertia depends on the axis of rotation.

We can also derive this from the definition of torque $\boldsymbol{\tau} = \frac{d\mathbf{L}}{dt}$ and the relationship $\mathbf{L} = I\boldsymbol{\omega}$:

\[
\tau^i = \frac{dL^i}{dt} = \frac{d}{dt}(I^{ij} \omega_j)
\]

If the inertia [[tensor]] is constant (for a [[Rigid Body]] with fixed mass distribution), then:

\[
\tau^i = I^{ij} \frac{d\omega_j}{dt} = I^{ij} \alpha_j
\]

Thus, we have the dynamic definition of [[Angular Acceleration]]:

\[
\boxed{\tau^i = I^{ij} \alpha_j}
\]
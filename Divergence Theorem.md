#DONE #Math-Concepts 

Let $\nabla$ and $\nabla^2$ denote respectively the gradient and Laplace operator in the two dimensional cartesian rectangular coordinate system $(x,y)$.
$$
\nabla = \hat{e_x}\frac{\partial}{\partial x} + \hat{e_y}\frac{\partial}{\partial y}, \nabla \cdot \nabla = \frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2}
$$

$$
\int_\Omega {div(G)}dxdy = \int_\Omega \nabla \cdot G dxdy = \oint_\Gamma \hat{n} \cdot Gds
$$or
$$
\int_\Omega (\frac{\partial G}{\partial x} + \frac{\partial G}{\partial y}) dxdy = \oint_\Gamma (G_xn_x + G_yn_y)ds
$$Here the dot denotes the scalar product of vector, $\hat{n}$ denotes the unit vector normal to the [[surface]] $\Gamma$ of the domain $\Omega$; $n_x$ and $n_y$ ($G_x$ and $G_y$)are the rectangular components of **$\hat{n}(G)$** and the circle on the boundary integral indicates that the integration is taken over the entire boundary. 
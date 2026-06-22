#SAD #DONE 
### Formal Definition of Quaternions

In the context of mathematics and [[Rigid Body Kinematics]], a **quaternion** is a four-dimensional complex number that provides an efficient, non-singular parameterization of [[Rotation]]s in three-dimensional space.

A quaternion is defined as a number of the form:

$$
\vec{q} = q_0 + q_1\mathbf{i} + q_2\mathbf{j} + q_3\mathbf{k} = \begin{bmatrix} q_0 \\ q_1 \\ q_2 \\ q_3 \end{bmatrix} = \begin{bmatrix} q_0 \\ \vec{q}_v \end{bmatrix}
$$

where:
*   $q_0, q_1, q_2, q_3$ are real numbers.
*   $\mathbf{i}, \mathbf{j}, \mathbf{k}$ are the fundamental quaternion units.
*   $q_0 $ is referred to as the **scalar part**.
*   $\vec{q}_v = [q_1, q_2, q_3]^T$ is referred to as the **vector part**.

### Fundamental Properties and Operations

#### 1. Quaternion Multiplication
The multiplication of two quaternions is defined by the Hamilton product, which is non-commutative. It is governed by the following rules for the fundamental units:
$$
\mathbf{i}^2 = \mathbf{j}^2 = \mathbf{k}^2 = \mathbf{ijk} = -1
$$
$$
\mathbf{ij} = \mathbf{k}, \quad \mathbf{jk} = \mathbf{i}, \quad \mathbf{ki} = \mathbf{j}
$$
$$
\mathbf{ji} = -\mathbf{k}, \quad \mathbf{kj} = -\mathbf{i}, \quad \mathbf{ik} = -\mathbf{j}
$$

For two quaternions $\vec{p} = [p_0, \vec{p}_v]$ and $\vec{q} = [q_0, \vec{q}_v]$, the Hamilton product is:
$$
\vec{p} \otimes \vec{q} = \begin{bmatrix} p_0 q_0 - \vec{p}_v \cdot \vec{q}_v \\ p_0 \vec{q}_v + q_0 \vec{p}_v + \vec{p}_v \times \vec{q}_v \end{bmatrix}
$$
This cross-product term in the vector part is the source of the non-commutativity ($\vec{p} \otimes \vec{q} \neq \vec{q} \otimes \vec{p}$) and is crucial for representing sequential rotations.

#### 2. Conjugate, Norm, and Inverse
*   **Conjugate:** $\vec{q}^* = [q_0, -\vec{q}_v]$
*   **Norm:** $\| \vec{q} \| = \sqrt{q_0^2 + q_1^2 + q_2^2 + q_3^2}$
*   **Inverse:** $\vec{q}^{-1} = \frac{\vec{q}^*}{\| \vec{q} \|^2}$

### Quaternions as Rotation Operators ([[Euler-Rodrigues Parameters]])

For representing rotations or changes in [[attitude]], **unit quaternions** are used. A unit quaternion satisfies $\| \vec{q} \| = 1$.

A unit quaternion can be constructed from a rotation of angle $\theta$ about a unit vector $\hat{\mathbf{e}} = [e_x, e_y, e_z]^T$ [[Euler Axis and Angle]]:
$$
\vec{q} = \begin{bmatrix} \cos(\theta/2) \\ \hat{\mathbf{e}} \sin(\theta/2) \end{bmatrix} = \begin{bmatrix} \cos(\theta/2) \\ e_x \sin(\theta/2) \\ e_y \sin(\theta/2) \\ e_z \sin(\theta/2) \end{bmatrix}
$$

This is often called the **[[Euler-Rodrigues Parameters]]** parameterization.

*   The scalar part, $q_0 = \cos(\theta/2)$, encodes the amount of rotation.
*   The vector part, $\vec{q}_v = \hat{\mathbf{e}} \sin(\theta/2)$, encodes the axis of rotation.

To rotate a vector $\vec{r}$ from one coordinate frame to another (e.g., from body frame to inertial frame) using a quaternion, the vector is first treated as a pure quaternion $(0, \vec{r})$. The rotation is then performed using quaternion multiplication:

$$
\vec{r}' = \vec{q} \otimes \begin{bmatrix} 0 \\ \vec{r} \end{bmatrix} \otimes \vec{q}^{-1}
$$

Since $\vec{q}$ is a unit quaternion, $\vec{q}^{-1} = \vec{q}^*$. The result $\vec{r}'$ is another pure quaternion whose vector part is the rotated vector.

### Kinematic Differential Equation for Quaternions

The time evolution of the [[attitude]] quaternion is governed by the following first-order differential equation, which is linear in the quaternion components:

$$
\dot{\vec{q}} = \frac{1}{2} \vec{q} \otimes \begin{bmatrix} 0 \\ \vec{\omega} \end{bmatrix} = \frac{1}{2} \begin{bmatrix} -q_1 & -q_2 & -q_3 \\ q_0 & -q_3 & q_2 \\ q_3 & q_0 & -q_1 \\ -q_2 & q_1 & q_0 \end{bmatrix} \begin{bmatrix} \omega_x \\ \omega_y \\ \omega_z \end{bmatrix}
$$

Where $\vec{\omega} = [\omega_x, \omega_y, \omega_z]^T$ is the [[Angular Velocity]] vector of the body-frame relative to the inertial frame, expressed in the body-frame.

### Why Quaternions are Preferred in Spacecraft [[Attitude]] Dynamics

1.  **Non-Singularity:** Unlike a three-parameter set like [[Euler angles]], quaternions do not suffer from "[[gimbal lock]]," a singularity where a degree of freedom is lost.
2.  **Computational Efficiency:** The kinematic equation is linear and contains no trigonometric functions, making it faster and more robust for numerical integration on flight computers compared to [[Euler angles]].
3.  **Unambiguous Representation:** While a single rotation has two quaternion representations ($\vec{q}$ and $-\vec{q}$), this is simpler than the trigonometric ambiguities inherent in other representations.

In summary, a **quaternion** is a four-parameter complex number that, when constrained to unit length, provides a highly efficient, singularity-free method for representing and propagating the orientation of a [[Rigid Body]], such as a spacecraft.
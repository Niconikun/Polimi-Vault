### **Formal Definition: The Euler Method**
#Math-Concepts #DONE 

**1. Conceptual Overview and Purpose**

The Euler Method is a first-order, explicit [[Numerical Analysis]] procedure for approximating the solutions of [[Initial Value Problems]] (IVPs). It is the simplest of the [[Runge-Kutta Methods]] (specifically, it is the first-order explicit [[Runge-Kutta Methods]] method). Its purpose is to generate a sequence of points that approximate the solution curve of the IVP:

$$
\frac{dy}{dt} = f(t, y), \quad y(t_0) = y_0
$$

where $y$ is the unknown function, $t$ is the independent variable, $f$ is a function that defines the derivative, and $ y_0$ is the initial condition.

**2. Formal Mathematical Definition**

The Euler Method constructs the approximation iteratively. Given a step size $h > 0$, the numerical approximation $y_{n+1}$ at [[Time]] $t_{n+1} = t_n + h$ is computed from the known approximation $y_n$ at time $n$ using the formula:

$$
y_{n+1} = y_n + h \cdot f(t_n, y_n)
$$

for $n = 0, 1, 2, \dots$, starting with the initial condition $y(t_0) = y_0$.

**3. Geometrical Interpretation and Derivation**

The method can be derived and understood from two primary perspectives:

*   **Finite Difference Approximation:**
    The derivative is approximated using a forward finite difference:
   $$
    \frac{dy}{dt} \approx \frac{y(t_{n+1}) - y(t_n)}{h}
   $$
    Substituting this into the ODE $y' = f(t, y)$ yields:
   $$
    \frac{y_{n+1} - y_n}{h} = f(t_n, y_n)
   $$
    Rearranging this expression gives the formal definition of the Euler Method.

*   **Geometric (Tangent Line) Interpretation:**
    The solution to the ODE passes through the point $(t_n, y_n)$ with a slope given by $f(t_n, y_n)$. The Euler Method proceeds by following this tangent line for one step of length $h$. The value $y_{n+1}$is the point on this tangent line at $t = t_{n+1}$.

**4. Classification**

*   **Type:** It is a **One-Step Method** because the new approximation $y_{n+1}$ depends only on the information from a single previous point $(t_n, y_n)$.
*   **Explicitness:** It is an **Explicit Method** because the formula for $y_{n+1}$ is given directly in terms of known data $(t_n, y_n)$.
*   **Order:** It is a **First-Order Method**.

**5. Key Properties and Analysis**

*   **Order of Accuracy ([[Consistency]]):**
    The Euler Method is a first-order method. This means:
    *   The **local truncation error** (the error committed in a single step) is $O(h^2)$.
    *   The **[[global error]]** (the cumulative error over a fixed interval $[t_0, T]$) is $O(h)$.
    Consequently, halving the step size $h$ roughly halves the global error.

*   **Stability:**
    The stability of the method is analyzed using the linear test equation $y' = \lambda y$, where $\lambda$ is a complex constant.
    Applying the Euler Method gives:
   $$
    y_{n+1} = y_n + h \lambda y_n = (1 + h\lambda) y_n
   $$
    The **stability function** is $R(z) = 1 + z$, where $z = h\lambda$.
    The **region of absolute stability** is the set of $z \in \mathbb{C}$ for which $|1 + z| < 1$. This describes a circle of radius 1 centered at $z = -1$ in the complex plane.
    *   For a purely real, negative $\lambda$ (a decaying solution), the method is stable only if $h < -\frac{2}{\lambda}$. This conditional stability can be a significant limitation, making the Euler Method unsuitable for "stiff" ODEs unless the step size $h$ is chosen to be very small.

*   **[[Convergence]]:**
    The method is **convergent**. For a Lipschitz-continuous function $f$, the numerical approximation produced by the Euler Method converges to the true solution as the step size $h \to 0$. This is guaranteed by the [[Lax-Richtmyer Equivalence Theorem]], as the method is both consistent and zero-stable.

**6. Variants**

*   **Backward Euler Method (Implicit Euler):**
    This is a first-order implicit variant defined by:
   $$
    y_{n+1} = y_n + h \cdot f(t_{n+1}, y_{n+1})
   $$
    This formula is implicit because the unknown $y_{n+1}$ appears on both sides, generally requiring the solution of a nonlinear equation at each step. The Backward Euler method is **unconditionally stable** for the linear test equation, making it highly suitable for stiff equations, despite its lower order of accuracy.

### **Summary**

In essence, the **Euler Method is a first-order, explicit, one-step numerical integrator that approximates the solution to an [[Ordinary Differential Equations (ODEs)]] ODE by following the local tangent line at each point.** Its simplicity makes it a foundational pedagogical tool, but its low order and conditional stability often render it inefficient or impractical for high-precision or stiff applications compared to higher-order methods like the [[Runge-Kutta Methods]] family.
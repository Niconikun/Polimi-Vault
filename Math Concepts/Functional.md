#Math-Concepts #DONE 
Consider the integral expression of the form:
$$
I(u) = \int^b_a{F(x,u,u')dx} , u=u(x), u' = \frac{du}{dx}
$$
where the integrand $F(x,u,u')$ is a given function of the coordinate x (independent variable), dependent variable u, and its derivative. For a given real function $u=u(x)$, $I(u)$ is a real number. Therefore, $I$ can be viewed as an operator that transforms functions $u(x)$ into real numbers, and such operators are called functionals.

We shall use the term functional to describe functions defined by integrals whose arguments themselves are functions. Thus, loosely speaking, a functional is "a function of functions". Its formal definition:

> A functional is an operator $I$ that maps functions $u$ from a linear vector space into a real number field.

## Properties

A functional is said to be linear if:
$$
l(\alpha u + \beta v) = \alpha l(u) + \beta l(v)
$$

A functional is said to be bilinear if its linear with both of its arguments
$$
B(\alpha u_1 + \beta u_2,v) = \alpha B(u_1,v) + \beta B(u_2,v) $$  
or 
$$
B(u,\alpha v_1 + \beta v_2) = \alpha B(u,v_1) + \beta B(u,v_2) $$
A bilinear functional is said to be symmetric if
$$
B(u,v) = B(v,u)
$$
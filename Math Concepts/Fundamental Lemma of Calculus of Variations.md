#DONE #Math-Concepts 
The fundamental lemma of [[Calculus of Variations]] can be stated as follows:
> For any integrable function $G(x)$, if the statement:
> $$
 \int^b_a{G(x) \nu (x]) = 0}
 $$
> holds for any arbitrary continuous function $\nu (x)$, for all $x$ in $(a, b)$, the int *follows that* $G(x)=0$ in $(a,b)$.

A simple proof of the lemma follows from setting $\nu (x)$, which is arbitrary, equal to $G$. We have
 $$
 \int^b_a{[G(x)]^2}dx = 0
 $$
 Since an integral of a positive function, $G^2$ is positive, the above statement implies that $G(x) = 0$ in the domain $\Omega = (a,b)$.
 A more general statement of the fundamental lemma is as follows: if $\nu(x)$ is arbitrary $a<x<b$ and $\nu(a)$ is arbitrary, then the statement
 $$
 \int^b_a{G \nu dx} + B(a) \nu (a) = 0
 $$
 Implies that
 $$
 G = 0, a<x<b, B(a)=0
 $$
 Because $\nu (x)$ is independent of $\nu (a)$.
 
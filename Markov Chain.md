---
title: Markov Chain
tags:
  - probability
  - stochastic processes
  - dynamical systems
  - discrete systems
---

# Markov Chain

## Formal Definition

A **Markov chain** is a stochastic process with the [[Markov Property]] in which the future state depends only on the current state and is independent of the history. Formally, a sequence of random variables $\{X_n : n \geq 0\}$ is a Markov chain if:
$$
P(X_{n+1} = x_{n+1} | X_n = x_n, X_{n-1} = x_{n-1}, \ldots, X_0 = x_0) = P(X_{n+1} = x_{n+1} | X_n = x_n)
$$

Markov chains are fundamental to [[Probability Theory]], statistics, control systems, and the modeling of systems with random transitions between discrete states.

## Historical Development

### Key Milestones
- **1906:** Andrey Markov introduces chains of dependent trials, founding theory
- **1930s:** Development of ergodic theory and stationary distributions
- **1944:** John von Neumann and Oskar Morgenstern apply chains to game theory
- **1950s–1960s:** Markov chains become central to queueing theory and operations research
- **1970s–Present:** Applications expand to [[Machine Learning]], hidden Markov models, Monte Carlo methods

### Foundational Contributors
1. **Andrey Markov (1856–1922):** Formulated chains and proved limit theorems
2. **Andrey Kolmogorov (1903–1987):** Developed rigorous probability theory including Markov processes
3. **Claude Shannon (1916–2001):** Applied chains to information theory and communication
4. **Leonard Kleinrock:** Developed Markov chain methods for queueing theory

## Mathematical Formulation

### Discrete-Time Markov Chain

**State Space:** Finite set $S = \{s_1, s_2, \ldots, s_N\}$ or countably infinite

**Transition Probability Matrix:**
$$
P = \begin{bmatrix} p_{11} & p_{12} & \cdots & p_{1N} \\ p_{21} & p_{22} & \cdots & p_{2N} \\ \vdots & \vdots & \ddots & \vdots \\ p_{N1} & p_{N2} & \cdots & p_{NN} \end{bmatrix}
$$

Where $p_{ij} = P(X_{n+1} = s_j | X_n = s_i)$ is the probability of transitioning from state $i$ to state $j$.

**Stochastic Matrix Property:**
$$
\sum_{j=1}^N p_{ij} = 1 \text{ for all } i
$$

(Each row sums to 1)

### One-Step Transition

$$
P(X_{n+1} = s_j | X_n = s_i) = p_{ij}
$$

### $n$-Step Transition

$$
P(X_{n+k} = s_j | X_n = s_i) = (P^k)_{ij}
$$

The $n$-step transition probability is given by the $(i,j)$-entry of matrix $P^n$.

### Distribution Evolution

**Initial Distribution:** $\boldsymbol{\pi}^{(0)} = [p_1^{(0)}, p_2^{(0)}, \ldots, p_N^{(0)}]^T$

**Distribution after $n$ steps:**
$$
\boldsymbol{\pi}^{(n)} = (P^T)^n \boldsymbol{\pi}^{(0)}
$$

Or equivalently:
$$
\boldsymbol{\pi}^{(n)} = \boldsymbol{\pi}^{(n-1)T} P
$$

### Special Cases

1. **Homogeneous Markov Chain:** Transition probabilities independent of time (time-homogeneous)

2. **Absorbing State:** State $i$ where $p_{ii} = 1$ (once entered, cannot leave)

3. **Reducible/Irreducible Chain:**
   - **Irreducible:** All states communicate (can reach each state from any other)
   - **Reducible:** Contains separate communicating classes

4. **Periodic/Aperiodic Chain:**
   - **Aperiodic:** No state returns to itself at regular intervals
   - **Periodic with period $d$:** Returns occur at multiples of $d$ steps

## Fundamental Principles

### Markov Property

The defining characteristic—future independent of past given present:
$$
P(X_{n+1} = x | X_n = x_n, \text{history}) = P(X_{n+1} = x | X_n = x_n)
$$

This "memoryless" property enables tractable analysis of complex stochastic systems.

### Classification of States

**Communication:** States $i$ and $j$ communicate if each is reachable from the other.

**Transient State:** Finite probability of eventual departure (never to return):
$$
f_{ii} = P(\text{return to } i | \text{start at } i) < 1
$$

**Recurrent State:** Certain return to state if starting there ($f_{ii} = 1$):
- **Positive Recurrent:** Expected return time is finite
- **Null Recurrent:** Expected return time is infinite

## Theoretical Framework

### Stationary Distribution

A distribution $\boldsymbol{\pi}$ is stationary if:
$$
\boldsymbol{\pi}^T = \boldsymbol{\pi}^T P
$$

Or entry-wise:
$$
\pi_i = \sum_{j} \pi_j p_{ji}
$$

**Interpretation:** If initial distribution is stationary, it remains unchanged.

### Convergence and Ergodicity

**Irreducible, aperiodic Markov chain:** Converges to unique stationary distribution regardless of initial state:
$$
\lim_{n \to \infty} P(X_n = s_j | X_0 = s_i) = \pi_j \text{ for all } i,j
$$

**Ergodic Theorem:** For ergodic chains, time-average converges to stationary average:
$$
\frac{1}{n}\sum_{k=0}^{n-1} f(X_k) \to E_\pi[f(X)] \text{ almost surely}
$$

### Detailed Balance and Reversibility

**Detailed Balance Condition:**
$$
\pi_i p_{ij} = \pi_j p_{ji}
$$

If satisfied, the chain is reversible (time-reversible). This condition is useful for constructing chains with desired stationary distributions.

## Applications

### Queueing Theory

**M/M/1 Queue:** Markovian arrivals and service
- State = number of customers in system
- Transition probabilities determined by arrival and service rates
- Stationary distribution gives system performance metrics

### Random Walks

Simple symmetric random walk on integers:
$$
p_{i,i+1} = p_{i,i-1} = \frac{1}{2}
$$

**Gambler's Ruin:** Player with $k$ dollars plays until reaching $0$ or $N$
- Probability of ruin depends on initial capital
- Absorbing barriers at states 0 and $N$

### Machine Learning and AI

**Hidden Markov Models (HMM):**
- Observations depend on hidden state sequence
- Applications: speech recognition, sequence labeling, bioinformatics

**Markov Decision Processes (MDP):**
- Extension with actions and rewards
- Foundation of [[Control Systems]] and [[Adaptive Control Theory]]
- Used in reinforcement learning

### Finance and Economics

- **Stock Price Models:** Discrete approximation of continuous processes
- **Credit Rating Transitions:** Transitions between rating states (AAA, AA, etc.)
- **Inventory Systems:** Discrete inventory levels and transitions

### Physical Systems

- **Molecular Dynamics:** Transitions between chemical states
- **Thermal Systems:** Heat transfer and diffusion processes
- **Reliability:** Component failure transitions (working → failed)

## Computational Methods

### Monte Carlo Simulation

Generate sample paths by repeatedly sampling from transition probabilities:

```
For each step n:
    Sample j ~ Categorical(p[current_state, :])
    current_state = j
```

### Matrix Methods for Stationary Distribution

Solve the system:
$$
\boldsymbol{\pi}^T(P - I) = 0^T, \quad \sum_i \pi_i = 1
$$

**Power Method:** Iteratively compute $\boldsymbol{\pi}^{(n)} = P^T \boldsymbol{\pi}^{(n-1)}$ until convergence.

### Relationship to Other Concepts

1. **Connection to [[Random Walk]]:**
   - Special case where transitions are to neighboring states
   - Fundamental example of Markov chain behavior

2. **Connection to [[Stochastic Processes]]:**
   - Discrete-time, discrete-space special case
   - Extension to continuous time → continuous-time Markov chains

3. **Connection to [[Control Systems]]:**
   - Markov Decision Processes extend chains with actions and rewards
   - Foundation for optimal control in stochastic settings

4. **Connection to [[Monte Carlo Method]]:**
   - Markov Chain Monte Carlo (MCMC) generates samples from complex distributions
   - Metropolis-Hastings algorithm uses Markov chains

## See Also

- [[Probability Theory]]
- [[Stochastic Processes]]
- [[Random Walk]]
- [[Monte Carlo Method]]
- [[Markov Decision Process]]
- [[Hidden Markov Model]]
- [[Stationary Distribution]]
- [[Control Systems]]
- [[Adaptive Control Theory]]
- [[Signal Processing]]

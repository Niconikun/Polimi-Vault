---
title: State Vector
tags:
  - control theory
  - dynamical systems
  - linear algebra
  - spacecraft dynamics
---

# State Vector

## Formal Definition

A **state vector** is a column vector in a dynamical system that contains all information necessary to describe the complete state of the system at a particular instant in time. The state vector is typically denoted as $\mathbf{x}(t)$ and encapsulates the minimal set of variables required to uniquely determine the future behavior of the system given knowledge of inputs and system dynamics.

## Historical Development

### Key Milestones
- **1950s:** Emergence of state-space representation as an alternative to classical transfer function methods in control theory
- **1960s:** Development of modern control theory by Rudolf E. Kálmán, emphasizing state-space formulation
- **1970s:** Widespread adoption in aerospace applications, particularly for spacecraft attitude control and trajectory estimation

### Foundational Contributors
1. **Rudolf E. Kálmán (1930–2016):** Formulated the modern state-space approach and developed the Kalman filter
2. **Charles A. Desoer & Ernest S. Kuh:** Advanced the theoretical foundations of state-space analysis
3. **Gene F. Franklin & Powell:** Applied state-space methods to practical engineering problems

## Mathematical Formulation

### General Form

The state of a dynamical system is described by:
$$
\mathbf{x}(t) = \begin{bmatrix} x_1(t) \\ x_2(t) \\ \vdots \\ x_n(t) \end{bmatrix}
$$

Where $n$ is the order of the system. The dynamics are governed by:
$$
\dot{\mathbf{x}}(t) = \mathbf{A}(t)\mathbf{x}(t) + \mathbf{B}(t)\mathbf{u}(t)
$$

And the output is:
$$
\mathbf{y}(t) = \mathbf{C}(t)\mathbf{x}(t) + \mathbf{D}(t)\mathbf{u}(t)
$$

### Component Breakdown

- **$\mathbf{x}(t) \in \mathbb{R}^n$**: State vector at time $t$
- **$\mathbf{u}(t) \in \mathbb{R}^p$**: Input/control vector
- **$\mathbf{y}(t) \in \mathbb{R}^q$**: Output vector
- **$\mathbf{A}(t) \in \mathbb{R}^{n \times n}$**: State transition matrix
- **$\mathbf{B}(t) \in \mathbb{R}^{n \times p}$**: Input influence matrix
- **$\mathbf{C}(t) \in \mathbb{R}^{q \times n}$**: Output matrix
- **$\mathbf{D}(t) \in \mathbb{R}^{q \times p}$**: Direct transmission matrix

### Special Cases

1. **Time-Invariant Linear System (LTI):**
   $$
   \dot{\mathbf{x}} = \mathbf{A}\mathbf{x} + \mathbf{B}\mathbf{u}
   $$

2. **Unforced System (Free Evolution):**
   $$
   \dot{\mathbf{x}} = \mathbf{A}\mathbf{x}
   $$

3. **Discrete-Time State Equation:**
   $$
   \mathbf{x}[k+1] = \mathbf{A}\mathbf{x}[k] + \mathbf{B}\mathbf{u}[k]
   $$

## Fundamental Principles

### Core Assumptions

1. **Causality:** The future state depends only on the current state and future inputs, not on past history
2. **Finite Dimensionality:** The state space has finite dimension $n$, meaning the system is describable by $n$ independent variables
3. **Sufficiency:** The state vector contains all information necessary to predict future system behavior
4. **Markovian Property:** Given the current state, the future is independent of the past

### Governing Principles

- **Superposition Principle:** For linear systems, responses due to different initial conditions and inputs superpose
- **State Transition:** From $\mathbf{x}(t_0)$ to $\mathbf{x}(t)$ via the state transition matrix $\boldsymbol{\Phi}(t,t_0)$
- **Observability and Controllability:** Criteria determining whether states can be estimated from outputs or driven to desired values through inputs

## Theoretical Framework

### Choice of State Variables

The selection of state variables is not unique. For a given system, multiple valid state representations exist related by linear transformations. Common choices include:

- **Physical state variables:** Directly measurable quantities (position, velocity, temperature)
- **Modal coordinates:** Eigenvectors of the system matrix in [[Characteristic Equation]] decomposition
- **Phase variables:** Successive derivatives of the output signal
- **Canonical forms:** [[Jordan canonical form]], controllable canonical form, observable canonical form

### Relationship to Other Concepts

1. **Connection to [[Ordinary Differential Equations (ODEs)]]:**
   - State-space form is a systematic way to express systems of first-order ODEs
   - Higher-order differential equations are decomposed into first-order state equations

2. **Connection to [[Characteristic Equation]] and [[Eigenvalues]]:**
   - Eigenvalues of matrix $\mathbf{A}$ determine system stability and response characteristics
   - Define the [[Poles|poles]] of the system transfer function

3. **Connection to [[Kalman Filter]]:**
   - Uses state-space representation for optimal state estimation from noisy measurements

4. **Connection to [[Linear Quadratic Regulator]]:**
   - Finds optimal control inputs based on state feedback to minimize cost functional

## Classification and Variants

### By System Type

1. **Continuous-Time:** State evolves continuously according to differential equations
2. **Discrete-Time:** State updates occur at discrete time intervals
3. **Hybrid:** Combination of continuous and discrete dynamics

### By Linearity

1. **Linear Systems:** State dynamics are linear functions of state and input
2. **Nonlinear Systems:** State dynamics contain nonlinear functions of state and input

## Applications in Engineering

### Spacecraft and Orbital Mechanics

In spacecraft dynamics, the state vector often includes:
$$
\mathbf{x} = \begin{bmatrix} \mathbf{r} \\ \mathbf{v} \\ \boldsymbol{\theta} \\ \boldsymbol{\omega} \end{bmatrix}
$$

Where:
- $\mathbf{r}$: [[Position]] vector
- $\mathbf{v}$: [[Velocity]] vector  
- $\boldsymbol{\theta}$: Attitude angles
- $\boldsymbol{\omega}$: Angular [[Velocity]]

### Control Systems

For [[Control Systems]], state feedback allows implementation of sophisticated control laws:
- Pole placement
- Optimal control ([[Linear Quadratic Regulator|LQR]])
- [[Adaptive Control Theory]]

### Estimation

The state vector is the target quantity in estimation problems:
- [[Kalman Filter]] for linear systems
- Extended Kalman Filter for nonlinear systems
- Particle filters for general nonlinear cases

## See Also

- [[State Transition Matrix]]
- [[Kalman Filter]]
- [[Linear Quadratic Regulator]]
- [[Control Systems]]
- [[Ordinary Differential Equations (ODEs)]]
- [[State Vector Propagation]]
- [[Phase Space]]
- [[Observability]]
- [[Controllability]]

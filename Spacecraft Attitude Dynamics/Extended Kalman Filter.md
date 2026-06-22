## Formal Definition

The **Extended Kalman Filter (EKF)** is a non-linear version of the Kalman Filter which linearizes the system’s dynamics and measurement models at each time step about the current state estimate. By using **Jacobian matrices** to calculate a local linear approximation, the EKF can estimate the state of systems governed by non-linear differential equations, such as a satellite’s orbital trajectory or its attitude during complex maneuvers. It remains the industry standard for spacecraft navigation, despite newer alternatives like the Unscented Kalman Filter (UKF), due to its computational efficiency and well-understood behavior.



## Historical Development

### Key Milestones
- **1960:** Rudolf Kalman publishes the linear filter theory.
- **1961–1967:** **Stanley Schmidt** and colleagues at NASA Ames modify the filter to handle the non-linear trajectories of the **Apollo program**, effectively creating the first EKF to navigate the Command Module to the Moon.
- **1970s:** The EKF is formalized as a standard recursive estimator for non-linear stochastic systems in the landmark textbook by Gelb.
- **Present:** The EKF is used in nearly every GPS receiver, smartphone, and satellite bus for real-time position and orientation estimation.

### Foundational Contributors
1. **Stanley Schmidt (1927–2015):** The NASA engineer who pioneered the practical implementation of the "Extended" Kalman Filter for spaceflight.
2. **Rudolf Kalman:** Provided the original optimal linear estimation framework.

## Mathematical Formulation

The EKF follows the same **Predict-Correct** cycle as the standard KF, but with the inclusion of linearization.

### 1. Prediction (Time Update)
Instead of a matrix $\mathbf{A}$, we use the full non-linear physics function $f$:
- **State Predict:** $\mathbf{\hat{x}}_{k|k-1} = f(\mathbf{\hat{x}}_{k-1|k-1}, \mathbf{u}_k)$
- **[[Covariance]] Predict:** $\mathbf{P}_{k|k-1} = \mathbf{F}_k \mathbf{P}_{k-1|k-1} \mathbf{F}_k^T + \mathbf{Q}_k$
  *Where $\mathbf{F}_k$ is the **Jacobian** of $f$ evaluated at the current estimate.*

### 2. Correction (Measurement Update)
Instead of a matrix $\mathbf{C}$ or $\mathbf{H}$, we use the non-linear sensor function $h$:
- **Innovation:** $\mathbf{y}_k = \mathbf{z}_k - h(\mathbf{\hat{x}}_{k|k-1})$
- **Kalman Gain:** $\mathbf{K}_k = \mathbf{P}_{k|k-1} \mathbf{H}_k^T (\mathbf{H}_k \mathbf{P}_{k|k-1} \mathbf{H}_k^T + \mathbf{R}_k)^{-1}$
- **State Update:** $\mathbf{\hat{x}}_{k|k} = \mathbf{\hat{x}}_{k|k-1} + \mathbf{K}_k \mathbf{y}_k$
  *Where $\mathbf{H}_k$ is the **Jacobian** of $h$ evaluated at the current estimate.*



## Fundamental Principles

### Core Assumptions
1. **Local Linearity:** Assumes that the system is "linear enough" over a single time step (e.g., 0.1 seconds) for the Jacobian approximation to hold.
2. **Gaussian Noise:** Assumes that process noise ($\mathbf{Q}$) and measurement noise ($\mathbf{R}$) are zero-mean Gaussian [[White Noise]].

### Governing Laws
- **[[Taylor Series Expansion]] Expansion:** The EKF is essentially a first-order Taylor approximation of the system.
- **Bayes' Theorem:** The filter updates the "posterior" probability of the state based on the "prior" prediction and new evidence.

## Theoretical Framework

### The Problem of Divergence
Because the EKF uses a linear approximation, it can "drift" if the system is highly non-linear or if the initial guess is poor. This is called **Filter Divergence**. To prevent this, engineers must:
1.  **Tune the $\mathbf{Q}$ and $\mathbf{R}$ matrices** carefully.
2.  **Ensure the frequency is high enough** so that the "jump" between steps is small enough for the tangent line to be accurate.

## Physical Interpretation

### The "Follow the Tangent" Method
Imagine you are walking on a circular track in the dark. 
- You have a map (the physics model $f$). 
- At every step, you feel the ground and guess the local slope of the track (the Jacobian $\mathbf{F}$). 
- You walk in a straight line for one inch along that slope. 
- Then, you open your eyes for a split second (the measurement $\mathbf{z}$) to see how far you strayed from the actual curve and "correct" your position. 
- You repeat this thousands of times. Even though you are walking in tiny straight segments, you successfully "navigate" the circle.

## Advantages and Limitations

### Strengths
1.  **Computational Efficiency:** Much faster than "Particle Filters" or "Unscented Filters" for systems with many states.
2.  **Standardization:** Decades of heritage; almost every aerospace engineer knows how to debug an EKF.

### Limitations
1.  **Sub-Optimal:** Unlike the linear KF, the EKF is not "optimal" because the transformation of a Gaussian through a non-linear function is not truly Gaussian.
2.  **Jacobian Complexity:** Manually deriving the partial derivatives for complex 6-DOF motion is tedious and prone to human error.

## Applications

### Spacecraft Missions
1.  **Attitude Estimation:** Combining Star Tracker angles with high-rate [[Gyroscope]] data.
2.  **Relative Navigation:** Estimating the position of a docking target relative to a chasing spacecraft.
3.  **Entry, Descent, and Landing (EDL):** Fusing radar, IMU, and camera data to land the Perseverance rover on Mars.

## See Also

- [[Kalman Filter]]
- [[Linearization]]
- [[Jacobian Matrix]]
- [[State-Space Representation]]

## Recommended Tags:
#navigation #estimation #EKF #Kalman-filter #nonlinear-dynamics #aerospace-engineering #GNC
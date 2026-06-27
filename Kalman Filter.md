---
title: Kalman Filter
tags:
  - control theory
  - estimation theory
  - signal processing
  - spacecraft systems
---

# Kalman Filter

## Formal Definition

The **Kalman filter** is an optimal recursive algorithm for estimating the state of a linear [[Dynamical Systems|dynamical system]] from noisy measurements. It sequentially processes incoming data to produce minimum-variance estimates of the system state, incorporating both process noise and measurement noise statistics. The Kalman filter is the optimal linear unbiased estimator for Gaussian noise and is fundamental to [[Control Systems]], spacecraft tracking, navigation, [[Signal Processing]], and state estimation in aerospace applications.

## Historical Development

### Key Milestones
- **1960:** Rudolf Kalman publishes foundational paper on recursive filtering
- **1961:** Kalman-Bucy paper extends to continuous-time filtering
- **1962–1963:** NASA Apollo Guidance Computer implements discrete Kalman filter
- **1965:** Stratonovich publishes parallel continuous-time results
- **1970s:** Extended Kalman Filter (EKF) for nonlinear systems
- **1990s:** Unscented Kalman Filter (UKF); particle filters
- **2000s–Present:** Autonomous systems, robotics, GPS/GNSS integration

### Foundational Contributors
1. **Rudolf E. Kalman (1930–2016):** Invention and optimal filtering theory
2. **Richard S. Bucy (1935–):** Continuous-time extension; Kalman-Bucy filter
3. **H.W. Sorenson:** Early applications and modifications
4. **Stanley Schmidt:** NASA Apollo computer implementation
5. **Simon Haykin:** Comprehensive treatment and adaptive extensions

## Mathematical Formulation

### Discrete-Time Linear System

**State-space model:**
$$
\mathbf{x}_{k+1} = \mathbf{A}\mathbf{x}_k + \mathbf{B}\mathbf{u}_k + \mathbf{w}_k
$$

**Measurement model:**
$$
\mathbf{z}_k = \mathbf{H}\mathbf{x}_k + \mathbf{v}_k
$$

Where:
- $\mathbf{x}_k \in \mathbb{R}^n$: state vector
- $\mathbf{z}_k \in \mathbb{R}^m$: measurement vector
- $\mathbf{w}_k$: process noise, $\mathbf{w}_k \sim \mathcal{N}(0, \mathbf{Q})$
- $\mathbf{v}_k$: measurement noise, $\mathbf{v}_k \sim \mathcal{N}(0, \mathbf{R})$
- $\mathbf{A}, \mathbf{B}, \mathbf{H}$: system matrices

### Kalman Filter Equations

**Time Update (Prediction):**

Prior estimate:
$$
\hat{\mathbf{x}}_{k|k-1} = \mathbf{A}\hat{\mathbf{x}}_{k-1|k-1} + \mathbf{B}\mathbf{u}_{k-1}
$$

Prior error covariance:
$$
\mathbf{P}_{k|k-1} = \mathbf{A}\mathbf{P}_{k-1|k-1}\mathbf{A}^T + \mathbf{Q}
$$

**Measurement Update (Correction):**

Kalman gain:
$$
\mathbf{K}_k = \mathbf{P}_{k|k-1}\mathbf{H}^T(\mathbf{H}\mathbf{P}_{k|k-1}\mathbf{H}^T + \mathbf{R})^{-1}
$$

Updated estimate:
$$
\hat{\mathbf{x}}_{k|k} = \hat{\mathbf{x}}_{k|k-1} + \mathbf{K}_k(\mathbf{z}_k - \mathbf{H}\hat{\mathbf{x}}_{k|k-1})
$$

Updated error covariance:
$$
\mathbf{P}_{k|k} = (I - \mathbf{K}_k\mathbf{H})\mathbf{P}_{k|k-1}
$$

### Continuous-Time Kalman-Bucy Filter

**Continuous state model:**
$$
\dot{\mathbf{x}}(t) = \mathbf{A}(t)\mathbf{x}(t) + \mathbf{B}(t)\mathbf{u}(t) + \mathbf{w}(t)
$$

**Continuous measurement:**
$$
\mathbf{z}(t) = \mathbf{H}(t)\mathbf{x}(t) + \mathbf{v}(t)
$$

**Filter equations:**

State estimate:
$$
\dot{\hat{\mathbf{x}}}(t) = \mathbf{A}(t)\hat{\mathbf{x}}(t) + \mathbf{B}(t)\mathbf{u}(t) + \mathbf{K}(t)(\mathbf{z}(t) - \mathbf{H}(t)\hat{\mathbf{x}}(t))
$$

Kalman gain:
$$
\mathbf{K}(t) = \mathbf{P}(t)\mathbf{H}^T(t)\mathbf{R}^{-1}(t)
$$

Riccati differential equation:
$$
\dot{\mathbf{P}}(t) = \mathbf{A}(t)\mathbf{P}(t) + \mathbf{P}(t)\mathbf{A}^T(t) - \mathbf{P}(t)\mathbf{H}^T(t)\mathbf{R}^{-1}(t)\mathbf{H}(t)\mathbf{P}(t) + \mathbf{Q}(t)
$$

## Optimality and Properties

### Optimality Criterion

**Kalman filter minimizes mean-squared error:**
$$
J = \mathbb{E}[\|\mathbf{x}_k - \hat{\mathbf{x}}_{k|k}\|^2]
$$

Among all linear unbiased estimators.

### Assumptions

1. **Linear system:** State and measurement equations linear
2. **Gaussian noise:** Process and measurement noise white, Gaussian
3. **Known statistics:** $\mathbf{Q}, \mathbf{R}$ known (or estimable)
4. **Initial conditions:** Initial state and covariance known (or assumed)
5. **No unknown inputs:** All disturbances are modeled noise

### Key Properties

**Unbiased:** $\mathbb{E}[\mathbf{x}_k - \hat{\mathbf{x}}_{k|k}] = 0$ (no systematic error)

**Minimum variance:** Lowest possible error covariance among linear unbiased filters

**Recursive:** Uses only previous estimate and current measurement (memory-efficient)

**Closed-loop stability:** Under controllability/observability conditions

## Connection to Related Concepts

1. **Connection to [[Control Systems]]:**
   - Observer for state estimation
   - Basis for [[Linear Quadratic Regulator]] with noise

2. **Connection to [[Signal Processing]]:**
   - Optimal Wiener filter for known statistics
   - Noise reduction and smoothing

3. **Connection to [[Covariance]]:**
   - Error covariance matrix $\mathbf{P}$ quantifies estimation uncertainty
   - Used in sensor fusion

4. **Connection to [[State Vector]]:**
   - Estimates entire state from partial/noisy measurements

## Extensions and Nonlinear Variants

### Extended Kalman Filter (EKF)

**For nonlinear systems:**
$$
\mathbf{x}_{k+1} = \mathbf{f}(\mathbf{x}_k, \mathbf{u}_k) + \mathbf{w}_k
$$
$$
\mathbf{z}_k = \mathbf{h}(\mathbf{x}_k) + \mathbf{v}_k
$$

**Approach:** Linearize about current estimate using Jacobians:
$$
\mathbf{F}_k = \left.\frac{\partial \mathbf{f}}{\partial \mathbf{x}}\right|_{\hat{\mathbf{x}}_k}, \quad \mathbf{H}_k = \left.\frac{\partial \mathbf{h}}{\partial \mathbf{x}}\right|_{\hat{\mathbf{x}}_k}
$$

Apply Kalman filter equations with Jacobian matrices.

**Limitation:** Linearization errors; approximation only.

### Unscented Kalman Filter (UKF)

**Deterministic sampling approach:**

Select sigma points (deterministically chosen sample points) to capture mean and covariance of state distribution.

**Advantages over EKF:**
- No explicit Jacobian computation
- Better accuracy for highly nonlinear systems
- Similar computational cost

### Particle Filter

**Sequential Monte Carlo approach:**

Represent posterior distribution by weighted particles; resample based on measurement likelihood.

**Advantages:**
- Handles non-Gaussian noise
- Suitable for nonlinear, non-Gaussian systems

**Disadvantage:** Higher computational cost for high-dimensional state spaces.

## Practical Initialization and Tuning

### Initial Conditions

**Initial state estimate:** $\hat{\mathbf{x}}_{0|0}$ from prior knowledge or first measurement

**Initial covariance:** $\mathbf{P}_{0|0}$ represents uncertainty in initial estimate

Large values → trust measurements; small values → trust model

### Noise Covariance Selection

**Process noise** $\mathbf{Q}$: Captures model uncertainty

- Too small: Filter trusts model too much; slow response to real changes
- Too large: Filter trusts measurements too much; noisy estimates

**Measurement noise** $\mathbf{R}$: Sensor specifications

- Often known from sensor documentation
- Ratio $\mathbf{Q}/\mathbf{R}$ critical: determines filter responsiveness

### Adaptive Kalman Filter

**Problem:** True noise statistics often unknown

**Solution:** Estimate $\mathbf{Q}, \mathbf{R}$ online using innovation sequence:
$$
\mathbf{y}_k = \mathbf{z}_k - \mathbf{H}\hat{\mathbf{x}}_{k|k-1}
$$

**Method:** Expectation-Maximization (EM) or maximum likelihood estimation.

## Applications

### GPS/GNSS Navigation

**Sensor fusion:** Combine GPS (accurate long-term, slow update) with inertial measurement unit (IMU) (high-rate, drifts over time)

**State:** Position, velocity, orientation

**Benefits:** Smooth estimate; fills GPS outages; better accuracy than either sensor alone.

### Spacecraft Attitude Estimation

**Spacecraft attitude control using:**
- Star trackers (occasional high-accuracy observations)
- Rate gyros (continuous but drifting)
- Sun sensors (coarse attitude)

**Kalman filter:** Optimal fusion of disparate sensors

**Application:** [[Attitude Determination and Control System (ADCS)]]

### Tracking and Ballistics

**Radar tracking of aircraft:**
- Measurement: Range, azimuth, elevation (noisy)
- State: Position, velocity

**Kalman filter:** Smooth trajectory; predict future position

**Military/civilian:** Air traffic control, missile guidance

### Economics and Finance

**Asset price tracking:**
- Observations: Daily stock prices (noisy)
- State: "True" asset value (latent variable)

Kalman filter estimates hidden state from noisy price data.

## Computational Considerations

### Stability Issues

**Numerically sensitive:** Covariance matrix $\mathbf{P}$ can become non-positive-definite

**Square-root filter:** Factor $\mathbf{P} = \mathbf{S}\mathbf{S}^T$; better numerical conditioning

**Joseph form covariance update:** Guarantees positive-definiteness

### Computational Cost

**Standard Kalman:** $O(n^3)$ per timestep (matrix operations)

**Applications:** Real-time systems demand efficient implementation

Optimizations:
- Structured matrices (sparse)
- Parallel computation
- Fixed-lag smoothing (trade latency for accuracy)

## Relationship to Other Estimators

### Comparison to Wiener Filter

**Kalman filter:** Time-varying gain; handles time-varying noise, nonstationary signals

**Wiener filter:** Fixed gain; optimal for stationary signals with known spectral characteristics

**Connection:** Kalman converges to Wiener for steady-state time-invariant systems.

### Comparison to Observers

**Deterministic observer:** Assumes no noise; ensures state convergence

**Kalman filter:** Probabilistic; minimizes estimation error variance

**Relationship:** Observer gain similar to Kalman gain; Kalman optimal for stochastic case.

## Advanced Topics

### Sensor Fusion Framework

**Multiple sensors:** GPS, IMU, magnetometer, barometer

**Unified Kalman filter:** Accommodates varying measurement rates, sensor outages

**Augmented state:** Include sensor biases and scale factors as state variables

### Constrained Kalman Filter

**Constraints:** State must satisfy physical bounds (e.g., angle modulo 2π)

**Modification:** Project updated state onto constraint manifold

**Application:** Spacecraft [[Attitude]] estimation (quaternion normalization)

### Dual State and Parameter Estimation

**Unknown parameters:** $\mathbf{x}_{k+1} = \mathbf{A}(\theta)\mathbf{x}_k + \mathbf{w}_k$

**Extended state vector:** $[\mathbf{x}^T, \theta^T]^T$

**Capability:** Simultaneously estimate state and parameters (adaptive identification)

## See Also

- [[Control Systems]]
- [[Control Theory]]
- [[Signal Processing]]
- [[State Vector]]
- [[Covariance]]
- [[Linear Quadratic Regulator]]
- [[Observer Design]]
- [[Attitude Determination and Control System (ADCS)]]
- [[Navigation Systems]]
- [[Estimation Theory]]

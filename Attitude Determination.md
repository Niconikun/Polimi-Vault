---
title: Attitude Determination
tags:
  - spacecraft systems
  - estimation theory
  - guidance navigation control
  - attitude determination
---

# Attitude Determination

## Formal Definition

**Attitude determination** is the process of estimating a spacecraft's orientation ([[Attitude|attitude]]) in inertial or orbital reference frames using sensor measurements and estimation algorithms. Attitude determination translates raw sensor data (sun direction, star positions, magnetic field, angular rates) into a unified attitude representation (quaternion, Euler angles, or direction cosine matrix). It forms the sensing component of an [[Attitude Determination and Control System (ADCS)|ADCS]], providing state feedback for [[Attitude Control|attitude control]] and enabling mission operations such as pointing, communications, and science observations. Modern attitude determination algorithms (primarily [[Kalman Filter|Kalman filtering]]) optimally fuse multiple sensors to achieve high-accuracy estimates despite measurement noise, sensor biases, and environmental disturbances.

## Historical Development

### Key Milestones
- **1960s:** Early attitude systems use analog sun/earth sensors; simple proportional-integral filters
- **1970s:** Digital flight computers enable more complex algorithms; TRIAD method popularized
- **1980s:** [[Kalman Filter|Kalman filter]] adopted for attitude estimation; multi-sensor fusion
- **1990s:** Star tracker development; arc-minute accuracy achievable
- **2000s:** Extended Kalman Filters (EKF), multiplicative formulations; autonomous algorithms
- **2010s–Present:** Machine learning for sensor fusion; real-time optimal estimation

### Foundational Contributors
1. **Richard Bellman (1920–1984):** Dynamic programming; optimal estimation concepts
2. **Rudolf Kálmán (1930–2016):** [[Kalman Filter|Kalman filter]] (1960); recursion optimal estimation
3. **Davenport Kailath:** K-matrix method (1968); deterministic multi-vector solution
4. **David Vallado (1960–present):** Attitude determination algorithms; standard references

## Problem Formulation

### Attitude Representations

**Quaternion** (primary in modern algorithms):
$$
\mathbf{q} = \begin{bmatrix} q_0 \\ q_1 \\ q_2 \\ q_3 \end{bmatrix}, \quad q_0^2 + q_1^2 + q_2^2 + q_3^2 = 1
$$

**Rotation matrix** (DCM—Direction Cosine Matrix):
$$
\mathbf{R} \in SO(3), \quad \mathbf{R}^T\mathbf{R} = \mathbf{I}, \quad \det(\mathbf{R}) = 1
$$

**Euler angles** (deprecated for algorithms; gimbal lock):
$$
(\phi, \theta, \psi) \text{ with singularities at } \theta = \pm 90°
$$

### Measurement Models

**Vector measurement** (sun, star, magnetic field):
$$
\mathbf{y}_i = \mathbf{R} \mathbf{b}_i + \mathbf{n}_i
$$

Where:
- $\mathbf{R}$: Attitude (rotation matrix to be estimated)
- $\mathbf{b}_i$: Reference vector in body frame (known; catalog)
- $\mathbf{y}_i$: Measured vector in inertial frame (sensor output)
- $\mathbf{n}_i$: Measurement noise (zero-mean, known covariance)

**Rate measurement** (gyroscope):
$$
\boldsymbol{\omega}_{\text{meas}} = \boldsymbol{\omega}_{\text{true}} + \mathbf{b}_{\text{gyro}} + \mathbf{n}_{\text{gyro}}
$$

Where $\mathbf{b}_{\text{gyro}}$ is gyro bias (slowly varying); $\mathbf{n}_{\text{gyro}}$ is noise.

### Estimation Objectives

**Minimize cost function:**
$$
J = \sum_i w_i |\mathbf{y}_i - \mathbf{R} \mathbf{b}_i|^2 + \text{regularization}
$$

**Subject to:** Attitude constraint (rotation matrix orthogonality or unit quaternion).

**Output:** Best-estimate attitude + uncertainty (covariance).

## Deterministic Algorithms

### TRIAD Method (Davenport, 1968)

**Inputs:**
- Two measurement vectors: $\mathbf{v}_1, \mathbf{v}_2$ (e.g., sun direction, magnetic field)
- Corresponding reference vectors: $\mathbf{r}_1, \mathbf{r}_2$ (known from models/catalogs)

**Assumptions:**
- Vectors not parallel
- No noise (idealized)

**Algorithm:**

**Step 1:** Construct orthonormal frame from measurements:
$$
\hat{\mathbf{m}}_1 = \frac{\mathbf{v}_1}{|\mathbf{v}_1|}
$$
$$
\hat{\mathbf{m}}_2 = \frac{\mathbf{v}_1 \times \mathbf{v}_2}{|\mathbf{v}_1 \times \mathbf{v}_2|}
$$
$$
\hat{\mathbf{m}}_3 = \hat{\mathbf{m}}_1 \times \hat{\mathbf{m}}_2
$$

**Step 2:** Construct reference frame:
$$
\hat{\mathbf{r}}_1 = \frac{\mathbf{r}_1}{|\mathbf{r}_1|}, \quad \hat{\mathbf{r}}_2 = \frac{\mathbf{r}_1 \times \mathbf{r}_2}{|\mathbf{r}_1 \times \mathbf{r}_2|}, \quad \hat{\mathbf{r}}_3 = \hat{\mathbf{r}}_1 \times \hat{\mathbf{r}}_2
$$

**Step 3:** Compute rotation matrix:
$$
\mathbf{M} = [\hat{\mathbf{m}}_1 | \hat{\mathbf{m}}_2 | \hat{\mathbf{m}}_3], \quad \mathbf{R} = \mathbf{M} \mathbf{R}_{\text{ref}}^T
$$

**Step 4:** Convert to quaternion (if needed).

**Advantages:** Deterministic; fast; no iteration.

**Disadvantages:** Ignores measurement noise; doesn't exploit gyro rates; requires exactly 2 vectors.

### Davenport K-Matrix Method

**Inputs:** Multiple vector pairs (2 or more); weighting (measurement covariance).

**Objective:** Minimize weighted residual:
$$
J = \sum_i a_i |\mathbf{y}_i - \mathbf{R}\mathbf{b}_i|^2
$$

**Solution:** Eigenvalue problem:
$$
\mathbf{K} \mathbf{x} = \lambda \mathbf{x}
$$

Where $\mathbf{K}$ is correlation matrix; $\mathbf{x}$ eigenvalue yields quaternion.

**Advantages:**
- Multi-sensor optimal (under 3-axis Gaussian noise assumption)
- Accounts for measurement weights
- Deterministic

**Disadvantages:** 
- No time evolution (static)
- Doesn't use rate information
- Requires multiple independent vectors

### QUEST Algorithm (Quaternion Estimator)

**Goal:** Same as K-matrix but computationally faster.

**Key difference:** Use Davenport's constant gain Kalman filter gain, not full Kalman iteration.

**Efficiency:** ~50% faster than eigenvalue decomposition; suitable for real-time.

## Kalman Filter Approach

### Extended Kalman Filter (EKF) for Attitude

**State vector:**
$$
\mathbf{x} = \begin{bmatrix} \mathbf{q} \\ \mathbf{b}_{\text{gyro}} \end{bmatrix} \in \mathbb{R}^7
$$

Where $\mathbf{q}$ is quaternion (4 components); $\mathbf{b}_{\text{gyro}}$ is gyro bias (3 components).

**Prediction step** (using gyroscope):
$$
\mathbf{q}_{k+1|k} = \mathbf{q}_{k|k} \oplus \Delta\mathbf{q}(\boldsymbol{\omega}_{\text{meas}} - \mathbf{b}_{\text{gyro},k|k})
$$

Where $\Delta\mathbf{q}$ represents incremental quaternion from angular velocity.

**Measurement update** (using sun sensor, star tracker, etc.):

Given measurement $\mathbf{z}_k$ (unit vector in inertial frame):
$$
\mathbf{z}_k = \mathbf{R}(\mathbf{q}_{k|k-1}) \mathbf{b} + \mathbf{n}_k
$$

Expected measurement (prior):
$$
\hat{\mathbf{z}}_{k|k-1} = \mathbf{R}(\mathbf{q}_{k|k-1}) \mathbf{b}
$$

Innovation (residual):
$$
\mathbf{y}_k = \mathbf{z}_k - \hat{\mathbf{z}}_{k|k-1}
$$

Updated quaternion:
$$
\mathbf{q}_{k|k} = \mathbf{q}_{k|k-1} + \mathbf{K}_k \mathbf{y}_k
$$

**Advantages:**
- Optimal under linear Gaussian assumptions
- Natural fusion of multiple sensor types
- Estimates state + bias
- Handles sensor dropouts gracefully

**Disadvantages:**
- Quaternion kinematics nonlinear (requires extended/unscented filter)
- Tuning process noise covariance Q, measurement covariance R
- Computational cost

### Multiplicative Kalman Filter (MKF)

**State:** Error quaternion + bias (not full quaternion).

**Advantage:** Avoids quaternion normalization issues; more numerically stable.

**Flight standard:** Most spacecraft flight software uses MKF variant.

### Unscented Kalman Filter (UKF)

**Approach:** Propagate sigma points through nonlinear kinematics.

**Advantage:** Higher accuracy than EKF for highly nonlinear problems.

**Disadvantage:** More computation; rarely needed for attitude (EKF typically sufficient).

## Sensor-Specific Measurement Models

### Sun Sensor

**Output:** Two angles (pitch, yaw relative to sun).

**Measurement equation:**
$$
\begin{bmatrix} \theta_s \\ \phi_s \end{bmatrix} = \arctan\left(\frac{y_s}{x_s}, \frac{z_s}{\sqrt{x_s^2 + y_s^2}}\right) + \mathbf{n}_s
$$

Where $(x_s, y_s, z_s)$ is sun direction in spacecraft frame (from sun vector after rotation).

**Covariance:** Typically diagonal; separate pitch/yaw uncertainties.

### Star Tracker

**Output:** Attitude quaternion directly (from image processing).

**High accuracy:** ±0.01–0.1° (image correlation + catalog matching).

**Covariance:** Often provided by tracker firmware.

**Integration:** Treated as single quaternion measurement; update directly.

### Earth Sensor

**Output:** Two angles (roll, pitch from horizon).

**Measurement equation:**
$$
\begin{bmatrix} \alpha \\ \beta \end{bmatrix} = f_{\text{Earth}}(\mathbf{R}) + \mathbf{n}_e
$$

Where $f_{\text{Earth}}$ is geometric projection; typically ±0.5–1° accuracy.

### Gyroscope

**Raw output:** Angular velocity + bias + noise.

**Integration:** Feed forward to prediction step; bias estimated as state.

**Bias modeling:**
- Constant bias (first order)
- Bias rate equation: $\dot{\mathbf{b}} = -\tau_b^{-1} \mathbf{b} + \mathbf{n}_b$ (low-pass filter)

### Magnetometer

**Output:** Magnetic field direction in body frame.

**Measurement equation:**
$$
\mathbf{B}_{\text{meas}} = \mathbf{R}^T \mathbf{B}_{\text{model}}(lat, lon, date) + \mathbf{n}_B + \mathbf{d}_{\text{bias}}
$$

Where $\mathbf{d}_{\text{bias}}$ is spacecraft magnetic dipole (static disturbance).

**Use:** Coarse attitude correction; often downweighted if stronger sensors available.

## Practical Implementation Considerations

### Sensor Scheduling

**Strategy:** Activate sensors sequentially to balance power/accuracy.

**Example (nanosatellite):**
- Coarse sun sensor always on (power ~0.5 W)
- Star tracker activated periodically (~5 min intervals; 10 W when active)
- Gyro continuous (~1 W)
- Update rate: 1–10 Hz

### Sensor Outages and Recovery

**Scenario:** Star tracker fails (clouds, sun blinding).

**Behavior:** Continue using sun sensor + gyro; accuracy degrades temporarily.

**Recovery:** When star tracker available again, Kalman filter re-converges.

**Time constant:** Depends on process noise tuning; typically 10–100 seconds.

### Initial Attitude Acquisition

**Cold start:** Spacecraft just powered on; attitude unknown.

**Method 1 (Slew to sun):** Command spacecraft to point at sun (sun sensors); safe mode attitude.

**Method 2 (Star tracker search):** If star tracker capable of blind search; faster.

**Method 3 (Gyro integration):** Use gyro plus known initial quaternion (attitude memo from previous mission phase).

### Attitude Singularities and Discontinuities

**Gimbal lock (Euler angles):** Avoided by using quaternions.

**Quaternion sign ambiguity:** $\mathbf{q}$ and $-\mathbf{q}$ represent same rotation; filter handles via continuity.

**Rate singularities:** At poles in some parameterizations; quaternion kinematics smooth everywhere.

## Performance Metrics

### Estimation Accuracy

**RMS error over test interval:**
$$
\sigma_{\text{error}} = \sqrt{\frac{1}{N} \sum_k ||\mathbf{q}_{\text{true}} - \mathbf{q}_{\text{est}}||^2}
$$

**Typical values:**
- Coarse: ±1–5° (sun sensor only)
- Medium: ±0.1–1° (multiple sensors, no star tracker)
- Fine: ±0.01–0.1° (star tracker + gyro)

### Convergence Time

**Time for filter to reach steady-state accuracy after sensor loss/recovery.**

**Typical:** 10–100 seconds (depends on process noise, measurement noise).

### Robustness to Biases

**Ability to estimate and correct sensor biases (especially gyro).**

**Metric:** RMS error vs. time when bias deliberately introduced.

## Connection to Other Concepts

1. **Connection to [[Attitude]]:**
   - Determines this fundamental spacecraft parameter

2. **Connection to [[Attitude Control]]:**
   - Provides state feedback for closed-loop control

3. **Connection to [[Kalman Filter]]:**
   - Primary algorithm used

4. **Connection to [[Attitude Determination and Control System (ADCS)]]:**
   - Forms sensing component of ADCS

5. **Connection to [[Control Theory]]:**
   - Observer design; state estimation

## See Also

- [[Attitude]]
- [[Attitude Control]]
- [[Attitude Determination and Control System (ADCS)]]
- [[Kalman Filter]]
- [[Quaternions]]
- [[TRIAD Algorithm]]
- [[Sensor Fusion]]
- [[Estimation Theory]]
- [[Spacecraft Navigation]]
- [[Gyroscopic Sensors]]

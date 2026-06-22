## Formal Definition

A **Kalman Filter** is an iterative mathematical algorithm that uses a series of measurements observed over time (containing noise and inaccuracies) to produce estimates of unknown variables that tend to be more accurate than those based on a single measurement alone. In spacecraft dynamics, it is primarily used for **State Estimation**—combining high-frequency but "drifting" data from IMUs with low-frequency but "absolute" data from Star Trackers or GPS. It operates via a prediction-correction loop, weighting each input based on its calculated uncertainty ([[covariance]]).



## Historical Development

### Key Milestones
- **1960:** Rudolf E. Kálmán publishes his seminal paper *A New Approach to Linear Filtering and Prediction Problems*.
- **1961:** Stanley Schmidt at NASA Ames realizes the filter’s potential for the Apollo program, leading to the development of the **[[Extended Kalman Filter]] (EKF)** to handle non-linear orbital trajectories.
- **1969:** The Apollo 11 Lunar Module uses a Kalman Filter to process radar data during the descent to the lunar surface.
- **Present:** The "Unscented Kalman Filter" (UKF) and "Particle Filters" are used for highly non-linear deep-space navigation and robotic docking.

### Foundational Contributors
1. **Rudolf E. Kálmán (1930–2016):** The Hungarian-American mathematician who derived the recursive optimal filter.
2. **Stanley Schmidt:** The NASA engineer who adapted the filter for real-world, non-linear aerospace applications.

## Mathematical Formulation

The filter operates in two distinct phases:

### 1. The Prediction (Time Update)
The filter projects the current state ($\mathbf{\hat{x}}$) and uncertainty ($\mathbf{P}$) forward in time using a physics model:
- **State Predict:** $\mathbf{\hat{x}}_{k|k-1} = \mathbf{F} \mathbf{\hat{x}}_{k-1|k-1}$
- **[[Covariance]] Predict:** $\mathbf{P}_{k|k-1} = \mathbf{F} \mathbf{P}_{k-1|k-1} \mathbf{F}^T + \mathbf{Q}$

### 2. The Correction (Measurement Update)
When a new sensor reading ($\mathbf{z}_k$) arrives, the filter calculates the **Kalman Gain** ($\mathbf{K}$) to decide how much to trust the sensor vs. the model:
- **Kalman Gain:** $\mathbf{K}_k = \mathbf{P}_{k|k-1} \mathbf{H}^T (\mathbf{H} \mathbf{P}_{k|k-1} \mathbf{H}^T + \mathbf{R})^{-1}$
- **State Update:** $\mathbf{\hat{x}}_{k|k} = \mathbf{\hat{x}}_{k|k-1} + \mathbf{K}_k (\mathbf{z}_k - \mathbf{H} \mathbf{\hat{x}}_{k|k-1})$
- **[[Covariance]] Update:** $\mathbf{P}_{k|k} = (\mathbf{I} - \mathbf{K}_k \mathbf{H}) \mathbf{P}_{k|k-1}$



## Fundamental Principles

### Core Assumptions
1. **Gaussian Noise:** Assumes that sensor errors and model errors follow a normal (Bell curve) distribution.
2. **Linearity:** The basic Kalman Filter assumes the system is linear (though the **EKF** is used to bypass this in spaceflight).
3. **Recursive Nature:** The filter does not need to remember the entire history of data; it only needs the estimate from the previous step.

### Governing Laws
- **Least Squares Estimation:** The filter is an "Optimal Estimator," meaning it minimizes the mean squared error of the estimated parameters.
- **Bayesian Inference:** The filter updates its "belief" about the spacecraft's state as new evidence (data) arrives.

## Theoretical Framework

### Sensor Fusion
The Kalman Filter solves the "Conflict of Information" problem. 
- If the **IMU** says the spacecraft turned 10.1 degrees.
- And the **Star Tracker** says the spacecraft turned 9.9 degrees.
- The Kalman Filter looks at the **[[Covariance]] Matrices** ($\mathbf{Q}$ and $\mathbf{R}$). If it knows the Star Tracker is usually very accurate but slow, and the IMU is fast but noisy, it might decide the true answer is **9.92 degrees**.

## Physical Interpretation

### The "Steady Hand"
Imagine trying to point a laser at a target while on a moving boat. Your "prediction" is where you think the boat is moving. Your "correction" is what your eyes see. If you have a steady hand, you ignore the minor jitters (sensor noise) but react to the big waves (true motion). The Kalman Filter is the mathematical "steady hand" for a spacecraft.

## Advantages and Limitations

### Strengths
1.  **Real-Time Processing:** Since it only needs the previous state, it uses very little memory.
2.  **Drift Correction:** It effectively "cancels out" the bias and drift inherent in inertial sensors.
3.  **Flexibility:** Can handle missing data; if a Star Tracker is blinded, the filter continues to predict the state using only the physics model.

### Limitations
1.  **"Tuning" Difficulty:** Defining the noise matrices ($\mathbf{Q}$ and $\mathbf{R}$) is more of an art than a science and requires extensive testing.
2.  **Divergence:** If the physics model is wrong (e.g., a thruster gets stuck open), the filter may "diverge" from reality and lose the spacecraft.

## Applications

### Spacecraft Systems
1.  **Orbit Determination:** Blending GPS, Ground Tracking, and Accelerometer data.
2.  **Attitude Estimation:** Merging Star Trackers, Gyroscopes, and Magnetometers.
3.  **Planetary Landing:** Used by the Mars Perseverance rover to fuse radar-altimeter data with visual terrain-relative navigation.

## See Also

- [[Inertial Measurement Unit (IMU)]]
- [[Star Tracker]]
- [[Quaternion]]
- [[Euler's Law]]

## Recommended Tags:
#state-estimation #kalman-filter #aerospace-engineering #navigation #control-theory #sensor-fusion #mathematics
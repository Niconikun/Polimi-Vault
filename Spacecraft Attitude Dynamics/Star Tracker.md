## Formal Definition

A **Star Tracker** is an optical [[attitude determination]] sensor that identifies and tracks the positions of stars to calculate a spacecraft's absolute orientation (attitude) relative to the celestial sphere. By capturing an image of the star field and comparing the detected patterns to an onboard star catalog using "Lost-In-Space" algorithms, the sensor provides highly accurate three-axis attitude data (typically within arcseconds). It is the most precise attitude sensor available and is essential for missions requiring fine pointing, such as space telescopes and high-resolution imaging satellites.



## Historical Development

### Key Milestones
- **1950s:** Early "Star Trackers" are developed for surface-to-surface missiles (like the SM-62 Snark) to provide mid-course navigation updates.
- **1966:** The **Orbiting Astronomical Observatory (OAO-2)** utilizes star trackers to maintain the extreme stability required for ultraviolet astronomy.
- **1990s:** The transition from heavy, vacuum-tube based sensors to solid-state **CCD** (Charge-Coupled Device) and later **CMOS** detectors significantly reduces mass and power.
- **2000s–Present:** Development of "Autonomous Star Trackers" that can determine attitude from scratch without any prior information (the "Lost-In-Space" capability).

### Foundational Contributors
1. **The Charles Stark Draper Laboratory:** Instrumental in developing the stellar-inertial guidance systems for the Apollo program.
2. **JPL (Jet Propulsion Laboratory):** Developed the high-reliability star trackers used for deep-space missions like Voyager and Cassini.

## Mathematical Formulation

### The Observation Vector
The sensor detects the unit vector $\mathbf{b}_i$ to several stars in the **Sensor Frame**. The onboard catalog provides the corresponding unit vectors $\mathbf{r}_i$ in the **Inertial Frame** (e.g., J2000).

### [[Wahba's Problem]]
The goal is to find the rotation matrix $\mathbf{A}$ (the attitude) that minimizes the loss function:
$$J(\mathbf{A}) = \frac{1}{2} \sum_{i=1}^{n} w_i | \mathbf{b}_i - \mathbf{A} \mathbf{r}_i |^2$$

### Component Breakdown
- **$w_i$:** Weighting factor for each star based on brightness/reliability.
- **$\mathbf{b}_i$:** Observed star vector.
- **$\mathbf{r}_i$:** Reference star vector from catalog.
- **$\mathbf{A}$:** The resulting [[Direction Cosine Matrix]] (DCM) or [[Quaternion]].



## Fundamental Principles

### Core Assumptions
1. **Inertial Fixedness:** Stars are so distant that their proper motion is negligible over the duration of a mission.
2. **Pattern Recognition:** Assumes the onboard catalog is sufficiently complete to identify a pattern from any orientation in the sky.

### Governing Laws
- **Projective Geometry:** Mapping 3D star positions onto a 2D detector plane.
- **Centroiding Algorithms:** Calculating the center of a star's light "blob" to sub-pixel accuracy to enhance precision.

## Theoretical Framework

### "Lost-In-Space" (LIS) Mode
When a spacecraft first turns on or recovers from a tumble, it has no idea where it is pointing. The LIS algorithm takes a single "snapshot," identifies the stars based on the angles between them (using methods like the **Pyramid Algorithm** or **Grid Algorithm**), and outputs the initial attitude. 

### Tracking Mode
Once the attitude is known, the sensor only looks at small windows where it *expects* stars to be in the next frame. This is much faster and requires less processing power than LIS mode.

## Physical Interpretation

### The Ultimate Map
A star tracker is essentially a digital version of an ancient mariner using a sextant. While a sun sensor only tells you where one "landmark" is, a star tracker sees thousands of landmarks simultaneously, allowing it to determine not just which way it's pointing, but also its exact "twist" (roll) around that line of sight.

## Advantages and Limitations

### Strengths
1. **Absolute Accuracy:** Provides arcsecond-level precision, far surpassing sun or Earth sensors.
2. **Three-Axis Sensing:** Can determine all three attitude components (Roll, Pitch, Yaw) from a single sensor.
3. **No Drift:** Unlike gyroscopes, star trackers do not suffer from bias drift over time.

### Limitations
1. **Blinding:** If the Sun, Moon, or bright Earth enters the [[Field of View]], the sensor is blinded (requiring a "Baffle").
2. **Processing Power:** Identifying patterns requires significant onboard memory and CPU cycles.
3. **Slew Limits:** If the spacecraft is spinning too fast, the stars "streak" across the detector, making identification impossible.

## Applications

### Spacecraft Systems
1. **Space Telescopes:** Hubble and JWST rely on star trackers to stay locked onto targets for days.
2. **Deep Space Navigation:** Probes like Juno (Jupiter) use star trackers to navigate where Earth-based landmarks are invisible.
3. **CubeSats:** Miniaturized star trackers now allow tiny satellites to perform complex Earth-imaging tasks.

## See Also

- [[Quaternion]]
- [[Sun Sensor]]
- [[Direction Cosine Matrix]]
- [[Gimbal Lock]]

## Recommended Tags:
#attitude-determination #star-trackers #spacecraft-sensors #astronomy #navigation #optical-sensors #arcsecond-precision
---
title: Local Sidereal Time
tags:
  - astronomy
  - timekeeping
  - orbital mechanics
  - coordinate systems
---

# Local Sidereal Time

## Formal Definition

**Local Sidereal Time (LST)** is a measure of the Earth's rotation relative to the stars, rather than the Sun. It represents the hour angle of the [[Vernal Equinox]] (First Point of Aries) at a particular geographic location. LST is fundamental to [[Coordinate System|coordinate systems]] in astronomy, satellite tracking, and telescope pointing, enabling conversion between Earth-based observations and celestial coordinates. Unlike [[Coordinated Universal Time (UTC)]], which measures time relative to the Sun, sidereal time accounts for Earth's orbital position, making it essential for precise astronomical and space operations.

## Historical Development

### Key Milestones
- **Ancient Times:** Babylonian and Greek astronomers use stellar positions for timekeeping
- **1670s:** Development of mechanical clocks enables precise sidereal time measurement
- **1884:** International Meridian Conference standardizes time zones; sidereal time remains separate
- **1925:** International Astronomical Union (IAU) formalizes sidereal time definitions
- **1960s–1970s:** Satellite tracking requires precise LST calculations
- **1984:** IAU Terrestrial Reference System (ITRS) standardizes LST internationally
- **Modern Era:** GPS and atomic clocks enable nanosecond-precision LST

### Foundational Contributors
1. **Ptolemy (100–170 AD):** Observations related to celestial reference frame
2. **Pierre Simon Laplace (1749–1827):** Theoretical framework for sidereal timekeeping
3. **Simon Newcomb (1835–1909):** Refined precession and sidereal time constants
4. **IAU Commission:** Standardized modern definitions (1976+)

## Mathematical Formulation

### Definition and Calculation

**Relationship to UTC:**
$$
\text{GST} = 18^h 41^m 50^s.54841 + 1.00273790935 \times (\text{UT1} - 12^h \text{ Jan 1, 2000})
$$

Where:
- GST: Greenwich Sidereal Time
- UT1: Universal Time 1 (UT corrected for polar motion)
- Constant accounts for precession of equinox

**Local Sidereal Time from Greenwich Sidereal Time:**
$$
\text{LST} = \text{GST} + \frac{\text{East Longitude}}{360°} \times 24^h
$$

Or in terms of hour angle:
$$
\text{LST (hours)} = \text{GST (hours)} + \frac{\lambda}{15°}
$$

Where $\lambda$ is longitude in degrees (positive East, negative West).

### Sidereal Day vs. Solar Day

**Sidereal Day** (rotation relative to stars):
$$
1 \text{ sidereal day} = 23^h 56^m 4^s.0905 = 86,164.0905 \text{ seconds}
$$

**Solar Day** (rotation relative to Sun):
$$
1 \text{ solar day} = 24^h = 86,400 \text{ seconds}
$$

**Relationship:**
$$
1 \text{ solar day} = 1.0027379 \text{ sidereal days}
$$

This ratio accounts for Earth's ~1° orbital advance per day around the Sun.

### Hour Angle Connection

**Hour Angle** of celestial object at location with LST:
$$
h = \text{LST} - \alpha
$$

Where:
- $h$: hour angle (0 to 24 hours, 0 = south)
- $\alpha$: right ascension of object (celestial coordinate)

**Interpretation:** LST directly gives the hour angle of the First Point of Aries.

## Fundamental Principles

### Diurnal Motion

Earth's rotation from West to East causes apparent celestial sphere rotation from East to West:

$$
\text{Angular rate} = \frac{2\pi}{1 \text{ sidereal day}} = 7.2921 \times 10^{-5} \text{ rad/s}
$$

Sidereal time quantifies this rotation.

### Celestial Coordinate System Connection

**Equatorial Coordinates** fixed to celestial sphere (independent of observer location):
- Right Ascension ($\alpha$): measured from Vernal Equinox
- [[Declination]] ($\delta$): measured from celestial equator

**Horizontal Coordinates** fixed to observer location:
- Altitude ($h$): angle above horizon
- Azimuth ($A$): angle from North, East direction

**Connection via LST:**
$$
\sin(h) = \sin(\delta)\sin(\phi) + \cos(\delta)\cos(\phi)\cos(\text{LST} - \alpha)
$$

Where $\phi$ is observer's latitude.

## Theoretical Framework

### Precession Effects

Earth's rotational axis precesses with period ~26,000 years (precession of equinox).

**Mean Sidereal Time (MST):** Removes short-period variations

**Apparent Sidereal Time (AST):** Includes nutation effects

**Equation of Equinoxes:**
$$
\text{AST} = \text{MST} + \Delta\psi \cos(\epsilon)
$$

Where:
- $\Delta\psi$: nutation in longitude
- $\epsilon$: obliquity of ecliptic (~23.44°)

### Relation to Other Time Standards

**Greenwich Mean Sidereal Time (GMST):**
Standard reference at Prime Meridian; basis for all LST calculations

**Greenwich Apparent Sidereal Time (GAST):**
Includes nutation corrections for high-precision work

**UT1:** Universal Time corrected for polar motion (best measure of Earth's rotation)

## Practical Applications

### Satellite Tracking and Ground Stations

**Antenna Pointing:**
Ground station at known latitude must point to satellite at specific LST:

$$
\text{Required LST} = \frac{\lambda_{\text{satellite}} - \lambda_{\text{station}}}{15°} + \alpha_{\text{reference}}
$$

**Tracking Pass Prediction:**
- Satellite position defined in Earth-centered inertial (ECI) coordinates
- Must convert to Earth-centered fixed (ECF) coordinates using LST
- Requires accurate LST calculation at observation epoch

### Telescope Operations

**Celestial Object Observation:**

To observe object with RA = $\alpha$, declination = $\delta$:

1. Calculate hour angle: $h = \text{LST} - \alpha$
2. Calculate altitude: $\sin(alt) = \sin(\delta)\sin(\phi) + \cos(\delta)\cos(\phi)\cos(h)$
3. Calculate azimuth from altitude and hour angle
4. Point telescope to computed altitude and azimuth

**Sidereal Rate Tracking:**
Telescope motor advances at sidereal rate (~0.25°/min) to follow star across sky.

### Navigation and Timing

**GPS and GNSS:**
Satellite navigation depends on accurate LST for coordinate transformations

**Atomic Clock Synchronization:**
Keeps UTC; LST derived from UTC via Greenwich sidereal time

### Astronomical Observations

**Proper Motion Measurements:**
Comparison of stellar positions over time requires LST conversion to fixed celestial frame

**Parallax Measurements:**
Baseline observations at different times use LST to convert to celestial coordinates

## Relationship to Other Concepts

1. **Connection to [[Coordinate System]]:**
   - Bridge between Earth-fixed and celestial coordinates
   - Essential for all coordinate transformations

2. **Connection to [[Right Ascension]] and [[Celestial Equator]]:**
   - LST directly measures hour angle of Vernal Equinox
   - RA measured from Vernal Equinox; LST provides reference

3. **Connection to [[Coordinated Universal Time (UTC)]]:**
   - LST derived from UTC
   - Ratio sidereal/solar day accounts for orbital geometry

4. **Connection to [[Orbital Mechanics]]:**
   - Essential for ground station visibility calculations
   - Satellite orbital elements referenced to celestial frame via LST

5. **Connection to [[Precession]]:**
   - Vernal Equinox precesses; LST definition updated periodically
   - Nutation introduces short-period variations

## Computational Methods

### Calculating LST

**Step-by-Step Algorithm:**

1. **Get UTC time** for observation epoch
2. **Convert to UT1:** Apply ΔUT1 correction (polar motion)
3. **Calculate Julian Date (JD)** from UT1
4. **Calculate Greenwich Mean Sidereal Time (GMST):**
   $$\text{GMST} = 18.6973746 + 24.065708496 \times (JD - 2451545.0)$$
5. **Apply nutation correction** (optional, for high precision)
6. **Calculate Local Sidereal Time:**
   $$\text{LST} = \text{GMST} + \lambda_{\text{degrees}} / 15$$

### Example Calculation

**Problem:** Observer at longitude 75°W, UTC = 12:00:00, Jan 1, 2000

**Solution:**

1. UT1 ≈ UTC (negligible correction for this epoch)
2. JD(2000 Jan 1, 12:00 UT) = 2451545.0
3. GMST = 18.6973746 + 24.065708496 × 0 = 18.697 hours
4. LST correction: -75°/15 = -5 hours (West longitude is negative)
5. LST = 18.697 - 5 = 13.697 hours ≈ 13h 41m 49s

### Precision Considerations

**High-Precision Requirements:**
- Satellite tracking: microsecond precision (< 100 ns LST error)
- VLBI astronomy: picosecond precision
- Requires UT1 with precision better than 0.1 ms
- Must account for nutation and polar motion

## Practical Tables and References

### Sidereal Time Conversion Rates

| Time Interval | Sidereal Advance |
|---|---|
| 1 solar day | 3m 55.909s |
| 1 solar hour | 9.83s |
| 1 solar minute | 0.1637s |
| 1 solar second | 0.00273s |

### Common LST Values

| Greenwich Longitude | LST = GST | Time Zone |
|---|---|---|
| 0° (Greenwich) | = GST | UTC±0 |
| 15°E | = GST + 1h | UTC+1 |
| 75°W | = GST - 5h | UTC-5 |
| 120°E | = GST + 8h | UTC+8 |

## See Also

- [[Coordinate System]]
- [[Right Ascension]]
- [[Declination]]
- [[Celestial Equator]]
- [[Coordinated Universal Time (UTC)]]
- [[First Point of Aries]]
- [[Precession]]
- [[Sidereal Time]]
- [[Hour Angle]]
- [[Orbital Mechanics]]

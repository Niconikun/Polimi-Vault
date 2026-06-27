---
title: Local Apparent Time
tags:
  - astronomy
  - timekeeping
  - solar time
  - coordinate systems
---

# Local Apparent Time

## Formal Definition

**Local Apparent Time (LAT)**, also known as **solar time** or **true solar time**, is a time measurement based on the actual (apparent) motion of the Sun across the sky as seen from a specific geographic location. Unlike [[Coordinated Universal Time (UTC)]], which measures time relative to an arbitrary reference, LAT is directly tied to the Sun's position, making it fundamental to [[Daylight]] hours, solar noon calculations, and historically, all timekeeping before mechanical clocks. LAT differs from mean solar time (clock time) due to the equation of time, accounting for Earth's elliptical orbit and axial tilt.

## Historical Development

### Key Milestones
- **Ancient Times:** Sun's position as primary timekeeping reference (sundials, obelisks)
- **1100s–1300s:** Mechanical clocks introduce mean solar time concept
- **1667:** John Flamsteed standardizes apparent time observation
- **1750s:** Equation of time mathematically formulated
- **1820:** Thomas Young tabulates equation of time
- **1884:** International Meridian Conference establishes standard zones
- **1905:** Einstein's relativity theory reframes time concepts
- **Modern Era:** GPS, satellite technology enable precise solar position calculations

### Foundational Contributors
1. **Hipparchus (190–120 BC):** Solar motion analysis; precursor concepts
2. **Nicolaus Copernicus (1473–1543):** Heliocentric model; solar reference frame
3. **Johannes Kepler (1571–1630):** Elliptical orbits; Earth's orbital speed variation
4. **John Flamsteed (1646–1719):** Rigorous solar observations and timekeeping
5. **Urbain Le Verrier (1811–1877):** Perturbation analysis of solar motion

## Mathematical Formulation

### Solar Hour Angle and Noon

**Hour angle of Sun at local location:**
$$
h_{\text{sun}} = \text{LST} - \alpha_{\text{sun}}
$$

Where [[Local Sidereal Time]] LST is known and $\alpha_{\text{sun}}$ is Sun's right ascension.

**Local apparent time** (hours from solar noon):
$$
\text{LAT} = 12^h + h_{\text{sun}} / 15°
$$

(Divide by 15°/hour to convert angular hours to clock hours)

**Solar noon:** When $h_{\text{sun}} = 0$ (Sun on local meridian)
$$
\text{LAT}_{\text{noon}} = 12^h 00^m 00^s
$$

### Mean Solar Time and Equation of Time

**Mean solar time (MST):** Time that would be measured by a hypothetical uniform solar motion

**Equation of time:**
$$
\text{EOT} = \text{LAT} - \text{MST}
$$

Accounts for:
1. **Orbital eccentricity:** Earth closer to Sun in January (perihelion); farther in July (aphelion)
2. **Obliquity of ecliptic:** Earth's axial tilt (~23.44°) relative to orbital plane

### Mathematical Expression of Equation of Time

Approximate formula (accurate to ~30 seconds):
$$
\text{EOT} (\text{minutes}) = 9.87\sin(2B) - 7.53\cos(B) - 1.5\sin(B)
$$

Where:
$$
B = \frac{360°(d - 1)}{365}
$$

With $d$ = day of year (1–365).

**Maximum values:**
- Maximum advance: $\approx +14$ minutes (early November)
- Maximum retard: $\approx -16$ minutes (mid-February)

### Variation with Latitude and Longitude

**Local apparent time independent of latitude** (depending only on Sun's declination, right ascension)

**Longitude effect on [[Coordinated Universal Time (UTC)|UTC]]:**
$$
\text{UTC} = \text{LAT}_{\text{reference}} - \frac{\lambda}{360°} \times 24^h
$$

Where $\lambda$ is longitude in degrees (East positive).

## Fundamental Principles

### Sun's Apparent Motion

**Earth's orbit:** Elliptical with eccentricity $e \approx 0.0167$

**Kepler's second law (equal areas):**
$$
r^2 \frac{d\theta}{dt} = \text{constant}
$$

Orbital speed varies:
- Perihelion (Jan 3): ~30.29 km/s
- Aphelion (Jul 4): ~29.29 km/s

**Result:** Sun's angular speed in ecliptic varies → apparent solar time varies.

### Axial Tilt (Obliquity)

**Angle between rotation axis and orbital normal:**
$$
\epsilon \approx 23°26'
$$

**Consequence:** Sun's declination varies seasonally
$$
\delta_{\text{sun}} = \epsilon \sin(\text{Longitude in ecliptic})
$$

**Effect on solar noon timing:** Sun's equation of time component from obliquity.

### Perihelion and Aphelion

**Perihelion (closest to Sun, January 3):**
- Distance: ~147.1 million km (1.0 AU)
- Angular speed: Maximum
- Solar noon occurs earlier than mean time

**Aphelion (farthest from Sun, July 4):**
- Distance: ~152.1 million km (1.0 AU)
- Angular speed: Minimum
- Solar noon occurs later than mean time

## Connection to Other Concepts

1. **Connection to [[Local Sidereal Time]]:**
   - LST gives Vernal Equinox hour angle (fixed celestial frame)
   - LAT gives Sun's hour angle (time-varying solar position)
   - Relationship: LAT = LST - RA(Sun) / 15°

2. **Connection to [[Daylight]] and Seasons:**
   - Duration varies throughout year due to obliquity and eccentricity
   - Sunrise/sunset times determined by Sun's declination and latitude

3. **Connection to [[Coordinated Universal Time (UTC)]]:**
   - UTC standard time; LAT natural solar time
   - Difference via equation of time and longitude

4. **Connection to [[Astronomy]] and Astrophysics:**
   - Solar phenomena observations (eclipses, transits) timed in apparent time
   - Apparent positions of celestial objects

5. **Connection to [[Spherical Coordinate System|Spherical Coordinates]]:**
   - Sun's position in equatorial coordinates (RA, declination)
   - Conversion to horizontal coordinates requires LAT

## Relationship to Daylight Saving Time

### Civil Time Systems

**Standard Time:** Mean solar time, offset by timezone

**Daylight Saving Time:** Advanced 1 hour (~April–October in Northern Hemisphere)

**Purpose:** Align working hours with daylight; energy savings motivation (debated effectiveness)

**Historical context:** Linked to apparent solar time originally; now administrative.

## Practical Applications

### Solar Noon Calculation

**Step-by-step for location (latitude $\phi$, longitude $\lambda$):**

1. **Find day of year:** $d = 1$ (Jan 1) to $365$ (Dec 31)
2. **Calculate equation of time:** EOT from above formula
3. **Calculate solar noon UTC:**
   $$\text{Solar noon UTC} = 12^h 00^m + \text{EOT} - \lambda/15°$$
4. **Convert to local time:** Add timezone offset

**Example:** New York (73.97°W), December 21

EOT ≈ -1.9 minutes; Solar noon ≈ 11:47 EST (UTC-5)

### Sunrise and Sunset Predictions

**Depends on:**
- Day of year (Sun's declination)
- Observer latitude (horizon geometry)
- Local apparent time (sun's diurnal motion)

**Algorithm:** Standard astronomical calculation; multiple approximations exist

### Solar Energy Applications

**Photovoltaic (PV) systems:** Track sun throughout day

**Optimal orientation:**
- Azimuth: South (Northern Hemisphere), North (Southern Hemisphere)
- Elevation: Local latitude (approximately)

**Time of maximum power generation:** Near solar noon

**Variation:** Clouds, atmospheric conditions; also depends on equation of time offset.

### Analemma (Figure-Eight Diagram)

**Plotting the Sun's position** (same local solar time, different dates):

$$
\text{x-coord} = \text{EOT} \times \text{scale factor}
$$
$$
\text{y-coord} = \text{Sun's declination}
$$

**Characteristic shape:** Figure-eight (analemma) results from combined orbital eccentricity and obliquity effects.

**Historical use:** Sundial design; modern: artistic representation of solar motion.

## Variation Throughout the Year

### Seasonal Equation of Time Patterns

| Season | EOT Range | Physical Cause |
|---|---|---|
| January | -14 to +2 min | Perihelion (fast motion) |
| April | -2 to +1 min | Obliquity effect peaks |
| July | -6 to 0 min | Aphelion (slow motion) |
| October | +14 to +8 min | Obliquity + eccentricity aligned |

### Length of Day Variation

**Sidereal day (star to star):** Constant ~23h 56m 4s

**Solar day (noon to noon):** Varies 23h 59m 39s to 24h 0m 30s

**Average:** 24h 00m 00s (by definition of mean solar time)

## Historical Timekeeping Systems

### Before Mechanical Clocks

- **Sundials:** Direct LAT measurement
- **Water clocks:** Attempted mean solar time approximation
- **Astronomical observations:** Precise LAT from stellar positions

### After Mechanical Clocks

- **Mean solar time adoption:** Standard timekeeping (independent of Sun's actual position)
- **International time zones (1884):** Longitude-based standard
- **UTC epoch (1972):** Atomic time basis (Cesium oscillators)

### Modern Context

LAT rarely used for civil purposes; retained for:
- Solar energy calculations
- Astronomical observations (epoch definitions)
- Historical/recreational purposes (sundials)

## See Also

- [[Local Sidereal Time]]
- [[Coordinated Universal Time (UTC)]]
- [[Daylight]]
- [[Declination]]
- [[Right Ascension]]
- [[Astronomy]]
- [[Solar Radiation]]
- [[Equation of Time]]
- [[Analemma]]
- [[Sundial]]

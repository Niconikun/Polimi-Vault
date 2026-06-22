#Orbital-Mechanics
### **Two-Line Element (TLE)**
A **Two-Line Element (TLE)** is a standardized data format used to describe the **orbital parameters** of an Earth-orbiting object (e.g., satellites, space debris) at a specific [[Epoch]]. TLEs are widely employed in **satellite tracking**, **orbit propagation**, and **space situational awareness** (SSA). The format was developed by **Norad (North American Aerospace Defense Command)** and is maintained as part of the **Space-Track.org** catalog.

---

#### **Structure of a TLE**
A TLE consists of **two lines of 69 characters each**, preceded by a **title line** (optional but common). The fields are fixed-width and encode orbital elements in a compact form.

1. **Line 0 (Optional Title Line)**:
   - Human-readable name of the object (e.g., `ISS (ZARYA)`).
   - Example: `HUBBLE SPACE TELESCOPE`

2. **Line 1**:
   - **Columns 1–2**: Line number (always `1`).
   - **Columns 3–7**: Satellite catalog number (e.g., `25544` for the ISS).
   - **Columns 8**: Classification (`U` for unclassified, `C` for classified, `S` for secret).
   - **Columns 10–17**: International designator (e.g., `98067A` for the ISS, where `98` = launch year, `067` = launch number, `A` = piece of the launch).
   - **Columns 19–20**: [[Epoch]] year (last 2 digits, e.g., `23` for 2023).
   - **Columns 21–32**: [[Epoch]] day and fractional day (e.g., `365.12345678`).
   - **Columns 34–43**: First time derivative of [[mean motion]] (ballistic coefficient, `B*`, in units of 1/earth radii).
   - **Columns 45–52**: Second time derivative of [[mean motion]] (rarely used, often `0`).
   - **Columns 54–61**: BSTAR drag term (decay rate, in units of 1/earth radii).
   - **Columns 63**: [[Ephemeris]] type (`0` for SGP/SDP4, `2` for SGP4/SDP8, etc.).
   - **Columns 65–68**: Element set number (incremented for updates).

3. **Line 2**:
   - **Columns 1–2**: Line number (always `2`).
   - **Columns 3–7**: Satellite catalog number (repeated from Line 1).
   - **Columns 9–16**: **[[Inclination]]** ($i$) in degrees (e.g., `51.64` for the ISS).
   - **Columns 18–25**: **[[Right Ascension of the Ascending Node]]** ($\Omega$) in degrees.
   - **Columns 27–33**: **[[Eccentricity]]** ($e$, no decimal point, e.g., `0006800` = $0.0006800$).
   - **Columns 35–42**: **Argument of perigee** ($\omega$) in degrees.
   - **Columns 44–51**: **[[Mean Anomaly]]** ($M$) in degrees.
   - **Columns 53–63**: **[[Mean motion]]** ($n$) in revolutions per day (e.g., `15.49` for the ISS).
   - **Columns 64–68**: **Revolution number at [[Epoch]]** (orbit count since launch).

---

#### **Orbital Elements Encoded in a TLE**
A TLE represents a **simplified Keplerian orbit** with perturbative terms for [[atmospheric drag]] and gravitational anomalies. The core elements are:
1. **[[Inclination]] ($i$)**: Angle between the [[orbital plane]] and the [[equatorial plane]].
2. **[[Right Ascension of the Ascending Node]] ($\Omega$)**: [[Geographic Longitude]] where the orbit crosses the equator northbound.
3. **[[Eccentricity]] ($e$)**: Shape of the orbit (0 = circular, 0 < $e$ < 1 = elliptical).
4. **[[Argument of Periapsis]] ($\omega$)**: Angle from the ascending node to perigee.
5. **[[Mean Anomaly]] ($M$)**: Fraction of the orbit elapsed since perigee.
6. **[[Mean Motion]] ($n$)**: Average [[Angular Velocity]] (revolutions per day).

---

#### **Perturbations and Propagation**
TLEs use the **Simplified General Perturbations (SGP4/SDP4)** models to account for:
- **[[Atmospheric Drag]]** (via the `B*` term).
- **Earth’s oblateness** ([[J₂ gravitational harmonic]]).
- **Luni-solar gravity** (for high-altitude orbits).
- **[[Solar Radiation Pressure]]** (for large, reflective objects).

The **[[Epoch]]** marks the time at which the [[Keplerian Parameters]] are valid. Propagation to other times requires numerical integration of the SGP4 model.

---

#### **Example TLE (International Space Station)**
```
ISS (ZARYA)
1 25544U 98067A   23365.12345678  .00020000  00000-0  40000-3 0  9991
2 25544  51.6400 123.4500 0006800 123.4500 236.5500 15.49000000345678
```

---

#### **Limitations of TLEs**
1. **Accuracy**: Degrades over time (especially for low-Earth orbits due to drag).
   - Typical validity: **a few days to weeks** (high-altitude orbits last longer).
2. **Simplifications**: SGP4 is an approximation; high-fidelity models (e.g., **High-Precision Orbit Propagator**) are used for critical operations.
3. **No [[Covariance]]**: TLEs do not include uncertainty estimates.

---

#### **Applications**
- **Satellite tracking** (e.g., [[SatNOGS]], [[Celestrak]]).
- **Collision avoidance** (conjunction analysis).
- **Amateur radio** (predicting satellite passes).
- **Space debris monitoring**.

---

#### **Suggested Additions for Your Note**
1. **Links**:
   - [[SGP4]] (propagation model)
   - [[Space-Track.org]] (TLE data source)
2. **Tools**:
   - [Celestrak](https://celestrak.org/) (TLE repository).
   - [PyEphem](https://rhodesmill.org/pyephem/) (Python library for TLE propagation).
3. **Tags**: `#orbital-mechanics`, `#satellite-tracking`, `#space-debris`.
4. **Diagram**: Visualization of TLE fields (e.g., [[inclination]], RAAN).

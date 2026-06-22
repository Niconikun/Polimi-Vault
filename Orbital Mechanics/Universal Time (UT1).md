#TBD #Orbital-Mechanics #time-standard

### **Definition of Universal Time (UT1)**
**Universal Time (UT1)** is the **primary astronomical timescale** based on **Earth’s rotation**, serving as the modern successor to **[[Greenwich Mean Time (GMT)]]**. It is defined as the **[[mean solar time]] at 0° [[Geographic Longitude]] ([[Greenwich Meridian]])**, corrected for **polar motion** and **irregularities in Earth’s rotation**. UT1 is the **non-uniform** but **observationally precise** standard used for:
- **Celestial navigation** (e.g., star/planet positions in almanacs).
- **Spacecraft tracking** (e.g., [[ground station]] synchronization).
- **Geodetic surveys** (e.g., VLBI and GPS corrections).

---

#### **1. Formal Characteristics**
- **Basis**:
  UT1 is derived from **Earth’s rotation angle (ERA)** relative to the **[[International Celestial Reference Frame (ICRF)]]**, measured via:
  - **Very Long Baseline Interferometry (VLBI)**: Tracks extragalactic quasars to determine Earth’s orientation with **~10 microarcsecond precision**.
  - **GPS and SLR (Satellite Laser Ranging)**: Complementary data sources for short-term variations.

- **Non-Uniformity**:
  UT1 varies due to:
  - **Tidal friction** (lunar/solar gravitational drag, slowing Earth by **~2.3 ms/day**).
  - **Core-mantle coupling** (geophysical processes causing **sub-millisecond fluctuations**).
  - **Polar motion** (Chandler wobble, contributing **±0.3s** variations).

- **Relationship to Other Timescales**:
  $
  \text{UT1} = \text{UTC} + \text{DUT1}
  $
  where **DUT1** (published by IERS) is the dynamic offset (typically **|DUT1| < 0.9s**).

---

#### **2. Key Applications**
| **Domain**               | **Use Case**                                                                 | **Example**                                  |
|--------------------------|------------------------------------------------------------------------------|---------------------------------------------|
| **Astronomy**            | Apparent positions of stars/planets (e.g., [[right ascension]]/[[Declination]]).   | *The Astronomical Almanac* uses UT1.        |
| **Navigation**           | Synchronization of maritime/aviation clocks (e.g., "Zulu time" adjustments). | GPS systems apply DUT1 corrections.         |
| **Geodesy**              | Earth orientation parameters (EOP) for surveying.                          | VLBI stations measure UT1 in real-time.    |
| **Space Operations**     | [[Ground station]] timing for satellite passes.                                 | NASA’s Deep Space Network uses UT1.         |

---

#### **3. Calculation and Corrections**
UT1 is computed by the **International Earth Rotation and Reference Systems Service (IERS)** using:
1. **Earth Rotation Angle (ERA)**:
   $
   \text{ERA} = 2\pi \times (0.7790572732640 + 1.00273781191135448 \times J)
   $
   where $J$ is the Julian century since [[J2000]].0.

2. **Polar Motion Adjustment**:
   - Corrections for **x-pole** and **y-pole** displacements (published in IERS Bulletin A).

3. **Leap Seconds**:
   - UT1 is kept within **±0.9s of UTC** by introducing leap seconds (e.g., last added on **2016-12-31 23:59:60 UTC**).

---
#### **4. UT1 vs. Related Timescales**
| **Timescale** | **Basis**               | **Offset from UT1**               | **Key Difference**                          |
|---------------|-------------------------|------------------------------------|---------------------------------------------|
| **UTC**       | Atomic clocks + leap sec. | UT1 − UTC = DUT1 (≤ 0.9s)         | UTC is uniform; UT1 follows Earth’s rotation. |
| **TAI**       | Atomic clocks           | UT1 ≈ TAI − 36.184s (varies with ΔT) | TAI ignores Earth’s rotation.              |
| **TT**        | Theoretical (SI second) | UT1 ≈ TT − ΔT (ΔT ≈ 69s in 2025)   | TT is uniform for orbital mechanics.        |
| **GMST**      | Greenwich Mean Sidereal Time | GMST = 6h41m50.54841s + 1.00273790935×UT1 | Sidereal vs. solar time.                   |

- **ΔT (Delta T)**: The cumulative difference **TT − UT1**, growing due to tidal deceleration (~69s in 2025; projected to reach ~86400s in ~5000 CE).

---

#### **5. Practical Example: UT1 Calculation**
To find **UT1 for 2025-01-01 00:00:00 UTC**:
1. Check **IERS Bulletin A** for DUT1 (e.g., **DUT1 = +0.1s**).
2. Apply correction:
   $$
   \text{UT1} = \text{UTC} + \text{DUT1} = 00:00:00 + 0.1s = 00:00:00.1
   $$
3. For **astronomical use**, convert to **Greenwich Apparent Sidereal Time (GAST)**:
   $$
   \text{GAST} = \text{GMST} + \text{Equation of Equinoxes}
   $$

---

#### **6. Data Sources and Tools**
- **Real-Time UT1**:
  - [IERS Earth Orientation Data](https://www.iers.org/IERS/EN/DataProducts/EarthOrientationData/eop.html)
  - **USNO’s "Earth Orientation Parameters"** (updated daily).
- **Software**:
  - **SOFA Library** (`iauUt1utc` function).
  - **Astropy** (`astropy.time` with `scale='ut1'`).

---
### **Suggested Additions for Your Note**
1. **Diagram**: Earth’s rotation irregularities (tidal friction, polar motion).
   ```mermaid
   graph LR
     A[Earth Rotation] -->|Tidal Friction| B[UT1 Slows ~2.3 ms/day]
     A -->|Polar Motion| C[±0.3s Variations]
   ```
2. **Table**: Historical DUT1 values (e.g., 1972–2025).
3. **Tags**: `#time-standard` `#geodesy` `#astronomy` `#IERS`
4. **See Also**: [[Greenwich Mean Time (GMT)]], [[Terrestrial Time (TT)]], [[International Atomic Time (TAI)]]

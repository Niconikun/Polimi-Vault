#time-standard #Orbital-Mechanics

**Greenwich Mean Time (GMT)** is the **[[Mean Solar Time]]** at the **Royal Observatory in Greenwich, London**, historically used as the world's primary [[Time]] standard. Key points:
- Based on Earth's rotation, with **noon GMT** defined as the moment the sun crosses the **[[Greenwich Meridian]]** (0° [[Geographic Longitude]]).
- Replaced by **[[Coordinated Universal Time (UTC)]]** as the global standard in 1972, but remains a widely recognized time reference (e.g., for time zones like GMT+0).
- **Not affected by daylight saving time** (unlike British Summer Time, which is GMT+1).

**Scientific Context**:
GMT was derived from astronomical observations but later refined to account for irregularities in Earth's rotation (via **UT1**, a moderHere’s a new section for your note [[Greenwich Mean Time (GMT)]] on **how GMT is calculated**, blending historical methods with modern refinements:

---

### **1. Historical Development of GMT**
- **Origins (17th–19th Century)**:
  - Established in **1675** when the Royal Observatory, Greenwich, was founded to solve the **[[Geographic Longitude]] problem** for navigation.
  - **John Flamsteed** and later **Nevil Maskelyne** (Astronomer Royal) standardized timekeeping using the **transit circle** telescope to track stars crossing the [[Greenwich Meridian]].
  - By the **1840s**, British railways adopted GMT to synchronize schedules, replacing local solar times (e.g., "Bristol Time" or "Liverpool Time").

- **Global Adoption (Late 19th Century)**:
  - The **1884 International Meridian Conference** in Washington, D.C., designated the [[Greenwich Meridian]] as the **Prime Meridian (0° [[Geographic Longitude]])** and GMT as the world’s time standard.
  - This resolved conflicts between national time systems (e.g., France used Paris Mean Time until 1911).

- **Decline and Legacy**:
  - **1925**: GMT was redefined to start at **midnight** (previously noon) to align with civil timekeeping.
  - **1972**: Replaced by **UTC** (Coordinated Universal Time) due to inconsistencies caused by Earth’s irregular rotation. UTC uses **atomic clocks** but remains within **±0.9 seconds of GMT** (via leap seconds).

---

### **2. Scientific and Technical Context**
#### **Astronomical Basis**
- **[[Mean Solar Time]] vs. Apparent Solar Time**:
  - GMT is based on the **fictitious "mean sun"**, which moves uniformly along the celestial equator (unlike the true sun, whose apparent motion varies due to Earth’s [[elliptical orbit]] and axial tilt).
  - **[[Equation of Time]]**: The difference between apparent solar time and [[mean solar time]] (GMT), ranging from **-14 to +16 minutes** annually.

#### **Modern Time Standards**
- **UTC vs. GMT**:
  - **UTC** is now the primary standard, derived from **International Atomic Time (TAI)** but adjusted with leap seconds to approximate GMT (UT1).
  - **UT1**: A modern version of GMT, corrected for **polar motion** and Earth’s rotational slowing (caused by tidal friction).
  - **Example**: When UTC is **23:59:60** (leap second), it synchronizes with UT1/GMT.

#### **Practical Applications**
- **Time Zones**: GMT is the basis for time zones (e.g., GMT+1 for Central European Time).
- **Navigation**: Still used in **aviation and maritime** contexts (e.g., "Zulu time" = GMT/UTC).
- **Legal/Historical Records**: Documents often use GMT to avoid ambiguity (e.g., "00:00 GMT, January 1, 2025").

---

### **3. Key Misconceptions**
- **"GMT is the same as UTC"**: Incorrect—UTC is atomic-time-based, while GMT is Earth-rotation-based. They differ by up to **0.9 seconds**.
- **"GMT observes daylight saving"**: No—daylight saving (e.g., BST = GMT+1) is a separate convention.

---
### **Suggested Additions for Your Note**

1. **Table**: Comparison of GMT, UTC, and UT1.
   | Standard | Basis               | Accuracy          | Adjustments               |
   |----------|---------------------|-------------------|----------------------------|
   | GMT       | Earth’s rotation    | ~±0.9s (via UT1)  | None (historical)         |
   | UTC       | Atomic clocks (TAI) | <1 nanosecond     | Leap seconds               |
   | UT1       | Earth’s rotation    | ~±0.9s from GMT   | Polar motion corrections   |

2. **Tags**: 

Would you like me to draft a section on **how GMT is calculated** or its **cultural impact** (e.g., the "Greenwich Time Ball")?n variant).


![[Pasted image 20251113205906.png]]
### **4. Calculation of Greenwich Mean Time**
GMT is derived from **Earth’s rotation** but requires corrections to account for irregularities. Its calculation has evolved from purely astronomical observations to hybrid systems integrating atomic precision.

---

#### **A. Historical Astronomical Method**
1. **Transit Telescope Observations**:
   - At the Royal Observatory, astronomers used a **transit circle** to record the exact moment a star (e.g., **Polaris** or **clock stars**) crossed the [[Greenwich Meridian]].
   - **[[Mean Solar Time]]** was calculated by averaging these transits over a year to smooth out variations caused by:
     - Earth’s **[[elliptical orbit]]** (faster in January, slower in July).
     - **Axial tilt** (23.5°), causing the sun’s apparent speed to vary (e.g., slower in winter).

2. **[[Equation of Time]]**:
   - The difference between **apparent solar time** (sundial time) and **[[mean solar time]]** (GMT) is described by:
     $$
     \text{Equation of Time} = \text{Apparent Time} - \text{Mean Time}
     $$
   - This correction (ranging from **-14.3 to +16.4 minutes**) was tabulated annually in nautical almanacs.

3. **Time Balls and Signals**:
   - The **Greenwich Time Ball** (installed 1833) dropped daily at **12:59:55 GMT** to synchronize chronometers.
   - Later, **telegraph signals** (from 1852) and **radio broadcasts** (from 1924) disseminated GMT globally.

---

#### **B. Modern Calculation (UT1)**
Today, GMT is effectively represented by **UT1**, which refines raw astronomical data:
1. **Earth Rotation Angle (ERA)**:
   - Measured via **Very Long Baseline Interferometry (VLBI)**, which tracks quasars to determine Earth’s orientation with **milliarcsecond precision**.
   - The **[[International Earth Rotation and Reference Systems Service (IERS)]]** computes UT1 by:
     $
     \text{UT1} = \text{ERA} / (15^\circ \text{ per hour}) + \text{corrections}
     $
     (where $15^\circ$ = 1 hour of rotation).

2. **Corrections Applied**:
   - **Polar Motion**: Adjusts for the wobble of Earth’s axis (up to **0.3 seconds**).
   - **Tidal Friction**: Accounts for the **2.3 milliseconds/day slowing** of Earth’s rotation (due to lunar gravity).
   - **Leap Seconds**: UT1 is kept within **±0.9 seconds of UTC** by adding/subtracting leap seconds (e.g., last added on **December 31, 2016**).

3. **Relationship to UTC**:
   - UTC is broadcast by atomic clocks (e.g., **NIST-F2**), while UT1 is derived from VLBI.
   - The difference **UTC − UT1** (called **DUT1**) is published by IERS and used for navigation (e.g., GPS systems).

---

#### **C. Practical Example: Calculating GMT for a Given Date**
To find GMT (UT1) for **January 1, 2025, 12:00:00 UTC**:
1. Check the latest **IERS Bulletin** for DUT1 (e.g., **DUT1 = +0.1s**).
2. Adjust UTC:
   $$
   \text{UT1} = \text{UTC} + \text{DUT1} = 12:00:00 + 0.1s = 12:00:00.1 \text{ GMT}
   $$
3. For **astronomical applications**, apply the **[[Equation of Time]]** (e.g., **+3.5 minutes** in early January) to convert to apparent solar time.

---

#### **D. Tools and Data Sources**
- **Historical GMT**:
  - [[Nautical Almanac]] (18th–20th century tables).
  - **Air Almanac** (used in aviation until the 1990s).
- **Modern UT1**:
  - [IERS UT1 Data](https://www.iers.org/IERS/EN/DataProducts/EarthOrientationData/eop.html)
  - **USNO Time Service**: Provides real-time UT1-UTC offsets.

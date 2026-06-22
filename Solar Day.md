#time-standard #Orbital-Mechanics 
### **Solar Day**
A **solar day** is the time interval between two successive **solar noons**, where **solar noon** is the moment when the Sun appears at its highest point in the sky (i.e., when it transits the local meridian).

#### **Key Characteristics:**
1. **Duration**:
   - The **mean solar day** is standardized to **24 hours** (86,400 seconds) and serves as the basis for civil timekeeping.
   - The **apparent solar day** (true solar day) varies slightly due to:
     - Earth’s **[[elliptical orbit]]** ([[Kepler’s second law]]: faster near perihelion, slower near aphelion).
     - Earth’s **axial tilt** (23.44°), causing the Sun’s apparent motion along the ecliptic to project unevenly onto the [[celestial equator]].

2. **[[Equation of Time]]**:
   The difference between the **apparent solar time** and **[[mean solar time]]** is described by the **[[Equation of Time]]** ($E$):
   $
   E = \text{apparent solar time} - \text{mean solar time}
   $
   - $E$ ranges from **-14.2 minutes** (around February 11) to **+16.3 minutes** (around November 3).
   - This variation is why sundials (which track apparent solar time) may disagree with clocks (which track [[mean solar time]]).

3. **Relation to [[Sidereal Day]]**:
   - A **[[Sidereal Day]]** (Earth’s rotation relative to distant stars) is **~23 hours 56 minutes 4 seconds** (shorter than a solar day).
   - The solar day is longer because Earth must rotate an **additional ~1°** (360°/365.25 days) to realign with the Sun due to its orbital motion.

4. **Types of Solar Days**:
   - **Mean Solar Day**: Averaged over a year to smooth out variations (basis for UTC).
   - **Apparent Solar Day**: Actual observed interval between solar noons, varying by up to ~30 seconds daily.

#### **Mathematical Formulation**:
The length of an apparent solar day ($T_{\text{apparent}}$) can be approximated as:
$
T_{\text{apparent}} \approx T_{\text{mean}} \left(1 - \frac{2e \cos L}{1 - e^2}\right) + \text{obliquity effects},
$
where:
- $T_{\text{mean}} = 86,400$ s (mean solar day),
- $e \approx 0.0167$ (Earth’s orbital [[Eccentricity]]),
- $L$ = [[Geographic Longitude]] of the Sun (varies with time of year).

#### **Practical Implications**:
- **Timekeeping**: Civil clocks use **[[mean solar time]]** for consistency, while astronomers may use **apparent solar time** for observations.
- **Sundials**: Show **apparent solar time**; corrections (via the [[Equation of Time]]) are needed to match clock time.

---

### **Suggested Additions for Your Note**:
1. **Diagram**: Include a sketch showing the difference between mean and apparent solar time (e.g., [[Analemma]]).
2. **Links**:
   - [[Equation of Time]] (for deeper math)
   - [[Sidereal Day]] (contrast with solar day)
#Orbital-Mechanics #DONE
### **Latitude**
**Latitude** is a geographic coordinate that specifies the **north-south position** of a point on the [[surface]] of a planet or celestial body (e.g., Earth) relative to its **[[Equatorial Plane]]**. It is measured as the **angle** between the [[equatorial plane]] and a line drawn from the center of the planet to the point of interest, ranging from **0° at the equator** to **+90° at the North Pole** and **-90° at the South Pole**. Latitude is a fundamental component of the **spherical coordinate system** used in geography, navigation, and orbital mechanics.

---

### **Mathematical Definition**
Latitude ($\phi$) is defined as the angle between:
1. The **[[equatorial plane]]** of the planet (a plane perpendicular to the rotational axis and passing through the center).
2. A **radial line** from the planet's center to the point of interest on its surface.

Mathematically, for a point $P$ on the surface of a sphere (e.g., Earth):
$$
\phi = \arcsin\left(\frac{z}{r}\right),
$$
where:
- $\phi$ is the latitude (in degrees or radians),
- $z$ is the **cartesian coordinate** along the rotational axis (positive northward),
- $r = \sqrt{x^2 + y^2 + z^2}$ is the distance from the center of the planet to the point $P$.

For an **oblate spheroid** (e.g., Earth), latitude is further classified into:
1. **Geocentric Latitude**: Angle between the [[equatorial plane]] and the line from the Earth's center to the point.
2. **Geodetic (Geographic) Latitude**: Angle between the [[equatorial plane]] and the **normal** to the reference ellipsoid at the point. This is the latitude typically used in maps and GPS systems.

---

### **Types of Latitude**
| **Type**               | **Description**                                                                                     | **Use Case**                                  |
|------------------------|-----------------------------------------------------------------------------------------------------|----------------------------------------------|
| **[[Geodetic Latitude]]**  | Angle between the [[equatorial plane]] and the normal to the ellipsoid surface.                        | Standard for maps, GPS, and navigation.      |
| **Geocentric Latitude**| Angle between the [[equatorial plane]] and the line from Earth's center to the point.                  | Astronomical calculations, orbital mechanics.|
| **Astronomic Latitude**| Angle between the [[equatorial plane]] and the local gravity vector (plumb line).                       | Surveying and geodesy.                       |
| **Reduced Latitude**   | Auxiliary latitude used in ellipsoidal calculations to simplify equations.                          | Geodetic computations.                       |

---

### **Key Properties**
1. **Range and Notation**:
   - Latitude ranges from **-90° (South Pole)** to **+90° (North Pole)**.
   - The equator is defined as **0° latitude**.
   - Positive values indicate **northern hemisphere**; negative values indicate **southern hemisphere**.

2. **Relation to [[Geographic Longitude]]**:
   - Latitude and **[[Geographic Longitude]]** together form a **spherical coordinate system** that uniquely defines a point on the Earth's surface.
   - Example: The coordinates (40°N, 75°W) specify a point 40° north of the equator and 75° west of the prime meridian.

3. **Circles of Latitude**:
   - Lines of constant latitude are called **parallels** and form circles parallel to the equator.
   - The length of a parallel decreases with increasing latitude, becoming a point at the poles.

4. **Effect on Climate**:
   - Latitude is a primary determinant of **climate zones** due to the variation in solar insolation:
     - **Low latitudes (0°–30°)**: Tropical and subtropical climates.
     - **Mid latitudes (30°–60°)**: Temperate climates.
     - **High latitudes (60°–90°)**: Polar and subpolar climates.

---

### **Applications**
1. **Navigation**:
   - Latitude is critical for **celestial navigation**, GPS systems, and flight planning.
   - Historically, latitude was determined using instruments like the **sextant** to measure the angle of the Sun or stars above the horizon.

2. **Cartography**:
   - Latitude lines form the horizontal grid on maps and globes.
   - Projections (e.g., Mercator, Robinson) distort latitude to preserve specific properties (e.g., shape, area).

3. **Orbital Mechanics**:
   - The **[[inclination]]** of a satellite's orbit is defined relative to the Earth's [[equatorial plane]], analogous to latitude.
   - Ground tracks of satellites are often described in terms of the latitudes they cross.

4. **Climatology and Ecology**:
   - Latitude influences **biodiversity**, **daylight duration**, and **seasonal variations**.
   - Example: The **Arctic Circle** (66.5°N) marks the southern limit of the polar day/night phenomenon.

5. **Astronomy**:
   - The **[[Declination]]** of celestial objects (analogous to latitude) is measured relative to the celestial equator.
   - Observatories are often located at specific latitudes to optimize viewing of the night sky.

---

### **Relation to Other Coordinates**
1. **Cartesian Coordinates**:
   For a sphere of radius $R$, latitude $\phi$ and [[Geographic Longitude]] $\lambda$ can be converted to Cartesian coordinates $(x, y, z)$ as:
   $$
   x = R \cos \phi \cos \lambda, \quad y = R \cos \phi \sin \lambda, \quad z = R \sin \phi.
   $$

2. **Spherical Coordinates**:
   Latitude is complementary to the **polar angle** $\theta$ in mathematics, where $\theta = 90° - \phi$.

3. **UTM and Other Projections**:
   - Latitude is a key input for converting geographic coordinates to **Universal Transverse Mercator (UTM)** or other map projections.

---

### **Historical Context**
- The concept of latitude dates back to **ancient Greek astronomy**, with **Eratosthenes** (3rd century BCE) being one of the first to calculate latitudes using the Sun's angle.
- **Ptolemy** (2nd century CE) developed a system of latitude and [[Geographic Longitude]] in his *Geography*.
- Modern latitude measurements rely on **geodetic reference systems** like **WGS84** (World Geodetic System 1984), used by GPS.

---

### **Suggested Additions for Your Note**
1. **Links**:
   - [[Geographic Longitude]] (complementary coordinate)
   - [[Geodetic System]] (reference ellipsoids and datums)
   - [[Inclination]] (latitude analog in orbital mechanics)
   - [[Climate Zones]] (latitude-dependent climate classification)
2. **Diagrams**:
   - Illustration of geodetic vs. geocentric latitude on an oblate spheroid.
   - Map showing major latitude lines (e.g., Tropic of Cancer, Arctic Circle).
3. **Examples**:
   - Calculation of the length of a parallel at a given latitude.
   - Derivation of solar insolation as a function of latitude and time of year.
1. **Tags**: `#geography`, `#navigation`, `#orbital-mechanics`, `#climatology`, `#geodesy`.
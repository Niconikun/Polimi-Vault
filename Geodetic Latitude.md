## Formal Definition

**Geodetic Latitude** ($\phi$) is the angle formed between the [[equatorial plane]] of an ellipsoidal model of the Earth and a line that is normal (perpendicular) to the surface of that ellipsoid at a specific point. Unlike geocentric latitude, which measures the angle from the Earth's center, geodetic latitude accounts for the Earth's flattening at the poles. It is the standard latitude used in mapping, GPS coordinates, and maritime navigation, typically expressed in degrees, minutes, and seconds north or south of the equator.



## Historical Development

### Key Milestones
- **1687:** Isaac Newton predicts in *Principia* that the Earth is an oblate spheroid rather than a perfect sphere due to its rotation.
- **1736–1737:** The French Geodesic Mission to Lapland, led by Pierre Louis Maupertuis, confirms the Earth's polar flattening, necessitating a distinction between spherical and ellipsoidal latitude.
- **1841:** Friedrich Bessel calculates the "Bessel Ellipsoid," providing one of the first highly accurate mathematical models for geodetic calculations.
- **1984:** The creation of the **WGS 84** (World Geodetic System) provides the current global standard ellipsoid used by GPS.

### Foundational Contributors
1. **Isaac Newton (1642–1727):** Provided the theoretical basis for the Earth's non-spherical shape.
2. **Friedrich Wilhelm Bessel (1784–1846):** A key figure in geodesy who refined the mathematical parameters of the Earth's ellipsoid.
3. **George Everest (1790–1866):** His work on the Great Trigonometrical Survey of India led to significant refinements in measuring geodetic coordinates over large landmasses.

## Mathematical Formulation

### General Form
Geodetic latitude is defined by the angle between the normal to the ellipsoid and the [[equatorial plane]]. It can be related to the geocentric latitude ($\psi$) by the following relationship:

$$
\tan \psi = (1 - f)^2 \tan \phi = \frac{b^2}{a^2} \tan \phi
$$

### Component Breakdown
- **$\phi$:** Geodetic latitude.
- **$\psi$:** Geocentric latitude.
- **$a$:** [[Semi-Major Axis]] (Equatorial radius).
- **$b$:** Semi-minor axis (Polar radius).
- **$f$:** Flattening of the ellipsoid ($f = \frac{a-b}{a}$).

### Cartesian Coordinates
The position of a point $(x, y, z)$ on the surface of the ellipsoid can be expressed using geodetic latitude:
$$
x = N(\phi) \cos \phi \cos \lambda
$$
$$
y = N(\phi) \cos \phi \sin \lambda
$$
$$
z = [N(\phi)(1 - e^2)] \sin \phi
$$
Where $N(\phi)$ is the radius of curvature in the prime vertical.

## Fundamental Principles

### Core Assumptions
1. **Ellipsoidal Model:** Assumes the Earth is a perfect oblate spheroid (ignoring local topographic variations or the [[geoid]]).
2. **Normal Line:** The latitude is defined by the line perpendicular to the *model surface*, which does not necessarily pass through the Earth's center.

### Governing Laws/Theorems
- **The Reference Ellipsoid:** The specific [[mathematical model]] (like WGS 84 or GRS 80) chosen to represent the Earth's surface.
- **Deflection of the Vertical:** The difference between the geodetic normal and the actual direction of gravity (the plumb line).

## Theoretical Framework

### Geodetic vs. Geocentric Latitude
Because the Earth is wider at the equator, a line drawn perpendicular to the surface at mid-latitudes will miss the Earth's center by several kilometers. 
- **Geodetic ($\phi$):** Based on the surface normal. This is what you see on a map.
- **Geocentric ($\psi$):** Based on a ray from the center. This is used in some orbital mechanics and satellite calculations.
The difference between the two is zero at the equator and the poles, reaching a maximum of about 11.5 arcminutes at $45^\circ$ latitude.

[Image showing the normal to the ellipsoid not passing through the center]

## Physical Interpretation

### Geometric Meaning
If you were to stand on the Earth with a level, geodetic latitude is the angle your "straight up" (defined by the ellipsoid model) makes with the equator. Because the Earth's surface curves more "slowly" near the poles, you have to travel a greater physical distance for your geodetic latitude to change by one degree as you move away from the equator.

## Advantages and Limitations

### Strengths
1. **Practical Mapping:** Aligns with the horizon and local vertical, making it intuitive for terrestrial surveying.
2. **Standardization:** Allows for a universal coordinate system (GPS) that works across all continents.

### Limitations
1. **Mathematical Complexity:** Formulas for distance and navigation are significantly more complex on an ellipsoid than on a sphere.
2. **Model Dependency:** Geodetic latitude changes slightly if you switch from one reference ellipsoid (e.g., NAD27) to another (e.g., WGS 84).

## Applications

### Disciplines
1. **Cartography and GIS:** The basis for all modern mapping and Geographic Information Systems.
2. **Aviation and Maritime Navigation:** Used for Great Circle (orthodromic) and Rhumb Line calculations.
3. **Geodesy:** Used to measure crustal deformation and sea-level rise.

### Practical Implementations
- **GPS Units:** Automatically convert raw satellite signals into WGS 84 geodetic coordinates.
- **Google Maps:** Uses geodetic coordinates projected via Web Mercator for display.

## See Also

- [[Reference Ellipsoid]]
- [[Geoid]]
- [[WGS 84]]
- [[Observer Meridian]]
- [[Geocentric Latitude]]
- [[Radius of Curvature]]

## Recommended Tags:
#geodesy #navigation #cartography #geodetic-latitude #mapping #earth-sciences #astronomy
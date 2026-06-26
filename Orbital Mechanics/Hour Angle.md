#Orbital-Mechanics #DONE 
### Formal Definition

The **Hour Angle** of a celestial body is the angular distance on the [[Celestial Sphere]] measured **westward** along the celestial equator from the observer's local meridian to the hour circle containing the body.

Let's break down the key components of this definition:

*   **Angular Distance:** It is measured in units of time (hours, minutes, seconds) or degrees.
    *   `1 hour = 15 degrees` (since 360°/24h = 15°/h)
*   **[[Celestial Sphere]]:** The imaginary sphere of infinite radius upon which all celestial objects are projected.
*   **[[Celestial Equator]]:** The projection of the Earth's equator onto the [[Celestial Sphere]].
*   **Observer's Local Meridian:** The great circle on the [[Celestial Sphere]] that passes through the observer's zenith (the point directly overhead) and the celestial poles (North and South). It is the line dividing the observer's visible sky into eastern and western halves.
*   **Hour Circle:** A great circle on the [[Celestial Sphere]] that passes through the celestial poles and the celestial body in question. It is analogous to a line of [[Geographic Longitude]] on Earth, but projected onto the sky.

### Interpretation and Significance

The Hour Angle is a measure of **how much time has passed** since the celestial body last transited (crossed) the observer's local meridian.

*   **Hour Angle = 0h:** The body is currently on the observer's local meridian. This moment is called **culmination** or **meridian transit**, and it is when the object reaches its highest altitude in the sky for that day.
*   **Hour Angle = 2h:** The body transited the meridian 2 hours ago and is now located 30 degrees (2h * 15°/h) to the **west** of the meridian.
*   **Hour Angle = -1h (or 23h):** The body will transit the meridian in 1 hour and is currently located 15 degrees to the **east** of the meridian.

### The Critical Relationship: Linking Time and Position

The Hour Angle is the crucial link between the equatorial coordinate system (which is fixed to the sky) and the diurnal motion of the [[Celestial Sphere]] (which is caused by the Earth's rotation). This is encapsulated in the fundamental formula:

**[[Local Sidereal Time]] = [[Right Ascension]] (RA) of a object + its Hour Angle (HA)**

Or, rearranged:
**Hour Angle (HA) = [[Local Sidereal Time]] - [[Right Ascension]] (RA)**

This equation is of paramount importance because:
*   **[[Right Ascension]] (RA)** is the object's "celestial [[Geographic Longitude]]," fixed on the [[Celestial Sphere]].
*   **[[Local Sidereal Time]]** is, by definition, the [[Right Ascension]] of stars currently on the observer's local meridian (i.e., the RA for which HA = 0).
*   **Hour Angle (HA)** is the object's position relative to the observer's meridian *at a specific moment in time*.

### Types of Hour Angle

1.  **Local Hour Angle (LHA):** The standard definition, as given above, measured from the observer's local meridian.
2.  **Greenwich Hour Angle (GHA):** The hour angle of a body measured from the [[Greenwich Meridian]](Prime) Meridian. It is used in nautical and astronomical almanacs for navigation.
    *   `LHA = GHA - Observer's West [[Longitude]]` (or `GHA + Observer's East Longitude`)

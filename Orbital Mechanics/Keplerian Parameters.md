#Orbital-Mechanics #DONE
### **Formal Definition**

**Keplerian Parameters (Classical Orbital Elements)**

The **Keplerian parameters** are a set of six independent scalar quantities that uniquely define the size, shape, and orientation of a celestial body's orbit around a primary, as well as the position of the orbiting body within that orbit at a specific [[Epoch]]. They provide a complete mathematical description of a two-body Keplerian orbit.

These parameters are defined with respect to a fundamental plane and a reference direction within an inertial reference frame, typically the **Geocentric Equatorial Coordinate System** for Earth-orbiting satellites or the **Heliocentric [[Ecliptic Coordinate System]]** for planets.

---

### **The Six Classical Orbital Elements**

The following table lists the six parameters, grouped by their function:

| Parameter                                       | Symbol                 | Role                  | Description                                                                                                                                 |
| :---------------------------------------------- | :--------------------- | :-------------------- | :------------------------------------------------------------------------------------------------------------------------------------------ |
| **1. [[Semi-Major Axis]]**                      | $a$                | **Orbit Size**        | Defines the size of the ellipse. Half the length of the longest diameter. Directly related to the orbital period via [[Kepler's Time Law]]. |
| **2. [[Eccentricity]]**                         | $e$                | **Orbit Shape**       | Defines the shape of the [[Elliptical Orbit]] (how much it deviates from a circle). Ranges from 0 (circle) to 1 (parabola).                 |
| **3. [[Inclination]]**                          | $i$                | **Orbit Tilt**        | The vertical angle between the [[orbital plane]] and the fundamental plane (e.g., the [[Celestial Equator]]).                                   |
| **4. [[Geographic Longitude]] of the Ascending Node [[Right Ascension of the Ascending Node]]** | $\Omega$           | **Orbit Swivel**      | The horizontal angle that locates the [[orbital plane]]'s line of nodes. Defines where the orbit crosses the fundamental plane.                 |
| **5. [[Argument of Periapsis]]**                | $\omega$           | **Orbit Rotation**    | Defines the orientation of the ellipse's major axis within the [[Orbital Plane]].                                                           |
| **6. [[True Anomaly]] at [[Epoch]]**            | $\nu$ (or $M$) | **Position in Orbit** | Specifies the location of the orbiting body along the ellipse at a specific time (the [[Epoch]]).                                               |

### **Detailed Explanation and Geometric Interpretation**

These elements can be visualized in a three-step process to build the orbit:

1.  **Define the [[Orbital Plane]]:**
    *   The orbit lies in a plane. We define its orientation relative to a fundamental plane (e.g., the Earth's [[equatorial plane]]).
    *   **[[Inclination]] ($i$):** The tilt of the [[orbital plane]]. Measured from 0° to 180°. Orbits with $i < 90^\circ$ are **prograde**; with $i > 90^\circ$ are **retrograde**.
    *   **[[Geographic Longitude]] of the Ascending Node ($\Omega$):** The ascending node is the point where the satellite crosses the fundamental plane moving from south to north. $\Omega$ is the angle, measured eastward from the [[Vernal Equinox]] (γ), to the ascending node.

2.  **Define the Orbit within the Plane:**
    *   Once the plane is fixed, we define the ellipse within that plane.
    *   **[[Semi-Major Axis]] ($a$):** Determines the physical size and energy of the orbit.
    *   **[[Eccentricity]] ($e$):** Determines the shape, from circular ($e=0$) to highly elliptical.
    *   **[[Argument of Periapsis]] ($\omega$):** The angle, measured within the [[orbital plane]] from the ascending node to the [[Periapsis]] (the point of closest approach). It defines the orientation of the ellipse's long axis.

3.  **Locate the Object on the Orbit:**
    *   **[[True Anomaly]] at [[Epoch]] ($\nu$):** The angular parameter that gives the object's position relative to [[Periapsis]] at a specific time (the **[[Epoch]]**). Sometimes the **[[Mean Anomaly]] ($M$)** is used instead, as it varies linearly with time and is related to $\nu$ via [[Kepler's Equation]].

### **Significance and Application**

*   **Complete State Description:** These six elements are equivalent to knowing the position and velocity vectors ($\vec{r}, \vec{v}$) of the object at a given time. They are simply a more intuitive and physically meaningful representation for orbital mechanics.
*   **Orbit Classification:** They are used to classify orbits (e.g., Low Earth Orbit: defined by $a$, Geostationary: defined by $a, e, i$, Molniya: defined by $e, i, \omega$).
*   **Perturbations:** In a perfect two-body system, the first five elements are constant. In reality, perturbations (e.g., Earth's oblateness, [[atmospheric drag]], third-body gravity) cause them to change slowly over time. Tracking these changes is essential for precise orbit determination and station-keeping.

In summary, the **Keplerian parameters** are the six fundamental quantities that provide a complete and elegant description of an object's orbit, defining its **size** ($a$), **shape** ($e$), **orientation in space** ($i, \Omega, \omega$), and the object's **position within it** ($\nu$) at a specified time.
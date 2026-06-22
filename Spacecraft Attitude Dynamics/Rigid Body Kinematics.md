#SAD #DONE 

**[[Rigid Body]] [[Kinematics]]** is the branch of classical mechanics that describes the _motion_ of a rigid body without considering the _forces_ or _torques_ that cause it. A rigid body is an idealized solid object in which the distance between any two given points remains constant in [[Time]], regardless of external forces exerted on it.

The study of rigid body kinematics is fundamentally concerned with two distinct aspects of motion:

1. **[[Translation]]:** The change in [[position]] of a single reference point (typically the [[Center of Mass]]) of the body relative to an [[Inertial Frame of Reference]]. This is described by the linear position, velocity, and acceleration vectors of that point.
    
2. **[[Rotation]]:** The change in _orientation_ of the body about its reference point. This describes how a coordinate system fixed to the body (the [[Body Reference Frame]]) is reoriented with respect to a fixed, inertial reference frame.
    

The primary challenge, and the core of rigid body kinematics, lies in quantitatively describing the rotational motion. This involves defining:

- **[[Attitude]] Representations:** Methods for parameterizing the orientation, such as:
    
    - [[Direction Cosine Matrix]] Matrix (DCM or Rotation Matrix):** A 3x3 orthogonal matrix that transforms vector coordinates from the body frame to the inertial frame.
        
    - [[Euler Angles]]:** A set of three sequential rotation angles (e.g., roll, pitch, yaw) about specific axes.
        
    - **Euler Parameters ([[Quaternion]]):** A four-parameter representation that is non-singular and computationally efficient, making it highly preferred in spacecraft applications.
        
    - **[[Euler Axis and Angle]]**
        
- **[[Angular Velocity]]:** The vector `ω` that describes the instantaneous axis and rate of rotation of the body. It is crucial to note that [[Angular Velocity]] is _not_ the derivative of any single vector [[attitude]] parameter (like [[Euler angles]]); its relationship is governed by specific kinematic differential equations.
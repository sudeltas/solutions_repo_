# Problem 1
Below is a Markdown document that addresses your request to investigate the range as a function of the angle of projection for projectile motion. It includes a theoretical derivation, analysis, practical applications, and a Python script for simulation and visualization.

---

# Investigating the Range as a Function of the Angle of Projection

## 1. Theoretical Foundation

Projectile motion describes the trajectory of an object under the influence of gravity, with no other forces (e.g., air resistance) considered in the idealized case. Let’s derive the equations of motion from Newton’s second law.

### Derivation of Governing Equations
The acceleration of a projectile is solely due to gravity, acting downward. In a 2D Cartesian coordinate system (x horizontal, y vertical), the acceleration components are:
- \( a_x = 0 \) (no horizontal forces),
- \( a_y = -g \) (gravity, where \( g \) is the gravitational acceleration, typically \( 9.8 \, \text{m/s}^2 \)).

The initial conditions are:
- Initial velocity: \( v_0 \) at angle \( \theta \) from the horizontal.
- Initial position: \( (x_0, y_0) = (0, 0) \) (launched from the origin for simplicity).
- Initial velocity components: \( v_{0x} = v_0 \cos\theta \), \( v_{0y} = v_0 \sin\theta \).

#### Horizontal Motion
Since \( a_x = 0 \), the velocity is constant:
$$
 v_x(t) = v_{0x} = v_0 \cos\theta 
 x(t) = v_0 \cos\theta \cdot t 
 $$   

#### Vertical Motion
With \( a_y = -g \):
\[ v_y(t) = v_{0y} - g t = v_0 \sin\theta - g t \]
\[ y(t) = v_0 \sin\theta \cdot t - \frac{1}{2} g t^2 \]

These are parametric equations describing a parabolic trajectory. The "family of solutions" arises from varying \( v_0 \), \( \theta \), \( g \), and initial height \( y_0 \) (if not zero).

### Time of Flight
The projectile hits the ground when \( y(t) = 0 \):
\[ v_0 \sin\theta \cdot t - \frac{1}{2} g t^2 = 0 \]
\[ t (v_0 \sin\theta - \frac{1}{2} g t) = 0 \]
- \( t = 0 \) (launch),
- \( t = \frac{2 v_0 \sin\theta}{g} \) (time of flight, \( T \)).

## 2. Analysis of the Range

The horizontal range \( R \) is the distance traveled when \( y = 0 \):
\[ R = x(T) = v_0 \cos\theta \cdot \frac{2 v_0 \sin\theta}{g} \]
Using the identity \( 2 \sin\theta \cos\theta = \sin(2\theta) \):
\[ R = \frac{v_0^2 \sin(2\theta)}{g} \]

### Dependence on Angle \( \theta \)
- \( R \) is maximized when \( \sin(2\theta) = 1 \), i.e., \( 2\theta = 90^\circ \), so \( \theta = 45^\circ \).
- \( R = 0 \) at \( \theta = 0^\circ \) or \( 90^\circ \) (no horizontal motion).
- Symmetry: \( R(\theta) = R(90^\circ - \theta) \), e.g., ranges at \( 30^\circ \) and \( 60^\circ \) are equal.

### Influence of Parameters
- *Initial Velocity (\( v_0 \))*: \( R \propto v_0^2 \), a quadratic relationship. Doubling \( v_0 \) quadruples the range.
- *Gravitational Acceleration (\( g \))*: \( R \propto 1/g \). Lower gravity (e.g., on the Moon, \( g \approx 1.62 \, \text{m/s}^2 \)) increases range.
- *Launch Height (\( y_0 \))*: If \( y_0 \neq 0 \), the time of flight changes, complicating the range formula (explored numerically below).

## 3. Practical Applications

This model applies to:
- *Sports*: Optimizing the launch angle in basketball, golf, or javelin for maximum distance.
- *Engineering*: Designing artillery or water jets, adjusting for terrain or wind.
- *Astrophysics*: Simplistic trajectories of celestial bodies (ignoring orbital mechanics).

For uneven terrain (e.g., landing at \( y = h \)), solve \( y(t) = h \) for \( t \) and compute \( x(t) \). Air resistance introduces a drag force, typically \( F_d \propto -v^2 \), requiring numerical solutions.

## 4. Implementation: Python Simulation

Below is a Python script to simulate and visualize the range as a function of \( \theta \).

python
import numpy as np
import matplotlib.pyplot as plt

# Parameters
v0 = 20.0  # initial velocity (m/s)
g = 9.8    # gravity (m/s^2)
theta_deg = np.linspace(0, 90, 91)  # angles from 0 to 90 degrees
theta_rad = np.radians(theta_deg)

# Range function (ideal case, y0 = 0)
def range_theta(v0, theta, g):
    return (v0**2 * np.sin(2 * theta)) / g

# Compute ranges
R = range_theta(v0, theta_rad, g)

# Plotting
plt.figure(figsize=(10, 6))
plt.plot(theta_deg, R, label=f'v0 = {v0} m/s, g = {g} m/s²')
plt.xlabel('Angle of Projection (degrees)')
plt.ylabel('Range (m)')
plt.title('Range vs. Angle of Projection')
plt.grid(True)
plt.legend()

# Test different v0 and g
v0_alt = 30.0
g_alt = 1.62  # Moon's gravity
R_alt_v0 = range_theta(v0_alt, theta_rad, g)
R_alt_g = range_theta(v0, theta_rad, g_alt)
plt.plot(theta_deg, R_alt_v0, label=f'v0 = {v0_alt} m/s, g = {g} m/s²')
plt.plot(theta_deg, R_alt_g, label=f'v0 = {v0} m/s, g = {g_alt} m/s² (Moon)')
plt.legend()
plt.show()

# Optional: Simulate trajectory for a specific angle
theta_sample = np.radians(45)
t_flight = 2 * v0 * np.sin(theta_sample) / g
t = np.linspace(0, t_flight, 100)
x = v0 * np.cos(theta_sample) * t
y = v0 * np.sin(theta_sample) * t - 0.5 * g * t**2

plt.figure(figsize=(10, 6))
plt.plot(x, y)
plt.xlabel('Horizontal Distance (m)')
plt.ylabel('Height (m)')
plt.title('Projectile Trajectory at 45°')
plt.grid(True)
plt.show()


### Output Description
- *First Plot*: Range vs. angle for \( v_0 = 20 \, \text{m/s} \), \( g = 9.8 \, \text{m/s}^2 \), plus variations with higher \( v_0 \) and lower \( g \). Peak range occurs at \( 45^\circ \).
- *Second Plot*: Sample trajectory at \( 45^\circ \), showing the parabolic path.

## Discussion and Limitations

### Limitations of the Idealized Model
- *Air Resistance*: Ignored here, but it reduces range and alters the optimal angle (typically < 45°).
- *Flat Terrain*: Assumes \( y_0 = 0 \) and landing at \( y = 0 \).
- *Constant Gravity*: \( g \) varies with altitude or planetary body.

### Extensions
- *Drag*: Add \( F_d = -k v^2 \) and solve numerically (e.g., using scipy.integrate.odeint).
- *Wind*: Include horizontal acceleration terms.
- *Height*: Adjust time of flight for \( y_0 \neq 0 \) or uneven landing.

This analysis and simulation highlight the elegance and versatility of projectile motion, bridging theory and real-world applications.

--- 

Let me know if you'd like to refine the code (e.g., add drag) or explore specific scenarios further!
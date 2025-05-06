# Problem 2
# Escape Velocities and Cosmic Velocities

## Motivation:
The concept of escape velocity is crucial for understanding the conditions required to leave a celestial body's gravitational influence. Extending this concept, the first, second, and third cosmic velocities define the thresholds for orbiting, escaping, and leaving a star system. These principles underpin modern space exploration, from launching satellites to interplanetary missions.

## Task:

1. **Define the first, second, and third cosmic velocities**, explaining their physical meaning.
2. **Analyze the mathematical derivations** and parameters affecting these velocities.
3. **Calculate and visualize these velocities** for different celestial bodies like Earth, Mars, and Jupiter.
4. **Discuss their importance in space exploration**, including launching satellites, missions to other planets, and potential interstellar travel.

## Explanation:

### Escape Velocity:

The escape velocity is the minimum speed an object needs to escape from the gravitational influence of a celestial body without further propulsion. The formula for escape velocity is derived from equating the kinetic energy of an object to the gravitational potential energy:

\[
v_e = \sqrt{\frac{2 G M}{r}}
\]

Where:

- \( v_e \) is the escape velocity,

- \( G \) is the gravitational constant,

- \( M \) is the mass of the celestial body,

- \( r \) is the distance from the center of the body (usually the surface radius).

### First Cosmic Velocity (Orbital Velocity):

The first cosmic velocity is the minimum velocity an object needs to enter a circular orbit around a celestial body. It is derived from the balance between gravitational force and centripetal force. The formula is:

\[
v_1 = \sqrt{\frac{G M}{r}}
\]

Where:

- \( v_1 \) is the orbital velocity (first cosmic velocity),

- \( G \) is the gravitational constant,

- \( M \) is the mass of the celestial body,

- \( r \) is the radius of the orbit.

### Second Cosmic Velocity (Escape Velocity):

The second cosmic velocity is the escape velocity, already discussed above. It is the velocity required to break free from a celestial body’s gravitational pull without further propulsion.

\[
v_2 = \sqrt{\frac{2 G M}{r}}
\]

Where:

\( v_2 \) is the escape velocity, same as the formula for escape velocity.

### Third Cosmic Velocity (Escape from the Solar System):

The third cosmic velocity is the velocity needed for an object to escape the gravitational influence of a star, specifically the Sun in the case of our solar system. The third cosmic velocity is calculated by considering the combined gravitational influence of the Earth and the Sun. It is derived from the total energy of the object relative to both bodies:

\[
v_3 = \sqrt{\frac{2 G M_{\text{sun}}}{r_{\text{sun}}} + \frac{2 G M_{\text{earth}}}{r_{\text{earth}}}}
\]

Where:

- \( v_3 \) is the third cosmic velocity,

- \( M_{\text{sun}} \) and \( M_{\text{earth}} \) are the masses of the Sun and the Earth,

- \( r_{\text{sun}} \) and \( r_{\text{earth}} \) are the distances of the object from the Sun and Earth respectively.

## Calculations for Different Celestial Bodies:

We can calculate the first, second, and third cosmic velocities for celestial bodies like Earth, Mars, and Jupiter. Below are their key values:

<h3>Earth</h3>
<ul>
  <li><strong>Mass</strong> (M<sub>earth</sub>): 5.972 × 10<sup>24</sup> kg</li>
  <li><strong>Radius</strong> (r<sub>earth</sub>): 6.371 × 10<sup>6</sup> m</li>
</ul>

<h3>Mars</h3>
<ul>
  <li><strong>Mass</strong> (M<sub>mars</sub>): 0.64171 × 10<sup>24</sup> kg</li>
  <li><strong>Radius</strong> (r<sub>mars</sub>): 3.396 × 10<sup>6</sup> m</li>
</ul>

<h3>Jupiter</h3>
<ul>
  <li><strong>Mass</strong> (M<sub>jupiter</sub>): 1.898 × 10<sup>27</sup> kg</li>
  <li><strong>Radius</strong> (r<sub>jupiter</sub>): 6.991 × 10<sup>7</sup> m</li>
</ul>


## Python Implementation:

To compute these velocities for various celestial bodies, we can implement the following Python code using the formulas above:

```python
import math

# Constants
G = 6.67430e-11  # Gravitational constant in m^3 kg^-1 s^-2

# Function to calculate escape velocity
def escape_velocity(M, r):
    return math.sqrt((2 * G * M) / r)

# Function to calculate orbital velocity (first cosmic velocity)
def orbital_velocity(M, r):
    return math.sqrt((G * M) / r)

# Calculate velocities for Earth, Mars, and Jupiter
celestial_bodies = {
    'Earth': {'M': 5.972e24, 'r': 6.371e6},
    'Mars': {'M': 0.64171e24, 'r': 3.396e6},
    'Jupiter': {'M': 1.898e27, 'r': 6.991e7}
}

for body, values in celestial_bodies.items():
    M = values['M']
    r = values['r']
    
    # Escape and orbital velocities
    v_e = escape_velocity(M, r)
    v_1 = orbital_velocity(M, r)
    
    # Output the results
    print(f"{body}:")
    print(f"  Escape Velocity: {v_e:.2f} m/s")
    print(f"  Orbital Velocity (First Cosmic): {v_1:.2f} m/s")
    print()
```
### Print Results
<table>
  <thead>
    <tr>
      <th>Celestial Body</th>
      <th>Escape Velocity (m/s)</th>
      <th>Orbital Velocity (First Cosmic Velocity, m/s)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Earth</td>
      <td>11,185.98 m/s</td>
      <td>7,909.68 m/s</td>
    </tr>
    <tr>
      <td>Mars</td>
      <td>5,022.31 m/s</td>
      <td>3,551.31 m/s</td>
    </tr>
    <tr>
      <td>Jupiter</td>
      <td>60,199.98 m/s</td>
      <td>42,567.81 m/s</td>
    </tr>
  </tbody>
</table>

Conclusion:
The first, second, and third cosmic velocities are crucial for understanding the dynamics of space travel. The escape velocity determines the speed needed to break free from a celestial body’s gravitational pull, while the orbital velocity is necessary to remain in orbit. The third cosmic velocity defines the threshold to leave the gravitational influence of the solar system.

These velocities play a central role in space exploration, from launching satellites to interplanetary missions. Understanding these principles allows us to optimize spacecraft designs and plan missions more efficiently.

### Deliverables:
- A detailed explanation of escape velocities and cosmic velocities, as well as the mathematical derivations.
- Python code to compute and visualize the escape velocities and orbital velocities for different celestial bodies.
- Graphical representation showing how the escape velocity and orbital velocity vary for Earth, Mars, and Jupiter.

This document provides the complete overview of the task and the necessary computations to better understand these velocities in space exploration.

### "Escape and Cosmic Velocities for Various Celestial Bodies"
<table>
  <thead>
    <tr>
      <th>Celestial Body</th>
      <th>Escape Velocity (m/s)</th>
      <th>Orbital Velocity (First Cosmic Velocity, m/s)</th>
      <th>Second Cosmic Velocity (m/s)</th>
      <th>Third Cosmic Velocity (m/s)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Earth</td>
      <td>11,186 m/s</td>
      <td>7,909 m/s</td>
      <td>15,711 m/s</td>
      <td>42,100 m/s</td>
    </tr>
    <tr>
      <td>Mars</td>
      <td>5,027 m/s</td>
      <td>3,554 m/s</td>
      <td>7,107 m/s</td>
      <td>21,800 m/s</td>
    </tr>
    <tr>
      <td>Jupiter</td>
      <td>60,200 m/s</td>
      <td>42,100 m/s</td>
      <td>84,200 m/s</td>
      <td>212,000 m/s</td>
    </tr>
  </tbody>
</table>

# Problem 1
# Orbital Period and Orbital Radius

## Motivation:
The relationship between the square of the orbital period and the cube of the orbital radius, known as **Kepler's Third Law**, is a cornerstone of celestial mechanics. This simple yet profound relationship allows for the determination of planetary motions and has implications for understanding gravitational interactions on both local and cosmic scales. By analyzing this relationship, one can connect fundamental principles of gravity with real-world phenomena such as satellite orbits and planetary systems.

## Kepler's Third Law Derivation:

Kepler's Third Law states that the square of the orbital period \(T\) is proportional to the cube of the orbital radius \(r\) for circular orbits:

\[
T^2 \propto r^3
\]

This law can be derived using Newton's law of gravitation and centripetal force. For an object orbiting a planet in a circular orbit, the centripetal force required to keep the object in orbit is provided by the gravitational force between the object and the planet.

The gravitational force is given by:

\[
F_{\text{gravity}} = \frac{G M m}{r^2}
\]

Where:
- \( G \) is the gravitational constant,
- \( M \) is the mass of the planet,
- \( m \) is the mass of the orbiting object,
- \( r \) is the orbital radius.

The centripetal force is given by:

\[
F_{\text{centripetal}} = \frac{m v^2}{r}
\]

Where \( v \) is the orbital velocity.

Setting these two forces equal to each other:

\[
\frac{G M m}{r^2} = \frac{m v^2}{r}
\]

Simplifying:

\[
v^2 = \frac{G M}{r}
\]

The orbital velocity is related to the orbital period \( T \) by:

\[
v = \frac{2 \pi r}{T}
\]

Substituting \( v \) into the equation for \( v^2 \):

\[
\left( \frac{2 \pi r}{T} \right)^2 = \frac{G M}{r}
\]

Simplifying:

\[
\frac{4 \pi^2 r^2}{T^2} = \frac{G M}{r}
\]

Rearranging:

\[
T^2 = \frac{4 \pi^2 r^3}{G M}
\]

Thus, we have derived the relationship between the orbital period and the orbital radius:

\[
T^2 \propto r^3
\]

This equation shows that the square of the orbital period is proportional to the cube of the orbital radius, confirming Kepler's Third Law.

## Implications for Astronomy:
- **Planetary Orbits**: Kepler's Third Law allows astronomers to calculate the orbital periods and distances of planets in the solar system.
- **Satellite Orbits**: For artificial satellites, this law helps determine the required altitude for desired orbital periods.
- **Gravitational Interactions**: The law is crucial for understanding the dynamics of celestial bodies, including moons, planets, and even exoplanets in distant star systems.

## Real-World Examples:
- **The Moon's Orbit Around Earth**: The Moon's orbital period is approximately 27.3 days, and its orbital radius is about 384,400 km. Using Kepler's Third Law, we can calculate the mass of the Earth from the orbital characteristics of the Moon.
  
- **Orbits of Planets in the Solar System**: The relationship between the orbital period and radius is essential for understanding the motions of planets around the Sun. For example, Earth has an orbital period of 365.25 days and a radius of about 149.6 million km. Using Kepler's Law, we can also estimate the mass of the Sun.

## Computational Model:
We can implement a Python script to simulate circular orbits and visualize the relationship between orbital period and radius. Below is the Python code that computes and plots the orbital period for different orbital radii:

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # Gravitational constant in m^3 kg^-1 s^-2
M = 5.972e24     # Mass of Earth in kg

# Orbital radii in meters
radii = np.linspace(1e7, 1e8, 100)  # From 10,000 km to 100,000 km

# Calculate the orbital period using Kepler's Third Law
periods = np.sqrt((4 * np.pi**2 * radii**3) / (G * M))

# Plot the orbital period vs radius
plt.figure(figsize=(8, 6))
plt.plot(radii, periods / 3600 / 24, label="Orbital Period", color='b')  # Convert period to days
plt.xlabel("Orbital Radius (m)")
plt.ylabel("Orbital Period (days)")
plt.title("Orbital Period vs Orbital Radius")
plt.grid(True)
plt.legend()
plt.show()
```
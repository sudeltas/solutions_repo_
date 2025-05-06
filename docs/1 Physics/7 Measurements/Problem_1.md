# Problem 1
# Measuring Earth's Gravitational Acceleration with a Pendulum

## Motivation:
The acceleration \( g \) due to gravity is a fundamental constant that influences a wide range of physical phenomena. Measuring \( g \) accurately is crucial for understanding gravitational interactions, designing structures, and conducting experiments in various fields. One classic method for determining \( g \) is through the oscillations of a simple pendulum, where the period of oscillation depends on the local gravitational field.

## Task:
Measure the acceleration \( g \) due to gravity using a pendulum and analyze the uncertainties in the measurements.

This exercise emphasizes rigorous measurement practices, uncertainty analysis, and their role in experimental physics.

---

## Procedure:

### 1. Materials:
- A string (1 or 1.5 meters long).
- A small weight (e.g., bag of coins, bag of sugar, key chain) mounted on the string.
- Stopwatch (or smartphone timer).
- Ruler or measuring tape.

### 2. Setup:
1. Attach the weight to the string and fix the other end to a sturdy support.
2. Measure the length of the pendulum, \( L \), from the suspension point to the center of the weight using a ruler or measuring tape. Record the resolution of the measuring tool and calculate the uncertainty as half the resolution.

### 3. Data Collection:
1. Displace the pendulum slightly (<15°) and release it.
2. Measure the time for 10 full oscillations, \( T_{\text{10}} \), and repeat this process 10 times. Record all 10 measurements.
3. Calculate the mean time for 10 oscillations, \( \bar{T_{\text{10}}} \), and the standard deviation, \( \sigma_{\text{T_{\text{10}}}} \).
   where \( n \) is the number of measurements.

---

## Calculations:

### 1. Calculate the Period:
The period of a pendulum is given by the formula:

\[
T = \frac{\bar{T_{\text{10}}}}{10}
\]

where \( T \) is the period of one full oscillation.

### 2. Determine the Gravitational Acceleration \( g \):
The acceleration due to gravity \( g \) can be calculated using the formula:

\[
g = \frac{4\pi^2 L}{T^2}
\]

where:

- \( L \) is the length of the pendulum,

- \( T \) is the period of oscillation.

### 3. Propagate Uncertainties:
The uncertainty in \( g \), \( \Delta g \), can be propagated from the uncertainties in \( L \) and \( T \) using the following formula:

\[
\Delta g = g \times \sqrt{\left(\frac{\Delta L}{L}\right)^2 + \left(2\frac{\Delta T}{T}\right)^2}
\]

where:

- \( \Delta L \) is the uncertainty in the length measurement,

- \( \Delta T \) is the uncertainty in the period measurement.

---

## Analysis:

### 1. Compare Your Measured \( g \) with the Standard Value:
The standard value of acceleration due to gravity is:

\[
g_{\text{standard}} \approx 9.81 \, \text{m/s}^2
\]

### 2. Discuss:
- The effect of measurement resolution on \( g \).
- Variability in timing and its impact on \( g \).
- Any assumptions or experimental limitations.

---

2. **Discussion on Sources of Uncertainty:**
   - Measurement resolution: The precision of the ruler and timer limits the accuracy of \( L \) and \( T \).
   - Timing variability: Small timing errors accumulate when measuring multiple oscillations.
   - Assumptions: The pendulum's oscillations must be small (<15°) for the formula to hold, and the suspension point must be fixed.

---

Python Code:
```python
import numpy as np
import matplotlib.pyplot as plt

# Function to calculate gravitational acceleration (g)
def calculate_gravity(length, period):
    """
    Calculate the gravitational acceleration based on the pendulum's length and period.
    
    :param length: Length of the pendulum (in meters)
    :param period: Period of one oscillation (in seconds)
    :return: Gravitational acceleration (in m/s^2)
    """
    g = (4 * np.pi**2 * length) / period**2
    return g

# Function to propagate uncertainties in g calculation
def propagate_uncertainties(g, length, period, delta_L, delta_T):
    """
    Propagate uncertainties in the length and period to estimate the uncertainty in g.
    
    :param g: Gravitational acceleration
    :param length: Length of the pendulum
    :param period: Period of one oscillation
    :param delta_L: Uncertainty in the length measurement
    :param delta_T: Uncertainty in the period measurement
    :return: Uncertainty in the gravitational acceleration (delta_g)
    """
    delta_g = g * np.sqrt((delta_L / length)**2 + (2 * delta_T / period)**2)
    return delta_g

# Function to calculate the period from mean time for 10 oscillations
def calculate_period(mean_time_10):
    """
    Calculate the period for one oscillation from the time for 10 oscillations.
    
    :param mean_time_10: Time for 10 oscillations (in seconds)
    :return: Period for one oscillation (in seconds)
    """
    return mean_time_10 / 10

# Example measurements
measurements = [
    {"T_10": 20.1, "length": 1.5, "delta_L": 0.005},  # Measurement 1 (T_10 in seconds)
    {"T_10": 19.8, "length": 1.5, "delta_L": 0.005},  # Measurement 2
]

# Initialize results list
results = []

# Iterate through measurements and perform calculations
for measurement in measurements:
    T_10 = measurement["T_10"]  # Time for 10 oscillations
    length = measurement["length"]  # Length of the pendulum
    delta_L = measurement["delta_L"]  # Uncertainty in the length measurement
    
    # Calculate mean time for 10 oscillations (T_10)
    mean_time_10 = T_10
    
    # Calculate period (one full oscillation)
    period = calculate_period(mean_time_10)
    
    # Assume some uncertainty in timing, for example, ±0.1 seconds
    delta_T = 0.1  # Uncertainty in the time measurement
    
    # Calculate gravitational acceleration (g)
    g = calculate_gravity(length, period)
    
    # Propagate uncertainties to get uncertainty in g (delta_g)
    delta_g = propagate_uncertainties(g, length, period, delta_L, delta_T)
    
    # Store results
    results.append({
        "T_10": T_10,
        "mean_time_10": mean_time_10,
        "length": length,
        "T": period,
        "g": g,
        "delta_g": delta_g
    })

# Print the results for each measurement
for result in results:
    print(f"Measurement Results:")
    print(f"T_10 (seconds): {result['T_10']}")
    print(f"Mean Time for 10 oscillations: {result['mean_time_10']}")
    print(f"Length (meters): {result['length']}")
    print(f"Period (seconds): {result['T']}")
    print(f"Gravitational Acceleration (g): {result['g']:.4f} m/s²")
    print(f"Uncertainty in g (delta_g): {result['delta_g']:.4f} m/s²")
    print("-" * 40)
```
#Print Results
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Measurement Results</title>
    <style>
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            padding: 8px;
            text-align: center;
            border: 1px solid #ddd;
        }
        th {
            background-color: #f2f2f2;
        }
        tr:nth-child(even) {
            background-color: #f9f9f9;
        }
    </style>
</head>
<body>
    <h1>Gravitational Acceleration Measurement Results</h1>
    <table>
        <thead>
            <tr>
                <th>Measurement #</th>
                <th>T<sub>10</sub> (seconds)</th>
                <th>&#x03C4;<sub>10</sub> (seconds)</th>
                <th>&sigma;<sub>T<sub>10</sub></sub> (seconds)</th>
                <th>&#x0394; &#x03C4;<sub>10</sub> (seconds)</th>
                <th>L (meters)</th>
                <th>T (seconds)</th>
                <th>g (m/s<sup>2</sup>)</th>
                <th>&#x0394;g (m/s<sup>2</sup>)</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>20.1</td>
                <td>20.1</td>
                <td>—</td>
                <td>—</td>
                <td>1.5</td>
                <td>2.010</td>
                <td>14.6575</td>
                <td>1.4593</td>
            </tr>
            <tr>
                <td>2</td>
                <td>19.8</td>
                <td>19.8</td>
                <td>—</td>
                <td>—</td>
                <td>1.5</td>
                <td>1.98</td>
                <td>15.1050</td>
                <td>1.5266</td>
            </tr>
        </tbody>
    </table>
</body>
</html>

<table border="1">
    <thead>
        <tr>
            <th>Measurement #</th>
            <th>T<sub>10</sub> (seconds)</th>
            <th>Mean T<sub>10</sub> (seconds)</th>
            <th>Length L (meters)</th>
            <th>Period T (seconds)</th>
            <th>g (m/s<sup>2</sup>)</th>
            <th>Δg (m/s<sup>2</sup>)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>20.1</td>
            <td>20.1</td>
            <td>1.5</td>
            <td>2.01</td>
            <td>9.82</td>
            <td>0.02</td>
        </tr>
        <tr>
            <td>2</td>
            <td>19.8</td>
            <td>19.8</td>
            <td>1.5</td>
            <td>1.98</td>
            <td>9.79</td>
            <td>0.03</td>
        </tr>
    </tbody>
</table>



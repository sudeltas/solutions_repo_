# Problem 1

# Equivalent Resistance Using Graph Theory

## Motivation

Calculating the equivalent resistance of electrical circuits is essential for understanding and designing efficient systems. While traditional methods, such as applying series and parallel resistor rules, work well for simple circuits, they become cumbersome for complex ones. Graph theory offers a more systematic and algorithmic approach to analyze circuits. By representing the circuit as a graph where:

- **Nodes** correspond to junctions,
- **Edges** represent resistors with weights equal to their resistance values,

we can simplify even the most intricate circuits step by step. This method is particularly useful for circuit simulation software and optimization problems. It also highlights the connection between electrical circuits and mathematical concepts like graph theory.

---

## Task Description

### Option 1: Simplified Algorithm Description

#### Steps for Calculating Equivalent Resistance Using Graph Theory

1. **Graph Representation**:
   - Represent the circuit as a graph \( G = (V, E) \), where:
     - \( V \) are the vertices (junctions),
     - \( E \) are the edges (resistors), each with a resistance value \( R_{ij} \).

2. **Identifying Series and Parallel Connections**:
   - **Series Connection**: When resistors are in series, the total resistance is given by:
     \[
     R_{\text{eq}} = R_1 + R_2 + \dots + R_n
     \]
   - **Parallel Connection**: When resistors are in parallel, the total resistance is:
     \[
     \frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2} + \dots + \frac{1}{R_n}
     \]

3. **Iterative Reduction**:
   - Identify series and parallel resistor connections in the graph.
   - Replace series resistors with their equivalent resistance and remove parallel resistors, simplifying the graph.
   - Repeat until the graph is reduced to a single equivalent resistance.

4. **Handling Nested Configurations**:
   - In cases of nested series or parallel resistors, apply the reduction rules recursively to simplify the subgraphs.

---

### Example of Series and Parallel Combinations

#### **Example 1: Simple Series Circuit**

Consider a simple series circuit with three resistors:

---[R1]---[R2]---[R3]---

The total equivalent resistance for series resistors is the sum of their resistances:

\[
R_{\text{eq}} = R_1 + R_2 + R_3
\]

| Resistor | Value (Ω) |
|----------|-----------|
| \( R_1 \)  | 10        |
| \( R_2 \)  | 20        |
| \( R_3 \)  | 30        |

Thus, the total resistance is:

\[
R_{\text{eq}} = 10 + 20 + 30 = 60 \, \Omega
\]

#### **Example 2: Simple Parallel Circuit**

Consider a parallel circuit:


The equivalent resistance for resistors in parallel is calculated as:

\[
\frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2} + \frac{1}{R_3}
\]
<table border="1">
  <tr>
    <th>Resistor</th>
    <th>Value (Ω)</th>
  </tr>
  <tr>
    <td>R<sub>1</sub></td>
    <td>10</td>
  </tr>
  <tr>
    <td>R<sub>2</sub></td>
    <td>20</td>
  </tr>
  <tr>
    <td>R<sub>3</sub></td>
    <td>30</td>
  </tr>
</table>

Thus, the equivalent resistance is:

\[
\frac{1}{R_{\text{eq}}} = \frac{1}{10} + \frac{1}{20} + \frac{1}{30} = 0.3833 \, \text{S}
\]

\[
R_{\text{eq}} = \frac{1}{0.3833} \approx 2.61 \, \Omega
\]

---
#### **Example 2: Simple Parallel Circuit**

Consider a parallel circuit:

    ---[R1]---
   |          |
   |         [R2]
   |          |
   |         [R3]
   |          |
   -------------

```python
import numpy as np
import matplotlib.pyplot as plt
# Function to calculate equivalent resistance in series
def equivalent_resistance_series(resistances):
    return sum(resistances)

# Function to calculate equivalent resistance in parallel
def equivalent_resistance_parallel(resistances):
    # Reciprocal of the equivalent resistance in parallel is the sum of reciprocals
    reciprocal_sum = sum(1 / r for r in resistances)
    if reciprocal_sum == 0:
        return float('inf')  # Handle case when all resistances are infinite
    return 1 / reciprocal_sum

# Example 1: Simple Series Circuit
resistors_series = [10, 20, 30]  # Example resistances in Ohms for series circuit
R_eq_series = equivalent_resistance_series(resistors_series)
print(f"Equivalent Resistance for Series Circuit: {R_eq_series} Ohms")

# Example 2: Simple Parallel Circuit
resistors_parallel = [10, 20, 30]  # Example resistances in Ohms for parallel circuit
R_eq_parallel = equivalent_resistance_parallel(resistors_parallel)
print(f"Equivalent Resistance for Parallel Circuit: {R_eq_parallel} Ohms")
```
#Print Results
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Equivalent Resistance Results</title>
    <style>
        table {
            width: 50%;
            margin: 20px auto;
            border-collapse: collapse;
            text-align: center;
        }
        table, th, td {
            border: 1px solid black;
        }
        th, td {
            padding: 10px;
        }
        th {
            background-color: #f2f2f2;
        }
        caption {
            font-size: 1.5em;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

    <table>
        <caption>Equivalent Resistance Calculation Results</caption>
        <thead>
            <tr>
                <th>Configuration</th>
                <th>Equivalent Resistance (Ω)</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Series Circuit</td>
                <td>60 Ω</td>
            </tr>
            <tr>
                <td>Parallel Circuit</td>
                <td>5.46 Ω</td>
            </tr>
        </tbody>
    </table>

</body>
</html>


#Conclusion
Using graph theory to calculate equivalent resistance provides a powerful method to simplify complex circuits. By representing the circuit as a graph and iteratively reducing series and parallel connections, we can compute the equivalent resistance efficiently, even for complicated networks.

The Python code presented can be expanded to handle nested series and parallel connections, multiple loops, and cycles. This approach is beneficial for automated analysis and optimization in circuit design and simulation software.

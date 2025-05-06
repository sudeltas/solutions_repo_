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
      ---[R1]---+---[R2]---
                  |
                  |
                 [R3]
                  |
                 ---
```python
import numpy as np
import matplotlib.pyplot as plt
import networkx as nx

def add_resistor(graph, node1, node2, resistance):
    graph.add_edge(node1, node2, weight=resistance)

def equivalent_resistance(graph, start, end):
    # Apply graph traversal (e.g., DFS or BFS) to calculate the equivalent resistance
    pass  # Implement algorithm logic for reducing series and parallel resistors

# Example: Simple Series Circuit
G = nx.Graph()
add_resistor(G, 'A', 'B', 10)  # R1 = 10 Ohm
add_resistor(G, 'B', 'C', 20)  # R2 = 20 Ohm
add_resistor(G, 'C', 'D', 30)  # R3 = 30 Ohm

# Calculate the equivalent resistance for a series circuit
R_eq = equivalent_resistance(G, 'A', 'D')
print("Equivalent Resistance: ", R_eq)

# Example: Simple Parallel Circuit
G2 = nx.Graph()
add_resistor(G2, 'A', 'B', 10)  # R1 = 10 Ohm
add_resistor(G2, 'B', 'C', 20)  # R2 = 20 Ohm
add_resistor(G2, 'C', 'A', 30)  # R3 = 30 Ohm

# Calculate the equivalent resistance for a parallel circuit
R_eq_parallel = equivalent_resistance(G2, 'A', 'C')
print("Equivalent Resistance for Parallel Circuit: ", R_eq_parallel)
```

#Conclusion
Using graph theory to calculate equivalent resistance provides a powerful method to simplify complex circuits. By representing the circuit as a graph and iteratively reducing series and parallel connections, we can compute the equivalent resistance efficiently, even for complicated networks.

The Python code presented can be expanded to handle nested series and parallel connections, multiple loops, and cycles. This approach is beneficial for automated analysis and optimization in circuit design and simulation software.

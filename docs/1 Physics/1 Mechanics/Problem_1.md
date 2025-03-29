# Problem 1
Investigating the Range as a Function of the Angle of Projection
Motivation:
Projectile motion offers an ideal context to explore fundamental principles of physics, blending theoretical rigor with practical relevance. Whether it’s the trajectory of a soccer ball or the launch of a rocket, understanding how the range of a projectile depends on the angle of projection provides a deep insight into how we model motion under gravity.

In this task, we will explore the relationship between the range of a projectile and the angle at which it is launched. While this is often a simple problem in introductory physics, it touches on a range of deeper principles—especially when we account for varying initial conditions such as velocity, height, and gravitational acceleration.

1. Theoretical Foundation
To begin, we need to derive the governing equations for projectile motion. Let's start by establishing the general form of the motion based on Newton’s laws.

Equations of Motion:
In projectile motion, we treat the horizontal and vertical motions separately, as they are independent of each other (with the horizontal motion having no acceleration in ideal conditions).

Horizontal motion (x-direction):

𝑥
(
𝑡
)
=
𝑣
0
cos
⁡
(
𝜃
)
⋅
𝑡
x(t)=v 
0
​
 cos(θ)⋅t
where:

𝑣
0
v 
0
​
  is the initial velocity,

𝜃
θ is the angle of projection,

𝑡
t is the time,

cos
⁡
(
𝜃
)
cos(θ) is the horizontal component of the initial velocity.

Vertical motion (y-direction):

𝑦
(
𝑡
)
=
𝑣
0
sin
⁡
(
𝜃
)
⋅
𝑡
−
1
2
𝑔
𝑡
2
y(t)=v 
0
​
 sin(θ)⋅t− 
2
1
​
 gt 
2
 
where:

𝑔
g is the acceleration due to gravity,

𝑣
0
sin
⁡
(
𝜃
)
v 
0
​
 sin(θ) is the vertical component of the initial velocity.

The point where the projectile returns to the ground occurs when 
𝑦
(
𝑡
)
=
0
y(t)=0, so we can solve for the time of flight, 
𝑇
T.

Time of Flight:
Set 
𝑦
(
𝑡
)
=
0
y(t)=0 for the point where the projectile hits the ground:

0
=
𝑣
0
sin
⁡
(
𝜃
)
⋅
𝑇
−
1
2
𝑔
𝑇
2
0=v 
0
​
 sin(θ)⋅T− 
2
1
​
 gT 
2
 
Factoring out 
𝑇
T:

𝑇
(
𝑣
0
sin
⁡
(
𝜃
)
−
1
2
𝑔
𝑇
)
=
0
T(v 
0
​
 sin(θ)− 
2
1
​
 gT)=0
This gives the time of flight:

𝑇
=
2
𝑣
0
sin
⁡
(
𝜃
)
𝑔
T= 
g
2v 
0
​
 sin(θ)
​
 
Horizontal Range (R):
The horizontal range 
𝑅
R is the horizontal distance the projectile travels before it hits the ground. Using the time of flight, we can find 
𝑅
R:

𝑅
=
𝑥
(
𝑇
)
=
𝑣
0
cos
⁡
(
𝜃
)
⋅
𝑇
=
𝑣
0
cos
⁡
(
𝜃
)
⋅
2
𝑣
0
sin
⁡
(
𝜃
)
𝑔
R=x(T)=v 
0
​
 cos(θ)⋅T=v 
0
​
 cos(θ)⋅ 
g
2v 
0
​
 sin(θ)
​
 
Simplifying:

𝑅
=
𝑣
0
2
sin
⁡
(
2
𝜃
)
𝑔
R= 
g
v 
0
2
​
 sin(2θ)
​
 
This equation describes the range as a function of the angle of projection 
𝜃
θ, the initial velocity 
𝑣
0
v 
0
​
 , and gravitational acceleration 
𝑔
g.

2. Analysis of the Range
Now that we have the expression for the range 
𝑅
R, let’s analyze how it depends on various factors:

Range as a function of the angle 
𝜃
θ:

𝑅
(
𝜃
)
=
𝑣
0
2
sin
⁡
(
2
𝜃
)
𝑔
R(θ)= 
g
v 
0
2
​
 sin(2θ)
​
 
The range reaches its maximum when 
sin
⁡
(
2
𝜃
)
sin(2θ) is maximized, which occurs at 
𝜃
=
45
∘
θ=45 
∘
 .

For angles less than 
45
∘
45 
∘
 , the range increases as 
𝜃
θ approaches 
45
∘
45 
∘
 , after which it decreases.

Effect of initial velocity 
𝑣
0
v 
0
​
 :

The range is directly proportional to the square of the initial velocity. A higher initial velocity leads to a greater range.

Effect of gravitational acceleration 
𝑔
g:

The range is inversely proportional to the gravitational acceleration. On the Moon, where 
𝑔
g is weaker, the range would be much greater than on Earth, for the same initial velocity and launch angle.

3. Practical Applications
This theoretical model can be adapted to real-world situations with modifications for factors such as:

Launch height: If the projectile is launched from a height, the time of flight will be longer, affecting the range.

Air resistance: For objects moving through the atmosphere, drag must be taken into account. The range is no longer a simple function of 
sin
⁡
(
2
𝜃
)
sin(2θ), and numerical methods or simulations must be used to model the trajectory.

Uneven terrain: If the projectile lands on sloped terrain, the range calculation becomes more complex, requiring consideration of the terrain’s angle and the projectile's trajectory.

4. Implementation
Now, let's simulate projectile motion and visualize the range as a function of the angle of projection using Python. The following code simulates the projectile motion for different launch angles and initial velocities.

Python Code (Simulation of Projectile Motion):
python
Kopyala
import numpy as np
import matplotlib.pyplot as plt

def projectile_motion(v0, angle, g=9.81):
    # Time of flight
    T = 2 * v0 * np.sin(np.radians(angle)) / g
    # Time intervals
    t = np.linspace(0, T, num=500)
    # Horizontal and vertical motion equations
    x = v0 * np.cos(np.radians(angle)) * t
    y = v0 * np.sin(np.radians(angle)) * t - 0.5 * g * t**2
    return x, y, T

def plot_range_vs_angle(v0, g=9.81):
    angles = np.linspace(0, 90, 91)
    ranges = []
    
    for angle in angles:
        x, y, T = projectile_motion(v0, angle, g)
        ranges.append(x[-1])  # Horizontal range is the last x value
    
    plt.figure(figsize=(8, 6))
    plt.plot(angles, ranges, label=f"v0 = {v0} m/s")
    plt.title("Range vs. Angle of Projection")
    plt.xlabel("Angle of Projection (degrees)")
    plt.ylabel("Range (m)")
    plt.grid(True)
    plt.legend()
    plt.show()

# Example usage
v0 = 20  # Initial velocity in m/s
plot_range_vs_angle(v0)
Explanation:
projectile_motion(v0, angle, g): This function calculates the trajectory of the projectile for a given initial velocity, launch angle, and gravitational acceleration.

plot_range_vs_angle(v0): This function computes the range for a range of launch angles and then plots the relationship between angle and range.

5. Limitations of the Idealized Model
While the model presented is elegant and useful for many scenarios, there are several limitations:

Air resistance: In reality, drag slows down projectiles, altering their trajectory. This can be modeled using differential equations, but it requires numerical solutions.

Wind: Wind can significantly alter the trajectory, especially at higher speeds.

Launch height: We assumed the projectile was launched from the ground level. If launched from a height, the projectile would follow a different path, and the range could be extended or reduced.

Earth’s curvature: Over long distances, the curvature of the Earth could influence the projectile's path, although this is negligible for most practical scenarios.

Conclusion
Through this investigation, we derived the governing equations for projectile motion, analyzed how the range depends on the launch angle, and implemented a computational tool to simulate the motion. This model, while idealized, provides valuable insight into real-world projectile motion problems, which can be further refined by incorporating more realistic factors like air resistance or wind.


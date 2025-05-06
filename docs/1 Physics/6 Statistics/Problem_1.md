# Problem 1
📘 Exploring the Central Limit Theorem through Simulations
🎯 Motivation
The Central Limit Theorem (CLT) is one of the foundational results in probability theory. It states:
If \( X_1, X_2, \dots, X_n \) are i.i.d. with mean \( \mu \) and variance \( \sigma^2 \), then as \( n \to \infty \):

\[
\frac{\bar{X}_n - \mu}{\sigma / \sqrt{n}} \xrightarrow{d} \mathcal{N}(0, 1)
\]
In simpler terms, regardless of the shape of the original distribution, the sampling distribution of the sample mean becomes approximately normal if the sample size is large enough.

🧪 1. Population Distribution: Exponential, Uniform, and Binomial
We will use three distinct distributions:

Exponential Distribution (skewed)

Uniform Distribution (flat)

Binomial Distribution (discrete)
```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# For reproducibility
np.random.seed(42)

# Define populations
population_size = 100_000
exp_pop = np.random.exponential(scale=2.0, size=population_size)
uni_pop = np.random.uniform(low=0, high=10, size=population_size)
binom_pop = np.random.binomial(n=10, p=0.5, size=population_size)
📊 2. Sampling and Visualization of Sample Means
We will take repeated samples and compute sample means for different sample sizes 
𝑛=5,30,50 Then we will plot histograms to observe convergence to normal distribution.
def simulate_sample_means(population, sample_size=30, num_samples=1000):
    means = []
    for _ in range(num_samples):
        sample = np.random.choice(population, size=sample_size)
        means.append(np.mean(sample))
    return means
📈 3. Visualization: Sampling Distribution
Let’s plot sample mean distributions from the exponential population:
sample_sizes = [5, 30, 50]
populations = {'Exponential': exp_pop, 'Uniform': uni_pop, 'Binomial': binom_pop}

for name, pop in populations.items():
    plt.figure(figsize=(15, 4))
    for i, n in enumerate(sample_sizes, 1):
        sample_means = simulate_sample_means(pop, sample_size=n)
        plt.subplot(1, 3, i)
        sns.histplot(sample_means, kde=True, color='tomato', stat='density')
        plt.title(f"{name} Dist. Sample Size = {n}")
        plt.xlabel("Sample Mean")
    plt.suptitle(f"{name} Population - Sampling Distribution of Means", fontsize=16)
    plt.tight_layout()
    plt.show()
📐 4. Mathematical Justification
Let’s recall the formulas:

Mean of sample means remains the same:
\[
\mathbb{E}[\bar{X}] = \mu
\]

\[
\text{Var}(\bar{X}) = \frac{\sigma^2}{n}
\]

As sample size 𝑛 increases, the spread (standard deviation) of the sample mean decreases, leading to a more concentrated (and normal) distribution.

🔍 5. Parameter Exploration Table
Below is a table showing sample standard deviations (spread) of sample means for different distributions and sample sizes.

from IPython.display import display, HTML

def sample_mean_std(pop, sizes):
    rows = []
    for n in sizes:
        sample_means = simulate_sample_means(pop, sample_size=n)
        rows.append(f"<tr><td>{n}</td><td>{np.std(sample_means):.4f}</td>")
    return rows

sizes = [5, 30, 50]
html = """
<table border="1">
<tr>
<th>Sample Size</th>
<th>Exponential STD</th>
<th>Uniform STD</th>
<th>Binomial STD</th>
</tr>
"""

for i in sizes:
    exp_std = np.std(simulate_sample_means(exp_pop, i))
    uni_std = np.std(simulate_sample_means(uni_pop, i))
    bin_std = np.std(simulate_sample_means(binom_pop, i))
    html += f"<tr><td>{i}</td><td>{exp_std:.4f}</td><td>{uni_std:.4f}</td><td>{bin_std:.4f}</td></tr>"

html += "</table>"

display(HTML(html))
🧠 6. Real-World Applications
Manufacturing Quality Control: Averages of product dimensions are monitored, not single units.

Finance: Portfolio average returns across time intervals.

Medicine: Average blood pressure from repeated clinical trials.

📦 7. Summary
The Central Limit Theorem ensures that the distribution of sample means becomes approximately normal as 
𝑛
→
∞
n→∞, regardless of population shape.

This is confirmed through simulation across exponential, uniform, and binomial distributions.

CLT allows us to apply powerful inference tools (like z-tests) even with non-normal data — as long as the sample size is large enough.


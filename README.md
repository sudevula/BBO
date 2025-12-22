# Imperial College Professional Certification in AI & ML  
## Black-Box Optimisation (BBO) Capstone Project

---

## 1. Project Overview

This capstone project focuses on **Black-Box Optimisation (BBO)**, where the goal is to optimise a set of unknown functions using a limited number of queries or evaluations. Each function represents a real-world scenario in which evaluating outcomes is expensive and slow, making brute-force search impractical.

The overall objective is to select input queries that maximise function outputs over time, using machine learning techniques to guide decision-making under uncertainty. This closely reflects real-world ML problems such as hyperparameter tuning, financial modelling, and scientific discovery.

This project is particularly relevant to my career interests as it develops skills in probabilistic modelling, optimisation under constraints, and iterative decision-making, which are highly applicable to data science, machine learning, and quantitative roles.

---

## 2. Inputs and Outputs

Each black-box function accepts a vector of continuous input values.

**Inputs**
- Real-valued vectors in **[0, 1]^d**
- Dimensionality **d ranges from 2 to 8**, depending on the function
- Each query must follow a strict format

Example inputs from Round 3:

Function 1: [0.810000, 0.730000]
Function 2: [0.620000, 0.820000]
Function 3: [0.700000, 0.850000, 0.200000]
Function 4: [0.410000, 0.400000, 0.370000, 0.450000]
Function 5: [0.950000, 0.080000, 0.820000, 0.950000]
Function 6: [0.520000, 0.150000, 0.600000, 0.880000, 0.050000]
Function 7: [0.030000, 0.200000, 0.300000, 0.200000, 0.420000, 0.700000]
Function 8: [0.400000, 0.080000, 0.380000, 0.050000, 0.780000, 0.080000, 0.090000, 0.050000]


**Outputs**
- A single scalar value returned by the black-box function
- Represents a performance signal such as yield, score, or efficiency
- Higher values are better, as all tasks are framed as maximisation problems

Example outputs from Round 3:

Function 1: -6.315914050868028e-31
Function 2: 0.1551709649428233
Function 3: -0.14601911938969364
Function 4: -0.03231027880219939
Function 5: 1820.0386226597477
Function 6: -0.5790954443054444
Function 7: 2.081316196964551
Function 8: 9.38655

---

## 3. Challenge Objectives

The objective of this project is to maximise each of the eight unknown functions over a fixed number of weekly queries.

Key constraints include:
- A strict limit of one query per function per week
- No access to the true function form or gradients
- Outputs may be noisy, non-linear, and multi-modal

This requires carefully balancing:
- Exploration (learning about unknown regions)
- Exploitation (refining high-performing areas)

---

## 4. Technical Approach

Early Iterations (Weeks 1–2)

In the initial rounds, I focused on exploration-heavy strategies, using:
- Gaussian Process (GP) surrogate models
- Acquisition functions such as Upper Confidence Bound (UCB)

This allowed me to model both predicted performance and uncertainty, helping avoid premature convergence to sub-optimal local maxima.

Later Iterations (Week 3 onwards)

As more data became available, I refined the approach by:
- Gradually adjusting exploration parameters toward exploitation
- Comparing acquisition behaviour across functions
- Introducing SVM-based thinking, framing the problem as separating high- vs low-performing regions rather than predicting exact outputs

Soft-margin SVMs are particularly useful in this setting, as outputs are noisy and imperfect.  
Kernel SVMs also help capture non-linear boundaries in higher-dimensional functions.

Overall, my approach combines Bayesian optimisation, surrogate modelling, and classification-based intuition, evolving as more data is collected.

## 5. Results So Far

After three rounds of queries, the results suggest that the optimisation process is beginning to stabilise in several functions, while others still benefit from exploration.

- Lower-dimensional functions (especially Functions 1, 2, and 4) show diminishing returns from repeated queries in similar regions, suggesting proximity to flat or near-optimal areas.
- Higher-dimensional functions (Functions 5–8) remain more variable.  
  - Function 5 continues to produce large outputs with noticeable fluctuations, indicating a complex surface with multiple local optima.
  - Functions 7 and 8 consistently return relatively high values, suggesting the strategy is successfully identifying strong-performing regions, even though the global optimum remains uncertain.

Overall, these results validate the use of Gaussian Process–based Bayesian optimisation with uncertainty-aware acquisition functions, while also highlighting the growing importance of:
- Controlling exploration as the dataset expands
- Considering alternative perspectives, such as classification-based models (SVMs), to efficiently distinguish high- and low-performing regions.

- Controlling exploration as the dataset expands
- Considering alternative perspectives, such as **classification-based models (SVMs)**, to efficiently distinguish high- and low-performing regions.

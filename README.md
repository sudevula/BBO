# Imperial College Professional Certification in AI & ML  
## Black-Box Optimisation (BBO) Capstone Project

---

## 1. Project Overview 

This capstone project focuses on **Black-Box Optimisation (BBO)**, where the objective is to maximise a set of unknown functions under strict evaluation constraints. Each function represents a real-world scenario in which evaluating outcomes is expensive and slow, making brute-force search impractical. Each function also represents a scenario where:

The underlying mathematical form is hidden
Gradients are unavailable
Evaluations are expensive and limited

Only one query per function per week was permitted, creating a sequential decision-making problem under uncertainty.

The overall objective is to select input queries that maximise function outputs over time, using machine learning techniques to guide decision-making under uncertainty. This mirrors real-world challenges such as:

- Hyperparameter tuning
- Financial risk optimisation
- Experimental design
- Scientific discovery

Over the full competition, I refined an adaptive optimisation strategy across 13 rounds and achieved 1st place on Function 3, along with competitive performance across multiple other functions

## 2. Datasheet and Model Card
Documentation for reproducibility and transparency:

Datasheet.Md — Documents the BBO capstone dataset: motivation, composition, collection process, preprocessing, intended/inappropriate uses, and distribution/maintenance.

Modelcard.md — Describes the optimisation approach: overview, intended use, strategy across the ten rounds, performance summary, assumptions and limitations, and ethical considerations.

## 3. Inputs and Outputs

Each black-box function accepts a vector of continuous input values.

**Inputs**
- Real-valued vectors in **[0, 1]^d**
- Dimensionality **d ranges from 2 to 8**, depending on the function
- Each query must follow a strict format

Example inputs from Round 3:

- **Function 1:** `[0.810000, 0.730000]`  
- **Function 2:** `[0.620000, 0.820000]`  
- **Function 3:** `[0.700000, 0.850000, 0.200000]`  
- **Function 4:** `[0.410000, 0.400000, 0.370000, 0.450000]`  
- **Function 5:** `[0.950000, 0.080000, 0.820000, 0.950000]`  
- **Function 6:** `[0.520000, 0.150000, 0.600000, 0.880000, 0.050000]`  
- **Function 7:** `[0.030000, 0.200000, 0.300000, 0.200000, 0.420000, 0.700000]`  
- **Function 8:** `[0.400000, 0.080000, 0.380000, 0.050000, 0.780000, 0.080000, 0.090000, 0.050000]`  


**Outputs**
- A single scalar value returned by the black-box function
- Represents a performance signal such as yield, score, or efficiency
- Higher values are better, as all tasks are framed as maximisation problems

Example outputs from Round 3:

- **Function 1:** `-6.315914050868028e-31`  
- **Function 2:** `0.1551709649428233`  
- **Function 3:** `-0.14601911938969364`  
- **Function 4:** `-0.03231027880219939`  
- **Function 5:** `1820.0386226597477`  
- **Function 6:** `-0.5790954443054444`  
- **Function 7:** `2.081316196964551`  
- **Function 8:** `9.38655` 

## 4. Challenge Objectives

The objective of this project is to maximise each of the eight unknown functions over a fixed number of weekly queries.

Key constraints include:
- A strict limit of one query per function per week
- No access to the true function form or gradients
- Outputs may be noisy, non-linear, and multi-modal

This requires carefully balancing:
- Exploration (learning about unknown regions)
- Exploitation (refining high-performing areas)

The challenge naturally reflects the exploration–exploitation trade-off studied in Bayesian optimisation and reinforcement learning.


## 5. Technical Approach 

**Early Iterations (Weeks 1–3)**

Early Phase (Weeks 1–3): Exploration-Focused Bayesian Optimisation

In early rounds, I prioritised uncertainty-aware modelling using:

Gaussian Process (GP) surrogate models
Upper Confidence Bound (UCB) acquisition

GPs allowed modelling both predicted mean and uncertainty.
UCB enabled structured exploration while avoiding premature convergence.

At this stage, the objective was to learn the shape of each function rather than aggressively exploit early local maxima.

**Middle Phase (Weeks 4–9): Adaptive Refinement**

As the dataset expanded:

- Exploration parameters were gradually reduced
- High-performing basins were refined via local search
- Grid-based and structured proposals were introduced in promising regions
- Function-specific behaviour began guiding strategy

Importantly, I began treating each function differently rather than applying a uniform global policy.

Key adjustments included:

- Local grid refinement around strong basins
- Reduced acquisition variance in stabilised functions
- Increased exploration for ambiguous or flat functions

**Late Phase (Weeks 10–13): Structured Exploitation & Stability**

In the final rounds, the strategy became more disciplined:

- Aggressive exploitation in stable high-performing basins
- Minimal-risk perturbations around strong regions
- Reduced variance in candidate proposals
- Controlled convergence

For Function 3, this structured refinement strategy proved highly effective, leading to top performance in the leaderboard.

## 6. Results Summary

After thirteen rounds of queries, the results were mixed-bag
- first place in function 3
- strong placement for functions 1 and 2
- competitive results across multiple additional functions

Observations- 
- Lower-dimensional functions (especially Functions 1, 2, and 3) stablised relatively quickly
- Higher-dimensional functions (Functions 5–8) remained more variable and required longer exploration phases.  
  - Function 5 continued to produce large output till the end with noticeable fluctuations in the beginning with a sudden spike and then diminishing returns in the later phases.

Overall, these results validate the use of Gaussian Process–based Bayesian optimisation with uncertainty-aware acquisition functions, while also highlighting the growing importance of:
- Controlling exploration as the dataset expands
- Considering alternative perspectives, such as classification-based models (SVMs), to efficiently distinguish high- and low-performing regions.

## 8. Broader ML Relevance

This capstone project demonstrates core machine learning principles:

- Bayesian optimisation
- Sequential decision-making
- Exploration–exploitation trade-offs
- Surrogate modelling under uncertainty
- Adaptive hyperparameter control

These skills directly translate to:

- Hyperparameter tuning in deep learning
- Automated ML systems
- Risk modelling
- Financial optimisation
- Experimental design in research

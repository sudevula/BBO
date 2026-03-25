
# 🧠 Model Card: BBO Optimisation Strategy (Final)

## Overview

**Model Title:** Adaptive Sequential Optimisation Framework for Black-Box Functions  
**Version:** Final  
**Author:** Sundari Devulapalle
**Date:** March 2026  
**Model Type:** Human-guided, Bayesian-inspired sequential optimisation framework  
**Presentation:** Not a standalone predictive model, but a documented decision framework combining exploratory and exploitative strategies inspired by Bayesian optimisation principles.

This Model Card documents the  optimisation strategy developed for the Black-Box Optimisation (BBO) Capstone Project at Imperial College, detailing its objectives, methodology, performance characteristics, assumptions, limitations, and ethical considerations.

The framework was applied across **13 sequential rounds** on **eight independent black-box functions** under strict query constraints (one evaluation per function per week).

The optimisation process combined Bayesian principles, structured refinement, adaptive exploration control, and function-specific reasoning.

---

### 🏆 Final Outcomes

- 🥇 **1st Place – Function 3**
- 🥈 Strong performance – Function 1
- Competitive performance across multiple additional functions

---

## Intended Use

### Primary Use Cases

This optimisation strategy is designed to:

- Guide sequential queries in black-box function optimisation when the objective is unknown.
- Demonstrate interpretable decision processes in optimisation under strict query counts / budgets.
- Support educational and research experiments on exploration vs exploitation trade-offs.
- Provide an interpretable workflow suitable for capstone evaluation and academic review.

### Out-of-Scope Use Cases

This strategy is **not recommended for**:

- Fully automated optimisation in production systems.
- Real-time decision systems without human oversight.
- Safety-critical domains without formal guarantees.
- High-dimensional problems outside small query budgets.

This strategy is best applied to structured experimentation environments where interpretability and iterative reasoning are priorities.

---

## Strategy Description

The optimisation strategy was developed over thirteen rounds of iterative queries across eight independent black-box functions. The overall methodology can be summarised as:

1. **Exploration Phase (Rounds 1–3):**  
   Broad sampling across the input domain to identify preliminary areas of interest. The initial phase was grounded in Bayesian optimisation principles. I applied Gaussian Process-style reasoning, prioritising:

  - Broad exploration of the input domain
  - Sampling uncertain regions
  - Avoiding premature convergence

  At this stage, the focus was on information gathering rather than immediate performance maximisation. The objective was to approximate the global landscape under strict query constraints.


2. **Hybrid Exploration & Exploitation Phase (Rounds 4–9):**  
   A mix of exploration and local refinement informed by observed performance trends. Local decisions were influenced by patterns such as boundary improvement or local signal stability.

Key developments:

- Structured local refinement around high-performing regions
- Reduced step sizes near strong basins
- Increased exploration in ambiguous or flat functions
- Feature sensitivity reasoning to detect influential dimensions
- Boundary-focused exploitation (notably effective for Function 5)
- Directional perturbation to assess local response behaviour

Each function was treated independently, recognising that different landscapes required different optimisation dynamics.

3. **Exploitation Phase (Rounds 10–13):**  
   In this phase, I focused refinement in regions with historically strong outputs. Step sizes were reduced and perturbations were conservative to avoid destabilising previously promising regions.  Decisions were documented to ensure interpretability and reproducibility. The strategy became less about aggressive optimisation and more about transparent reasoning under uncertainty.

This structured refinement was particularly effective for **Function 3**, leading to first place on the leaderboard.

Across thirteen rounds, the strategy evolved from:

> Probabilistic exploration → structured refinement → research-informed reasoning → hyperparameter tuning logic → precision-based exploitation → transparency-focused optimisation>

---

## Performance Summary

### Evaluation Criteria

Performance was assessed using:

- Best observed function value
- Improvement trend stability
- Controlled reduction of variance
- Final leaderboard ranking

### Observed Behaviour Patterns
- **Lower-dimensional functions** showed diminishing returns after early rounds.
- Higher-dimensional functions required sustained exploration.
- Boundary-sensitive functions benefited from structured exploitation.
- **Several functions** remained noisy and exhibited high sensitivity to input changes.

---

## Assumptions

The optimisation framework assumes:

- Local smoothness near high-performing regions
- Historical performance trends provide directional information
- Independence across the eight functions
- Strict query budget constraints
- - **No formal surrogate training:** While inspired by Bayesian reasoning, no automated surrogate model was fitted.

The framework does not assume availability of gradients.

---

## Transparency and Reproducibility

This optimisation strategy facilitates reproducibility by:

- Providing complete query history for every function and round.
- Documenting the context and reasoning behind each query.
- Offering interpretable logic for why particular regions were explored or exploited.

To reproduce this strategy, an external reviewer needs:

- Complete historical data of function queries and outputs (available in this repository).
- Documentation of the reasoning per round.
- Knowledge of step-size rules and adjustment strategies.

---

## Limitations

- No formal convergence guarantees
- Manual strategic judgement influenced decisions
- Limited sampling density relative to dimensionality
- No full probabilistic uncertainty quantification in later rounds
- Possible over-concentration in discovered basins

Despite these limitations, the strategy demonstrated strong adaptive behaviour under limited information.

---

## Ethical Considerations

Even though this framework is not applied to sensitive real-world data, records of decision logic and transparency practices align with ethical optimisation principles:

- **Transparent reasoning:** All query decisions are documented round by round.
- **Reproducibility:** Inputs and outputs per round are recorded in structured logs.
- **Assumption disclosure:** Decision assumptions are made explicit to reduce misinterpretation.
- **Educational value:** The strategy supports clear learning outcomes for optimisation under constraints.

If adapted to real-world domains (e.g., finance or healthcare), additional ethical safeguards such as bias auditing, uncertainty quantification and governance oversight would be necessary.


---

## Broader ML Relevance

This capstone project demonstrates applied skills in:

- Bayesian optimisation principles
- Exploration–exploitation trade-offs
- Sequential decision-making under uncertainty
- Adaptive step-size control
- Function-specific optimisation logic

These skills directly translate to:

- Hyperparameter tuning
- Automated ML systems
- Financial modelling
- Experimental design
- Reinforcement learning environments

---

## Final Reflection

The central lesson from this project is that optimisation success depends on:

- Adaptability
- Disciplined exploration
- Function-specific reasoning
- Controlled exploitation
- Long-term strategic thinking

Achieving competitive places on certain functions validated the structured adaptive approach and demonstrated that principled exploration followed by disciplined exploitation is a powerful framework for optimisation under uncertainty.

---





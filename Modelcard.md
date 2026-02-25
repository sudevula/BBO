# 🧠 Model Card: BBO Optimization Strategy (v1.0)

## Overview

**Model Title:** Iterative BBO Optimization Strategy  
**Version:** 1.0  
**Author:** Sundari Devulapalle
**Date:** 26th Feb 2026

**Model Type:** Human-guided sequential optimisation framework  
**Presentation:** Not a standalone predictive model, but a documented decision framework combining exploratory and exploitative strategies inspired by Bayesian optimisation principles.

This Model Card describes the optimisation approach developed in the BBO Capstone Project, detailing its objectives, methodology, performance characteristics, assumptions, limitations, and ethical considerations.

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

The optimisation strategy was developed over ten rounds of iterative queries across eight independent black-box functions. The overall methodology can be summarised as:

1. **Exploration Phase (Rounds 1–3):**  
   Broad sampling across the input domain to identify preliminary areas of interest. The initial phase was grounded in Bayesian optimisation principles. I applied Gaussian Process-style reasoning, prioritising:

  - Broad exploration of the input domain
  - Sampling uncertain regions
  - Avoiding premature convergence

  At this stage, the focus was on information gathering rather than immediate performance maximisation. The objective was to approximate the global landscape under strict query constraints.


2. **Hybrid Exploration & Exploitation Phase (Rounds 4–7):**  
   A mix of exploration and local refinement informed by observed performance trends. Local decisions were influenced by patterns such as boundary improvement or local signal stability.

   In **weeks 4 and 5**, I went for structured exploitation and Feature Sensitivity. As more observations accumulated, I shifted toward identifying locally promising regions. I began analysing feature sensitivity, identifying trends (particularly boundary-driven behaviour in Function 5) and reducing step sizes near strong outputs. The strategy transitioned from uncertainty-driven exploration to structured local refinement. **Week 6** was refinement based on research. After reviewing neural network optimisation literature, I incorporated ideas such as gradient-like reasoning via small perturbations and viewing output changes as local directional signals. The conceptual framing shifted toward understanding local response behaviour. **Week 7** optimisation task was reframed to hyperparameter tuning treating each function independently and adjusting step sizes dynamically. I recognised the diminishing returns in saturated regions and I tried to avoid overfitting to some noisy signals I have seen. 

3. **Exploitation Phase (Rounds 8–10):**  
   In this phase, I focused refinement in regions with historically strong outputs. Step sizes were reduced and perturbations were conservative to avoid destabilising previously promising regions.  Decisions were documented to ensure interpretability and reproducibility. The strategy became less about aggressive optimisation and more about transparent reasoning under uncertainty.

Across ten rounds, the strategy evolved from:

> Probabilistic exploration → structured refinement → research-informed reasoning → hyperparameter tuning logic → precision-based exploitation → transparency-focused optimisation


---

## Performance Summary

### Evaluation Metrics

This strategy evaluates performance based on:

- **Best Observed Output:** The highest value returned by the black-box function per round.
- **Trend Consistency:** Whether improvements occur as step sizes are reduced.
- **Local Stability:** Whether small adjustments yield predictable changes.

### Key Observations

- **Function 5** demonstrated consistently strong boundary-guided gains (peaking above 4000).
- **Functions 7 and 8** stabilised in moderately high output regions, indicating consistent exploitation success.
- **Lower-dimensional functions** showed diminishing returns after early rounds.
- **Several functions** remained noisy and exhibited high sensitivity to input changes.

No formal theoretical convergence guarantees were produced; performance was measured through best-so-far values and behaviour over time.

---

## Assumptions

This strategy is based on several key assumptions:

- **Local smoothness** near high-performing regions, i.e., small perturbations yield predictable behaviour.
- **Historical performance trends** are indicative of future directions in the search space.
- **Independence across functions**, i.e., each function can be optimised separately.
- **Resource constraints**, recognising that only one query per function per round is permitted.

These assumptions shaped decision logic and influenced step size choices. In scenarios where the objective surface is discontinuous or chaotic, the strategy may underperform.

---

## Limitations

Important limitations include:

- **Limited sampling budgets:** With only ~10–20 queries per function, the search space cannot be fully covered.
- **Manual heuristic influence:** Decision logic includes subjective judgement, which may introduce bias.
- **Uneven space coverage:** Early exploratory noise combined with later refinement leads to dense sampling in some local regions and sparse coverage elsewhere.
- **No formal surrogate training:** While inspired by Bayesian reasoning, no automated surrogate model was fitted.
- **Absence of uncertainty estimation:** Predictions or confidence bounds were not generated.

These limitations restrict generalisability to larger, complex, or safety-critical optimisation contexts.

---

## Ethical Considerations

Even though this framework is not applied to sensitive real-world data, records of decision logic and transparency practices align with ethical optimisation principles:

- **Transparent reasoning:** All query decisions are documented round by round.
- **Reproducibility:** Inputs and outputs per round are recorded in structured logs.
- **Assumption disclosure:** Decision assumptions are made explicit to reduce misinterpretation.
- **Educational value:** The strategy supports clear learning outcomes for optimisation under constraints.

If adapted to real-world domains (e.g., finance or healthcare), additional ethical safeguards such as bias auditing, uncertainty quantification and governance oversight would be necessary.

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

Future iterations may integrate automated surrogate fitting with preserved logging to combine interpretability with performance.

---




# 📄 Datasheet for Black-Box Optimisation (BBO) Capstone Dataset

## 1. Motivation

### Why was this dataset created?

This dataset was created as part of the Imperial College Professional Certification in AI & ML Black-Box Optimisation (BBO) Capstone Project.

The objective of the dataset is to support experimentation with **sequential optimisation under uncertainty**, where:

- The true objective functions are unknown  
- Evaluations are expensive  
- Only one query per function per round per week is allowed  

This setup mirrors real-world optimisation problems such as:

- Hyperparameter tuning  
- Financial optimisation  
- Scientific experimentation  
- Engineering design optimisation  

The dataset allows analysis of how optimisation strategies evolve over time and how decision-making improves as more observations become available.

---

## 2. Composition

### What does the dataset contain?

The dataset contains:

- Eight independent black-box functions  
- Input vectors in the range `[0, 1]^d`  
- Dimensions ranging from 2 to 8  
- One scalar output per query  
- Approximately 19 observations per function after ten rounds  

Each record includes:

- Round number  
- Function identifier (1–8)  
- Input vector (continuous values between 0 and 1)  
- Output value (real number returned by the hidden function)  

### Format

Data is stored as:

- CSV files  
- NumPy arrays  
- Weekly structured documents  

### Known Gaps

- Coverage of the input space is uneven  
- Later rounds focus more heavily on high-performing regions  
- Some regions remain unexplored due to limited query budget  

There are no missing values.

---

## 3. Collection Process

### How were queries generated?

Queries were generated sequentially across ten weekly rounds.

The strategy evolved over time:

- **Rounds 1–3:** Exploration-heavy sampling  
- **Rounds 4–7:** Hybrid exploration and exploitation  
- **Rounds 8–10:** Local refinement near high-performing regions  

Techniques used include:

- Bayesian optimisation intuition 
- Manual trend analysis  
- Boundary probing  
- Local perturbation around maxima  

Only one query per function was allowed per round.

### Time Frame

Data was collected over approximately ten weeks as part of the structured capstone programme.

---

## 4. Preprocessing and Intended Uses

### Preprocessing

- No transformations were applied to inputs or outputs  
- Inputs remain scaled in `[0,1]`  
- Outputs are used in raw form  

### Intended Uses

This dataset is suitable for:

- Studying optimisation under limited evaluation budgets  
- Comparing exploration vs exploitation strategies  
- Demonstrating sequential decision-making  
- Educational experimentation  

### Inappropriate Uses

This dataset should **not** be used for:

- Real-world financial or healthcare decision-making  
- Safety-critical optimisation  
- Claims about generalisable optimisation performance  

---

## 5. Distribution and Maintenance

### Availability

The dataset is hosted publicly in this GitHub repository alongside:

- Query history  
- Results  
- Notebooks  
- Documentation  

### Terms of Use

- Educational and research purposes  
- No commercial or production deployment  

### Maintenance

The dataset is maintained by the project author.

Updates occur incrementally by round and are version-controlled.

No personal, sensitive, or real-world data is included.

---

## 6. Transparency Statement

This datasheet was created to:

- Improve reproducibility  
- Clarify assumptions  
- Document sampling bias  
- Enable external review  

All optimisation decisions are documented to allow others to replicate or critique the approach.

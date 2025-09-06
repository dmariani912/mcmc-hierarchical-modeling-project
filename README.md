# Bayesian Hierarchical Analysis of Public Transit Wait Times

## 📊 Project Overview
This project involved a statistical analysis of public bus wait times across 10 major US cities for the Department of Transportation. The goal was to model city-specific wait times using a **Bayesian hierarchical (multilevel) model**. This advanced technique allows for information sharing between cities, producing more robust and accurate estimates, especially for locations with smaller sample sizes.

## ⚙️ Technical Implementation

### Model & Methods
*   **Likelihood:** City-specific wait times were modeled using an Exponential distribution: `y_i ~ Exp(θ_i)`.
*   **Hierarchical Structure:** Used Gamma hyperpriors for the Exponential rate parameters: `θ_j ~ Gamma(α, β)` with weakly informative hyperpriors on `α` and `β`.
*   **Custom MCMC Sampler:** Implemented a **Metropolis-Hastings MCMC algorithm from scratch in R** to sample from the intractable joint posterior distribution of the hyperparameters `α` and `β`.
*   **Convergence Diagnostics:** Rigorously assessed model reliability using:
    *   Trace plots
    *   Gelman-Rubin diagnostic (R-hat < 1.1)
    *   Raftery-Lewis diagnostic
    *   Effective Sample Size (ESS)
*   **Inference:** Calculated posterior means and 95% credible intervals for the wait time in each city.

### 🛠️ Tools & Technologies
*   **R**
*   **Libraries:** `MCMCpack`, `coda`, `TruncatedNormal`
*   **Statistical Methods:** Markov Chain Monte Carlo (MCMC), Metropolis-Hastings Algorithm, Hierarchical Bayesian Modeling, Probabilistic Programming

## 📈 Key Findings
The hierarchical model provided posterior estimates for average wait times, revealing crucial insights:

| City | Mean Estimated Wait (Mins) | 95% Credible Interval |
|:---|---:|---:|
| Los Angeles | 14.5 | (9.7, 22.0) |
| Miami | 13.0 | (9.6, 18.2) |
| New York City | 10.1 | (6.6, 15.7) |
| Boston | 5.2 | (3.4, 7.9) |
| **Overall Mean** | **~8.0** | |

*   **Uncertainty Trend:** Cities with the longest waits (e.g., LA, Miami, NYC) also exhibited the highest uncertainty, suggesting inconsistent scheduling and a greater need for operational review.
*   **Shrinkage Effect:** The model effectively "shrunk" estimates for cities with small sample sizes toward the overall mean, demonstrating the primary benefit of hierarchical modeling.

---

**Note on Academic Integrity:** This project was completed as the capstone for **STAT 223: Bayesian Inference** at the University of Rochester. The original RMarkdown (`.Rmd`) source file is not distributed here to adhere to my university's academic integrity policies regarding the publication of course solutions. The provided PDF represents the complete final output and analysis.

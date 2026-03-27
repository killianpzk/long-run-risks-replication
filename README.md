# Replication Project: The Long-Run Risks Model

This repository contains the Python codebase and historical data used to replicate, simulate, and empirically assess the Long-Run Risks (LRR) asset pricing model. 

The project focuses on both the baseline framework proposed by Bansal and Yaron (2004) and its extension featuring stochastic volatility, as developed by Bansal, Kiku, and Yaron (2010). This repository serves as the computational companion to the analytical report provided.

## 📄 Repository Structure

* **`Replication_Project_LongRunRisks_Pliszczak.pdf`**: The comprehensive analytical report. It contains the derivations of the pricing kernel, the risk-free rate, and the equity premium under recursive (Epstein-Zin) preferences, alongside a detailed discussion of the empirical findings.
* **`Replication_Project_LongRunRisks_Pliszczak.ipynb`**: The core Jupyter Notebook. It includes the fixed-point numerical solutions, Monte Carlo simulations, and the predictive regressions framework.
* **`ie_data.xls`**: The historical macro-financial dataset provided by Robert Shiller, used to reconstruct the empirical asset pricing moments.

## ⚙️ Computational Methodology

The code is structured around two main quantitative tasks:

1. **Numerical Calibration & Simulation**
   * Solves the model's complex fixed-point equations for both the BY (2004) and BKY (2010) parametrizations using an iterative convergence algorithm (`tol=1e-8`).
   * Runs large-scale Monte Carlo simulations (100,000 paths) to generate model-implied unconditional moments (e.g., expected equity premium, risk-free rate, and price-dividend ratio).
   * Random seeds are strictly enforced to ensure full reproducibility of the research outputs.

2. **Empirical Predictability Analysis**
   * Reconstructs a clean macro-financial dataset by merging Robert Shiller's historical data with real consumption and T-Bill series fetched dynamically from the FRED database via `pandas_datareader`.
   * Evaluates the model's ability to generate return predictability by running univariate and multivariate OLS regressions (`statsmodels`) across multiple horizons (1Y, 3Y, 5Y), comparing simulated $R^2$ values against empirical benchmarks.

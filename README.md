# Multi-Asset & R&D Pipeline Portfolio Risk Analytics

## Executive Summary
This repository contains a modular, object-oriented Python framework designed to simulate, stress-test, and quantify risk across two distinct asset domains: financial investment portfolios and multi-stage pharmaceutical R&D pipelines. By decoupling the simulation engine from asset specifics, the framework leverages stochastic methods to evaluate downside risk, volatility, and capital allocation efficiencies. This module also contains a Monte Carlo simulation script that determines the Probability of Success (PoS) and Valuation of a hypothetical R&D Portfolio. 

There are different types of portfolios to keep in mind: 

- Aggressive (high-risk for maximum capital appreciation)
- Defensive (stable, low-volatility assets)
- Income-generating (focused on dividends/yields)
- Hybrid (balanced mixes of stocks and bonds)
- Socially Responsible/ESG Portfolio (aligns with personal values without sacrificing financial returns)
- Speculative Portfolio (achieve rapid, outsided returns by capitalizing on short-term market inefficiencies or emerging sectors)

## Repository Structure
* `portfolio_analysis_with_python_classes.ipynb`: An object-oriented architecture evaluating diverse financial asset strategies (ESG, Income, Speculative, Defensive).
* `monte_carlo_sims_practice.ipynb`: A stochastic engine simulating cumulative probabilities of success ($PoS$) across sequential regulatory phases.

## Methodology & Mathematical Framework

### 1. Financial Portfolio Risk Framework (`portfolio_analysis_with_python_classes.ipynb`)
The financial analysis module utilizes Python classes to encapsulate historical asset parameters and compute core risk-adjusted return metrics:

* **Expected Portfolio Return ($E[R_p]$):** Calculated via matrix multiplication of asset weights ($W$) and historical mean returns ($\mu$):
  $$E[R_p] = W^T \mu$$
* **Portfolio Volatility ($\sigma_p$):** Derived using the asset covariance matrix ($\Sigma$) to isolate multi-variable tracking errors:
  $$\sigma_p = \sqrt{W^T \Sigma W}$$
* **Asset Strategies Evaluated:**
  * **Aggressive / Speculative:** Maximizing high-beta asset exposure to capitalize on short-term market inefficiencies.
  * **Defensive / Income:** Low-volatility, dividend-yielding architectures optimized for capital preservation.
  * **Socially Responsible (ESG):** Constrained optimization filtering for non-financial compliance boundaries without degrading the efficient frontier.

### 2. Pharmaceutical R&D Stochastic Modeling (`monte_carlo_sims_practice.ipynb`)
To model the highly volatile path of binary drug development pipelines, the system applies Monte Carlo frameworks to calculate cumulative phase-gate risk.

* **Cumulative Probability of Success ($PoS_{cum}$):** For a drug moving through $n$ independent regulatory phases (Phase I, Phase II, Phase III, Regulatory Review):
  $$PoS_{cum} = \prod_{i=1}^{n} P(\text{Success} \mid \text{Phase } i)$$
* **Stochastic Volatility Injection:** Rather than utilizing static historical averages, phase-gate success rates are modeled as random variables drawn from beta distributions to capture real-world trials uncertainty and pipeline path dependency.
* **Risk Aggregation:** Simulates $N = 10,000+$ trials to generate risk distributions, mapping out the Value-at-Risk ($VaR$) for R&D capital expenditure lines.

## Core Technical Stack
* **Languages:** Python (Object-Oriented Architecture)
* **Libraries:** NumPy (Vectorized Matrix Computations), Pandas (Data Aggregation & Wrangling), Matplotlib/Seaborn (Risk Distribution Visualizations)
* **Environment:** Jupyter Notebooks, Git

## Getting Started

### Prerequisites
Ensure you have Python 3.8+ installed. Clone the repository and install dependencies:

```bash
git clone https://github.com
cd drug_pipeline_probability_of_success
pip install -r requirements.txt
```

### Running the Analytics Engine
Launch the Jupyter notebooks to interact with the models:
<!--```bash
jupyter no -->

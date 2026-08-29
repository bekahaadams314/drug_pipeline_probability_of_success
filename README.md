# Portfolio Risk Analytics for R&D Pipeline

## Summary:
This repository presents a simulation framework designed to model stage-gated clinical trial progression, evaluate expected portfolio Net Present Value (NPV) distributions, and quantify tail risk using 95% Value at Risk (VaR). We explore a classic Monte Carlo approach and a cleaner object-oriented approach. 

## 1. Mathematical Formulation:

### Stage-Gated Decision Dynamics:
Clinical trials operate as a semi-Markov process over sequential phases $k \in \{1, 2, \dots, N\}$. Transitioning from stage $k-1$ to stage $k$ requires a deterministic capital injection $C_k$ and exhibits an empirical probability of success $p_k \in (0, 1)$.

The cumulative probability of a candidate reaching commercial launch after stage $N$ is expressed as:

$$P(\text{Approval}) = \prod_{k=1}^{N} p_k$$

### Discounted Expected Valuation:
Given a discount rate $r$, expected commercial market payoff $V$, and stage completion times $\tau_k$, the expected cumulative present value of candidate $i$ factors in intermediate abandonment states:

$$\mathbb{E}[\text{NPV}_i] = \left( \prod_{k=1}^{N} p_{i,k} \right) \frac{V_i}{(1+r)^{\sum \tau_{i,k}}} - \sum_{k=1}^{N} \left( \prod_{j=1}^{k-1} p_{i,j} \right) \frac{C_{i,k}}{(1+r)^{\sum_{m=1}^{k-1} \tau_{i,m}}}$$

This is similar to what I recall learning in my design class in undergrad and my energy systems modelling course in graduate school. A lot of that type of economic thinking has inspired me to consider this in the first place, especially for R&D in relevant sectors that I am interested in, such as energy and pharma.

### Downside Risk & Value at Risk (VaR):
To quantify downside tail exposure across a portfolio of $M$ independent or correlated assets under trial outcome uncertainty, we define total portfolio loss $L = \sum_{i=1}^M \left( \mathbb{E}[\text{NPV}_i] - \text{NPV}_i(\omega) \right)$ for scenario draw $\omega$. 

The portfolio $\text{VaR}_\alpha$ at confidence level $\alpha \in (0, 1)$ represents the infimum loss threshold such that the tail probability of exceeding that loss does not surpass $1 - \alpha$:

$$\text{VaR}_\alpha = \inf \{ l \in \mathbb{R} : P(L > l) \le 1 - \alpha \}$$

## 2. Key Findings (Open to Suggestions):

* **Phase II Bottleneck:** Sensitivity analysis indicates that Phase II transition probability accounts for 62% of overall portfolio NPV variance.
* **Risk Thresholding:** Across 10,000 Monte Carlo trials, the portfolio 95% VaR converges at $48.2M, driven primarily by simultaneous late-stage (Phase III) pipeline failures.
* **Optimal Stopping:** Incorporating interim dynamic decision checkpoints reduces projected portfolio loss variance by 18%.
  
## Technical Stack:
* **Languages:** Python 
* **Libraries:** NumPy, Pandas, Matplotlib/Seaborn
* **Environment:** Jupyter Notebooks, Git



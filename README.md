# Portfolio Risk Analytics for R&D Pipeline

This project presents a simulation framework designed to model stage-gated clinical trial progression, evaluate expected portfolio Net Present Value (NPV) distributions, and quantify tail risk using 95% Value at Risk (VaR).

## Motivation 

I was interested in the process of clinical trials and whether it can be modeled. Primarily, this stemmed from my interest in translating scientific theory and work in an academic setting and translating that work to scalable R&D environments in industry. This not only applies to energy systems but, most importantly, to drug delivery candidates and pharmaceuticals. A lot of the work done in the lab winds up not being as scalable or effective in clinical trials, which requires a deeper dive into the science itself. I was more interested in how to stage the clinical trial progression and how one can determine risk and value from it.

Furthermore, I wanted to identify bottlenecks in the trial. That is what led me to metrics such as VaR. Furthermore, I was able to implement what I learned from my energy systems class and design class in undergrad and grad school. Seeing all the details come together and play a role in this aspect of Monte Carlo simulation and risk analytics was rewarding for me and got me interested in the field of risk analytics and decision science in the first place. 

## Mathematics behind the work: 

### Stage-Gated Decision Dynamics
Clinical trials operate as a semi-Markov process over sequential phases $k \in \{1, 2, \dots, N\}$. Transitioning from stage $k-1$ to stage $k$ requires a deterministic capital injection $C_k$ and exhibits an empirical probability of success $p_k \in (0, 1)$.

The cumulative probability of a candidate reaching commercial launch after stage $N$ is expressed as:

$$P(\text{Approval}) = \prod_{k=1}^{N} p_k$$

For this project, I thought it would be interesting to use a Monte Carlo process where each stage is represented as a probability distribution. These are values that I just looked up on Google to get a sense of the success of each stage and the probability behavior realistically. 

### Discounted Expected Valuation
Given a discount rate $r$, expected commercial market payoff $V$, and stage completion times $\tau_k$, the expected cumulative present value of candidate $i$ factors in intermediate abandonment states:

$$\mathbb{E}[\text{NPV}_i] = \left( \prod_{k=1}^{N} p_{i,k} \right) \frac{V_i}{(1+r)^{\sum \tau_{i,k}}} - \sum_{k=1}^{N} \left( \prod_{j=1}^{k-1} p_{i,j} \right) \frac{C_{i,k}}{(1+r)^{\sum_{m=1}^{k-1} \tau_{i,m}}}$$

### Downside Risk & Value at Risk (VaR)
To quantify downside tail exposure across a portfolio of $M$ independent or correlated assets under trial outcome uncertainty, we define total portfolio loss $L = \sum_{i=1}^M \left( \mathbb{E}[\text{NPV}_i] - \text{NPV}_i(\omega) \right)$ for scenario draw $\omega$. 

The portfolio $\text{VaR}_\alpha$ at confidence level $\alpha \in (0, 1)$ represents the infimum loss threshold such that the tail probability of exceeding that loss does not surpass $1 - \alpha$:

$$\text{VaR}_\alpha = \inf \{ l \in \mathbb{R} : P(L > l) \le 1 - \alpha \}$$

## Key Findings (Open to Suggestions):

- **Phase II Bottleneck:** Sensitivity analysis indicates that Phase II transition probability accounts for 62% of overall portfolio NPV variance.
- **Risk Thresholding:** Across 10,000 Monte Carlo trials, the portfolio 95% VaR converges at $48.2M, driven primarily by simultaneous late-stage (Phase III) pipeline failures.
- **Optimal Stopping:** Incorporating interim dynamic decision checkpoints reduces projected portfolio loss variance by 18%.
  
## Languages used for this project:
* **Languages:** Python 
* **Libraries:** NumPy, Pandas, Matplotlib/Seaborn
* **Environment:** Jupyter Notebooks



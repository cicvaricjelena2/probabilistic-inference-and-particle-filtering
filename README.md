# Probabilistic Inference and Particle Filtering

A Python-based project exploring probabilistic reasoning, Bayesian networks, Monte Carlo sampling methods, and particle filtering for dynamic state estimation.

The project consists of two independent tasks covering probabilistic inference and sequential estimation under uncertainty.

Project Overview

Part 1 — Bayesian Network Inference

This task focuses on estimating conditional probabilities in a Bayesian network using exact inference and stochastic sampling methods.

Methods implemented:

* Bayesian Network representation using a Directed Acyclic Graph (DAG).
* Conditional Probability Tables (CPTs).
* Variable Elimination.
* Rejection Sampling.
* Gibbs Sampling.
* Monte Carlo estimation.

The objective is to estimate:

[
P(B=b^+ \mid E=e^-,F=f^-)
]

The exact inference result is used as a reference for evaluating the sampling methods.

Experimental Results

Method	Mean Estimate	Standard Deviation
Variable Elimination	0.2391	—
Rejection Sampling	0.2392	0.0078
Gibbs Sampling	0.2388	0.0079

Both sampling approaches produce estimates close to the exact inference result.

Part 2 — Particle Filtering for State Estimation

This task implements a particle filter to estimate the position and velocity of a moving target from noisy observations.

Motion Model

The target moves along a one-dimensional axis. Its velocity is modeled as a time-dependent Gaussian random variable, while its position is obtained by accumulating velocity over time.

Measurement Model

The observation model includes:

* Laplace-distributed measurement noise.
* A 10% probability of receiving an observation containing noise only.
* Measurement noise whose scale increases with the target’s distance from the origin.

Particle Filter Implementation

Each particle represents a hypothesis about the target state:

[
s_t^{(i)}=(x_t^{(i)},v_t^{(i)})
]

The implementation includes:

* Particle initialization.
* Importance weight calculation.
* State estimation using weighted averages.
* Particle propagation according to the motion model.
* Particle resampling.

The filter uses 1,000 particles.

Resampling Strategy Comparison

Three resampling strategies are investigated:

1. No Resampling — particles retain their weights throughout the estimation process.
2. Resampling at Every Iteration — particles are resampled at every time step.
3. Conditional Resampling — resampling is performed only when the effective sample size falls below half the total number of particles.

The effective sample size is defined as:

[
N_{\mathrm{eff}}=\frac{1}{\sum_i w_i^2}
]

The resampling threshold is:

[
N_{\mathrm{eff}}<\frac{N}{2}
]

Experimental Evaluation

* 500 independent Monte Carlo simulations.
* Position estimation error evaluation.
* Root Mean Squared Error (RMSE).
* Comparison of the three resampling strategies.

The reported experiments show that conditional resampling achieves the best performance among the three investigated strategies, while no resampling leads to particle degeneracy and less reliable estimates.

Technologies and Libraries

* Python
* NumPy
* Matplotlib
* SciPy
* Jupyter Notebook

Repository Structure

probabilistic-inference-and-particle-filtering/
│
├── notebooks/
│   ├── bayesian_network_inference.ipynb
│   └── particle_filter_tracking.ipynb
│
├── requirements.txt
├── .gitignore
└── README.md

How to Run

Clone the repository:

git clone https://github.com/cicvaricjelena2/probabilistic-inference-and-particle-filtering.git

Install dependencies:

pip install -r requirements.txt

Start Jupyter Notebook:

jupyter notebook

Open either notebook in the notebooks/ directory and execute the cells.

Key Concepts Demonstrated

* Probabilistic graphical models
* Bayesian inference
* Exact and approximate inference
* Monte Carlo methods
* Markov Chain Monte Carlo (MCMC)
* Gibbs Sampling
* Rejection Sampling
* Sequential state estimation
* Particle Filtering
* Importance Sampling
* Effective Sample Size (ESS)
* Resampling strategies
* Monte Carlo performance evaluation

Conclusion

This project demonstrates two important approaches to reasoning under uncertainty.

The Bayesian network task compares exact inference with stochastic sampling methods, while the particle filtering task investigates sequential state estimation in the presence of noisy observations and outliers.

Together, the two tasks provide practical implementations of probabilistic inference, Monte Carlo simulation, and Bayesian state estimation.

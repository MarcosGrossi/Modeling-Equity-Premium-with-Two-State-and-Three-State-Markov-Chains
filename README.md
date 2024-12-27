# Modeling Equity Premium with Two-State and Three-State Markov Chains

This Python project investigates the dynamics of the equity premium by modeling the economy using two-state and three-state Markov chains. It calibrates state-dependent parameters and solves the investor’s Euler equations to determine the mean equity premium under different economic scenarios, including the presence of rare disasters.

## 🔬 Overview

This project implements calculations and analyses to:

- **Two-State Model (Normal and Recession):**
  - Define a two-state Markov chain representing Normal times and Recessions.
  - Calibrate transition probabilities to match empirical recession frequency.
  - Align mean consumption growth with observed data.
  - Solve state-dependent Euler equations to determine stock returns and risk-free rates.
  - Compute the mean equity premium.

- **Three-State Model (Normal, Recession, and Disaster):**
  - Extend the two-state model by introducing a Disaster state.
  - Adjust transition probabilities to incorporate the occurrence of rare disasters.
  - Determine the stationary distribution of the three-state Markov chain.
  - Calibrate consumption growth in Normal times to match empirical averages.
  - Solve a system of three Euler equations for state-dependent stock returns.
  - Calculate risk-free rates and the mean equity premium in the presence of disasters.

In simpler terms:

- **Two-State Model:**  
  Models the economy during Normal and Recession periods, calibrating transition probabilities and consumption growth to align with historical data. It then solves for stock returns and the equity premium based on investor preferences.

- **Three-State Model:**  
  Adds a rare Disaster state to the economy, adjusting transition dynamics and consumption growth accordingly. This extension allows for the analysis of how rare catastrophic events influence the equity premium.

## ⚙️ Project Functionalities

### Two-State Model

1. **Transition Probability Calibration:**
   - Define transition probabilities between Normal and Recession states.
   - Calibrate the probability of moving from Recession to Normal \$\pi_{21}\$ to ensure recessions occur every 10 years on average.

2. **Consumption Growth Calibration:**
   - Calculate the mean consumption growth from empirical data \$\bar{G}\$.
   - Calibrate the Normal state consumption growth rate \$G_1\$ to match \$\bar{G}\$:

     \$\bar{G} = \Pi_1 G_1 + \Pi_2 G_2\$

3. **Solving Euler Equations:**
   - With the calibrated parameters, set up and solve the investor’s Euler equations for each state:

     \$1 = \beta \sum_{j=1}^2 \pi_{ij} (G_j)^{-\gamma} R_j, \quad i = 1, 2.$

4. **Risk-Free Rates Calculation:**
   - Compute the risk-free rate in each state:

     \$R_{f,i} = \frac{1}{\beta \sum_{j=1}^2 \pi_{ij} (G_j)^{-\gamma}}\$

5. **Mean Equity Premium:**
   - Calculate the mean equity premium as the difference between the mean equity return and the mean risk-free rate:

     \$\mathbb{E}[R_{\text{eq}}] - \mathbb{E}[R_f]\$

### Three-State Model

1. **Introducing the Disaster State:**
   - Add a third state representing Disasters, with consumption growth \$G_3 = 0.70\$ (30% decline).

2. **Adjusting Transition Probabilities:**
   - Modify transition probabilities to incorporate the Disaster state:
     - From Normal (state 1): \$\pi_{11} = 0.91\$, \$\pi_{12} = 0.07\$, \$\pi_{13} = 0.02\$.
     - From Recession (state 2): \$\pi_{21} = 0.72\$, \$\pi_{22} = 0.28\$, \$\pi_{23} = 0.00\$.
     - From Disaster (state 3): \$\pi_{31} = 1.00\$, \$\pi_{32} = 0.00\$, \$\pi_{33} = 0.00\$.

3. **Stationary Distribution:**
   - Determine the long-run stationary distribution \$\Pi = (\Pi_1, \Pi_2, \Pi_3)\$ by solving:

     \$\Pi = \Pi P \quad \text{and} \quad \Pi_1 + \Pi_2 + \Pi_3 = 1\$

4. **Consumption Growth Calibration:**
   - Calibrate the Normal state consumption growth rate (\$G_1\$) to match the empirical mean consumption growth:
     \$\bar{G} = \Pi_1 G_1 + \Pi_2 G_2 + \Pi_3 G_3
     \$

5. **Solving Euler Equations:**
   - Set up and solve the investor’s Euler equations for each of the three states:

     \$1 = \beta \sum_{j=1}^{3} \pi_{ij} (G_j)^{-\gamma} R_j, \quad i = 1, 2, 3\$

6. **Risk-Free Rates Calculation:**
   - Compute the risk-free rate in each state:

     \$R_{f,i} = \frac{1}{\beta \sum_{j=1}^{3} \pi_{ij} (G_j)^{-\gamma}}\$

7. **Mean Equity Premium:**
   - Calculate the mean equity premium considering all three states:

     \$\mathbb{E}[R_{\text{eq}}] - \mathbb{E}[R_f] = \left( \Pi_1 R_1 + \Pi_2 R_2 + \Pi_3 R_3 \right) - \left( \Pi_1 R_{f,1} + \Pi_2 R_{f,2} + \Pi_3 R_{f,3} \right)\$

## ⚠️ Assumptions

- **Two-State Model:**
  - Economy transitions between Normal and Recession states with calibrated probabilities.
  - Consumption growth in Recession is fixed at \$G_2 = 0.97\$.
  - Discount factor \$\beta = 0.99\$ and risk aversion \$\gamma = 5\$.

- **Three-State Model:**
  - Introduces a Disaster state with consumption growth \$G_3 = 0.70\$.
  - Disasters occur only from the Normal state with probability \$\pi_{13} = 0.02\$.
  - Disasters last exactly one period, transitioning back to Normal.
  - No direct transition from Recession to Disaster (\$\pi_{23} = 0\$).
  - Adjusted transition probabilities ensure each row in the transition matrix sums to 1.

- **General:**
  - Consumption growth data is provided as gross growth factors (e.g., 1.02 for 2% growth).
  - The empirical mean consumption growth is accurately estimated from the provided dataset.

## ✅ Requirements

- **Python 3.x**
- **Libraries:**
  - NumPy: `pip install numpy`
  - Pandas: `pip install pandas`
  - Matplotlib: `pip install matplotlib`

## 🪄 Usage

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/MarcosGrossi/State-Dependent-Equity-Premium-Analysis-Using-Markov-Models.git



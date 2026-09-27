# Monte Carlo Tree Search (MCTS) Analysis in a Multi-Agent Environment

A reinforcement learning research project analyzing the performance, convergence, and variance of the Monte Carlo Tree Search (MCTS) algorithm in a deterministic, zero-sum game environment (Tic-Tac-Toe).

## 📌 Project Overview
This project formulates Tic-Tac-Toe as a formal Markov Decision Process (MDP) and implements an online planning agent utilizing Monte Carlo Tree Search with the Upper Confidence Bound for Trees (UCT) selection policy. The study investigates how computational planning budgets (simulation counts) impact policy quality, convergence toward game-theoretic optimality, and multi-seed stability.

## 🧠 Algorithmic Framework
The MCTS agent executes four core phases iteratively before taking an action:
1. **Selection:** Tree traversal guided by UCB1 balancing exploitation and exploration:
   $$UCB = \frac{Q_i}{N_i} + c \cdot \sqrt{\frac{\ln N_{parent}}{N_i}}$$
2. **Expansion:** Generating child nodes for previously unexplored legal actions.
3. **Simulation (Rollout):** Fast-forwarding terminal states using a uniform random default policy.
4. **Backpropagation:** Propagating rollout outcomes (win/loss/draw) upward to update visit counts and node values.

## 📈 Benchmark & Stability Evaluation
Agents were evaluated across multiple independent seeds (Seeds: 42, 100, 999) against two distinct baseline strategies:
* **Random Agent:** Uniform random action selection.
* **Greedy Agent:** Rule-based agent with 1-step lookahead for immediate wins and opponent blocking.

### Quantitative Results (Mean ± Std over Multiple Seeds):
* **Scalability:** Win rates against the Random Agent climbed from **83.33% ± 7.20%** at 2 simulations to **97.78% ± 3.14%** at 100 simulations.
* **Theoretical Convergence:** When playing against the Greedy Agent, increasing simulations eliminated MCTS losses, converging to **86.67% draws** and **~51% wins**, confirming that the agent learned the minimax-optimal policy for this solved game.
* **Variance Reduction:** As simulation budgets increased, standard deviation dropped sharply, demonstrating high algorithmic stability invariant to rollout randomness.

## 🛠 Tech Stack
* **Language:** Python
* **Libraries:** NumPy, Matplotlib, Pandas, Random

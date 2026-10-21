# 🎓 2026 ENC AI: Lab 05 – Intelligent Agents in Vacuum World 3x3

This repository contains the student implementation and analysis for the **2026 ENC AI** laboratory exercise. The objective is to design, implement, and benchmark different types of software agents within a simulated grid environment ($3 \times 3$ Vacuum World).

---

## 🏛️ Theoretical Framework & PEAS Architecture

Following the principles of artificial intelligence (*Russell & Norvig*), an agent perceives its environment through **sensors** and acts upon it using **actuators**. We define the problem using the **PEAS** framework:

* **Performance (Performance Measure):**
  * $+10$ points for each cleaned dirty square.
  * $-1$ point for each movement (energy consumption).
  * $-1$ point for redundant cleaning on an already clean square.
  * $-5$ points for hitting a wall (moving outside the grid).
* **Environment:** A $3 \times 3$ grid (9 squares). Each square can be either `CLEAN` ($0$) or `DIRTY` ($1$). The agent's position is given by coordinates $(r, c) \in \{0, 1, 2\}^2$.
* **Actuators:** Actions from the set `{'UP', 'DOWN', 'LEFT', 'RIGHT', 'CLEAN', 'NOOP'}`.
* **Sensors:** Local perception – the agent only knows its current position and the dirt status of its current tile: `(r, c, is_dirty)`.

---

## 🤖 Implemented Agents

1. **`RandomAgent`:** Selects actions completely at random. Serves as a baseline for comparison.
2. **`SimpleReflexAgent`:** A stateless agent reacting purely to the current percept. If the current square is dirty, it cleans; otherwise, it moves randomly.
3. **`ModelBasedAgent`:** An agent with internal state and memory. It maintains a history map and follows a fixed snake-like patrolling path to systematically clean the grid.

---

## 🔥 Challenge A: Dynamic Environment with Dirt Spawning

To test agent adaptability, the simulation was extended to a **dynamic environment**. In each step, new dirt can spawn on a randomly chosen clean square with a probability of $p_{spawn} = 0.05$. 

* **Impact:** In this dynamic setting, static strategies (like a single-pass `ModelBasedAgent`) experience a performance drop because cleared squares can become dirty again behind the agent's back, requiring adaptive or continuous monitoring strategies.

---

## 📊 Summary of Benchmark Results (100 Runs, 50 Steps)

| Agent Type | Average Score | Cleanliness Ratio |
| :--- | :--- | :--- |
| **RandomAgent** | $-80.76$ | $14.1\%$ |
| **SimpleReflexAgent** | $-37.36$ | $84.2\%$ |
| **ModelBasedAgent** | $+42.59$ | $100.0\%$ |

---

## 🚀 How to Run

1. Open the provided Jupyter Notebook (`.ipynb`) in **Google Colab**.
2. Run **Cell 1** to initialize the environment simulator.
3. Implement or execute the agent cells (`SimpleReflexAgent`, `ModelBasedAgent`).
4. Run the visualization and Monte Carlo benchmark cells to reproduce the results.

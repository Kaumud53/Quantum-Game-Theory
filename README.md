# Quantum Strategies: Classical vs Quantum Game Theory

This repository provides an overview of my project **“Quantum Strategies: Comparison between Classical and Quantum Implementation of Strategies.”**  
The work investigates how quantum mechanics—specifically **superposition** and **entanglement**—can enhance or fundamentally change outcomes in traditional game-theoretic problems.

## 📌 Overview

Classical game theory assumes players choose strategies from fixed sets, leading to outcomes determined by payoff matrices. However, when games are extended to the quantum domain using the **Eisert–Wilkens–Lewenstein (EWL) model**, players can apply quantum operations as strategies. This unlocks new phenomena such as:

- **Strategy superposition**
- **Entanglement-driven correlations**
- **New Nash equilibria absent in classical versions**
- **Higher achievable payoffs**

This project studies two key games:

### **1. Quantum Prisoner’s Dilemma**
- Reproduces classical results at zero entanglement.
- Shows that with increasing entanglement, the classical dilemma can be resolved.
- Demonstrates how quantum strategies outperform classical “Defect–Defect” outcomes.

### **2. Quantum Minority Game**
- Uses a GHZ-entangled initial state.
- Shows enhanced payoffs compared to classical random play.
- Quantum advantage persists until strong noise is introduced.

### **Noise Analysis**
Both **depolarizing** and **amplitude-damping** noise models are applied to study robustness.  
Amplitude damping degrades quantum advantage faster, highlighting sensitivity of entanglement-dependent strategies.

## 🧠 Key Insight

Quantum strategies can **shift equilibria**, **improve outcomes**, and **eliminate classical dilemmas**—but their advantage depends heavily on entanglement levels and noise.

## 📄 Contents

The repository includes:
- The full PDF report explaining theory, methodology, and results.
- Example circuits, payoff tables, and plots demonstrating the difference between classical and quantum strategies.
- Discussions, limitations, and future directions for quantum game theory research.

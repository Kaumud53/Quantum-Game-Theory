# Quantum Strategies: Comparison between Quantum and Classical Implementation of Strategies

**Author:** Kaumud Sharma (I23PH011)

## Overview

This repository contains the report, Qiskit simulation code, and results for a project studying how quantum mechanics — via the **Eisert–Wilkens–Lewenstein (EWL) quantization scheme** — changes the strategic structure and outcomes of two classic games: the **Prisoner's Dilemma** and the **Minority Game**.

Classical strategies are embedded into a quantum circuit using unitary operators and controlled entanglement. Both analytical modeling and Qiskit-based simulation are used to study how entanglement strength, strategy parameters, and realistic noise (depolarizing and amplitude damping) affect payoffs and equilibria.

## Key Findings

- **Quantum Prisoner's Dilemma:** at zero entanglement (γ = 0) the game reduces exactly to the classical case, with (D,D) as the only Nash equilibrium. As entanglement γ increases, the payoff landscape shifts; at γ = π/4 the quantum strategy pair (Q,Q) achieves the Pareto-optimal payoff (3,3), resolving the classical dilemma.
- **Quantum strategy landscape:** sweeping the strategy parameters (θ, φ) reveals multiple payoff peaks from quantum interference, with the dominant "Eisert strategy" emerging as the global maximum under maximal entanglement — a richer strategy space than the classical binary choice.
- **Quantum Minority Game:** initializing 3 players in a GHZ state raises the expected payoff from the classical ~0.33 to ~0.42 (≈25% improvement) via constructive interference that increases the odds of exactly one player landing in the minority.
- **Noise sensitivity:** both depolarizing and amplitude-damping noise erode the quantum advantage — amplitude damping degrades it faster, since it destroys entanglement more aggressively. The quantum-classical payoff gap nearly vanishes at a depolarizing probability around the reported threshold, underscoring the need for high-coherence hardware for any practical benefit.

## Repository Contents

```
.
├── report/             # Project report (IEEE format) and compiled PDF
├── notebooks/          # Jupyter notebooks with Qiskit circuit construction and simulations
├── src/                # Python source (game modeling, EWL circuit builders, payoff extraction, noise models)
├── figures/            # Generated plots (payoff vs. entanglement, payoff surfaces, noise-robustness curves)
└── README.md
```

*(Adjust the folder names above to match the actual repository layout.)*

## Methodology

The project follows an eight-step workflow:

1. **Classical game modeling** — payoff matrices and Nash equilibria for PD and the Minority Game
2. **Quantum game formulation (EWL scheme)** — entangling operator `J(γ) = exp(iγ σx⊗σy / 2)`, per-player unitary strategy `U(θ, φ)`, final state `|ψf⟩ = J†(UA⊗UB)J|00⟩`
3. **Circuit construction in Qiskit** — RX/CNOT-based entangler, per-player strategy gates, disentangler, measurement
4. **Strategy parameter sweeps** — comparing classical strategies (C = Identity, D = Pauli-X) against quantum strategies
5. **Entanglement variation** — classical (γ=0), partial, and maximal entanglement regimes
6. **Measurement and payoff extraction** — converting measured basis-state probabilities into expected payoffs
7. **Noise modeling** — depolarizing and amplitude-damping channels at varying noise probabilities
8. **Comparative analysis** — classical vs. quantum vs. noisy payoffs, equilibrium shifts, and noise robustness

### Tools and Technologies

- Python 3.11
- Qiskit Aer Simulator
- NumPy / Matplotlib
- Jupyter Notebook

### Reproducing the Results

```bash
# example — update to match actual script/notebook names
pip install qiskit qiskit-aer numpy matplotlib
jupyter notebook notebooks/quantum_prisoners_dilemma.ipynb
jupyter notebook notebooks/quantum_minority_game.ipynb
```

## Key Results Summary

**Prisoner's Dilemma payoffs at different entanglement strengths (strategy pair shown as (payoff_A, payoff_B)):**

| Entanglement γ | (C,C) | (D,D) | (C,D) | (D,C) |
|---|---|---|---|---|
| 0 | (3,3) | (1,1) | (0,5) | (5,0) |
| π/2 | (2.6,2.6) | (2,2) | (0.9,4.1) | (4.1,0.9) |
| π/4 | (3,3) | (3,3) | (1.5,3.5) | (3.5,1.5) |

**Minority Game expected payoff:**

| Game Type | Expected Payoff |
|---|---|
| Classical (random) | ~0.33 |
| Quantum (GHZ state) | ~0.42 |
| Quantum + low noise | 0.38 |
| Quantum + high noise | 0.30 |

**Effect of noise on Quantum PD payoffs (Q,Q strategy):**

| Noise Probability | Depolarizing | Amplitude Damping |
|---|---|---|
| 0.0 | (3.0, 3.0) | (3.0, 3.0) |
| 0.1 | (2.6, 2.6) | (2.3, 2.3) |
| 0.2 | (2.2, 2.2) | (1.8, 1.8) |
| 0.3 | (1.9, 1.9) | (1.4, 1.4) |

## Limitations

- Restricted to small qubit systems; no experiments on real quantum hardware
- Only two noise models analyzed (depolarizing, amplitude damping)
- EWL formulation used here is restricted to two-player games
- No error-corrected/fault-tolerant circuits implemented

## Future Work

- Multi-strategy and multi-player quantum game extensions
- Implementation on real quantum hardware
- Use of quantum error correction to preserve entanglement during gameplay

## References

1. J. Eisert, M. Wilkens, and M. Lewenstein, "Quantum Games and Quantum Strategies," *Phys. Rev. Lett.*, 1999.
2. E. Flitney and L. C. L. Hollenberg, "Quantum Minority Game," *Phys. Lett. A*, 2007.
3. D. Meyer, "Quantum strategies," *Phys. Rev. Lett.*, 1999.
4. A. Iqbal, "Studies in quantum games," PhD Thesis, 2005.
5. M. Nielsen & I. Chuang, *Quantum Computation and Quantum Information*, Cambridge Univ. Press.

## Acknowledgements

Thanks to Dr. Nitesh Funde, Department of Artificial Intelligence, for guidance and feedback throughout this project.

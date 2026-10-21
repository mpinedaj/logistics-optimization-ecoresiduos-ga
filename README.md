# EcoResiduos del Llano — Agricultural Waste Logistics Network Optimization

> Optimization of agricultural waste reception and processing in the Meta department (Colombia) using **Linear Programming (Transportation / Minimum-Cost Flow Problem)** and **Genetic Algorithms**, with an interactive interface and sensitivity analysis.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-In%20development-yellow)

**Universidad de los Llanos** · Faculty of Basic Sciences and Engineering · Systems Engineering
**Course:** Optimization · **Term:** 2026-II · **Final Course Project**

---

## Description

EcoResiduos del Llano S.A.S. turns agricultural waste (palm, rice, livestock, and forestry by-products) into organic fertilizers, biofuels, and animal nutrition supplements. Its network connects **10 allied agricultural companies** (sources) with **4 processing plants** (destinations) located in **Villavicencio, Restrepo, Granada, and Puerto Gaitán**.

The current empirical assignment of routes leads to excess operating costs. This system:

1. Models the network as a directed graph and finds the **global optimum** with an exact solver.
2. Implements a **Genetic Algorithm (GA)** to obtain near-optimal solutions.
3. Allows **dynamic parameterization** of costs, supplies, and demands, and the addition of new companies or plants.
4. Performs **sensitivity analysis** (shadow prices, stability ranges, scenarios).
5. Generates a **comparative report** exact vs. GA (cost, time, gap, behavior).

## Features

-  **Exact model** for the transportation / minimum-cost problem (PuLP + CBC) with automatic constraint validation.
-  **Genetic Algorithm** with tournament/roulette selection, one- or two-point crossover, mutation, and penalized fitness.
-  **Sensitivity analysis**: shadow prices (duals), reduced costs, allowable ranges, and scenario simulation.
-  **Comparison** exact vs. GA: total cost, execution time, gap (%), and scalability.
-  **Web interface** (Streamlit) to edit cost matrices, supplies, and demands in real time.
-  **Scalable**: supports more companies and plants without code changes.

## Genetic Algorithm Design

| Component | Design |
|---|---|
| **Chromosome** | Flattened $m \times n$ matrix of flows $x_{ij}$, or shipment proportions per source |
| **Fitness** | $1 / (Z + \lambda \cdot \text{penalty})$, penalizing supply/demand violations |
| **Selection** | Tournament or roulette |
| **Crossover** | One- or two-point |
| **Mutation** | Flow perturbation / reassignment between plants |
| **Parameters** | Population size, generations, crossover rate, and mutation rate (adjustable from the interface) |

## Repository Structure

```
ecoresiduos-llano-optimizacion/
├── src/
│   ├── modelo/            # Network definition, graph, and data
│   ├── exacto/            # Linear programming solver (PuLP)
│   ├── genetico/          # Genetic Algorithm
│   ├── sensibilidad/      # Duals, ranges, and scenarios
│   ├── comparacion/       # Exact vs. GA report
│   └── interfaz/          # Streamlit app
├── data/                  # Sample matrices (CSV/JSON)
├── tests/                 # Unit tests
├── docs/                  # IEEE report, diagrams, figures
├── requirements.txt
├── LICENSE
└── README.md
```

## Sensitivity Analysis

Supported scenarios:

- **Fuel/transport cost** variation (± %).
- Percentage variation of **waste supply**.
- **Bottlenecks** in plant capacity/demand.

Outputs: shadow prices, reduced costs, validity ranges of the optimal basis, and the compared behavior of the exact model and the GA.

## Comparative Report

| Metric | Exact | Genetic Algorithm |
|---|---|---|
| Total cost ($) | — | — |
| Execution time (s) | — | — |
| Gap vs. optimum (%) | 0 | — |

*(Filled in automatically when the comparison module is run.)*

## Team and Roles

| Role | Member | Responsibility |
|---|---|---|
| Project Lead / Business Analyst | _Name_ | Coordination, IEEE report, model validation |
| Modeling and Optimization Engineer | _Name_ | Mathematical formulation and exact solver |
| Metaheuristics Developer | _Name_ | Genetic Algorithm and parameter tuning |
| Software and Interface Developer | _Name_ | Architecture, UI, and visualization |

## Deliverables

- [ ] Technical report (IEEE format) in `docs/`
- [ ] Documented and modular source code
- [ ] Practical defense with live scenarios

## 🛠️ Technologies

Python · PuLP (CBC) · NumPy · Pandas · NetworkX · Plotly · Streamlit · Pytest

## 📄 License

Distributed under the MIT license. See [`LICENSE`](LICENSE).

# Scenario-Based Analysis

Scenario-based analysis is an architecture evaluation method from classical
software engineering [^state-of-the-art-analysis].
It uses concrete usage scenarios for the system under design to test whether the
architecture can hold up to the requirements of its use cases.

In FullStaQD, we use this method to guide the design of our
[reference architecture](../reference-architecture/).
Additionally, we document the scenarios for other software architects to use them in the evaluation of their own
quantum software architecture instantiations, and for ourselves to evaluate
architectural decisions in future versions of our reference architecture.

Our set of scenarios was originally inspired by
[Carbonelli et al.'s work](https://doi.org/10.1007/978-3-031-64136-7_12) which
presented three industrial usage scenarios for quantum computing.
We have since extended our scenarios with the goal of covering a representative
set [^representative-study].
Our analysis currently covers the following scenarios:


[^state-of-the-art-analysis]: R. Kazman, G. Abowd, L. Bass and P. Clements [Scenario-based analysis of software architecture](https://doi.org/10.1109/52.542294) IEEE software 13.6 (1996)
[^representative-study]: Quantum Technology and Application Consortium–QUTAC info@ qutac. de, et al. [Industry quantum computing applications](https://link.springer.com/article/10.1140/epjqt/s40507-021-00114-x) EPJ Quantum Technology 8.1 (2021)

1. [Quantum Simulation for Material Science, Chemistry and Physics](./quantum-simulation.md)
2. [Quantum Cloud Services for Optimisation Problems](./cloud-optimisation.md)
3. [Collision Detection using Quantum Machine Learning](./quantum-machine-learning.md)

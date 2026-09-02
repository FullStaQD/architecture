# Scenario-Based Analysis

Scenario-based analysis is an archictecture evaluation method from classical
software engineering.
It uses concrete usage scenarios for the system under design to test whether the
architecture can hold up to the requirements of its use cases.

In FullStaQD, we used this method to guide the design of our
[reference architecture](../reference-architecture/).
We document them here for others to use in the evaluation of their own
quantum software architecture instantiations, and for ourselves to evaluate
architectural decisions in future editions of our reference architecture.

Our set of scenarios was originally inspired by
[Carbonelli et al.'s work](https://doi.org/10.1007/978-3-031-64136-7_12) which
presented three industrial usage scenarios for quantum computing.
We have since extended our scenarios with the goal of covering a representative
set.
Our analysis currently covers the following scenarios:

1. [Quantum Simulation for Material Science, Chemistry and Physics](./quantum-simulation.md)
2. [Quantum Cloud Services for Optimisation Problems](./cloud-optimisation.md)
3. [Collision Detection with an Embedded QPU](./embedded.md)
4. [Collision Detection using Quantum Machine Learning](./quantum-machine-learning.md)

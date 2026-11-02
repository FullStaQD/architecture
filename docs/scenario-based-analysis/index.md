# Scenario-Based Analysis

Scenario-based analysis is an architecture evaluation method from classical
software engineering [^state-of-the-art-analysis].
It uses concrete usage scenarios for the system under design to verify whether the
architecture can hold up to the requirements of its use cases.

In FullStaQD, we use this method to guide the design of our
[reference architecture](../reference-architecture/). At the current stage of the reference architecture, the scenario-based analysis focuses on the building block and runtime view. An extension to include the deployment view is planned for the future.
Additionally, we document the scenarios for other software architects to use them in the evaluation of their own
quantum software architecture instantiations, and for ourselves to evaluate
architectural decisions in future versions of our reference architecture. 

In order to use scenario-based analysis effectively, we validated an initial version of the FullStaQD Reference Architecture, developed as part of the QCNext Project[^qc-next], which was referred to as the “Proto-Stack”. Each software component in the scenarios was retrospectively assigned to its corresponding [building block](../reference-architecture/building-block-view.md) to provide better orientation and clarify the relationship between the individual software components. The conclusions of the scenario-based analysis can be seen in the [runtime view](../reference-architecture/runtime-view.md). 




Our set of scenarios was originally inspired by
[Carbonelli et al.'s work](https://doi.org/10.1007/978-3-031-64136-7_12) which
presented three industrial usage scenarios for quantum computing.
We have since adjusted our scenarios with the goal of covering a representative
set [^representative-study].
Our analysis currently covers the following scenarios:


[^state-of-the-art-analysis]: R. Kazman, G. Abowd, L. Bass and P. Clements [Scenario-based analysis of software architecture](https://doi.org/10.1109/52.542294) IEEE software 13.6 (1996)
[^representative-study]: Quantum Technology and Application Consortium–QUTAC et al. [Industry quantum computing applications](https://link.springer.com/article/10.1140/epjqt/s40507-021-00114-x) EPJ Quantum Technology 8.1 (2021)
[^qc-next]: QC Next – Development of a modular software stack for the commercial application of quantum computing:  [innovation concept](https://www.digital.iao.fraunhofer.de/en/competences/quantum-computing/innovation-concept-quantum-computing-software-stack-staqc.html) (2025)

1. [Quantum Simulation for Material Science, Chemistry and Physics](./quantum-simulation.md)
2. [Quantum Cloud Services for Optimisation Problems](./cloud-optimisation.md)
3. [Collision Detection using Quantum Machine Learning](./quantum-machine-learning.md)

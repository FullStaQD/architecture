# Scenario-Based Analysis

## Background

Scenario-based analysis is an architecture evaluation method from classical
software engineering [^state-of-the-art-analysis].
It uses concrete usage scenarios for the system under design to verify whether the
architecture can hold up to the requirements of its use cases.

## Methodology

In FullStaQD, we use this method to guide the design of our
[reference architecture](../reference-architecture/index.md). At the current stage of the reference architecture, the scenario-based analysis focuses on the building block and runtime view. An extension to include the deployment view is planned for the future.
Additionally, we document the scenarios for other software architects to use them in the evaluation of their own
quantum software architecture instantiations, and for ourselves to evaluate
architectural decisions in future versions of our reference architecture. 


In order to use the scenario-based analysis, we evaluate the "Proto-Stack" which was designed in the QCNext project[^qc-next], a predecessor of the FullStaQD project. The Proto-Stack is visualized below:
  ![](./images/Protostack.png)


Our set of scenarios was originally inspired by
[Carbonelli et al.'s work](https://doi.org/10.1007/978-3-031-64136-7_12) which
presented three industrial usage scenarios for quantum computing.
We have since adjusted our scenarios with the goal of covering a representative
set [^representative-study].
Our analysis currently covers the following scenarios:


1. [Quantum Simulation for Material Science, Chemistry and Physics](./quantum-simulation.md)
2. [Quantum Cloud Services for Optimisation Problems](./cloud-optimisation.md)
3. [Collision Detection using Quantum Machine Learning](./quantum-machine-learning.md)

To provide better orientation and clarify the relationships between individual software components, each component in the scenarios was retrospectively assigned to its corresponding building block of the [Building Block View](../reference-architecture/building-block-view/index.md). 

The results of the scenario-based analysis are embedded in many parts of the reference architectur, such as in the [Runtime View](../reference-architecture/runtime-view.md), [Building Block View](../reference-architecture/building-block-view.md), or in the [Cross-Cutting Concepts](../reference-architecture/cross-cutting-concepts.md). 

## Conclusions of the Scenario-based Analysis

### Separation of Concerns
A crucial aspect of the reference architecture is a clear separation of concerns between software components. This separation is essential for fulfilling key architectural [quality requirements](../reference-architecture/quality-requirements.md), such as [modularity](../reference-architecture/quality-requirements.md#maintainability-and-modularity) and [interchangeability](../reference-architecture/quality-requirements.md#interchangeability). Our scenario-based analysis of the Proto-Stack shows that a three-layered structure consisting of an application, system and physical layer provides a sufficient basis for separating the responsibilities of software components and aswell as their required associated knowledge, as discussed in more detail in the [Building Block View](../reference-architecture/building-block-view.md). A more granular structure with sublayers, as the Proto-Stack has, restricts the development of a software system too much and does not facilitate the realisation of the quality requirements. 

Additionally, our scenario-based analysis shows that some software components, such as software components which facilitate [fault tolerance](../reference-architecture/cross-cutting-concepts.md#fault-tolerance), can not be assigned exclusively to one layer. Depending on their functionality, they may extend across multiple layers or may not belong to any specific layer at all. We classify these software components as part of the [Cross-Cutting Concepts](../reference-architecture/cross-cutting-concepts.md), which also includes software components which are used for monitoring, benchmarking and resource estimation. The Proto-Stack addresses these types of software components through an additional layer. While this approach may be suitable for some components, our scenario-based analysis shows that they mostly need to be integrated into the relevant layers rather than treated as a separate layer.


### Interface between the Application and System Layer {#app-sys-interface}
In our scenario-based analysis, we introduce the concept of a *program* to define the interface between the Application and System Layer. A naive approach would be to use only a quantum circuit as interface. In this case, the Application Layer would provide a quantum circuit, which is subsequently transpiled by the System Layer and executed on the quantum hardware through the Physical Layer. However, a quantum circuit alone may not provide all the information required by the different layers of the architecture. Additional informationen may therefore be necessary like fault tolerance configurations, compilation requirements, or deployment specifications. Fruther details on the *program* interface are provided in the [Building Block View](../reference-architecture/building-block-view.md).




### Interface between the System and Physical Layers {#sys-phys-interaction}
The scenario-based analysis shows that the interface between the System Layer and the Physical Layer must exchange three types of information. First, the System Layer must be able to provide a set of commands supported by the firmware to execute the quantum circuit on the quantum hardware. Second, it needs to receive the results produced by the quantum hardware. Third, information about the hardware's properties and capabilities is required in advance to enable the System Layer to transpile the program for the target quantum hardware. 

Within the quantum computing ecosystem, several solutions already exist to facilitate this type of communication between the System Layer and the Physical Layer. These solutions are referred to as *Common Quantum Device Interfaces*, such as the [Quantum Device Management Interface (QDMI)](https://munich-quantum-software-stack.github.io/QDMI/) and the [Quantum Resource Management Interface (QRMI)](https://quantum.cloud.ibm.com/docs/en/guides/qrmi). A more detailed description of the communication and interaction of the System and Physical Layer is provided in the [Runtime View](../reference-architecture/runtime-view.md).





[^state-of-the-art-analysis]: R. Kazman, G. Abowd, L. Bass and P. Clements [Scenario-based analysis of software architecture](https://doi.org/10.1109/52.542294) IEEE software 13.6 (1996)
[^representative-study]: Quantum Technology and Application Consortium–QUTAC et al. [Industry quantum computing applications](https://link.springer.com/article/10.1140/epjqt/s40507-021-00114-x) EPJ Quantum Technology 8.1 (2021)
[^qc-next]: QC Next – Development of a modular software stack for the commercial application of quantum computing:  [innovation concept](https://www.digital.iao.fraunhofer.de/en/competences/quantum-computing/innovation-concept-quantum-computing-software-stack-staqc.html) (2025)

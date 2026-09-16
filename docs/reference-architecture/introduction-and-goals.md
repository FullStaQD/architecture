# Introduction and Goals {#section-introduction-and-goals}
The FullStaQD reference architecture is the first step towards modular full-stack quantum software, which ensures compatibility and interoperability of various components in the quantum ecosystem. We aim to develop a reference architecture with uniform standardised interfaces, which is consistent, modular and open. 


## Overview 
The reference architecture is divided into three layers: Application, System and Physical Layer.

![](./images/Reference-Architecture-Introduction.png)



In addition to these three layers, the architecture also defines cross-layer concerns, which can show up in any of the layers. 

The table below provides a brief description of the layers and the cross-layer concerns.

| Module  | Description | 
| ------------- | ------------- | 
| Application Layer | Contains all components on a high-level programming language or algorithmic level  |
| System Layer  | Contains all components to adjust high-level program to the specific hardware and to integrate HPC |
| Physical Layer  | Contains all components on a physical layer which indirectly/directly communicate with the physical quantum device  |
| Cross-Layer Concerns  | Is part of each Layer and contains all components like Testing, Benchmarking, Simulations, Tools, Visualization, ...  |

A detailed breakdown of the components of the layers can be seen in the [building block view](./building-block-view.md).


## Quality Goals {#_quality_goals}
To maintain a state of the art reference architecture in the quantum ecosystem, we consider the following quality goals as most important for this architecture.

| Quality Goal  | Description | 
| ------------- | ------------- | 
| Operability  | The reference architecture can be understood, learned, used and is attractive to users from academia and industry  |
| Compatibility  | HPCs and existing infrastructure can be integrated into the reference architecture using specific interfaces  |
| Maintainability  | The reference architecture can be modified, corrected, adapted or improved due to changes in the environment or requirements with ease |
| Modularity  | Systems, components or whole layers can be integrated and are exchangeable into the reference architecture using specified interfaces  |
| Reliability  | The reference architecture can maintain a high level of performance  when used under specific conditions  |

## Stakeholders {#stakeholders}
Quantum software systems is developed and used by stakeholders with different
motives, interests and constraints.
These forces influence the design of software systems, and software architecture
in particular.
For example, stakeholders can demand different levels of abstractions:
Business users of quantum software benefit from a high level of abstraction to
inform their decisions whereas quantum firmware developers need access to all
technical details.

Schmidbauer et al.[^stakeholder-personas-ref] present the following persona
hypothesis, that is a characterisation of the typical stakeholders in quantum
software:

| Category | Stakeholders |
|-|-|
| *Application-oriented* | business user, early adopter, government contractor |
| *Application- and hardware-oriented* | simulation-focused engineer, researcher |
| *Hardware-oriented* | platform builder, quantum algorithm designer, HPC engineer, embedded quantum developer |

In the FullStaQD Reference Architecture, we keep stakeholders in mind throughout
the architecture design.
Most prominently, the reference architecture uses a
[three-layered architecture](./building-block-view.md) to offer different levels
of abstraction to different stakeholders. 

??? info "More about stakeholders"

    More info on documenting stakeholders can be found in the
    [arc42 docs](https://docs.arc42.org/section-1/#13-stakeholder).
    For a recent study on stakeholders in quantum software, check out the
    ["Know You Qubits, Know Your Users: Personas for Quantum Software"][stakeholder-personas-link]
    paper by Schmidbauer et al..

[^stakeholder-personas-ref]: Schmidbauer, L. ["Know You Qubits, Know Your Users: Personas for Quantum Software"][stakeholder-personas-link]. Preprint on arXiv (2026).

[stakeholder-personas-link]: https://arxiv.org/abs/2608.18598

## Methodology  
To fulfill the requirements and goals of the reference architecture, we consider several key aspects that are fundamental to the design of modern software architectures:

- the multitude of perspective of stakeholders and use cases
- the multitude of abstractions, where most expertise of stakeholders focuses only a specified area
- the multitude of languages, which are used by the different domain experts  (physicists, software-engineers, mathematicians, ...)
- the rapid advancement in the quantum eco system


To address these aspects and continuously validate and refine the reference architecture, we employ a set of state-of-the-art methods from classical software engineering:
 <!--  Hier könnte man Paper oder Ergebnisse hinten noch als Spalte in Zukunft Verlinken -->
| Method  | Description | Reason | 
| ------------- | ------------- | ------------- | 
|[scenario-based analysis](../scenario-based-analysis/)| Using predefined scenarios of use cases on the reference architecture  | To assess how well the reference architecture covers the predefined scenarios and to identify the common requirements shared by the components on which those scenarios depend.  |
| Requirement Survey  | Sending surveys to stakeholders asking for requirements and needs for their components | Obtaining high-level input on the requirements that the reference architecture must fulfill  |
| Interview with Stakeholders  | In-depth interviews with stakeholders about the reference architecture and their respective positions  | Acquiring detailed insights of Stakeholders and adopt their input  |
| Workshops  | Regular on-site exchange with the consortium  | Updating partners of current status and discussing next steps |
| Community Engagement | Allowing open requests and discussion about the reference architecture through our ticket system | Ensuring external input, extendability and exchangability | 

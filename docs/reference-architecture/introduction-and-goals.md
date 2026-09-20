# Introduction and Goals {#section-introduction-and-goals}
The FullStaQD reference architecture is the first step towards modular full-stack quantum software, which ensures compatibility and interoperability of various components in the quantum ecosystem. We aim to develop a reference architecture with uniform standardised interfaces, which is consistent, modular and open. 

!!! info "What is a reference architecture?"

    **Software Architecture:**
    In software engineering, the architecture of a software system describes its
    high-level design.
    Software architectures are ideally designed after researching the
    requirements of the system under design, and before designing the
    fine-grained structure of the system.
    Thinking about the high-level structure of a system early on in its design
    process allows the architect to address *architecturally significant
    requirements* -- such requirements are usually hard or expensive to retrofit
    once the system has been implemented already.
    A typical example for architecturally significant requirements is a
    performance requirement since tight performance bounds can often only be
    achieved with the right technologies (e.g. programming languages or
    databases), and with tight couplings between components that require
    low-latency or high-bandwidth communication.

    **Reference Architecture:**
    A reference architecture adds another level of abstraction compared to
    concrete software architectures.
    It describes the "essence of the architectures of a set of software systems
    of a given domain" and "its purpose is to be a guidance for the development,
    standardization, and evolution of systems."[^nakagawa-refarch-model]
    Reference architectures can be used to describe families or product lines of
    software systems, and here we use it to describe the family of quantum
    software systems.

    **Example:**
    The well-known OSI telecommunications model is a well-known example which
    can be considered a reference architecture.
    It defines seven abstractions layers which characterise a separation of
    concerns in telecommunications without specifying concrete implementations
    for these layers, or concrete protocols between them.
    The OSI model can be *instantiated* to describe WWW systems, for example
    using TCP on the transport layer, SSL on the presentation
    layer, and HTTP on the application layer.
    The reference architecture is abstract enough to be stable w.r.t. changes of
    the concrete protocols (e.g. using a different encryption protocol on the
    presentation layer) yet it is concrete enough to provide a common structure
    to telecommunications systems.

    <figure markdown="span">
        ![](./images/osi-model.png){ style="max-width: min(100%, 25rem)" }
        *Visualisation of the OSI model, adapted from Fortier et al.[^fortier-osi-model].*
    </figure>

[^nakagawa-refarch-model]: Nakagawa, E. Y., Oquendo, F. & Becker, M. ["RAModel: A Reference Model for Reference Architectures"](https://doi.org/10.1109/WICSA-ECSA.212.49). 2012 Joint Working IEEE/IFIP Conference on Software Architecture and European Conference on Software Architecture (2012).
[^fortier-osi-model]: Fortier, P. J. & Michel, H. E. ["15 - Analysis of Computer Networks Components"](https://doi.org/10.1016/B978-155558260-9/50015-1), in Computer Systems Performance Evaluation and Prediction (2003).


## Overview 
The reference architecture is divided into three layers: Application, System and Physical Layer.

<figure markdown="span">
    ![](./images/Reference-Architecture-Introduction.png){ style="max-width: min(100%, 20rem)" }
</figure>


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
| [Scenario-Based Analysis](../scenario-based-analysis)| Using predefined scenarios of use cases on the reference architecture  | To assess how well the reference architecture covers the predefined scenarios and to identify the common requirements shared by the components on which those scenarios depend.  |
| Requirement Survey  | Sending surveys to stakeholders asking for requirements and needs for their components | Obtaining high-level input on the requirements that the reference architecture must fulfill  |
| Interview with Stakeholders  | In-depth interviews with stakeholders about the reference architecture and their respective positions  | Acquiring detailed insights of Stakeholders and adopt their input  |
| Workshops  | Regular on-site exchange with the consortium  | Updating partners of current status and discussing next steps |
| Community Engagement | Allowing open requests and discussion about the reference architecture through our ticket system | Ensuring external input, extendability and exchangability | 

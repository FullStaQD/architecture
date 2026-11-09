# Quality Requirements {#section-quality-scenarios}
Quality Requirements are a key aspect in designing an architecture. They describe non-functional properties of a system and must be addressed at an architectural level, as changes for addressing quality requirements can become difficult or expensive afterwards.

This section describes typical quality requirements that are relevant to quantum software systems in general. Although many of these quality requirements have been addressed in the design of the reference architecture, they still need to be taken into account during implementation. Specific implementations may have additional quality requirements, which are not covered. To validate the quality requirements, we also describe and assign example scenarios. Our quality terminology is in line with the [arc42 quality model](https://quality.arc42.org/qualities/) but tailored towards quantum software.


## Quality Requirements

### Adaptability
*Related quality scenarios: [`SC2`](#sc2), [`SC4`](#sc4)*

There are various different physical implementations for the mathematical model
of a quantum computer.
This includes Neutral Atom Qubits, Superconducting Qubits, Majorana Qubits and
others.
No clear winner has yet emerged from these hardware architectures and it is
reasonable to assume that application developers might want to switch hardware,
or be able to execute their application on multiple hardware types.
We therefore specify the following quality requirement:

!!! abstract "Quantum software systems should be adaptable to different quantum computing hardware."

??? note "Realisation in the FullStaQD Reference Architecture"

    In the FullStaQD Reference Architecture, adaptability is realised through the
    following measures:

    * The [three-layered architecture](./building-block-view.md) specifies the
      [Application Layer](./building-block-view.md#application-layer) to be
      device-independent.
      This separation limits the places that need to be changed in order to
      adapt to a new type of hardware to the
      [System](./building-block-view.md#system-layer) and
      [Physical Layer](./building-block-view.md#physical-layer). 
    * Adaptation of a program to specific hardware types is an explicit
      responsibility of the Compiler within the System Layer.
      Most adaptation logic can therefore be contained within a single
      place[^fn-adaptation-in-single-place], which also enables reuse of
      adaptation logic.

[^fn-adaptation-in-single-place]: The compiler can contain most but not all required changes for adapting to different hardware. Exceptions include the Common Quantum Device Interface Adapter which needs to be implemented for each individual hardware type (but is reusable) and any hardware-specific features used in the application layer. 

### Evolvability and Extensibility
*Related quality scenarios: [`SC2`](#sc2)*

The field of quantum computing is evolving rapidly with new hardware models,
algorithms, quantum error correction codes and SDKs becoming available at an
enormous pace.
For many of these aspects, it is not yet clear which exact implementations will
be chosen for the realisation of practical quantum computing.
To keep up with the state of the art, quantum software systems must be able to
adopt such new methods.
We here phrase this evolvability requirement as a matter of extensibility:

!!! abstract "Quantum software systems need to be extensible in the following dimensions:"

    * They must be extensible to use new problem transformations.
    * They must be extensible to employ new quantum algorithms.
    * They must be extensible to support new quantum programming languages and quantum SDKs.
    * They must be extensible to use new quantum error correction codes.
    * They must be extensible to use new compilation passes.
    * They must be extensible to execute quantum programs on new hardware models (see also: [Adaptability](#adaptability)).

??? note "Realisation in the FullStaQD Reference Architecture"

    The FullStaQD Reference Architecture realises the extensibility requirements
    through modularity and a clear separation of concerns.

    * New problem transformations and algorithms can be implemented as part of
      the [Application Layer](./building-block-view.md#application-layer) within
      the respective components.
    * New quantum programming languages and quantum SDKs can be supported by
      implementing a corresponding language frontend within the
      [System Layer](./building-block-view.md#system-layer)'s Compiler.
    * New quantum error correction codes can be implemented as compilation
      passes, as part of the Quantum System Controller, or as part of the
      Use Case within the Application Layer, see
      [Fault Tolerance](./cross-cutting-concepts.md#fault-tolerance) for
      details.
    * The compilation pass extensibility requirement is realised in the
      Compiler.
    * New types of quantum hardware can be supported by implementing a
      corresponding Common Quantum Device Interface Adapter and a corresponding
      Backend within the Compiler, see [Adaptability](#adaptability).

### Fault Tolerance
*Related quality scenarios: [`SC3`](#sc3)*

Quantum computers are subject to noise, i.e. their states are disturbed randomly
through imprecise operations or unwanted interactions with the environment (such
as electromagnetic radiation).
Noise is widely recognised one of the most significant challenges in quantum
computing[^ref-preskill-nisq].
When unhandled, these disturbances can accumulate such that the result of the
(ideal) computation is lost.
Fault tolerance is therefore one of the central quality requirements of a
quantum software sytems:

!!! abstract "Quantum software systems must be resilient to noise on hardware, i.e. quantum programs should produce their intended result even in the presence of limited amounts of noise."
<!-- TODO: make it concrete, what noise levels are to be expected? -->

??? note "Realisation in the FullStaQD Reference Architecture"

    The FullStaQD Reference Architecture treats
    [Fault Tolerance as a cross-cutting concept](./cross-cutting-concepts.md#fault-tolerance),
    providing guidance on typical ways to implement fault tolerance measures
    such as quantum error [correction](./glossary.md#quantum-error-correction),
    [mitigation](./glossary.md#quantum-error-mitigation) and
    [suppression](./glossary.md#quantum-error-suppression).
    The narrow latency and bandwidth requirements of quantum error correction
    are baked into the design of the architecture,
    see&nbsp;[Deployment](./deployment-view.md) and [Latency](#latency).

[^ref-preskill-nisq]: Preskill, J. [Quantum Computing in the NISQ era and beyond](https://quantum-journal.org/papers/q-2018-08-06-79/). Quantum 2, 79 (2018).

### Integrability
*Related quality scenarios: [`SC2`](#sc2)*

Quantum computers are not expected to replace traditional computers as they
excel only at problems that can be mapped well onto the quantum computation
model.
Therefore, quantum software systems will usually be used as part of a larger
system where those specialised problems arise.
For example, an optimisation problem from the scheduling systems of a logistics
company might be submitted to a quantum software system, or a molecule
specification from specialised pharmaceutical research software might be sent to
a quantum software system for computing the ground state.
Integrability is crucial for corporate users of quantum software systems, so we
state the following quality requirement: 

!!! abstract "Quantum software systems must be integrable into existing IT infrastracture."

??? "Realisation in the FullStaQD Reference Architecture"

    The boundaries of quantum software systems, and the integration into
    external IT infrastructure is discussed in the
    [Context and Scope](./context-and-scope.md) section.
    The interface between external IT systems and quantum software systems is a
    responsibility of the
    [Application Layer](./building-block-view.md#application-layer).
    More specfically, the interface to external IT systems can be realised
    through the Use Case component, or it can be supported by specialised
    Integration Tooling.

### Latency 
The data transmission latency between components e.G. between quantum device and QEC decoder must be minimised. ([SC3](#quality-scenarios))
### Maintainability 
The architecture needs must allow modifications with ease after the baseline is established. ([SC2,SC4](#quality-scenarios))
### Modularity  
The architecture needs to limit changes to one component from affecting other components, e.g. exchanging quantum hardware should not affect the application layer. ([SC4](#quality-scenarios))
### Interchangeability 
The architecture should be interchangeable, which allows it to substitute one component, part, or element with another of the same type without requiring modifications to the system or loss of functionality. This including different SDKs, compilers and hardware backends. ([SC2](#quality-scenarios))
### Resource utilization 
The quantum compiler should optimise quantum programs in order to minimise the number of required qubits and gates. An inefficient quantum program can lead to high costs for the user. ([SC1](#quality-scenarios))
### Scalability 
Because of the rapidly evolving field of quantum technology, the architecture should be scalable in terms of job size, kernel amount, ... ([SC2](#quality-scenarios))
### Testability 
The architecture needs to be capable to enable an objective and feasible test to be designed and performed to determine whether a requirement is met.


## Quality Scenarios

### `SC1`: Cost Estimation {#sc1}
A stakeholder who received a cost estimate for the execution of their program only has to pay the estimated amount.

### `SC2`: Switching Hardware Vendor {#sc2}
A stakeholder should be able to change its hardware vendors without facing high costs.

### `SC3`: Performance should be guaranteed {#sc3}
The time and quality of performance when executing a program should be as expected.

### `SC4`: Software Update {#sc4}
The maintenance time must be low when the software used for the quantum programme is updated.

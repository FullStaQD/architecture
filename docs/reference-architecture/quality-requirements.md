# Quality Requirements
Quality Requirements are a key aspect in designing an architecture.
They describe non-functional properties of a system and must be addressed on an architectural level, as changes for addressing quality requirements can become difficult or expensive afterwards.

This section describes typical quality requirements relevant to quantum software
systems in general.
Although many of these quality requirements have been addressed in the design of
the reference architecture, they still need to be taken into account during
the implementation.
Concrete quantum software systems will usually have additional quality
requirements which are not covered here.

!!! info "Terminology"

    Our quality requirements terminology is based on the *arc42 quality model*
    but tailored towards quantum software.
    Check out the [arc42 quality docs](https://quality.arc42.org/qualities/) for
    explanations and examples of the quality terms in the context of classical
    software engineering.

## Adaptability

There are various different physical implementations for the mathematical model
of a quantum computer.
This includes neutral atom qubits, superconducting qubits and others.
The field has not yet converged on a single hardware architecture and it is
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
      adapt to a new type of quantum hardware to the
      [System](./building-block-view.md#system-layer) and
      [Physical Layer](./building-block-view.md#physical-layer). 
    * Adaptation of a program to specific quantum hardware types is an explicit
      responsibility of the Compiler within the System Layer.
      Most adaptation logic can therefore be contained within a single
      place[^fn-adaptation-in-single-place], which also enables reuse of
      adaptation logic.

[^fn-adaptation-in-single-place]: The compiler can contain most but not all required changes for adapting to different hardware. Exceptions include the Common Quantum Device Interface Adapter which needs to be implemented for each individual quantum hardware type (but is reusable) and any hardware-specific features used in the application layer. 

## Evolvability and Extensibility

The field of quantum computing is evolving rapidly with new quantum hardware
models, algorithms, error correction codes and SDKs becoming available
at an enormous pace.
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

## Fault Tolerance

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

## Integrability

Quantum computers are not expected to replace classical computers as they
outperform classical computers only for problems that can be mapped well onto
the quantum computation model.
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

## Latency

Noise is one of the most significant challenges in practical quantum computing,
and quantum error correction is considered a key measure in order to achieve
[Fault Tolerance](#fault-tolerance).
But as noise accumulates quickly, quantum error correction rounds must be run at
a high frequence to be effective.
This implies the following latency requirement:

!!! abstract "The data transmission latency between the Quantum System Controller and the Quantum Error Correction Decoder must be low."
<!-- TODO: specify concrete value -->

??? note "Realisation in the FullStaQD Reference Architecture"

    Latency and bandwith between execution environments are discussed in the
    [Deployment View](./deployment-view.md) section.
    The FullStaQD Reference Architecture suggests to execute latency-critical
    parts of the quantum software system in an execution environment close to
    the [QPU](./glossary.md#quantum-processing-unit) whereas less
    latency-critical parts of the system such as the compiler can be executed
    elsewhere.
    The Compiler and HPC Resource Scheduler are responsible for running
    latency-critical parts on suitable hardware.

## Maintainability and Modularity

The key motivation behind the FullStaQD Reference Architecture is to promote
interoperability in the quantum software ecosystem
(see&nbsp;[Introduction](./index.md)).
Software engineering design principles suggest modularity as a solution to
keeping complex systems maintainable.
We therefore make modularity an explicit quality requirement:

!!! abstract "Quantum software systems must be modular, i.e. changes to one component should not affect other components."

??? note "Realisation in the FullStaQD Reference Architecture"

    Modularity was one of the guiding design principles in the design of the
    FullStaQD Reference Architecture.
    It is achieved through a clear separation of concerns and well-defined
    interfaces.
    For example, the following architectural decisions were taken for the sake
    of modularity:
    
    * The Common Quantum Device Interface acts as a facade to the Physical
      Layer.
      Changes to the Quantum System Controller or Simulator can therefore be
      contained within the Physical Layer.
    * Quantum programming languages and other exchange formats act as an
      interface between the Application and System Layer.
      Changes within one of these layers will not affect the other.

    See [Building Block View](./building-block-view.md) for details.

## Interchangeability

One of the key goals of the FullStaQD Reference Architecture is to promote
interoperability between various components in the quantum software ecosystem.
Our reference architecture describes a common framework for quantum software
systems with placeholder components representing the various different
responsibilities.
Therefore, any component realising the full specification of some placeholder
component should be suitable for an implementation.
We state this as the following requirement:

!!! abstract "All components should be interchangeable, i.e. it should be possible to substitute them with another implementation of the same type without requiring modifications to the quantum software system, or incurring loss of functionality."

??? note "Realisation in the FullStaQD Reference Architecture"

    The FullStaQD Reference Architecture doesn't specify concrete
    implementations; it merely describes the abstract components and
    responsibilities necessary for realising quantum software systems, as well
    as the interfaces between them
    (see&nbsp;[Building Block View](./building-block-view.md)).
    Components of the reference architecture are therefore interchangeable by
    design.

## Resource utilisation 

In the NISQ era, quantum resources like qubits and gates will be
scarce[^ref-preskill-nisq] and resource utilisation is often a deciding factor
for whether a quantum program can run at all.
The roadmaps of major quantum hardware providers suggest that devices with
thousands to millions of physical qubits might become available in the next few
decades but even then, practical applications might run into limits due to
quantum error correction overheads or the sheer problem size.
Furthermore, it is not yet clear how expensive quantum resource usage will be in
the long term.
Therefore, we formulate the following resource utilisation requirement:

!!! abstract "Quantum software systems should minimise the number of used qubits and gates."

??? note "Realisation in the FullStaQD Reference Architecture"

    While minimising resource utilisation is a joint effort between all
    components of the stack, the FullStaQD Reference Architecture identifies the
    following key areas for achieving a low resource utilisation:
    
    * Application problems are first mapped to quantum programs in the Use Case
      and Problem Transformations components within the
      [Application Layer](./building-block-view.md#application-layer).
      This mapping first determines the amount of required resources.
    * The Compiler within the
      [System Layer](./building-block-view.md#system-layer) is responsible for
      minimising the resource usage of a given quantum program.
    * Quantum Resource Estimation and Monitoring tools can further help analyse
      and understand the quantum resource usage of a given application.
      See the [Cross-Cutting Concepts](./cross-cutting-concepts.md) section for
      further details.

## Scalability

NISQ era quantum hardware only features up to a few hundred qubits and gates but
major hardware providers claim in their roadmaps that these numbers will
increase rapidly within the next decade.
Scaling up to a large number of qubits and gates comes with new challenges:
For example, decoding large quantum error correction codes can no longer be done
using lookup tables, programs can no longer be stored as plain circuits and
qubit routing in transpilation can become computationally expensive.
We therefore state the following quality requirement:

!!! abstract "Quantum software systems need to be scalable in terms of qubit count, gate count, and number of jobs."

??? note "Realisation in the FullStaQD Reference Architecture"

    The FullStaQD Reference Architecture addresses this requirement through the
    following measures:

    * We explore quantum program formats beyond OpenQASM circuits.
      Since no standard has yet emerged for this purpose, the interfaces between
      the three layers deliberately allow for different formats and components
      are specified with dynamic circuits in mind.
      See the [Building Block View](./building-block-view.md) section for
      further details.
    * The [Deployment View](./deployment-view.md) section also discusses the
      integration of [QPUs](./glossary.md#quantum-processing-unit) into HPC
      systems to meet computational needs.
      For example, the architecture suggests to locate QEC decoders on powerful
      machines close to the Quantum System Controller.
    * The architecture addresses the potentially large number of quantum
      computing jobs through an integration with HPC resource schedulers.
      See the [Physical Layer](./building-block-view.md#physical-layer) for
      details.

    In the end, however, scalability is something that cannot be addressed in
    the architecture alone and needs to be considered in the design of
    individual components too. 

## Unit Testability

The FullStaQD Reference Architecture aims to achieve a separation of concerns
that allows vendors to implement quantum software components independently from
each other.
The [Modularity](#maintainability-and-modularity) requirement already states
that changes to one component should not affect other components.
For full independence of the development process, developers also need to be
able to test components independently from each other.
We therefore state the following unit testability requirement:

!!! abstract "Components of quantum software systems should be testable independently from each other."

??? note "Realisation in the FullStaQD Reference Architecture"

    The FullStaQD Reference Architecture discusses benchmarking and testing
    tools as [Cross-Cutting Concepts](./cross-cutting-concepts.md).

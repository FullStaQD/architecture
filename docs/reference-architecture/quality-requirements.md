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

### Evolvability 
Due to the fast evolving field of quantum computing, the architecture needs to adapt to changes in its environment, requirements, and implementation technologies in a cost-effective way. These changes could involve new software, algorithms, or hardware technology.  ([SC4](#quality-scenarios))
### Extensibility 
We want to be able to extend quantum software systems with new compilation passes, problem transformations and applications. ([SC2](#quality-scenarios))
### Fault tolerance 
Quantum software systems must be resilient to noise on hardware, i.e. quantum programs should produce their intended result even in the presence of noise. ([SC3](#quality-scenarios))
### Integrability 
The architecture allows software components or systems to be easily integrated into the existing IT infrastructure of stakeholders. It is important to ensure that stakeholders are motivated to use the architecture.  ([SC2](#quality-scenarios))
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
